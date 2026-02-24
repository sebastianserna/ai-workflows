# AGENTS.md

Leitfaden für KI-Agenten, die an diesem Projekt arbeiten.

<!-- Sprache: Definieren Sie hier die Sprache für Agentenantworten und für Code -->

## Stack

<!-- Definieren Sie hier den Technologie-Stack des Projekts. Beispiel:
- Framework:
- UI:
- Backend/DB:
- Sprache:
-->

## Setup und Befehle

<!-- Wesentliche Projektbefehle. Beispiel:
```bash
npm install        # Abhängigkeiten installieren
npm run dev        # Entwicklungsserver
npm run build      # Produktions-Build
npm run lint       # Linter
npm run test       # Tests
```
-->

<!-- Erforderliche Umgebungsvariablen:
- Listen Sie hier die in `.env` benötigten Variablen auf
-->

## Projektstruktur

<!-- Beschreiben Sie die wichtigsten Ordner des Projekts. Beispiel:
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## Code-Konventionen

- Einrückung: 2 Leerzeichen
- Code auf Englisch, Dokumentation und Kommentare auf Deutsch

<!-- Weitere Team-Konventionen hinzufügen. Beispiel:
- Benennung: camelCase für Variablen, PascalCase für Komponenten
- Striktes TypeScript
-->

## Wissensbasis (wisdom/)

Der Ordner `wisdom/` enthält die technische Dokumentation des Projekts. Er ist die maßgebliche Quelle, um zu verstehen, wie das System funktioniert.

Grundstruktur:
- `wisdom/architecture/` — Wie das System aufgebaut ist (Entscheidungen, Muster, Struktur)
- `wisdom/development/` — Wie am Projekt gearbeitet wird (Konventionen, Tests, Workflows)
- `wisdom/operations/` — Wie es bereitgestellt und betrieben wird (CI/CD, Umgebungen, Monitoring)

Zusätzliche Ordner (`database/`, `security/`, `integrations/`) können hinzugefügt werden, wenn das Projekt sie erfordert. Siehe `wisdom/README.md` für die Kriterien.

Agenten sollten `wisdom/` konsultieren, bevor sie Entscheidungen treffen, die bestehende Architektur oder Muster betreffen.

## Planverwaltung (workplan/)

Der Ordner `workplan/` verwaltet den Lebenszyklus der Projektaufgaben.

**Ordner:**
- `backlog/` — Ausstehende Pläne, priorisiert und bearbeitungsbereit
- `coding/` — Pläne in aktiver Bearbeitung
- `done/` — Abgeschlossene Pläne (historisches Archiv)
- `draft/` — Entwürfe, Ideen und Architekturentscheidungen (kein Workflow oder Identifikator)

**Workflow:** `backlog/ -> coding/ -> done/`

**Dateinamenformat:**
- Mit Issue-Tracker: `TYPE-YYYY-MM-DD-iNNNN-description.md`
- Ohne Issue-Tracker: `TYPE-YYYY-MM-DD-description.md`
- TYPE: `BACKLOG`, `CODING`, `DONE`
- iNNNN: GitHub/GitLab Issue-Nummer (wenn der Tracker konfiguriert ist)

Siehe `workplan/README.md` für das vollständige Template und detaillierte Regeln.

## Authentifizierung und Rollen

<!-- Definieren Sie das Authentifizierungs- und Rollensystem. Beispiel:
- Auth-Provider:
- Rollenhierarchie:
- Composable/Funktion für Berechtigungsprüfungen:
-->

## Git-Workflow

- Hauptbranch: `main` (PRs erforderlich)
- Branches: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + Beschreibung auf Englisch
- Commits: Conventional Commits auf Englisch (`feat:`, `fix:`, `docs:`, etc.)
- PRs: Titel auf Englisch (Conventional Commits), Beschreibung/Body auf Deutsch
- Issues: Titel und Beschreibung auf Deutsch
- **Kein** `Co-Authored-By` von KI-Agenten in Commits
- **Keinen** „Generated with Claude Code"-Link in Commit-Nachrichten oder PRs

<!-- Weitere Git-Workflow-Regeln bei Bedarf hinzufügen -->

## Tests

<!-- Definieren Sie die Teststrategie. Beispiel:
- Test-Framework:
- Was getestet werden muss:
- Dateimuster: `*.test.ts` oder `*.spec.ts`
-->

## Geschützte Bereiche (NICHT ändern)

<!-- Listen Sie Dateien oder Ordner auf, die Agenten NICHT ändern dürfen. Beispiel:
| Datei | Grund |
|-------|-------|
| `.env` | Niemals committen |
| `migrations/` (angewendet) | Stattdessen eine neue erstellen |
-->

## Bekannte Stolperfallen

<!-- Dokumentieren Sie bekannte Probleme oder häufige Fallstricke. Beispiel:
- Bug X: Beschreibung und Workaround
- Einschränkung Y: Kontext und temporäre Lösung
-->

## Detaillierte Spezifikationen

<!-- Listen Sie Links zu Referenzdokumenten in wisdom/ auf. Beispiel:
| Dokument | Inhalt |
|----------|--------|
| [wisdom/architecture/...](wisdom/architecture/...) | Systemarchitektur |
| [wisdom/database/...](wisdom/database/...) | DB-Schema und Konventionen |
-->
