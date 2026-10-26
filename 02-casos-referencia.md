# Casos de referencia — cómo se ve un cierre real en SIGA

Transcripciones reales del Seguimiento (ambiente de pruebas, copia de producción, y producción) y escenarios operativos. Sirven para reconocer el patrón de un rechazo, de una aceptación, de un pendiente y de las acciones administrativas.

**Cómo usar estos casos.** Son material de entrenamiento, no una jerarquía de decisión: muestran cómo se ve un cierre y cómo razonó el área en un expediente concreto. Ninguno sustituye al certificado de la avería que se está revisando, y una decisión excepcional (una aceptación por atención comercial, un rechazo donde cabían dos causales) no se convierte en regla para el siguiente folio. Los criterios que el área sí fijó como regla están en `03-criterios-dictamen.md` y en las instrucciones; aquí solo se citan como ejemplo.

## 167773 — Rechazado (`No procede garantía`)

Producto EXCELLENCE CARSHOP M2 VD, Chevrolet Cavalier 2023, contrato 674076, 88,742 km al contratar, garantía de fábrica: no (seminuevo → regla de mantenimiento de 6 meses / 10,000 km, cláusula 9). Presupuesto $22,658.40 (compresor de A/C). Su cláusula 1 trae la lista de componentes excluidos de los productos M2 (el compresor no está en ella).

**Secuencia:**
1. `19/09/2026 12:41:49` Registrada → Registrada — "Registro de avería por taller externo" (asesor del taller).
2. `19/09/2026 12:41:49` — Asignación del técnico (SIGA).
3. `19/09/2026 13:00:34` — "Solicitud de validación" (taller).
4. `20/09/2026 20:09:26` Validación → Validación — el técnico pide: foto de VIN, historial de mantenimientos, carta de diagnóstico con síntoma y pruebas realizadas, imágenes a detalle del componente reclamado.
5. Sin respuesta del taller.
6. Documento tipo **Resolución** subido: `RESOLUCIÓN 167773 - RECHAZADA.docx`, `24/09/2026 17:38:06`.
7. `24/09/2026 17:41:05` Validación → **No procede garantía** — sin observación adicional, usuario de la cuenta del área (`averias@…`).

**Estado final de los renglones:** refacción "Compresor de A/C" → `Rechazada`; servicio "DIAGNÓSTICO" → `Rechazada`. La causa capturada quedó visible bajo "Síntomas de la avería": *"Falta de documentación y evidencia técnica solicitada dentro del plazo de 72 horas para acreditar la falla y la procedencia de la cobertura."*

**Después de cerrado:** título "Visualización de avería"; único botón "Reabrir avería".

**Patrón que enseña:** rechazo documental (el taller no entregó lo solicitado en el plazo de 72 h de 12.4, contadas desde la solicitud del 20/09 20:09). Motivo de catálogo coherente: *Falta al proceso o incompleto (Distribuidor)*. Es "no acreditó", no "no cumplió". El Informe se subió **tres minutos antes** de marcar "No procede garantía": primero el documento, luego el dictamen. La causa del renglón se capturó en texto libre; **desde el 26/10/2026 ésa es la regla**: cada refacción lleva su porqué en texto libre (`causas`) y el motivo del catálogo va en el dictamen.

## 165694 — Aceptado (`Aceptada` → `Taller`)

Producto EXCELLENCE VANGUARDIA M1, Honda CR-V 2024, contrato 492445, 29,291 km al contratar, vigencia desde 31/08/2026 (al terminar la garantía amplia Honda de 3 años), garantía de fábrica: sí. Presupuesto $30,437.01 (kit de inyectores $17,223.80 + mano de obra 10 h $9,015.00 + IVA $4,198.21 desglosado en la prefactura). Km de avería 44,476 (orden de atención; sin foto de odómetro). Cuatro servicios Honda dentro de 12,000 km / 12 meses, sellados en el carnet. Su cláusula 1 trae lista de exclusiones e incisos sobre la garantía del fabricante. Revisado con el proyecto el 06/10/2026: Opus y Sonnet dieron "procede" por $30,437.01, igual que la resolución real.

