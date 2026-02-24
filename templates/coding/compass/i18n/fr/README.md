# Nom du projet

Description breve du projet.

## Prerequis

<!-- Lister les prerequis systeme : Node.js, Python, Docker, etc. -->

## Installation

```bash
# Cloner le depot
git clone <url-du-repo>
cd <nom-du-projet>

# Installer les dependances
# npm install / pip install / etc.

# Configurer les variables d'environnement
cp .env.example .env
```

## Developpement

```bash
# Demarrer le serveur de developpement
# npm run dev / python manage.py runserver / etc.
```

## Structure du projet

```
AGENTS.md               # Instructions pour les agents IA
CLAUDE.md               # Configuration de Claude Code
README.md               # Ce fichier
wisdom/                 # Base de connaissances (architecture, guides)
workplan/               # Gestion des plans de travail
├── backlog/            #   Plans en attente
├── coding/             #   En cours
├── done/               #   Termines
└── draft/              #   Brouillons et idees
```

## Travail avec des agents IA

Ce projet est configure pour fonctionner avec des agents IA comme Claude Code :

- **AGENTS.md** — Guide complet pour que l'agent comprenne le projet
- **CLAUDE.md** — Point d'entree charge automatiquement au demarrage de Claude Code
- **wisdom/** — Documentation technique consultee par l'agent pour la prise de decision
- **workplan/** — Systeme de gestion des taches que l'agent peut lire et mettre a jour

## Licence

<!-- Remplacer par la licence choisie -->
The MIT License (MIT)

Copyright (c) <annee> - <auteur>

Le code source de ce depot a ete cree partiellement ou entierement avec l'aide d'outils d'intelligence artificielle alimentes par des modeles de langage avances (LLMs) tels que Claude, GPT, Gemini, entre autres. L'utilisation de ces outils a ete soigneusement guidee et supervisee par l'auteur du projet.
