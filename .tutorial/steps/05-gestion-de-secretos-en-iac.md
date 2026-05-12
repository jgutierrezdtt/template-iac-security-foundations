# Paso 5. Gestion de secretos en iac

## Objetivo de aprendizaje

Modificar la plantilla IaC para representar y luego corregir un riesgo real.

## Archivo y seccion que debes modificar

- Archivo objetivo: `iac/main.tf`.
- Seccion donde aplicar el cambio: recurso Terraform del ejemplo.
- Resultado esperado: el repositorio incorpora el control de este paso de forma legible y revisable.

## Cambio que debes introducir

Copia este bloque como base y adáptalo al contexto real del repositorio:

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

- Usa un recurso sencillo para que el hallazgo sea visible.
- Si el paso es sobre secretos, evita dejar valores literales en variables o recursos.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-05.py` comprueba el archivo y los marcadores esperados de este paso.
- Debe encontrar el marcador `resource "aws_s3_bucket"` en `iac/main.tf`.
- Debe encontrar el marcador `aws_s3_bucket_public_access_block` en `iac/main.tf`.
- Debe encontrar el marcador `block_public_policy` en `iac/main.tf`.

## Criterio de finalizacion

El paso 5 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 6.
