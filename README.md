# IaC Security Foundations

Tutorial de fundamentos de seguridad en Infraestructura como Código (IaC).

## Objetivo

Aprender los conceptos y herramientas esenciales para detectar y corregir configuraciones inseguras en IaC: análisis estático de plantillas, gestión de secretos, control de permisos excesivos y validación automatizada.

## Audiencia

Desarrolladores, ingenieros DevOps y equipos de plataforma que quieran incorporar seguridad en sus flujos de trabajo de infraestructura desde el principio.

## Requisitos previos

- Conocimientos básicos de Git y GitHub.
- Nociones de algún lenguaje IaC (Terraform, CloudFormation, Bicep o similar).

## Herramientas utilizadas

- Checkov o herramienta IaC scanner equivalente
- GitHub Actions
- Scripts de validación del curso

## Inicio del tutorial

[Empezar tutorial](https://github.com/new?template_name=template-iac-security-foundations&template_owner=jgutierrezdtt)

## Acceso al repositorio

- [Crear mi repositorio desde este template](https://github.com/new?template_name=template-iac-security-foundations&template_owner=jgutierrezdtt)
- [Volver al portal general](https://github.com/jgutierrezdtt/security-learning-portal)

## Gestión del progreso

- [Validar progreso](../../actions/workflows/validate.yml)
- [Probar integridad del tutorial](../../actions/workflows/test-tutorial.yml)
- [Ejecutar tests funcionales del tutorial](../../actions/workflows/functional-tests.yml)
- [Reiniciar tutorial](../../actions/workflows/reset-tutorial.yml)
- [Ver pasos del tutorial](./.tutorial/steps/)

## Tabla de pasos

| Paso | Tema |
| --- | --- |
| 0 | Introducción |
| 1 | Plantilla IaC básica insegura |
| 2 | Primer escaneo con checkov |
| 3 | Interpretación de hallazgos |
| 4 | Corrección de permisos excesivos |
| 5 | Gestión de secretos en IaC |
| 6 | Reglas custom de IaC |
| 7 | Excepciones documentadas |
| 8 | Integración en GitHub Actions |
| 9 | Reporting básico |
| 10 | Medalla final IaC Foundations |

## Paso 0

El paso 0 describe el entorno, permisos y limitaciones del laboratorio. No bloquea el flujo: el botón principal abre directamente el paso 1.

## Actualización desde template

Este repositorio incluye `.template-version` y workflow de actualización para revisar cambios del template sin sobrescribir trabajo del usuario.

## Badge final

Al cerrar el curso se generan artefactos de finalización en:

- `.tutorial/badges/completion-badge.md`
- `.tutorial/badges/completion-badge.svg`
- `.tutorial/evidence/completion.json`

## Referencias

- [Checkov](https://www.checkov.io/)
- [GitHub Actions](https://docs.github.com/actions)
