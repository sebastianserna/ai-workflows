# Nome do Projeto

Breve descrição do projeto.

## Requisitos

<!-- Liste os requisitos do sistema: Node.js, Python, Docker, etc. -->

## Instalação

```bash
# Clonar o repositório
git clone <url-do-repo>
cd <nome-do-projeto>

# Instalar dependências
# npm install / pip install / etc.

# Configurar variáveis de ambiente
cp .env.example .env
```

## Desenvolvimento

```bash
# Iniciar servidor de desenvolvimento
# npm run dev / python manage.py runserver / etc.
```

## Estrutura do projeto

```
AGENTS.md               # Instruções para agentes de IA
CLAUDE.md               # Configuração do Claude Code
README.md               # Este arquivo
wisdom/                 # Base de conhecimento (arquitetura, guias)
workplan/               # Gestão de planos de trabalho
├── backlog/            #   Planos pendentes
├── coding/             #   Em andamento
├── done/               #   Concluídos
└── draft/              #   Rascunhos e ideias
```

## Trabalhando com agentes de IA

Este projeto está configurado para trabalhar com agentes de IA como o Claude Code:

- **AGENTS.md** — Guia completo para os agentes entenderem o projeto
- **CLAUDE.md** — Ponto de entrada que carrega automaticamente ao iniciar o Claude Code
- **wisdom/** — Documentação técnica que os agentes consultam para tomar decisões
- **workplan/** — Sistema de gestão de tarefas que os agentes podem ler e atualizar

## Licença

<!-- Substituir pela licença escolhida -->
The MIT License (MIT)

Copyright (c) <ano> - <autor>

O código-fonte deste repositório foi criado parcial ou inteiramente com a assistência de ferramentas de inteligência artificial alimentadas por modelos de linguagem avançados (LLMs) como Claude, GPT, Gemini, entre outros. O uso dessas ferramentas foi cuidadosamente guiado e supervisionado pelo autor do projeto.
