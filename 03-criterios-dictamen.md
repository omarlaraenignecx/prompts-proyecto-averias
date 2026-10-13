# Criterios de dictamen — GarantiPlus MX

Reglas para decidir si una avería procede. Todas se apoyan en lo que dicen los certificados de GarantiPlus leídos en casos reales de SIGA, o en lo observado en esos casos. No existe un contrato general de referencia: **cada avería tiene su propio certificado y es el único texto contractual que cuenta**; este documento solo describe cómo suele leerlo el área y qué buscar en él. Cuando una regla es criterio del área y no cláusula, se dice. **El certificado de cada caso, que llega completo dentro de `expediente_completo`, es la primera fuente de verdad y manda sobre este documento.** Para redactar el Informe, ver `05-redaccion-informes.md`.

## 0. Jerarquía de fuentes y gobierno del criterio

1. **El certificado de esta avería** (hoja resumen + condicionado). Antes de usarlo, confirma que es el de este folio: número de contrato, producto y VIN tienen que coincidir con la ficha de SIGA. Si no coinciden, no se cita nada y se reporta la discrepancia. Un contrato de otro producto, aunque tenga el mismo nombre comercial, no sirve ni para "ver cómo se numera".
2. **SIGA y las evidencias del expediente** (ficha, presupuesto, diagnóstico, odómetro, carnet, facturas, fotos, videos, Seguimiento). Aportan los hechos. Si dos de ellas se contradicen en un dato que cambia el veredicto o el Informe (VIN, kilometraje, fecha, importe), no se elige en silencio: se muestran los dos valores con su fuente y decide el técnico.
3. **Los criterios del área** fijados en este documento y en las instrucciones (intervalo por omisión, tolerancia, qué cuenta como servicio, orden de causales, IVA incluido). Se aplican tal cual y se citan como "criterio del área". Solo cambian cuando el área lo decide, no porque un caso haya salido distinto.
4. **Los casos de `02-casos-referencia.md`**: ilustran, no deciden. Una decisión excepcional de un folio (atención comercial, aceptación "con lo que hay") no se traslada a otro.

Si falta un dato sin el cual no se puede decidir, el resultado es 🟡 pendiente, no una decisión por inferencia. Si el técnico decide contra la lectura del certificado (excepción comercial u otra), se registra quién, por qué y con qué alcance, y la excepción vale solo para ese folio.

### La numeración de las cláusulas cambia por producto

Los numerales que aparecen en este documento y en la tabla de motivos de las instrucciones son los más frecuentes en los certificados leídos hasta ahora (CARSHOP M2 VD, SUV GM M1 36, SEDANES GM M2, FARRERA EXCELLENCE M2, donde coinciden) y sirven solo para saber qué buscar. Otros productos los recorren. Verificado en un certificado real **EXCELLENCE AFASA M2 12M**: su cláusula 12 se llama "EXCLUSIONES ADICIONALES", empieza con un 12.1 nuevo (cobertura del fabricante) y lo demás se desplaza: mantenimientos en 12.4 (no 12.3), plazo de 72 h en 12.5 (no 12.4), relación de kilómetros en 12.6 (no 12.5), y el **periodo de espera de 90 días para "transmisión y dirección" está en el 12.9**, no en la cláusula 1.

Regla: **cita siempre el numeral tal como aparece en el certificado del caso**, nunca el de este documento. Para localizar una regla, busca por su texto ("mantenimientos e inspecciones", "72h", "periodo de espera", "90 días", "kilómetros de inicio"), no por su número.

## 1. Lo primero: qué trae la cláusula 1 del certificado de este caso

El condicionado cambia por producto. Antes de evaluar componente y causa, lee la cláusula 1 del certificado real:

