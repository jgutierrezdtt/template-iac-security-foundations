# Paso 6. Reglas custom de iac

## Objetivo de aprendizaje

Entender que los checks por defecto no siempre bastan y que, incluso en un laboratorio básico, conviene expresar criterio propio dentro de la configuración del escáner.

## Que vas a cambiar y por que

En este paso vas a reforzar `.checkov.yml` como lugar donde se declara una política mínima propia. En este template, ese criterio se representa con la combinación de `framework:`, `check:` y `skip-check:`: suficiente para mostrar que el equipo no acepta ciegamente la configuración por defecto del escáner.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.checkov.yml`.
- Mantén el archivo corto y legible.
- Usa esta configuración para dejar claro qué aplica y qué queda explícitamente fuera del análisis inicial.

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

- Usa `check:` para mostrar qué controles consideras esenciales en el baseline.
- Usa `skip-check:` solo cuando la exclusión sea una decisión visible y no una forma de esconder ruido.
- Aunque sea una configuración mínima, debe leerse como política del equipo y no como accidente del tutorial.

## Que deberia verse al terminar

- Existe una política mínima propia dentro del archivo de configuración.
- La intención del control se entiende leyendo el archivo.
- El validador puede localizar los marcadores que representan ese criterio propio.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-06.py` comprueba este paso contra el archivo configurado.
- El workflow busca `framework:` dentro de `.checkov.yml`.
- El workflow busca `- terraform` dentro de `.checkov.yml`.
- El workflow busca `check:` dentro de `.checkov.yml`.
- El workflow busca `skip-check:` dentro de `.checkov.yml`.

## Criterio de finalizacion

El paso 6 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 7.
