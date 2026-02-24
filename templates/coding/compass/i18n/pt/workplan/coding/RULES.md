# Regras: coding/

> Planos sendo trabalhados ativamente.

## O que vai aqui

- Planos atualmente em andamento
- Apenas planos que estão sendo implementados ativamente

## Nomenclatura

**Com issue tracker (GitHub / GitLab):**

```
CODING-YYYY-MM-DD-iNNNN-description.md
```

**Sem issue tracker:**

```
CODING-YYYY-MM-DD-description.md
```

A data reflete quando o trabalho começou.

## Regras-chave

- Cada plano deve ter YAML frontmatter com `state: "coding"` (veja `workplan/README.md` para o formato)
- Atualize as caixas de seleção de progresso conforme os passos são concluídos
- Ao finalizar: mova para `done/`, renomeie o prefixo para `DONE`, atualize a data e o frontmatter
- Para pausar: mova de volta para `backlog/`, renomeie o prefixo para `BACKLOG`, atualize o frontmatter
- Veja `workplan/README.md` para a referência completa

## Veja também

- `backlog/RULES.md` — Regras para planos pendentes
- `done/RULES.md` — Regras para planos concluídos
- `draft/RULES.md` — Regras para rascunhos e ideias