- **Si trae una lista "Se excluyen de manera expresa los siguientes elementos"** (visto en EXCELLENCE CARSHOP M2 VD y en EXCELLENCE VANGUARDIA M1, que además añade incisos sobre lo que sigue a cargo de la garantía del fabricante): esa lista manda. Suele incluir asientos y sus mecanismos, elementos del habitáculo y maletero, neumáticos y válvulas de rueda, carrocería completa, cristales, faros y lámparas, molduras y espejos, consumibles (filtros, aceite, juntas, amortiguadores, escapes, discos y pastillas, correas, bujías, batería, plumas), elementos deformados (bujes, gomas, soportes) y **transmisiones DSG, CVT y cajas de dirección electroasistida o electrónica durante un periodo de espera de 90 días**. Un componente de esa lista → **Componente excluido**. La lista se cita desde el certificado del caso, no desde esta descripción.
- **Si no trae lista** (visto en EXCELLENCE SUV GM M1 36 y FARRERA EXCELLENCE M2): el componente está cubierto salvo que caiga en el numeral 13 (operaciones no incluidas).
- El nombre del producto (M1, M2, VD, 12M…) **no** predice cuál de los dos casos aplica; hay que leer la cláusula 1 de cada certificado.

Desde octubre de 2026 el certificado del conector llega completo. Si por excepción llegara truncado, busca en el índice del expediente un documento del taller con el contrato completo (CONTRATO.pdf o clase certificado) y pídelo con `leer_documento`; si tampoco existe, dilo en una viñeta y no cites la lista de la cláusula 1 de memoria: sin texto del certificado no hay cita.

**Garantía del fabricante.** Algunos certificados (VANGUARDIA M1 en 1.10–1.11 y 13.30; AFASA M2 12M en 12.1) dejan a cargo del fabricante lo que aún cubra su garantía amplia o de tren motriz. Si la ficha dice "Garantía de fábrica: sí", comprueba si la vigencia de GarantiPlus arrancó al terminar la cobertura del fabricante (la hoja resumen lo permite): en ese caso la garantía de fábrica ya no aplica y el componente se evalúa normalmente. Si la garantía del fabricante sigue vigente para ese componente, dilo en una viñeta y deja que el técnico decida; no es motivo de rechazo automático.

En ambos casos, la definición de AVERÍA es la misma: inutilidad operativa de una pieza garantizada por **rotura imprevista o fortuita**. No es avería la reducción gradual de rendimiento proporcional a la antigüedad y el kilometraje (desgaste), ni la derivada de accidentes o influencias externas.

## 2. Mantenimiento: la regla depende del tipo de vehículo (cláusula 9)

| Vehículo | Regla | Fuente |
| --- | --- | --- |
| **Nuevo, con garantía de fábrica vigente** (ficha → "Garantía de fábrica: sí") | Plan de mantenimiento programado del fabricante, en tiempo y en kilometraje. Si el plan no está en el expediente, el área aplica **12,000 km o 12 meses, lo que ocurra primero**. | Cláusula 9 "NUEVOS" + criterio del área |
| **Seminuevo, o garantía de fábrica terminada** ("Garantía de fábrica: no") | **6 meses o 10,000 km, lo que ocurra antes**, aunque el fabricante indique más. Revisión mínima: aceite, filtro de aceite y verificación de fugas, ruidos y holguras. Siempre en distribuidor autorizado del fabricante; un mantenimiento fuera de distribuidor autorizado invalida el contrato. | Cláusula 9 "SEMINUEVOS" (contractual) |

