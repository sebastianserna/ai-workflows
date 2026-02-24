# Regole: coding/

> Piani attivamente in lavorazione.

## Cosa va qui

- Piani attualmente in corso
- Solo piani che vengono implementati attivamente

## Nomenclatura

**Con issue tracker (GitHub / GitLab):**

```
CODING-YYYY-MM-DD-iNNNN-descrizione.md
```

**Senza issue tracker:**

```
CODING-YYYY-MM-DD-descrizione.md
```

La data riflette quando il lavoro è iniziato.

## Regole chiave

- Ogni piano deve avere il YAML frontmatter con `state: "coding"` (vedere `workplan/README.md` per il formato)
- Aggiornare le caselle di avanzamento man mano che i passi vengono completati
- Al termine: spostare in `done/`, rinominare il prefisso in `DONE`, aggiornare data e frontmatter
- Per mettere in pausa: spostare in `backlog/`, rinominare il prefisso in `BACKLOG`, aggiornare il frontmatter
- Vedere `workplan/README.md` per il riferimento completo

## Vedi anche

- `backlog/RULES.md` — Regole per i piani in attesa
- `done/RULES.md` — Regole per i piani completati
- `draft/RULES.md` — Regole per bozze e idee
