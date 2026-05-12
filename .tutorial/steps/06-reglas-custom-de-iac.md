# Paso 6. Reglas custom de iac

## Objetivo de aprendizaje

Los checks por defecto no siempre cubren el baseline interno de tu organización. Este paso enseña a añadir criterio propio.

## Que vas a cambiar y por que

Introduce una regla o política personalizada que complemente el escaneo estándar.

## Archivo y seccion que debes modificar

- Archivo objetivo: `.checkov.yml`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```yaml
external-checks-dir: policies/checkov
framework:
  - terraform
```

## Como adaptarlo correctamente

- Si tu repositorio aún no tiene carpeta de políticas, créala junto a la configuración del escáner.
- La regla custom debe cubrir un requisito que no esté ya bien cubierto por los checks estándar.
- Describe el control con un nombre legible, no solo con un identificador interno.

## Que deberia verse al terminar

- Existe una política o regla adicional a la configuración base.
- La intención del control se entiende leyendo el archivo.
- El validador puede localizar los marcadores del control nuevo.

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
