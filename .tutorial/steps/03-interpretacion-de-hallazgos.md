# Paso 3. Interpretacion de hallazgos

## Objetivo de aprendizaje

Detectar un hallazgo no basta. En seguridad IaC hace falta convertir la salida del escáner en un documento que explique qué recurso está afectado, qué riesgo introduce y cuál será la decisión operativa para corregirlo.

## Que vas a cambiar y por que

En este paso vas a estructurar `docs/iac-reporting.md` para que el hallazgo no quede aislado del contexto. El documento debe ayudarte a pasar de un resultado técnico a una conversación de remediación: qué se encontró, dónde está, por qué importa y qué se hará a continuación.

## Archivo y seccion que debes modificar

- Archivo objetivo: `docs/iac-reporting.md`.
- Si el archivo aún no existe, créalo en este paso.
- Mantén las cuatro secciones base porque el resto del tutorial puede reutilizar este documento como evidencia simple de análisis.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```markdown
## Hallazgos
## Recursos afectados
## Riesgo
## Plan de remediacion
```

## Como adaptarlo correctamente

- Usa el nombre exacto del recurso Terraform o del fichero analizado al describir el hallazgo.
- Separa el hallazgo del riesgo: una mala configuración es el hecho técnico; el riesgo explica por qué importa.
- Haz que el plan de remediación sea una decisión concreta y no una frase genérica como "revisar más adelante".
- Piensa en este documento como una evidencia mínima para revisión entre desarrollo, plataforma y seguridad.

## Que deberia verse al terminar

- El documento tiene secciones legibles y útiles para revisión.
- Se identifica qué recurso está afectado.
- La decisión o siguiente acción queda explícita.
- Otra persona puede entender el hallazgo sin tener que volver a leer la salida cruda del escáner.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-03.py` comprueba este paso contra el archivo configurado.
- El workflow busca `## Hallazgos` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Recursos afectados` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Riesgo` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Plan de remediacion` dentro de `docs/iac-reporting.md`.

## Criterio de finalizacion

El paso 3 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 4.
