# wisdom/ — Base de conhecimento

Esta pasta contém a documentação técnica do projeto. É a **fonte da verdade** que os agentes de IA consultam antes de tomar decisões.

## Finalidade

- Documentar decisões de arquitetura e suas justificativas
- Manter os guias técnicos atualizados
- Evitar que os agentes repitam erros ou tomem decisões inconsistentes
- Preservar conhecimento que não cabe no código em si

## Estrutura

```
wisdom/
├── README.md           # Este arquivo
├── architecture/       # Como o sistema é projetado
│   └── AGENTS.md
├── development/        # Como trabalhar no projeto
│   └── AGENTS.md
└── operations/         # Como é feito o deploy e a operação
    └── AGENTS.md
```

Cada `AGENTS.md` fornece contexto aos agentes de IA sobre o escopo da pasta e quando consultá-la.

### architecture/

Decisões de arquitetura, estrutura do sistema, padrões escolhidos e suas justificativas. Responde **"como é projetado e por quê"**.

Exemplos: estrutura de pastas, padrões de camadas, escolhas de bibliotecas, diagramas de componentes.

### development/

Guias de desenvolvimento do dia a dia. Responde **"como trabalhar neste projeto"**.

Exemplos: convenções de código, guia de testes, workflow git, setup local, linting.

### operations/

Tudo relacionado a levar o código para produção e mantê-lo funcionando. Responde **"como é feito o deploy e a operação"**.

Exemplos: pipeline CI/CD, configuração de ambientes, monitoramento, variáveis de ambiente.

## Quando adicionar mais pastas

As três pastas base cobrem a maioria dos projetos. Se o projeto crescer em um domínio específico, adicione pastas dedicadas:

| Pasta | Quando adicionar |
|-------|-----------------|
| `database/` | O projeto tem seu próprio banco de dados com migrações |
| `security/` | Regras de auth, permissões ou compliance para documentar |
| `integrations/` | Múltiplas APIs externas ou serviços de terceiros |
| `api/` | API pública consumida por outros |

**Regra:** não crie pastas vazias "por precaução". Crie-as quando houver pelo menos um documento real para colocar dentro.

## Convenções

- Documentos em Markdown, um tópico por arquivo
- Manter atualizado quando a arquitetura mudar
- Referenciar a partir do `AGENTS.md` na seção "Especificações detalhadas"

## Diferença em relação ao workplan/

| | `wisdom/` | `workplan/` |
|---|-----------|-------------|
| **Contém** | Documentação permanente | Planos de trabalho com ciclo de vida |
| **Muda** | Quando a arquitetura evolui | Constantemente (backlog → coding → done) |
| **Formato** | Livre | Template padronizado com cabeçalho |
| **Finalidade** | Entender o sistema | Gerenciar o que precisa ser feito |
