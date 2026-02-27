# Reglas: done/

> Planes completados — archivo y referencia.

## Qué va aquí

- Planes que han sido completamente implementados y verificados
- Esta carpeta sirve como registro histórico

## Nomenclatura

```
DONE-YYYY-MM-DD-author_descripción.md
```

La fecha refleja cuándo se completó el plan.

## Reglas clave

- Cada plan debe tener YAML frontmatter con `state: "done"` (ver `workplan/README.md` para el formato)
- Todos los checkboxes de progreso deben estar marcados
- Los planes completados generalmente no se modifican
- Ver `workplan/README.md` para la referencia completa

## Ejemplos

### Ejemplo mínimo

```markdown
---
plan: "Configuración de autenticación de usuarios"
state: "done"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: ""
backlog: "2026-01-15"
coding: "2026-01-20"
done: "2026-02-01"
tags: "enhancement"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [x] Crear migración de base de datos para tabla de usuarios
- [x] Implementar generación y validación de tokens JWT
- [x] Agregar endpoints de login y registro
- [x] Crear middleware de autenticación

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
state: "done"
author: "sebastianserna"
author_model: "claude-opus-4"
assignee: "sebastianserna"
assignee_model: "claude-sonnet-4"
issue: "https://github.com/user/repo/issues/60"
backlog: "2026-01-15"
coding: "2026-01-20"
done: "2026-02-01"
tags: "enhancement, auth"
---

# Configuración de autenticación de usuarios

## Progreso

### Fase 1: MVP
- [x] Crear migración de base de datos para tabla de usuarios
- [x] Implementar generación y validación de tokens JWT
- [x] Agregar endpoints de login y registro
- [x] Crear middleware de autenticación

### Fase 2: Mejoras
- [x] Agregar flujo de recuperación de contraseña
- [x] Implementar rate limiting en endpoints de autenticación

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

- [x] El registro crea un usuario y retorna un JWT válido
- [x] El login con credenciales correctas retorna un JWT
- [x] El login con credenciales incorrectas retorna 401
- [x] Los endpoints protegidos rechazan solicitudes sin token válido
- [x] El flujo de recuperación de contraseña envía email y permite cambiar contraseña

## Comentarios

### 2026-01-20 — sebastianserna
Inicio de implementación. Migración y utilidades JWT completadas. Continuando con endpoints del API.

### 2026-01-21 — sebastianserna
Se decidió usar refresh tokens en lugar de JWTs de larga duración. Access token expira en 15 minutos, refresh token en 7 días.

### 2026-02-01 — sebastianserna
Todas las fases completadas. Rate limiting configurado a 5 intentos por minuto por IP. PR fusionado.
```

## Ver también

- `backlog/README.md` — Reglas para planes pendientes
- `coding/README.md` — Reglas para planes en progreso
- `draft/README.md` — Reglas para borradores e ideas
