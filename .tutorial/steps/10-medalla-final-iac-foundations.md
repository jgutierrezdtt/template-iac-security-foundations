# Paso 10. Medalla final iac foundations

## Que vas a hacer en este paso?

Implementaras este control de IAC de forma concreta sobre el archivo `docs/iac-security.md` y registraras evidencia tecnica en `.tutorial/evidence/step-10.json`.

## Por que es importante

**En la practica real**:
- Este control reduce riesgo operativo y mejora trazabilidad.
- Permite validar avance real, no solo lectura del tutorial.

**Lo que logras**:
- Resultado tecnico verificable para el paso 10.
- Evidencia auditable para revisiones de seguridad.

---

## Instrucciones paso-a-paso

### Paso 10.1: Prepara el artefacto principal

Crea o actualiza el archivo objetivo de este paso:

```bash
mkdir -p "$(dirname docs/iac-security.md)"
touch docs/iac-security.md
```

### Paso 10.2: Registra evidencia del paso

Crea el archivo `.tutorial/evidence/step-10.json` con este contenido:

```bash
mkdir -p .tutorial/evidence
cat > .tutorial/evidence/step-10.json << 'EOF'
{
  "step": 10,
  "title": "Medalla final iac foundations",
  "status": "completed",
  "artifact": "docs/iac-security.md"
}
EOF
```

---

## Verificacion local

```bash
test -f docs/iac-security.md && echo "artifact ok"
python3 -c 'import json;json.load(open(".tutorial/evidence/step-10.json"));print("evidence ok")'
```

---

## Validacion automatica

`validate-step-10.py` verificara:
- Existe `docs/iac-security.md`.
- Existe `.tutorial/evidence/step-10.json`.
- La evidencia marca `status=completed` y `step=10`.

---

## Criterio de finalizacion

Paso 10 esta completo cuando:
1. `docs/iac-security.md` existe en el repositorio.
2. `.tutorial/evidence/step-10.json` existe y es JSON valido.
3. `.tutorial/state.json` muestra `"current_step": 11`.

**Siguiente paso**: Paso 11
