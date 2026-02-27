# Reglas: coding/

> Planes que se están trabajando activamente.

## Qué va aquí

- Planes actualmente en progreso
- Solo planes que están siendo implementados activamente

## Nomenclatura

```
CODING-YYYY-MM-DD-author_descripción.md
```

La fecha refleja cuándo se inició el trabajo.

## Reglas clave

- Cada plan debe tener YAML frontmatter con `state: "coding"` (ver `workplan/README.md` para el formato)
- Actualizar los checkboxes de progreso conforme se completan los pasos
- Al terminar: mover a `done/`, renombrar prefijo a `DONE`, actualizar fecha y frontmatter
- Para pausar: mover de vuelta a `backlog/`, renombrar prefijo a `BACKLOG`, actualizar frontmatter
- Ver `workplan/README.md` para la referencia completa

## Ejemplos

### Ejemplo mínimo

```markdown
---
plan: "Configuración de autenticación de usuarios"
state: "coding"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: ""
backlog: "2026-01-15"
coding: "2026-01-20"
done: ""
tags: "enhancement"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [x] Crear migración de base de datos para tabla de usuarios
- [x] Implementar generación y validación de tokens JWT
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
state: "coding"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: "https://github.com/user/repo/issues/60"
backlog: "2026-01-15"
coding: "2026-01-20"
done: ""
tags: "enhancement, auth"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [x] Crear migración de base de datos para tabla de usuarios
- [x] Implementar generación y validación de tokens JWT
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

## Comentarios

### 2026-01-20 — sebastianserna
Inicio de implementación. Migración y utilidades JWT completadas. Continuando con endpoints del API.

### 2026-01-21 — sebastianserna
Se decidió usar refresh tokens en lugar de JWTs de larga duración. Access token expira en 15 minutos, refresh token en 7 días.
```

## Ver también

- `backlog/README.md` — Reglas para planes pendientes
- `done/README.md` — Reglas para planes completados
- `draft/README.md` — Reglas para borradores e ideas
