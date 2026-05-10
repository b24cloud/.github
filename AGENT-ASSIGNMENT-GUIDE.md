# Guía de Asignación para Agentes

## Propósito

Dar una base reutilizable y ligera para asignar trabajo a agentes en los repositorios de `b24cloud`.

El issue define el trabajo. El texto de asignación solo debería fijar restricciones de ejecución y calidad.

## Plantilla corta por defecto

```text
Trabaja solo en este issue y no amplíes el alcance.

Sigue la gobernanza organizativa en b24cloud/.github y las reglas específicas del repositorio.

Reglas de ejecución:
- Usa una sola rama y una sola PR para este issue, salvo instrucción explícita en contra
- Prefiere el nombre de rama issue-<issue-number>-<short-slug>
- Incluye Closes #<issue-number> en el cuerpo de la PR
- Mantén la PR en Draft hasta que esté realmente lista para revisión humana
- No hagas merge de la PR
- No modifiques archivos no relacionados
- Añade o actualiza validaciones cuando proceda
- Si algo es ambiguo o está bloqueado, detente y repórtalo claramente en la PR
```

## Añadidos opcionales

### Issue solo de documentación

```text
Este issue es solo de documentación. No cambies comportamiento runtime, workflows, scripts ni lógica de despliegue.
```

### Issue operativo sensible

```text
Este issue afecta a comportamiento operativo. Mantén los cambios mínimos y no alteres despliegue, backup o recovery salvo que el issue lo exija explícitamente.
```

## Lista rápida para mantenedores

- el issue tiene alcance claro
- el issue deja claro qué validar
- la asignación no reescribe innecesariamente todo el issue
- las restricciones adicionales solo se añaden si son realmente específicas

## Política de overrides locales

Los repositorios pueden añadir restricciones más estrictas por:

- seguridad operativa
- despliegue, backup o recovery
- automatización sensible
- riesgos específicos del repositorio

Las reglas locales deben extender esta base, no debilitarla.