Cómo se mide, en los dos casos:
- **Desde el servicio anterior**: recorrido en km y días entre un servicio y el siguiente. El primer tramo arranca en la fecha de la primera factura (nuevo) o en el servicio anterior documentado (seminuevo).
- **Tolerancia de hasta 1,000 km o 30 días por tramo** (criterio del área): nuevo, excedido desde 13,001 km o 396 días; seminuevo, desde 11,001 km o 213 días. Verificado: 12,630 km aceptado (160678), 13,077 km rechazado (159886).
- Lo que acredita: carnet sellado por el distribuidor con km, facturas del mantenimiento, o un historial del distribuidor (reporte de servicio, registro del sistema de la marca). Si el cliente no tiene ninguno, puede pedir reimpresión de facturas al distribuidor (cláusula 9).
- **Si el expediente no trae ningún comprobante**, el mantenimiento no se evalúa ni bloquea el veredicto, con "servicios a tiempo" en sí o en no (el área aceptó 159721 y 160612 con "no" y sin comprobantes). Se anota la ausencia; pedir el carnet antes del Informe es decisión del técnico.
- **Desde dónde se cuenta**: nuevo/M1, todo el historial desde la primera factura; seminuevo/M2, desde la fecha y el km de inicio del contrato (161833 se aceptó pese a un hueco de 997 días anterior al contrato; 160942 se rechazó contando desde "INICIO GARANTÍA"). El tramo abierto hasta la fecha de avería también cuenta.
- **Vehículos medidos en horas** (motos acuáticas): la cláusula 9 de esos certificados fija el intervalo en horas de uso (100 h); se mide por horas, no por meses.
- Un rótulo de factura ("servicio de 20 mil") no es el plan del fabricante.
- Reporta así: "N de M servicios exceden el intervalo (recorridos: …)". La tabla completa (fecha · km · días · recorrido) va en la argumentación y en el Informe si se rechaza.
- Distingue **no cumplió** (hay comprobantes y muestran intervalos excedidos → Intervalo de Mantenimiento Excedido, el inciso de la cláusula 12 sobre incumplimiento de mantenimientos, 12.3 en la mayoría de los certificados) de **no acreditó** (se requirieron comprobantes y no llegaron en 72 h → Falta al proceso o incompleto (Distribuidor), el inciso de las 72 h, 12.4 en la mayoría). Y de **no hay comprobantes y nadie los pidió**, que no es ninguna de las dos: se anota y se dictamina con el resto.
- **Cuando caben dos causales**, el motivo de catálogo sigue este orden: falta al proceso (desmontaje sin autorización, 12.1; documentación no entregada, 12.4) → causa excluida (fuga, desgaste, siniestro, influencia externa) → intervalo de mantenimiento. El área rechazó 161008 por desmontaje sin autorización aunque había boletín del fabricante, y 161239 y 162922 por la causa aunque el mantenimiento también fallaba. Un boletín de servicio del fabricante no convierte por sí solo la falla en Campaña y/o Fallo epidémico (13.12); úsalo como refuerzo, no como motivo principal.
- Una "revisión general" o "inspección" **sin cambio de aceite y filtro** no cuenta como revisión para seminuevos: la cláusula 9 fija como mínimo aceite, filtro de aceite y verificación de fugas, ruidos y holguras. En cambio, un **servicio del plan sellado en el carnet** (10, 20, 30 mil…) sí cuenta aunque la factura no desglose el aceite: el sello del distribuidor lo acredita.
- El tramo se mide entre servicios reales, aunque cruce la fecha de inicio de vigencia: un tramo que empezó antes de la vigencia y terminó dentro de ella cuenta completo.

**Qué vale como comprobante.** La cláusula 9 acepta el carnet sellado, las facturas o una **reimpresión** pedida al distribuidor. Las "prefacturas / estados de cuenta" reimpresos por el distribuidor (con placa, VIN, kilometraje, fecha y conceptos de aceite y filtro) se aceptaron como historial válido (167410: diez reimpresiones del distribuidor, 2022-2026). Lo que importa es que identifiquen la unidad, la fecha, el kilometraje y el cambio de aceite y filtro en distribuidor autorizado.

## 3. Periodo de espera

- Existe solo en los productos cuyo certificado lo mencione, y puede estar en dos lugares: en la lista de la **cláusula 1** (CARSHOP M2 VD: "DSG, CVT y cajas de dirección electroasistida o electrónicas, durante el periodo de espera de 90 días") o dentro de la **cláusula 12** (AFASA M2 12M, 12.9: "transmisión y dirección", 90 días). Búscalo por texto en todo el certificado. Siempre son **90 días desde el inicio de vigencia**.
- No se extiende a otros sistemas ni a productos cuyo certificado no lo mencione.
- Si la fecha de avería (registro en SIGA) cae dentro de esos 90 días y el componente es uno de esos → **Periodo de Espera**.
- Cuenta desde la "FECHA INICIO GARANTÍA" de la hoja resumen, no desde la fecha de contrato ni de pago.

