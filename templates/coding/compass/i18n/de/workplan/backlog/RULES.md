# Regeln: backlog/

> Ausstehende Pläne, die auf Bearbeitung warten.

## Was hier abgelegt wird

- Pläne, die definiert und startbereit sind (oder auf Priorisierung warten)
- Neue Pläne werden hier nach der Erstellung eingetragen

## Benennung

**Mit Issue-Tracker (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**Ohne Issue-Tracker:**

```
BACKLOG-YYYY-MM-DD-description.md
```

Das Datum spiegelt den Zeitpunkt der Planerstellung wider.

## Wichtige Regeln

- Jeder Plan muss den standardisierten Header mit `Status: Backlog` haben
- **Wenn ein Issue-Tracker konfiguriert ist**, erstellen Sie zuerst das Issue (`gh issue create`, `glab issue create`, etc.) und verwenden Sie die Issue-Nummer im Dateinamen (`iNNNN`)
- Zum Starten: nach `coding/` verschieben, Präfix in `CODING` umbenennen, Datum und Header aktualisieren
- Pläne können auch von `coding/` hierher zurückgebracht werden, wenn sie pausiert werden
- Siehe `workplan/README.md` für die vollständige Referenz

## Siehe auch

- `coding/RULES.md` — Regeln für Pläne in Bearbeitung
- `done/RULES.md` — Regeln für abgeschlossene Pläne
- `draft/RULES.md` — Regeln für Entwürfe und Ideen
