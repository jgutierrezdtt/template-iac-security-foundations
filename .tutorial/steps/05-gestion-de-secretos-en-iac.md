# Paso 5. Gestion de secretos en iac

## Objetivo de aprendizaje

Entender que un secreto escrito directamente en Terraform termina contaminando el código, el plan o el estado. El aprendizaje de este paso es separar el manejo de datos sensibles del resto de la plantilla sin romper la base de infraestructura ya construida.

## Que vas a cambiar y por que

Este paso se apoya en el mismo `iac/main.tf` que vienes usando con el bucket S3. La idea es introducir el criterio correcto para cualquier dato sensible que aparezca en esa plantilla: no dejar valores literales y moverlos a variables u otro mecanismo controlado. Al mismo tiempo, la estructura base del bucket y su bloqueo público debe mantenerse, porque el workflow sigue usándola como referencia de validación.

## Archivo y seccion que debes modificar

- Archivo objetivo: `iac/main.tf`.
- Mantén en este archivo el recurso S3 que ya sirve como base del laboratorio.
- Si introduces parámetros sensibles, colócalos como variables y evita mezclarlos con literales inseguros dentro del recurso.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```hcl
variable "db_password" {
  type      = string
  sensitive = true
}

resource "aws_s3_bucket" "app" {
  bucket = "demo-bucket"
}

resource "aws_s3_bucket_public_access_block" "app" {
  bucket              = aws_s3_bucket.app.id
  block_public_policy = true
}
```

## Como adaptarlo correctamente

- Si usas `iac/main.tf`, declara la variable en `iac/variables.tf` o al principio del mismo archivo.
- No dejes ejemplos con contraseñas literales ni tokens ficticios dentro del recurso final.
- Mantén los marcadores del bucket S3 porque el flujo automático todavía comprueba esa estructura.
- El patrón importante es separar datos sensibles de la configuración estática, aunque este template siga validando sobre el mismo recurso base.

## Que deberia verse al terminar

- La plantilla conserva el bucket base y su bloqueo público.
- Si aparece algún dato sensible en el archivo, queda modelado como variable y no como literal.
- El archivo sigue siendo utilizable como base para los pasos posteriores.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-05.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 5 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 6.