## 4. Vigencia y efectos (cláusulas 3 y 4, hoja resumen)

- Cubre solo averías ocurridas **dentro** de FECHA INICIO y FECHA FIN de la hoja resumen. Fuera → **Sin Vigencia**.
- Comunicada después de la fecha fin, aunque haya ocurrido antes → exclusión 12.6.
- El contrato no tiene efectos hasta el pago total; la ficha trae la fecha de pago. Avería anterior al pago → no cubierta (cláusula 4).
- La vigencia puede empezar a computarse al terminar la garantía del fabricante (hoja resumen); por eso un vehículo "nuevo" puede tener fecha de inicio muy posterior a la compra.

## 5. Proceso y desmontaje (cláusula 10 leída junto con 12.1 y 12.2)

- El taller debe aportar: orden de entrada (fecha, km, descripción), **presupuesto hecho sin intervenir ni desmontar** (10.3.b), libro de mantenimiento si existe, y facturas de los mantenimientos con los datos de 10.3.d.
- **Nada de desmontaje, montaje ni reparación antes de la resolución** (10.4), salvo que GarantiPlus lo requiera para determinar el origen. Entonces el desmontaje lo autoriza GarantiPlus **y** el propietario del vehículo por escrito (en SIGA se ve como "SOLICITUD DE DESMONTAJE" firmada).
- **Un desmontaje solicitado por GarantiPlus no es la exclusión 12.1.** 12.1 y 12.2 aplican cuando el taller trabajó o movió el vehículo **por su cuenta** antes de la resolución. Si el Seguimiento muestra que el área pidió el desmontaje, no lo cuentes como falta al proceso.
- Si la avería no procede, el costo del desmontaje lo paga el cliente (10.5), y el diagnóstico tampoco se cubre (13.8).
- **Plazo de 72 horas (12.4)**: corre desde que el área **requiere** la documentación (busca en el Seguimiento la fecha y hora del mensaje "favor de compartir…"). Vencido sin respuesta → **Falta al proceso (Distribuidor)**. Antes de vencer, o si nadie la requirió, el caso es pendiente, no rechazo.
- GarantiPlus se obliga a resolver en 48 horas hábiles desde que recibe la documentación o desde el desmontaje (10.5). Un folio con días de espera sin resolver después de eso es un pendiente del área, no del taller.
- Vehículo inmovilizado hasta la resolución (10.4 / 12.2).

## 6. Componente y causa, por separado

Se evalúan los dos. **Pieza cubierta no implica causa cubierta.**

**Causas que excluyen (numeral 13) y su motivo de catálogo:**

| Causa documentada | Numeral | Motivo de catálogo |
| --- | --- | --- |
| Preexistente o previsible al contratar; evidente durante la garantía del fabricante | 13.1, 13.2 | Preexistente |
| Consecuencia de una mala reparación anterior | 13.3 | Mala Reparación Anterior |
| Fin de vida útil por uso natural; erosión, corrosión, deformación, piezas que perdieron su morfología | 13.4, 13.5 | Daño por uso o degradación |
| Consumibles, fugas de aceite/refrigerante/combustible, batería, frenos, correas, escapes, catalizador | 13.6 | Componente excluido (o Fuga excluida si es fuga) |
| Software, actualizaciones, programaciones | 13.7 | Componente No incluido en cobertura |
| Defecto de serie, vicio oculto, fallo epidémico, campaña del fabricante | 13.12 | Campaña y/o Fallo epidémico |
| Alteración o modificación de la especificación del fabricante; accesorios no de origen | 13.13, 13.24 | Influencia Externa |
| Siguió circulando con testigos de avería encendidos | 13.14 | Negligencia de uso |
| Mal uso, competiciones, sobrecarga, agentes abrasivos | 13.15–13.18 | Negligencia de uso |
| Accidente, robo, incendio, explosión, vandalismo, catástrofe natural | 13.19 | Siniestro |
| Combustibles o lubricantes no conformes o contaminados | 13.23 | Influencia Externa |

