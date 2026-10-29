[ 🌐 عربي ](README.ar.md) | [ 🇩🇪 Deutsch ](README.de.md) | [ 🇫🇷 Français ](README.fr.md) | [ 🇳🇱 Nederlands ](README.nl.md) | [ 🇪🇸 Español ](README.sp.md) | [ 🇬🇧 English ](README.md)


# Plantilla de Excel de contabilización por unidades y NAV de fondos: rastree la propiedad del pool de inversión, las cuentas de capital de los socios y los flujos de caja en múltiples fechas

<div align="left">

![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Microsoft%20Excel-217346)
![Domain](https://img.shields.io/badge/domain-Fund%20NAV%20Accounting-orange)

**Una hoja de cálculo dinámica de Microsoft Excel para la contabilización por unidades de fondos y una calculadora de valor liquidativo (NAV) diseñada para clubes de inversión, sindicatos inmobiliarios, pools privados de negociación y family offices que gestionan aportaciones y reembolsos de inversores en fechas escalonadas.**

[Lanzar la demo web interactiva de la calculadora de contabilización por unidades y NAV de fondos](https://hyvoid.github.io/investment-pool-nav-excel-template/) 

[Descargar el libro de Excel completo de contabilización por unidades y NAV de fondos (gratis)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)

</div>

El **libro de contabilización por unidades y NAV de fondos** es un **rastreador de pools de inversión en Microsoft Excel** automatizado y un **libro mayor de cuentas de capital de socios**. Calcula el **valor liquidativo (NAV) por unidad**, automatiza la **emisión de participaciones y el precio de reembolso**, previene la **dilución de beneficios previos a la entrada** y mantiene una **tabla de capitalización de inversores lista para auditoría** a lo largo de fechas de aportación escalonadas, sin requerir software institucional de administración de fondos.

---

## Vista previa visual: motor de cálculo del NAV y panel de cuentas de capital de socios

<img width="1536" height="1024" alt="Fund Unitization Excel Template Dashboard showing Net Asset Value per unit and investor ownership percentages" src="https://github.com/user-attachments/assets/42e2fe30-0173-45cc-945a-0d066ac2c974" />
<img width="1672" height="941" alt="Investment Pool Transaction Ledger in Excel tracking staggered capital contributions, withdrawals, and P&L updates" src="https://github.com/user-attachments/assets/1b9a5b9c-5037-4e2a-8ddb-fd1584d48a5c" />
<img width="1448" height="1086" alt="Partner Capital Account Statement in Excel displaying unit issuance, entry NAV pricing, and real-time redemption balances" src="https://github.com/user-attachments/assets/71d0cb5b-76f8-4152-b13d-0b58f792e9bc" />

> Pruebe las matemáticas de asignación basadas en unidades en su navegador antes de descargar: [Demo del simulador interactivo de contabilización por unidades y NAV de fondos](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/)

---

## Por qué fallan las tablas de capitalización estáticas en pools de inversión con múltiples fechas

Las disputas contables en pools de inversión surgen cuando los tesoreros combinan porcentajes de propiedad fijos, fechas de entrada de capital escalonadas y asignaciones manuales de pérdidas y ganancias (P&L) en una hoja de cálculo plana. Cuando un inversor solicita un reembolso parcial o total meses después, reconstruir el saldo exacto de su cuenta de capital expone los fallos estructurales de los modelos de porcentajes estáticos.

**El flujo de trabajo heredado de porcentajes estáticos (alto riesgo de disputas):**

```text
New capital subscription logged
-> Partner ownership percentage split adjusted manually
-> Unrealized pre-entry market gains mixed with new capital
-> Valuation and dilution dispute surfaces at investor withdrawal

```

**El flujo de trabajo automatizado de contabilización por unidades con NAV (listo para auditoría):**

```text
New capital subscription logged
-> Pool units issued at current mark-to-market NAV per unit
-> Early investors' accumulated gains locked in structurally
-> Real-time capital account balances updated at every cash flow event

```

Los operadores de pools, los GP de sindicatos y los tesoreros de clubes necesitan claridad operativa verificable. Cada socio general y socio limitado debe poder verificar los saldos exactos de liquidación, las unidades en cartera y las participaciones de propiedad implícitas en cualquier fecha de valoración.

---

## La lógica de negocio y la metodología: contabilidad NAV por unidades frente a repartos porcentuales

Este libro resuelve el **problema de asignación de capital multiperíodo** mediante la **contabilización por unidades de fondos mutuos y la contabilidad del valor liquidativo (NAV) ponderado por tiempo** (alineada con las normas FASB ASC 946 y de valoración de inversión colectiva de IOSCO).

### El problema comercial: flujos de capital asíncronos frente a movimiento continuo del mercado

En un pool de inversión dinámico, dos variables cambian de forma asíncrona:

1. **Valoración de la cartera (P&L de mercado):** Los activos subyacentes fluctúan a diario, semanalmente o mensualmente.
2. **Flujos de caja de los participantes (suscripciones y reembolsos):** Los inversores depositan o retiran capital a intervalos irregulares.

Cuando un pool rastrea la propiedad estrictamente por el efectivo acumulado aportado dividido entre el patrimonio total del pool, cada depósito posterior a una ganancia de mercado transfiere una parte del beneficio no realizado de los inversores tempranos al participante entrante. Por el contrario, depositar tras una caída obliga al nuevo entrante a subvencionar pérdidas históricas que nunca sufrió.

### La metodología central: emisión de unidades a valoración a mercado

En lugar de ajustar directamente los porcentajes de propiedad, el libro separa el **rendimiento económico** de la **dilución de capital** mediante una máquina de estados de tres ecuaciones ejecutada en cada fila de transacción:

1. **Valoración del NAV previa a la transacción:**

$$\text{NAV per Unit}_{t} = \frac{\text{Total Pool Market Value}_{t}}{\text{Total Outstanding Units}_{t-1}}$$



*Efecto comercial:* Todas las pérdidas y ganancias de mercado, realizadas y no realizadas, modifican el precio de la unidad ($\text{NAV per Unit}$), dejando intacto el recuento de unidades de cada participante.
2. **Precios de suscripción y reembolso a valor razonable:**

$$\text{Units Issued or Redeemed}_{i,t} = \frac{\text{Cash Flow}_{i,t}}{\text{NAV per Unit}_{t}}$$



*Efecto comercial:* El capital nuevo compra unidades al NAV actual ajustado a mercado en lugar del valor nominal. Los inversores tempranos conservan el 100% de su apreciación previa a la entrada porque el inversor entrante paga un precio mayor por unidad.
3. **Estado derivado continuo de la cuenta de capital:**

$$\text{Investor Balance}_{i,t} = \text{Units Held}_{i,t} \times \text{NAV per Unit}_{t}$$


$$\text{Economic Ownership \%}_{i,t} = \frac{\text{Units Held}_{i,t}}{\text{Total Outstanding Units}_{t}}$$



*Efecto comercial:* Los porcentajes de propiedad se convierten en un resultado derivado de las unidades en cartera en lugar de una tabla de entrada manual. Los reembolsos se liquidan de inmediato a $\text{Units Redeemed} \times \text{Current NAV}$ sin recálculos retroactivos.

---

## Tres trampas de asignación de capital en las hojas de cálculo de inversión manuales

### Trampa 1: Los repartos porcentuales estáticos diluyen las ganancias de mercado previas a la entrada

Asignar la propiedad según la cuota de aportación de capital falla en el momento en que dos inversores entran en una cartera en alza en fechas diferentes.

Suponga que un pool de inversión crece de $100,000 a $130,000 (rentabilidad del +30%) y un segundo inversor aporta $65,000, llevando los activos totales del pool a $195,000. Si el operador asigna al nuevo participante una participación plana del 33.3% ($65,000 / $195,000) sin contabilizar por unidades el patrimonio previo, el nuevo inversor captura de inmediato un derecho sobre la ganancia previa a la entrada de $30,000 del primer inversor.

Los operadores de pools que calculan repartos porcentuales planos en las fechas de aportación compensan insuficientemente a los inversores tempranos de forma rutinaria. La discrepancia contable se acumula silenciosamente a lo largo de múltiples rondas de financiación y desencadena disputas durante la liquidación.

### Trampa 2: Usar XIRR de Excel para calcular los saldos de capital de los socios

La función `XIRR` de Excel calcula una tasa interna de retorno anualizada sobre una única serie de flujos de caja con fechas. Mide el **rendimiento histórico ajustado por tiempo**, mientras que la administración de un pool requiere **contabilidad de saldos de liquidación actuales**.

Usar `XIRR` como mecanismo de asignación de patrimonio obliga al tesorero a mantener matrices de flujos de caja separadas para cada participante, recalcular las series de rentabilidad después de cada depósito y conciliar manualmente los saldos totales frente al patrimonio real del bróker. `XIRR` no mantiene ningún estado continuo de libro mayor; cada llamada de capital a mitad de período, distribución parcial o asiento de valoración a mercado requiere una nueva pasada manual de conciliación.

### Trampa 3: Conciliación de dilución diferida al cierre de período

En los modelos tradicionales de sociedad basados en porcentajes, las nuevas suscripciones de capital suelen registrarse como efectivo bruto y conciliarse solo en el cierre trimestral o anual. En la fecha de liquidación, el valor de mercado exacto de la cartera en el momento del depósito a mitad de período queda enterrado bajo las oscilaciones de mercado posteriores.

Si la cartera ganó un 25% antes de un depósito a mitad de trimestre y perdió un 10% después, agrupar el período completo borra la ventaja temporal del inversor temprano. La contabilidad NAV por unidades resuelve la dilución en el momento exacto en que el capital se liquida, fijando la transacción al NAV por unidad de ese día.

---

## Para quién es esta plantilla de Excel de contabilización por unidades de fondos

Esta plantilla está dirigida a operadores que han superado las hojas de cálculo porcentuales ad hoc y necesitan lógica de **software de contabilidad NAV de nivel institucional dentro de Microsoft Excel**:

| Rol y persona de búsqueda | Escenario operativo específico y caso de uso de la plantilla |
| --- | --- |
| **Tesoreros de clubes de inversión** *(hoja de cálculo contable para clubes de inversión)* | Gestionar cuotas mensuales de miembros, recargas irregulares y compras totales de participaciones de miembros para 3–20 miembros, generando estados de capital de miembros verificables. |
| **Líderes de sindicatos y operadores GP** *(plantilla de Excel de tabla de capitalización para SPV y sindicatos)* | Incorporar socios de capital en etapas avanzadas a través de múltiples tramos de cierre (closes continuos) protegiendo a los LP tempranos de la dilución de valoración previa al cierre. |
| **Gestores emergentes de hedge funds y pools de cripto** *(calculadora NAV sombra para fondos incubadora)* | Mantener un libro mayor contable sombra independiente junto a los estados del bróker para rastrear clases de participaciones de LP, precios de unidades y NAV por participación antes de contratar un administrador de fondos externo. |
| **Coordinadores de family offices** *(libro de asignación para pools de inversión familiar)* | Combinar capital de múltiples trusts familiares o cuentas generacionales que entran en fechas diferentes, garantizando una atribución justa del P&L y pistas de auditoría limpias para los CPA fiscales. |
| **Líderes de grupos de negociación propietaria y discrecional** *(rastreador de distribución de P&L para pools de negociación)* | Emitir unidades de participación cuando nuevos traders o financiadores depositan capital de margen, y liquidar los retiros parciales de beneficios a precios de unidad a valoración a mercado. |

---

## Casos de uso reales: resolución de escenarios de asignación de capital en múltiples fechas

### Escenario A: Closes continuos en sindicatos de inversión privados y SPV

Cuando un socio general (GP) de un sindicato capta capital en tres fechas de cierre separadas a lo largo de seis meses mientras los activos subyacentes ya se aprecian, los socios limitados (LP) tempranos exigen protección frente al aprovechamiento gratuito de los tramos posteriores. Al registrar cada tramo de cierre como una **suscripción de unidades al NAV actual**, los entrantes posteriores compran al precio de unidad incrementado, preservando el 100% de las ganancias previas al cierre para los inversores del Tramo 1.

### Escenario B: Entrada de miembros, recargas y compras de participaciones en clubes de inversión de acciones y cripto

Los clubes de inversión suelen recaudar depósitos mensuales desiguales permitiendo que los miembros existentes pausen aportaciones o retiren efectivo parcialmente. En lugar de renegociar los acuerdos de sociedad cada mes, el tesorero del club registra el valor de liquidación actual de la cuenta del bróker, actualiza el **NAV por unidad** y procesa todos los depósitos mensuales y solicitudes de compra de participaciones a ese único precio de liquidación.

### Escenario C: Fondos incubadora y pools de negociación de amigos y familiares que necesitan contabilidad sombra

Los gestores de fondos emergentes que administran una cartera de amigos y familiares de $100K–$5M rara vez justifican más de $15,000+/año en honorarios de administración de fondos institucional. Este libro funciona como un **sistema local de contabilidad NAV sombra en Excel**, produciendo libros mayores de unidades por inversor, historiales de aportaciones y resúmenes de cuentas de capital listos para la preparación fiscal por un CPA (soporte de Schedule K-1) o informes para LP.

---

## Qué rastrea el libro: mapeo de puntos de dolor a soluciones

| Punto de dolor contable del pool | Requisito de búsqueda de alta frecuencia | Solución integrada del libro de Excel |
| --- | --- | --- |
| **Dilución injusta en depósitos escalonados** | *Cómo asignar beneficios cuando los inversores entran en momentos diferentes* | **Motor automatizado de emisión de unidades:** Convierte los depósitos de efectivo entrantes en unidades del pool al precio del NAV por unidad exacto previo al depósito, aislando automáticamente las ganancias previas. |
| **Errores en la distribución manual del P&L** | *Hoja de cálculo de asignación de P&L para pools de inversión* | **Recálculo continuo del NAV:** Las ganancias y pérdidas de la cartera actualizan el NAV global por unidad; los saldos individuales de los inversores (`Units × Current NAV`) se ajustan dinámicamente sin ninguna edición manual de porcentajes. |
| **Cálculos complejos de retiros parciales** | *Calcular el valor de compra de participaciones / reembolso de un inversor en un pool de sociedad* | **Reembolso de unidades a valoración a mercado:** Convierte las solicitudes de retiro en dólares en reembolsos exactos de unidades al NAV actual, dejando intactos los saldos de los socios restantes. |
| **Informes opacos de saldos de inversores** | *Rastreador de cuentas de capital de socios y plantilla de Excel de tabla de capitalización* | **Panel en tiempo real por participante:** Muestra el capital neto invertido, el saldo de unidades, el % de propiedad económica, el NAV de entrada ponderado y el P&L acumulado en dólares de cada inversor. |
| **Fricción en la conciliación de auditoría e impuestos** | *Libro mayor de transacciones de fondos auditable para revisión de CPA* | **Pista de auditoría cronológica de transacciones:** Registra cada evento de valoración, depósito y reembolso con NAV con marca de tiempo, delta de unidades y estado del pool posterior a la transacción para exportación instantánea a CSV/PDF. |

---

## Caso práctico: asignación porcentual manual frente a contabilización NAV automatizada por unidades

**Perfil del pool:** 8 socios de capital que aportaron de forma desigual a lo largo de 18 meses a una cartera negociada activamente que se apreció ~40% en total. Inicialmente rastreada por el socio gestor principal en una hoja de cálculo manual de repartos porcentuales.

**El fallo operativo:** Tres inversores se unieron a mitad de ciclo durante meses de alta volatilidad. El socio gestor recalculaba manualmente los porcentajes de aportación de capital después de cada depósito y distribuía el P&L mensual según esos pesos estáticos.

Cuando dos socios tempranos solicitaron reembolsos totales de capital, tres disputas contables detuvieron las distribuciones:

1. Cómo asignar una caída del 15% de la cartera a mitad de año que ocurrió entre las fechas de financiación de la Cohorte 1 y la Cohorte 2.
2. Cómo corregir un depósito de socio de $25,000 registrado en la pestaña de conciliación mensual equivocada.
3. Qué tabla de porcentajes de propiedad regía el último mes parcial antes de la liquidación del reembolso.

Reconstruir las cuentas de capital históricas requirió tres semanas de contabilidad forense por parte de un CPA externo.

### Comparación: hojas de cálculo porcentuales estáticas frente a contabilidad NAV por unidades

| Operación contable | Hoja de cálculo manual de repartos porcentuales (antes) | Libro de Excel automatizado de contabilización por unidades de fondos (después) |
| --- | --- | --- |
| **Modelo de propiedad patrimonial** | Porcentajes estáticos de aportación de capital sobrescritos manualmente después de cada depósito | **Modelo NAV por unidades** dinámico; unidades emitidas a precio de valoración a mercado en cada depósito |
| **Gestión de entrantes tardíos y dilución** | El capital nuevo diluía las ganancias no realizadas previas salvo aislamiento manual por tramo | **Precios automáticos antidilución**; el capital entrante compra unidades al NAV actual |
| **Asignación periódica del P&L** | Recálculo manual al cierre de período sobre tablas porcentuales de socios cambiantes | **Ajuste del NAV por unidad en tiempo real**; los saldos de unidades de los inversores permanecen constantes durante los movimientos de mercado |
| **Liquidación de reembolsos y compras de participaciones de socios** | Reconstrucción forense de las pestañas históricas de P&L mensual requerida antes del pago | **Precio de liquidación instantáneo** (`Redeemed Units × Current NAV`) leído directamente del libro mayor en vivo |
| **Pista de auditoría y superficie de disputa** | Alto riesgo de error en cada sobrescritura manual de fórmulas y arrastre de período | **Libro mayor cronológico de transacciones de fuente única**; la conciliación se gestiona en la capa contable |

---

## Normas institucionales detrás de la contabilidad NAV por unidades

Los vehículos de inversión colectiva regulados —incluidos fondos mutuos, ETF, vehículos SPV de capital privado y hedge funds— se apoyan en la contabilidad del valor liquidativo por unidades porque los flujos de caja asíncronos de los inversores crean un problema de atribución económica que las tablas porcentuales planas no pueden resolver.

Un inversor que suscribe el día 90 en una cartera en apreciación no asumió el riesgo de mercado de los días 1 al 89. La estructura por unidades codifica el momento de entrada directamente en el **precio de la unidad de suscripción (NAV en la fecha de depósito)**. El rendimiento de mercado posterior fluye estrictamente a través de las **fluctuaciones del NAV por unidad**, mientras que los retiros de los inversores se liquidan al NAV de liquidación vigente.

| Dimensión contable del fondo | Mecanismo NAV institucional implementado en este libro |
| --- | --- |
| **Momento de la suscripción de capital** | Fijado en el precio de compra del inversor mediante el **NAV por unidad en la fecha de depósito** |
| **Rendimiento de mercado de la cartera (P&L)** | Reflejado estrictamente a través del **movimiento del NAV por unidad**; los recuentos de unidades en circulación permanecen sin cambios |
| **Tamaño de la aportación de capital** | Reflejado en la **cantidad de unidades del pool emitidas** ($\text{Deposit} \div \text{Current NAV}$) |
| **Protección contra la dilución para los LP existentes** | Aplicada emitiendo nuevas unidades al **NAV actual a valoración a mercado** en lugar del valor nominal inicial |

**Normas contables y de valoración de referencia:**

* [CFA Institute: Estructura y valoración de vehículos de inversión colectiva](https://www.cfainstitute.org)
* [IOSCO: Principios para la valoración de esquemas de inversión colectiva](https://www.iosco.org)
* [FASB ASC 946: Servicios financieros — Normas contables para empresas de inversión](https://www.fasb.org)

---

## Ejemplo numérico detallado: cómo funcionan la emisión de unidades y el precio del NAV

El **valor liquidativo por unidad** de un pool es igual al valor de mercado total de la cartera dividido entre el total de unidades en circulación. El capital entrante compra nuevas unidades al NAV por unidad actual. Las ganancias y pérdidas de mercado alteran el NAV por unidad dejando sin cambios los recuentos de unidades en circulación.

| Evento de transacción | Valor de mercado total del pool | Total de unidades en circulación | NAV por unidad | Delta de unidades del socio e impacto contable |
| --- | --- | --- | --- | --- |
| **1. El inversor A deposita $100,000** | $100,000 | 100,000 | $1.000 | Al inversor A se le emitieron **100,000 unidades** al NAV nominal inicial de $1.000 (propiedad del 100%) |
| **2. Ganancia de mercado de la cartera: +30%** | $130,000 | 100,000 | $1.300 | Recuento de unidades sin cambios; el NAV sube a **$1.300/unidad** (saldo del inversor A = $130,000) |
| **3. El inversor B deposita $65,000** | $195,000 | 150,000 | $1.300 | El inversor B compra **50,000 unidades** al NAV de $1.300 (propiedad del 33.33%; A conserva $130,000) |
| **4. Pérdida de mercado de la cartera: −15%** | $165,750 | 150,000 | $1.105 | Recuento de unidades sin cambios; el NAV cae a **$1.105/unidad** (A = $110,500; B = $55,250) |
| **5. El inversor A reembolsa 50,000 unidades** | $110,250 | 100,000 | $1.105 | El inversor A retira **$55,250 en efectivo** (50,000 × $1.105); mantiene 50,000 unidades (50% del pool restante) |

**Por qué las matemáticas por unidades protegen a cada participante:**

* **Precio justo de entrada:** El inversor B aporta $65,000 cuando el precio de la unidad es $1.300, recibiendo 50,000 unidades. El beneficio previo a la entrada de $30,000 del inversor A permanece 100% intacto dentro de las 100,000 unidades del inversor A.
* **Atribución proporcional de las caídas:** Tras la pérdida de mercado del 15%, el NAV cae de $1.300 a $1.105. Las 50,000 unidades del inversor B valen $55,250—absorbiendo exactamente una pérdida del 15% sobre sus $65,000 de capital de entrada sin heredar ni subvencionar el período anterior del inversor A.

---

## Tutorial de inicio rápido: cómo configurar su libro mayor NAV de pool de inversión en 6 pasos

Siga este flujo de trabajo paso a paso para pasar su club de inversión, sindicato o pool de negociación de los repartos porcentuales manuales a la contabilización NAV automatizada por unidades:

1. **Pruebe su escenario de flujo de caja en el simulador en vivo del navegador**
Abra la [demo web interactiva de contabilización por unidades y NAV de fondos](https://hyvoid.github.io/Fund-Unitization-NAV-Excel-tool-for-cashflow-management/) para simular depósitos escalonados, oscilaciones de P&L de mercado y reembolsos antes de introducir sus números reales de sociedad.
2. **Inicialice los parámetros del pool y los perfiles de los socios**
Registre sus inversores iniciales, establezca su moneda base y defina su NAV nominal por unidad de apertura (por ejemplo, $1.00 o $100.00 por unidad) en la fecha de constitución.
3. **Registre las suscripciones de capital para emitir unidades automáticamente**
Anote cada depósito de inversor junto con el valor de mercado actual de la cartera. El libro calcula el NAV por unidad vigente y emite la cantidad exacta de unidades fraccionarias o enteras en la cuenta de capital del socio.
4. **Registre periódicamente el P&L de la cartera a valoración a mercado**
Introduzca las actualizaciones de valoración de la cartera, realizadas y no realizadas, con una frecuencia diaria, semanal o mensual—inmediatamente antes de cualquier flujo de caja externo—para actualizar el NAV por unidad del pool.
5. **Procese los retiros de inversores y los reembolsos de unidades**
Introduzca las solicitudes de reembolso parciales o totales. El motor liquida el número correspondiente de unidades al NAV actual, reduce el total de unidades en circulación y recalcula los pesos de propiedad posteriores al reembolso para los socios restantes.
6. **Audite los estados de cuentas de capital y descargue el libro de Excel reutilizable**
Verifique la integridad de los saldos mediante los indicadores automatizados de comprobación de errores y exporte registros de transacciones limpios para informes a LP o preparación fiscal. Una vez validado el flujo de trabajo en la demo web de sesión única, **[descargue la plantilla de Excel completa y reutilizable de contabilización por unidades y NAV de fondos](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)** para guardar libros mayores históricos permanentes, personalizar los paneles de socios y gestionar operaciones continuas de pools multianuales sin conexión en Microsoft Excel.

*Aviso: este libro es una plantilla de contabilidad operativa y de apoyo a la toma de decisiones. Consulte a un CPA cualificado o a un abogado especializado en fondos respecto a las asignaciones fiscales de la sociedad (por ejemplo, IRC Section 704(b) / Schedule K-1) y el cumplimiento de normativa de valores en su jurisdicción.*

---

## Descargue la plantilla de Excel completa

¿Listo para automatizar la contabilidad de su pool de inversión y mantener un libro mayor de socios permanente y auditable?

👉 **[Obtenga el libro de Excel completo de contabilización por unidades y NAV de fondos (descarga gratuita)](https://www.theseusworkshop.com/l/FundUnitizationDashboad?utm_source=github&utm_medium=GitHub%20README&utm_campaign=readme%20new%20launch&utm_content=fund-unitization-nav)**

---

## Alcance técnico y limitaciones operativas

* **Dependencia de la precisión de los datos de entrada:** La precisión del NAV por unidad depende de introducir las valoraciones de la cartera a valoración a mercado inmediatamente antes de registrar cualquier nuevo depósito o retiro de capital.
* **Alcance contable operativo (no es asesoramiento fiscal/legal):** Refleja las matemáticas estándar de contabilización NAV por unidades ponderadas por tiempo; las asignaciones fiscales específicas de la sociedad, las conciliaciones contabilidad-impuestos y las presentaciones regulatorias requieren validación por un CPA colegiado o asesor legal.
* **Entrada manual de valoraciones sin conexión:** Diseñado para privacidad y cero dependencias externas; los valores de mercado de la cartera se introducen manualmente en lugar de obtenerse mediante API de bróker en tiempo real.
* **Alcance estándar de honorarios y flujos de caja:** Cubre suscripciones de capital, reembolsos y P&L de mercado. Las cascadas complejas de carried interest GP/LP, las tasas mínimas (hurdle rates), las comisiones de rendimiento de high-water mark y la cobertura FX multidivisa quedan fuera del alcance de esta versión base.
* **Escala recomendada del pool:** Optimizado para pools de inversión con **3 a 20 participantes** que registran transacciones semanales o mensuales.
* **Compatibilidad del sistema:** Construido para **Microsoft Excel 2016 o posterior (Windows y macOS)** usando fórmulas nativas estándar sin dependencias de seguridad de macros/VBA.
* **Disposiciones estructurales especiales:** Las asignaciones ilíquidas de side-pocket, los calendarios de vencimiento de períodos de bloqueo y las colas de reembolso con compuertas requieren ajustes de calendario personalizados fuera de la pestaña central del libro mayor.

---

## Acerca de Theseus Workshop

Construimos modelos financieros y operativos de Excel transparentes y listos para auditoría para fondos pequeños, sindicatos y negocios dirigidos por operadores que necesitan lógica contable institucional dentro de Microsoft Excel.

Cada plantilla se ejecuta localmente con fórmulas nativas de hoja de cálculo, dando a su equipo visibilidad total de cada celda de cálculo y cada asiento del libro mayor de propiedad.

¿Gestiona flujos de trabajo complejos de asignación de capital, conciliación o rastreo de propiedad en hojas de cálculo? **[Explore nuestra biblioteca completa de plantillas de Excel financieras y operativas en Theseus Workshop →](https://www.theseusworkshop.com)**

---

## Licencia

Distribuido bajo la [Licencia de código abierto MIT](https://opensource.org/licenses/MIT).

