# Paso 8. Integracion en github actions

## Objetivo de aprendizaje

En este paso vas a practicar un control de IaC para entender que decision de configuracion aplicar y por que.

## Que debe hacer la persona participante

1. Revisar el contexto del control en este paso.
2. Editar la configuracion esperada en `.github/workflows/iac.yml`.
3. Guardar y subir el cambio en el flujo normal del repositorio (commit/push o PR).

## Que configurar exactamente

- Campo o seccion objetivo: relacionado con "Integracion en github actions".
- Ubicacion principal: `.github/workflows/iac.yml`.
- Resultado esperado: que la configuracion refleje el control del paso 8.

## Checklist de configuracion

- El cambio del paso 8 esta presente en `.github/workflows/iac.yml`.
- El cambio es coherente con el objetivo del paso.
- El repositorio incluye la evidencia de progreso para este paso.

## Validacion automatica (sin ejecucion manual)

- `validate-steps.yml` se ejecuta automaticamente por eventos `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-08.py` valida que el control de este paso esta aplicado.
- El estado de progreso se refleja en `.tutorial/state.json`.

## Criterio de finalizacion

El paso 8 se marca como completado cuando GitHub Actions reporta exito para `validate-step-08.py`.

Siguiente paso: Paso 9.
