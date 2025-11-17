---
id: d7220fbc-8e20-4953-a56d-68ce414ebe73
title: project-goal
tags:
  - project-goal
  - requirements
  - mvp
  - vision
  - personas
  - hypercortex
  - exocortex
  - template
category: CTX
created_at: '2025-11-13T07:55:33.770Z'
updated_at: '2025-11-13T07:55:33.770Z'
last_reviewed: '2025-11-13T07:55:33.770Z'
links: []
sources: []
abstract: >-
  Hypercortex ist ein Template-Repository für individuelle Exocortex-Projekte.
  Ein Hypercortex ist eine Ansammlung von Exocortexes (externen Gehirnen).
  Informationen werden mittels llm-mem verwaltet und für LLMs aufbereitet.
  Zielgruppe sind Entwickler und nicht-technische Mitarbeiter bei kernpunkt.
---

# Project Goal: Hypercortex

## Summary
Hypercortex ist ein Template-Repository für die Erstellung individueller Exocortex-Projekte. Ein Hypercortex ist eine Ansammlung von Exocortexes (externen Gehirnen). Jeder Exocortex ist ein Memory-Management-System, das Erinnerungen und Informationen mittels `llm-mem` ablegt, indiziert und für LLMs aufbereitet. Nutzer können das Template klonen, ihre eigenen Exocortex-Projekte erstellen, ihre Erinnerungen verwalten und über Pull Requests Wissen zwischen verschiedenen Exocortex-Instanzen teilen.

## Motivation
Ein Exocortex ist eine Sammlung von Informationen, die benötigt werden, um den Job zu machen, speziell aufbereitet für ein LLM. Ein Hypercortex ist eine Ansammlung solcher Exocortexes. Das Problem: Menschen benötigen ein System, um ihr Wissen strukturiert zu speichern und für KI-Assistenten zugänglich zu machen. Bestehende Lösungen sind oft nicht LLM-optimiert oder zu komplex. Hypercortex dient als Template für individuelle Exocortex-Projekte.

**Wertversprechen:**
- **LLM-optimiert**: Informationen sind direkt für KI-Assistenten nutzbar
- **Flexibel**: Template deckt alle Use-Cases ab
- **Kollaborativ**: Wissensaustausch zwischen verschiedenen Instanzen möglich
- **Einfach**: Minimaler Setup-Aufwand durch Template-Ansatz
- **Privat**: Jeder verwaltet seine eigenen Erinnerungen ohne andere zu stören

## User Personas

### Primary Personas

#### Entwickler (Developer)
- **Rolle**: Software-Entwickler, die technische Informationen und Wissen speichern möchten
- **Technische Expertise**: Hoch - vertraut mit Git, Command-Line, Entwicklungstools
- **Ziele**: 
  - Code-Snippets, Architektur-Entscheidungen, API-Dokumentation speichern
  - Technisches Wissen für LLM-Assistenten aufbereiten
  - Entwicklungskontext für bessere KI-Unterstützung bereitstellen
- **Pain Points**: 
  - Wissen ist verstreut in verschiedenen Tools
  - LLMs haben keinen Zugriff auf persönliches Wissen
  - Schwierig, Wissen strukturiert zu organisieren
- **Workflows**: 
  - Nutzt Git und Command-Line täglich
  - Arbeitet mit verschiedenen Entwicklungstools
  - Erstellt und verwaltet technische Dokumentation
- **Erfolgskriterien**: Schneller Zugriff auf relevante Informationen durch LLM-Assistenten, strukturierte Wissenssammlung

#### Nicht-technische Wissensarbeiter (Non-Technical Knowledge Workers)
- **Rolle**: CEOs, Product Owner, Scrum Master, Consultants, Solution Architects bei kernpunkt
- **Technische Expertise**: Niedrig bis Mittel - grundlegende Computerkenntnisse, möglicherweise Git-Basiswissen
- **Ziele**: 
  - Geschäftsprozesse, Meeting-Notizen, Entscheidungen speichern
  - Kundeninformationen und Projektkontext verwalten
  - Wissen für LLM-Assistenten zugänglich machen
- **Pain Points**: 
  - Wissen ist in verschiedenen Dokumenten verstreut
  - Schwierig, Informationen für KI-Assistenten aufzubereiten
  - Keine strukturierte Wissenssammlung
- **Workflows**: 
  - Arbeitet hauptsächlich mit Dokumenten und Notizen
  - Nutzt möglicherweise Git nur für Pull Requests
  - Braucht einfache, intuitive Bedienung
