# Planverwaltung

> **Diese Datei ist die maßgebliche Quelle für die Planverwaltung.** KI-Agenten müssen diesen Anweisungen folgen, wenn sie Pläne erstellen, verschieben oder ändern.

## Konfiguration

**Issue-Tracker:** none
<!-- Optionen: GitHub | GitLab | none -->
<!-- Zum Aktivieren: ändern Sie zu „GitHub" oder „GitLab" und konfigurieren Sie das Repository -->

**Repository:** `benutzer/repo-name`

## Dateinamenformat

Das Format hängt davon ab, ob ein Issue-Tracker konfiguriert ist:

**Mit Issue-Tracker (GitHub / GitLab):**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**Ohne Issue-Tracker (none):**

```
TYPE-YYYY-MM-DD-description.md
```

| Segment | Beschreibung | Beispiel |
|---------|-------------|---------|
| `TYPE` | Status: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Datum des Übergangs zum aktuellen Status | `2026-01-15` |
| `iNNNN` | Issue-Nummer, 4 Ziffern mit führenden Nullen und `i`-Präfix (nur mit Tracker) | `i0060` |
| `description` | Kurzer Name in kebab-case | `user-auth-setup` |

### Issue-Identifikator (`iNNNN`)

Wenn ein Issue-Tracker konfiguriert ist (GitHub oder GitLab), **muss** jeder Plan ein entsprechendes Issue haben. Die Issue-Nummer wird zum eindeutigen Identifikator des Plans:

- Das `i`-Präfix unterscheidet die Issue-Nummer von anderen numerischen Segmenten
- Mit führenden Nullen auf 4 Ziffern aufgefüllt: Issue #7 → `i0007`, Issue #123 → `i0123`
- Der Identifikator ist **permanent** — er ändert sich nicht, wenn der Plan zwischen Status verschoben wird
- GitHub/GitLab garantiert atomare Eindeutigkeit und eliminiert Kollisionsrisiken in kollaborativen Umgebungen

**Wenn der Issue-Tracker als „none" konfiguriert ist**, haben Pläne kein Identifikator-Segment. Der Dateiname ist einfach `TYPE-YYYY-MM-DD-description.md`.

### Datumsregel

Das Datum im Dateinamen spiegelt den Übergang zum aktuellen Status wider:

| Status | Datum im Namen = |
|--------|-----------------|
| BACKLOG | Datum der Planerstellung |
| CODING | Datum des Arbeitsbeginns |
| DONE | Datum der Fertigstellung |

## Ordnerstruktur

```
workplan/
├── README.md          # Diese Datei (maßgebliche Quelle)
├── backlog/           # Ausstehende Pläne
│   └── RULES.md
├── coding/            # In Bearbeitung
│   └── RULES.md
├── done/              # Abgeschlossene Pläne (Archiv)
│   └── RULES.md
└── draft/             # Entwürfe, Ideen und Entscheidungen (kein Status-Workflow)
    └── RULES.md
```

Jede `RULES.md` enthält ordnerspezifische Regeln und Benennungskonventionen:

- `backlog/RULES.md` — Einstiegspunkt für neue Pläne, Anleitung zur Issue-Erstellung
- `coding/RULES.md` — Aktive Arbeit, Übergangs- und Fortschrittsregeln
- `done/RULES.md` — Archiv, Abschlusskriterien
- `draft/RULES.md` — Ideenbank, kein Workflow, kein Issue-Identifikator

## YAML Frontmatter

Jede Plandatei muss mit einem YAML-Frontmatter-Block auf **Zeile 1** beginnen (keine Leerzeilen vor dem öffnenden `---`). GitHub rendert dies als Metadatentabelle.

```yaml
---
plan: "Beschreibender Titel"
state: "backlog"
issue: ""
domain: "general"
backlog: "2026-01-15"
coding: ""
done: ""
---
```

**Frontmatter-Felder:**

| Feld | Beschreibung | Werte |
|------|-------------|-------|
| `plan` | Kurzer beschreibender Titel | Freitext |
| `state` | Aktueller Status (muss mit dem Dateinamen-Präfix übereinstimmen) | `backlog`, `coding`, `done`, `draft` |
| `issue` | Issue-Identifikator (`iNNNN`) oder leer | `"i0060"`, `""` |
| `domain` | Funktionale Domäne | `general`, oder projektspezifisch |
| `backlog` | Datum der Planerstellung | `"2026-01-15"`, `""` |
| `coding` | Datum des Arbeitsbeginns | `"2026-01-20"`, `""` |
| `done` | Datum der Fertigstellung | `"2026-02-01"`, `""` |

