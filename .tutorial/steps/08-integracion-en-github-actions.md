# Paso 8. Integracion en github actions

## Objetivo de aprendizaje

Ejecutar el escaneo IaC automáticamente en cada cambio relevante.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.github/workflows/iac.yml`.
- Seccion donde aplicar el cambio: workflow de escaneo IaC.
- Resultado esperado: el repositorio incorpora el control de este paso de forma legible y revisable.

## Cambio que debes introducir

Copia este bloque como base y adáptalo al contexto real del repositorio:

```yaml
name: IAC Security
on:
  pull_request:
  push:
jobs:
  checkov:
    runs-on: ubuntu-latest
```

## Como adaptarlo correctamente

- Ejecuta el análisis en PRs para detectar riesgos antes del merge.
- Si el repositorio tiene varios directorios IaC, especifica bien la ruta de análisis.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-08.py` comprueba el archivo y los marcadores esperados de este paso.
- Debe encontrar el marcador `name: IAC Security` en `.github/workflows/iac.yml`.
- Debe encontrar el marcador `pull_request:` en `.github/workflows/iac.yml`.
- Debe encontrar el marcador `push:` en `.github/workflows/iac.yml`.
- Debe encontrar el marcador `checkov:` en `.github/workflows/iac.yml`.

## Criterio de finalizacion

El paso 8 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 9.
