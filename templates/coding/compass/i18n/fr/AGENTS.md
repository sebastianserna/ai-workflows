# AGENTS.md

Guide pour les agents IA travaillant sur ce projet.

<!-- Langue : definir ici la langue pour les reponses de l'agent et pour le code -->

## Stack

<!-- Definir le stack technologique du projet ici. Exemple :
- Framework :
- UI :
- Backend/DB :
- Langage :
-->

## Setup et commandes

<!-- Commandes essentielles du projet. Exemple :
```bash
npm install        # Installer les dependances
npm run dev        # Serveur de developpement
npm run build      # Build de production
npm run lint       # Linter
npm run test       # Tests
```
-->

<!-- Variables d'environnement requises :
- Lister ici les variables requises dans `.env`
-->

## Structure du projet

<!-- Decrire la structure de dossiers principale du projet. Exemple :
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## Conventions de code

- Indentation : 2 espaces
- Code en anglais, documentation et commentaires en français

<!-- Ajouter d'autres conventions d'equipe. Exemple :
- Nommage : camelCase pour les variables, PascalCase pour les composants
- TypeScript strict
-->

## Base de connaissances (wisdom/)

Le dossier `wisdom/` contient la documentation technique du projet. C'est la source de verite pour comprendre le fonctionnement du systeme.

Structure de base :
- `wisdom/architecture/` — Comment le systeme est concu (decisions, patterns, structure)
- `wisdom/development/` — Comment travailler sur le projet (conventions, testing, workflows)
- `wisdom/operations/` — Comment il est deploye et opere (CI/CD, environnements, monitoring)

Des dossiers supplementaires (`database/`, `security/`, `integrations/`) peuvent etre ajoutes selon les besoins du projet. Voir `wisdom/README.md` pour les criteres.

Les agents doivent consulter `wisdom/` avant de prendre des decisions qui affectent l'architecture ou les patterns existants.

## Gestion des plans (workplan/)

Le dossier `workplan/` gere le cycle de vie des taches du projet.

**Dossiers :**
- `backlog/` — Plans en attente, priorises et prets a travailler
- `coding/` — Plans en cours de progression active
- `done/` — Plans termines (archive historique)
- `draft/` — Brouillons, idees et decisions d'architecture (sans workflow ni identifiant)

**Workflow :** `backlog/ -> coding/ -> done/`

**Format de nom de fichier :**
- Avec issue tracker : `TYPE-YYYY-MM-DD-iNNNN-description.md`
- Sans issue tracker : `TYPE-YYYY-MM-DD-description.md`
- TYPE : `BACKLOG`, `CODING`, `DONE`
- iNNNN : numero d'issue GitHub/GitLab, zero-padded avec prefixe `i` (lorsque le tracker est configure)

Consulter `workplan/README.md` pour le modele complet et les regles detaillees.

## Auth et roles

<!-- Definir le systeme d'authentification et de roles. Exemple :
- Fournisseur d'auth :
- Hierarchie des roles :
- Composable/fonction pour la verification des permissions :
-->

## Git workflow

- Branche principale : `main` (PRs obligatoires)
- Branches : `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + description en anglais
- Commits : Conventional Commits en anglais (`feat:`, `fix:`, `docs:`, etc.)
- PRs : titre en anglais (Conventional Commits), description/body en français
- Issues : titre et description en français
- **Ne pas inclure** `Co-Authored-By` des agents IA dans les commits
- **Ne pas inclure** le lien « Generated with Claude Code » dans les messages de commit ou PRs

<!-- Ajouter d'autres regles de workflow Git si necessaire -->

## Testing

<!-- Definir la strategie de testing. Exemple :
- Framework de tests :
- Ce qui doit avoir des tests :
- Pattern de fichiers : `*.test.ts` ou `*.spec.ts`
-->

## Zones protegees (NE PAS modifier)

<!-- Lister les fichiers ou dossiers que les agents NE doivent PAS modifier. Exemple :
| Fichier | Raison |
|---------|--------|
| `.env` | Ne jamais commiter |
| `migrations/` (appliquees) | Creer une nouvelle a la place |
-->

## Problemes connus

<!-- Documenter les problemes connus ou les pieges courants. Exemple :
- Bug X : description et contournement
- Limitation Y : contexte et solution temporaire
-->

## Specifications detaillees

<!-- Lister les liens vers les documents de reference dans wisdom/. Exemple :
| Document | Contenu |
|----------|---------|
| [wisdom/architecture/...](wisdom/architecture/...) | Architecture du systeme |
| [wisdom/database/...](wisdom/database/...) | Schema et conventions DB |
-->
