# Planverwaltung

> **Diese Datei ist die maßgebliche Quelle für die Planverwaltung.** KI-Agenten müssen diesen Anweisungen folgen, wenn sie Pläne erstellen, verschieben oder ändern.

## Konfiguration

**Issue-Tracker:** none
<!-- Optionen: GitHub | GitLab | none -->
<!-- Zum Aktivieren: ändern Sie zu „GitHub" oder „GitLab" und konfigurieren Sie das Repository -->

**Repository:** `benutzer/repo-name`

## Dateinamenformat

```
TYPE-YYYY-MM-DD-NNNN-description.md
```

| Segment | Beschreibung | Beispiel |
|---------|-------------|---------|
| `TYPE` | Status: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Datum des Übergangs zum aktuellen Status | `2026-01-15` |
| `NNNN` | Interne sequenzielle ID, 4 Ziffern mit führenden Nullen | `0001` |
| `description` | Kurzer Name in kebab-case | `user-auth-setup` |

### Interne ID (`NNNN`)

Projektspezifischer inkrementeller Zähler. Um die nächste zu erhalten:

1. Finden Sie die höchste `NNNN` in allen Unterordnern (`backlog/`, `coding/`, `done/`)
2. Addieren Sie 1

Die ID ist **permanent** — sie ändert sich nicht, auch wenn Status oder Name des Plans geändert werden.

> **Reserviert:** ID `0000` ist für Beispiel-/Template-Dateien reserviert. Der erste echte Plan muss `0001` verwenden.

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
├── coding/            # In Bearbeitung
├── done/              # Abgeschlossene Pläne (Archiv)
└── draft/             # Entwürfe, Ideen und Entscheidungen (kein Status-Workflow)
```

## Standardisierter Header

```markdown
# Plan: Beschreibender Titel

**Status:** Backlog | Coding | Done
**Backlog:** 2026-01-15
**Coding:** —
**Done:** —
**Bereich:** allgemein
**Issue:** —
```

**Header-Regeln:**
- Der Status muss mit dem Dateinamen-Präfix übereinstimmen
- Daten erfassen, wann jeder Übergang stattfand (`—` wenn nicht zutreffend)
- **Issue** ist `—`, wenn der Issue-Tracker als „none" konfiguriert ist

## Standard-Template

### Erforderliche Terminologie

| Begriff | Verwendung | Beispiel |
|---------|-----------|---------|
| **Phase** | Wichtiger Implementierungsmeilenstein | Phase 1: MVP, Phase 2: Verbesserungen |
| **Schritt** | Konkreter Punkt in der Fortschrittscheckliste | `- [ ] SQL-Migration erstellen` |

### Abschnittsreihenfolge

Header → Fortschritt → Ziel → Kontext → Umsetzung → Überprüfung → Risiken

Optionale Abschnitte werden **weggelassen**, nicht leer gelassen.

### Template

```markdown
# Plan: Beschreibender Titel

**Status:** Backlog
**Backlog:** YYYY-MM-DD
**Coding:** —
**Done:** —
**Bereich:** allgemein
**Issue:** —

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

1. **Fortschritt immer nach dem Header**, niemals am Ende
2. Schritte nach Phasen gruppiert (`### Phase N: Name`)
3. Jeder Schritt muss konkret und überprüfbar sein (nicht generisch)
4. Technische Details in der Umsetzung, Zusammenfassung im Fortschritt
5. Nur „Phase" und „Schritt" verwenden
6. Optionale Abschnitte werden weggelassen, nicht leer gelassen

## Workflow

### Plan erstellen

1. Die nächste sequenzielle ID (`NNNN`) ermitteln
2. Datei erstellen in `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`

### Arbeit beginnen

1. Von `backlog/` nach `coding/CODING-YYYY-MM-DD-NNNN-description.md` verschieben (Datum = heute, ID unverändert)
2. Header aktualisieren: `Status: Coding`, `Coding: YYYY-MM-DD`

### Abschließen

1. Von `coding/` nach `done/DONE-YYYY-MM-DD-NNNN-description.md` verschieben (Datum = heute)
2. Header aktualisieren: `Status: Done`, `Done: YYYY-MM-DD`

### Zurück zum Backlog

1. Von `coding/` nach `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md` verschieben
2. Header aktualisieren: `Status: Backlog`

## Querverweise

Pläne referenzieren sich gegenseitig über die **interne ID** (`NNNN`), die permanent ist:

```markdown
**Abhängigkeiten:** Plan 0001, Plan 0002

Siehe Plan 0003 für Details.
```

**Regel:** Referenzieren Sie einen Plan niemals über seinen vollständigen Dateinamen (er ändert sich bei jedem Übergang). Verwenden Sie immer die interne ID.

## Nächste ID ermitteln

```bash
# Die höchste NNNN in allen Unterordnern finden
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# 1 zum Ergebnis addieren
```

## Entwürfe

Entwürfe werden in `draft/` im Format `DRAFT-YYYY-MM-DD-description.md` gespeichert. Sie folgen nicht dem BACKLOG→CODING→DONE-Workflow und haben keine sequenzielle ID. Sie dienen als Ideenbank: Planentwürfe, technische Entscheidungen, explorative Notizen. Wenn ein Entwurf ausgereift genug ist, wird er als formaler Plan in `backlog/` befördert.
