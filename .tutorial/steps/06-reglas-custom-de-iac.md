# Paso 6. Reglas custom de iac

## Objetivo de aprendizaje

Definir el alcance del análisis y las reglas que deben aplicarse.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.checkov.yml`.
- Seccion donde aplicar el cambio: configuración del escáner IaC.
- Resultado esperado: el repositorio incorpora el control de este paso de forma legible y revisable.

## Cambio que debes introducir

Copia este bloque como base y adáptalo al contexto real del repositorio:

```yaml
framework:
  - terraform
check:
  - CKV_AWS_20
skip-check:
  - CKV_AWS_18
```

## Como adaptarlo correctamente

- No añadas skips permanentes sin documentar el motivo.
- Mantén solo checks relevantes para el tipo de plantilla del repositorio.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-06.py` comprueba el archivo y los marcadores esperados de este paso.
- Debe encontrar el marcador `framework:` en `.checkov.yml`.
- Debe encontrar el marcador `- terraform` en `.checkov.yml`.
- Debe encontrar el marcador `check:` en `.checkov.yml`.
- Debe encontrar el marcador `skip-check:` en `.checkov.yml`.

## Criterio de finalizacion

El paso 6 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 7.
