# Reglas: done/

> Planes completados — archivo y referencia.

## Qué va aquí

- Planes que han sido completamente implementados y verificados
- Esta carpeta sirve como registro histórico

## Nomenclatura

**Con issue tracker (GitHub / GitLab):**

```
DONE-YYYY-MM-DD-iNNNN-descripción.md
```

**Sin issue tracker:**

```
DONE-YYYY-MM-DD-descripción.md
```

La fecha refleja cuándo se completó el plan.

## Reglas clave

- Cada plan debe tener YAML frontmatter con `state: "done"` (ver `workplan/README.md` para el formato)
- Todos los checkboxes de progreso deben estar marcados
- Los planes completados generalmente no se modifican
- Ver `workplan/README.md` para la referencia completa

## Ver también

- `backlog/RULES.md` — Reglas para planes pendientes
- `coding/RULES.md` — Reglas para planes en progreso
- `draft/RULES.md` — Reglas para borradores e ideas
