# Gestion des plans

> **Ce fichier est la source de verite pour la gestion des plans.** Les agents IA doivent suivre ces instructions lors de la creation, du deplacement ou de la modification des plans.

## Configuration

**Issue tracker :** aucun
<!-- Options : GitHub | GitLab | aucun -->
<!-- Pour activer : changer en "GitHub" ou "GitLab" et configurer le depot -->

**Depot :** `utilisateur/nom-du-repo`

## Format de nom de fichier

```
TYPE-YYYY-MM-DD-NNNN-description.md
```

| Segment | Description | Exemple |
|---------|-------------|---------|
| `TYPE` | Etat : `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Date de transition vers l'etat actuel | `2026-01-15` |
| `NNNN` | ID sequentiel interne, 4 chiffres zero-padded | `0001` |
| `description` | Nom court en kebab-case | `user-auth-setup` |

### ID interne (`NNNN`)

Compteur incremental propre au projet. Pour obtenir le suivant :

1. Trouver le plus grand `NNNN` dans tous les sous-dossiers (`backlog/`, `coding/`, `done/`)
2. Ajouter 1

L'ID est **permanent** — il ne change pas meme si l'etat ou le nom du plan change.

> **Reserve :** L'ID `0000` est reserve pour les fichiers d'exemple/template. Le premier plan reel doit utiliser `0001`.

### Regle de date

La date dans le nom de fichier reflete la transition vers l'etat actuel :

| Etat | Date dans le nom = |
|------|-------------------|
| BACKLOG | Date de creation du plan |
| CODING | Date de debut de travail |
| DONE | Date de completion |

## Structure de dossiers

```
workplan/
├── README.md          # Ce fichier (source de verite)
├── backlog/           # Plans en attente
├── coding/            # Travail en cours
├── done/              # Plans termines (archive)
└── draft/             # Brouillons, idees et decisions (sans workflow d'etats)
```

## En-tete standardise

```markdown
# Plan : Titre descriptif

**Etat :** Backlog | Coding | Done
**Backlog :** 2026-01-15
**Coding :** —
**Done :** —
**Domaine :** general
**Issue :** —
```

**Regles de l'en-tete :**
- L'etat doit correspondre au prefixe du nom de fichier
- Les dates enregistrent quand chaque transition a eu lieu (`—` si non applicable)
- **Issue** est `—` si l'issue tracker est configure comme « aucun »

## Modele standard

### Terminologie obligatoire

| Terme | Utilisation | Exemple |
|-------|-------------|---------|
| **Phase** | Jalon majeur d'implementation | Phase 1 : MVP, Phase 2 : Ameliorations |
| **Etape** | Element concret de la checklist de progression | `- [ ] Creer la migration SQL` |

### Ordre des sections

En-tete -> Progression -> Objectif -> Contexte -> Implementation -> Verification -> Risques

Les sections optionnelles sont **omises**, pas laissees vides.

### Modele

```markdown
# Plan : Titre descriptif

**Etat :** Backlog
**Backlog :** YYYY-MM-DD
**Coding :** —
**Done :** —
**Domaine :** general
**Issue :** —

## Progression

### Phase 1 : MVP
- [ ] Etape concrete et verifiable
- [ ] Autre etape

### Phase 2 : Ameliorations *(si applicable)*
- [ ] Etape concrete et verifiable

## Objectif

Ce que l'on veut accomplir et pourquoi (1-3 paragraphes).

## Contexte *(optionnel)*

Etat actuel, prerequis.

## Implementation

### Phase 1 : MVP

Detail technique de l'implementation.

### Phase 2 : Ameliorations *(optionnel)*

## Verification *(optionnel)*

Etapes pour valider que le plan a ete correctement complete.

## Risques *(optionnel)*

Uniquement pour les plans complexes.
```

### Regles

1. **Progression toujours apres l'en-tete**, jamais a la fin
2. Etapes groupees par phase (`### Phase N : Nom`)
3. Chaque etape doit etre concrete et verifiable (pas generique)
4. Detail technique dans Implementation, resume dans Progression
5. Uniquement « Phase » et « Etape », jamais « Stade »
6. Les sections optionnelles sont omises, pas laissees vides

## Workflow

### Creer un plan

1. Obtenir le prochain ID sequentiel (`NNNN`)
2. Creer le fichier dans `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`

### Demarrer le travail

1. Deplacer de `backlog/` vers `coding/CODING-YYYY-MM-DD-NNNN-description.md` (date = aujourd'hui, ID inchange)
2. Mettre a jour l'en-tete : `Etat : Coding`, `Coding : YYYY-MM-DD`

### Terminer

1. Deplacer de `coding/` vers `done/DONE-YYYY-MM-DD-NNNN-description.md` (date = aujourd'hui)
2. Mettre a jour l'en-tete : `Etat : Done`, `Done : YYYY-MM-DD`

### Retourner au backlog

1. Deplacer de `coding/` vers `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`
2. Mettre a jour l'en-tete : `Etat : Backlog`

## References croisees

Les plans se referencent entre eux en utilisant l'**ID interne** (`NNNN`), qui est permanent :

```markdown
**Dependances :** Plan 0001, Plan 0002

Voir plan 0003 pour les details.
```

**Regle :** ne jamais referencer un plan par son nom de fichier complet (il change a chaque transition). Toujours utiliser l'ID interne.

## Obtenir le prochain ID

```bash
# Trouver le plus grand NNNN dans tous les sous-dossiers
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# Ajouter 1 au resultat
```

## Brouillons (drafts)

Les brouillons sont stockes dans `draft/` avec le format `DRAFT-YYYY-MM-DD-description.md`. Ils ne suivent pas le workflow BACKLOG->CODING->DONE et n'ont pas d'ID sequentiel. Ils servent de banque d'idees : brouillons de plans, decisions techniques, notes exploratoires. Quand un brouillon est suffisamment mur, il est promu en `backlog/` comme plan formel.
