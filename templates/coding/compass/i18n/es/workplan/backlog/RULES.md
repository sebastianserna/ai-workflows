# Reglas: backlog/

> Planes pendientes esperando a ser trabajados.

## Qué va aquí

- Planes que están definidos y listos para iniciar (o esperando priorización)
- Los nuevos planes entran aquí después de su creación

## Nomenclatura

**Con issue tracker (GitHub / GitLab):**

```
BACKLOG-YYYY-MM-DD-iNNNN-descripción.md
```

**Sin issue tracker:**

```
BACKLOG-YYYY-MM-DD-descripción.md
```

La fecha refleja cuándo se creó el plan.

## Reglas clave

- Cada plan debe tener YAML frontmatter con `state: "backlog"` (ver `workplan/README.md` para el formato)
- **Si hay un issue tracker configurado**, crear el issue primero (`gh issue create`, `glab issue create`, etc.) y usar el número de issue en el nombre de archivo (`iNNNN`)
- Para iniciar trabajo: mover a `coding/`, renombrar prefijo a `CODING`, actualizar fecha y header
- Los planes también pueden ser devueltos aquí desde `coding/` si se pausan
- Ver `workplan/README.md` para la referencia completa

## Ver también

- `coding/RULES.md` — Reglas para planes en progreso
- `done/RULES.md` — Reglas para planes completados
- `draft/RULES.md` — Reglas para borradores e ideas
