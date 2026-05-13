# Paso 8. Integracion en github actions

## Objetivo de aprendizaje

Entender que un control IaC deja de ser opcional cuando entra en la ruta normal de cambios del repositorio y se ejecuta automáticamente sobre `push` y `pull_request`.

## Que vas a cambiar y por que

En este paso vas a definir `.github/workflows/iac.yml` para que el análisis de infraestructura se lance en eventos reales de desarrollo. El objetivo es mover el escaneo desde una comprobación manual o puntual a una puerta automatizada y repetible.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.github/workflows/iac.yml`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

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

- Usa un nombre de workflow que deje claro que analiza infraestructura.
- Mantén triggers de `push` y `pull_request` para que el control se vea antes del merge.
- Si el repositorio tiene varios directorios IaC, delimita la ruta en el comando de análisis.
- Mantén el job `checkov` como unidad clara de análisis para que la intención del workflow se entienda sin esfuerzo.

## Que deberia verse al terminar

- Existe un workflow específico para IaC.
- El job está orientado al escaneo, no mezclado con build o test de aplicación.
- La automatización se entiende al leer el YAML.
- Queda claro que el control se ejecuta en el flujo normal de colaboración del repositorio.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-08.py` comprueba este paso contra el archivo configurado.
- El workflow busca `name: IAC Security` dentro de `.github/workflows/iac.yml`.
- El workflow busca `pull_request:` dentro de `.github/workflows/iac.yml`.
- El workflow busca `push:` dentro de `.github/workflows/iac.yml`.
- El workflow busca `checkov:` dentro de `.github/workflows/iac.yml`.

## Criterio de finalizacion

El paso 8 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 9.
