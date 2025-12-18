# Tagebucheintrag transkribieren

Workflow zum Transkribieren von Tagebucheinträgen aus Bildern.

## Workflow

### 1. Bilder mit Mistral-OCR transkribieren
- Verwende das `mistral-ocr` MCP Tool (`mcp_mistral-ocr_extract_file_content`) für alle bereitgestellten Bilder
- Führe die OCR-Extraktion für alle Bilder parallel durch
- **Bildtypen analysieren:**
  - **Handgemalte Bilder erkennen:** Analysiere die OCR-Ergebnisse und Bildinhalte auf handgemalte Zeichnungen, Skizzen, Illustrationen oder handgeschriebene Notizen mit visuellen Elementen
  - **Nicht transkribierte Bilder erkennen:** Prüfe, ob ein Bild keine oder nur minimale Text-Extraktion ergeben hat (z.B. nur Fotos ohne Text, Bilder mit zu schlechter Qualität für OCR, oder Bilder die hauptsächlich visuelle Inhalte ohne Text enthalten)
- Kombiniere die transkribierten Texte zu einem vollständigen Eintrag
- **Merke dir für jeden Eintrag:**
  - Ob handgemalte Bilder vorhanden sind → Tag `hasdrawing` hinzufügen
  - Ob nicht transkribierte Bilder vorhanden sind → Tag `hasphoto` hinzufügen

### 2. Tagebuch-Memory anlegen
- **Mood extrahieren:** In der Überschrift des Eintrags steht immer eine Zahl, die die Stimmung (Mood) des Tages repräsentiert. Extrahiere diese Zahl aus der Überschrift.
- **Titel extrahieren:** 
  - Wenn die erste Zeile des transkribierten Texts eine unterstrichene Überschrift ist (Markdown-Format mit `---` oder `___`), verwende diese Zeile als Titel
  - Entferne die Unterstriche aus dem Titel (z.B. `---Titel---` → `Titel`)
  - **Wichtig:** Konvertiere den Titel immer in normale Schreibweise (nicht ALL CAPS). Auch wenn der Titel im Original in Großbuchstaben steht (z.B. `SCHLECHTE NACHRICHTEN`), verwende normale Schreibweise (z.B. `Schlechte Nachrichten`)
  - Falls keine unterstrichene erste Zeile vorhanden ist, verwende das Format "Tagebucheintrag DD.MM.YY" oder "Tagebucheintrag YYYY-MM-DD" basierend auf dem Datum
- **Datum extrahieren:** Extrahiere das Datum aus dem Titel oder dem Inhalt des Eintrags und konvertiere es in ISO-Format (YYYY-MM-DD)
- Erstelle eine neue DIARY-Erinnerung mit `mcp_llm-mem_write_mem`
- **Kategorie:** `DIARY`
- **Titel:** Wie oben extrahiert
- **Inhalt:** Der vollständige transkribierte Text (ohne die unterstrichene erste Zeile, falls diese als Titel verwendet wurde)
  - **Bilder verlinken:** Füge am Ende des Inhalts einen Abschnitt "## Bilder" hinzu und verlinke alle verwendeten Quell-Bilder im Obsidian-Wiki-Link-Format
  - Verwende das Obsidian-Wiki-Link-Format: `![[Dateiname]]` (ohne Pfad, nur Dateiname)
  - Format: `![[YYYY-MM-DD N.jpeg]]` oder `![[YYYY-MM-DD N.png]]` (wenn mehrere Bilder vorhanden)
  - Beispiel: `![[2025-08-14 1.png]]` und `![[2025-08-14 2.png]]`
  - **Wichtig:** Verwende nur den Dateinamen ohne `Images/` Pfad, da Obsidian die Dateien im Vault findet
- **Tags:** Mindestens `diary` und das Datum (z.B. `2025-08-14`)
  - **Bild-bezogene Tags hinzufügen:**
    - Wenn handgemalte Bilder erkannt wurden: Füge `hasdrawing` hinzu
    - Wenn nicht transkribierte Bilder vorhanden sind: Füge `hasphoto` hinzu
- **Abstract:** Kurze Zusammenfassung des Eintrags (1-2 Sätze)
- **Frontmatter (template):** Füge IMMER die folgenden Felder hinzu:
  - `mood`: Die extrahierte Mood-Zahl
  - `date`: Das Datum im ISO-Format (YYYY-MM-DD)
  - `place`: Initial auf `null` setzen (wird in Schritt 2.5 aktualisiert, falls ein Place identifiziert wird)
  - Verwende den `template` Parameter mit `{"mood": <zahl>, "date": "YYYY-MM-DD", "place": null}`
  - Beispiel: `template: {"mood": 5, "date": "2025-08-14", "place": null}`

### 2.5. Places identifizieren und zuweisen
- **Prüfe Benutzer-Kommando:** Wenn der Benutzer im Kommando explizit einen Place erwähnt (z.B. "Place: Familie Nickola" oder "bei Familie Nickola"), verwende diesen Place
- **Place aus Text extrahieren:** Analysiere den transkribierten Text auf Ortsangaben:
  - Adressen (Straße + Hausnummer + PLZ + Stadt)
  - Bekannte Orte (z.B. "bei Familie Nickola", "in Kaiserslautern", "Spinozastraße 15")
  - Städte oder Regionen
