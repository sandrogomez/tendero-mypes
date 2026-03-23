# Resumen Ejecutivo — Sistema Contable Multi-Cliente MYPE Chile

**Versión:** 2.0 (Marzo 2026)
**Archivo:** `Programa Contabilidad.xlsx`
**Estado:** Template limpio, auditado, 0 errores de fórmulas

---

## Descripción del Proyecto

Sistema de contabilidad profesional en formato Excel (.xlsx) diseñado para micro y pequeñas empresas (MYPE) chilenas. Permite gestionar la contabilidad completa de múltiples clientes desde un solo archivo, sin macros VBA, con cálculos automáticos basados en fórmulas SUMPRODUCT y cumplimiento de la normativa contable y tributaria chilena vigente.

El template está pensado para contadores novatos o clientes con conocimientos contables limitados: las celdas editables están destacadas en amarillo, cada hoja incluye instrucciones paso a paso, y los estados financieros se generan automáticamente a partir del Libro Diario.

---

## Estructura del Archivo

El archivo contiene 12 hojas organizadas en un flujo lógico de trabajo:

| Nº | Hoja | Función | Tipo |
|----|------|---------|------|
| 1 | **Inicio** | Guía paso a paso para el usuario (8 pasos numerados) | Navegación |
| 2 | **Marco Regulatorio** | Documentación del marco normativo vigente y prácticas contables (6 secciones) | Referencia |
| 3 | **Clientes** | Registro de clientes (RUT, razón social, giro, representante legal) | Entrada de datos |
| 4 | **Nuevo Cliente** | Formulario para agregar un nuevo cliente al sistema | Entrada de datos |
| 5 | **Cuentas** | Plan de cuentas estándar PCGA Chile — 95 cuentas precargadas por cliente | Configuración |
| 6 | **Libro Diario** | Registro cronológico de asientos contables (partida doble) | Entrada de datos |
| 7 | **Libro Mayor** | Saldos por cuenta, calculados automáticamente desde el Libro Diario | Automático |
| 8 | **Balance General** | Estado de Situación Financiera (Corriente / No Corriente) | Automático |
| 9 | **Estado Resultados** | Estado de Resultado Integral por función del gasto | Automático |
| 10 | **Indicadores** | KPIs financieros con semáforos (liquidez, deuda, rentabilidad, actividad) | Automático |
| 11 | **Flujo de Caja** | Flujo de Efectivo método indirecto + indicadores de sostenibilidad | Automático |
| 12 | **Auditoría** | Informe de auditoría contable (19 hallazgos, 5 resueltos) | Diagnóstico |

---

## Estadísticas Técnicas

- **Fórmulas:** 2.420 (verificadas con LibreOffice recalc, 0 errores)
- **Clientes precargados:** 3 slots (CLI001, CLI002, CLI003) — expandible
- **Cuentas por cliente:** 95 cuentas estándar PCGA Chile
- **Capacidad Libro Diario:** ~4.990 líneas de asientos por cliente
- **Motor de cálculo:** Fórmulas SUMPRODUCT (sin macros VBA)
- **Formato moneda:** CLP sin decimales, separador de miles

---

## Marco Normativo Aplicado

### Norma Contable
- **NIIF para Pymes (IFRS for SMEs)** — Obligatoria en Chile desde 2013 (Boletín Técnico N°82, Colegio de Contadores A.G.)
- Secciones aplicadas: 2 (conceptos), 3 (presentación EEFF), 4 (balance), 5 (resultado integral), 7 (flujo de efectivo), 10 (políticas), 17 (PPE), 22 (patrimonio), 23 (ingresos), 27 (deterioro), 28 (beneficios empleados), 29 (impuesto a las ganancias)

### Legislación Tributaria
- **D.L. 824 (LIR):** Art. 14D Pro-Pyme, Art. 17 N°5 aportes de capital, Art. 29-33 base imponible, Art. 31 gastos deducibles, Art. 31 N°5/5bis depreciación, Art. 41 corrección monetaria, Art. 42 N°2 retención honorarios, Art. 84 PPM
- **D.L. 825 (IVA):** Tasa 19%, IVA Crédito Fiscal (Art. 23), IVA Débito Fiscal (Art. 24)
- **Código del Trabajo:** Art. 44 remuneración mínima, Art. 67 vacaciones, Art. 163 indemnización

### Leyes Complementarias
- Ley 21.755 (2024) — Rebaja transitoria IDPC Pro-Pyme a 12,5% (2025-2027)
- Ley 21.133 (2019) — Retención progresiva honorarios: 14,5% (2025), 15,25% (2026), 16% (2027), 17% (2028+)
- Ley 20.720 — Insolvencia y reestructuración
- Res. Ex. SII N°43/2002 — Tablas de vida útil para depreciación

---

## Assumptions (Supuestos del Template)

### Supuestos Generales
1. **Régimen tributario:** El template soporta tanto régimen General (27%) como Pro-Pyme (12,5% en 2025-2027). El usuario debe aplicar la tasa correcta según su régimen.
2. **Moneda:** Todos los montos en Pesos Chilenos (CLP), sin decimales. No hay soporte para multimoneda ni UF.
3. **Período:** Ejercicio anual calendario (enero-diciembre). El filtro de año permite comparar períodos.
4. **IVA:** Tasa fija 19%. No contempla regímenes especiales (exportadores, zona franca, ferias libres).
5. **Entidad separada:** Cada cliente es una entidad contable independiente; no hay consolidación entre clientes.

