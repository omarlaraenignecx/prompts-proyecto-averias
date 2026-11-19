# Documentos de pago de averías procedentes

**Versión de este recurso: 2026-11-19 (v5.0).** Acompaña a la sección 8 de las instrucciones. Sale de tres fuentes revisadas el 19/11/2026: 80 documentos de pago de 16 averías reales (11 nacionales, 5 de Bridgestone), 130 hilos de correo a contabilidad de julio a noviembre de 2026 y la bitácora de SIGA. Los umbrales son los del conector; lo que está «pendiente con el área» se dice.

## 1. El proceso, de punta a punta

1. La avería se **acepta** (estatus Aceptada). El técnico comenta al taller qué debe subir.
2. El taller sube los documentos, marca «Vehículo en Taller» (estatus **Taller**) y carga la **factura** en PDF y XML en «Registro de factura(s)»; al marcar «auto reparado» queda **Solucionada**. No siempre lo hacen en ese orden: hay averías con todo cargado que siguen en Aceptada o en Taller.
3. El técnico revisa y manda el paquete por correo a contabilidad (con el conector: `enviar_a_pagos`).
4. Contabilidad paga y contesta en el mismo hilo con el comprobante, un PDF llamado `GPMX AVERIA <folio>.pdf`. Tarda 1 día en la mediana; el 90 % llega en 3.
5. El comprobante se sube a la avería (tipo «Comprobante de pago») y se avisa al taller para que marque «factura liquidada», lo que la deja **Cerrada**. Si la factura fue PPD, el taller sube además el complemento de pago.

Muchas averías pagadas se quedan años en Taller o Solucionada porque el taller no da el último paso: por eso «por pagar» se define por la **ausencia de comprobante**, no por el estatus.

## 2. Qué documentos son

### Nacional (GarantiPLUS MX, BMW, Motornation)

| Documento | Cómo viene en la práctica | Qué se revisa |
|---|---|---|
| **Factura (CFDI)** en PDF y XML | En «Registro de factura(s)», no en Documentos. A veces el taller sube además el PDF como «Taller» | Total = importe aprobado con IVA (se toleran ±$0.02; lo normal es exacto o ±$0.01). Receptor GARANTIPLUS MEXICO, RFC GME160927DW0. Método de pago |
| **Opinión de cumplimiento** (32-D) | PDF del SAT con texto, 1 página | Sentido **POSITIVO** y fecha de emisión |
| **Constancia de situación fiscal** | PDF del SAT con texto, 3 páginas | «Estatus en el padrón: ACTIVO» y fecha de emisión |
| **Datos bancarios** | Carátula o primera página del estado de cuenta (lo más común, casi siempre imagen); u hoja membretada del taller con varias cuentas | Titular = emisor de la factura; CLABE legible |
| **Finiquito** | La «Carta recepción del vehículo», última página de la Resolución, firmada. Suele venir pegada a la Resolución y a tres infografías de GarantiPLUS (ignóralas) | Ver §3 |
| **Identificación del cliente** | INE por ambos lados; archivo aparte o **dentro del PDF del finiquito** | Ambos lados, vigente, mismo nombre del finiquito |
| Prefactura | Reporte del sistema del taller. Opcional | No se manda a contabilidad |

### Internacional (Bridgestone: talleres de Colombia, Costa Rica, Ecuador; pago en USD)

Finiquito, identificación del cliente (cédula), y los **datos bancarios del beneficiario: titular, número de cuenta, código SWIFT/ABA/IBAN y dirección del banco** (tesorería pide los cuatro; el SWIFT suele venir en una nota aparte y se acepta así). **No hay** constancia, opinión ni XML. La factura local a GARANTIPLUS MEXICO suele llegar **después** del pago: su ausencia no impide enviarlo, pero hay que pedirla. El importe de SIGA mezcla monedas y **no se usa**: el monto y la moneda los dicta el técnico, de la Resolución.

## 3. El checklist, regla por regla

