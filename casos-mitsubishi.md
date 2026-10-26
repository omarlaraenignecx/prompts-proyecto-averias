# Criterios y documentos — programa Mitsubishi (plantilla `mitsubishi`)

**Versión de este recurso: 2026-10-26 (v1: preparado; la cuenta Mitsubishi sigue fuera del alcance del proyecto hasta que se pruebe en el ambiente de pruebas).** Quien lo edite actualiza aquí la fecha y la nota de qué cambió.

Todo lo que el conector y el área saben del programa Mitsubishi, para cuando el proyecto lo atienda. **Nada de `casos-garantiplus.md` aplica aquí salvo que este archivo lo diga**: los criterios de GarantiPlus (intervalos de 12,000 km / 6 meses, tolerancias, 12.5, 13.30…) se apoyan en cláusulas que este certificado no tiene.

## 1. Qué es el programa y cómo se ve en SIGA

- Es un **programa de garantía para unidades nuevas** vendidas por Mitsubishi Motors de México (producto «GARANTÍA REAL 7», certificado de febrero de 2019, vigente según el área). **No hay certificado individual por vehículo**: todas las averías comparten el condicionado del programa y el contrato en SIGA es el centinela **57227**.
- La ficha de `expediente_completo` marca la cuenta como **MITSUBISHI (programa, sin contrato individual)** y la plantilla del Informe como `mitsubishi`. `averias_pendientes` las lista con esa etiqueta.
- Para el Informe, **`numeroContrato` es el `policyId`** de la avería (el `contractId` es siempre el 57227 y no se imprime).
- La vigencia y el kilometraje de inicio no se pueden verificar contra un certificado individual: salen de la ficha de SIGA (póliza) y, si faltan, se dicen como «por confirmar»; nunca se inventan.
- El condicionado que el conector entrega para estas averías es el **certificado del programa** transcrito abajo (anexo), con su propia numeración (1–20). El motor de `generar_resolucion` con `plantilla: "mitsubishi"` transcribe los numerales de **ese** texto: un numeral que no exista ahí se rechaza.

## 2. La numeración es distinta de la de GarantiPlus (y es la que vale)

| Tema | Certificado Mitsubishi | EXCELLENCE (GarantiPlus) |
|---|---|---|
| Definiciones (AVERÍA/AS: rotura imprevista / fortuita; excluye la reducción gradual proporcional a antigüedad y km) | **1** | 1 |
| Exclusiones de piezas (lista literal) | **2** | dentro de la 1 |
| Cobertura PHEV (batería y componentes eléctricos, 7 años) | **3** | — |
| Objeto · Duración · Perfección · Delimitación geográfica | 4 · 5 · 6 · 7 | 2 · 3 · 4 · 5 |
| Obligaciones del contratante (8.3: «el auto deberá de ser nuevo») | **8** | 6 |
| Obligaciones del beneficiario (9.3 mantenimientos del fabricante; 9.4 conservar facturas) | **9** | 7 |
| Obligaciones de GarantiPlus (no cubre uso inadecuado ni desgaste normal) | **10** | 8 |
| Mantenimientos periódicos (**un solo párrafo: plan del fabricante, en tiempo y kilometraje; sin tabla ni carnet**) | **11** | 9 |
| Procedimiento en caso de avería (orden de entrada, presupuesto sin desmontar, facturas de mantenimiento; 72 h; inmovilizado; resolución en 48 h) | **12** | 10 |
| Límites (valor de venta del libro azul) | **13** | 11 |
| Exclusiones generales — **6 ítems** | **14** | 12 (7 ítems) |
| Operaciones no incluidas — **28 ítems** | **15** | 13 (31 ítems) |
| Devoluciones · Avisos · Rescisión · Sumisión · Protección de datos | 16–20 | 14–19 |

Mapa de ítems respecto del genérico (para traducir un razonamiento, nunca para citar): genérico 12.N → **14.N** para N ≤ 4, 12.6 → 14.5, 12.7 → 14.6; genérico 13.N → **15.(N−1)** para N ≥ 3. Lo que el genérico tiene y este certificado **no**: 12.5 (kilómetros de inicio sin relación con los de la avería), 13.2 (causa evidente durante la garantía del fabricante), 13.30 (ruidos, zumbidos, vibraciones), 13.31 (propulsión eléctrica o híbrida). Redacciones propias: 15.1 y 15.11 definen «previsible / epidémico» como falla en más de 50 vehículos; 15.8 añade «avería del motor originada por la falla de banda de distribución»; 15.4 añade mangueras y retenes a los elementos que pierden su morfología; 15.5 amplía la lista de consumibles.

