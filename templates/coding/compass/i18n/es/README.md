# Nombre del Proyecto

Descripción breve del proyecto.

## Requisitos

<!-- Listar requisitos del sistema: Node.js, Python, Docker, etc. -->

## Instalación

```bash
# Clonar el repositorio
git clone <url-del-repo>
cd <nombre-del-proyecto>

# Instalar dependencias
# npm install / pip install / etc.

# Configurar variables de entorno
cp .env.example .env
```

## Desarrollo

```bash
# Iniciar servidor de desarrollo
# npm run dev / python manage.py runserver / etc.
```

## Estructura del proyecto

```
AGENTS.md               # Instrucciones para agentes de IA
CLAUDE.md               # Configuración de Claude Code
README.md               # Este archivo
wisdom/                 # Base de conocimiento (arquitectura, guías)
workplan/               # Gestión de planes de trabajo
├── backlog/            #   Planes pendientes
├── coding/             #   En progreso
├── done/               #   Completados
└── draft/              #   Borradores e ideas
```

## Trabajo con agentes de IA

Este proyecto está preparado para trabajar con agentes de IA como Claude Code:

- **AGENTS.md** — Guía completa para que el agente entienda el proyecto
- **CLAUDE.md** — Punto de entrada que carga automáticamente al iniciar Claude Code
- **wisdom/** — Documentación técnica que el agente consulta para tomar decisiones
- **workplan/** — Sistema de gestión de tareas que el agente puede leer y actualizar