| Regla | Quién la evalúa | OK | AVISO | REVISAR |
|---|---|---|---|---|
| La avería procedió | conector | Aceptada, con Resolución e importe aprobado | Hubo «Ajuste de importe autorizado» después (dice de cuánto a cuánto) | Falta la Resolución o el importe es cero |
| Factura = importe aprobado | conector (XML) | Igual, o diferencia de hasta $0.02 (se enseña) | — | Diferencia mayor |
| Facturada a GarantiPLUS | conector (XML) | Receptor GME160927DW0 | — | Otro receptor |
| Método de pago | conector (XML) | PUE del mes en curso | PPD (hará falta el complemento) | **PUE de un mes anterior**: contabilidad pide refacturar |
| Opinión de cumplimiento | conector si tiene texto | Positiva, de 30 días o menos | 31 a 90 días | Más de 90 días, o no positiva |
| Constancia de situación fiscal | conector si tiene texto | ACTIVO, de 90 días o menos | Más de 90 días | Padrón no activo |
| Mismo RFC en factura, constancia y opinión | conector | Coinciden | — | Alguno distinto |
| Cuenta bancaria a nombre del emisor | **tú** | — | Hoja con varias cuentas: contabilidad tendrá que elegir | Titular o RFC distinto del emisor (el conector lo marca solo si la carátula traía texto con otro RFC) |
| Finiquito firmado | **tú** | — | — | — |
| Identificación del cliente | **tú** | — | — | — |

Si falta el documento, la regla sale **FALTA**. Si el documento es una imagen y la regla necesitaba leerlo, sale **NO SE PUDO LEER** y la lees tú.

**Lo que miras en el finiquito:** el «N.º Avería» impreso es el de esta avería (se ha visto el número de contrato en su lugar); hay nombre y firma (no en blanco; el nombre es un nombre, no un número de cédula); la fecha es posterior a la Resolución; el VIN es el del expediente. Firmas que se dan por buenas: rúbrica, nombre manuscrito, iniciales, trazo digital. **Alerta:** la misma imagen de firma pegada en finiquitos de averías distintas. En un PDF digital la firma no aparece en el texto: pídelo en imagen antes de decir que falta.

**Lo que miras en la identificación:** ambos lados, vigencia (el año va en el frente) y que el nombre sea el que firma el finiquito.

**Pendiente de confirmar con el área** (dilo si el técnico pregunta por qué una opinión de 40 días sale en AVISO): los plazos de la opinión y la constancia (David pidió «no más de 3 meses»; la plantilla del área dice «positiva del mes en curso»; en la práctica se ha pagado con más de 100 días y también sin opinión), y la regla PUE/PPD (la plantilla del técnico pide PPD; la infografía, PUE hasta el día 25 y PPD después).

## 4. Cómo reconocer cada documento

**El tipo que el taller eligió en SIGA no es confiable**: en la muestra, 22 de 80 documentos estaban en la casilla equivocada (una INE como «opinion_cumplimiento», una Resolución como «opinion_cumplimiento», una cédula como «constancia_situacion_fiscal», constancias y opiniones como «Taller» o «Varios»). El conector clasifica por contenido cuando hay texto y te dice «supuesta» cuando no lo hubo: entonces confírmalo tú.

| Documento | Lo que trae |
|---|---|
| Constancia | «CÉDULA DE IDENTIFICACIÓN FISCAL», «CONSTANCIA DE SITUACIÓN FISCAL», «idCIF», «Lugar y Fecha de Emisión … A dd DE mes DE aaaa», «Estatus en el padrón: ACTIVO» |
| Opinión | «Opinión del cumplimiento de obligaciones fiscales», «Sentido … POSITIVO», «Fecha y hora de emisión». El formato viejo dice «Revisión practicada el día…» |
| Carátula bancaria | «Estado de Cuenta», «No. Cuenta CLABE», «R.F.C», «Periodo DEL … AL …». **Ojo:** el «ESTADO DE CUENTA» del sistema del taller (con «NO.ORDEN», «CLIENTE A FACTURAR») es una prefactura, no un documento del banco |
| Hoja de cuentas del taller | «DEPOSITAR A NOMBRE DE», tabla de bancos con varias CLABE, membrete de la marca |
| Finiquito | «CARTA RECEPCIÓN DEL VEHÍCULO», «en mi carácter de titular del contrato», «- Nombre y Firma -» |
| INE | «INSTITUTO NACIONAL ELECTORAL / CREDENCIAL PARA VOTAR»; al reverso, la línea `IDMEX…` |
| Factura en PDF | «representación impresa de un CFDI», «Folio fiscal», «Método de pago» |
| Complemento de pago | «Uso de CFDI: CP01», «Saldo Insoluto» |
| Comprobante de pago | «BBVA Net Cash», «Operación autorizada», «Motivo de pago: AVERIA <folio>» (este folio viene mal a veces: no te fíes) |
| Certificación bancaria (Colombia) | «BANCOLOMBIA S.A. se permite informar que … identificado(a) con NIT» |
| Factura extranjera | «Factura Electrónica de Venta», «CUFE» (Colombia); «CLAVE DE ACCESO», «R.U.C.» (Ecuador) |

