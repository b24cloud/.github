# Ciclo de Desarrollo

## Propósito

Definir la gobernanza mínima que deben compartir los repositorios de `b24cloud` sin meter complejidad innecesaria en el trabajo diario.

Este documento es la base organizativa. Cada repositorio puede añadir reglas operativas más estrictas, pero no debería debilitar estas mínimas.

## Principios mínimos

1. El issue es la fuente de verdad del alcance.
2. La pull request es el artefacto de implementación.
3. Por defecto hay una sola implementación activa por issue.
4. El merge siempre es una decisión humana.
5. La automatización debe centrarse en validar, no en gobernar tickets.

## Contrato mínimo del issue

Todo issue de implementación debería dejar claros estos apartados:

- `## Objetivo`
- `## Alcance`
- `## Tests o validación`
- `## Definición de hecho`

La estructura puede ser ligera, pero no debería obligar a humanos o agentes a adivinar el trabajo real.

## Contrato mínimo de la PR

Toda PR de implementación debe:

- referenciar el issue principal con `Closes #<issue-number>`
- permanecer en `Draft` hasta que esté realmente lista para revisión humana
- mantenerse dentro del alcance del issue
- incluir validaciones relevantes o explicar claramente por qué no aplican

## Modelo simple recomendado

Si el repositorio usa GitHub Project, el modelo recomendado por defecto es este:

| Estado | Significado |
|---|---|
| `Backlog` | Trabajo aceptado, pendiente de implementación |
| `In progress` | Trabajo en curso |
| `Review` | PR lista para revisión humana |
| `Done` | Cambio fusionado y operativamente completo para su alcance |

Notas prácticas:

- En cambios puramente documentales o internos, `Done` puede coincidir con el merge.
- En cambios operativos, `Done` debería significar merge más validación relevante.

## Política del Project

- Gestiona los estados del Project manualmente por defecto.
- Evita usar GitHub Actions para mover tickets o sincronizar estados salvo que exista una necesidad real y sostenida.
- El Project debe reflejar el estado del trabajo, no el detalle técnico del workflow.

## Política de automatización

- La automatización reusable debe vivir en `b24cloud/github-actions`.
- Los repositorios deben mantener wrappers mínimos en `.github/workflows/` cuando haga falta reaccionar a eventos locales.
- Evita automatizaciones cuyo único valor sea añadir fricción a issues, PRs o agentes.

## Política de overrides locales

Los repositorios pueden añadir reglas más detalladas para:

- cambios sensibles de producción
- despliegue y validación operativa
- backup y recovery
- controles de riesgo específicos del repositorio

Si hay conflicto, usa esta precedencia:

1. Base organizativa en `b24cloud/.github`
2. Reglas específicas del repositorio
3. Decisiones concretas del mantenedor en el issue
