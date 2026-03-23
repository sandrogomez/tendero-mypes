# Guía de uso de la plantilla Excel

Este documento describe la estructura y el flujo de trabajo de la plantilla `contabilidad_pyme.xlsx` incluida en el directorio `templates/`.

---

## Hojas incluidas

| Hoja | Propósito |
|------|-----------|
| **Portada** | Datos de la empresa y período contable |
| **Plan de Cuentas** | Catálogo de cuentas contables sugerido |
| **Libro Diario** | Registro cronológico de asientos contables |
| **Ingresos y Egresos** | Resumen mensual de ingresos y gastos |
| **Estado de Resultados** | Resultado del ejercicio (utilidad/pérdida) |
| **Balance General** | Posición financiera (activos, pasivos, patrimonio) |
| **Registro IVA** | Control de débitos y créditos fiscales IVA |

---

## Flujo de trabajo recomendado

```
┌───────────────┐
│   Portada     │  → Complete nombre, RUT y período
└──────┬────────┘
       │
┌──────▼────────┐
│ Libro Diario  │  → Ingrese cada operación con fecha, glosa y montos
└──────┬────────┘
       │
┌──────▼────────┐
│ Registro IVA  │  → Registre facturas/boletas para cuadrar F29
└──────┬────────┘
       │
┌──────▼──────────────┐
│ Ingresos y Egresos  │  → Revise el resumen mensual
└──────┬──────────────┘
       │
┌──────▼────────────────┐
│ Estado de Resultados  │  → Consolide resultado anual
└──────┬────────────────┘
       │
┌──────▼──────────┐
│ Balance General │  → Verifique que activos = pasivos + patrimonio
└─────────────────┘
```

---

## Regenerar la plantilla

La plantilla se genera con el script Python `src/generate_template.py`.

```bash
# Requisitos
pip install openpyxl

# Generar
python3 src/generate_template.py
```

---

## Convenciones de colores

| Color | Significado |
|-------|------------|
| Azul oscuro (fondo encabezado) | Fila de encabezado de sección |
| Azul claro | Sub-encabezados o totales positivos |
| Verde claro | Ingresos / resultado positivo |
| Rojo/salmón | Egresos / resultado negativo |
| Naranja | Fila de totales calculados |
| Gris claro | Filas alternas para facilitar la lectura |

---

## Notas

- Todos los montos están en **pesos chilenos (CLP)**.
- Los campos de IVA usan la **tasa del 19%** vigente en Chile.
- La plantilla **no reemplaza** un sistema contable profesional; es un apoyo para microempresas y pequeños negocios.
