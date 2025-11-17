Erstelle ein neues Endeavour (Teilprojekt) mit dem `llm-mem` MCP Tool.

**WICHTIG - Vorgehen:**
1. Verwende IMMER das `write_mem` Tool mit `category: "ENDEAVOUR"`
2. Stelle sicher, dass du folgende Frontmatter-Felder im `template` Parameter setzt:
   - `status`: Einer der folgenden Werte:
     - `active` - Aktives Endeavour, wird aktuell bearbeitet
     - `on-hold` - Endeavour ist pausiert, wird vorübergehend nicht bearbeitet
     - `delegated` - Endeavour wurde an jemand anderen übergeben
     - `archived` - Endeavour ist abgeschlossen oder archiviert
     - `backlog` - Endeavour ist im Backlog, noch nicht gestartet
   - `summary`: Eine kurze Zusammenfassung des Endeavours (1-2 Sätze)
3. Der `summary` muss jedes Mal aktualisiert werden, wenn Änderungen am Endeavour vorgenommen werden
4. Endeavours werden **ausschließlich** in llm-mems verwaltet, NICHT im Dateisystem
5. Verwende aussagekräftige Titel, die das Endeavour klar beschreiben
6. Füge relevante Tags hinzu für bessere Kategorisierung und Suche

**Beispiel-Struktur:**
- Titel sollte das Projekt/Initiative klar benennen
- Content sollte Objective, Timeline, Milestones, Team, Resources, Risks enthalten
- Tags sollten Projekttyp, zugehörige Company (falls vorhanden), Technologien enthalten

**Nach dem Erstellen:**
- Wenn das Endeavour zu einer Company gehört, verlinke es mit der entsprechenden COMPANY-Memory mittels `link_mem`