**Secuencia (resumen):**
1. El taller sube presupuesto, evidencia y varios (contrato, histórico de garantías, encuesta de falla, hoja de diagnóstico) el `10/09/2026` entre `17:01` y `17:28`.
2. `11/09/2026 12:24:42` — nota de que un video se envió por WhatsApp "ya que el portal no deja subir video".
3. Documento tipo **Resolución** subido: `RESOLUCIÓN 165694.pdf`, `11/09/2026 18:38:58`, por el técnico asignado con su propia sesión.
4. `11/09/2026 18:39:12` Validación → Validación — "Se notifica al taller la validación de sus datos fiscales y bancarios" (SIGA).
5. `11/09/2026 18:39:12` Validación → **Aceptada** (sin observación), técnico asignado.
6. `11/09/2026 18:39:36` Aceptada → Aceptada — mensaje plantilla del técnico con los siguientes pasos para el taller: cargar finiquito firmado, identificación oficial, datos bancarios, Constancia de Situación Fiscal y Opinión de Cumplimiento positiva; después seleccionar "Vehículo en Taller" → "Aceptar" para habilitar la carga de factura PDF/XML, y "Enviar" para que el área de pagos la vea.
7. `19/09/2026 13:44:42` Taller → Taller — "Entrada a taller" (taller).

**Estado final de los renglones:** refacción "Inyectores" → `Aceptada`, con "Precios aceptados" mostrados junto a los del taller.

**Patrón que enseña:** en una aceptación, el Informe se sube primero, el dictamen cambia el estatus a Aceptada, y de inmediato se publica en Observaciones ("Enviar") un comentario con los pasos para el pago. El comentario final es parte del cierre. El monto del Informe, el de los renglones aceptados y el del Seguimiento son el mismo.

## 167938 — Cancelación de prueba

Folio en estatus `Registrada`, con presupuesto $6,261.03 (bujías). Se usó "Cancelar avería" para confirmar el formato:

- Motivo capturado: *"Prueba de exploración del flujo de cierre de averías (entorno de pruebas) — avería registrada sin evidencia ni presupuesto, se cancela para validar el flujo administrativo."*
- Entrada resultante (`01/10/2026 16:11:40`, Registrada → **Cancelada**):
  > `Cancelación de avería por el usuario averias@garantiplus.mx razón: {motivo}`
- Después: "Visualización de avería", único botón "Reabrir avería".

## 167971 — Cierre administrativo de prueba

Folio en estatus `Registrada`, sin presupuesto. Se usó "Cerrar avería" sin factura para confirmar el formato:

- Motivo capturado: *"Prueba de exploración del flujo de cierre de averías (entorno de pruebas) — cierre administrativo sin factura adjunta, para documentar el flujo."*
- Entrada resultante (`01/10/2026 16:13:07`, Registrada → **Cerrada**):
  > `Cierre de avería por el usuario averias@garantiplus.mx razón: {motivo}`
- Después: mismo patrón, "Visualización de avería" y solo "Reabrir avería".

## 167410 — Válvula EVAP, Cavalier 2021 (M2 24): mismo folio, dos ambientes

Producto EXCELLENCE SEDANES GM M2 24, contrato 589833, km inicial 36,821, vigencia 09/10/2025–08/10/2027. Presupuesto: refacción "Válvula EVAP" + servicio "Diagnóstico" ($5,076.44 con IVA). Carta de diagnóstico GM (P0444, bobina del solenoide fuera de 10-30 Ω) y foto del escáner con el VIN.

**Producción:** el taller subió 10 prefacturas de servicio (reimpresiones del distribuidor, 2022-2026) el 26/09 y el área **aceptó** el 28/09 por $5,076.44. Con esas facturas, los tramos desde el inicio del contrato (05/09/2025 36,821 km → 12/03/2026 43,253 km → 28/08/2026 49,297 km → avería 18/09/2026) cumplen 6 meses / 10,000 km.

