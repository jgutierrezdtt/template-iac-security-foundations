# Paso 5. Gestion de secretos en iac

## Objetivo de aprendizaje

Un secreto escrito directamente en Terraform termina en el repositorio, en el plan o en el estado. Este paso enseña a sustituir valores hardcodeados por variables sensibles.

## Que vas a cambiar y por que

Mueve cualquier valor sensible a una variable marcada como `sensitive = true` y referencia esa variable desde el recurso.

## Archivo y seccion que debes modificar

- Archivo objetivo: `iac/main.tf`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```hcl
variable "db_password" {
  type      = string
  sensitive = true
}

resource "aws_db_instance" "app" {
  identifier = "demo-db"
  password   = var.db_password
}
```

## Como adaptarlo correctamente

- Si usas `iac/main.tf`, declara la variable en `iac/variables.tf` o al principio del mismo archivo.
- No dejes ejemplos con contraseñas literales ni tokens ficticios dentro del recurso final.
- La idea del paso es mostrar el patrón correcto: variable sensible y referencia desde el recurso.

## Que deberia verse al terminar

- La plantilla usa `variable` para el dato sensible.
- La variable está marcada como sensible.
- El recurso ya no contiene un secreto literal.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-05.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 5 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 6.
