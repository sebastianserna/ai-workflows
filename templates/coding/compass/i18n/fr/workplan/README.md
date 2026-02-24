# Gestion des plans

> **Ce fichier est la source de verite pour la gestion des plans.** Les agents IA doivent suivre ces instructions lors de la creation, du deplacement ou de la modification des plans.

## Configuration

**Issue tracker :** none
<!-- Options : GitHub | GitLab | none -->
<!-- Pour activer : changer en "GitHub" ou "GitLab" et configurer le depot -->

**Depot :** `utilisateur/nom-du-repo`

## Format de nom de fichier

Le format depend de la configuration de l'issue tracker :

**Avec issue tracker (GitHub / GitLab) :**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**Sans issue tracker (none) :**

```
TYPE-YYYY-MM-DD-description.md
```

| Segment | Description | Exemple |
|---------|-------------|---------|
| `TYPE` | Etat : `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Date de transition vers l'etat actuel | `2026-01-15` |
| `iNNNN` | Numero d'issue, 4 chiffres zero-padded avec prefixe `i` (uniquement avec tracker) | `i0060` |
| `description` | Nom court en kebab-case | `user-auth-setup` |

### Identifiant d'issue (`iNNNN`)

Lorsqu'un issue tracker est configure (GitHub ou GitLab), chaque plan **doit** avoir un issue correspondant. Le numero d'issue devient l'identifiant unique du plan :

- Le prefixe `i` distingue le numero d'issue des autres segments numeriques
- Zero-padded a 4 chiffres : issue #7 → `i0007`, issue #123 → `i0123`
- L'identifiant est **permanent** — il ne change pas lorsque le plan est deplace entre les etats
- GitHub/GitLab garantit l'unicite atomique, eliminant les risques de collision dans les environnements collaboratifs

**Lorsque l'issue tracker est « none »**, les plans n'ont pas de segment identifiant. Le nom de fichier est simplement `TYPE-YYYY-MM-DD-description.md`.

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
│   └── RULES.md
├── coding/            # Travail en cours
│   └── RULES.md
├── done/              # Plans termines (archive)
│   └── RULES.md
└── draft/             # Brouillons, idees et decisions (sans workflow d'etats)
    └── RULES.md
```

Chaque `RULES.md` contient les regles et conventions de nommage specifiques au dossier :

- `backlog/RULES.md` — Point d'entree pour les nouveaux plans, instructions de creation d'issues
- `coding/RULES.md` — Travail actif, regles de transition et de progression
- `done/RULES.md` — Archive, criteres de completion
- `draft/RULES.md` — Banque d'idees, sans workflow, sans identifiant d'issue

## YAML Frontmatter

Chaque fichier de plan doit commencer par un bloc de YAML frontmatter a la **ligne 1** (aucune ligne vide avant le `---` d'ouverture). GitHub le rend sous forme de tableau de metadonnees.

```yaml
---
plan: "Titre descriptif"
state: "backlog"
issue: ""
domain: "general"
backlog: "2026-01-15"
coding: ""
done: ""
---
```

**Champs du frontmatter :**

| Champ | Description | Valeurs |
|-------|-------------|---------|
| `plan` | Titre descriptif court | Texte libre |
| `state` | Etat actuel (doit correspondre au prefixe du nom de fichier) | `backlog`, `coding`, `done`, `draft` |
| `issue` | Identifiant d'issue (`iNNNN`) ou vide | `"i0060"`, `""` |
| `domain` | Domaine fonctionnel | `general`, ou specifique au projet |
| `backlog` | Date de creation du plan | `"2026-01-15"`, `""` |
| `coding` | Date de debut du travail | `"2026-01-20"`, `""` |
| `done` | Date de completion | `"2026-02-01"`, `""` |

**Regles du frontmatter :**
- Le premier `---` doit etre exactement a la ligne 1 sans lignes vides avant
- La valeur de `state` doit correspondre au prefixe du nom de fichier (en minuscules)
- **issue** est `""` si l'issue tracker est configure comme "none"
- Lorsque le tracker est actif, **issue** contient l'identifiant : `"i0060"`
- Les brouillons omettent les champs `issue` et de dates entierement
- Les champs de date enregistrent quand chaque transition a eu lieu (`""` si pas encore atteint)

## Modele standard

### Terminologie obligatoire

| Terme | Utilisation | Exemple |
|-------|-------------|---------|
| **Phase** | Jalon majeur d'implementation | Phase 1 : MVP, Phase 2 : Ameliorations |
| **Etape** | Element concret de la checklist de progression | `- [ ] Creer la migration SQL` |

### Ordre des sections

Frontmatter → Progression → Objectif → Contexte → Implementation → Verification → Risques

Les sections optionnelles sont **omises**, pas laissees vides.

### Modele

```markdown
---
plan: "Titre descriptif"
state: "backlog"
issue: ""
domain: "general"
backlog: "YYYY-MM-DD"
coding: ""
done: ""
---

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

1. **Progression toujours apres le frontmatter**, jamais a la fin
2. Etapes groupees par phase (`### Phase N : Nom`)
3. Chaque etape doit etre concrete et verifiable (pas generique)
4. Detail technique dans Implementation, resume dans Progression
5. Uniquement « Phase » et « Etape », jamais « Stade »
6. Les sections optionnelles sont omises, pas laissees vides

## Workflow

### Creer un plan

**Avec issue tracker :**

1. Creer d'abord l'issue : `gh issue create` (GitHub) ou `glab issue create` (GitLab)
2. Noter le numero d'issue (ex. #60)
3. Creer le fichier dans `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` (ex. `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Remplir le champ `issue` du frontmatter avec l'identifiant

**Sans issue tracker :**

1. Creer le fichier dans `backlog/BACKLOG-YYYY-MM-DD-description.md`

### Demarrer le travail

1. Deplacer de `backlog/` vers `coding/CODING-YYYY-MM-DD-...-description.md` (date = aujourd'hui, identifiant inchange)
2. Mettre a jour le frontmatter : `state: "coding"`, `coding: "YYYY-MM-DD"`

### Terminer

1. Deplacer de `coding/` vers `done/DONE-YYYY-MM-DD-...-description.md` (date = aujourd'hui)
2. Mettre a jour le frontmatter : `state: "done"`, `done: "YYYY-MM-DD"`

### Retourner au backlog

1. Deplacer de `coding/` vers `backlog/BACKLOG-YYYY-MM-DD-...-description.md`
2. Mettre a jour le frontmatter : `state: "backlog"`, `coding: ""`

## References croisees

**Avec issue tracker :** les plans se referencent entre eux en utilisant le numero d'issue avec `#N`, qui est permanent et active l'auto-linking :

```markdown
**Dependances :** #1, #2

Voir #3 pour les details.
```

**Sans issue tracker :** referencer les plans par leur nom descriptif :

```markdown
**Dependances :** user-auth-setup, api-rate-limiting
```

**Regle :** ne jamais referencer un plan par son nom de fichier complet (il change a chaque transition).

## Brouillons

Les brouillons sont stockes dans `draft/` avec le format `DRAFT-YYYY-MM-DD-description.md`. Ils ne suivent pas le workflow BACKLOG→CODING→DONE et n'ont pas d'identifiant d'issue. Ils servent de banque d'idees : brouillons de plans, decisions techniques, notes exploratoires. Quand un brouillon est suffisamment mur, il est promu en `backlog/` comme plan formel.
