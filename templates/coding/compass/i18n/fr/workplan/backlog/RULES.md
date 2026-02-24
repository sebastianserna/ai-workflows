# Regles : backlog/

> Plans en attente de traitement.

## Ce que l'on trouve ici

- Plans definis et prets a demarrer (ou en attente de priorisation)
- Les nouveaux plans entrent ici apres leur creation

## Nommage

**Avec issue tracker (GitHub / GitLab) :**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**Sans issue tracker :**

```
BACKLOG-YYYY-MM-DD-description.md
```

La date reflete le moment ou le plan a ete cree.

## Regles cles

- Chaque plan doit avoir le YAML frontmatter avec `state: "backlog"` (voir `workplan/README.md` pour le format)
- **Si un issue tracker est configure**, creer d'abord l'issue (`gh issue create`, `glab issue create`, etc.) et utiliser le numero d'issue dans le nom de fichier (`iNNNN`)
- Pour demarrer le travail : deplacer vers `coding/`, renommer le prefixe en `CODING`, mettre a jour la date et l'en-tete
- Les plans peuvent egalement etre renvoyes ici depuis `coding/` en cas de pause
- Voir `workplan/README.md` pour la reference complete

## Voir aussi

- `coding/RULES.md` — Regles pour les plans en cours
- `done/RULES.md` — Regles pour les plans termines
- `draft/RULES.md` — Regles pour les brouillons et idees
