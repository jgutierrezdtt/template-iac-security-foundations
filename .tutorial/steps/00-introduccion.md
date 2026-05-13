# Paso 0. Introducción

Este tutorial sirve para practicar seguridad en Infraestructura como Código desde un nivel de fundamentos. La idea no es aprender una herramienta aislada, sino entender cómo detectar configuraciones inseguras, priorizar hallazgos y dejar controles simples pero repetibles dentro del repositorio.

## Qué vas a trabajar

A lo largo del recorrido vas a tocar problemas muy habituales en entornos IaC:

- plantillas con configuraciones inseguras por defecto
- permisos excesivos en recursos cloud
- secretos expuestos o mal gestionados dentro del código de infraestructura
- necesidad de escanear cambios antes de integrarlos
- documentación de excepciones y reporting mínimo para no perder contexto

## Qué tecnologías representa este laboratorio

El repositorio está planteado como un laboratorio mixto de Terraform, YAML de Kubernetes y validación automatizada. Eso permite practicar controles comunes en varios formatos de IaC sin depender de un único proveedor.

## Cómo se recorre el tutorial

Cada paso te pedirá dejar un cambio concreto y revisable en un archivo del repositorio. El objetivo no es ejecutar acciones manuales fuera del flujo, sino ir completando piezas que hagan visible el control que se está aprendiendo. Los workflows del tutorial se encargan de comprobar el progreso.

## Qué deberías observar desde el principio

- una plantilla insegura rara vez falla por una sola línea; suele reflejar una ausencia de criterio
- un hallazgo útil no se limita a existir, también tiene que poder interpretarse y remediarse
- una excepción sin contexto acaba convirtiéndose en deuda invisible
- integrar validación en GitHub Actions es parte del control, no un extra opcional

## Qué aspecto tiene un buen resultado

Al final del tutorial deberías haber convertido este template en una referencia básica de seguridad IaC: con ejemplos inseguros identificables, correcciones claras, validación automatizada y documentación suficiente para que otro equipo entienda por qué cada control existe.