**Frontmatter-Regeln:**
- Das erste `---` muss genau auf Zeile 1 stehen, ohne Leerzeilen davor
- Der `state`-Wert muss mit dem Dateinamen-Präfix übereinstimmen (Kleinbuchstaben)
- **issue** ist `""`, wenn der Issue-Tracker als „none" konfiguriert ist
- Wenn der Tracker aktiv ist, enthält **issue** den Identifikator: `"i0060"`
- Entwürfe lassen die `issue`- und Datumsfelder ganz weg
- Datumsfelder erfassen, wann jeder Übergang stattfand (`""` wenn noch nicht erreicht)

## Standard-Template

### Erforderliche Terminologie

| Begriff | Verwendung | Beispiel |
|---------|-----------|---------|
| **Phase** | Wichtiger Implementierungsmeilenstein | Phase 1: MVP, Phase 2: Verbesserungen |
| **Schritt** | Konkreter Punkt in der Fortschrittscheckliste | `- [ ] SQL-Migration erstellen` |

### Abschnittsreihenfolge

Frontmatter → Fortschritt → Ziel → Kontext → Umsetzung → Überprüfung → Risiken

Optionale Abschnitte werden **weggelassen**, nicht leer gelassen.

### Template

```markdown
---
plan: "Beschreibender Titel"
state: "backlog"
issue: ""
domain: "general"
backlog: "YYYY-MM-DD"
coding: ""
done: ""
---

## Fortschritt

### Phase 1: MVP
- [ ] Konkreter, überprüfbarer Schritt
- [ ] Weiterer Schritt

### Phase 2: Verbesserungen *(falls zutreffend)*
- [ ] Konkreter, überprüfbarer Schritt

## Ziel

Was erreicht werden soll und warum (1-3 Absätze).

## Kontext *(optional)*

Aktueller Stand, Voraussetzungen.

## Umsetzung

### Phase 1: MVP

Technische Details der Umsetzung.

### Phase 2: Verbesserungen *(optional)*

## Überprüfung *(optional)*

Schritte zur Validierung, dass der Plan korrekt abgeschlossen wurde.

## Risiken *(optional)*

Nur für komplexe Pläne.
```

### Regeln

1. **Fortschritt immer nach dem Frontmatter**, niemals am Ende
2. Schritte nach Phasen gruppiert (`### Phase N: Name`)
3. Jeder Schritt muss konkret und überprüfbar sein (nicht generisch)
4. Technische Details in der Umsetzung, Zusammenfassung im Fortschritt
5. Nur „Phase" und „Schritt" verwenden
6. Optionale Abschnitte werden weggelassen, nicht leer gelassen

## Workflow

### Plan erstellen

**Mit Issue-Tracker:**

1. Zuerst das Issue erstellen: `gh issue create` (GitHub) oder `glab issue create` (GitLab)
2. Die Issue-Nummer notieren (z.B. #60)
3. Datei erstellen in `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` (z.B. `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Das `issue`-Frontmatter-Feld mit dem Identifikator ausfüllen

**Ohne Issue-Tracker:**

1. Datei erstellen in `backlog/BACKLOG-YYYY-MM-DD-description.md`

### Arbeit beginnen

1. Von `backlog/` nach `coding/CODING-YYYY-MM-DD-...-description.md` verschieben (Datum = heute, Identifikator unverändert)
2. Frontmatter aktualisieren: `state: "coding"`, `coding: "YYYY-MM-DD"`

### Abschließen

1. Von `coding/` nach `done/DONE-YYYY-MM-DD-...-description.md` verschieben (Datum = heute)
2. Frontmatter aktualisieren: `state: "done"`, `done: "YYYY-MM-DD"`

### Zurück zum Backlog

1. Von `coding/` nach `backlog/BACKLOG-YYYY-MM-DD-...-description.md` verschieben
2. Frontmatter aktualisieren: `state: "backlog"`, `coding: ""`

## Querverweise

**Mit Issue-Tracker:** Pläne referenzieren sich gegenseitig über die Issue-Nummer mit `#N`, die permanent ist und automatische Verlinkung ermöglicht:

```markdown
**Abhängigkeiten:** #1, #2

Siehe #3 für Details.
```

**Ohne Issue-Tracker:** Referenzieren Sie Pläne über ihren beschreibenden Namen:

```markdown
**Abhängigkeiten:** user-auth-setup, api-rate-limiting
```

**Regel:** Referenzieren Sie einen Plan niemals über seinen vollständigen Dateinamen (er ändert sich bei jedem Übergang).

## Entwürfe

Entwürfe werden in `draft/` im Format `DRAFT-YYYY-MM-DD-description.md` gespeichert. Sie folgen nicht dem BACKLOG→CODING→DONE-Workflow und haben keinen Issue-Identifikator. Sie dienen als Ideenbank: Planentwürfe, technische Entscheidungen, explorative Notizen. Wenn ein Entwurf ausgereift genug ist, wird er als formaler Plan in `backlog/` befördert.