**Pruebas (copia del 19/09):** sin facturas, con dos requerimientos sin respuesta (18/09 y 28/09) → rechazo documental por 12.4, motivo *Falta al proceso o incompleto (Distribuidor)*. Se generó con el conector el Informe improcedente (`numerales: ["12.4"]` + cláusula 9 completa en `clausulasLiterales`, sin `desarrollo`; 3 páginas) como `RESOLUCIÓN 167410.pdf`. El 🗑 del servicio DIAGNÓSTICO no respondió desde el navegador integrado (diálogo nativo) y el panel "Resolución" siguió oculto; quedó para el técnico.

**Patrón que enseña:** el conector y la pantalla pueden traer documentos distintos para el mismo folio cuando están en ambientes distintos; por eso ambos tienen que apuntar al mismo ambiente y el veredicto se razona con el expediente que de verdad hay en ese ambiente. También muestra la diferencia entre la causa de texto libre por renglón y el motivo de catálogo literal: **son dos parámetros distintos y desde el 26/10/2026 van los dos** (`causas` y `motivo`).

## 164143 — Rechazo por intervalos de mantenimiento (resolución real del equipo)

Producto EXCELLENCE SUV GM M1 36, Chevrolet Express Max cargo van 2025, contrato 605704, km al contratar 0, vigencia 17/07/2026–16/07/2029. Presupuesto $12,516.86 (generador $11,834.78 + mano de obra 1.4 h $682.08). Expediente con 4 videos (VIN en parabrisas y lecturas de multímetro 11.9 V), facturas de mantenimiento, cartas, orden de ingreso y póliza.

Resolución real subida el 05/09/2026 (`RESOLUCION AVERIA 164143.pdf`): **no procede**, "el historial de servicios muestra 3 servicios con intervalo excedido por kilometraje" contra el intervalo del fabricante de 12 meses o 12,000 km, con fundamento en 12.3 y 9. Encabezado con KM Avería 66,745 (coincide en la foto del tablero de FOTOS.pdf, la orden de ingreso y el presupuesto). Después se subió una "SOLICITUD DE DESMONTAJE" (21/09/2026), en pruebas se reabrió el 21/09 (`No procede garantía → Validación · Avería restablecida en validación por averias@garantiplus.mx`, conservando renglón y documentos) y el folio seguía en Validación al 05/10/2026.

**Patrón que enseña:** una tabla de intervalos (fecha, km, días, recorrido entre servicios) basta como evidencia; el km de avería se confirma cruzando la foto del tablero con la orden de ingreso y el presupuesto; un folio con Resolución previa puede seguir abierto por una solicitud de desmontaje. El expediente no trae el plan del fabricante; el equipo aplicó 12,000 km / 12 meses medidos desde el servicio anterior, mientras que las facturas del distribuidor rotulan los servicios como 5 / 20 / 40 / 60 mil. Es el caso que mostró que el intervalo por omisión debe ser un criterio del área, no un supuesto de cada revisión.

## 171469 — Primer rechazo en producción con el copiloto (06/10/2026)

Aveo 2020, EXCELLENCE SEDANES GM M2 12, transmisión. Rechazo por intervalo de mantenimiento excedido en tiempo (245 días desde el inicio del contrato sin servicio; regla de 6 meses / 10,000 km). Lo que dejó la prueba:

