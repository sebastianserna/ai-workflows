# Gestión de planes

> **Este archivo es la fuente de verdad para la gestión de planes.** Los agentes de IA deben seguir estas instrucciones al crear, mover o modificar planes.

## Configuración

**Issue tracker:** ninguno
<!-- Opciones: GitHub | GitLab | ninguno -->
<!-- Para activar: cambiar a "GitHub" o "GitLab" y configurar el repositorio -->

**Repositorio:** `usuario/nombre-del-repo`

## Formato de nombre de archivo

```
TIPO-YYYY-MM-DD-NNNN-descripción.md
```

| Segmento | Descripción | Ejemplo |
|----------|-------------|---------|
| `TIPO` | Estado: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Fecha de la transición al estado actual | `2026-01-15` |
| `NNNN` | ID interno secuencial, 4 dígitos zero-padded | `0001` |
| `descripción` | Nombre corto en kebab-case | `user-auth-setup` |

### ID interno (`NNNN`)

Consecutivo incremental propio del proyecto. Para obtener el siguiente:

1. Buscar el mayor `NNNN` en todas las subcarpetas (`backlog/`, `coding/`, `done/`)
2. Sumar 1

El ID es **permanente** — no cambia aunque cambie el estado o nombre del plan.

> **Reservado:** El ID `0000` está reservado para archivos de ejemplo/template. El primer plan real debe usar `0001`.

### Regla de fecha

La fecha en el nombre de archivo refleja la transición al estado actual:

| Estado | Fecha en nombre = |
|--------|-------------------|
| BACKLOG | Fecha de creación del plan |
| CODING | Fecha de inicio de trabajo |
| DONE | Fecha de completado |

## Estructura de carpetas

```
workplan/
├── README.md          # Este archivo (fuente de verdad)
├── backlog/           # Planes pendientes
├── coding/            # Trabajo en progreso
├── done/              # Planes completados (archivo)
└── draft/             # Borradores, ideas y decisiones (sin flujo de estados)
```

## Header estandarizado

```markdown
# Plan: Título descriptivo

**Estado:** Backlog | Coding | Done
**Backlog:** 2026-01-15
**Coding:** —
**Done:** —
**Dominio:** general
**Issue:** —
```

**Reglas del header:**
- El estado debe coincidir con el prefijo del nombre de archivo
- Las fechas registran cuándo ocurrió cada transición (`—` si no aplica)
- **Issue** es `—` si el issue tracker está configurado como "ninguno"

## Plantilla estándar

### Terminología obligatoria

| Término | Uso | Ejemplo |
|---------|-----|---------|
| **Fase** | Hito mayor de implementación | Fase 1: MVP, Fase 2: Mejoras |
| **Paso** | Ítem concreto del checklist de progreso | `- [ ] Crear migración SQL` |

### Orden de secciones

Header → Progreso → Objetivo → Contexto → Implementación → Verificación → Riesgos

Secciones opcionales se **omiten**, no se dejan vacías.

### Plantilla

```markdown
# Plan: Título descriptivo

**Estado:** Backlog
**Backlog:** YYYY-MM-DD
**Coding:** —
**Done:** —
**Dominio:** general
**Issue:** —

## Progreso

### Fase 1: MVP
- [ ] Paso concreto y verificable
- [ ] Otro paso

### Fase 2: Mejoras *(si aplica)*
- [ ] Paso concreto y verificable

## Objetivo

Qué se quiere lograr y por qué (1-3 párrafos).

## Contexto *(opcional)*

Estado actual, prerequisitos.

## Implementación

### Fase 1: MVP

Detalle técnico de la implementación.

### Fase 2: Mejoras *(opcional)*

## Verificación *(opcional)*

Pasos para validar que el plan se completó correctamente.

## Riesgos *(opcional)*

Solo para planes complejos.
```

### Reglas

1. **Progreso siempre después del header**, nunca al final
2. Pasos agrupados por fase (`### Fase N: Nombre`)
3. Cada paso debe ser concreto y verificable (no genérico)
4. Detalle técnico en Implementación, resumen en Progreso
5. Solo "Fase" y "Paso", nunca "Etapa"
6. Secciones opcionales se omiten, no se dejan vacías

## Flujo de trabajo

### Crear plan

1. Obtener siguiente ID secuencial (`NNNN`)
2. Crear archivo en `backlog/BACKLOG-YYYY-MM-DD-NNNN-descripción.md`

### Iniciar trabajo

1. Mover de `backlog/` a `coding/CODING-YYYY-MM-DD-NNNN-descripción.md` (fecha = hoy, ID no cambia)
2. Actualizar header: `Estado: Coding`, `Coding: YYYY-MM-DD`

### Completar

1. Mover de `coding/` a `done/DONE-YYYY-MM-DD-NNNN-descripción.md` (fecha = hoy)
2. Actualizar header: `Estado: Done`, `Done: YYYY-MM-DD`

### Devolver a backlog

1. Mover de `coding/` a `backlog/BACKLOG-YYYY-MM-DD-NNNN-descripción.md`
2. Actualizar header: `Estado: Backlog`

## Referencias cruzadas

Los planes se referencian entre sí usando el **ID interno** (`NNNN`), que es permanente:

```markdown
**Dependencias:** Plan 0001, Plan 0002

Ver plan 0003 para detalles.
```

**Regla:** nunca referenciar un plan por su nombre de archivo completo (cambia con cada transición). Siempre usar el ID interno.

## Obtener siguiente ID

```bash
# Buscar el mayor NNNN en todas las subcarpetas
ls workplan/{backlog,coding,done}/ | grep -oP '\d{4}' | sort -n | tail -1
# Sumar 1 al resultado
```

## Drafts (borradores y decisiones)

Los drafts se almacenan en `draft/` con formato `DRAFT-YYYY-MM-DD-descripción.md`. No siguen el flujo BACKLOG→CODING→DONE, no tienen ID secuencial. Son un banco de ideas: borradores de planes, decisiones técnicas, notas exploratorias. Cuando un draft madura lo suficiente, se promueve a `backlog/` como plan formal.