**Partidas que nunca se cubren aunque la avería proceda:** diagnóstico si la avería no procede (13.8), mantenimiento preventivo (13.10), controles y reglajes (13.11), piezas cambiadas sin haber fallado (13.20), intervenciones de asistencia en carretera (13.21), grúa y transporte (13.22, 13.25), estacionamiento (13.26), daños consecuenciales y lucro cesante (13.27, 13.28).

Cómo distinguir **falla súbita** (cubierta) de **desgaste** (13.4): la rotura imprevista deja evidencia (pieza fracturada, cortocircuito, pérdida repentina de función con lectura fuera de parámetro); el desgaste es progresivo y proporcional al kilometraje (superficies gastadas, material de fricción consumido, gomas deformadas, ruido que crecía). **Una "holgura" o "juego" por sí sola no es desgaste**: lo es cuando el taller la atribuye al uso ("vencido", "desgaste", "deformado", "por el uso") o cuando está en elementos de fricción o goma (pastas, bujes, bases, gomas) o en una caja de dirección con kilometraje alto (162130 con 74,000 km, 161932 con 77,000 km). Una holgura "fuera de especificación" en una pieza mecánica de una unidad reciente con mantenimiento al día se aceptó como avería (160579, S10 2023, eje de horquilla de cambios). Si el diagnóstico del taller solo dice "falla" sin pruebas, pide la evidencia del punto 7.

Lo que el área ha tratado como **desgaste o causa excluida**, aunque el taller lo llame "falla" (resoluciones reales; ilustran la lectura, no la sustituyen):
- Polea o balero (rodamiento) agarrotado, de alternador, tensor o compresor: pérdida progresiva de lubricación y pistas, no rotura súbita (162922 → Daño por uso o degradación). La banda que se rompe por eso es consumible (13.6).
- Quemacocos con cable roto cuando el fabricante tiene boletín técnico sobre esa falla: el área lo trató como desgaste progresivo más Campaña y/o Fallo epidémico (162262). **No generalizar a otros mecanismos**: un regulador o elevador de cristal con cable dañado se aceptó como avería cubierta (160678); un actuador de seguro de puerta también (160711).
- Fuga de refrigerante por bomba de agua, fuga de aceite por cárter, sellos o juntas: pérdida de hermeticidad, no rotura interna (164276 → Fuga excluida).
- Historial de mantenimiento con huecos grandes antes de contratar (dos años o 27,000 km sin servicio): el área lo usó como señal de condición preexistente aunque el contrato fuera reciente (157279).
- Compresor de A/C que **hace ruido pero sigue funcionando**: el área lo lee como desprendimiento gradual de partículas de desgaste (rebabas) y holgura entre piezas móviles, no como rotura imprevista; "incumple la definición de AVERÍA" y se rechaza citando la cláusula 1 (165728, Onix 2023 con 83,000 km, 05/10/2026). La avería exige **inutilidad operativa**, no solo un síntoma.

Lo que el área ha tratado como **falla cubierta**: módulo o actuador electrónico que deja de comunicar o de responder (palanca de cambios 163549 y 160579, cluster 162592, actuador IBR 162328, sensor radar 162526, amplificador 162559, inyectores 165694, actuador de árbol de levas 161833, motor de unidad climatizadora 161305, switch de ignición 159721), mecanismos eléctricos de puerta o ventana que dejan de funcionar (regulador de cristal 160678, actuador de seguro 160711) y columna de dirección con falla eléctrica (160612), válvula solenoide de purga EVAP con circuito abierto confirmado por código y medición (P0444, bobina fuera de 10-30 Ω; 167410, aceptada el 28/09/2026 por $5,076.44), con código de falla o prueba física que confirme la falla. **Cuando la pieza falla de golpe y no hay fuga, holgura ni desgaste visible, es avería cubierta aunque el expediente sea delgado.**

**SIGA tiene su propio filtro de componentes.** En el menú Averías, "Refacciones prods. amplia" (`/Averias/RefaccionesNoPermitidas`) lista las refacciones **no cubiertas** por producto de cobertura amplia y "Refacciones prods. limitada" (`/Averias/RefaccionesPermitidas`) las **cubiertas** por producto de cobertura limitada. Con eso SIGA intenta un rechazo automático al registrar la avería y lo deja escrito en "Logs de resolución de averías" de la pantalla Details. Sirve como cruce rápido de "componente cubierto"; **no sustituye al certificado**, que es la primera fuente de verdad.