- La causa de rechazo del renglón se capturó en texto libre y quedó impresa en "Síntomas de la avería". En octubre el área la quería igual al motivo del catálogo (`Intervalo de Mantenimiento Excedido`); **el 26/10/2026 se decidió lo contrario**: cada refacción lleva su porqué en texto libre, y el motivo del catálogo va sólo en el dictamen. No se puede corregir después, por eso se confirma en la tabla de parámetros antes de ejecutar.
- Comentario estándar de rechazo publicado con "Enviar": *"Hola, excelente día. Compartimos resolución del expediente y se explica en el archivo adjunto como resolución."*
- El Informe del conector salió con datos de pago en un rechazo; el técnico lo rehízo a mano (`RESOLUCIÓN 171469.pdf`). La receta correcta está en `05-redaccion-informes.md`.
- Con el usuario de dirección la pantalla abrió en solo lectura: solo el técnico asignado o la cuenta del área operan la avería.
- Details mostró "Logs de resolución de averías" con el intento de rechazo automático de SIGA (165 refacciones no permitidas para el producto; no todas las del presupuesto caían ahí → resolución manual).

## 165728 — Compresor de A/C, Onix 2023 (CARSHOP M2 VD)

Rechazada en producción el 05/10/2026: la evidencia mostraba ruido del compresor sin pérdida de funcionalidad; el área lo trató como desgaste gradual (rebabas, holgura) y citó la definición de AVERÍA/AS de la cláusula 1. Sin carta de diagnóstico en el expediente; el historial de mantenimiento pedido el 21/09 nunca llegó. En pruebas se usó solo como caso de **mecánica** de aceptación (renglón ✓, Informe procedente con IVA desglosado, "Procede garantía"), no como criterio: el ✓ de la refacción no respondió desde el navegador integrado (`aceptaRefaccion` valida montos y pide confirmación nativa).

## 167311 — Bomba de dirección electrohidráulica, Oroch 2024 (FARRERA EXCELLENCE M2)

Carta de diagnóstico del taller: la bomba recibe 12 V y señales, no genera presión por daño electrónico interno. Contrato sin lista de exclusiones ni periodo de espera para dirección (la cláusula 1 termina en el punto 9). 175 días y 2,429 km desde el inicio del contrato: no había servicio vencido. El área pidió el 18/09 pruebas eléctricas adicionales (DTC, activación, voltajes, amperaje, fluido) y el historial; sin respuesta. Caso tipo de **pendiente con mensaje al taller**: en pruebas se publicó un comentario con "Enviar" (`06/10/2026 15:24:36`) y una nota con "Uso Interno" (`15:25:45`); las dos aparecen iguales en el Seguimiento.

## 177442 y 177608 — Primer cierre en producción con el flujo del conector (23/10/2026)

**177442 — Rechazado.** AUDI A1 TFSI 2026 · contrato 797015 (NISSAN RENOVACION CALL CENTER) · componente: unidad de control de red de a bordo -J519, cargada por el taller como «UCH UNIDAD DE CONTROL DEL HABITÁCULO» (renglón 228367). La cláusula 1 lista literalmente los 7 componentes cubiertos y excluye los elementos internos del habitáculo; el protocolo midió 13.81 V («OK») y el DTC fue esporádico. Informe `RESOLUCIÓN 177442.pdf` (versión 9a6168f2, documentId 587257) subido con `subir_resolucion`; `rechazar_averia` con motivo «Componente No incluido en cobertura», sin `causas` (anterior a la regla del 26/10), plantilla de rechazo con «Enviar»; verificación todo OK; `Validación → No procede garantía` 16:23:18. **Patrón que enseña:** el nombre con que el taller carga el renglón («habitáculo») puede reforzar la exclusión; la ficha marcaba el contrato Cancelado un día después del registro de la avería y no cambió nada porque la vigencia cubría la fecha de avería.

