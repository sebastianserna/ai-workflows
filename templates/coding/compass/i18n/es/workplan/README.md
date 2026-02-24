# Gestión de planes

> **Este archivo es la fuente de verdad para la gestión de planes.** Los agentes de IA deben seguir estas instrucciones al crear, mover o modificar planes.

## Configuración

**Issue tracker:** none
<!-- Opciones: GitHub | GitLab | none -->
<!-- Para activar: cambiar a "GitHub" o "GitLab" y configurar el repositorio -->

**Repositorio:** `usuario/nombre-del-repo`

## Formato de nombre de archivo

El formato depende de si hay un issue tracker configurado:

**Con issue tracker (GitHub / GitLab):**

```
TIPO-YYYY-MM-DD-iNNNN-descripción.md
```

**Sin issue tracker (none):**

```
TIPO-YYYY-MM-DD-descripción.md
```

| Segmento | Descripción | Ejemplo |
|----------|-------------|---------|
| `TIPO` | Estado: `BACKLOG`, `CODING`, `DONE`, `DRAFT` | `BACKLOG` |
| `YYYY-MM-DD` | Fecha de la transición al estado actual | `2026-01-15` |
| `iNNNN` | Número de issue, 4 dígitos zero-padded con prefijo `i` (solo con tracker) | `i0060` |
| `descripción` | Nombre corto en kebab-case | `user-auth-setup` |

### Identificador de issue (`iNNNN`)

Cuando hay un issue tracker configurado (GitHub o GitLab), cada plan **debe** tener un issue correspondiente. El número de issue se convierte en el identificador único del plan:

- El prefijo `i` distingue el número de issue de otros segmentos numéricos
- Zero-padded a 4 dígitos: issue #7 → `i0007`, issue #123 → `i0123`
- El identificador es **permanente** — no cambia cuando el plan se mueve entre estados
- GitHub/GitLab garantiza unicidad atómica, eliminando riesgos de colisión en entornos colaborativos

**Cuando el issue tracker es "none"**, los planes no tienen segmento de identificador. El nombre de archivo es simplemente `TIPO-YYYY-MM-DD-descripción.md`.

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
│   └── RULES.md
├── coding/            # Trabajo en progreso
│   └── RULES.md
├── done/              # Planes completados (archivo)
│   └── RULES.md
└── draft/             # Borradores, ideas y decisiones (sin flujo de estados)
    └── RULES.md
```

Cada `RULES.md` contiene reglas y convenciones de nomenclatura específicas de la carpeta:

- `backlog/RULES.md` — Punto de entrada para nuevos planes, instrucciones de creación de issues
- `coding/RULES.md` — Trabajo activo, reglas de transición y progreso
- `done/RULES.md` — Archivo, criterios de completado
- `draft/RULES.md` — Banco de ideas, sin flujo de trabajo, sin identificador de issue

## YAML Frontmatter

Cada archivo de plan debe comenzar con un bloque de YAML frontmatter en la **línea 1** (sin líneas en blanco antes del `---` de apertura). GitHub lo renderiza como una tabla de metadatos.

```yaml
---
plan: "Título descriptivo"
state: "backlog"
issue: ""
domain: "general"
backlog: "2026-01-15"
coding: ""
done: ""
---
```

**Campos del frontmatter:**

| Campo | Descripción | Valores |
|-------|-------------|---------|
| `plan` | Título descriptivo corto | Texto libre |
| `state` | Estado actual (debe coincidir con el prefijo del nombre de archivo) | `backlog`, `coding`, `done`, `draft` |
| `issue` | Identificador de issue (`iNNNN`) o vacío | `"i0060"`, `""` |
| `domain` | Dominio funcional | `general`, o específico del proyecto |
| `backlog` | Fecha de creación del plan | `"2026-01-15"`, `""` |
| `coding` | Fecha de inicio del trabajo | `"2026-01-20"`, `""` |
| `done` | Fecha de completado | `"2026-02-01"`, `""` |

**Reglas del frontmatter:**
- El primer `---` debe estar exactamente en la línea 1 sin líneas en blanco antes
- El valor de `state` debe coincidir con el prefijo del nombre de archivo (en minúsculas)
- **issue** es `""` si el issue tracker está configurado como "none"
- Cuando el tracker está activo, **issue** contiene el identificador: `"i0060"`
- Los borradores omiten los campos `issue` y de fechas por completo
- Los campos de fecha registran cuándo ocurrió cada transición (`""` si aún no se ha alcanzado)

## Plantilla estándar

### Terminología obligatoria

| Término | Uso | Ejemplo |
|---------|-----|---------|
| **Fase** | Hito mayor de implementación | Fase 1: MVP, Fase 2: Mejoras |
| **Paso** | Ítem concreto del checklist de progreso | `- [ ] Crear migración SQL` |

### Orden de secciones

Frontmatter → Progreso → Objetivo → Contexto → Implementación → Verificación → Riesgos

Secciones opcionales se **omiten**, no se dejan vacías.

### Plantilla

```markdown
---
plan: "Título descriptivo"
state: "backlog"
issue: ""
domain: "general"
backlog: "YYYY-MM-DD"
coding: ""
done: ""
---

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

