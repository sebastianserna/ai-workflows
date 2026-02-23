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

<!-- Define las convenciones del equipo. Ejemplo:
- Indentación: 2 espacios
- Naming: camelCase para variables, PascalCase para componentes
- TypeScript estricto
- Código en inglés, documentación en español
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
- `draft/` — Borradores, ideas y decisiones de arquitectura (sin flujo ni identificador)

**Flujo:** `backlog/ -> coding/ -> done/`

**Formato de nombre de archivo:**
- Con issue tracker: `TIPO-YYYY-MM-DD-iNNNN-descripción.md`
- Sin issue tracker: `TIPO-YYYY-MM-DD-descripción.md`
- TIPO: `BACKLOG`, `CODING`, `DONE`
- iNNNN: número de issue de GitHub/GitLab, zero-padded con prefijo `i` (cuando el tracker está configurado)

Consultar `workplan/README.md` para la plantilla completa y reglas detalladas.

## Auth y roles

<!-- Define el sistema de autenticación y roles. Ejemplo:
- Proveedor de auth:
- Jerarquía de roles:
- Composable/función para verificar permisos:
-->

## Git workflow

<!-- Define el flujo de trabajo con Git. Ejemplo:
- Rama principal: `main`
- Ramas: `feature/`, `fix/`, `hotfix/`, `docs/` + descripción
- Commits: Conventional Commits (`feat:`, `fix:`, `docs:`, etc.)
- PRs obligatorios para merge a main
-->

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