- **Erfolgskriterien**: Einfache Erstellung von Erinnerungen, Zugriff auf relevantes Wissen durch LLM-Assistenten

### Secondary Personas

#### Wissensmanager (Knowledge Manager)
- **Rolle**: Person, die Wissen zwischen verschiedenen Exocortex-Projekten koordiniert
- **Technische Expertise**: Mittel - vertraut mit Git, Pull Requests
- **Ziele**: 
  - Wissen zwischen verschiedenen Instanzen teilen
  - Qualität der geteilten Informationen sicherstellen
  - Wissensaustausch-Prozesse optimieren
- **Pain Points**: 
  - Manuelle Koordination von Pull Requests
  - Schwierig, relevante Informationen zu identifizieren
- **Workflows**: 
  - Erstellt Pull Requests für Wissensaustausch
  - Reviewt und merged Wissens-Updates
- **Erfolgskriterien**: Effizienter Wissensaustausch, hohe Qualität der geteilten Informationen

## MVP (Minimum Viable Product)

### Core Features

1. **Template-Repository Setup**
   - Basis-Konfiguration für `llm-mem`
   - Memory-Konfiguration (memory-config.yaml) mit Kategorien: ADR, DOC, CTX, COMPANY, PERSON, ENDEAVOUR, RAW
   - README mit Setup-Anleitung
   - Beispiel-Konfigurationen

2. **Erinnerungen erstellen und verwalten**
   - Nutzung von `llm-mem` MCP Tools zum Erstellen von Erinnerungen
   - Unterstützung aller Memory-Kategorien (ADR, DOC, CTX, COMPANY, PERSON, ENDEAVOUR, RAW)
   - Indizierung und Suche über `llm-mem`
   - Basis-Dokumentation zur Nutzung

3. **Manueller Wissensaustausch via Pull Requests**
   - Git-basierter Workflow für Wissensaustausch
   - Dokumentation des PR-Prozesses
   - Beispiel-Workflows für Wissensaustausch

4. **Flexible Struktur**
   - Template ist flexibel genug für alle Use-Cases
   - Keine Einschränkungen auf spezifische Informationsarten
   - Erweiterbare Konfiguration

### Success Criteria

- **Funktionalität**: Nutzer können erfolgreich Erinnerungen erstellen und verwalten
- **Usability**: Setup ist für Entwickler einfach, für nicht-technische Nutzer mit minimaler Hilfe möglich
- **Flexibilität**: Template deckt verschiedene Use-Cases ab (technisch und nicht-technisch)
- **Dokumentation**: Ausreichende Dokumentation für Setup und Nutzung vorhanden
- **Wissensaustausch**: Mindestens ein erfolgreicher Wissensaustausch via Pull Request durchgeführt

### Timeline

- **Phase 1**: Template-Setup und Basis-Konfiguration (abgeschlossen)
- **Phase 2**: Dokumentation und Beispiele (in Arbeit)
- **Phase 3**: Erste Nutzer-Tests und Feedback (geplant)
- **Phase 4**: MVP-Release (geplant)

## Full Product Vision

### Extended Functionality

#### Automatischer Wissensaustausch
- **GitHub MCP Integration**: Automatisierung von Wissensaustausch-Prozessen
- **Slash Commands**: Command-basierte Steuerung für Wissensaustausch
- **Intelligente Filterung**: Automatische Identifikation von relevanten Informationen für den Austausch
- **Kategorisierter Austausch**: Wissensaustausch basierend auf Kategorien (z.B. nur COMPANY-Informationen)

#### Erweiterte Suchfunktionen
- **Semantische Suche**: Verbesserte Suche über `llm-mem` FlexSearch
- **Cross-Instance Suche**: Suche über mehrere Exocortex-Projekte hinweg
- **Temporale Suche**: Suche nach Zeiträumen oder Daten

#### Kollaborations-Features
- **Wissens-Graph**: Visualisierung von Verbindungen zwischen Erinnerungen
- **Wissens-Review**: Review-Prozess für geteiltes Wissen
- **Wissens-Versionierung**: Nachverfolgung von Änderungen an Erinnerungen

#### Integrationen
- **IDE-Integration**: Direkte Nutzung in Entwicklungsumgebungen
- **CI/CD Integration**: Automatische Wissens-Updates in Build-Prozessen
- **External Tool Integration**: Anbindung an bestehende Tools (Notion, Obsidian, etc.)