1. **Progreso siempre después del frontmatter**, nunca al final
2. Pasos agrupados por fase (`### Fase N: Nombre`)
3. Cada paso debe ser concreto y verificable (no genérico)
4. Detalle técnico en Implementación, resumen en Progreso
5. Solo "Fase" y "Paso", nunca "Etapa"
6. Secciones opcionales se omiten, no se dejan vacías

## Flujo de trabajo

### Crear plan

**Con issue tracker:**

1. Crear el issue primero: `gh issue create` (GitHub) o `glab issue create` (GitLab)
2. Anotar el número de issue (ej. #60)
3. Crear archivo en `backlog/BACKLOG-YYYY-MM-DD-iNNNN-descripción.md` (ej. `BACKLOG-2026-01-15-i0060-user-auth-setup.md`)
4. Completar el campo `issue` del frontmatter con el identificador

**Sin issue tracker:**

1. Crear archivo en `backlog/BACKLOG-YYYY-MM-DD-descripción.md`

### Iniciar trabajo

1. Mover de `backlog/` a `coding/CODING-YYYY-MM-DD-...-descripción.md` (fecha = hoy, identificador no cambia)
2. Actualizar frontmatter: `state: "coding"`, `coding: "YYYY-MM-DD"`

### Completar

1. Mover de `coding/` a `done/DONE-YYYY-MM-DD-...-descripción.md` (fecha = hoy)
2. Actualizar frontmatter: `state: "done"`, `done: "YYYY-MM-DD"`

### Devolver a backlog

1. Mover de `coding/` a `backlog/BACKLOG-YYYY-MM-DD-...-descripción.md`
2. Actualizar frontmatter: `state: "backlog"`, `coding: ""`

## Referencias cruzadas

**Con issue tracker:** los planes se referencian entre sí usando el número de issue con `#N`, que es permanente y habilita auto-linking:

```markdown
**Dependencias:** #1, #2

Ver #3 para detalles.
```

**Sin issue tracker:** referenciar planes por su nombre descriptivo:

```markdown
**Dependencias:** user-auth-setup, api-rate-limiting
```

**Regla:** nunca referenciar un plan por su nombre de archivo completo (cambia con cada transición).

## Borradores

Los borradores se almacenan en `draft/` con formato `DRAFT-YYYY-MM-DD-descripción.md`. No siguen el flujo BACKLOG→CODING→DONE, no tienen identificador de issue. Son un banco de ideas: borradores de planes, decisiones técnicas, notas exploratorias. Cuando un borrador madura lo suficiente, se promueve a `backlog/` como plan formal.
