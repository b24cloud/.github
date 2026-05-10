# Repositorio de configuración de la organización b24cloud

Este repositorio contiene las configuraciones y plantillas globales para todos los repositorios de la organización `b24cloud`.

## Limites y responsabilidades

- Este repositorio define estandares globales de colaboracion y community health.
- Aqui deben vivir plantillas de issue y PR, guias de contribucion y politicas.
- Aqui no deben vivir workflows de automatizacion de CI/CD ni logica ejecutable reusable.
- Los workflows reutilizables de despliegue, lifecycle y sincronizacion de Project viven en `b24cloud/github-actions`.
- Cada repositorio de servicio mantiene solo wrappers minimos en `.github/workflows/` para disparar eventos locales y delegar en `github-actions`.
- Si hay conflicto entre plantilla y automatizacion, la automatizacion reusable es la fuente de verdad operativa.

## Estructura

```
.github/
├── ISSUE_TEMPLATE/
│   ├── bug-report.yml
│   ├── configuration-issue.yml
│   ├── documentation.yml
│   ├── implementation-task.yml
│   └── config.yml
├── AGENTS.md
├── INFRASTRUCTURE.md
├── DEVELOPMENT-LIFECYCLE.md
├── AGENT-ASSIGNMENT-GUIDE.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── SECURITY.md
└── SUPPORT.md
```

## Contenido

- **`ISSUE_TEMPLATE/`**: Plantillas por defecto para bugs, configuraciones, documentación y tareas de implementación, además de la configuración global de issue templates.
- **`AGENTS.md`**: Instrucciones universales para agentes de desarrollo (Claude Code, GitHub Copilot, Codex, Cursor y similares).
- **`INFRASTRUCTURE.md`**: Documentación del stack de infraestructura (nodos, servicios, CI/CD, secretos, red).
- **`DEVELOPMENT-LIFECYCLE.md`**: Baseline organizacional del ciclo de trabajo con issues, PRs y Project.
- **`AGENT-ASSIGNMENT-GUIDE.md`**: Reglas base de asignación para agentes de implementación.
- **`CONTRIBUTING.md`**: Guía para contribuir al código de la organización.
- **`CODE_OF_CONDUCT.md`**: Código de conducta para la comunidad.
- **`SECURITY.md`**: Política de seguridad y cómo reportar vulnerabilidades.
- **`SUPPORT.md`**: Información sobre cómo obtener soporte.

## Uso

Estas plantillas y guías se aplican como baseline a los repositorios de la organización cuando no hay una definición local más específica.

## Contacto

Para más información, contacta al equipo de soporte de `b24cloud`.
