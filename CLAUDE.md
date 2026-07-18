# CLAUDE.md — b24cloud

Instrucciones adicionales para **Claude Code** en los repositorios de la organización `b24cloud`.
Estas instrucciones complementan `AGENTS.md`; en caso de conflicto, aplica la regla más restrictiva.

---

## Contexto de arquitectura b24cloud

- **Infra:** Oracle Cloud — 2 tenants:
  - `b24cloud` (tenant principal): nodo **srv** (`ssh.b24cloud.com`)
  - `b24cloud-rosa` (tenant secundario): nodos **runner** (`runner.b24cloud.com`) y **vollery** (`82.70.88.234`)
  - Red local: **hp** HPE Microserver (`192.168.1.5`) + **PC** (`immich-pc-oriol`, RTX 4080)
  - Cloudflare (Workers, Pages, Tunnel)
- **CI/CD:** GitHub Actions con workflows reutilizables centralizados en `b24cloud/github-actions`.
- **Secrets:** Infisical como fuente de verdad; GitHub Secrets como fallback operativo.
- **Identity:** Keycloak SSO + Infisical Machine Identities (OIDC) por repositorio.
- **Runner:** Self-hosted efímero en **runner** (labels: `self-hosted,linux,arm64`).
- **Containers:** Docker en **srv**, **hp** y **vollery**.

---

## Convenciones de naming

| Elemento | Patrón | Ejemplo |
|----------|--------|---------|
| Ramas | `<tipo>/<descripcion-corta>` | `feat/login-page`, `fix/token-refresh` |
| Commits | Conventional Commits (`<tipo>(<scope>): <desc>`) | `feat(auth): add OIDC login flow` |
| Workflows reutilizables | `b24cloud/github-actions/.github/workflows/<nombre>.yml` | `deploy-cloudflare-pages.yml` |
| Machine Identities | `<repo-name>` | `vollery-web`, `pulsari-app` |
| Secrets en Infisical | `SCREAMING_SNAKE_CASE` bajo `/services/<repo>/` | `/services/vollery-web/CLOUDFLARE_API_TOKEN` |

---

## Reglas operativas específicas

- **Nunca hagas commit ni push directo a `main`** salvo orden explícita del mantenedor en la sesión activa.
- **No abras una PR ni la marques como Ready for review si hay tests o checks fallando.** Esto incluye checks de lint, typecheck, build y cualquier status check configurado en el repo.
- Cuando crees un workflow de GitHub Actions, **reutiliza los workflows de `b24cloud/github-actions`** en lugar de duplicar lógica. Crea wrappers mínimos en el repo destino.
- Si necesitas añadir un secreto, documenta el path de Infisical correspondiente en el PR body.
- Ante cualquier duda sobre el alcance, **pregunta antes de implementar**.
- No instales dependencias globales en el runner sin justificación explícita.

---

## Stack por tipo de proyecto

| Tipo | Stack habitual | Test runner |
|------|---------------|-------------|
| Frontend web | Next.js / Astro + TypeScript + Tailwind | Vitest / Playwright |
| Workers | Cloudflare Workers + TypeScript | Vitest |
| Backend API | Node.js / Hono + TypeScript | Vitest |
| Infra scripts | Bash / Python | shellcheck / pytest |
| Workflows CI | YAML (GitHub Actions) | `actionlint` |

---

## Modelo de automatización

- Los workflows reutilizables viven en `b24cloud/github-actions`.
- Los repos mantienen wrappers mínimos en `.github/workflows/` para disparar eventos locales.
- Evita automatizaciones que gestionen estados de tickets o Projects si no aportan valor operativo claro.