## 5. Por qué contabilidad devuelve un pago (lo que más conviene cazar antes)

1. **El correo llegó sin adjuntos o sin la factura.** El conector lo impide: la factura entra sola y sin ella no envía un pago nacional.
2. **Factura PUE de un mes ya cerrado:** piden refacturar. Es la devolución más repetida.
3. **La cuenta bancaria está a nombre de alguien distinto del que factura.** Tesorería lo rechaza siempre.
4. **Límite de depósitos en la cuenta del beneficiario** (personas físicas). No se ve en los documentos; si el taller es persona física, menciónalo.
5. **Pago internacional sin SWIFT o sin dirección del banco.**
6. **Dudas de autorización** en atenciones comerciales o pagos a persona física: van con visto bueno de dirección; el técnico lo pone en `observaciones`.

Nunca han devuelto un pago por opinión o constancia vencida: por eso esas reglas avisan y no bloquean.

## 6. Casos reales (para calibrar)

- **Expediente limpio con tipos equivocados** (170743): constancia, opinión y carátula subidas como «Taller»; el finiquito trae la INE dentro. Todo en orden; nada que pedir.
- **Opinión inservible** (156883): opinión de 2022 en un expediente por lo demás correcto; factura un centavo abajo del aprobado (se acepta). Salida B: se enseña la opinión y decide el técnico.
- **Todo en «Varios»** (173648): INE, estado de cuenta, opinión y constancia como «Varios»; factura PUE del mes en curso (bien). El cliente que firma el finiquito no es el de la orden del taller: menciónalo.
- **Casilla ocupada por otro documento** (152462, 150811): en «opinion_cumplimiento» había una Resolución en un caso y una INE en el otro; en realidad **no había opinión**. Una casilla llena no prueba que el documento exista.
- **Hoja con varias cuentas** (156883, 175101): cinco bancos sin decir cuál usar. AVISO: contabilidad elige.
- **VIN que no cuadra** (176485): el finiquito imprimía un VIN distinto al del expediente. REVISAR, con el documento abierto.
- **Bridgestone completo** (180346, Ecuador): finiquito con sello del taller, cédula, registro fiscal, hoja con banco, SWIFT, cuenta y dirección, y factura local en «Varios» (SIGA rechazó registrarla). Es el modelo.
- **Bridgestone flojo** (174076, 165232): mismo número de cédula y misma imagen de firma en finiquitos de dos averías distintas; certificación bancaria de 2024; SWIFT en una captura de pantalla. Dilo todo.
- **Comprobante con el folio mal** (152462 decía 154262; 158467 decía 150152): el nombre del archivo sí traía el folio correcto.

## 7. Catálogo de comentarios de pago

Son los textos que el área ya usa. Se publican **sólo con el sí del técnico**, con `comentar_averia` y la etiqueta indicada; salen firmados «Atentamente Nombre Apellido | etiqueta». Sustituye lo que va entre llaves.

### `pago_requisitos_nacional` · etiqueta `falta_documentacion`
**Cuándo:** Avería aceptada sin ningún documento de pago.

