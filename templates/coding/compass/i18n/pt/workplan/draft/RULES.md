# Regras: draft/

> Rascunhos são um banco de ideias: rascunhos de planos, decisões técnicas, notas exploratórias.

## O que vai aqui

- Ideias em estágio inicial que ainda não estão prontas para o backlog
- Registros de decisões técnicas
- Notas exploratórias e pesquisas

## Nomenclatura

```
DRAFT-YYYY-MM-DD-description.md
```

Rascunhos **nunca** carregam um identificador de issue, independentemente da configuração do tracker.

## Regras-chave

- Cada rascunho deve ter YAML frontmatter com `state: "draft"` (veja `workplan/README.md` para o formato)
- Rascunhos **não** seguem o workflow BACKLOG → CODING → DONE
- Quando um rascunho amadurece, é promovido para `backlog/` como plano formal
- Veja `workplan/README.md` para a referência completa

## Veja também

- `backlog/RULES.md` — Regras para planos pendentes
- `coding/RULES.md` — Regras para planos em andamento
- `done/RULES.md` — Regras para planos concluídos
