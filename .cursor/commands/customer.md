Erstelle eine neue COMPANY-Erinnerung (Kunde/Unternehmen) mit dem `llm-mem` MCP Tool.

**WICHTIG - Vorgehen:**
1. Suche ZUERST im llm-mem, ob bereits eine COMPANY-Erinnerung für dieses Unternehmen existiert:
   - Verwende `search_mem` mit Filter `category: COMPANY` oder
   - Verwende `list_mems` mit Filter `category: COMPANY`
2. Wenn bereits eine COMPANY-Erinnerung existiert, frage den Benutzer, ob er diese aktualisieren möchte
3. Wenn keine existiert, erstelle eine neue mit `write_mem` und `category: "COMPANY"`
4. COMPANY-Erinnerungen werden **ausschließlich** in llm-mems verwaltet
5. Verwende aussagekräftige Titel im Format: "<Firmenname> - Customer Profile" oder ähnlich

**Typische Inhalte für COMPANY-Erinnerungen:**
- Company Type, Industry, Location
- Contact Information (Primary Contact, Email, Phone)
- Business Relationship (Status, Contract Start, Annual Revenue, Payment Terms)
- Key Projects (mit Status)
- Notes (Kommunikationspräferenzen, Entscheidungsträger, etc.)

**Nach dem Erstellen:**
- Wenn es zugehörige Personen gibt, verlinke diese mit `link_mem`
- Wenn es zugehörige Endeavours gibt, verlinke diese ebenfalls

**KRITISCH:** 
- Immer zuerst llm-mem durchsuchen, bevor Dateien im Dateisystem gelesen werden
- Wenn du später Dateien im Dateisystem findest, stelle sicher, dass die Erinnerung ebenfalls aktualisiert wird

