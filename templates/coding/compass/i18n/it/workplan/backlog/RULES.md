# Regole: backlog/

> Piani in attesa di essere lavorati.

## Cosa va qui

- Piani definiti e pronti per iniziare (o in attesa di prioritizzazione)
- I nuovi piani entrano qui dopo la creazione

## Nomenclatura

**Con issue tracker (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-descrizione.md
```

**Senza issue tracker:**

```
BACKLOG-YYYY-MM-DD-descrizione.md
```

La data riflette quando il piano è stato creato.

## Regole chiave

- Ogni piano deve avere il YAML frontmatter con `state: "backlog"` (vedere `workplan/README.md` per il formato)
- **Se un issue tracker è configurato**, creare prima l'issue (`gh issue create`, `glab issue create`, ecc.) e usare il numero di issue nel nome del file (`iNNNN`)
- Per avviare il lavoro: spostare in `coding/`, rinominare il prefisso in `CODING`, aggiornare data e intestazione
- I piani possono anche essere riportati qui da `coding/` se messi in pausa
- Vedere `workplan/README.md` per il riferimento completo

## Vedi anche

- `coding/RULES.md` — Regole per i piani in corso
- `done/RULES.md` — Regole per i piani completati
- `draft/RULES.md` — Regole per bozze e idee
