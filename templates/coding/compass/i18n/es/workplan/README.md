# Gestión de planes

> **Este archivo es la fuente de verdad para la gestión de planes.** Los agentes de IA deben seguir estas instrucciones al crear, mover o modificar planes.

## Formato de nombre de archivo

```
TIPO-YYYY-MM-DD-author_descripción.md
```

| Segmento | Descripción | Ejemplo |
|----------|-------------|---------|
| `TIPO` | Estado: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Fecha de la transición al estado actual | `2026-01-15` |
| `author` | Username del creador del plan en la plataforma de control de versiones (GitHub, GitLab, Bitbucket, etc.) | `sebastianserna` |
| `_` | Underscore separador entre author y descripción | `_` |
| `descripción` | Nombre corto en kebab-case | `user-auth-setup` |

### Identificador de autor

El username del creador en la plataforma de control de versiones (GitHub, GitLab, Bitbucket, etc.) funciona como identificador del plan:

- El underscore `_` separa el author de la descripción, evitando ambigüedad con usernames que contienen guiones
- El author es **permanente** — no cambia cuando el plan se mueve entre estados
- La unicidad está garantizada por la combinación de fecha + author + descripción
- Permite visibilidad inmediata de quién creó cada plan al listar archivos: `ls *sebastianserna*`
- **Múltiples autores:** el nombre de archivo siempre usa al **creador** (una persona). Si varias personas coautoran el plan, el campo `author` del frontmatter los lista separados por coma (ej. `"sebastianserna, juanperez"`), pero el nombre de archivo solo incluye al creador

### Regla de fecha

La fecha en el nombre de archivo refleja la transición al estado actual:

| Estado | Fecha en nombre = |
|--------|-------------------|
| BACKLOG | Fecha de creación del plan |
| CODING | Fecha de inicio de trabajo |
| DONE | Fecha de completado |
| DRAFT | Fecha de creación del borrador |

## Estructura de carpetas

```
workplan/
├── README.md          # Este archivo (fuente de verdad)
├── backlog/           # Planes pendientes
│   └── README.md
├── coding/            # Trabajo en progreso
│   └── README.md
├── done/              # Planes completados (archivo)
│   └── README.md
├── draft/             # Borradores, ideas y decisiones
│   └── README.md
└── guides/            # Base de conocimiento (arquitectura, desarrollo, operaciones)
    └── README.md
```

Cada `README.md` de subcarpeta contiene reglas, convenciones de nomenclatura y ejemplos embebidos (mínimo y completo) específicos de la carpeta:

- `backlog/README.md` — Punto de entrada para nuevos planes
- `coding/README.md` — Trabajo activo, reglas de transición y progreso
- `done/README.md` — Archivo, criterios de completado
- `draft/README.md` — Banco de ideas, borradores y decisiones
- `guides/README.md` — Vista general de la base de conocimiento y criterios de expansión

## YAML Frontmatter

Cada archivo de plan debe comenzar con un bloque de YAML frontmatter en la **línea 1** (sin líneas en blanco antes del `---` de apertura). GitHub lo renderiza como una tabla de metadatos.

**Todos los estados usan la misma estructura de frontmatter** (como un issue en Jira o Linear — mismos campos, solo cambian los valores):

```yaml
---
plan: "Título descriptivo"
state: "backlog"
author: ""
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: "2026-01-15"
coding: ""
done: ""
tags: ""
---
```

**Campos del frontmatter:**

| Campo | Descripción | Valores |
|-------|-------------|---------|
| `plan` | Título descriptivo corto | Texto libre |
| `state` | Estado actual (debe coincidir con el prefijo del nombre de archivo) | `backlog`, `coding`, `done`, `draft` |
| `author` | Username(s) del creador(es) del plan (de la plataforma de control de versiones) | `"sebastianserna"`, `"sebastianserna, juanperez"`, `""` |
| `author_model` | Modelo(s) de IA que crearon el plan | `"claude-opus-4"`, `"claude-opus-4, claude-sonnet-4"`, `""` |
| `assignee` | Username de la persona que implementa | `"sebastianserna"`, `""` |
| `assignee_model` | Modelo(s) de IA que ejecutaron el plan | `"claude-sonnet-4"`, `""` |
| `issue` | URL al issue vinculado (cualquier tracker) | `"https://github.com/user/repo/issues/60"`, `""` |
| `backlog` | Fecha de creación del plan | `"2026-01-15"`, `""` |
| `coding` | Fecha de inicio del trabajo | `"2026-01-20"`, `""` |
| `done` | Fecha de completado | `"2026-02-01"`, `""` |
| `tags` | Etiquetas para categorización (como labels de issue tracker) | `"enhancement"`, `"bug, api"`, `""` |

