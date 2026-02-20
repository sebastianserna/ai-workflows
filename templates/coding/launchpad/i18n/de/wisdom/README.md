# wisdom/ — Wissensbasis

Dieser Ordner enthält die technische Dokumentation des Projekts. Er ist die **maßgebliche Quelle**, die KI-Agenten vor Entscheidungen konsultieren.

## Zweck

- Architekturentscheidungen und ihre Begründungen dokumentieren
- Technische Leitfäden aktuell halten
- Verhindern, dass Agenten Fehler wiederholen oder inkonsistente Entscheidungen treffen
- Wissen bewahren, das nicht in den Code selbst passt

## Struktur

```
wisdom/
├── README.md           # Diese Datei
├── architecture/       # Wie das System aufgebaut ist
├── development/        # Wie am Projekt gearbeitet wird
└── operations/         # Wie es bereitgestellt und betrieben wird
```

### architecture/

Architekturentscheidungen, Systemstruktur, gewählte Muster und ihre Begründungen. Beantwortet **„wie ist es aufgebaut und warum"**.

Beispiele: Ordnerstruktur, Schichtenmuster, Bibliotheksentscheidungen, Komponentendiagramme.

### development/

Leitfäden für die tägliche Entwicklung. Beantwortet **„wie arbeite ich an diesem Projekt"**.

Beispiele: Code-Konventionen, Testleitfaden, Git-Workflow, lokales Setup, Linting.

### operations/

Alles rund um die Bereitstellung in Produktion und den laufenden Betrieb. Beantwortet **„wie wird es bereitgestellt und betrieben"**.

Beispiele: CI/CD-Pipeline, Umgebungskonfiguration, Monitoring, Umgebungsvariablen.

## Wann weitere Ordner hinzufügen

Die drei Basisordner decken die meisten Projekte ab. Wenn das Projekt in einem bestimmten Bereich wächst, fügen Sie dedizierte Ordner hinzu:

| Ordner | Wann hinzufügen |
|--------|-----------------|
| `database/` | Das Projekt hat eine eigene Datenbank mit Migrationen |
| `security/` | Auth-Regeln, Berechtigungen oder Compliance zu dokumentieren |
| `integrations/` | Mehrere externe APIs oder Drittanbieter-Dienste |
| `api/` | Öffentliche API, die von anderen genutzt wird |

**Regel:** Erstellen Sie keine leeren Ordner „auf Vorrat". Erstellen Sie sie erst, wenn mindestens ein echtes Dokument hineingehört.

## Konventionen

- Dokumente in Markdown, ein Thema pro Datei
- Aktuell halten, wenn sich die Architektur ändert
- Referenzieren aus `AGENTS.md` im Abschnitt „Detaillierte Spezifikationen"

## Unterschied zu workplan/

| | `wisdom/` | `workplan/` |
|---|-----------|-------------|
| **Enthält** | Permanente Dokumentation | Arbeitspläne mit Lebenszyklus |
| **Ändert sich** | Wenn die Architektur sich weiterentwickelt | Ständig (backlog → coding → done) |
| **Format** | Freiform | Standardisiertes Template mit Header |
| **Zweck** | Das System verstehen | Verwalten, was zu tun ist |
