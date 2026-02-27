# Reglas: backlog/

> Planes pendientes esperando a ser trabajados.

## Qué va aquí

- Planes que están definidos y listos para iniciar (o esperando priorización)
- Los nuevos planes entran aquí después de su creación

## Nomenclatura

```
BACKLOG-YYYY-MM-DD-author_descripción.md
```

La fecha refleja cuándo se creó el plan.

## Reglas clave

- Cada plan debe tener YAML frontmatter con `state: "backlog"` (ver `workplan/README.md` para el formato)
- Completar `author` (username) y otros campos relevantes del frontmatter
- Para iniciar trabajo: mover a `coding/`, renombrar prefijo a `CODING`, actualizar fecha y frontmatter
- Los planes también pueden ser devueltos aquí desde `coding/` si se pausan
- Ver `workplan/README.md` para la referencia completa

## Ejemplos

### Ejemplo mínimo

```markdown
---
plan: "Configuración de autenticación de usuarios"
state: "backlog"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: ""
assignee_model: ""
issue: ""
backlog: "2026-01-15"
coding: ""
done: ""
tags: "enhancement"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [ ] Crear migración de base de datos para tabla de usuarios
- [ ] Implementar generación y validación de tokens JWT
- [ ] Agregar endpoints de login y registro
- [ ] Crear middleware de autenticación

## Objetivo

Implementar autenticación de usuarios para la aplicación usando tokens JWT. Todos los endpoints del API necesitan verificar la identidad del usuario antes de desplegar cualquier funcionalidad orientada al usuario.

## Implementación

### Fase 1: MVP

Crear tabla `users` con `id`, `email`, `password_hash`, `created_at`. Usar bcrypt para hashing de contraseñas y jsonwebtoken para JWT. El middleware extraerá el token del header Authorization y adjuntará el usuario a `req.user`.
```

### Ejemplo completo

```markdown
---
plan: "Configuración de autenticación de usuarios"
state: "backlog"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: ""
assignee_model: ""
issue: "https://github.com/user/repo/issues/60"
backlog: "2026-01-15"
coding: ""
done: ""
tags: "enhancement, auth"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [ ] Crear migración de base de datos para tabla de usuarios
- [ ] Implementar generación y validación de tokens JWT
- [ ] Agregar endpoints de login y registro
- [ ] Crear middleware de autenticación

### Fase 2: Mejoras
- [ ] Agregar flujo de recuperación de contraseña
- [ ] Implementar rate limiting en endpoints de autenticación

## Objetivo

Implementar autenticación de usuarios para la aplicación usando tokens JWT. Es requisito antes de desplegar cualquier funcionalidad orientada al usuario, ya que todos los endpoints del API necesitan verificar la identidad del usuario.

## Contexto

La aplicación actualmente no tiene autenticación. La base de datos es PostgreSQL y el API está construido con Express. El frontend espera un Bearer token en el header Authorization.

## Implementación

### Fase 1: MVP

Crear tabla `users` con `id`, `email`, `password_hash`, `created_at`. Usar bcrypt para hashing de contraseñas y jsonwebtoken para JWT. El middleware extraerá el token del header Authorization y adjuntará el usuario a `req.user`.

### Fase 2: Mejoras

Agregar tabla `password_reset_tokens`. Implementar endpoint `/forgot-password` que envíe un enlace de recuperación y endpoint `/reset-password` que valide el token y actualice la contraseña.

## Verificación

- [ ] El registro crea un usuario y retorna un JWT válido
- [ ] El login con credenciales correctas retorna un JWT
- [ ] El login con credenciales incorrectas retorna 401
- [ ] Los endpoints protegidos rechazan solicitudes sin token válido
- [ ] El flujo de recuperación de contraseña envía email y permite cambiar contraseña

## Riesgos

- El secreto JWT debe almacenarse en variables de entorno, nunca en el repositorio
- El rate limiting es crítico para prevenir ataques de fuerza bruta en login
```

## Ver también

- `coding/README.md` — Reglas para planes en progreso
- `done/README.md` — Reglas para planes completados
- `draft/README.md` — Reglas para borradores e ideas
