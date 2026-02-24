# Projektname

Kurze Beschreibung des Projekts.

## Voraussetzungen

<!-- Systemanforderungen auflisten: Node.js, Python, Docker, etc. -->

## Installation

```bash
# Repository klonen
git clone <repo-url>
cd <projektname>

# Abhängigkeiten installieren
# npm install / pip install / etc.

# Umgebungsvariablen einrichten
cp .env.example .env
```

## Entwicklung

```bash
# Entwicklungsserver starten
# npm run dev / python manage.py runserver / etc.
```

## Projektstruktur

```
AGENTS.md               # Anweisungen für KI-Agenten
CLAUDE.md               # Claude Code Konfiguration
README.md               # Diese Datei
wisdom/                 # Wissensbasis (Architektur, Leitfäden)
workplan/               # Arbeitsplanverwaltung
├── backlog/            #   Ausstehende Pläne
├── coding/             #   In Bearbeitung
├── done/               #   Abgeschlossen
└── draft/              #   Entwürfe und Ideen
```

## Arbeiten mit KI-Agenten

Dieses Projekt ist für die Zusammenarbeit mit KI-Agenten wie Claude Code eingerichtet:

- **AGENTS.md** — Vollständiger Leitfaden, damit Agenten das Projekt verstehen
- **CLAUDE.md** — Einstiegspunkt, der beim Start von Claude Code automatisch geladen wird
- **wisdom/** — Technische Dokumentation, die Agenten für Entscheidungen heranziehen
- **workplan/** — Aufgabenverwaltungssystem, das Agenten lesen und aktualisieren können

## Lizenz

<!-- Durch die gewählte Lizenz ersetzen -->
The MIT License (MIT)

Copyright (c) <Jahr> - <Autor>

Der Quellcode in diesem Repository wurde teilweise oder vollständig mit Unterstützung von Werkzeugen der künstlichen Intelligenz erstellt, die auf fortschrittlichen Sprachmodellen (LLMs) wie Claude, GPT, Gemini und anderen basieren. Der Einsatz dieser Werkzeuge wurde vom Autor des Projekts sorgfältig angeleitet und überwacht.
