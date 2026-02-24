# Regras: backlog/

> Planos pendentes aguardando para serem trabalhados.

## O que vai aqui

- Planos definidos e prontos para iniciar (ou aguardando priorização)
- Novos planos entram aqui após a criação

## Nomenclatura

**Com issue tracker (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-description.md
```

**Sem issue tracker:**

```
BACKLOG-YYYY-MM-DD-description.md
```

A data reflete quando o plano foi criado.

## Regras-chave

- Cada plano deve ter YAML frontmatter com `state: "backlog"` (veja `workplan/README.md` para o formato)
- **Se um issue tracker estiver configurado**, crie a issue primeiro (`gh issue create`, `glab issue create`, etc.) e use o número da issue no nome do arquivo (`iNNNN`)
- Para iniciar o trabalho: mova para `coding/`, renomeie o prefixo para `CODING`, atualize a data e o cabeçalho
- Planos também podem ser retornados para cá de `coding/` se pausados
- Veja `workplan/README.md` para a referência completa

## Veja também

- `coding/RULES.md` — Regras para planos em andamento
- `done/RULES.md` — Regras para planos concluídos
- `draft/RULES.md` — Regras para rascunhos e ideias
