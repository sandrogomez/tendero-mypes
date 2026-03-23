# Skill: Auditoría Contable — Programa de Contabilidad MYPE Chile

## ¿Qué hace este skill?

Revisa automáticamente el archivo "Programa Contabilidad.xlsx" buscando errores técnicos y problemas de cumplimiento normativo contable chileno. Al terminar, inserta una hoja "Auditoría" dentro del mismo archivo con una tabla detallada de todos los hallazgos encontrados, su severidad, la norma que los respalda y un plan concreto para resolverlos.

## ¿Cuándo se activa?

Cada vez que le pidas a Claude algo como: "audita la contabilidad", "revisa el programa contable", "busca errores en el xlsx", "valida el libro diario", "verifica el balance", "chequea la normativa chilena", o cualquier variante similar.

## ¿Qué revisa exactamente?

### 1. Estructura del archivo
Verifica que estén presentes las 10 hojas del sistema (Inicio, Clientes, Nuevo Cliente, Cuentas, Libro Diario, Libro Mayor, Indicadores, Flujo de Caja, Balance General, Estado Resultados), que estén en el orden correcto y que los encabezados de columna sean los esperados.

### 2. Libro Diario
Revisa la integridad de cada asiento contable: que cada asiento cuadre (Debe = Haber, partida doble), que las fechas sean válidas y estén en orden cronológico, que cada código de cuenta exista en el Plan de Cuentas para ese cliente, que cada cliente exista en la hoja Clientes, que no haya montos negativos, que todos los asientos tengan glosa y que cada asiento tenga mínimo 2 líneas.

### 3. Plan de Cuentas
Busca códigos duplicados por cliente, verifica que la clasificación sea coherente con el código (1xxx = Activo, 2xxx = Pasivo, 3xxx = Gasto, 4xxx = Ingreso), identifica cuentas sin movimientos en el Libro Diario (huérfanas) y detecta correctamente las cuentas de depreciación acumulada como cuentas reguladoras del activo.

### 4. Fórmulas y referencias cruzadas
Detecta errores de fórmula (#VALUE!, #REF!, #NAME?, #DIV/0!, #N/A) en todas las hojas. Claude además verifica manualmente que el Balance General cuadre (Activos = Pasivos + Patrimonio), que el Estado de Resultados sea coherente con el Libro Diario y que los Indicadores y Flujo de Caja no tengan referencias circulares.

### 5. Cumplimiento normativo chileno
Verifica aspectos de la normativa vigente: que existan cuentas de IVA Crédito y Débito Fiscal (D.L. 825), que el plan de cuentas incluya las cuentas mínimas para una MYPE (Caja, Bancos, Capital), que exista provisión de vacaciones (Art. 67 Código del Trabajo, NIIF Pymes Sec. 28), que las notas normativas en Balance y EERR citen correctamente las secciones de NIIF, y que las tasas de impuesto estén actualizadas.

## ¿Qué produce?

Una hoja nueva llamada "Auditoría" insertada en el mismo archivo xlsx, con:

- Un banner profesional con el mismo estilo visual del resto del archivo
- Metadata con fecha, nombre del archivo y resumen de hallazgos
- Una tabla con columnas: Nº, Severidad, Categoría, Hoja, Ubicación, Hallazgo, Referencia Normativa, Impacto, Plan de Resolución, Estado
- Filas coloreadas por severidad (rojo = crítico, naranja = alto, amarillo = medio, azul = bajo, verde = informativo)
- Filtros automáticos para poder ordenar y filtrar por severidad o categoría
- Resumen ejecutivo al final con recomendación general

## Niveles de severidad

| Nivel | Significado | Ejemplo |
|-------|-------------|---------|
| CRÍTICO | Invalida estados financieros o causa incumplimiento legal | Asiento descuadrado, balance que no cuadra |
| ALTO | Distorsiona significativamente la información financiera | Cuenta mal clasificada, código inexistente |
| MEDIO | Puede generar confusión o errores futuros | RUT mal formateado, fechas desordenadas |
| BAJO | Mejora recomendada para calidad profesional | Asiento sin glosa |
| INFO | Observación sin acción requerida | Cuentas sin movimientos |

## Normativa de referencia

El skill basa sus verificaciones en: NIIF para Pymes (BT N°82 del Colegio de Contadores A.G.), LIR (D.L. 824), D.L. 825 IVA, Código de Comercio Art. 25, Código del Trabajo, Ley 20.720 de Insolvencia, y estándares SERCOTEC/CMF/CORFO para MYPE.

## Componentes del skill

| Archivo | Función |
|---------|---------|
| SKILL.md | Instrucciones completas para Claude |
| scripts/auditar.py | Script que ejecuta las verificaciones automáticas y genera un JSON |
| scripts/insertar_hoja_auditoria.py | Script que convierte el JSON en la hoja formateada del xlsx |
| references/normativa_chile.md | Referencia con artículos de ley, secciones NIIF y umbrales de indicadores |

## Cómo instalar

Hacer doble clic en el archivo `auditoria-contable.skill` o arrastrarlo a la app de Claude.