**Cita siempre con la numeración de este certificado.** El área lo hace así en sus resoluciones Mitsubishi: 166585 (sensor O2, mantenimiento) citó **14** ítem 3 y **11**; 162031 (muelles, desgaste) citó **1**, **10** y **15**. Un Informe Mitsubishi que cite «12.4» o «13.8» está citando el contrato de otra cuenta.

## 3. Cómo se lee un caso Mitsubishi (lo que cambia respecto de GarantiPlus)

1. **Componente:** primero la lista literal de la cláusula **2** (asientos, habitáculo, neumáticos, carrocería, cristales, faros, molduras, consumibles, amortiguadores, escapes, discos y pastillas, correas, batería, elementos que perdieron su morfología). No hay periodo de espera de 90 días ni lista de componentes por producto. En un **PHEV**, la cláusula **3** cubre batería de alto voltaje y componentes eléctricos 7 años sin límite de km, pero no la pérdida gradual de carga.
2. **Causa:** cláusula **1** (AVERÍA/AS = rotura imprevista / fortuita; la reducción gradual proporcional a antigüedad y km no es avería), **10** (no cubre uso inadecuado ni desgaste normal) y los 28 ítems de la **15** (previsible/epidémico, mala reparación anterior, fin de vida útil, corrosión/morfología, consumibles y fugas, software, diagnóstico, elementos no garantizados y banda de distribución, mantenimiento preventivo, reglajes, defectos de serie, modificaciones, seguir circulando con testigos, mal uso, competición, sobrecarga, abrasivos, siniestro, piezas cambiadas sin fallar, asistencia in situ, grúa, combustibles no conformes, accesorios no de origen, estacionamiento, daños consecuenciales, lucro cesante, daños a terceros).
3. **Mantenimiento:** la **11** exige el plan del fabricante «tanto en periodos de tiempo como en kilometraje» y la 9.4 conservar las facturas. **No hay intervalo fijo en el certificado**: el intervalo es el del plan de Mitsubishi para ese modelo (normalmente 10,000 km o 6 meses, pero se lee del manual o del carnet del expediente, no se supone). La tolerancia de 1,000 km / 30 días es criterio del área de GarantiPlus y **no está decidido** que aplique aquí: si se usa, se dice como `Criterio del área` y se deja al técnico. Como el vehículo es nuevo por definición (8.3), se cuenta desde la primera factura.
4. **Proceso:** la **12** (orden de entrada, presupuesto **sin intervenir ni desmontar**, facturas de mantenimiento, 72 h tras requerirlas → 14.4; vehículo inmovilizado → 14.2; trabajo previo a la resolución → 14.1) y la **14** (comunicación fuera de vigencia → 14.5; incumplimiento del beneficiario → 14.6).
5. **Vigencia y km de inicio:** sin certificado individual, se toman de la ficha de SIGA; si no están, no se verifica la vigencia y se dice en una viñeta.
6. **Dos reglas del área que aquí no tienen cláusula** (decisión de Omar, 2026-09-25): «el odómetro no retrocede» (relación de kilometraje, 12.5 del genérico) y «ruidos, zumbidos y vibraciones no se cubren» (13.30 del genérico). Se aplican como criterio del área, **se marcan como «Cláusula especial del programa Mitsubishi»** en el veredicto y **no se cita un numeral que no exista**; decide el técnico.
7. **Motivo de catálogo de SIGA:** el mismo desplegable de 18 motivos (ver `instructions.md` §6.1); la causal se escoge por el hecho, y en el Informe se cita el ítem de la 14 o la 15 que lo sostiene.

## 4. El Informe de Resolución en Mitsubishi

