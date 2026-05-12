# Paso 2. Primer escaneo con checkov

## Objetivo de aprendizaje

El escáner no aporta valor si no queda claro qué tecnología debe analizar y qué controles son relevantes para el ejemplo.

## Que vas a cambiar y por que

Declara en `.checkov.yml` el framework y los checks que vas a usar en el tutorial.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.checkov.yml`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```yaml
framework:
  - terraform
check:
  - CKV_AWS_20
```

## Como adaptarlo correctamente

- Usa solo el framework que realmente aparece en el repositorio, en este caso Terraform.
- No añadas `skip-check` gratuitos si todavía no has explicado la excepción.
- Mantén el archivo corto para que se entienda que controla el escáner.

## Que deberia verse al terminar

- Se ve claramente el framework que se analiza.
- Hay al menos un check explicitado o una política del escáner clara.
- El archivo sirve de entrada para el workflow automático.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-02.py` comprueba este paso contra el archivo configurado.
- El workflow busca `framework:` dentro de `.checkov.yml`.
- El workflow busca `- terraform` dentro de `.checkov.yml`.
- El workflow busca `check:` dentro de `.checkov.yml`.
- El workflow busca `skip-check:` dentro de `.checkov.yml`.

## Criterio de finalizacion

El paso 2 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 3.
