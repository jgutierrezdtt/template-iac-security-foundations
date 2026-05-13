# Paso 4. Correccion de permisos excesivos

## Objetivo de aprendizaje

Entender cómo se corrige una exposición por permisos excesivos directamente en la plantilla IaC, sin depender de acciones manuales posteriores en la consola cloud.

## Que vas a cambiar y por que

En este paso vas a reforzar `iac/main.tf` con un bloqueo explícito de acceso público sobre el bucket principal. El valor del cambio no está solo en "tener el flag", sino en dejar escrita la intención de mínimo privilegio dentro del código de infraestructura.

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
- Piensa en este recurso como una evidencia visible de que la exposición se remedia en código y no fuera del repositorio.

## Que deberia verse al terminar

- Se ve un bucket y, justo después, un recurso `aws_s3_bucket_public_access_block` asociado a él.
- Los campos `block_public_acls`, `block_public_policy`, `ignore_public_acls` y `restrict_public_buckets` están a `true`.
- La corrección es legible sin tener que deducirla desde un comentario.
- Queda claro que el control persigue reducir superficie pública por defecto.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-04.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 4 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 5.
