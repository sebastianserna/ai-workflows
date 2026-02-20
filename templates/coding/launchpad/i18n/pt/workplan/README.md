# Gestão de planos

> **Este arquivo é a fonte da verdade para a gestão de planos.** Os agentes de IA devem seguir estas instruções ao criar, mover ou modificar planos.

## Configuração

**Issue tracker:** none
<!-- Opções: GitHub | GitLab | none -->
<!-- Para ativar: altere para "GitHub" ou "GitLab" e configure o repositório -->

**Repositório:** `usuario/nome-do-repo`

## Formato de nomes de arquivo

```
TYPE-YYYY-MM-DD-NNNN-description.md
```

| Segmento | Descrição | Exemplo |
|----------|-----------|---------|
| `TYPE` | Estado: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Data da transição para o estado atual | `2026-01-15` |
| `NNNN` | ID sequencial interno, 4 dígitos com zero à esquerda | `0001` |
| `description` | Nome curto em kebab-case | `user-auth-setup` |

### ID interno (`NNNN`)

Contador incremental específico do projeto. Para obter o próximo:

1. Encontre o maior `NNNN` em todas as subpastas (`backlog/`, `coding/`, `done/`)
2. Some 1

O ID é **permanente** — não muda mesmo que o estado ou nome do plano sejam alterados.

> **Reservado:** O ID `0000` é reservado para arquivos de exemplo/template. O primeiro plano real deve usar `0001`.

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
├── coding/            # Trabalho em andamento
├── done/              # Planos concluídos (arquivo)
└── draft/             # Rascunhos, ideias e decisões (sem workflow de estados)
```

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

1. Obter o próximo ID sequencial (`NNNN`)
2. Criar arquivo em `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`

### Iniciar trabalho

1. Mover de `backlog/` para `coding/CODING-YYYY-MM-DD-NNNN-description.md` (data = hoje, ID inalterado)
2. Atualizar cabeçalho: `Estado: Coding`, `Coding: YYYY-MM-DD`

### Concluir

1. Mover de `coding/` para `done/DONE-YYYY-MM-DD-NNNN-description.md` (data = hoje)
2. Atualizar cabeçalho: `Estado: Done`, `Done: YYYY-MM-DD`

### Retornar ao backlog

1. Mover de `coding/` para `backlog/BACKLOG-YYYY-MM-DD-NNNN-description.md`
2. Atualizar cabeçalho: `Estado: Backlog`

## Referências cruzadas

Os planos fazem referência uns aos outros usando o **ID interno** (`NNNN`), que é permanente:

```markdown
**Dependências:** Plano 0001, Plano 0002

Veja o plano 0003 para detalhes.
```

**Regra:** nunca referencie um plano pelo nome completo do arquivo (ele muda a cada transição). Sempre use o ID interno.

## Obter próximo ID

```bash
# Encontrar o maior NNNN em todas as subpastas
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# Somar 1 ao resultado
```

## Rascunhos

Rascunhos são armazenados em `draft/` com o formato `DRAFT-YYYY-MM-DD-description.md`. Eles não seguem o workflow BACKLOG→CODING→DONE e não possuem ID sequencial. Servem como banco de ideias: rascunhos de planos, decisões técnicas, notas exploratórias. Quando um rascunho amadurece o suficiente, é promovido para `backlog/` como um plano formal.