- `generar_resolucion` con `plantilla: "mitsubishi"`. Dos cubiertas del área: **`cubierta-mitsu.docx`** (con el cuadro de valoración: procedente) y **`cubierta-mitsu-sin-valoracion.docx`** (sin cuadro: improcedente); el conector elige según el veredicto.
- La cubierta Mitsubishi sólo tiene estos campos del encabezado: **`numeroAveria`, `numeroContrato` (= `policyId`), `fechaAveria`, `modelo`, `vin`, `kmAveria`, `fechaCierre`**. Los demás (`producto`, `marca`, `fechaInicio`, `kmInicial`) se ignoran con aviso; «MITSUBISHI» va fijo en la plantilla.
- `numerales` se transcriben del certificado del programa: valen «14.3», «15.7», «11», «1»… y **no** valen «12.4» ni «13.8». La definición de AVERÍA/AS (cláusula 1) y la 11 completa van en `clausulasLiterales` cuando se citan, igual que la 9 en GarantiPlus. El numeral de cierre del diagnóstico no cubierto es el **15.7**.
- El cuerpo (`causaBreve`, `desarrollo`) sigue las fórmulas de `05-redaccion-informes.md`, cambiando sólo la numeración.
- Procedente: igual que en GarantiPlus (sólo partidas autorizadas, `totalConIva`), con el límite del libro azul de la cláusula 13 si el importe se acerca al valor del vehículo.

## 5. Lo que todavía no se sabe (no inventar)

- Las **condiciones especiales del programa** que David quedó de mandar (bomba de combustible y otras): hasta que lleguen, se dictamina sólo con el certificado y las dos reglas especiales del punto 3.6.
- Si la **tolerancia** de 1,000 km / 30 días del área aplica a Mitsubishi.
- Cómo se verifica la **vigencia** cuando la ficha no trae fecha de inicio de la póliza.

## 6. Qué cambiará en el flujo cuando Mitsubishi entre en alcance

Lo mismo de `instructions.md` (tres mensajes, tabla de parámetros, `causas` por refacción, `motivo` del catálogo), con tres diferencias: la plantilla es `mitsubishi`, el encabezado lleva sólo los siete campos de arriba, y toda cita es con la numeración del anexo. Antes de abrirlo hay que cerrar en `pruebas` un rechazo y una aprobación Mitsubishi de punta a punta.

---

## Anexo · Certificado de garantía del programa Mitsubishi (GARANTÍA REAL 7, febrero 2019)

Transcrito de `CERTIFICADO-MITSUBISHI-GARANTIA-REAL-7-febrero-2019.pdf` (31 páginas; las 12–31 son el anexo de VIN y no se transcriben). Los ítems de cada sección llevan aquí su numeral por posición (**S.N**), que es como se citan en el Informe. Las secciones 16–20 se dejan sólo por encabezado.

### 1.- DEFINICIONES

- **1.1 CONTRATANTE:** el vendedor del VEHÍCULO, obligado al pago del precio del certificado de garantía mecánica.
- **1.2 BENEFICIARIO:** el comprador del VEHÍCULO, destinatario de la garantía.
- **1.3 VEHÍCULO:** únicamente el descrito en la HOJA RESUMEN; no más de 450 C.V. ni denominación industrial ligera o pesada.
- **1.4 AVERÍA/AS:** «Se entiende por avería mecánica, eléctrica, o electrónica, la inutilidad operativa (conforme a las especificaciones del fabricante) de la pieza garantizada, debido a una rotura imprevista / fortuita. No se incluye en esta definición la reducción gradual en el rendimiento operativo de la pieza garantizada que sea proporcional y equivalente a su antigüedad y kilometraje (se entiende a partir de la primera matriculación del vehículo, y no a partir del inicio del contrato de garantía), ni las averías derivadas de accidentes o cualesquiera influencias externas.»
- **1.5** «Mediante este contrato de Garantía GarantiPlus México se compromete a pagar los costos razonables de reparación de una avería cubierta relativa al vehículo garantizado, dentro de los límites de pago por avería y condiciones del mismo. Quedan cubiertas por el certificado contratado la reparación o sustitución de todas las piezas o componentes que presenten defectos como consecuencia de una avería fortuita en los elementos mecánicos, eléctricos o electrónicos.»

### 2.- EXCLUSIONES

