# Gestione dei piani

> **Questo file è la fonte di verità per la gestione dei piani.** Gli agenti IA devono seguire queste istruzioni quando creano, spostano o modificano piani.

## Configurazione

**Issue tracker:** none
<!-- Opzioni: GitHub | GitLab | none -->
<!-- Per attivare: cambiare in "GitHub" o "GitLab" e configurare il repository -->

**Repository:** `user/repo-name`

## Formato dei nomi file

Il formato dipende dalla configurazione dell'issue tracker:

**Con issue tracker (GitHub / GitLab):**

```
TIPO-YYYY-MM-DD-iNNNN-descrizione.md
```

**Senza issue tracker (none):**

```
TIPO-YYYY-MM-DD-descrizione.md
```

| Segmento | Descrizione | Esempio |
|----------|-------------|---------|
| `TIPO` | Stato: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Data della transizione allo stato attuale | `2026-01-15` |
| `iNNNN` | Numero di issue, 4 cifre con zero iniziali e prefisso `i` (solo con tracker) | `i0060` |
| `descrizione` | Nome breve in kebab-case | `user-auth-setup` |

### Identificatore di issue (`iNNNN`)

Quando è configurato un issue tracker (GitHub o GitLab), ogni piano **deve** avere un issue corrispondente. Il numero di issue diventa l'identificatore unico del piano:

- Il prefisso `i` distingue il numero di issue da altri segmenti numerici
- Zero-padded a 4 cifre: issue #7 → `i0007`, issue #123 → `i0123`
- L'identificatore è **permanente** — non cambia quando il piano viene spostato tra gli stati
- GitHub/GitLab garantisce unicità atomica, eliminando i rischi di collisione in ambienti collaborativi

**Quando l'issue tracker è "none"**, i piani non hanno un segmento identificatore. Il nome del file è semplicemente `TIPO-YYYY-MM-DD-descrizione.md`.

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
│   └── RULES.md
├── coding/            # Lavori in corso
│   └── RULES.md
├── done/              # Piani completati (archivio)
│   └── RULES.md
└── draft/             # Bozze, idee e decisioni (senza workflow di stato)
    └── RULES.md
```

Ogni `RULES.md` contiene regole e convenzioni di nomenclatura specifiche della cartella:

- `backlog/RULES.md` — Punto di ingresso per nuovi piani, istruzioni per la creazione di issue
- `coding/RULES.md` — Lavoro attivo, regole di transizione e avanzamento
- `done/RULES.md` — Archivio, criteri di completamento
- `draft/RULES.md` — Banca delle idee, senza workflow, senza identificatore di issue

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
- Quando il tracker è attivo, **Issue** contiene il link all'issue: `[#60](https://github.com/user/repo/issues/60)`

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

**Con issue tracker:**

1. Creare prima l'issue: `gh issue create` (GitHub) o `glab issue create` (GitLab)
2. Annotare il numero di issue (es. #60)
3. Creare il file in `backlog/BACKLOG-YYYY-MM-DD-iNNNN-descrizione.md` (es. `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Compilare il campo `Issue` dell'intestazione con il link

**Senza issue tracker:**

1. Creare il file in `backlog/BACKLOG-YYYY-MM-DD-descrizione.md`

### Avviare il lavoro

1. Spostare da `backlog/` a `coding/CODING-YYYY-MM-DD-...-descrizione.md` (data = oggi, identificatore invariato)
2. Aggiornare l'intestazione: `Stato: Coding`, `Coding: YYYY-MM-DD`

### Completare

1. Spostare da `coding/` a `done/DONE-YYYY-MM-DD-...-descrizione.md` (data = oggi)
2. Aggiornare l'intestazione: `Stato: Done`, `Done: YYYY-MM-DD`

### Rimettere in backlog

1. Spostare da `coding/` a `backlog/BACKLOG-YYYY-MM-DD-...-descrizione.md`
2. Aggiornare l'intestazione: `Stato: Backlog`

## Riferimenti incrociati

**Con issue tracker:** i piani si referenziano tra loro usando il numero di issue con `#N`, che è permanente e abilita l'auto-linking:

```markdown
**Dipendenze:** #1, #2

Vedere #3 per i dettagli.
```

**Senza issue tracker:** referenziare i piani con il loro nome descrittivo:

```markdown
**Dipendenze:** user-auth-setup, api-rate-limiting
```

**Regola:** non referenziare mai un piano con il nome completo del file (cambia a ogni transizione).

## Bozze

Le bozze sono archiviate in `draft/` con il formato `DRAFT-YYYY-MM-DD-descrizione.md`. Non seguono il workflow BACKLOG→CODING→DONE e non hanno un identificatore di issue. Servono come banca delle idee: bozze di piani, decisioni tecniche, note esplorative. Quando una bozza matura abbastanza, viene promossa a `backlog/` come piano formale.
