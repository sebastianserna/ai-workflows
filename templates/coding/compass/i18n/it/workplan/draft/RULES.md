# Regole: draft/

> Le bozze sono una banca delle idee: bozze di piani, decisioni tecniche, note esplorative.

## Cosa va qui

- Idee in fase iniziale non ancora pronte per il backlog
- Registrazioni di decisioni tecniche
- Note esplorative e ricerche

## Nomenclatura

```
DRAFT-YYYY-MM-DD-descrizione.md
```

Le bozze non portano **mai** un identificatore di issue, indipendentemente dalla configurazione del tracker.

## Regole chiave

- Ogni bozza deve avere il YAML frontmatter con `state: "draft"` (vedere `workplan/README.md` per il formato)
- Le bozze **non** seguono il workflow BACKLOG → CODING → DONE
- Quando una bozza matura, viene promossa in `backlog/` come piano formale
- Vedere `workplan/README.md` per il riferimento completo

## Vedi anche

- `backlog/RULES.md` — Regole per i piani in attesa
- `coding/RULES.md` — Regole per i piani in corso
- `done/RULES.md` — Regole per i piani completati
