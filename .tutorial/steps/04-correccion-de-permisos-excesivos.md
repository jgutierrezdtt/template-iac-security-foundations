# Paso 4. Correccion de permisos excesivos

## Objetivo de aprendizaje

Un recurso en la nube con permisos excesivos suele quedar expuesto por una ACL o una policy demasiado abierta. El objetivo de este paso es cerrar esa exposición desde la propia plantilla.

## Que vas a cambiar y por que

Añade al recurso principal un control explícito de bloqueo de acceso público para que el repositorio muestre la corrección, no solo la describa.

## Archivo y seccion que debes modificar

- Archivo objetivo: `iac/main.tf`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```hcl
resource "aws_s3_bucket" "app" {
  bucket = "demo-bucket"
}

resource "aws_s3_bucket_public_access_block" "app" {
  bucket                  = aws_s3_bucket.app.id
  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
```

## Como adaptarlo correctamente

- Si el archivo `iac/main.tf` no existe todavía, créalo y coloca el recurso de ejemplo ahí.
- Mantén el nombre del bucket simple; lo importante del paso es el bloqueo público, no el naming.
- No mezcles este cambio con secretos, cifrado o versionado; aquí solo se corrige exposición pública.

## Que deberia verse al terminar

- Se ve un bucket y, justo después, un recurso `aws_s3_bucket_public_access_block` asociado a él.
- Los campos `block_public_acls`, `block_public_policy`, `ignore_public_acls` y `restrict_public_buckets` están a `true`.
- La corrección es legible sin tener que deducirla desde un comentario.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-04.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 4 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 5.
