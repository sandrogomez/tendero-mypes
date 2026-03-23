# furio-contable

Base de conocimiento y herramientas de contabilidad para PYMES en Chile.

---

## Descripción

**furio-contable** es un proyecto modular que centraliza:

1. **Plantillas Excel** para la contabilidad diaria de pequeñas y medianas empresas chilenas.
2. **Base de conocimiento** sobre el sistema tributario y contable de Chile.
3. (Futuro) Integraciones con software de gestión para automatizar el registro contable.

---

## Estructura del repositorio

```
furio-contable/
├── templates/
│   └── contabilidad_pyme.xlsx   # Plantilla principal de contabilidad
├── docs/
│   ├── contabilidad_chile.md    # Marco legal, tributos y obligaciones
│   └── uso_plantilla.md         # Guía de uso de la plantilla Excel
├── src/
│   └── generate_template.py     # Script para (re)generar la plantilla Excel
├── LICENSE
└── README.md
```

---

## Plantilla Excel – `contabilidad_pyme.xlsx`

La plantilla incluye las siguientes hojas:

| Hoja | Descripción |
|------|-------------|
| **Portada** | Datos de la empresa y período |
| **Plan de Cuentas** | Catálogo de cuentas contables (PYME) |
| **Libro Diario** | Registro cronológico de asientos |
| **Ingresos y Egresos** | Resumen mensual con totales anuales |
| **Estado de Resultados** | Resultado del ejercicio |
| **Balance General** | Posición financiera al cierre |
| **Registro IVA** | Control de débito y crédito fiscal |

### Uso rápido

1. Abra `templates/contabilidad_pyme.xlsx` en Excel, LibreOffice Calc o Google Sheets.
2. Complete la hoja **Portada** con los datos de su empresa.
3. Registre cada transacción en **Libro Diario**.
4. Controle el IVA mensual en **Registro IVA**.
5. Consulte los resúmenes en **Ingresos y Egresos**, **Estado de Resultados** y **Balance General**.

### Regenerar la plantilla

```bash
pip install openpyxl
python3 src/generate_template.py
```

---

## Documentación

- [Contabilidad en Chile – Guía para PYMES](docs/contabilidad_chile.md)
- [Guía de uso de la plantilla Excel](docs/uso_plantilla.md)

---

## Contribuir

Las contribuciones son bienvenidas. Si deseas agregar nuevas hojas a la plantilla, ampliar la base de conocimiento o integrar herramientas externas, abre un *issue* o un *pull request*.

---

## Licencia

Distribuido bajo la licencia MIT. Ver [LICENSE](LICENSE) para más detalles.
