# Reglas: draft/

> Los borradores son un banco de ideas: borradores de planes, decisiones técnicas, notas exploratorias.

## Qué va aquí

- Ideas en etapa temprana que aún no están listas para backlog
- Registros de decisiones técnicas
- Notas exploratorias e investigación

## Nomenclatura

```
DRAFT-YYYY-MM-DD-author_descripción.md
```

## Reglas clave

- Cada borrador debe tener YAML frontmatter con `state: "draft"` (ver `workplan/README.md` para el formato)
- Los borradores usan la misma estructura de frontmatter que todos los demás estados
- Los borradores **no** siguen el flujo BACKLOG → CODING → DONE
- Cuando un borrador madura, se promueve a `backlog/` — solo actualizar `state` y fecha `backlog`
- Ver `workplan/README.md` para la referencia completa

## Ejemplos

### Ejemplo mínimo

```markdown
---
plan: "Estrategia de rate limiting para API"
state: "draft"
author: "sebastianserna"
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: ""
coding: ""
done: ""
tags: "architecture"
---

# Estrategia de rate limiting para API

## Contexto

El API actualmente no tiene rate limiting. Después de desplegar la autenticación, se observaron intentos automatizados de login desde múltiples IPs. Se necesita una estrategia antes de abrir el API a consumidores externos.

## Opciones consideradas

### Opción A: Middleware de Express (express-rate-limit)
- Ventajas: configuración simple, sin dependencias externas
- Desventajas: solo por instancia, no apto para despliegues multi-instancia

### Opción B: Basado en Redis (rate-limiter-flexible)
- Ventajas: compartido entre instancias, soporta ventana deslizante
- Desventajas: requiere infraestructura Redis

## Decisión

Inclinación hacia Opción B ya que ya usamos Redis para sesiones. Se promoverá a `backlog/` una vez definidos los límites por endpoint.
```

### Ejemplo completo

```markdown
---
plan: "Estrategia de rate limiting para API"
state: "draft"
author: "sebastianserna"
author_model: ""
assignee: ""
assignee_model: ""
issue: ""
backlog: ""
coding: ""
done: ""
tags: "architecture, api"
---

# Estrategia de rate limiting para API

## Contexto

El API actualmente no tiene rate limiting. Después de desplegar el sistema de autenticación, se observaron intentos automatizados de login desde múltiples IPs. Necesitamos una estrategia de rate limiting antes de abrir el API a consumidores externos.

## Opciones consideradas

### Opción A: Middleware de Express (express-rate-limit)
- Ventajas: configuración simple, en memoria por defecto, sin dependencias externas
- Desventajas: solo por instancia, se reinicia con la app, no apto para despliegues multi-instancia

### Opción B: Basado en Redis (rate-limiter-flexible)
- Ventajas: compartido entre instancias, persistente, soporta ventana deslizante
- Desventajas: requiere infraestructura Redis, complejidad operacional adicional

### Opción C: API Gateway (proveedor cloud)
- Ventajas: sin cambios de código, servicio gestionado, incluye protección DDoS
- Desventajas: dependencia de proveedor, menor control granular, mayor costo

## Decisión

Cuando el borrador madure, se promueve a `backlog/` como plan formal.

## Comentarios

### 2026-01-25 — sebastianserna
Borrador inicial después de observar intentos automatizados de login. Inclinación hacia Opción B ya que ya usamos Redis para sesiones.

### 2026-01-28 — juanperez
Confirmado que Redis está disponible en todos los entornos. Opción B es viable. Falta definir límites por endpoint.
```

## Ver también

- `backlog/README.md` — Reglas para planes pendientes
- `coding/README.md` — Reglas para planes en progreso
- `done/README.md` — Reglas para planes completados
