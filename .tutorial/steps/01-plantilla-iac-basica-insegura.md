# Paso 1. Plantilla iac basica insegura

## Objetivo de aprendizaje

Antes de corregir riesgos hay que tener un ejemplo inseguro reconocible. Este paso crea esa base para que el resto del tutorial tenga algo que escanear y remediar.

## Que vas a cambiar y por que

Define un recurso deliberadamente simple y con una debilidad visible que más adelante se corregirá.

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
```

## Como adaptarlo correctamente

- Mantén el ejemplo pequeño; basta un bucket o un security group para ilustrar el riesgo.
- No intentes meter varios riesgos a la vez en el mismo paso.
- Deja el recurso en `iac/main.tf` para que los pasos siguientes trabajen sobre el mismo archivo.

## Que deberia verse al terminar

- Existe un recurso base en `iac/main.tf`.
- La inseguridad inicial es fácil de entender por lectura.
- El siguiente paso puede escanear exactamente ese archivo.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-01.py` comprueba este paso contra el archivo configurado.
- El workflow busca `resource "aws_s3_bucket"` dentro de `iac/main.tf`.
- El workflow busca `aws_s3_bucket_public_access_block` dentro de `iac/main.tf`.
- El workflow busca `block_public_policy` dentro de `iac/main.tf`.

## Criterio de finalizacion

El paso 1 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 2.
