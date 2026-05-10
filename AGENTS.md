# AGENTS.md — b24cloud

Instrucciones universales para agentes de desarrollo (Claude Code, GitHub Copilot, Codex, Cursor y similares).

Todos los agentes deben seguir estas reglas en cualquier repositorio de la organización `b24cloud`.
Los repositorios pueden añadir reglas más estrictas en su propio `AGENTS.md` local.

---

## Visibilidad de repositorios

**Todos los repositorios nuevos deben crearse como `private` por defecto.**

- Nunca crear un repositorio con visibilidad pública sin autorización explícita del mantenedor.
- Al crear un repositorio mediante herramienta, API o agente, usar siempre el parámetro `private: true`.
- Cualquier excepción debe estar documentada y aprobada expresamente por el mantenedor antes de proceder.

---

## Reglas de trabajo

- El **issue** es la fuente de verdad del alcance. No amplíes el alcance sin autorización explícita del mantenedor.
- La **PR** es el artefacto de implementación. Una PR por issue activo.
- **Nunca hagas commit ni push directamente a `main`** o a cualquier rama protegida.
- Trabaja siempre en una rama con prefijo según el tipo: `feat/`, `fix/`, `chore/`, `docs/`.
- Mantén la PR en **Draft** hasta haber superado todas las validaciones del repo.
- No modifiques archivos no relacionados con el issue.
- No hagas merge de la PR como agente.
- Si hay bloqueo o ambigüedad, reporta el problema en el issue en vez de adivinar.
- Incluye `Closes #<issue-number>` en el cuerpo de la PR.

---

## Validación obligatoria antes de marcar la PR Ready for review

Este proceso es **obligatorio e independiente del stack** del repositorio.

### Paso 1 — Descubrir el test runner

Busca en este orden qué mecanismo de validación existe en el repositorio destino:

| Prioridad | Archivo a buscar | Comandos a ejecutar |
|-----------|-----------------|---------------------|
| 1 | `package.json` | `npm run lint`, `npm test`, `npm run build` |
| 2 | `pyproject.toml` / `setup.py` | `ruff check .` / `flake8`, `pytest`, `python -m build` |
| 3 | `Cargo.toml` | `cargo clippy`, `cargo test`, `cargo build` |
| 4 | `go.mod` | `golangci-lint run`, `go test ./...`, `go build ./...` |
| 5 | `composer.json` | `composer run lint`, `composer run test` |
| 6 | `Makefile` | `make lint`, `make test`, `make build` (o targets equivalentes) |
| 7 | `.github/workflows/` | Replica localmente los pasos del job de CI |
| 8 | `README.md` / `CONTRIBUTING.md` | Sigue las instrucciones de desarrollo indicadas |

Si no existe ningún mecanismo, ejecuta como mínimo un build de comprobación y **abre un issue separado** proponiendo añadir tests.

### Paso 2 — Ejecutar en orden

1. **Lint / format check** — errores de estilo que el CI rechazará
2. **Typecheck** — TypeScript (`tsc --noEmit`), mypy, etc.
3. **Tests unitarios** — toda la suite automatizada
4. **Tests de integración** — si son ejecutables localmente
5. **Build de producción** — el artefacto final debe compilar sin errores

### Paso 3 — Criterio de paso

- ✅ Todos los checks en verde → puedes marcar la PR como Ready for review.
- ❌ Algún check falla → corrige antes de continuar.
- Si el fallo es preexistente y no relacionado con tu cambio, documéntalo en el issue y no lo ignores.
- **Nunca abras ni marques una PR como lista con checks en rojo.**

### Paso 4 — Documentar en la PR

Incluye siempre la sección `## Validación` en el cuerpo de la PR con el formato definido en `PULL_REQUEST_TEMPLATE.md`.

---

## Precedencia de instrucciones

1. `AGENTS.md` en la raíz del repo destino (si existe)
2. Este `AGENTS.md` organizativo (`b24cloud/.github`)
3. `CLAUDE.md` / instrucciones específicas del modelo
4. Decisiones concretas del mantenedor en el issue

Si dos reglas difieren, aplica la más restrictiva.