## 7. Evidencia mínima según el tipo de falla (qué pedir si falta)

| Tipo de falla | Lo que debe haber en el expediente | Si falta, pedir al taller |
| --- | --- | --- |
| Mecánica interna (motor, transmisión, dirección, diferencial) | Síntoma descrito, pruebas previas sin desmontar, carta de diagnóstico con causa, fotos identificables de la pieza y del vehículo (VIN), y autorización escrita si hubo desmontaje | Carta de diagnóstico con causa y pruebas; fotos de la pieza montada; evidencia del desmontaje autorizado |
| Eléctrica / electrónica (alternador, módulos, sensores, bombas eléctricas) | Reporte de diagnóstico con códigos **y** su contexto, pruebas de alimentación y señal según procedimiento del fabricante, componente identificado y su relación con el síntoma. **Un código de falla aislado no prueba ni la pieza ni la causa** | Procedimiento de prueba del fabricante seguido, lecturas (voltaje, resistencia) y foto del componente |
| Transmisión o dirección en productos con periodo de espera | Tipo exacto del sistema (DSG/CVT/electroasistida o no), fecha de inicio de vigencia, fecha de aparición y de comunicación, pruebas que distingan falla súbita de degradación | Ficha técnica del sistema; historial del síntoma |
| Fugas, desgaste, sobretemperatura | Origen de la fuga o del calentamiento, secuencia del daño (qué falló primero), mantenimiento al día, testigos del tablero, evidencia que separe causa primaria de daño consecuente | Fotos del origen; lectura de niveles; historial de testigos |

Siempre, para cualquier tipo: foto del **odómetro o tablero con km**, foto del **VIN**, **presupuesto** desglosado, **orden de ingreso**, y **carnet o facturas de mantenimiento**. Sin odómetro no hay km de avería y el Informe no se puede generar (el veredicto sí).

## 8. Alertas de integridad (motivos de comprobación, no de rechazo automático)

Si ves alguna, va en una viñeta del veredicto con su fuente y, si cambia el resultado, el caso queda 🟡 pendiente hasta aclararla con el técnico o el taller; nunca se resuelve eligiendo un valor en silencio:

- VIN distinto entre certificado, SIGA, foto del parabrisas, facturas u orden de ingreso.
- Kilometraje que **baja** entre documentos, o km de avería menor que el km al contratar (12.5 → Falta de relación en kms, y es causa de rescisión).
- Fechas imposibles (servicio posterior a la avería; factura anterior a la compra).
- Presupuesto duplicado, o presupuesto cuyo concepto no coincide con el diagnóstico (ej. mano de obra rotulada para otra pieza).
- Factura de mantenimiento sin RFC, sin placas o sin km (10.3.d).
- Fotos o videos que no se pueden vincular al vehículo (sin VIN ni placa visible).
- Trabajos o desmontaje anteriores a cualquier autorización en el Seguimiento.
- Entrada al taller muchos días antes del registro en SIGA (10.1 pide comunicar "en cuanto tenga conocimiento"); se menciona, no excluye por sí sola.
- Certificado cuyo contrato, producto o VIN no coinciden con la ficha de SIGA (no es el certificado de esta avería).

## 9. Valoración (cuando procede)

