---
id: 111e9daa-89d4-46b8-b2ff-21541e25fbdf
title: Reflexionen als REFLECTION-Erinnerungen speichern
tags:
  - workflow
  - reflection
  - diary
  - llm-mem
category: CTX
created_at: '2025-12-13T12:46:29.097Z'
updated_at: '2025-12-13T12:46:29.097Z'
last_reviewed: '2025-12-13T12:46:29.097Z'
links: []
sources: []
---

Wenn ich Monatsreflexionen aus Tagebucheinträgen erstelle (über den `/reflect` Befehl), muss ich das Ergebnis immer als REFLECTION-Erinnerung im llm-mem System speichern.

**Wichtig:**
- Verwende `mcp_llm-mem_write_mem` mit der Kategorie `REFLECTION`
- Titel-Format: "Monatsreflexion [Monat] [Jahr]" (z.B. "Monatsreflexion August 2025")
- Tags: `reflection`, `diary`, `[monat]`, `[jahr]`
- Abstract: Der eine Satz, der den Monat zusammenfasst
- Frontmatter: Füge `date` hinzu (Datum des Monatsendes oder aktuelles Datum)

Die Reflexionen werden NICHT als normale Markdown-Dateien gespeichert, sondern ausschließlich als REFLECTION-Erinnerungen im llm-mem System.