> Buen día. La avería se encuentra aceptada y se compartió la resolución. Para procesar el pago, les pedimos cargar en el apartado de documentos: finiquito firmado por el cliente (viene en la última página de la resolución); identificación oficial del cliente por ambos lados; datos bancarios para la transferencia (banco, razón social, cuenta y CLABE interbancaria); constancia de situación fiscal; y opinión de cumplimiento positiva del mes en curso. Después seleccionen «Vehículo en Taller» y «Aceptar»: se habilitarán los campos para cargar la factura en PDF y XML; al cargarla, seleccionen «Enviar» para que quede visible para el área de pagos. La factura se emite a GARANTIPLUS MEXICO, RFC GME160927DW0, por el monto aceptado en la resolución. Quedamos atentos.

### `pago_requisitos_internacional` · etiqueta `falta_documentacion`
**Cuándo:** Bridgestone (taller extranjero) aceptada sin documentos de pago.

> Buen día. La avería se encuentra aceptada y se compartió la resolución. Para procesar el pago, les pedimos cargar en el apartado de documentos: finiquito firmado por el cliente (viene adjunto en la resolución); identificación oficial del cliente por ambos lados; y los datos bancarios del beneficiario: nombre del banco, razón social del titular de la cuenta, número de cuenta, código SWIFT, ABA o IBAN según corresponda al país, y dirección del banco receptor. Después seleccionen «Vehículo en Taller» y «Aceptar» para cargar la factura correspondiente y seleccionen «Enviar». Quedamos atentos.

### `pago_falta_documento` · etiqueta `falta_documentacion`
**Cuándo:** Hay documentos de pago pero falta alguno.

> Buen día. Revisamos la documentación para el pago de la avería y nos hace falta: {lo que falta 1}; y {lo que falta 2}. De su apoyo cargándolo en el apartado de documentos y dejando un comentario una vez que se encuentre cargado. Quedamos atentos.

### `pago_falta_factura` · etiqueta `falta_documentacion`
**Cuándo:** Documentos completos y sin factura registrada.

> Buen día. Agradecemos de antemano su apoyo compartiendo la factura correspondiente (PDF y XML), ya que el área de pagos la requiere para continuar con el proceso y efectuar el pago. Una vez cargados ambos archivos, seleccionen «Enviar» y dejen un comentario. La factura se emite a GARANTIPLUS MEXICO, RFC GME160927DW0, por el monto aceptado en la resolución. Quedamos atentos.

### `pago_corregir_documento` · etiqueta `falta_documentacion`
**Cuándo:** Un documento no sirve: se dice cuál y por qué.

> Buen día. Revisamos la documentación para el pago de la avería y necesitamos su apoyo con lo siguiente: {qué documento y por qué no sirve}. De su apoyo cargando el documento corregido y dejando un comentario. Quedamos atentos.

### `pago_en_proceso` · etiqueta `completo`
**Cuándo:** El paquete ya se envió a contabilidad.

> Buen día. Se recibe la documentación completa y se procesa para pago. En cuanto contemos con el comprobante se lo compartimos por este medio.

### `pago_comprobante` · etiqueta `completo`
**Cuándo:** El comprobante de pago ya está cargado en la avería.

> Buen día. Se comparte comprobante de pago. De estar todo correcto, favor de cambiar el estatus a «factura liquidada» para cerrar la avería. Quedamos atentos en caso de una avería futura.


## 8. El correo a contabilidad (lo arma el conector; no lo redactes tú)

- **Asunto:** `Pago avería <folio> / Garantía <póliza> / Contrato <contrato> / VIN <vin>`; en Bridgestone, `Pago Bridgestone avería <folio> / Garantía <póliza> / Contrato <contrato>`.
- **Cuerpo:** «Hola, excelente tarde. De su apoyo con el pago. Anexo la documentación requerida. Misma que se encuentra cargada en SIGA. Quedo atento, saludos.» más las observaciones del técnico si las hay; en internacional, el monto y la moneda.
- **Adjuntos:** la factura (`averia_<folio>_<uuid>.xml` y `.pdf`) y los documentos que el técnico aprobó.
- **Destinatarios:** los de la configuración del conector. En modo de pruebas, sólo la dirección de pruebas, con `[PRUEBA]` en el asunto.
