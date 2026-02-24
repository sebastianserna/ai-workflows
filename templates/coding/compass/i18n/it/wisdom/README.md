# wisdom/ — Base di conoscenza

Questa cartella contiene la documentazione tecnica del progetto. È la **fonte di verità** che gli agenti IA consultano prima di prendere decisioni.

## Scopo

- Documentare le decisioni architetturali e le loro motivazioni
- Mantenere aggiornate le guide tecniche
- Evitare che gli agenti ripetano errori o prendano decisioni incoerenti
- Preservare la conoscenza che non trova posto nel codice stesso

## Struttura

```
wisdom/
├── README.md           # Questo file
├── architecture/       # Come il sistema è progettato
│   └── AGENTS.md
├── development/        # Come lavorare sul progetto
│   └── AGENTS.md
└── operations/         # Come viene distribuito e gestito
    └── AGENTS.md
```

Ogni `AGENTS.md` fornisce contesto agli agenti IA sull'ambito della cartella e quando consultarla.

### architecture/

Decisioni architetturali, struttura del sistema, pattern adottati e le loro motivazioni. Risponde alla domanda **"come è progettato e perché"**.

Esempi: struttura delle cartelle, pattern dei layer, scelte di librerie, diagrammi dei componenti.

### development/

Guide per lo sviluppo quotidiano. Risponde alla domanda **"come lavoro su questo progetto"**.

Esempi: convenzioni di codice, guida ai test, workflow Git, setup locale, linting.

### operations/

Tutto ciò che riguarda la messa in produzione del codice e il suo mantenimento operativo. Risponde alla domanda **"come viene distribuito e gestito"**.

Esempi: pipeline CI/CD, configurazione degli ambienti, monitoraggio, variabili d'ambiente.

## Quando aggiungere altre cartelle

Le tre cartelle base coprono la maggior parte dei progetti. Se il progetto cresce in un dominio specifico, aggiungere cartelle dedicate:

| Cartella | Quando aggiungerla |
|----------|--------------------|
| `database/` | Il progetto ha un proprio database con migrazioni |
| `security/` | Regole di autenticazione, permessi o compliance da documentare |
| `integrations/` | Molteplici API esterne o servizi di terze parti |
| `api/` | API pubblica consumata da altri |

**Regola:** non creare cartelle vuote "per precauzione". Crearle quando c'è almeno un documento reale da inserire.

## Convenzioni

- Documenti in Markdown, un argomento per file
- Mantenere aggiornati quando l'architettura cambia
- Referenziare da `AGENTS.md` nella sezione "Specifiche dettagliate"

## Differenza rispetto a workplan/

| | `wisdom/` | `workplan/` |
|---|-----------|-------------|
| **Contiene** | Documentazione permanente | Piani di lavoro con ciclo di vita |
| **Cambia** | Quando l'architettura evolve | Costantemente (backlog → coding → done) |
| **Formato** | Libero | Template standardizzato con intestazione |
| **Scopo** | Comprendere il sistema | Gestire ciò che deve essere fatto |
