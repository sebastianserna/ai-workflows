# Nome del progetto

Breve descrizione del progetto.

## Requisiti

<!-- Elencare i requisiti di sistema: Node.js, Python, Docker, ecc. -->

## Installazione

```bash
# Clonare il repository
git clone <repo-url>
cd <project-name>

# Installare le dipendenze
# npm install / pip install / ecc.

# Configurare le variabili d'ambiente
cp .env.example .env
```

## Sviluppo

```bash
# Avviare il server di sviluppo
# npm run dev / python manage.py runserver / ecc.
```

## Struttura del progetto

```
AGENTS.md               # Istruzioni per gli agenti IA
CLAUDE.md               # Configurazione di Claude Code
README.md               # Questo file
wisdom/                 # Base di conoscenza (architettura, guide)
workplan/               # Gestione del piano di lavoro
├── backlog/            #   Piani in attesa
├── coding/             #   In corso
├── done/               #   Completati
└── draft/              #   Bozze e idee
```

## Lavorare con agenti IA

Questo progetto è configurato per lavorare con agenti IA come Claude Code:

- **AGENTS.md** — Guida completa per permettere agli agenti di comprendere il progetto
- **CLAUDE.md** — Punto di ingresso che si carica automaticamente all'avvio di Claude Code
- **wisdom/** — Documentazione tecnica che gli agenti consultano per prendere decisioni
- **workplan/** — Sistema di gestione delle attività che gli agenti possono leggere e aggiornare

## Licenza

<!-- Sostituire con la licenza scelta -->
The MIT License (MIT)

Copyright (c) <anno> - <autore>

Il codice sorgente di questo repository è stato creato parzialmente o interamente con l'assistenza di strumenti di intelligenza artificiale alimentati da modelli linguistici avanzati (LLMs) come Claude, GPT, Gemini, tra gli altri. L'utilizzo di questi strumenti è stato attentamente guidato e supervisionato dall'autore del progetto.

---

Basato su [Coding Compass](https://github.com/sebastianserna/ai-workflows) v1.0.0
