# wisdom/ — Base de conocimiento

Esta carpeta contiene la documentación técnica del proyecto. Es la **fuente de verdad** que los agentes de IA consultan antes de tomar decisiones.

## Propósito

- Documentar decisiones de arquitectura y sus razones
- Mantener guías técnicas actualizadas
- Evitar que los agentes repitan errores o tomen decisiones inconsistentes
- Preservar conocimiento que no cabe en el código mismo

## Estructura

```
wisdom/
├── README.md           # Este archivo
├── architecture/       # Cómo está diseñado el sistema
├── development/        # Cómo se trabaja en el proyecto
└── operations/         # Cómo se despliega y opera
```

### architecture/

Decisiones de arquitectura, estructura del sistema, patrones elegidos y sus razones. Responde a **"cómo está diseñado y por qué"**.

Ejemplos: estructura de carpetas, patrón de capas, decisiones de librerías, diagramas de componentes.

### development/

Guías para el día a día del desarrollo. Responde a **"cómo trabajo en este proyecto"**.

Ejemplos: convenciones de código, guía de testing, flujo de git, setup local, linting.

### operations/

Todo lo relacionado con llevar el código a producción y mantenerlo corriendo. Responde a **"cómo se despliega y opera"**.

Ejemplos: pipeline de CI/CD, configuración de ambientes, monitoreo, variables de entorno.

## Cuándo agregar más carpetas

Las tres carpetas base cubren la mayoría de proyectos. Si el proyecto crece en un dominio específico, agregar carpetas dedicadas:

| Carpeta | Cuando agregarla |
|---------|-----------------|
| `database/` | El proyecto tiene base de datos propia con migraciones |
| `security/` | Reglas de auth, permisos o compliance que documentar |
| `integrations/` | Múltiples APIs externas o servicios de terceros |
| `api/` | API pública que otros consumen |

**Regla:** no crear carpetas vacías "por si acaso". Crear cuando haya al menos un documento real que poner dentro.

## Convenciones

- Documentos en Markdown, un tema por archivo
- Mantener actualizados cuando cambia la arquitectura
- Referenciar desde `AGENTS.md` en la sección "Especificaciones detalladas"

## Diferencia con workplan/

| | `wisdom/` | `workplan/` |
|---|-----------|-------------|
| **Contiene** | Documentación permanente | Planes de trabajo con ciclo de vida |
| **Cambia** | Cuando evoluciona la arquitectura | Constantemente (backlog → coding → done) |
| **Formato** | Libre | Plantilla estandarizada con header |
| **Propósito** | Entender el sistema | Gestionar qué se va a hacer |