Se excluyen de manera expresa los siguientes elementos:
- **2.1** Asientos completos y mecanismos (mecánicos).
- **2.2** Elementos internos del habitáculo y/o maletero (tapizados, guarnecidos, reposabrazos, salpicadero, consolas, soportes, tapas, aireadores, ceniceros, encendedor, lámparas).
- **2.3** Neumáticos, válvula de rueda (con o sin sensor).
- **2.4** Totalidad de los elementos de carrocería.
- **2.5** Totalidad de cristales y lunas, incluida térmica.
- **2.6** Faros, intermitentes, calaveras, lámparas.
- **2.7** Molduras, embellecedores, espejos retrovisores completos, paragolpes.
- **2.8** Consumibles (filtros, cartuchos, aceite, juntas), amortiguadores, escapes, discos de freno, pastillas, correas, servicio periódico, servicios intermedios, lubricantes, combustibles, aditivos, carga de circuito de a/a (salvo que sea necesario por avería cubierta), bujías, calentadores, batería, escobillas, plumas limpiaparabrisas.
- **2.9** Elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas).

### 3.- COBERTURA PARA VEHÍCULOS PHEV

- **3.1 BATERÍA DE MANEJO ALTO VOLTAJE (sólo PHEV):** a. garantizada los primeros 7 AÑOS sin límite de kilómetros desde la fecha de inicio de la garantía; b. la pérdida gradual de la retención de carga debida al tiempo y el uso NO está cubierta; c. ver el Manual del propietario.
- **3.2 COMPONENTES ELÉCTRICOS (sólo PHEV):** a. garantizados los primeros 7 AÑOS sin límite de kilómetros; b. incluyen: motor eléctrico, motor eléctrico del sistema de refrigeración, líneas de alta tensión, conexión regular de carga, inversor – PHEV-ECU, conexión de carga rápida, trans eje, cargador a bordo / convertidor DC-DC.

### 4.- OBJETO DEL CERTIFICADO

GARANTIPLUS MÉXICO garantiza, dentro de los límites fijados en el presente documento, el pago de la reparación de las AVERÍA/AS.

### 5.- DURACIÓN DEL CERTIFICADO

- **5.1** El periodo de garantía será el indicado en el certificado; sólo estarán cubiertas las AVERÍA/AS que tenga el VEHÍCULO durante la vigencia del contrato.
- **5.2** Siempre que se hayan realizado en el VEHÍCULO en tiempo y forma los servicios y mantenimientos señalados.

### 6.- PERFECCIÓN Y EFECTOS · 7.- DELIMITACIONES GEOGRÁFICAS

Se perfecciona con la firma. La garantía se limita a las AVERÍA/AS que tengan lugar dentro de la República Mexicana.

### 8.- OBLIGACIONES DEL CONTRATANTE

- **8.1** Pagar el precio del certificado y su I.V.A.
- **8.2** Revisar el VEHÍCULO antes de venderlo y reparar cualquier avería antes de la venta.
- **8.3** «El auto deberá de ser nuevo para poder ser objeto de contratación de garantía.»

### 9.- OBLIGACIONES DEL BENEFICIARIO

- **9.1** Comunicar todas las AVERÍA/AS durante la vigencia.
- **9.2** Seguir estrictamente el PROCEDIMIENTO EN CASO DE AVERÍA/AS del punto 12.
- **9.3** «Realizar en el VEHÍCULO los mantenimientos periódicos exigidos por el fabricante en tiempo y forma.»
- **9.4** «Conservar las facturas correspondientes a los trabajos o reparaciones de mantenimiento descritos en el apartado anterior.»
- **9.5** Hacer un uso del VEHÍCULO razonable a sus características.
- **9.6** En caso de AVERÍA/AS, no agravarla por un uso inadecuado o negligente.

### 10.- OBLIGACIONES DE GARANTIPLUS

«GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en relación con el certificado contratado, tiene la obligación de, en los términos y con los límites fijados en el mismo, hacerse cargo de la reparación de las AVERÍA/AS cubiertas, que dentro del periodo de vigencia del certificado pueda tener el VEHÍCULO, siempre y cuando dichas AVERÍAS no traigan causa en un uso inadecuado del VEHÍCULO, o en el deterioro y/o desgaste normal del mismo.»

### 11.- MANTENIMIENTOS PERIÓDICOS

«Para que el certificado contratado sea efectivo, el BENEFICIARIO se obliga a efectuar en el VEHÍCULO los trabajos o tareas de mantenimiento exigidas por el POR EL FABRICANTE SIGUIENDO SU PLAN DE MANTENIMIENTO PRECONIZADO, tanto en periodos de tiempo como en kilometraje.» (Es todo: no hay tabla de intervalos ni mención de carnet.)

