Erstelle eine neue PERSON-Erinnerung (Kontakt/Person) mit dem `llm-mem` MCP Tool.

**WICHTIG - Vorgehen:**
1. Suche ZUERST im llm-mem, ob bereits eine PERSON-Erinnerung für diese Person existiert:
   - Verwende `search_mem` mit Filter `category: PERSON` oder
   - Verwende `list_mems` mit Filter `category: PERSON`
2. Wenn bereits eine PERSON-Erinnerung existiert, frage den Benutzer, ob er diese aktualisieren möchte
3. Wenn keine existiert, erstelle eine neue mit `write_mem` und `category: "PERSON"`
4. Verwende aussagekräftige Titel im Format: "<Vorname Nachname> - <Rolle/Bezeichnung>" (z.B. "Anna Schmidt - Technical Contact")

**Typische Inhalte für PERSON-Erinnerungen:**
- Role, Company, Location
- Contact Information (Email, Phone, LinkedIn, etc.)
- Background (Experience, Expertise, Education)
- Communication Preferences (Preferred method, Availability, Response time)
- Working Relationship (Role in decision making, Preferences, Values)
- Notes (Languages, Community involvement, etc.)

**Nach dem Erstellen:**
- Wenn die Person zu einer Company gehört, verlinke sie mit der entsprechenden COMPANY-Memory mittels `link_mem`
- Wenn die Person mit Endeavours verbunden ist, verlinke diese ebenfalls

**Tags:**
- Füge relevante Tags hinzu wie: contact, role (z.B. cto, pm), company-name, etc.

