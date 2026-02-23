# AGENTS.md

Guida per gli agenti IA che lavorano su questo progetto.

<!-- Lingua: definire qui la lingua per le risposte degli agenti e per il codice -->

## Stack

<!-- Definire qui lo stack tecnologico del progetto. Esempio:
- Framework:
- UI:
- Backend/DB:
- Linguaggio:
-->

## Setup e comandi

<!-- Comandi essenziali del progetto. Esempio:
```bash
npm install        # Installare le dipendenze
npm run dev        # Server di sviluppo
npm run build      # Build di produzione
npm run lint       # Linter
npm run test       # Test
```
-->

<!-- Variabili d'ambiente richieste:
- Elencare qui le variabili richieste in `.env`
-->

## Struttura del progetto

<!-- Descrivere la struttura principale delle cartelle del progetto. Esempio:
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## Convenzioni di codice

<!-- Definire le convenzioni del team. Esempio:
- Indentazione: 2 spazi
- Naming: camelCase per le variabili, PascalCase per i componenti
- TypeScript rigoroso
- Codice in inglese, documentazione in inglese
-->

## Base di conoscenza (wisdom/)

La cartella `wisdom/` contiene la documentazione tecnica del progetto. È la fonte di verità per comprendere il funzionamento del sistema.

Struttura base:

- `wisdom/architecture/` — Come il sistema è progettato (decisioni, pattern, struttura)
- `wisdom/development/` — Come lavorare sul progetto (convenzioni, testing, workflow)
- `wisdom/operations/` — Come viene distribuito e gestito (CI/CD, ambienti, monitoraggio)

Cartelle aggiuntive (`database/`, `security/`, `integrations/`) possono essere aggiunte quando il progetto lo richiede. Consultare `wisdom/README.md` per i criteri.

Gli agenti devono consultare `wisdom/` prima di prendere decisioni che impattano l'architettura o i pattern esistenti.

## Gestione dei piani (workplan/)

La cartella `workplan/` gestisce il ciclo di vita delle attività del progetto.

**Cartelle:**
- `backlog/` — Piani in attesa, prioritizzati e pronti per essere lavorati
- `coding/` — Piani in corso di sviluppo
- `done/` — Piani completati (archivio storico)
- `draft/` — Bozze, idee e decisioni architetturali (senza workflow né identificatore)

**Workflow:** `backlog/ -> coding/ -> done/`

**Formato dei nomi file:**
- Con issue tracker: `TIPO-YYYY-MM-DD-iNNNN-descrizione.md`
- Senza issue tracker: `TIPO-YYYY-MM-DD-descrizione.md`
- TIPO: `BACKLOG`, `CODING`, `DONE`
- iNNNN: numero di issue GitHub/GitLab, zero-padded con prefisso `i` (quando il tracker è configurato)

Consultare `workplan/README.md` per il template completo e le regole dettagliate.

## Auth e ruoli

<!-- Definire il sistema di autenticazione e ruoli. Esempio:
- Provider di autenticazione:
- Gerarchia dei ruoli:
- Composable/funzione per il controllo dei permessi:
-->

## Git workflow

<!-- Definire il workflow Git. Esempio:
- Branch principale: `main`
- Branch: `feature/`, `fix/`, `hotfix/`, `docs/` + descrizione
- Commit: Conventional Commits (`feat:`, `fix:`, `docs:`, ecc.)
- PR obbligatorie per il merge su main
-->

## Testing

<!-- Definire la strategia di testing. Esempio:
- Framework di test:
- Cosa deve avere i test:
- Pattern dei file: `*.test.ts` o `*.spec.ts`
-->

## Zone protette (NON modificare)

<!-- Elencare i file o le cartelle che gli agenti NON devono modificare. Esempio:
| File | Motivo |
|------|--------|
| `.env` | Non committare mai |
| `migrations/` (applicate) | Creare una nuova migrazione |
-->

## Problemi noti

<!-- Documentare problemi noti o insidie comuni. Esempio:
- Bug X: descrizione e soluzione temporanea
- Limitazione Y: contesto e soluzione provvisoria
-->

## Specifiche dettagliate

<!-- Elencare i link ai documenti di riferimento in wisdom/. Esempio:
| Documento | Contenuto |
|-----------|-----------|
| [wisdom/architecture/...](wisdom/architecture/...) | Architettura del sistema |
| [wisdom/database/...](wisdom/database/...) | Schema DB e convenzioni |
-->
