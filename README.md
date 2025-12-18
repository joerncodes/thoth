# Hypercortex

![](https://res.cloudinary.com/ddux8vytr/image/upload/w_300/v1763023316/c32xmhrvm5heh4tlhen0.jpg)

Ein Template-System für Exocortex-Projekte, basierend auf [llm-mem](https://github.com/kernpunkt/llm-mem).

## Überblick

Hypercortex ist ein Template-Repository für die Erstellung individueller Exocortex-Projekte. Ein Hypercortex ist eine Ansammlung von Exocortexes (externen Gehirnen). Jeder Exocortex ist ein Memory-Management-System, das KI-Assistenten ermöglicht, Informationen, Erinnerungen und Projekte (Endeavours) strukturiert zu speichern und abzurufen. Es dient als externes Gedächtnis für KI-Workflows und ermöglicht persistente Wissensverwaltung über verschiedene Sessions hinweg.

## Features

- **Memory Management**: Strukturierte Speicherung von Erinnerungen und Informationen
- **Endeavour Tracking**: Verwaltung von Projekten und Teilprojekten mit verschiedenen Stati
- **FlexSearch Integration**: Schnelle Volltextsuche durch alle gespeicherten Memories
- **Kategorisierung**: Organisierte Speicherung mit Kategorien und Tags
- **MCP Integration**: Nahtlose Integration mit Model Context Protocol

## Installation

### Voraussetzungen

- Node.js (Version 18 oder höher)
- pnpm (Paketverwaltung)

### Setup

```bash
# Dependencies installieren
pnpm install
```

### MCP-Server Konfiguration

Das Projekt verwendet mehrere MCP-Server (Model Context Protocol), die in `.cursor/mcp.json` konfiguriert sind:

- **llm-mem**: Memory-Management-Server für die Verwaltung von Erinnerungen und Endeavours
- **github-tools**: GitHub-Integration über GitHub Copilot API

**Wichtig:** Für den `github-tools` Server muss die Datei `.cursor/.env.github-mcp` vorhanden sein. Diese Datei enthält dein GitHub Personal Access Token:

```bash
# Die Datei .cursor/.env.github-mcp muss erstellt werden mit folgendem Inhalt:
GITHUB_PAT=dein_github_personal_access_token
```

Falls du die Konfiguration aus einem anderen Projekt kopiert hast, stelle sicher, dass die `.env.github-mcp` Datei ebenfalls kopiert oder neu erstellt wurde.

## Konfiguration

Die Konfiguration erfolgt über `memory-config.yaml`:

```yaml
frontmatter:
    ENDEAVOUR:
        company: null
        status: "unknown"
    RAW:
        company: null
```

## Verwendung

### Memory Management

Memories werden über das `llm-mem` MCP Tool verwaltet. Alle Endeavours werden ausschließlich in llm-mems gespeichert und haben die Kategorie `ENDEAVOUR`.

### Workflows

Das Projekt unterstützt verschiedene Workflows für:
- Projektziel-Definition
- Endeavour-Verwaltung
- Memory-Erstellung und -Verwaltung
- Persona-Management

## Projektstruktur

```
hypercortex/
├── memory-config.yaml    # Konfiguration für Memory-Frontmatter
├── package.json          # Projekt-Dependencies
├── pnpm-workspace.yaml   # pnpm Workspace-Konfiguration
└── docs/                 # Dokumentation und gespeicherte Memories
```

## Dependencies

- **llm-mem**: Memory-Management-Bibliothek für KI-Assistenten

## Entwicklung

### Paketverwaltung

Dieses Projekt verwendet **pnpm** als Paketverwaltung. Alle Paketoperationen sollten mit `pnpm` durchgeführt werden.

## Lizenz

MIT

## Repository

[GitHub Repository](https://github.com/kernpunkt/hypercortex)

