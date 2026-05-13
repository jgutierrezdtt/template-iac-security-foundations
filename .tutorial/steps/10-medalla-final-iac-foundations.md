# Paso 10. Medalla final iac foundations

## Objetivo de aprendizaje

Cerrar el recorrido foundations con una vista final del estado de seguridad IaC: qué se detectó, qué recursos estuvieron implicados, qué riesgo quedó descrito y cómo se decidió remediarlo.

## Que vas a cambiar y por que

En este último paso vas a usar `docs/iac-reporting.md` como resumen final del laboratorio. La idea es que el documento no solo sirva para un hallazgo puntual, sino también para demostrar que el repositorio termina el tutorial con una narrativa mínima de findings, recursos, riesgo y plan de remediación.

## Archivo y seccion que debes modificar

- Archivo objetivo: `docs/iac-reporting.md`.
- Aplícalo en la parte del archivo que corresponde al título del paso.
- Si el archivo aún no existe, créalo con este contenido inicial y luego evoluciona desde ahí en los siguientes pasos.

## Cambio base recomendado

Este bloque no es para pegar a ciegas: úsalo como punto de partida y ajústalo al contexto del repositorio.

```markdown
## Hallazgos
## Recursos afectados
## Riesgo
## Plan de remediacion
```

## Como adaptarlo correctamente

- Usa el nombre exacto del recurso Terraform al describir el hallazgo.
- Separa el riesgo técnico del plan de remediación para que el documento sirva en revisión.
- En este paso final, haz que el reporte sirva como cierre del recorrido y no solo como nota intermedia.
- Resume de forma clara qué controles quedaron implantados a nivel de foundations.

## Que deberia verse al terminar

- El documento tiene secciones legibles y útiles para revisión.
- Se identifica qué recurso está afectado.
- La decisión o siguiente acción queda explícita.
- El documento puede leerse como evidencia final de lo aprendido en el tutorial.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-10.py` comprueba este paso contra el archivo configurado.
- El workflow busca `## Hallazgos` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Recursos afectados` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Riesgo` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Plan de remediacion` dentro de `docs/iac-reporting.md`.

## Criterio de finalizacion

El paso 10 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Este es el ultimo paso del tutorial.
