# Gestione dei piani

> **Questo file è la fonte di verità per la gestione dei piani.** Gli agenti IA devono seguire queste istruzioni quando creano, spostano o modificano piani.

## Configurazione

**Issue tracker:** none
<!-- Opzioni: GitHub | GitLab | none -->
<!-- Per attivare: cambiare in "GitHub" o "GitLab" e configurare il repository -->

**Repository:** `user/repo-name`

## Formato dei nomi file

```
TIPO-YYYY-MM-DD-NNNN-descrizione.md
```

| Segmento | Descrizione | Esempio |
|----------|-------------|---------|
| `TIPO` | Stato: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Data della transizione allo stato attuale | `2026-01-15` |
| `NNNN` | ID sequenziale interno, 4 cifre con zero iniziali | `0001` |
| `descrizione` | Nome breve in kebab-case | `user-auth-setup` |

### ID interno (`NNNN`)

Contatore incrementale specifico del progetto. Per ottenere il prossimo:

1. Trovare il valore `NNNN` più alto in tutte le sottocartelle (`backlog/`, `coding/`, `done/`)
2. Aggiungere 1

L'ID è **permanente** — non cambia anche se lo stato o il nome del piano cambiano.

> **Riservato:** L'ID `0000` è riservato per i file di esempio/template. Il primo piano reale deve usare `0001`.

### Regola sulla data

La data nel nome del file riflette la transizione allo stato attuale:

| Stato | Data nel nome = |
|-------|-----------------|
| BACKLOG | Data di creazione del piano |
| CODING | Data di inizio del lavoro |
| DONE | Data di completamento |

## Struttura delle cartelle

```
workplan/
├── README.md          # Questo file (fonte di verità)
├── backlog/           # Piani in attesa
├── coding/            # Lavori in corso
├── done/              # Piani completati (archivio)
└── draft/             # Bozze, idee e decisioni (senza workflow di stato)
```

## Intestazione standardizzata

```markdown
# Piano: Titolo descrittivo

**Stato:** Backlog | Coding | Done
**Backlog:** 2026-01-15
**Coding:** —
**Done:** —
**Dominio:** generale
**Issue:** —
```

**Regole dell'intestazione:**
- Lo stato deve corrispondere al prefisso del nome file
- Le date registrano quando è avvenuta ogni transizione (`—` se non applicabile)
- **Issue** è `—` se l'issue tracker è configurato come "none"

## Template standard

### Terminologia obbligatoria

| Termine | Utilizzo | Esempio |
|---------|----------|---------|
| **Fase** | Traguardo principale dell'implementazione | Fase 1: MVP, Fase 2: Miglioramenti |
| **Passo** | Elemento concreto nella checklist di avanzamento | `- [ ] Creare migrazione SQL` |

### Ordine delle sezioni

Intestazione → Avanzamento → Obiettivo → Contesto → Implementazione → Verifica → Rischi

Le sezioni opzionali vengono **omesse**, non lasciate vuote.

### Template

```markdown
# Piano: Titolo descrittivo

**Stato:** Backlog
**Backlog:** YYYY-MM-DD
**Coding:** —
**Done:** —
**Dominio:** generale
**Issue:** —

## Avanzamento

### Fase 1: MVP
- [ ] Passo concreto e verificabile
- [ ] Altro passo

### Fase 2: Miglioramenti *(se applicabile)*
- [ ] Passo concreto e verificabile

## Obiettivo

Cosa si vuole ottenere e perché (1-3 paragrafi).

## Contesto *(opzionale)*

Stato attuale, prerequisiti.

## Implementazione

### Fase 1: MVP

Dettaglio tecnico dell'implementazione.

### Fase 2: Miglioramenti *(opzionale)*

## Verifica *(opzionale)*

Passi per validare che il piano sia stato completato correttamente.

## Rischi *(opzionale)*

Solo per piani complessi.
```

### Regole

1. **L'avanzamento viene sempre dopo l'intestazione**, mai alla fine
2. Passi raggruppati per fase (`### Fase N: Nome`)
3. Ogni passo deve essere concreto e verificabile (non generico)
4. Dettaglio tecnico nell'Implementazione, riepilogo nell'Avanzamento
5. Solo "Fase" e "Passo", mai "Stadio"
6. Le sezioni opzionali vengono omesse, non lasciate vuote

## Workflow

### Creare un piano

1. Ottenere il prossimo ID sequenziale (`NNNN`)
2. Creare il file in `backlog/BACKLOG-YYYY-MM-DD-NNNN-descrizione.md`

### Avviare il lavoro

1. Spostare da `backlog/` a `coding/CODING-YYYY-MM-DD-NNNN-descrizione.md` (data = oggi, ID invariato)
2. Aggiornare l'intestazione: `Stato: Coding`, `Coding: YYYY-MM-DD`

### Completare

1. Spostare da `coding/` a `done/DONE-YYYY-MM-DD-NNNN-descrizione.md` (data = oggi)
2. Aggiornare l'intestazione: `Stato: Done`, `Done: YYYY-MM-DD`

### Rimettere in backlog

1. Spostare da `coding/` a `backlog/BACKLOG-YYYY-MM-DD-NNNN-descrizione.md`
2. Aggiornare l'intestazione: `Stato: Backlog`

## Riferimenti incrociati

I piani si referenziano tra loro usando l'**ID interno** (`NNNN`), che è permanente:

```markdown
**Dipendenze:** Piano 0001, Piano 0002
Vedere il piano 0003 per i dettagli.
```

**Regola:** non referenziare mai un piano con il nome completo del file (cambia a ogni transizione). Usare sempre l'ID interno.

## Ottenere il prossimo ID

```bash
# Trovare il NNNN più alto in tutte le sottocartelle
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# Aggiungere 1 al risultato
```

## Bozze

Le bozze sono archiviate in `draft/` con il formato `DRAFT-YYYY-MM-DD-descrizione.md`. Non seguono il workflow BACKLOG→CODING→DONE e non hanno un ID sequenziale. Servono come banca delle idee: bozze di piani, decisioni tecniche, note esplorative. Quando una bozza matura abbastanza, viene promossa a `backlog/` come piano formale.