### 12.- PROCEDIMIENTO EN CASO DE AVERÍA/AS

- **12.1** El BENEFICIARIO comunica la avería a GarantiPlus por teléfono (+52 55 3300 5925) o correo (averias@garantiplus.mx).
- **12.2** Facilita al menos: Nº de garantía, placas, declaración de la avería, lugar y taller (o pide que se le indique uno).
- **12.3** Ya en el taller, el responsable vuelve a contactar y aporta: a. orden de entrada (fecha, kilómetros, descripción); b. **presupuesto aproximado, «QUE DEBERÁ REALIZARSE SIN INTERVENIR NI DESMONTAR EL VEHÍCULO»**; c. copia del libro de mantenimiento si dispone de él; d. copia de las **facturas de las inspecciones** que indica GarantiPlus, con identificación del taller, del vehículo (marca, modelo, placa, kilómetros), reparaciones desglosadas en piezas y mano de obra, fecha y firma o sello, fecha de entrega.
- **12.4** Hasta que la reparación no esté autorizada, **ningún desmontaje, montaje, reparación o intervención**, salvo que GarantiPlus lo requiera para determinar el origen; cualquier autorización de pruebas/desmontaje/diagnosis anterior a la aceptación la da el propietario. **El VEHÍCULO permanecerá inmovilizado** hasta que se resuelva el expediente.
- **12.5** Recibida la documentación, GarantiPlus decide si hace falta desmontaje y **resuelve por escrito y motivadamente en 48 horas** (sin domingos ni festivos) desde la documentación o el desmontaje; la resolución se remite al taller. Si no se sigue el procedimiento o la avería no está cubierta, el costo del desmontaje/montaje/intervención es del cliente, propietario o beneficiario.
- **12.6** Si se acepta, la resolución detalla las reparaciones y su valoración; GarantiPlus no se hace cargo de trabajos no autorizados en ella.
- **12.7** Autorizada la reparación, el taller la realiza.
- **12.8** Reparado, el taller envía la factura original firmada por el BENEFICIARIO, sólo con las reparaciones autorizadas y nunca por un importe superior a la valoración; junto con una copia firmada del informe de resolución.
- **12.9** La factura a nombre de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. (Calle Bosques de Duraznos 61, piso 1, Col. Bosques de las Lomas, Miguel Hidalgo, CDMX, 11700).
- **12.10** Recibida toda la documentación, pago en 15 días desde la recepción de la factura.
- **12.11** Si el presupuesto del taller supera la valoración autorizada, el BENEFICIARIO elige: i) reparar en el taller que indique GarantiPlus (desplazamiento a su costa) o ii) reparar según el presupuesto del taller aceptando por escrito la diferencia a su cargo, con dos facturas (una por la valoración autorizada a GarantiPlus, otra por la diferencia al beneficiario).
- **12.12** GarantiPlus se reserva el derecho a elegir los medios de reparación y a proporcionar las piezas.

### 13.- LÍMITES DEL CERTIFICADO

- **13.1** La valoración de la reparación nunca superará el valor de venta del VEHÍCULO según el libro azul del año de venta; si lo supera, GarantiPlus paga la menor de: i) el límite por AVERÍA/AS del certificado, ii) el límite del contrato, iii) el valor de venta del VEHÍCULO.
- **13.2** Si el vehículo no está en los boletines, el valor de venta se calcula por el valor medio de mercado (sin el más bajo ni el más alto) por un evaluador que elige y paga GarantiPlus.

### 14.- EXCLUSIONES GENERALES DEL CONTRATO

GarantiPlus podrá rechazar la reparación y/o el pago en los siguientes supuestos:
- **14.1** Cuando se haya realizado cualquier tipo de trabajo sobre el VEHÍCULO antes de la resolución del expediente.
- **14.2** Cuando el VEHÍCULO no haya permanecido inmovilizado en el taller desde la comunicación hasta la resolución.
- **14.3** Cuando el BENEFICIARIO no haya cumplido sus obligaciones de mantenimientos e inspecciones.
- **14.4** Cuando las facturas de los mantenimientos periódicos o cualquier documentación exigida en el artículo 12 no estén debidamente cumplimentadas o no se aporten **en un plazo de 72 h tras ser requeridas**.
- **14.5** Cuando la AVERÍA/AS haya sido comunicada transcurrido el plazo de duración del contrato, aun cuando haya acontecido antes de su expiración.
- **14.6** Cuando haya habido cualquier tipo de incumplimiento del CONTRATANTE o del BENEFICIARIO.

