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

## Frontera del repositorio público

Este repositorio es público y debe contener únicamente reglas y plantillas genéricas que cualquier repositorio de b24cloud pueda reutilizar.

- No incluyas topología, inventario de infraestructura, nombres de host, IPs, rutas de secretos, detalles de despliegue ni know-how operativo.
- No menciones proveedores, cuentas, proyectos internos o servicios usados por la organización cuando no sean necesarios para contribuir.
- Guarda la documentación específica de ingeniería y las instrucciones operativas internas en el repositorio privado de ingeniería de la organización.

---

## Reglas de trabajo

- El **issue** es la fuente de verdad del alcance. No amplíes el alcance sin autorización explícita del mantenedor.
- La **PR** es el artefacto de implementación. Una PR por issue activo.
- **Nunca hagas commit ni push directamente a `main`** o a cualquier rama protegida.
- Trabaja siempre en una rama con prefijo según el tipo: `feat/`, `fix/`, `chore/`, `docs/`.
- Mantén la PR en **Draft** hasta haber superado todas las validaciones del repo.
- **Implementa SIEMPRE el set completo de tests mínimos** que se necesitan para asegurar que podemos cerrar la PR tranquilos, con una **cobertura mínima del 85%** en el código ejecutable nuevo o modificado.
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

Si el cambio toca código ejecutable, **es obligatorio implementar siempre el set completo de tests mínimos** con una cobertura mínima del **85%**. Si el repositorio carece de infraestructura de tests y configurarla excede el alcance autorizado del issue, detente y repórtalo en el issue para acordar su incorporación antes de marcar la PR como lista (en cambios puramente documentales o declarativos sin lógica ejecutable, documenta `N/A`).

### Paso 2 — Ejecutar en orden

1. **Lint / format check** — errores de estilo que el CI rechazará
2. **Typecheck** — TypeScript (`tsc --noEmit`), mypy, etc.
3. **Tests unitarios y cobertura (≥ 85%)** — toda la suite automatizada verificando el set completo de tests mínimos y cobertura ≥ 85% en código ejecutable (`--coverage`, `pytest --cov`, `go test -cover ./...`, etc.)
4. **Tests de integración** — si son ejecutables localmente
5. **Build de producción** — el artefacto final debe compilar sin errores

### Paso 3 — Criterio de paso

- ✅ Set completo de tests mínimos implementado (flujos principales, casos límite, errores y regresiones) con **cobertura ≥ 85%** en código ejecutable (o `N/A` justificado si no hay código ejecutable).
- ✅ Todos los checks en verde → puedes marcar la PR como Ready for review.
- ❌ Faltan tests del set mínimo, la cobertura es `< 85%` o algún check falla → corrige y amplía tests antes de continuar.
- Si el fallo es preexistente y no relacionado con tu cambio, documéntalo en el issue y no lo ignores.
- **Nunca abras ni marques una PR como lista con checks en rojo.**

### Paso 4 — Documentar en la PR

Incluye siempre la sección `## Validación` en el cuerpo de la PR con el formato definido en `PULL_REQUEST_TEMPLATE.md`.

---

## Precedencia de instrucciones

1. `AGENTS.md` en la raíz del repo destino (si existe)
2. Este `AGENTS.md` organizativo (`b24cloud/.github`)
3. Instrucciones específicas del modelo, si están disponibles
4. Decisiones concretas del mantenedor en el issue

Si dos reglas difieren, aplica la más restrictiva.
