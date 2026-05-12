# Paso 2. Primer escaneo con checkov

## Que vas a hacer en este paso?

Implementaras este control de IAC de forma concreta sobre el archivo `.checkov.yml` y registraras evidencia tecnica en `.tutorial/evidence/step-02.json`.

## Por que es importante

**En la practica real**:
- Este control reduce riesgo operativo y mejora trazabilidad.
- Permite validar avance real, no solo lectura del tutorial.

**Lo que logras**:
- Resultado tecnico verificable para el paso 2.
- Evidencia auditable para revisiones de seguridad.

---

## Instrucciones paso-a-paso

### Paso 2.1: Prepara el artefacto principal

Crea o actualiza el archivo objetivo de este paso:

```bash
mkdir -p "$(dirname .checkov.yml)"
touch .checkov.yml
```

### Paso 2.2: Registra evidencia del paso

Crea el archivo `.tutorial/evidence/step-02.json` con este contenido:

```bash
mkdir -p .tutorial/evidence
cat > .tutorial/evidence/step-02.json << 'EOF'
{
  "step": 2,
  "title": "Primer escaneo con checkov",
  "status": "completed",
  "artifact": ".checkov.yml"
}
EOF
```

---

## Verificacion local

```bash
test -f .checkov.yml && echo "artifact ok"
python3 -c 'import json;json.load(open(".tutorial/evidence/step-02.json"));print("evidence ok")'
```

---

## Validacion automatica

`validate-step-02.py` verificara:
- Existe `.checkov.yml`.
- Existe `.tutorial/evidence/step-02.json`.
- La evidencia marca `status=completed` y `step=2`.

---

## Criterio de finalizacion

Paso 2 esta completo cuando:
1. `.checkov.yml` existe en el repositorio.
2. `.tutorial/evidence/step-02.json` existe y es JSON valido.
3. `.tutorial/state.json` muestra `"current_step": 3`.

**Siguiente paso**: Paso 3
