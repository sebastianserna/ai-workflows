# AGENTS.md

Guía para agentes de IA que trabajan en este proyecto.

<!-- Idioma: define aquí el idioma para respuestas del agente y para el código -->

## Stack

<!-- Define aquí el stack tecnológico del proyecto. Ejemplo:
- Framework:
- UI:
- Backend/DB:
- Lenguaje:
-->

## Setup y comandos

<!-- Comandos esenciales del proyecto. Ejemplo:
```bash
npm install        # Instalar dependencias
npm run dev        # Servidor de desarrollo
npm run build      # Build de producción
npm run lint       # Linter
npm run test       # Tests
```
-->

<!-- Variables de entorno necesarias:
- Listar aquí las variables requeridas en `.env`
-->

## Estructura del proyecto

<!-- Describe la estructura de carpetas principal del proyecto. Ejemplo:
```
src/
docs/
tests/
wisdom/
workplan/
```
-->

## Convenciones de código

- Indentación: 2 espacios
- Código en inglés, documentación y comentarios en español

<!-- Agrega más convenciones del equipo. Ejemplo:
- Naming: camelCase para variables, PascalCase para componentes
- TypeScript estricto
-->

## Base de conocimiento (wisdom/)

La carpeta `wisdom/` contiene la documentación técnica del proyecto. Es la fuente de verdad para entender cómo funciona el sistema.

Estructura base:
- `wisdom/architecture/` — Cómo está diseñado el sistema (decisiones, patrones, estructura)
- `wisdom/development/` — Cómo se trabaja en el proyecto (convenciones, testing, workflows)
- `wisdom/operations/` — Cómo se despliega y opera (CI/CD, ambientes, monitoreo)

Se pueden agregar carpetas adicionales (`database/`, `security/`, `integrations/`) cuando el proyecto lo requiera. Ver `wisdom/README.md` para criterios.

Los agentes deben consultar `wisdom/` antes de tomar decisiones que afecten arquitectura o patrones existentes.

## Gestión de planes (workplan/)

La carpeta `workplan/` gestiona el ciclo de vida de las tareas del proyecto.

**Carpetas:**
- `backlog/` — Planes pendientes, priorizados y listos para trabajar
- `coding/` — Planes en progreso activo
- `done/` — Planes completados (archivo histórico)
- `draft/` — Borradores, ideas y decisiones

**Flujo:** `backlog/ -> coding/ -> done/`

**Formato de nombre de archivo:** `TIPO-YYYY-MM-DD-author_descripción.md`
- TIPO: `BACKLOG`, `CODING`, `DONE`, `DRAFT`
- author: username del creador del plan (GitHub, GitLab, Bitbucket, etc.)
- `_` separa author de descripción

Todos los estados comparten la misma estructura de YAML frontmatter (campos uniformes en draft, backlog, coding, done).

Consultar `workplan/README.md` para la plantilla completa y reglas detalladas.

## Auth y roles

<!-- Define el sistema de autenticación y roles. Ejemplo:
- Proveedor de auth:
- Jerarquía de roles:
- Composable/función para verificar permisos:
-->

## Git workflow

- Rama principal: `main` (PRs obligatorios)
- Ramas: `feature/`, `fix/`, `hotfix/`, `refactor/`, `chore/`, `docs/` + descripción en inglés
- Commits: Conventional Commits en inglés (`feat:`, `fix:`, `docs:`, etc.)
- PRs: título en inglés (Conventional Commits), descripción/body en español
- Issues: título y descripción en español
- **No incluir** `Co-Authored-By` de agentes de IA en commits
- **No incluir** el enlace "Generated with Claude Code" en mensajes de commit o PRs

<!-- Agrega más reglas de Git workflow si es necesario -->

## Testing

<!-- Define la estrategia de testing. Ejemplo:
- Framework de tests:
- Qué debe tener tests:
- Patrón de archivos: `*.test.ts` o `*.spec.ts`
-->

## Zonas protegidas (NO modificar)

<!-- Lista archivos o carpetas que los agentes NO deben modificar. Ejemplo:
| Archivo | Razón |
|---------|-------|
| `.env` | Nunca commitear |
| `migrations/` (aplicadas) | Crear nueva en su lugar |
-->

## Gotchas conocidos

<!-- Documenta problemas conocidos o trampas comunes. Ejemplo:
- Bug X: descripción y workaround
- Limitación Y: contexto y solución temporal
-->

## Especificaciones detalladas

<!-- Lista enlaces a documentos de referencia en wisdom/. Ejemplo:
| Documento | Contenido |
|-----------|-----------|
| [wisdom/architecture/...](wisdom/architecture/...) | Arquitectura del sistema |
| [wisdom/database/...](wisdom/database/...) | Esquema y convenciones DB |
-->
