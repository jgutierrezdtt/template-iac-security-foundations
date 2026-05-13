# Paso 7. Excepciones documentadas

## Objetivo de aprendizaje

Una excepción sin trazabilidad acaba convirtiéndose en deuda invisible. Este paso enseña a documentar qué riesgo se acepta, sobre qué recurso recae y hasta cuándo puede seguir abierto.

## Que vas a cambiar y por que

Vas a crear `docs/iac-exceptions.yml` como registro explícito de excepciones. La intención es que una desviación del baseline no quede escondida en comentarios o en conversaciones temporales, sino en una estructura revisable con check afectado, recurso, motivo y fecha de caducidad.

## Archivo y seccion que debes modificar

- Archivo objetivo: `docs/iac-exceptions.yml`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```yaml
exceptions:
  - check_id: CKV_AWS_20
    resource: aws_s3_bucket.app
    reason: "control temporal mientras se migra el servicio"
    expires_on: "2026-12-31"
```

## Como adaptarlo correctamente

- Registra una excepción por recurso y por check, no una excepción genérica.
- Incluye una fecha de revisión o caducidad desde el principio.
- Si la excepción afecta a producción, deja el motivo en lenguaje claro.
- Redacta el `reason` de forma que otra persona pueda entender por qué la desviación se acepta y qué la haría desaparecer.

## Que deberia verse al terminar

- Cada excepción apunta a un recurso concreto.
- Se entiende el motivo de negocio o técnico.
- Existe un campo de caducidad revisable.
- El documento se puede usar como evidencia de seguimiento y no solo como anotación puntual.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-07.py` comprueba este paso contra el archivo configurado.
- El workflow busca `exceptions:` dentro de `docs/iac-exceptions.yml`.
- El workflow busca `check_id:` dentro de `docs/iac-exceptions.yml`.
- El workflow busca `resource:` dentro de `docs/iac-exceptions.yml`.
- El workflow busca `reason:` dentro de `docs/iac-exceptions.yml`.
- El workflow busca `expires_on:` dentro de `docs/iac-exceptions.yml`.

## Criterio de finalizacion

El paso 7 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 8.