- Tres cifras distintas, nunca mezclarlas: **presupuesto del taller** (lo que pide), **valoración** (lo que Claude propone autorizar, partida por partida) y **monto autorizado** (lo que el técnico confirma, va al Informe y se marca en los renglones de SIGA; las tres salidas con la misma cifra).
- Los importes de los presupuestos **ya incluyen IVA** en todas las cuentas (regla del área). No se pide ni se calcula IVA.
- Partida por partida: refacción, mano de obra (horas × tarifa del taller), diversos. Cada una se autoriza o no; las no autorizadas se dicen en el veredicto con su numeral (13.8, 13.20, etc.) y se rechazan en los renglones de SIGA, pero **no se escriben en el Informe**: el Informe procedente solo lleva lo autorizado (regla del área, 08/10/2026).
- **Límites** (cláusula 11 y hoja resumen): la valoración nunca supera el valor de venta del vehículo (libro azul). Si el presupuesto se acerca al valor del vehículo, menciónalo y deja que el técnico decida; es raro.
- **No hay deducible** en los contratos GarantiPlus leídos hasta ahora. Si un certificado lo menciona, aplícalo como diga.
- Si el presupuesto del taller supera lo autorizado, el cliente elige entre reparar en el taller que indique GarantiPlus o pagar la diferencia (10.11); eso se lo explica el técnico al taller, no va en el veredicto.

## 10. Lecturas difíciles del condicionado (cómo se resuelven aquí)

| Tensión | Lectura que se adopta | Cuándo preguntar al técnico |
| --- | --- | --- |
| 10.4/10.5 permiten un desmontaje requerido por GarantiPlus; 12.1 excluye trabajos antes de la resolución | Desmontaje pedido por el área y autorizado por el propietario = parte del proceso, no exclusión. Trabajo por cuenta del taller sin pedirlo = 12.1 | Si el Seguimiento no deja claro quién pidió el desmontaje |
| La lista de la cláusula 1 excluye la carga de a/a "salvo que sea necesaria por avería cubierta"; 13.6 la excluye sin salvedad | Si la avería del A/C procede, la carga necesaria para repararla se autoriza como diverso; si no procede, no | Siempre que la carga sea una partida relevante del presupuesto |
| La hoja resumen remite a la "cláusula 7" para mantenimientos; el detalle está en la 9 | Citar la 9 (y 12.3) como fundamento; la 7 solo enumera obligaciones generales | No hace falta |
| Dos domicilios: el del encabezado del contrato y el de 10.9 para la factura | Para el comentario de pago, usar el domicilio fiscal de la plantilla del área que confirme el técnico | Antes de publicar un comentario de pago con domicilio |
| 12.7 ("cualquier incumplimiento") es muy amplia | No se usa sola como causal; siempre acompañada de la cláusula concreta incumplida | Nunca rechazar solo con 12.7 |

## 11. Después de aceptar: lo que sigue para el taller

Observado en el caso 165694 (Aceptada → Taller). Tras marcar "Procede garantía", el técnico publica en Observaciones ("Enviar") el comentario con los pasos para el pago (plantilla literal en `01-mecanica-siga.md`):

1. Cargar en SIGA el **finiquito firmado** por el beneficiario (copia firmada del Informe de Resolución, 10.8), **identificación oficial**, **datos bancarios** del taller, **Constancia de Situación Fiscal** y **Opinión de Cumplimiento positiva**.
2. Seleccionar "Vehículo en Taller" → "Aceptar" para habilitar la carga de la **factura PDF y XML**, a nombre de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., por el monto autorizado (nunca mayor, 10.8), con el domicilio fiscal vigente (10.9; el de la plantilla, confirmado por el técnico).
3. "Enviar" para que el área de pagos la vea. Pago en 15 días desde la recepción de la factura (10.10).

Los datos bancarios y fiscales concretos del taller no se escriben en el chat ni en la bitácora.

## 12. Preguntas tipo al técnico cuando el caso queda pendiente o se argumenta

Una sola, la que destrabe el caso:

- ¿Hay un contrato o anexo distinto al certificado que leí para este producto?
- ¿Cuál es el kilometraje de avería y en qué documento está?
- ¿Cuándo apareció la falla y cuándo se comunicó? (si hay lapso largo entre ingreso y registro)
- ¿Con qué prueba se distingue esta falla de desgaste?
- ¿Quién pidió el desmontaje y cuándo se autorizó?
- ¿Se requirieron los comprobantes de mantenimiento al taller y en qué fecha?
- ¿Alguna partida del presupuesto queda fuera por criterio del área?
- ¿Hay una excepción comercial (ATC)? ¿Quién la autorizó y con qué alcance?
- Dos fuentes dan valores distintos de {dato}: ¿cuál prevalece?
