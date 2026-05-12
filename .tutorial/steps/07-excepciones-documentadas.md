# Paso 7. Excepciones documentadas

## Objetivo de aprendizaje

Registrar desviaciones justificadas del baseline IaC.

## Archivo y seccion que debes modificar

- Archivo objetivo: `docs/iac-exceptions.yml`.
- Seccion donde aplicar el cambio: catálogo de excepciones IaC.
- Resultado esperado: el repositorio incorpora el control de este paso de forma legible y revisable.

## Cambio que debes introducir

Copia este bloque como base y adáptalo al contexto real del repositorio:

```yaml
exceptions:
  - check_id: CKV_AWS_20
    resource: aws_s3_bucket.app
    reason: "control temporal en migracion"
    expires_on: "2026-12-31"
```

## Como adaptarlo correctamente

- La excepción debe apuntar a un recurso concreto.
- Evita excepciones abiertas sin fecha de revisión.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-07.py` comprueba el archivo y los marcadores esperados de este paso.
- Debe encontrar el marcador `exceptions:` en `docs/iac-exceptions.yml`.
- Debe encontrar el marcador `check_id:` en `docs/iac-exceptions.yml`.
- Debe encontrar el marcador `resource:` en `docs/iac-exceptions.yml`.
- Debe encontrar el marcador `reason:` en `docs/iac-exceptions.yml`.
- Debe encontrar el marcador `expires_on:` en `docs/iac-exceptions.yml`.

## Criterio de finalizacion

El paso 7 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 8.
