# Regles : coding/

> Plans en cours de traitement.

## Ce que l'on trouve ici

- Plans actuellement en cours
- Uniquement les plans en cours d'implementation active

## Nommage

**Avec issue tracker (GitHub / GitLab) :**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**Sans issue tracker :**

```
CODING-YYYY-MM-DD-description.md
```

La date reflete le moment ou le travail a commence.

## Regles cles

- Chaque plan doit avoir le YAML frontmatter avec `state: "coding"` (voir `workplan/README.md` pour le format)
- Mettre a jour les cases a cocher de progression au fur et a mesure que les etapes sont completees
- Une fois termine : deplacer vers `done/`, renommer le prefixe en `DONE`, mettre a jour la date et le frontmatter
- Pour mettre en pause : deplacer vers `backlog/`, renommer le prefixe en `BACKLOG`, mettre a jour le frontmatter
- Voir `workplan/README.md` pour la reference complete

## Voir aussi

- `backlog/RULES.md` — Regles pour les plans en attente
- `done/RULES.md` — Regles pour les plans termines
- `draft/RULES.md` — Regles pour les brouillons et idees
