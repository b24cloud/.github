## Descripción

<!-- Explica qué cambia y por qué. Sé concreto. -->

Closes #<!-- número del issue -->

---

## Tipo de cambio

- [ ] `feat` — nueva funcionalidad
- [ ] `fix` — corrección de bug
- [ ] `chore` — mantenimiento, dependencias, configuración
- [ ] `docs` — documentación
- [ ] `refactor` — sin cambio de comportamiento externo

---

## Validación

<!-- Obligatorio. Documenta qué checks has ejecutado y su resultado. -->

| Check | Comando | Resultado |
|-------|---------|----------|
| Lint | `...` | PASS |
| Typecheck | `...` | PASS / N/A |
| Tests | `...` | PASS / N/A |
| Coverage (≥ 85%) | `...` | PASS (<X>%) / N/A |
| Build | `...` | PASS |

**Validaciones no ejecutadas** (si aplica):
<!-- Justifica la razón y el riesgo asociado. Si no hay ninguna, borra esta línea. -->

---

## Checklist

- [ ] La rama **no es `main`** — trabajé en `feat/`, `fix/`, `chore/` o `docs/`
- [ ] He implementado el set completo de tests mínimos para cerrar la PR con tranquilidad (cobertura ≥ 85% en código ejecutable, o N/A justificado)
- [ ] Todos los checks de la tabla anterior están en PASS
- [ ] No he modificado archivos fuera del alcance del issue
- [ ] No he incluidos secretos, credenciales, tokens, claves, datos personales, endpoints internos ni detalles de infraestructura; los ejemplos están redactados
- [ ] La PR incluye `Closes #<número>` vinculado al issue
- [ ] He revisado el diff completo antes de marcar como Ready for review
