# Paso 9. Reporting basico

## Objetivo de aprendizaje

Detectar un hallazgo no basta; hay que convertirlo en un reporte que explique qué recurso falla, por qué importa y cómo se remedia.

## Que vas a cambiar y por que

Estructura un documento donde cada hallazgo se conecte con el recurso afectado y con una decisión de remediación.

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
- En el paso final, resume qué controles quedaron implantados.

## Que deberia verse al terminar

- El documento tiene secciones legibles y útiles para revisión.
- Se identifica qué recurso está afectado.
- La decisión o siguiente acción queda explícita.

## Que valida el workflow automaticamente

- `validate-steps.yml` se ejecuta con `push`, `pull_request` y `workflow_dispatch`.
- `scripts/validate-step-09.py` comprueba este paso contra el archivo configurado.
- El workflow busca `## Hallazgos` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Recursos afectados` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Riesgo` dentro de `docs/iac-reporting.md`.
- El workflow busca `## Plan de remediacion` dentro de `docs/iac-reporting.md`.

## Criterio de finalizacion

El paso 9 queda completado cuando el workflow de GitHub Actions valida este cambio sin errores.

Siguiente paso: Paso 10.