**177608 — Aceptado (llantas GarantiPlus).** HONDA HR-V 2027 · contrato 827309 (LLANTAS 8000) · llanta 225/55R18 con desgarre pasante en el flanco, DOT idéntico a las cuatro garantizadas, 228 km. La cláusula 3.1 excluye «los costos de colocación de las llantas de recambio»; **el técnico decidió incluir la mano de obra** ($734.48) «para evitar problemas» con el taller (fuente `Técnico`, 23/10/2026; decisión de ese folio, no regla: regla 15). Hubo tres versiones del Informe; se subió la tercera (1041ca7b, documentId 587295) con llanta $3,139.40 + M.O. $734.48 + IVA $619.82 = $4,493.70. `aprobar_averia` con `renglones: [{id: 228602, aceptar, cantidad 1, mo 734.48, precio 3139.40}]`, ATC No, plantilla de aceptación; verificación todo OK; `Validación → Aceptada` 16:45:43; SIGA añadió por su cuenta «Se notifica al taller la validación de sus datos fiscales y bancarios». **Patrones que enseña:** (1) los renglones de SIGA llevan los montos sin IVA cuando el presupuesto lo desglosa, y el Informe lleva el total con IVA: renglones + IVA = total; (2) la plantilla de procedente imprime «por un importe de hasta $8,000.00» (límite por llanta del certificado), y el importe real va en la tabla de valoración; (3) con la prompt v3 este cierre tomó seis mensajes del técnico (dos confirmaciones: subir y dictaminar); v4 lo deja en tres.

## Nota sobre numerales que el conector no encuentra

En el folio 169027 el conector rechazó el numeral "3.15" porque el condicionado de ese certificado no lo trae con ese nombre. Se resolvió mandando la cláusula en `clausulasLiterales` con su numeral, título ("SE EXCLUYEN DE MANERA EXPRESA") y texto exacto leído del certificado. Nunca se inventa ni se parafrasea el texto de una cláusula, y nunca se toma de otro contrato.

## Escenarios operativos (qué debe pasar en cada situación)

Escenarios de comportamiento, no de cobertura. Sirven para reconocer la situación y actuar igual cada vez.

**A. Expediente incompleto.** Falta un documento necesario. Resultado: 🟡 pendiente, no rechazo. El comentario al taller enumera los faltantes (uno por línea, con la fecha en que ya se pidieron si aplica), se publica una sola vez con "Enviar", y el folio sigue en Validación. Solo si el contrato fija plazo (72 h en la mayoría), el área lo requirió y venció sin respuesta, el caso pasa a rechazo documental. Nunca se decide "automáticamente" por el paso del tiempo sin que el técnico lo confirme.

**B. Resolución favorable.** Todas las partidas con decisión y monto; el Informe generado, aprobado por versión y subido con el conector; el archivo visto en SIGA (`renglones_averia` o la página recargada); el cierre ensayado con `aprobar_averia`, enseñado al técnico y confirmado con su "Sí" y el `plan`; la verificación del conector leída entera (renglones, comentario y estatus en `OK`). El monto del Informe, el de los renglones aceptados y el que se confirma en el resumen de cierre son el mismo.

**C. Pruebas y producción.** El mismo folio existe en los dos ambientes con documentos y estatus distintos. El `entorno` se manda igual en todas las llamadas de la conversación y, si se mira la avería en el navegador integrado, el host de esa pestaña debe coincidir con el del conector ("Ver en SIGA"); el ambiente se anota en la bitácora de cierre. Nada hecho en pruebas modifica producción.

**D. Latencia y reintento.** Una acción no se repite: el conector la ejecuta una vez, relee y reporta, y rechaza un plan ya ejecutado. Si la verificación trae `ERROR` o `NO VERIFICADO`, lo revisa el técnico en SIGA. Dos entradas iguales en el Seguimiento no se "corrigen": se anotan.

**E. Versión incorrecta.** Puede haber varias versiones del Informe en la bandeja. La que se sube es la que `subir_resolucion` nombra en su llamada sin `confirmar` y que el técnico aprobó viéndola abierta en el navegador. Si después de aprobar se cambia cualquier dato, hay nueva versión y nueva aprobación. SIGA no borra documentos: una versión mal subida se queda.

**F. Permisos y asignación.** El conector opera con la cuenta del área, así que puede editar cualquier avería en Validación; si está asignada a otro técnico, el ensayo lo avisa y el técnico decide. Si `renglones_averia` o el ensayo dicen "NO editable", es estatus terminal o la sesión del servidor no tiene permiso: no se intenta nada y se avisa.