**Reglas del frontmatter:**
- El primer `---` debe estar exactamente en la línea 1 sin líneas en blanco antes
- El valor de `state` debe coincidir con el prefijo del nombre de archivo (en minúsculas)
- **Todos los campos están presentes en todos los estados** — vacíos (`""`) si aún no aplican
- Promover un borrador a backlog solo requiere actualizar `state` y la fecha `backlog` — sin cambio estructural
- `issue` es una URL completa a cualquier issue tracker (GitHub, Linear, Jira, etc.) — dejar vacío si no hay issue vinculado
- Todos los campos multi-valor (`author`, `author_model`, `assignee_model`, `tags`) usan strings separados por coma: `"claude-opus-4, claude-sonnet-4"`, `"enhancement, api"`
- El primer valor en `author` es el creador y debe coincidir con el author del nombre de archivo
- Los campos de fecha registran cuándo ocurrió cada transición (`""` si aún no se ha alcanzado)

## Plantilla estándar

### Terminología obligatoria

| Término | Uso | Ejemplo |
|---------|-----|---------|
| **Fase** | Hito mayor de implementación | Fase 1: MVP, Fase 2: Mejoras |
| **Paso** | Ítem concreto del checklist de progreso | `- [ ] Crear migración SQL` |

### Orden de secciones

Frontmatter → Título H1 → Progreso → Objetivo → Contexto → Implementación → Verificación → Riesgos → Comentarios

Secciones opcionales se **omiten**, no se dejan vacías.

### Plantilla

```markdown
---
plan: "Título descriptivo"
state: "backlog"
author: ""
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: "YYYY-MM-DD"
coding: ""
done: ""
tags: ""
---

# Título descriptivo

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

## Comentarios *(opcional)*

### YYYY-MM-DD — author
Texto del comentario: decisiones, bloqueos, actualizaciones de estado, cambios de contexto.
```

### Reglas

1. **Título H1 después del frontmatter** — debe coincidir con el valor del campo `plan`
2. **Progreso siempre después del H1**, nunca al final
3. Pasos agrupados por fase (`### Fase N: Nombre`)
4. Cada paso debe ser concreto y verificable (no genérico)
5. Detalle técnico en Implementación, resumen en Progreso
6. Solo "Fase" y "Paso", nunca "Etapa"
7. Secciones opcionales se omiten, no se dejan vacías
8. **Comentarios** siempre es la última sección, en orden cronológico (más antiguo primero)

## Flujo de trabajo

### Crear plan

1. Crear archivo en `backlog/BACKLOG-YYYY-MM-DD-author_descripción.md` (ej. `BACKLOG-2026-01-15-sebastianserna_user-auth-setup.md`)
2. Completar los campos del frontmatter (`author`, fecha `backlog`, `tags`, etc.)
3. *(Opcional)* Crear un issue en tu tracker y agregar la URL al campo `issue`

### Iniciar trabajo

1. Mover de `backlog/` a `coding/CODING-YYYY-MM-DD-author_descripción.md` (fecha = hoy, author no cambia)
2. Actualizar frontmatter: `state: "coding"`, `coding: "YYYY-MM-DD"`

### Completar

1. Mover de `coding/` a `done/DONE-YYYY-MM-DD-author_descripción.md` (fecha = hoy)
2. Actualizar frontmatter: `state: "done"`, `done: "YYYY-MM-DD"`

### Devolver a backlog

1. Mover de `coding/` a `backlog/BACKLOG-YYYY-MM-DD-author_descripción.md`
2. Actualizar frontmatter: `state: "backlog"`, `coding: ""`

## Referencias cruzadas

Referenciar planes por su nombre descriptivo, que es permanente entre transiciones de estado:

```markdown
**Dependencias:** user-auth-setup, api-rate-limiting
```

Si los planes tienen issues vinculados, también se pueden referenciar por número de issue para auto-linking:

```markdown
**Dependencias:** #1, #2

Ver #3 para detalles.
```

**Regla:** nunca referenciar un plan por su nombre de archivo completo (cambia con cada transición).

## Borradores

Los borradores se almacenan en `draft/` con formato `DRAFT-YYYY-MM-DD-author_descripción.md`. Usan la misma estructura de frontmatter que todos los demás estados. Son un banco de ideas: borradores de planes, decisiones técnicas, notas exploratorias. Cuando un borrador madura lo suficiente, se promueve a `backlog/` como plan formal — solo hay que actualizar `state` y la fecha `backlog`.
