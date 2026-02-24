# Regeln: coding/

> Pläne, die aktiv bearbeitet werden.

## Was hier abgelegt wird

- Pläne, die sich aktuell in Bearbeitung befinden
- Nur Pläne, die aktiv implementiert werden

## Benennung

**Mit Issue-Tracker (GitHub / GitLab):**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**Ohne Issue-Tracker:**

```
CODING-YYYY-MM-DD-description.md
```

Das Datum spiegelt den Arbeitsbeginn wider.

## Wichtige Regeln

- Jeder Plan muss YAML Frontmatter mit `state: "coding"` haben (siehe `workplan/README.md` für das Format)
- Fortschritts-Checkboxen aktualisieren, sobald Schritte abgeschlossen sind
- Bei Fertigstellung: nach `done/` verschieben, Präfix in `DONE` umbenennen, Datum und Frontmatter aktualisieren
- Zum Pausieren: zurück nach `backlog/` verschieben, Präfix in `BACKLOG` umbenennen, Frontmatter aktualisieren
- Siehe `workplan/README.md` für die vollständige Referenz

## Siehe auch

- `backlog/RULES.md` — Regeln für ausstehende Pläne
- `done/RULES.md` — Regeln für abgeschlossene Pläne
- `draft/RULES.md` — Regeln für Entwürfe und Ideen
