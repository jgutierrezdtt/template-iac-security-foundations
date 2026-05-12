# Paso 3. Interpretacion de hallazgos

## Objetivo de aprendizaje

Dejar por escrito los hallazgos, su criticidad y el plan de remediación.

## Archivo y seccion que debes modificar

- Archivo objetivo: `docs/iac-reporting.md`.
- Seccion donde aplicar el cambio: reporte de hallazgos y decisiones.
- Resultado esperado: el repositorio incorpora el control de este paso de forma legible y revisable.

## Cambio que debes introducir

Copia este bloque como base y adáptalo al contexto real del repositorio:

```markdown
## Hallazgos
## Recursos afectados
## Riesgo
## Plan de remediacion
```

## Como adaptarlo correctamente

- Enlaza cada hallazgo con el recurso Terraform o CloudFormation afectado.
- Explica qué cambio elimina el riesgo y en qué plazo.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-03.py` comprueba el archivo y los marcadores esperados de este paso.
- Debe encontrar el marcador `## Hallazgos` en `docs/iac-reporting.md`.
- Debe encontrar el marcador `## Recursos afectados` en `docs/iac-reporting.md`.
- Debe encontrar el marcador `## Riesgo` en `docs/iac-reporting.md`.
- Debe encontrar el marcador `## Plan de remediacion` en `docs/iac-reporting.md`.

## Criterio de finalizacion

El paso 3 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 4.