#### Analytics und Insights
- **Wissens-Metriken**: Statistiken über gespeichertes Wissen
- **Coverage-Analyse**: Analyse der Dokumentations-Abdeckung (siehe usage.md)
- **Wissens-Lücken**: Identifikation von fehlenden Informationen

### Future Considerations

#### Skalierung
- **Enterprise-Features**: Multi-User-Support, Berechtigungen, Audit-Logs
- **Performance-Optimierung**: Optimierung für große Wissenssammlungen
- **Cloud-Integration**: Optional Cloud-Backup und Sync

#### Community
- **Wissens-Marktplatz**: Geteiltes Wissen aus verschiedenen Exocortex-Projekten
- **Templates und Vorlagen**: Vorgefertigte Templates für verschiedene Rollen
- **Best Practices**: Sammlung von Best Practices für Wissensmanagement

#### KI-Enhancements
- **Auto-Kategorisierung**: Automatische Kategorisierung von Erinnerungen
- **Wissens-Vorschläge**: KI-basierte Vorschläge für relevante Informationen
- **Zusammenfassungen**: Automatische Zusammenfassungen von Erinnerungen

#### Plattform-Erweiterungen
- **Mobile App**: Mobile Zugriff auf Exocortex
- **Web-Interface**: Web-basierte Verwaltungsoberfläche
- **API**: REST/GraphQL API für externe Integrationen

## Technical Considerations

### Technische Anforderungen

- **llm-mem**: Einzige technische Abhängigkeit für Memory-Management
- **Node.js/TypeScript**: Basis für Tooling und Erweiterungen
- **Git**: Versionierung und Wissensaustausch
- **pnpm**: Paketverwaltung (siehe Workspace Rules)

### Memory-Struktur

Basierend auf usage.md werden folgende Kategorien unterstützt:

- **ADR**: Architecture Decision Records - Architektur-Entscheidungen
- **DOC**: Dokumentation über Features, Business Logic, Edge Cases, Klassen und Funktionen
- **CTX**: Context Memories für LLM-Sessions
- **COMPANY**: Firmen- und Kundeninformationen (ausschließlich über llm-mem verwaltet)
- **PERSON**: Persönliche Kontakte und Beziehungen
- **ENDEAVOUR**: Teilprojekte und Initiativen (ausschließlich über llm-mem verwaltet, mit status und summary Frontmatter)
- **RAW**: Rohe oder unstrukturierte Daten

### Plattform-Unterstützung

- **Entwicklungsumgebungen**: Cursor, VS Code, etc.
- **Betriebssysteme**: macOS, Linux, Windows
- **Git-Hosting**: GitHub, GitLab, etc.

### Performance-Erwartungen

- **Schnelle Suche**: FlexSearch-basierte Suche für schnelle Ergebnisse
- **Skalierbarkeit**: Unterstützung für tausende von Erinnerungen
- **Effiziente Indizierung**: Asynchrone Indizierung für nicht-blockierende Operationen

### Integration-Anforderungen

- **MCP-Server**: Integration mit Model Context Protocol für LLM-Zugriff
- **Git-Integration**: Nahtlose Git-Integration für Wissensaustausch
- **GitHub MCP**: Zukünftige Integration für automatisierte Prozesse

## Success Metrics

### Technische Metriken
- **Setup-Zeit**: < 10 Minuten für Entwickler, < 30 Minuten für nicht-technische Nutzer
- **Performance**: Suche < 200ms für 10.000 Erinnerungen
- **Zuverlässigkeit**: 99%+ Erfolgsrate bei Memory-Operationen

### Nutzungs-Metriken
- **Adoption**: Anzahl aktiver Exocortex-Projekte
- **Engagement**: Durchschnittliche Anzahl von Erinnerungen pro Nutzer
- **Wissensaustausch**: Anzahl erfolgreicher Pull Requests für Wissensaustausch

### Qualitäts-Metriken
- **Dokumentations-Coverage**: Coverage-Analyse basierend auf usage.md
- **Wissens-Qualität**: Review-Scores für geteiltes Wissen
- **Nutzer-Zufriedenheit**: Feedback von Nutzern (technisch und nicht-technisch)

### Business-Impact
- **Produktivitäts-Steigerung**: Zeitersparnis durch besseren Zugriff auf Wissen
- **Wissens-Retention**: Verbesserte Wissensbewahrung in der Organisation
- **KI-Effektivität**: Verbesserte Qualität der LLM-Assistenten durch besseren Kontext
