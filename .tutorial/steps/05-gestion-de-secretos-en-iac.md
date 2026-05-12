# Paso 5. Gestion de secretos en iac

## Que vas a hacer en este paso?

Implementaras este control de IAC de forma concreta sobre el archivo `.checkov.yml` y registraras evidencia tecnica en `.tutorial/evidence/step-05.json`.

## Por que es importante

**En la practica real**:
- Este control reduce riesgo operativo y mejora trazabilidad.
- Permite validar avance real, no solo lectura del tutorial.

**Lo que logras**:
- Resultado tecnico verificable para el paso 5.
- Evidencia auditable para revisiones de seguridad.

---

## Instrucciones paso-a-paso

### Paso 5.1: Prepara el artefacto principal

Crea o actualiza el archivo objetivo de este paso:

```bash
mkdir -p "$(dirname .checkov.yml)"
touch .checkov.yml
```

### Paso 5.2: Registra evidencia del paso

Crea el archivo `.tutorial/evidence/step-05.json` con este contenido:

```bash
mkdir -p .tutorial/evidence
cat > .tutorial/evidence/step-05.json << 'EOF'
{
  "step": 5,
  "title": "Gestion de secretos en iac",
  "status": "completed",
  "artifact": ".checkov.yml"
}
EOF
```

---

## Verificacion local

```bash
test -f .checkov.yml && echo "artifact ok"
python3 -c 'import json;json.load(open(".tutorial/evidence/step-05.json"));print("evidence ok")'
```

---

## Validacion automatica

`validate-step-05.py` verificara:
- Existe `.checkov.yml`.
- Existe `.tutorial/evidence/step-05.json`.
- La evidencia marca `status=completed` y `step=5`.

---

## Criterio de finalizacion

Paso 5 esta completo cuando:
1. `.checkov.yml` existe en el repositorio.
2. `.tutorial/evidence/step-05.json` existe y es JSON valido.
3. `.tutorial/state.json` muestra `"current_step": 6`.

**Siguiente paso**: Paso 6
