# Paso 1. Plantilla iac basica insegura

## Objetivo de aprendizaje

Antes de escanear o remediar hace falta una plantilla mínima sobre la que trabajar. En este paso vas a crear una base S3 sencilla, todavía incompleta desde el punto de vista de endurecimiento, para que el resto del tutorial tenga un artefacto real que analizar.

## Que vas a cambiar y por que

Define en `iac/main.tf` un bucket y el bloque de control de acceso público que servirá como punto de partida. Aunque ya aparece una medida de protección, la plantilla sigue siendo básica y no representa un hardening completo; justamente por eso es útil como primer ejemplo revisable.

## Archivo y seccion que debes modificar

- Archivo objetivo: `iac/main.tf`.
- Si el archivo aún no existe, créalo en este paso.
- Mantén el cambio pequeño y centrado en el recurso S3 que se usará en el resto del recorrido.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "demo-bucket"
}

resource "aws_s3_bucket_public_access_block" "app" {
  bucket = aws_s3_bucket.app.id

  block_public_policy = true
}
```

## Como adaptarlo correctamente

- No conviertas este paso en la corrección final de todos los riesgos; aquí solo necesitas una base clara para escanear.
- Asegúrate de que el archivo contenga tanto el recurso `aws_s3_bucket` como el bloque `aws_s3_bucket_public_access_block`.
- Deja visible `block_public_policy` porque el validador usa ese marcador como parte de la estructura esperada.

## Que deberia verse al terminar

- Existe un archivo `iac/main.tf` con un bucket base y un bloque de acceso público asociado.
- La plantilla sigue siendo lo bastante simple como para usarla como ejemplo de análisis en los pasos siguientes.
- El siguiente paso puede escanear exactamente ese archivo sin cambiar de superficie.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-01.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 1 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 2.
