# wisdom/ — Base de connaissances

Ce dossier contient la documentation technique du projet. C'est la **source de verite** que les agents IA consultent avant de prendre des decisions.

## Objectif

- Documenter les decisions d'architecture et leurs raisons
- Maintenir les guides techniques a jour
- Empecher les agents de repeter des erreurs ou de prendre des decisions incoherentes
- Preserver le savoir qui ne tient pas dans le code lui-meme

## Structure

```
wisdom/
├── README.md           # Ce fichier
├── architecture/       # Comment le systeme est concu
│   └── AGENTS.md
├── development/        # Comment travailler sur le projet
│   └── AGENTS.md
└── operations/         # Comment il est deploye et opere
    └── AGENTS.md
```

Chaque `AGENTS.md` fournit du contexte aux agents IA sur la portee du dossier et quand le consulter.

### architecture/

Decisions d'architecture, structure du systeme, patterns choisis et leurs raisons. Repond a **« comment est-il concu et pourquoi »**.

Exemples : structure de dossiers, patterns en couches, choix de bibliotheques, diagrammes de composants.

### development/

Guides pour le developpement au quotidien. Repond a **« comment je travaille sur ce projet »**.

Exemples : conventions de code, guide de testing, workflow git, setup local, linting.

### operations/

Tout ce qui concerne la mise en production du code et son bon fonctionnement. Repond a **« comment est-il deploye et opere »**.

Exemples : pipeline CI/CD, configuration des environnements, monitoring, variables d'environnement.

## Quand ajouter plus de dossiers

Les trois dossiers de base couvrent la plupart des projets. Si le projet grandit dans un domaine specifique, ajouter des dossiers dedies :

| Dossier | Quand l'ajouter |
|---------|-----------------|
| `database/` | Le projet a sa propre base de donnees avec des migrations |
| `security/` | Regles d'auth, permissions ou conformite a documenter |
| `integrations/` | Plusieurs APIs externes ou services tiers |
| `api/` | API publique consommee par d'autres |

**Regle :** ne pas creer de dossiers vides « au cas ou ». Les creer quand il y a au moins un document reel a y mettre.

## Conventions

- Documents en Markdown, un sujet par fichier
- Maintenir a jour quand l'architecture change
- Referencer depuis `AGENTS.md` dans la section « Specifications detaillees »

## Difference avec workplan/

| | `wisdom/` | `workplan/` |
|---|-----------|-------------|
| **Contient** | Documentation permanente | Plans de travail avec cycle de vie |
| **Change** | Quand l'architecture evolue | Constamment (backlog -> coding -> done) |
| **Format** | Libre | Modele standardise avec en-tete |
| **Objectif** | Comprendre le systeme | Gerer ce qui doit etre fait |
