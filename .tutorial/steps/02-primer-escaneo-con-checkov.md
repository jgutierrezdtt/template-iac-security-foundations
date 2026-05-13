# Paso 2. Primer escaneo con checkov

## Objetivo de aprendizaje

Entender que el primer escaneo útil no consiste solo en ejecutar una herramienta, sino en dejar claro qué tecnología analiza y qué política mínima de checks aplica sobre el repositorio.

## Que vas a cambiar y por que

Vas a crear o completar `.checkov.yml` para declarar el framework objetivo y una política mínima de control con `check:` y `skip-check:`. En un laboratorio de foundations, esto ayuda a que el escaneo sea entendible desde el primer momento: qué se está buscando y qué casos se dejan fuera de forma explícita.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.checkov.yml`.
- Si el archivo aún no existe, créalo en este paso.
- Mantén una configuración corta para que la intención del escáner se pueda leer de un vistazo.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```yaml
framework:
  - terraform
check:
  - CKV_AWS_20
skip-check:
  - CKV_AWS_21
```

## Como adaptarlo correctamente

- Usa solo el framework que realmente aparece en el repositorio, en este caso Terraform.
- Si añades `skip-check`, trátalo como una decisión visible del laboratorio y no como una omisión escondida.
- Mantén el archivo corto para que se entienda que controla el escáner.
- La combinación de `check:` y `skip-check:` debe dejar clara una política mínima y revisable.

## Que deberia verse al terminar

- Se ve claramente el framework que se analiza.
- Hay al menos un check explicitado y una exclusión declarada de forma visible.
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
