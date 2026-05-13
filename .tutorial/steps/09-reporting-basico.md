# Paso 9. Reporting basico

## Objetivo de aprendizaje

Entender que un hallazgo aislado no crea seguimiento. Este paso convierte el análisis previo en un formato de reporting básico que pueda revisarse con cierta regularidad.

## Que vas a cambiar y por que

Vas a reforzar `docs/iac-reporting.md` para que funcione como reporte sencillo del estado de seguridad IaC. No basta con registrar un finding: el documento debe servir para revisar hallazgos, recursos afectados, riesgo y plan de remediación como una vista mínima de seguimiento.

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
- Redáctalo como un reporte que podría compartirse periódicamente, no como una nota improvisada.
- En el paso final, resume qué controles quedaron implantados.

## Que deberia verse al terminar

- El documento tiene secciones legibles y útiles para revisión.
- Se identifica qué recurso está afectado.
- La decisión o siguiente acción queda explícita.
- El formato permite reutilizar el documento como reporting básico del laboratorio.

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
