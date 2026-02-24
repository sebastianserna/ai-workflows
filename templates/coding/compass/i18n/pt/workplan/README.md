# Gestão de planos

> **Este arquivo é a fonte da verdade para a gestão de planos.** Os agentes de IA devem seguir estas instruções ao criar, mover ou modificar planos.

## Configuração

**Issue tracker:** none
<!-- Opções: GitHub | GitLab | none -->
<!-- Para ativar: altere para "GitHub" ou "GitLab" e configure o repositório -->

**Repositório:** `usuario/nome-do-repo`

## Formato de nomes de arquivo

O formato depende de o issue tracker estar configurado ou não:

**Com issue tracker (GitHub / GitLab):**

```
TYPE-YYYY-MM-DD-iNNNN-description.md
```

**Sem issue tracker (none):**

```
TYPE-YYYY-MM-DD-description.md
```

| Segmento | Descrição | Exemplo |
|----------|-----------|---------|
| `TYPE` | Estado: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Data da transição para o estado atual | `2026-01-15` |
| `iNNNN` | Número da issue, 4 dígitos com zero à esquerda e prefixo `i` (apenas com tracker) | `i0060` |
| `description` | Nome curto em kebab-case | `user-auth-setup` |

### Identificador de issue (`iNNNN`)

Quando um issue tracker está configurado (GitHub ou GitLab), cada plano **deve** ter uma issue correspondente. O número da issue se torna o identificador único do plano:

- O prefixo `i` distingue o número da issue de outros segmentos numéricos
- Preenchido com zeros até 4 dígitos: issue #7 → `i0007`, issue #123 → `i0123`
- O identificador é **permanente** — não muda quando o plano se move entre estados
- GitHub/GitLab garante unicidade atômica, eliminando riscos de colisão em ambientes colaborativos

**Quando o issue tracker é "none"**, os planos não possuem segmento identificador. O nome do arquivo é simplesmente `TYPE-YYYY-MM-DD-description.md`.

### Regra de data

A data no nome do arquivo reflete a transição para o estado atual:

| Estado | Data no nome = |
|--------|---------------|
| BACKLOG | Data de criação do plano |
| CODING | Data de início do trabalho |
| DONE | Data de conclusão |

## Estrutura de pastas

```
workplan/
├── README.md          # Este arquivo (fonte da verdade)
├── backlog/           # Planos pendentes
│   └── RULES.md
├── coding/            # Trabalho em andamento
│   └── RULES.md
├── done/              # Planos concluídos (arquivo)
│   └── RULES.md
└── draft/             # Rascunhos, ideias e decisões (sem workflow de estados)
    └── RULES.md
```

Cada `RULES.md` contém regras e convenções de nomenclatura específicas da pasta:

- `backlog/RULES.md` — Ponto de entrada para novos planos, instruções de criação de issues
- `coding/RULES.md` — Trabalho ativo, regras de transição e progresso
- `done/RULES.md` — Arquivo, critérios de conclusão
- `draft/RULES.md` — Banco de ideias, sem workflow, sem identificador de issue

## Cabeçalho padronizado

```markdown
# Plano: Título descritivo

**Estado:** Backlog | Coding | Done
**Backlog:** 2026-01-15
**Coding:** —
**Done:** —
**Domínio:** geral
**Issue:** —
```

**Regras do cabeçalho:**
- O estado deve corresponder ao prefixo do nome do arquivo
- As datas registram quando cada transição ocorreu (`—` se não aplicável)
- **Issue** é `—` se o issue tracker estiver configurado como "none"
- Quando o tracker está ativo, **Issue** contém o link para a issue: `[#60](https://github.com/user/repo/issues/60)`

## Template padrão

### Terminologia obrigatória

| Termo | Uso | Exemplo |
|-------|-----|---------|
| **Fase** | Marco principal de implementação | Fase 1: MVP, Fase 2: Melhorias |
| **Passo** | Item concreto na checklist de progresso | `- [ ] Criar migração SQL` |

### Ordem das seções

Cabeçalho → Progresso → Objetivo → Contexto → Implementação → Verificação → Riscos

Seções opcionais são **omitidas**, não deixadas vazias.

### Template

```markdown
# Plano: Título descritivo

**Estado:** Backlog
**Backlog:** YYYY-MM-DD
**Coding:** —
**Done:** —
**Domínio:** geral
**Issue:** —

## Progresso

### Fase 1: MVP
- [ ] Passo concreto e verificável
- [ ] Outro passo

### Fase 2: Melhorias *(se aplicável)*
- [ ] Passo concreto e verificável

## Objetivo

O que se deseja alcançar e por quê (1-3 parágrafos).

## Contexto *(opcional)*

Estado atual, pré-requisitos.

## Implementação

### Fase 1: MVP

Detalhe técnico da implementação.

### Fase 2: Melhorias *(opcional)*

## Verificação *(opcional)*

Passos para validar que o plano foi concluído corretamente.

## Riscos *(opcional)*

Apenas para planos complexos.
```

### Regras

1. **Progresso sempre após o cabeçalho**, nunca no final
2. Passos agrupados por fase (`### Fase N: Nome`)
3. Cada passo deve ser concreto e verificável (não genérico)
4. Detalhe técnico na Implementação, resumo no Progresso
5. Apenas "Fase" e "Passo", nunca "Etapa"
6. Seções opcionais são omitidas, não deixadas vazias

## Workflow

### Criar plano

**Com issue tracker:**

1. Criar a issue primeiro: `gh issue create` (GitHub) ou `glab issue create` (GitLab)
2. Anotar o número da issue (ex.: #60)
3. Criar arquivo em `backlog/BACKLOG-YYYY-MM-DD-iNNNN-description.md` (ex.: `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Preencher o campo `Issue` do cabeçalho com o link

**Sem issue tracker:**

1. Criar arquivo em `backlog/BACKLOG-YYYY-MM-DD-description.md`

### Iniciar trabalho

1. Mover de `backlog/` para `coding/CODING-YYYY-MM-DD-...-description.md` (data = hoje, identificador inalterado)
2. Atualizar cabeçalho: `Estado: Coding`, `Coding: YYYY-MM-DD`

### Concluir

1. Mover de `coding/` para `done/DONE-YYYY-MM-DD-...-description.md` (data = hoje)
2. Atualizar cabeçalho: `Estado: Done`, `Done: YYYY-MM-DD`

### Retornar ao backlog

1. Mover de `coding/` para `backlog/BACKLOG-YYYY-MM-DD-...-description.md`
2. Atualizar cabeçalho: `Estado: Backlog`

## Referências cruzadas

**Com issue tracker:** os planos fazem referência uns aos outros usando o número da issue com `#N`, que é permanente e permite auto-linking:

```markdown
**Dependências:** #1, #2

Veja #3 para detalhes.
```

**Sem issue tracker:** referencie os planos pelo nome descritivo:

```markdown
**Dependências:** user-auth-setup, api-rate-limiting
```

**Regra:** nunca referencie um plano pelo nome completo do arquivo (ele muda a cada transição).

## Rascunhos

Rascunhos são armazenados em `draft/` com o formato `DRAFT-YYYY-MM-DD-description.md`. Eles não seguem o workflow BACKLOG→CODING→DONE e não possuem identificador de issue. Servem como banco de ideias: rascunhos de planos, decisões técnicas, notas exploratórias. Quando um rascunho amadurece o suficiente, é promovido para `backlog/` como um plano formal.