- **Suche nach existierenden PLACE-Erinnerungen:** 
  - Suche mit `mcp_llm-mem_search_mem` nach PLACE-Erinnerungen, die zu den extrahierten Ortsangaben passen
  - Verwende Kategorie-Filter: `category: PLACE`
  - Suche nach Adressen, Straßennamen, Städtenamen oder anderen eindeutigen Identifikatoren
- **Place zuweisen:**
  - **Wenn explizit im Kommando erwähnt:** Verwende den erwähnten Place, auch wenn mehrere Matches gefunden werden
  - **Wenn eindeutig identifiziert (genau ein Match):** 
    - Verknüpfe den Tagebucheintrag mit der PLACE-Erinnerung mit `mcp_llm-mem_link_mem` (bidirektionale Verknüpfung)
    - Aktualisiere die DIARY-Erinnerung mit `mcp_llm-mem_edit_mem` und setze das `place` Feld im Frontmatter auf die ID der PLACE-Erinnerung
  - **Wenn mehrere Matches oder unklar:** 
    - Lege den Tagebucheintrag **ohne Place** an (place bleibt `null`)
    - Ausnahme: Wenn der Benutzer explizit einen Place im Kommando erwähnt hat, verwende diesen trotzdem
  - **Wenn kein Match gefunden:** Lege den Tagebucheintrag ohne Place an (place bleibt `null`)

### 3. Personen identifizieren und verlinken
- Analysiere den transkribierten Text auf erwähnte Personen
- Für jede erwähnte Person:
  - Prüfe, ob bereits eine PERSON-Erinnerung existiert (mit `mcp_llm-mem_search_mem`)
  - Falls nicht vorhanden: Erstelle eine neue PERSON-Erinnerung mit `mcp_llm-mem_write_mem`
    - **Kategorie:** `PERSON`
    - **Inhalt:** Name als Überschrift, Erwähnungen aus dem Tagebucheintrag
    - **Tags:** `persons`
- Verknüpfe den Tagebucheintrag mit allen erwähnten Personen mit `mcp_llm-mem_link_mem`
  - Bidirektionale Verknüpfung zwischen Tagebucheintrag und jeder Person

### 4. Zusätzliche Tags extrahieren
- **Häufig verwendete Tags abrufen:** Lese zuerst die Memory "Tags, die ich häufig verwende" mit `mcp_llm-mem_read_mem` oder `mcp_llm-mem_search_mem`, um die bevorzugten Tags zu erhalten
- Analysiere den Tagebucheintrag auf wichtige Themen und Kontexte
- **Tags bevorzugen:** Wenn Inhalte im Tagebucheintrag zu den häufig verwendeten Tags passen (z.B. `physiotherapies`, `psychotherapies`, `doctors`, `offices`), verwende diese bevorzugt
- **Bild-bezogene Tags bereits hinzugefügt:** Die Tags `hasdrawing` und `hasphoto` wurden bereits in Schritt 2 hinzugefügt, falls zutreffend
- Extrahiere die **wichtigsten zusätzlichen Tags** (zusätzlich zu `diary`, Datum, `hasdrawing` und `hasphoto`)
  - **Keine Begrenzung:** Füge so viele relevante Tags hinzu, wie sinnvoll sind (mindestens 3-5, aber gerne mehr wenn passend)
  - Berücksichtige dabei auch visuelle Inhalte aus den Bildern (z.B. `food` wenn Essen fotografiert wurde, `nature` für Naturbilder, `people` für Personenfotos, etc.)
- Aktualisiere die Tagebuch-Erinnerung mit `mcp_llm-mem_edit_mem` und füge alle relevanten Tags hinzu
- Beispiele für sinnvolle Tags: `families`, `jobs`, `stresses`, `health-issues`, `therapies`, `physiotherapies`, `travels`, `food`, `nature`, `people`, `activities`, `events`, etc.

## Formatierung (optional)

Falls Formatierung aus dem Original übernommen werden soll:
- Unterstrichene Überschriften beibehalten
- Wörter in Akzentfarbe als **fett** markieren
- Namen nur **fett** setzen, wenn sie in Akzentfarbe hervorgehoben sind

## Beispiel

```
1. OCR-Extraktion: 2 Bilder (2025-08-14 1.png, 2025-08-14 2.png) → kombinierter Text
2. Mood extrahieren: Zahl "5" aus Überschrift → mood: 5
3. Datum extrahieren: "14.8.25" → date: "2025-08-14"
4. Titel extrahieren: Unterstrichene erste Zeile oder "Tagebucheintrag 14.8.25"
5. Memory erstellen: "Tagebucheintrag 14.8.25" mit Kategorie DIARY, mood: 5, date: "2025-08-14", place: null im Frontmatter
6. Inhalt: Transkribierter Text + Bilder-Abschnitt am Ende:
   ## Bilder
   ![[2025-08-14 1.png]]
   ![[2025-08-14 2.png]]
7. Place identifizieren: "Spinozastraße 15" im Text → Suche nach PLACE-Erinnerung → eindeutig gefunden → verlinken und place: <place-id> setzen
8. Personen: Bethany, Emmett, Emily, Markus → PERSON-Erinnerungen erstellen/verknüpfen
9. Tags: diary, 2025-08-14, hasdrawing (wenn handgemalte Bilder), hasphoto (wenn nicht transkribierte Bilder), families, stresses, jobs, physiotherapies, therapies, [weitere relevante Tags basierend auf Inhalt]
```
