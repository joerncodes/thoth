Ich gebe dir "rohen" Input. Ich möchte, dass du diesen mittels `llm-mem` Tools als Erinnerung der Category `RAW` aufnimmst. Diese gehören immer zur einer Company.

**WICHTIG - Vorgehen:**
1. Suche ZUERST die Company-Datei im Dateisystem in `Kunden/` oder `Sales/` (z.B. `Sales/Riese + Müller/Riese + Müller.md`)
2. Suche dann die zugehörige COMPANY-Erinnerung (Memory mit `category: COMPANY`) mittels `search_mem` oder `list_mems` mit Filter `category: COMPANY`
3. Der Wikilink in der Frontmatter muss EXAKT dem Dateinamen entsprechen (ohne `.md` Erweiterung)
   - Beispiel: Datei `Sales/Riese + Müller/Riese + Müller.md` → Wikilink: `[[Riese + Müller]]`
   - NICHT den Memory-Titel verwenden, sondern den Dateinamen!
4. Erstelle die RAW-Erinnerung mit `write_mem` und setze die Company-Verknüpfung über den `template` Parameter:
   ```javascript
   template: {
     company: "[[Dateiname ohne .md]]"
   }
   ```
   - Der Key `company` wird als Frontmatter-Feld in der Erinnerung gespeichert
   - Der Wert muss der Wikilink sein (z.B. `"[[Riese + Müller]]"`)
5. Verlinke die RAW-Erinnerung anschließend mittels `link_mem` bidirektional mit der COMPANY-Memory (falls vorhanden).

**KRITISCH:** Die COMPANY-Erinnerung (Memory) MUSS im Frontmatter der RAW-Erinnerung über das `company` Feld verlinkt werden. Dies geschieht über den `template` Parameter beim Erstellen der RAW-Erinnerung.