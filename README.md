# Tendero MIPE — Sistema Contable Multi-Cliente para MYPE Chile

<p align="center">
  <strong>Un proyecto de <a href="https://furiolabs.cl">furiolabs.cl</a></strong><br>
  Iniciativa de experimentación e innovación en herramientas de gestión para micro y pequeñas empresas chilenas.
</p>

### Autores

- **Sandro A. Gómez Araya** — Software Craftsman ([furiolabs.cl](https://furiolabs.cl))
- **Danilo J. Gómez Araya** — Contador Auditor

---

## Descripción

**Tendero MIPE** es un sistema de contabilidad profesional en formato Excel (.xlsx) diseñado específicamente para micro y pequeñas empresas (MYPE) chilenas. Permite gestionar la contabilidad completa de múltiples clientes desde un solo archivo, sin macros VBA, cumpliendo con la normativa contable y tributaria chilena vigente.

El template está pensado para contadores novatos, emprendedores y clientes con conocimientos contables limitados: las celdas editables están destacadas en amarillo, cada hoja incluye instrucciones paso a paso con citas normativas, y los estados financieros se generan automáticamente a partir del Libro Diario.

### Problema que resuelve

Las MYPE chilenas (más de 1,8 millones de empresas) enfrentan barreras significativas para llevar contabilidad ordenada: los sistemas ERP son costosos, los contadores externos cobran tarifas mensuales elevadas, y las planillas Excel caseras carecen de estructura normativa. Tendero MIPE ofrece una solución intermedia: un sistema contable profesional, gratuito, auditable y basado en normativa vigente.

---

## Estado del Arte

### Versión Actual: 2.0 (Marzo 2026)

| Métrica | Valor |
|---------|-------|
| Hojas | 12 (incluye hoja de auditoría) |
| Fórmulas | 2.420 (0 errores verificados) |
| Cuentas por cliente | 95 (plan estándar PCGA Chile) |
| Indicadores financieros | 22 KPIs con semáforos |
| Capacidad Libro Diario | ~4.990 asientos por cliente |
| Macros VBA | Ninguna (100% fórmulas nativas) |
| Última auditoría | 22/03/2026 — 0 hallazgos críticos |

### Normativa Implementada

- **NIIF para Pymes (IFRS for SMEs)** — 12 secciones aplicadas (BT N°82, Colegio de Contadores A.G.)
- **D.L. 824 (LIR)** — Art. 14D Pro-Pyme (12,5% Ley 21.755), Art. 31 gastos, Art. 42 N°2 retenciones
- **D.L. 825 (IVA)** — Tasa 19%, IVA CF/DF, F-29
- **Código del Trabajo** — Provisión vacaciones, remuneraciones
- **Ley 21.755** — Rebaja transitoria IDPC Pro-Pyme 12,5% (2025-2027)
- **Ley 21.133** — Retención progresiva honorarios: 14,5% (2025) → 17% (2028+)

### Estructura del Archivo

```
tendero_mipe_template.xlsx
├── Inicio                  → Guía paso a paso (8 pasos)
├── Marco Regulatorio       → Documentación normativa (6 secciones)
├── Clientes                → Registro multi-cliente
├── Nuevo Cliente           → Formulario de alta
├── Cuentas                 → Plan de cuentas PCGA Chile (95 cuentas × cliente)
├── Libro Diario            → Asientos contables (partida doble)
├── Libro Mayor             → Saldos por cuenta (automático)
├── Balance General         → Estado de Situación Financiera (automático)
├── Estado Resultados       → Estado de Resultado Integral (automático)
├── Indicadores             → 14 KPIs: liquidez, deuda, rentabilidad, actividad
├── Flujo de Caja           → Método indirecto NIC 7 + 8 indicadores sostenibilidad
└── Auditoría               → Informe de auditoría contable
```

### Motor de Cálculo

Todas las referencias cruzadas entre hojas usan fórmulas `SUMPRODUCT` que filtran dinámicamente por ID de cliente, código de cuenta y año:

```
=SUMPRODUCT(('Libro Diario'!$A$10:$A$5000=cliente)*
            ('Libro Diario'!$E$10:$E$5000=código)*
            (YEAR('Libro Diario'!$C$10:$C$5000)=año)*
            ('Libro Diario'!$H$10:$H$5000))
```

Esto elimina la necesidad de macros VBA, haciendo el archivo completamente transparente y auditable.

---

## Cómo Usar

1. Descarga `tendero_mipe_template.xlsx`
2. Abre en Excel o LibreOffice Calc
3. Sigue los 8 pasos de la hoja **Inicio**
4. Registra tus clientes en la hoja **Clientes**
5. Ingresa asientos en el **Libro Diario** (partida doble)
6. Los estados financieros se generan automáticamente

> **Tip:** Las celdas con fondo amarillo son editables. Las demás contienen fórmulas — no las modifiques.

---

## Skill de Auditoría (Claude)

El proyecto incluye un skill de auditoría para [Claude](https://claude.ai) que verifica automáticamente:

- Cuadratura del Libro Diario (partida doble)
- Integridad del plan de cuentas
- Errores de fórmulas (2.420 fórmulas)
- Cumplimiento normativo (NIIF Pymes, LIR, D.L. 825)
- Consistencia de la hoja Marco Regulatorio
- Formato RUT, tasas de impuesto vigentes

Para usarlo, instala `auditoria-contable.skill` y pide: *"audita la contabilidad"*.

---

## Archivos del Repositorio

| Archivo | Descripción |
|---------|-------------|
| `tendero_mipe_template.xlsx` | Template contable principal |
| `auditoria-contable.skill` | Skill de auditoría para Claude |
| `Resumen Ejecutivo — Programa Contabilidad MYPE.md` | Documentación técnica detallada |
| `Guía Skill Auditoría Contable.md` | Guía de uso del skill |
| `README.md` | Este archivo |
| `.gitignore` | Archivos excluidos del repositorio |

---

## Cómo Contribuir

Tendero MIPE es un proyecto abierto de [furiolabs.cl](https://furiolabs.cl). Agradecemos contribuciones de contadores, desarrolladores y emprendedores chilenos.

### Áreas donde necesitamos ayuda

- **Normativa:** Verificación de tasas y artículos vigentes, especialmente ante reformas tributarias
- **Cuentas:** Planes de cuentas especializados por sector (agricultura, transporte, comercio electrónico, etc.)
- **Indicadores:** Umbrales sectoriales más precisos que los genéricos SERCOTEC/CMF
- **UX:** Mejoras en la experiencia de uso para contadores no técnicos
- **Testing:** Pruebas con datos reales (anonimizados) de diferentes tipos de MYPE
- **Documentación:** Traducciones, guías de uso, tutoriales en video

### Cómo enviar una contribución

1. **Fork** este repositorio
2. Crea una **branch** con tu mejora: `git checkout -b mejora/nombre-descriptivo`
3. Realiza tus cambios
4. Si modificas el xlsx, verifica que no introduces errores de fórmulas
5. Crea un **Pull Request** describiendo:
   - Qué cambias y por qué
   - Referencia normativa (si aplica)
   - Si probaste con datos reales (anonimizados)

### Directrices

- **No incluyas datos reales de clientes** — usa datos ficticios (CLI001, CLI002, etc.)
- **Cita siempre la normativa** cuando modifiques cálculos o notas (ej: "Art. 14D LIR", "NIIF Pymes Sec. 4")
- **Mantén el archivo libre de macros VBA** — todo debe resolverse con fórmulas nativas de Excel
- **Documenta los assumptions** de cualquier cálculo nuevo en la hoja Marco Regulatorio

### Reportar Issues

Si encuentras un error normativo, de fórmula, o de usabilidad:
1. Abre un **Issue** con el label adecuado: `bug`, `normativa`, `ux`, `enhancement`
2. Incluye: hoja afectada, celda(s), descripción del problema, normativa de referencia
3. Si es un error de tasa o artículo, incluye la fuente oficial (SII, BCN, etc.)

---

## Roadmap

- [ ] Libro de Compras y Ventas (para F-29 SII)
- [ ] Notas a los Estados Financieros (NIIF Pymes Sec. 8)
- [ ] Cálculo automático de depreciación (tabla SII Res. Ex. 43/2002)
- [ ] Corrección monetaria automatizada (Art. 41 LIR, variación IPC)
- [ ] Planes de cuenta sectoriales (transporte, comercio, servicios profesionales)
- [ ] Soporte multimoneda (UF, USD)
- [ ] Versión web (posible migración a aplicación)

---

## Advertencia Legal

Este template es una herramienta de apoyo para la gestión contable interna. **No reemplaza la asesoría de un contador público autorizado** ni la revisión por un auditor independiente. Las tasas de impuesto y referencias normativas están actualizadas a marzo de 2026 y deben verificarse ante cambios legislativos.

El usuario es responsable de la correcta aplicación de la normativa tributaria a su situación particular. Para declaraciones al SII (F-29, F-22, etc.), los formularios deben completarse en [sii.cl](https://www.sii.cl).

---

## Licencia

Este proyecto es parte de las iniciativas de experimentación e innovación de **[furiolabs.cl](https://furiolabs.cl)**.

---

<p align="center">
  Hecho con dedicación para las MYPE de Chile<br>
  <strong>Sandro A. Gómez Araya</strong> · Software Craftsman · <a href="https://furiolabs.cl">furiolabs.cl</a><br>
  <strong>Danilo J. Gómez Araya</strong> · Contador Auditor<br><br>
  <a href="https://furiolabs.cl">furiolabs.cl</a> — Innovación para emprendedores
</p>