### 15.- OPERACIONES NO INCLUIDAS EN LA GARANTÍA

No estarán cubiertas, y GarantiPlus no estará obligada a reparar ni a pagar:
- **15.1** AVERÍA/AS y/o defectos previsibles: los que afecten a más de 50 vehículos de un modelo, o que usen un mismo componente, o tengan una falla específica, por defectos de fabricación, ensamble y/o desgaste prematuro.
- **15.2** AVERÍA/AS consecuencia de una mala reparación anterior.
- **15.3** Sustitución, reparación, ajustes, reajustes o reparaciones de piezas que hayan llegado al final de su vida útil como consecuencia de su función y usabilidad natural.
- **15.4** Daños por erosión, corrosión, deformación, oxidación, descomposición, herrumbre e incrustaciones, y elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas, mangueras, retenes).
- **15.5** Sustitución de lubricantes y aditivos, bujías, filtros, cartuchos, aceites, juntas, carburantes, cargas de a/a, **fugas de aceite, de refrigerante o de combustible**, neumáticos, amortiguadores, discos y pastillas de freno, correas de distribución, escapes, catalizadores, batería, plumas: cualquier elemento consumible.
- **15.6** Actualizaciones, programaciones o cargas de software de cualquier módulo electrónico.
- **15.7** Los costos de diagnóstico cuando las averías no queden cubiertas.
- **15.8** AVERÍA/AS derivadas del mal funcionamiento o falla de elementos no garantizados, o **avería del motor originada por la falla de banda de distribución**.
- **15.9** Operaciones de mantenimiento periódicas, de carácter preventivo.
- **15.10** Controles y/o reglajes, con o sin cambio de piezas.
- **15.11** Averías por defectos de serie, diseño defectuoso, vicios ocultos epidémicos, fallo epidémico (más de 50 vehículos…), campañas del fabricante.
- **15.12** Daños sobre piezas garantizadas producidos por alteración o modificación de la especificación del fabricante.
- **15.13** AVERÍA/AS por seguir circulando cuando los indicadores de avería, incidencia o alarma indiquen un mal funcionamiento.
- **15.14** AVERÍA/AS por mal uso o negligencia de utilización.
- **15.15** AVERÍA/AS por uso del vehículo en competiciones.
- **15.16** AVERÍA/AS por sobrecarga.
- **15.17** AVERÍA/AS por el uso de agentes abrasivos.
- **15.18** AVERÍA/AS por accidente, robo, tentativa de robo, incendio, explosión, vandalismo o catástrofes naturales.
- **15.19** Piezas cambiadas en la reparación sin que hayan fallado.
- **15.20** Cualquier intervención «in situ» de un servicio de asistencia en carretera.
- **15.21** Servicios de grúa, remolque y gastos de transporte del VEHÍCULO y ocupantes.
- **15.22** Averías por combustibles o lubricantes no conformes con el fabricante o contaminados.
- **15.23** Sustitución, mantenimiento o reparación de accesorios o piezas no montados de origen, aun siendo elementos garantizados.
- **15.24** Ningún servicio de grúa.
- **15.25** Gastos de estacionamiento y/o almacenamiento hasta la reparación.
- **15.26** Daños o pérdidas consecuencia de la AVERÍA/AS o del retraso en su reparación.
- **15.27** Lucro cesante por no poder utilizar el VEHÍCULO.
- **15.28** Daños a terceros que traigan causa en la AVERÍA/AS.

### 16.- DEVOLUCIONES · 17.- AVISOS · 18.- RESCISIÓN · 19.- SUMISIÓN EXPRESA · 20.- PROTECCIÓN DE DATOS

Sin efecto en el dictamen (rescisión anticipada sin devolución; aviso de cambio de domicilio con 30 días; rescisión automática por incumplimiento; tribunales de la Ciudad de México; datos personales conforme a la ley).
