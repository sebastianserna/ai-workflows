# Reglas: draft/

> Los borradores son un banco de ideas: borradores de planes, decisiones técnicas, notas exploratorias.

## Qué va aquí

- Ideas en etapa temprana que aún no están listas para backlog
- Registros de decisiones técnicas
- Notas exploratorias e investigación

## Nomenclatura

```
DRAFT-YYYY-MM-DD-descripción.md
```

Los borradores **nunca** llevan identificador de issue, independientemente de la configuración del tracker.

## Reglas clave

- Cada borrador debe tener YAML frontmatter con `state: "draft"` (ver `workplan/README.md` para el formato)
- Los borradores **no** siguen el flujo BACKLOG → CODING → DONE
- Cuando un borrador madura, se promueve a `backlog/` como plan formal
- Ver `workplan/README.md` para la referencia completa

## Ver también

- `backlog/RULES.md` — Reglas para planes pendientes
- `coding/RULES.md` — Reglas para planes en progreso
- `done/RULES.md` — Reglas para planes completados