### Supuestos Contables
6. **Base de devengo:** Ingresos y gastos se reconocen cuando ocurren, no cuando se cobran/pagan.
7. **Método de inventario:** El template no prescribe FIFO ni CMP; el usuario registra el costo según su política.
8. **Depreciación:** Se registra manualmente en el Libro Diario. No hay cálculo automático de depreciación. Las tablas de vida útil SII (Res. Ex. 43/2002) se citan como referencia.
9. **Corrección monetaria:** No automatizada. Requiere asiento manual de cierre basado en variación IPC (Art. 41 LIR).
10. **Impuesto diferido:** No implementado. Para MYPE con diferencias temporarias significativas, el contador debe calcularlo manualmente.
11. **Empresa en marcha:** Se asume continuidad operacional. Los indicadores de Flujo de Caja alertan sobre riesgo de insolvencia.

### Supuestos de Indicadores
12. **Umbrales de referencia:** Basados en benchmarks SERCOTEC, CMF y CORFO para MYPE chilenas del sector comercio/servicios. Pueden no aplicar a todos los sectores.
13. **Semáforos:** Los indicadores usan rangos fijos (ej: Razón Corriente ≥1.5 = verde). El usuario debe interpretar según su industria.

### Limitaciones Conocidas
14. **Sin notas formales a los EEFF:** Las citas normativas están integradas en cada hoja, pero no hay una hoja formal de Notas per NIIF Pymes Sec. 8. Suficiente para gestión interna; para presentación a terceros se recomienda agregar.
15. **Sin libro de compras/ventas:** El template no genera el libro de compras y ventas exigido por el SII para la declaración F-29.
16. **Sin generación automática de formularios SII:** El template prepara la información contable, pero la declaración electrónica se realiza en sii.cl.
17. **Capacidad máxima:** ~4.990 líneas en el Libro Diario por el rango fijo de las fórmulas SUMPRODUCT. Para volúmenes mayores se requiere ampliar los rangos.

---

## Estructura del Plan de Cuentas

| Rango | Tipo | Naturaleza | Ejemplos |
|-------|------|------------|----------|
| 1000000–1999999 | Activo | Deudora | Caja, Bancos, CxC, PPE, Dep. Acumulada* |
| 2000000–2099999 | Pasivo Corriente | Acreedora | Proveedores, IVA DF, Remuneraciones |
| 2100000–2299999 | Pasivo No Corriente | Acreedora | Préstamos LP, Leasing LP |
| 2300000–2399999 | Patrimonio | Acreedora | Capital, Resultado Ejercicio, Acumulados |
| 3000000–3999999 | Gasto / Pérdida | Deudora | Costo Ventas, Remuneraciones, Arriendos |
| 4000000–4999999 | Ingreso / Ganancia | Acreedora | Ventas, Servicios, Otros Ingresos |

*Nota: Las cuentas de Depreciación Acumulada (1201002, 1202006, etc.) tienen código 1xxx pero naturaleza acreedora — son cuentas reguladoras del activo (NIC 16.73).*

---

## Indicadores Financieros Implementados

### Hoja Indicadores (14 KPIs)
- **Liquidez:** Razón Corriente, Razón Ácida, Razón de Efectivo
- **Deuda:** Endeudamiento, D/E Ratio, Cobertura de Intereses, Endeudamiento Corriente
- **Rentabilidad:** ROE, ROA, Margen Bruto, Margen Operacional
- **Actividad:** Rotación de Inventarios, Días de Cobro (PMC), Días de Pago (PMP)

### Hoja Flujo de Caja (8 KPIs adicionales)
- Runway de Caja, Cobertura Gastos Fijos, Burn Rate, Punto de Equilibrio
- PMC, Días de Inventario, Ciclo Conversión Efectivo (CCE), DSCR

---

## Resultado de la Última Auditoría

**Fecha:** 22/03/2026 | **Hallazgos:** 19 total

| Severidad | Cantidad | Estado |
|-----------|----------|--------|
| CRÍTICO | 0 | — |
| ALTO | 2 | **Resueltos** (tasas Pro-Pyme actualizadas con Ley 21.755) |
| MEDIO | 3 | **Resueltos** (retención honorarios actualizada con Ley 21.133) |
| BAJO | 3 | Informativos (notas EEFF, corrección monetaria, impuesto diferido) |
| INFO | 11 | Observaciones positivas de cumplimiento |

Todos los hallazgos ALTO y MEDIO han sido corregidos. Los hallazgos BAJO son limitaciones inherentes al formato Excel que se documentan como procedimientos manuales de cierre.

---

## Archivos del Proyecto

| Archivo | Descripción |
|---------|-------------|
| `Programa Contabilidad.xlsx` | Template contable principal (12 hojas, 2.420 fórmulas) |
| `auditoria-contable.skill` | Skill de auditoría empaquetado (instalable en Claude) |
| `Guía Skill Auditoría Contable.md` | Guía para usar el skill de auditoría |
| `Resumen Ejecutivo — Programa Contabilidad MYPE.md` | Este documento |

---

## Mantenimiento Recomendado

1. **Anual (abril):** Verificar tasas de impuesto vigentes (IDPC Pro-Pyme, retención honorarios) y actualizar las notas del EERR y Marco Regulatorio.
2. **Anual (enero):** Actualizar el sueldo mínimo en las notas del EERR (referencia Art. 44 Código del Trabajo).
3. **Ante reforma tributaria:** Ejecutar el skill de auditoría (`audita la contabilidad`) para verificar compliance con cambios normativos.
4. **Ante nuevos clientes:** Registrar en hoja Clientes, verificar que el plan de cuentas se replica correctamente.

---

*Documento generado el 22 de marzo de 2026. Normativa verificada al día de emisión.*
