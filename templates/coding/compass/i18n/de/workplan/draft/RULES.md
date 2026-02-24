# Regeln: draft/

> Entwürfe sind eine Ideenbank: Planentwürfe, technische Entscheidungen, explorative Notizen.

## Was hier abgelegt wird

- Frühe Ideen, die noch nicht für den Backlog bereit sind
- Aufzeichnungen technischer Entscheidungen
- Explorative Notizen und Recherchen

## Benennung

```
DRAFT-YYYY-MM-DD-description.md
```

Entwürfe tragen **niemals** einen Issue-Identifikator, unabhängig von der Tracker-Konfiguration.

## Wichtige Regeln

- Jeder Entwurf muss YAML Frontmatter mit `state: "draft"` haben (siehe `workplan/README.md` für das Format)
- Entwürfe folgen **nicht** dem BACKLOG → CODING → DONE-Workflow
- Wenn ein Entwurf ausgereift ist, wird er als formaler Plan in `backlog/` befördert
- Siehe `workplan/README.md` für die vollständige Referenz

## Siehe auch

- `backlog/RULES.md` — Regeln für ausstehende Pläne
- `coding/RULES.md` — Regeln für Pläne in Bearbeitung
- `done/RULES.md` — Regeln für abgeschlossene Pläne
