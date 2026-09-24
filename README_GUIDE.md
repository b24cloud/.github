# Guía de READMEs — b24cloud

> Estructura minimalista tipo big-tech. Un README debe entenderse en 30s.

## Filosofía

- **Un propósito**: explicar qué es, con qué está hecho y cómo arrancarlo.
- **5 secciones fijas**. Nada más en el README. El detalle va en `docs/`.
- **Español** para repos internos/privados. Inglés solo si el repo es público/open-source.

## Estructura estándar

| Orden | Sección | Obligatoria | Contenido |
|-------|---------|-------------|-----------|
| 1 | `# título` + `> tagline` | Sí | Nombre del repo + descripción de 1 línea (qué + para quién) |
| 2 | `## Stack` | Sí | 3-6 bullets `**Tecnología** — Propósito` (no versiones) |
| 3 | `## Quick Start` | Sí | 3-4 comandos copy-paste que dejan el servicio en `up` |
| 4 | `## Docs` | Sí | 1-3 links relativos a `docs/` o archivos clave (`AGENTS.md`, `CONTRIBUTING.md`) |
| 5 | `## License` | Sí | La licencia declarada por ese repositorio; no se presupone una licencia OSS |

> Si necesitas arquitectura, variables de entorno, despliegue o troubleshooting → `docs/` (ej: `docs/ARCHITECTURE.md`, `docs/DEPLOYMENT.md`). En repositorios públicos, la documentación debe permanecer sanitizada: sin topología, endpoints internos, rutas de secretos, inventarios ni procedimientos operativos internos.

## Reglas por sección

### Título + tagline
```md
# nombre-del-repo

> Qué hace + para quién, en 1 frase sin tecnicismos.
```
Mal: `> Repo de backend`. Bien: `> API multi-tenant para reservas de pistas y facturación de clubes`.

### Stack
- Solo tecnologías que un nuevo dev necesita para ubicarse.
- Formato `**Nombre** — Rol`. Sin badges, sin tabla de versiones.
- Orden: runtime/framework → base de datos → infra.

### Quick Start
- Debe funcionar con `git clone` + `cp .env.example .env` + `docker compose up -d` (o el comando de desarrollo del proyecto si aplica).
- No documentes todos los comandos; 1 bloque es suficiente.
- Si el setup requiere configuración adicional, linka a `docs/SETUP.md` sin incluir valores sensibles.

### Docs
- Usa links relativos, no absolutos, y solo enlaza a archivos que existen.
- Si el repo no tiene `docs/`, usa el texto `Documentación: docs/` como placeholder, sin convertirlo en un enlace vacío.

### License
- Indica la licencia declarada por ese repositorio.
- Si es open source, añade un archivo `LICENSE` y enlázalo.
- Si es privado o proprietary, declara explícitamente la política de la organización.

## Ejemplo completo

Ver [`README_TEMPLATE.md`](README_TEMPLATE.md).

## Checklist

- [ ] Título = nombre del repo en `kebab-case`
- [ ] Tagline < 120 caracteres
- [ ] Stack 3-6 bullets, sin versiones fijadas
- [ ] Quick Start probado con repo limpio
- [ ] Docs apunta a archivos que existen
- [ ] Descripción corta del repo en GitHub (Settings) coincide con tagline

## Anti-patrones

- README de 500 líneas con toda la arquitectura → mueve a `docs/`.
- Badges decorativos sin valor (coverage, etc.) en repos privados.
- `Quick Start` con 10 pasos manuales → automatiza en `docker compose` o script.
- Mezclar español e inglés en el mismo README.
- Incluir secretos, credenciales, IPs, nombres de host o detalles de producción en un README público.
- Duplicar en README lo que ya está en `docker-compose.yml` o `.env.template`.

## Referencia

Plantilla: [`README_TEMPLATE.md`](README_TEMPLATE.md)
Estándar global: [`AGENTS.md`](AGENTS.md) · [`CONTRIBUTING.md`](CONTRIBUTING.md)
