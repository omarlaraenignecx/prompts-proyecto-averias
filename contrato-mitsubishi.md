# Contrato de cobertura Mitsubishi — referente único del programa GARANTÍA REAL 7 (certificado GarantiPlus + Póliza de Garantía Limitada MMDM + Programa de Reactivación)

**Versión de este recurso: 2026-10-28 (v1: creado. Fusiona el certificado GARANTÍA REAL 7 de GarantiPlus (febrero 2019), la Póliza de Garantía Limitada de Vehículo Nuevo Mitsubishi y Cuaderno de Mantenimiento de MMDM (agosto 2019) y el Manual del Programa de Reactivación de Garantía de MMDM (MMDM-MG-007-2025, agosto 2025) en un solo contrato de referencia, con la lectura flexible que decidió Omar el 28/10/2026. Sustituye al Anexo que `casos-mitsubishi.md` traía hasta su v3.1.)** Quien lo edite actualiza aquí la fecha y la nota de qué cambió.

---

## 0. Qué es este documento y cómo se usa

### 0.1 En SIGA no hay contrato de cobertura Mitsubishi

Los técnicos del área lo dijeron y hay que hacerles caso: **para las averías de la cuenta Mitsubishi, SIGA no tiene un contrato de cobertura.** Todas cuelgan del contrato centinela **57227**, no existe certificado individual por vehículo, la hoja resumen del certificado remite la vigencia de cada unidad a «un anexo» de VIN que SIGA no expone, y la ficha de `expediente_completo` dice «MITSUBISHI (programa, sin contrato individual)». Lo único que el conector entrega como «certificado» en esos folios es su copia del certificado del programa.

Por eso existe este archivo: es **el referente absoluto del «contrato Mitsubishi»** para analizar una avería de esa cuenta. Cuando `instructions.md` o `casos-garantiplus.md` dicen «el único contrato que existe para ti es el certificado de la avería», en Mitsubishi ese certificado **es este documento**. No hay otro.

### 0.2 De qué está hecho

Tres fuentes, fusionadas en un solo contrato (decisión de Omar, 28/10/2026: GarantiPlus administra y resuelve en SIGA la garantía de 7 años de MMDM, así que lo que promete la póliza del fabricante lo resuelve GarantiPlus):

| Fuente | Qué es | Cómo se cita en el Informe |
| --- | --- | --- |
| **Certificado GARANTÍA REAL 7** (GarantiPlus México, `CERTIFICADO FEBRERO. 2019.pdf`, 31 páginas: 1–11 el texto, 12–31 el anexo de VIN) | El contrato de garantía mecánica que MMDM (contratante) suscribe con GarantiPlus para cada unidad nueva. Es el texto que el conector transcribe. | Por numeral (`numerales: ["14.3"]`), con la numeración **S.N por posición** del Anexo A (sección 14, ítem 3). La definición de la cláusula 1, la 10 y la 11 van en `clausulasLiterales` porque no tienen párrafo de presentación. |
| **Póliza de Garantía Limitada de Vehículo Nuevo Mitsubishi y Cuaderno de Mantenimiento** (MMDM, `Service-Warranty-Booklet.pdf`, 48 páginas, agosto 2019) | La garantía del fabricante que MMDM entrega con cada vehículo: 7 años sin límite de kilometraje «defensa a defensa», partes cubiertas, exclusiones, obligaciones del propietario, programa de mantenimiento recomendado y registros de sellos. | Sólo en `clausulasLiterales`, con `numeral: "Póliza MMDM"` y `titulo` = el encabezado **exacto** de la sección del Anexo B (p. ej. `DAÑOS MENORES`). Nunca se le inventa un número. |
| **Manual del Programa de Reactivación de Garantía** (MMDM, `MMDM-MG-007-2025`, agosto 2025) | Las políticas de MMDM para desfases de mantenimiento (tres rangos) y el proceso de reactivación. | No es cláusula: se cita en el chat y en `desarrollo` como «conforme al Programa de Reactivación de Garantía de MMDM (MMDM-MG-007-2025)». |

Cada regla de las secciones 1–12 dice de cuál sale: `Certificado S.N`, `Póliza MMDM — SECCIÓN`, `Manual MMDM-MG-007-2025`. Los tres textos están íntegros en los Anexos A, B y C; las secciones 1–12 los ordenan por tema y los reconcilian.

### 0.3 Principio de lectura: flexible, a favor de la cobertura

El área tiene buena relación comercial con Mitsubishi y quiere **rechazar menos** (decisión de Omar, 28/10/2026). Este contrato se lee así:

1. **Cobertura «defensa a defensa» salvo exclusión expresa.** Todo componente mecánico, eléctrico o electrónico del vehículo está cubierto salvo que esté en una lista de exclusión expresa (cláusula 2 del certificado, o «PARTES Y SERVICIOS NO CUBIERTOS» y «PARTES CON GARANTIA DIRECTA DEL FABRICANTE» de la póliza) **y** la exclusión esté probada en el expediente. Las listas de «PARTES CUBIERTAS» de la póliza son ilustrativas, no limitativas.
2. **En duda, procede.** Si ningún texto excluye el componente ni la causa, y la evidencia no prueba una exclusión, la avería se trata como cubierta.
3. **Una exclusión se aplica con evidencia específica, no por sospecha.** Golpe, manipulación, negligencia, falla epidémica o campaña exigen constancia (fotos, diagnóstico, boletín de MMDM, comunicación del área). «Podría ser» no rechaza.
4. **Antes de rechazar, se pide lo que falta.** Un dato esencial ausente (diagnóstico, odómetro, comprobante de mantenimiento, presupuesto corregido) produce un comentario al distribuidor, no un rechazo.
5. **Entre dos lecturas que algún texto sostenga, la más favorable al beneficiario.** Donde el certificado y la póliza MMDM digan cosas distintas sobre un mismo componente o causa, se aplica la lectura más favorable al beneficiario **que alguno de los dos textos sostenga** (nunca una que no esté en ninguno), y el veredicto dice cuál texto la sostiene. Lo que el certificado prohíbe tajantemente y la póliza no matiza **no se relaja**: avería fuera de vigencia (5 y 14.5), siniestros (15.18), trabajos sobre el vehículo antes de la resolución cuando están probados (14.1), vehículo que no permaneció inmovilizado (14.2).
6. **Flexible no es inventar.** No se inventan cláusulas, intervalos, tolerancias ni precios; lo que no está en ningún texto no existe. El técnico decide siempre; este documento le da el texto.

### 0.4 Jerarquía dentro del contrato

1. La **vigencia y la identidad** de la unidad las da la póliza de SIGA (`policyId`, fechas si las trae), la carátula o la fecha de facturación que esté en el expediente. Si ninguna fuente las da, se piden; no se infieren.
2. El **certificado** (Anexo A) manda en procedimiento, límites, causales de rechazo y numerales.
3. La **póliza MMDM** (Anexo B) manda en cobertura de componentes, subgarantías, plan de mantenimiento y causas de exclusión que el certificado no describe (daños menores, odómetro alterado, modificaciones).
4. El **Manual** (Anexo C) manda en desfases de mantenimiento: sus tres rangos sustituyen a cualquier otra tolerancia.
5. Lo que el área instruya por escrito después del 28/10/2026 manda sobre este archivo (se registra con fuente `Técnico`, quién y cuándo, y quien edite este archivo lo incorpora).

---

## 1. Partes, objeto y hoja resumen

### 1.1 Las partes (Certificado, hoja resumen y cláusula 1)

- **GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.**, R.F.C. GME160927DW0, Av. Presidente Masaryk Nº 111 – Piso 1, Col. Chapultepec Morales, Ciudad de México, 11560 (hoja resumen); dirección de facturación de reparaciones: Calle Bosques de Duraznos 61, piso 1, Col. Bosques de las Lomas, Miguel Hidalgo, Ciudad de México, 11700 (12.9).
- **CONTRATANTE – DISTRIBUIDOR:** «MITSUBISHI MOTORS DE MEXICO SA DE CV», R.F.C. MMM1711282H8 (hoja resumen). En el certificado, «Tendrá la consideración de CONTRATANTE del contrato el vendedor del VEHÍCULO, que será el obligado al pago del precio del certificado contratado de garantía mecánica» (1.1).
- **BENEFICIARIO:** «el comprador del VEHÍCULO, quien será el destinatario de la garantía mecánica objeto del certificado contratado» (1.2).
- **MMDM** en la póliza: «Mitsubishi Motors de México, S.A. de C.V.», escritura N-2017100943, R.F.C. MMM1711282H8, Torre Omega piso 7 of. 702-B, Campos Elíseos 345, Polanco Chapultepec, Miguel Hidalgo, C.P. 11560 (Póliza MMDM — PÓLIZA DE GARANTÍA LIMITADA). **Distribuidor de Mitsubishi Motors:** el concesionario autorizado que presta el servicio y las reparaciones (Póliza MMDM — INTRODUCCIÓN).

### 1.2 Producto y límites (Certificado, hoja resumen)

| Dato | Valor |
| --- | --- |
| Producto contratado | **GARANTÍA REAL 7** |
| Fecha de contrato (del formato) | 24/06/2019 |
| Límite por avería | **Valor venta vehículo** |
| Límite de contrato | **Valor venta vehículo** |
| Vehículo objeto | Marca MITSUBISHI; «NUMERO DE SERIE (VIN): ANEXA A ESTE CONTRATO» |
| Periodo de vigencia | «FECHA INICIO GARANTIA: ANEXA AL CONTRATO · FECHA FIN GARANTIA: ANEXA AL CONTRATO» |
| Anexo | «AL FINAL DEL CONTRATO SE ANEXA EL LISTADO DE VINES GARANTIZADOS, INDICANDO EN CADA UNO DE ELLOS EL INICIO Y EL FIN DE GARANTÍA» |

Texto literal de la hoja resumen que hay que conocer: «*Los datos introducidos tendrán que coincidir fehacientemente con los del vehículo objeto de garantía. En caso de error será motivo de rescisión del contrato.*» Y sobre la vigencia: «*Siempre que se hayan realizado en el VEHÍCULO en tiempo y forma los servicios y mantenimientos; el PERIODO DE VIGENCIA DEL CONTRATO podrá comenzar a computarse hasta el momento en que expire la garantía del fabricante o alguna otra garantía de similar naturaleza, ya sea por sobrepasar el kilometraje o cumplirse el tiempo establecido en la misma. En cualquier caso, la Garantía Mecánica de GarantiPlus México, S.A.P.I. de C.V. será válida conforme a los términos y condiciones del presente Contrato.*»

**Cómo se lee ese párrafo aquí** (decisión de Omar, 28/10/2026): es texto genérico del formato de GarantiPlus. En el programa Mitsubishi, GarantiPlus administra la propia garantía de 7 años de MMDM, así que **no hay una «garantía del fabricante» previa que desplace el inicio**: la vigencia de cada unidad es la del anexo por VIN (inicio y fin de garantía), que en la práctica se confirma con la póliza de SIGA, la carátula o la fecha de facturación, y coincide con la «Fecha de inicio de la garantía» de la póliza MMDM (1.4). El párrafo no se usa para negar una avería dentro de los 7 años.

### 1.3 Objeto

- **Certificado 4:** «GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. garantiza, dentro de los límites fijados en el presente documento, el pago de la reparación de las AVERÍA/AS.»
- **Certificado 1.5:** «Mediante este contrato de Garantía GarantiPlus México se compromete a pagar los costos razonables de reparación de una avería cubierta relativa al vehículo garantizado, dentro de los límites de pago por avería y condiciones del mismo. Quedan cubiertas por el certificado contratado la reparación o sustitución de todas las piezas o componentes que presenten defectos como consecuencia de una avería fortuita en los elementos mecánicos, eléctricos o electrónicos.»
- **Póliza MMDM — COBERTURAS DE GARANTÍA:** «MMDM garantiza que el Vehículo se encuentra protegido en términos generales por defectos de fabrica por calidad de materiales o mano de obra por un plazo de 7 (siete) años sin límite de kilometraje defensa a defensa*, contados a partir de la fecha de facturación del vehículo como se establece en el Registro del primer propietario de esta póliza (en adelante, “Fecha de inicio de la garantía") o puesta en marcha lo que ocurra primero.» Y: «MMDM otorga al propietario original o subsecuente del vehículo registrado y operado normalmente en la República Mexicana a través de sus Distribuidores de Mitsubishi Motors, los servicios de reparaciones de garantía de partes en las que se demuestre que están defectuosas por calidad de producto o manufactura dentro del período de garantía aplicable a dichas partes, la cual será reparada o reemplazada sin costo alguno para el cliente por un distribuidor Mitsubishi Motors cumpliendo con la norma oficial mexicana respectiva y durante la vigencia especificada en la presente póliza, siempre y cuando se haya realizado el mantenimiento correcto y no aplique alguna de las exclusiones descritas más adelante.»

### 1.4 La «Fecha de inicio de la garantía»

Es «la fecha de facturación del vehículo como se establece en el Registro del primer propietario de esta póliza … o puesta en marcha lo que ocurra primero» (Póliza MMDM — COBERTURAS DE GARANTÍA). Desde ella corren los 7 años, las subgarantías de la sección 3 y el plan de mantenimiento. En SIGA suele coincidir con la fecha de inicio de la póliza; si difieren, se enseñan las dos y decide el técnico.

---

## 2. Definiciones

### 2.1 Del certificado (Certificado 1, literal)

- **1.1 CONTRATANTE:** «Tendrá la consideración de CONTRATANTE del contrato el vendedor del VEHÍCULO, que será el obligado al pago del precio del certificado contratado de garantía mecánica.»
- **1.2 BENEFICIARIO:** «Tendrá la consideración de BENEFICIARIO el comprador del VEHÍCULO, quien será el destinatario de la garantía mecánica objeto del certificado contratado.»
- **1.3 VEHÍCULO:** «A los efectos del certificado contratado, tendrá la consideración de VEHÍCULO únicamente el descrito en la HOJA RESUMEN DEL CONTRATO DE GARANTÍA MECÁNICA que, en todo caso, no podrá tener más de 450 C.V. de potencia o tener denominación industrial ya sea ligera o pesada.»
- **1.4 AVERÍA/AS:** «Se entiende por avería mecánica, eléctrica, o electrónica, la inutilidad operativa (conforme a las especificaciones del fabricante) de la pieza garantizada, debido a una rotura imprevista / fortuita. No se incluye en esta definición la reducción gradual en el rendimiento operativo de la pieza garantizada que sea proporcional y equivalente a su antigüedad y kilometraje (se entiende a partir de la primera matriculación del vehículo, y no a partir del inicio del contrato de garantía), ni las averías derivadas de accidentes o cualesquiera influencias externas.»
- **1.5** (el párrafo de compromiso, transcrito en 1.3 de este documento).

### 2.2 De la póliza MMDM

- **Vehículo:** el fabricado por MMDM «con los mejores materiales, con las últimas técnicas de ingeniería de automóviles y los métodos más avanzados de control de calidad» (Póliza MMDM — INTRODUCCIÓN).
- **Defecto cubierto:** «defectos de fabrica por calidad de materiales o mano de obra» (Póliza MMDM — COBERTURAS DE GARANTÍA).
- **Fecha de inicio de la garantía:** 1.4 de este documento.
- **Registro del propietario:** el informe de registro del primer, segundo y tercer propietario y la inspección antes de la entrega que llena el distribuidor (Póliza MMDM — INFORME DE REGISTRO; INSPECCIÓN ANTES DE LA ENTREGA).

### 2.3 Cómo se leen juntas

Una **avería cubierta** es la inutilidad operativa de una pieza garantizada por rotura imprevista o fortuita (certificado 1.4) **o** la falla de una parte «defectuosa por calidad de producto o manufactura» (póliza). Las dos definiciones excluyen lo mismo: la reducción gradual proporcional a antigüedad y kilometraje (1.4), el «desgaste normal» (10; Póliza MMDM — DESGASTE) y lo que viene de accidentes o influencias externas (1.4; Póliza MMDM — ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE). Un componente que falla antes de lo que su función y kilometraje hacen esperar, sin causa externa probada, encaja en las dos y **se trata como avería cubierta**.

---

## 3. Duración, vigencia, transferencia y territorio

### 3.1 Duración (Certificado 5; Póliza MMDM — COBERTURAS DE GARANTÍA)

- **Certificado 5:** «El periodo de garantía cubierto por el certificado de garantía contratado será el indicado en el mismo. Por tanto, sólo estarán cubiertas las AVERÍA/AS que tenga el VEHÍCULO durante la vigencia del contrato. Siempre que se hayan realizado en el VEHÍCULO en tiempo y forma los servicios y mantenimientos señalados.»
- **Póliza MMDM:** **7 (siete) años sin límite de kilometraje, defensa a defensa**, desde la Fecha de inicio de la garantía.
- **Lectura:** la vigencia de la unidad es la del anexo por VIN / póliza de SIGA; a falta de ese dato, 7 años desde la facturación. Una avería **ocurrida y comunicada dentro de la vigencia** está en plazo. «Siempre que se hayan realizado … los servicios y mantenimientos» se lee con los rangos de desfase de la sección 8: un desfase dentro de rango no quita la vigencia.

### 3.2 Subgarantías con plazo propio (Póliza MMDM — COBERTURAS DE GARANTÍA; Certificado 3)

| Componente | Plazo | Fuente |
| --- | --- | --- |
| Vehículo en general («defensa a defensa») | 7 años, sin límite de km | Póliza MMDM — COBERTURAS DE GARANTÍA |
| Paneles metálicos, por corrosión | «5 (cinco) años o 60,000 (sesenta mil) Kilómetros a partir de la fecha de inicio de la garantía» | Póliza MMDM — COBERTURAS DE GARANTÍA |
| Batería auxiliar (12 volts) de equipo original | «24 (veinticuatro) meses a partir de la fecha de inicio de la garantía» | Póliza MMDM — COBERTURAS DE GARANTÍA |
| Smart Display Audio o Display Audio (estéreo) | «3 (tres) años o 60,000 (sesenta mil) kilómetros lo que ocurra primero» | Póliza MMDM — COBERTURAS DE GARANTÍA (nota *) |
| Batería de manejo de alto voltaje (PHEV) | «los primeros 7 AÑOS sin límite de kilómetros, a partir de la fecha de inicio de la garantía»; «La pérdida gradual de la retención de carga de la batería debido al tiempo y el uso NO está cubierta» | Certificado 3.1; Póliza MMDM — PARTES CUBIERTAS |
| Componentes eléctricos PHEV (motor eléctrico, motor eléctrico del sistema de refrigeración, líneas de alta tensión, conexión regular de carga, inversor – PHEV-ECU, conexión de carga rápida, trans eje, cargador a bordo / convertidor DC-DC) | «los primeros 7 AÑOS sin límite de kilómetros» | Certificado 3.2; Póliza MMDM — PARTES CUBIERTAS |

**Lectura flexible:** la batería de 12 V y el estéreo están en la lista de exclusiones del certificado (2.8) o en «PARTES CON GARANTIA DIRECTA DEL FABRICANTE» (estéreos), pero la póliza les da un plazo propio de cobertura. Por la regla 5 de 0.3, **dentro de esos plazos se tratan como cubiertos** (batería 12 V hasta 24 meses; Smart Display Audio hasta 3 años / 60,000 km) cuando fallan por defecto y no por uso; fuera de ellos aplica la exclusión. Se cita la sección de la póliza en `clausulasLiterales`.

### 3.3 Transferencia y cesión

- «La cobertura de la Garantía de Vehículo será transferida automáticamente sin costo alguno, a los propietarios subsecuentes del vehículo, siempre que el mantenimiento requerido sea realizado por un Distribuidor de Mitsubishi Motors dentro de los límites de tiempo y kilometraje especificados en el manual del propietario y el de servicio.» (Póliza MMDM — COBERTURAS DE GARANTÍA). «La garantía se otorga al propietario original o propietarios subsecuentes del Vehículo, en su caso, por el periodo restante de garantía.»
- «Los derechos que otorga esta póliza de garantías solo aplicarán para los vehículos descritos en el adverso de este documento y no podrán ser transferidos bajo ninguna circunstancia a otro vehículo. La presente Póliza de Garantía podrá ser transferible a otra persona sin necesidad de aprobación por el distribuidor Mitsubishi a propietarios subsecuentes del vehículo.» (Póliza MMDM — CESIÓN).
- **Lectura:** un cambio de propietario no afecta la cobertura. La condición «mantenimiento en Distribuidor Mitsubishi» se lee con la sección 8.6 (servicios en taller independiente).

### 3.4 Territorio y perfección

- **Certificado 6:** «El certificado contratado se perfecciona por el consentimiento manifestado con la firma del mismo documento.»
- **Certificado 7:** «La garantía objeto del certificado contratado se extiende y limita a las AVERÍA/AS que tengan lugar dentro de la República Mexicana.»
- **Póliza MMDM — PRESTACIÓN DEL SERVICIO LUGAR Y HORARIO:** «El servicio de garantía no aplica si las reparaciones fueron realizadas por terceros o distribuidores Mitsubishi fuera de la República Mexicana.»

### 3.5 Cómo se confirma la vigencia en un caso

1. Póliza de SIGA (fechas de inicio y fin, si la ficha las trae). 2. Carátula o póliza de la unidad en el expediente. 3. Fecha de facturación o de entrega (factura de venta, inspección antes de la entrega, PRC). 4. Si ninguna fuente la da: se pide al distribuidor (comentario) y el caso queda pendiente; **no se rechaza por «sin vigencia» sin un dato que lo pruebe**, y tampoco se acepta por inferencia (0.4).

---

## 4. Cobertura: qué está cubierto

### 4.1 El principio (Certificado 1.5 y 10; Póliza MMDM — COBERTURAS DE GARANTÍA)

- **Certificado 10:** «GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en relación con el certificado contratado, tiene la obligación de, en los términos y con los límites fijados en el mismo, hacerse cargo de la reparación de las AVERÍA/AS cubiertas, que dentro del periodo de vigencia del certificado pueda tener el VEHÍCULO, siempre y cuando dichas AVERÍAS no traigan causa en un uso inadecuado del VEHÍCULO, o en el deterioro y/o desgaste normal del mismo.»
- **Póliza MMDM:** «defensa a defensa» por «defectos de fabrica por calidad de materiales o mano de obra».
- **Regla de este contrato (0.3):** cubierto todo elemento mecánico, eléctrico o electrónico montado de origen, salvo exclusión expresa y probada (sección 5) o causa excluida y probada (sección 6).

### 4.2 Partes cubiertas que la póliza nombra expresamente (Póliza MMDM — PARTES CUBIERTAS, literal)

Lista **ilustrativa**: lo que está aquí está cubierto sin discusión; lo que no está aquí también lo está salvo exclusión (0.3).

**COMPONENTES DE TREN MOTRIZ — MOTOR:**
- Bloque de cilindros y todas piezas lubricadas internas incluyendo:
- Cigüeñal y rodamientos principales
- Banda de Distribución y piezas relacionadas
- Ejes de balancines
- Conjuntos de cabeza de cilindro
- Soportes del motor
- Volante o placa de mando (incluido el engranaje de anillo)
- Bomba de combustible (s)
- Múltiple de admisión y escape
- Válvulas de Admisión y escape
- Bomba de aceite
- Cubiertas de válvula y juntas de cubierta de válvula
- Bomba de agua
- Turbocompresor
- Juntas y sellos de todos los componentes anteriores

**TRANSEJE / TRANSMISIÓN Y CAJA DE TRANSFERENCIA:**
- Convertidor de par (incluido el engranaje de anillo)
- Caja de transeje y todas las piezas lubricadas internas, juntas y sellos
- Soportes de transmisión, transmisión y caja de transferencia y todas las piezas lubricadas internas, juntas y sellos
- Caja de transmisión y todas las piezas lubricadas internas, juntas y sellos

**OTROS COMPONENTES DE TREN MOTRIZ:**
- Carcasa del eje y todas las piezas lubricadas internas, juntas y sellos
- Cojinetes del eje
- Ensamblajes de diferenciales y todas las piezas lubricadas internas, juntas y sellos
- Conjuntos de eje de transmisión y eje de dirección (incluidas juntas de velocidad constante)
- Ensambles de propelas de eje y yugos (incluidas juntas de velocidad constante y / o juntas universales)
- Rodamientos centrales del eje de la propela

**BATERÍA DE MANEJO ALTO VOLTAJE (para vehículo PHEV únicamente):** «La batería del vehículo de equipo original está garantizada. La pérdida gradual de la retención de carga de la batería debido al tiempo y el uso NO está cubierta por esta GARANTÍA.»

**COMPONENTES ELÉCTRICOS (para vehículo PHEV únicamente):** motor eléctrico; motor eléctrico del sistema de refrigeración; líneas de alta tensión; conexión regular de carga; inversor – PHEV-ECU; conexión de carga rápida; transeje; cargador a bordo / convertidor DC-DC.

### 4.3 Cobertura PHEV (Certificado 3, literal)

- **3.1 BATERÍA DE MANEJO ALTO VOLTAJE (para vehículo PHEV únicamente):** «a. La batería de la unidad equipada originalmente está garantizada para los primeros 7 AÑOS sin límite de kilómetros, a partir de la fecha de inicio de la garantía. b. La pérdida gradual de la retención de carga de la batería debido al tiempo y el uso NO está cubierta por esta GARANTÍA. c. Consulte el Manual del propietario para obtener más información sobre la pérdida de capacidad de la batería.»
- **3.2 COMPONENTES ELECTRICOS (para vehículo PHEV únicamente):** «a. Los componentes Eléctricos (PHEV) equipados originalmente están garantizados para los primeros 7 AÑOS sin límite de kilómetros, a partir de la fecha de inicio de la garantía. b. COMPONENTES Eléctricos (PHEV) incluyen los siguientes: i. Motor eléctrico. ii. Motor eléctrico del sistema de refrigeración iii. Líneas de alta tensión. iv. Conexión regular de carga v. Inversor - PHEV-ECU vi. Conexión de carga rápida vii. Trans eje viii. Cargador a bordo /Convertidor DC-DC».

### 4.4 Guía de lectura por sistema

| Sistema | Cubierto (con qué texto) | Excluido sólo si (con qué texto) |
| --- | --- | --- |
| **Motor** (bloque, cabeza, cigüeñal, árboles, válvulas, bombas de aceite, agua y combustible, múltiples, turbo, soportes, volante, juntas y sellos) | Póliza MMDM — PARTES CUBIERTAS (lista literal); Certificado 1.5 | Causa probada de las secciones 6 (desgaste normal al final de vida útil 15.3; falta de lubricación por mantenimiento no hecho; combustible o lubricante contaminado 15.22; seguir circulando con testigo 15.13; motor dañado por falla de banda de distribución 15.8, con la lectura de 5.3) |
| **Transmisión, transeje, CVT, caja de transferencia, convertidor, diferenciales, flechas, juntas homocinéticas, soportes de transmisión** | Póliza MMDM — PARTES CUBIERTAS; Certificado 1.5 | Igual que motor; sobrecarga 15.16; competiciones 15.15 |
| **Sistema eléctrico y electrónico** (módulos, sensores, actuadores, arneses, alternador, marcha, interruptores, instrumentos, ECU, red CAN) | Certificado 1.4–1.5 («eléctrica, o electrónica»); Póliza MMDM — COBERTURAS DE GARANTÍA («defensa a defensa») | Actualizaciones, programaciones o cargas de software (15.6; Póliza MMDM — ACTUALIZACIONES); manipulación de la red CAN o del control de emisiones (Póliza MMDM — ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE); accesorios no originales (15.23) |
| **Climatización** (compresor, condensador, evaporador, válvula de expansión, portalentes, mangueras de A/C, módulo de clima) | Certificado 1.5; criterio del área: portalentes y mangueras de A/C cubiertos (`casos-mitsubishi.md` §5.3) | Carga de gas como servicio (2.8, 15.5) salvo que la necesite una avería cubierta; fuga por golpe o corrosión probados (15.4, 15.18) |
| **Dirección y suspensión** (cremallera, bomba o motor de dirección asistida, brazos, rótulas, bujes, muelles, amortiguadores) | Certificado 1.5 para cremallera, bomba/motor EPS, brazos, rótulas; Póliza MMDM — PARTES CUBIERTAS («eje de dirección») | Amortiguadores (2.8, 15.5; Póliza MMDM — MANTENIMIENTO: «Amortiguadores desgastados»); bujes y gomas que perdieron su morfología (2.9, 15.4); desgaste normal (15.3) |
| **Frenos** (bomba, booster, cilindros, calipers, ABS, EPB) | Certificado 1.5 para la hidráulica y el ABS | Discos, balatas y forros (2.8, 15.5; Póliza MMDM — CONSUMIBLES); líquido de frenos (lubricantes) |
| **Combustible y escape** (bomba, inyectores, riel, catalizador, sensores EGT y O2, DPF) | Certificado 1.5; Póliza MMDM — PARTES CUBIERTAS (bomba de combustible, múltiple de escape); criterio del área: sensor EGT (`casos-mitsubishi.md` §5.3) | Escapes y catalizadores como consumible (2.8, 15.5); combustible contaminado (15.22) |
| **Enfriamiento** (radiador, bomba de agua, termostato, ventilador, mangueras) | Bomba de agua en Póliza MMDM — PARTES CUBIERTAS; el resto por 1.5 | Fugas de refrigerante como consumible (15.5) salvo que sean el síntoma de un componente cubierto que falló; mangueras que perdieron morfología (15.4) |
| **Carrocería, cristales, faros, molduras, asientos, habitáculo, neumáticos** | — | Excluidos por lista (2.1–2.7; Póliza MMDM — PARTES CON GARANTIA DIRECTA DEL FABRICANTE: neumáticos; PINTURA Y OTROS ELEMENTOS DE APARIENCIA; CORROSIÓN salvo paneles 5 años / 60,000 km) |
| **Infoentretenimiento** | Smart Display Audio 3 años / 60,000 km (3.2 de este documento) | Estéreos: «garantía directa del fabricante» (Póliza MMDM — PARTES CON GARANTIA DIRECTA DEL FABRICANTE) fuera de ese plazo |
| **PHEV** | Certificado 3; Póliza MMDM — PARTES CUBIERTAS | Pérdida gradual de retención de carga (3.1.b) |

---

## 5. Exclusiones de elementos (qué piezas no cubre)

### 5.1 Lista expresa del certificado (Certificado 2, literal)

«Se excluyen de manera expresa los siguientes elementos:»
- **2.1** Asientos completos y mecanismos (mecánicos)
- **2.2** Elementos internos del habitáculo y/o maletero (tapizados, guarnecidos, reposabrazos, salpicadero, consolas, soportes, tapas, aireadores, ceniceros, encendedor, lámparas)
- **2.3** Neumáticos, válvula de rueda (con o sin sensor)
- **2.4** Totalidad de los elementos de carrocería
- **2.5** Totalidad de cristales y lunas, incluida térmica
- **2.6** Faros, intermitentes, calaveras, lámparas
- **2.7** Molduras, embellecedores, espejos retrovisores completos, paragolpes
- **2.8** Consumibles (filtros, cartuchos, aceite, juntas), amortiguadores, escapes, discos de freno, pastillas, correas, servicio periódico, servicios intermedios, lubricantes, combustibles, aditivos, carga de circuito de a/a (salvo que sea necesario por avería cubierta), bujías, calentadores, batería, escobillas, plumas limpiaparabrisas
- **2.9** Elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas).

### 5.2 Partes y servicios no cubiertos por la póliza (Póliza MMDM, literal)

**PARTES CON GARANTIA DIRECTA DEL FABRICANTE:** «Las partes que se enlistan a continuación no están cubiertas por la garantía de MMDM, la garantía la cubrirá directamente el fabricante de las partes: Neumáticos; Estéreos; Todas las partes que no sean instaladas originalmente en el vehículo nuevo.»

**PARTES Y SERVICIOS NO CUBIERTOS (EXCEPCIONES) — CONSUMIBLES Y LUBRICANTES.** «Algunos ejemplos incluyen, sin limitar:» CONSUMIBLES: elemento del filtro de aire; elemento de filtro de aceite; elemento filtro de combustible; correas de transmisión; bujía (excluyendo Platino o Iridio tipo de enchufe con punta); plato del embrague, pastillas de freno y forro de freno; plumilla y mecanismo de limpiaparabrisas; fusible; foco (excepto faros de haz sellado, halógeno y de descarga); otras piezas consumibles. LUBRICANTES: aceite de motor; aceite de transmisión manual; fluido de transmisión automática; fluido de frenos y embrague; grasa; refrigerante del motor; aceite del engranaje diferencial; aceite y/o fluido de engranaje de dirección; aceite para engranajes de transferencia; batería electrolítica; refrigerante; líquido para lavaparabrisas; combustible.

**MANTENIMIENTO / DESGASTE / ACTUALIZACIONES — MANTENIMIENTO:** «Las piezas y la mano de obra necesarias para mantener el vehículo y el reemplazo de las piezas debido al desgaste normal no están cubiertos por la garantía y son responsabilidad del propietario. Algunos ejemplos incluyen, sin limitar:» alineación de neumáticos; balatas / disco de freno desgastados; limpieza y pulido; revestimientos del disco del embrague desgastados; afinaciones del motor; lubricación (aceite, lubricante o refrigerante de motor, transmisión, frenos o embrague, diferencial, dirección, caja de transferencia, limpiaparabrisas); reemplazo de filtros de aire o aceite, refrigerantes o fusibles; reemplazo de bujías de encendido; plumillas del limpiaparabrisas desgastadas; banda / cadena de tiempo; correas de transmisión; amortiguadores desgastados; revisiones en general; daños causados por una reparación o mantenimiento insuficientes o inadecuados; las piezas y el material utilizados en relación con dicho servicio.

**ACTUALIZACIONES:** actualizaciones de software y mapas para sistemas de navegación; actualizaciones de hardware o software necesarias para admitir o conectar dispositivos no suministrados por Mitsubishi Motors.

**PINTURA Y OTROS ELEMENTOS DE APARIENCIA; CORROSIÓN; DESGASTE; DAÑOS MENORES:** texto íntegro en el Anexo B. El de **DAÑOS MENORES** importa para los ruidos: «Pequeñas irregularidades que no afectan la calidad, el rendimiento o la función del vehículo o sus partes (por ejemplo, un ruido leve o vibración) o que aparecen en particular solo en operaciones anormales.»

### 5.3 Reconciliaciones (certificado vs. póliza), con la lectura que aplica

Cada fila dice los dos textos y la lectura más favorable al beneficiario que alguno sostiene (0.3, regla 5). Es la lectura de este contrato; el técnico decide.

| Pieza | Certificado | Póliza MMDM | Lectura que aplica |
| --- | --- | --- | --- |
| **Soportes de motor y de transmisión** | 2.9 excluye «elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas)»; 15.4 repite | PARTES CUBIERTAS lista «Soportes del motor» y «Soportes de transmisión» | **Cubiertos** cuando fallan por rotura, defecto o antes de lo que su kilometraje hace esperar; **excluidos** sólo si la causa probada es pérdida de morfología por envejecimiento normal (goma vencida, agrietada por años) y el diagnóstico lo dice. En duda, cubierto. |
| **Juntas y sellos (retenes)** | 2.8 «juntas» como consumible; 15.4 «juntas, mangueras, retenes» que perdieron morfología; 15.5 «fugas de aceite» | PARTES CUBIERTAS: «Juntas y sellos de todos los componentes anteriores» (motor, transeje, ejes, diferenciales) | **Cubiertas** cuando son parte de la reparación de un componente cubierto o fallan por defecto (un retén que se vence prematuramente y deja sin aceite un componente cubierto); **excluidas** como consumible de un servicio periódico o cuando la fuga es la única falla y la pieza llegó al final de su vida útil (15.3). |
| **Banda de distribución** | 2.8 «correas»; 15.5 «correas de distribución»; 15.8 excluye «avería del motor originada por la falla de banda de distribución» | PARTES CUBIERTAS: «Banda de Distribución y piezas relacionadas»; pero MANTENIMIENTO lista «Banda / Cadena de tiempo» como reemplazo de desgaste no cubierto; programa S13: reemplazo a 100,000 km (L200 y Montero Sport) | La **banda** como pieza es cubierta si falla por defecto antes de su intervalo de reemplazo (100,000 km) con mantenimiento acreditado. El **motor dañado por su falla** sigue excluido por 15.8, **salvo** que la banda haya fallado dentro de su intervalo de reemplazo y con el plan cumplido: entonces la causa es un defecto de la pieza cubierta y la avería consecuente se valora con ella (lectura flexible; se dice como tal y decide el técnico). |
| **Mangueras** (A/C, refrigerante, frenos) | 15.4 excluye mangueras que perdieron su morfología; 15.5 fugas de refrigerante | PARTES CUBIERTAS no las lista; el criterio del área (PDF 27/10/2026) cubre portalentes y mangueras de A/C | **Cubiertas** por defecto, por indicación de MMDM (`casos-mitsubishi.md` §5.3) y por 1.5; excluidas sólo si la pérdida de morfología por envejecimiento normal está probada. |
| **Batería 12 V** | 2.8 y 15.5 la excluyen | Garantizada 24 meses desde el inicio | **Cubierta hasta 24 meses** por defecto de fabricación (no por descarga por uso o abandono); después, excluida. |
| **Bujías de platino o iridio** | 2.8, 15.5 «bujías» | CONSUMIBLES excluye bujía «excluyendo Platino o Iridio tipo de enchufe con punta» | **Cubiertas** si fallan por defecto antes de su intervalo (S13: 90,000–100,000 km); las convencionales, consumible. |
| **Estéreo / Smart Display Audio** | 1.5 (elemento electrónico) | Estéreos: garantía directa del fabricante; Smart Display Audio: 3 años / 60,000 km | Dentro de 3 años / 60,000 km, **cubierto**; fuera, se orienta al distribuidor para la garantía directa del fabricante, y el Informe lo dice en vez de llamarlo «excluido» sin más. |
| **Amortiguadores** | 2.8, 15.5 (por lista) | MANTENIMIENTO: sólo «Amortiguadores desgastados» | Excluidos por 2.8 y 15.5. La póliza sólo excluye los desgastados, así que un amortiguador roto por defecto con kilometraje bajo es una lectura flexible **pendiente de confirmar con Omar**; mientras tanto, excluido y se dice. |
| **Discos y balatas; embrague** | 2.8, 15.5 | CONSUMIBLES; MANTENIMIENTO | Consumibles: excluidos. El **volante o placa de mando** sí está cubierto (PARTES CUBIERTAS). |
| **Catalizador, DPF, escape** | 2.8 «escapes»; 15.5 «escapes, catalizadores» | PARTES CUBIERTAS: «Múltiple de admisión y escape» | Múltiple de escape **cubierto** (la póliza lo lista). Catalizador, DPF y silenciadores **excluidos** por 2.8 y 15.5: la póliza no los nombra como cubiertos y el «defensa a defensa» genérico no vence una exclusión expresa del certificado. Si el técnico quiere cubrir un catalizador por defecto de fábrica, es decisión suya (fuente `Técnico`). |
| **Sensores de O2 / EGT, sensores en general** | 1.5 | «defensa a defensa» | **Cubiertos**; el sensor EGT aunque el presupuesto lo rotule como O2 (`casos-mitsubishi.md` §5.3). |
| **Turbocompresor** | 1.5 | PARTES CUBIERTAS | **Cubierto**; excluido sólo con prueba de falta de lubricación por mantenimiento no hecho o aceite contaminado. |
| **Carga de A/C** | 2.8 «salvo que sea necesario por avería cubierta» | — | Cubierta cuando forma parte de la reparación de un componente de clima cubierto. |
| **Fusibles, focos, plumas, filtros, faros** | 2.6, 2.8 | CONSUMIBLES | Excluidos. Los faros de haz sellado, halógeno y de descarga no son consumible para la póliza, pero 2.6 excluye «Faros» por lista: excluidos. |

### 5.4 Elementos que no están en ninguna lista

Un componente que no aparece en 2.1–2.9 ni en las listas de la póliza **está cubierto** (0.3). Un rechazo por «componente excluido» exige nombrar el inciso o la sección que lo excluye; si no existe, no hay rechazo por componente y se pasa a la causa (sección 6).

---

## 6. Exclusiones por causa y causales de rechazo

### 6.1 Exclusiones generales del contrato (Certificado 14, literal)

«GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. podrá rechazar la reparación, y/o en su caso el pago de la AVERÍA/AS en los siguientes supuestos:»
- **14.1** Cuando se haya realizado cualquier tipo de trabajo sobre el VEHÍCULO antes de la resolución del expediente por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **14.2** Cuando el VEHÍCULO no haya permanecido inmovilizado en el taller desde la comunicación de la AVERÍA/AS hasta la resolución del expediente por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **14.3** Cuando el BENEFICIARIO no haya cumplido sus obligaciones en relación con los mantenimientos e inspecciones exigidas en el certificado contratado.
- **14.4** Cuando las facturas correspondientes a los mantenimientos periódicos o cualquier documentación exigida dentro del Articulo 12.-PROCEDIMIENTO EN CASO DE AVERÍAS/AS del certificado contratado, no estén debidamente cumplimentadas, o directamente no se aporten a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en un plazo de 72h tras ser requeridas.
- **14.5** Cuando la AVERÍA/AS haya sido comunicada a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., transcurrido el plazo de duración del contrato, aun cuando la AVERÍA/AS haya acontecido con anterioridad a su expiración
- **14.6** Cuando haya habido cualquier tipo de incumplimiento por parte del CONTRATANTE o del BENEFICIARIO.

**Cómo se aplican (lectura flexible):**

| Causal | Qué evidencia hace falta | Lectura |
| --- | --- | --- |
| 14.1 trabajos antes de la resolución | Constancia de que el taller desmontó, reparó o intervino antes de la resolución **sin** que GarantiPlus lo requiriera (12.4): fotos de piezas ya desmontadas sin solicitud de desmontaje, factura de reparación previa, Seguimiento. | Se aplica cuando está probado (0.3, regla 5: no se relaja). Un desmontaje **requerido por GarantiPlus y autorizado por el propietario** para determinar el origen (12.4) **no** es 14.1. El diagnóstico por lectura de códigos, prueba de manejo o inspección visual no es «trabajo sobre el vehículo». |
| 14.2 no inmovilizado | Prueba de que circuló entre la comunicación y la resolución (odómetro distinto, salida del taller). | Se aplica con prueba. |
| 14.3 mantenimientos no cumplidos | La tabla de intervalos (sección 8) con un tramo **fuera de los rangos del Manual** (más de 6,000 km o más de 186 días), o un desfase en rangos 2–3 en el que el cliente o el distribuidor declinaron la Carta Compromiso o la Reactivación. | Es la causal del rechazo por mantenimiento; se cita con la 11 literal. **No** se aplica por un desfase dentro de los rangos del Manual, ni por un desfase antiguo subsanado (8.4), ni sin comprobantes (se piden primero). |
| 14.4 documentación no aportada en 72 h | Requerimiento formal al distribuidor (comentario en SIGA con fecha) y 72 h transcurridas sin respuesta. | Sólo tras requerimiento formal; el técnico decide. Un comentario sin fecha de requerimiento no basta. |
| 14.5 comunicada fuera de vigencia | Fecha de comunicación posterior al fin de garantía. | Tajante: no se relaja (0.3). |
| 14.6 cualquier incumplimiento | — | **Nunca sola.** Sólo acompaña a una causal concreta. |

### 6.2 Operaciones no incluidas (Certificado 15, literal)

«No estarán cubiertas por la garantía objeto del certificado contratado, y por tanto GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., no estará obligada a reparar ni a realizar el pago de las siguientes:»
- **15.1** AVERÍA/AS y/o defectos previsibles, en el entendido de que se entenderá por avería o defecto previsible, aquellas que afecten a más de 50 vehículos de determinado modelo o que utilicen un mismo componente o que tengan una falla específica, ya sea por defectos de fabricación, ensamble y/o desgaste prematuro
- **15.2** AVERÍA/AS que sean consecuencia de una mala reparación anterior.
- **15.3** La sustitución, reparación, ajustes, reajustes o reparaciones de piezas realizados sobre piezas que hayan llegado al final de su vida útil como consecuencia de su función y usabilidad natural.
- **15.4** Los daños ocasionados por erosión, corrosión, deformación, oxidación, descomposición, herrumbre e incrustaciones, así como elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas, mangueras, retenes)
- **15.5** La sustitución de lubricantes y otros aditivos, bujías, bujías de encendido, filtros, cartuchos, aceites, juntas, carburantes, cargas de a/a, fugas de aceite, fugas de refrigerante o fugas de combustible, neumáticos, amortiguadores, discos de freno, pastillas de freno, correas de distribución, escapes, catalizadores, batería, plumas limpiaparabrisas, en definitiva, cualquier elemento consumible.
- **15.6** Las actualizaciones, programaciones o cargas de software de cualquier módulo electrónico del vehículo.
- **15.7** Los costos de diagnóstico cuando las averías no queden cubiertas por GarantiPLUS México S.A.P.I. de C.V.
- **15.8** AVERÍA/AS que se deriven del mal funcionamiento o falla de elementos no garantizados, o avería del motor originada por la falla de banda de distribución.
- **15.9** Las operaciones de mantenimiento periódicas, de carácter preventivo.
- **15.10** Los controles y/o reglajes, con o sin cambio de piezas.
- **15.11** Averías motivadas por defectos de serie, diseño defectuoso, vicios ocultos epidémicos, fallo epidémico, mismos que se entenderán como aquellas que afecten a más de 50 vehículos de determinado modelo o que utilicen un mismo componente o que tengan una falla específica, ya sea por defectos de fabricación, ensamble y/o desgaste prematuro., campañas del fabricante.
- **15.12** Cualquier daño sobre piezas garantizadas que se haya producido por la alteración o modificación de la especificación del fabricante.
- **15.13** Las AVERÍA/AS ocasionadas por seguir circulando cuando con los indicadores de avería, incidencia o alarma indiquen un mal funcionamiento.
- **15.14** Las AVERÍA/AS ocasionadas por mal uso o negligencia de utilización del vehículo por parte del propietario del titular del contrato.
- **15.15** Las AVERÍA/AS ocasionadas por el uso del vehículo en competiciones.
- **15.16** Las AVERÍA/AS ocasionadas por sobrecarga.
- **15.17** Las AVERÍA/AS ocasionadas por el uso de agentes abrasivos.
- **15.18** Las AVERÍA/AS ocasionadas por un accidente, robo, tentativa de robo, incendio, explosión, vandalismo o catástrofes naturales.
- **15.19** Las piezas que sean cambiadas en el momento de la reparación sin que hayan fallado.
- **15.20** Cualquier intervención efectuada “in situ” por cualquier servicio de asistencia en carretera.
- **15.21** Los servicios de grúa, remolque y gastos de transporte sobre el VEHÍCULO y ocupantes.
- **15.22** Averías producidas por combustibles o lubricantes no conformes con las indicaciones del fabricante o con alto grado de agua o contaminación de otros elementos químicos.
- **15.23** Sustitución, mantenimiento o reparación de accesorios o piezas no montados de origen, aun siendo elementos garantizados.
- **15.24** Ningún servicio de grúa.
- **15.25** Gastos de estacionamiento y/o almacenamiento del VEHÍCULO hasta su reparación.
- **15.26** Daños o pérdidas ocasionadas como consecuencia de la AVERÍA/AS o el retraso en su reparación.
- **15.27** Lucro cesante por no poder utilizar el VEHÍCULO.
- **15.28** Los daños a terceros que traigan causa en la AVERÍA/AS.

### 6.3 Exclusiones por causa de la póliza MMDM (literal en el Anexo B; aquí lo esencial)

- **ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE** («Algunos ejemplos incluyen, sin limitar»): no operar el vehículo según el Manual del Propietario; vehículo declarado pérdida total o salvamento; colisión, incendio, congelación, disturbios, explosiones u objetos que golpeen el vehículo; uso indebido (terracería, sobrepasar carga o pasajeros, correr, fuente de energía estacionaria); alteración (carrocería, chasis, frenos, software u otros); manipulación de emisiones, sistema eléctrico, red CAN; combustibles, fluidos o lubricantes contaminados o inadecuados; productos químicos aplicados por el propietario; daño a las vestiduras; vandalismo o robo.
- **DAÑO CAUSADO POR EL USO Y / O EL MEDIO AMBIENTE:** aire, sal, consecuencias industriales, piedras, productos químicos, riesgos viales, siniestros, lluvia ácida, granizo, savia, insectos, excrementos, rayo, arena, inundaciones.
- **DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO O FALTA DE SEGUIMIENTO DEL PROGRAMA DE MANTENIMIENTO RECOMENDADO:** «La reparación de daños, que se debe a que las piezas o servicios utilizados no fueron los que se prescriben en el programa de mantenimiento recomendado de este manual, no están cubiertos por la garantía. Es responsabilidad del propietario mantener el vehículo como se establece más detalladamente en el programa de mantenimiento descritos en este manual. Tenga en cuenta que la cobertura de la garantía puede ser denegada si no se sigue el mantenimiento de acuerdo con el programa el vehículo nuevo Mitsubishi.»
- **MODIFICACIONES:** piezas no originales; combustibles y fluidos no requeridos; neumáticos y ruedas de tamaño inadecuado; modificación de combustible, admisión, escape, emisión, suspensión, motor, tren de transmisión o cableado; reprogramación o chips en computadoras o módulos; reparaciones, actualizaciones y modificaciones no aprobadas; blindajes; accesorios no originales.
- **DAÑOS MENORES:** «Pequeñas irregularidades que no afectan la calidad, el rendimiento o la función del vehículo o sus partes (por ejemplo, un ruido leve o vibración) o que aparecen en particular solo en operaciones anormales.»
- **El Distribuidor de Mitsubishi Motors no está obligado a prestar el servicio de reparación en los siguientes casos:** vehículo no mantenido en buenas condiciones mecánicas según el manual; mantenimientos no realizados en un Distribuidor Mitsubishi Motors; falla imputable a una reparación del distribuidor dentro de los 30 días naturales (ésa se repara de nuevo sin costo); falla ocasionada por una reparación previa en talleres no autorizados; reparación no aprobada por el propietario; daños por una pieza no aprobada por MMDM instalada por alguien que no sea un distribuidor.
- **VEHÍCULOS CON ODÓMETRO ALTERADO:** «Si no se puede determinar o representar fielmente el kilometraje del vehículo por alteración o paro del odómetro.»
- **CAMBIOS DE PRODUCCIÓN; DAÑOS Y PERJUICIOS; CASO FORTUITO O FUERZA MAYOR:** Anexo B.

### 6.4 Qué evidencia hace falta para aplicar cada grupo (lectura flexible)

| Grupo | Causales | Evidencia que exige este contrato | Sin ella |
| --- | --- | --- | --- |
| **Desgaste o fin de vida útil** | 1.4 (reducción gradual), 10, 15.3; Póliza MMDM — DESGASTE, MANTENIMIENTO | Diagnóstico que describa el desgaste y su correspondencia con la antigüedad y el kilometraje (medidas, fotos del desgaste); kilometraje coherente con la vida útil esperada de la pieza. Antes de 140,000 KM, en componentes del listado Mitsubishi autorizado, el desgaste prematuro **no rechaza automáticamente** (`casos-mitsubishi.md` §5.2). | Avería cubierta (rotura prematura = defecto). |
| **Morfología, corrosión, deformación** | 2.9, 15.4; Póliza MMDM — CORROSIÓN | Foto o diagnóstico de la pieza que muestre la pérdida de morfología, corrosión o deformación **y** que la causa sea envejecimiento o agente externo, no un defecto. | Cubierta (5.3). |
| **Fugas** | 15.5 | Que la fuga sea la única falla y venga de una junta o retén consumible al final de su vida útil. Una fuga que sea el síntoma de un componente cubierto que falló (bomba de agua, retén de cigüeñal prematuro, radiador roto por defecto) **no** es 15.5. | Cubierta. |
| **Epidémico, campaña, defecto de serie** | 15.1, 15.11; Póliza MMDM — CAMBIOS DE PRODUCCIÓN | Constancia de MMDM o del área (boletín, campaña, comunicación formal) de que la falla afecta a más de 50 vehículos o es campaña. **Nunca por conjetura** del técnico o de Claude. Los casos especiales vigentes del área (bomba L200 MY25 en campaña de satisfacción) se **autorizan**, no se excluyen (`casos-mitsubishi.md` §5.3). | Cubierta. |
| **Daño externo, accidente, mal uso, negligencia, sobrecarga, competiciones, abrasivos** | 1.4 (influencias externas), 15.12–15.18; Póliza MMDM — ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE; DAÑO CAUSADO POR EL USO Y / O EL MEDIO AMBIENTE | Evidencia específica: fotos de impacto, deformación, objeto, rastro de manipulación, registro de siniestro, carga, uso en competición, abrasivo. «Una fotografía aislada de una pieza rota no sustituye el diagnóstico cuando existe posibilidad de golpe, manipulación, impacto o daño externo» (criterio del área): si cabe golpe y no hay evidencia, se **pide** el diagnóstico, no se rechaza. | Cubierta. |
| **Seguir circulando con testigo** | 15.13 | Constancia de que el testigo estaba encendido antes y el cliente siguió circulando (códigos con kilometraje de registro, declaración del cliente en el PRC, historial del distribuidor). | No se aplica. |
| **Combustible o lubricante contaminado** | 15.22; Póliza MMDM — ALTERACIÓN… | Análisis o evidencia del contaminante (agua en el tanque, muestra, lectura del distribuidor). | No se aplica. |
| **Modificaciones, accesorios no originales, software** | 15.6, 15.12, 15.23; Póliza MMDM — MODIFICACIONES | Constancia de la modificación o del accesorio y de su relación causal con la falla. | No se aplica. |
| **Mala reparación anterior** | 15.2; Póliza MMDM (reparación previa en talleres no autorizados) | Historial de la reparación anterior y diagnóstico que la relacione con la falla. Una reparación del propio distribuidor dentro de 30 días se repara sin costo (Póliza MMDM). | No se aplica. |
| **Ruidos, zumbidos, vibraciones** | 1.4 (la avería exige inutilidad operativa); **Póliza MMDM — DAÑOS MENORES** | Que el diagnóstico no identifique una pieza inutilizada ni un defecto: sólo el síntoma. Si el ruido viene de un componente que falló (rodamiento, soporte roto, junta homocinética), **es avería de ese componente** y se cubre. | Cubierta cuando hay componente fallado. |
| **Odómetro alterado o que retrocede** | **Póliza MMDM — VEHÍCULOS CON ODÓMETRO ALTERADO**; 14.3 por imposibilidad de verificar | Kilometraje que baja entre documentos sin explicación, odómetro parado. Se pide aclaración antes de rechazar. | No se aplica. |
| **Partidas nunca cubiertas** | 15.7, 15.9, 15.10, 15.19, 15.20, 15.21, 15.24, 15.25, 15.26, 15.27, 15.28 | — | Se descuentan de la valoración aunque la avería proceda; no rechazan la avería. |

### 6.5 Diagnóstico de una avería que no procede (15.7)

Los costos de diagnóstico sólo se pagan cuando la avería procede. En un rechazo, 15.7 se cita para cerrar la valoración en cero; en una aceptación parcial, el diagnóstico se paga con la parte que procede.

---

## 7. Obligaciones

### 7.1 Del contratante (Certificado 8, literal)

«El CONTRATANTE, en relación con el certificado contratado, tiene las siguientes obligaciones:»
- **8.1** Pagar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. el precio del certificado de garantía, y el I.V.A. correspondiente a dicho precio.
- **8.2** Con anterioridad a la venta del VEHÍCULO al BENEFICIARIO, deberá revisar el VEHÍCULO, y en caso de que el mismo tenga cualquier tipo de avería, tendrá la obligación de repararla antes de la venta.
- **8.3** El auto deberá de ser nuevo para poder ser objeto de contratación de garantía.

### 7.2 Del beneficiario (Certificado 9, literal)

«El BENEFICIARIO, en relación con el certificado contratado, tiene las siguientes obligaciones:»
- **9.1** Comunicar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. todas las AVERÍA/AS que tenga el VEHÍCULO durante el periodo de vigencia del certificado.
- **9.2** En caso de AVERÍA/AS, seguir estrictamente el PROCEDIMIENTO EN CASO DE AVERÍA/AS descrito en el punto 12 de este anexo.
- **9.3** Realizar en el VEHÍCULO los mantenimientos periódicos exigidos por el fabricante en tiempo y forma.
- **9.4** Conservar las facturas correspondientes a los trabajos o reparaciones de mantenimiento descritos en el apartado anterior.
- **9.5** Hacer un uso del VEHÍCULO razonable a las características del mismo.
- **9.6** En caso de AVERÍA/AS, no agravar la misma por un uso inadecuado o negligente del VEHÍCULO.

### 7.3 Del propietario según la póliza (Póliza MMDM — ORDEN DE REPARACIÓN DE GARANTÍA; INFORMACIÓN GENERAL)

- «Si el propietario debe realizar un servicio de garantía en este Vehículo, deberá de solicitar una copia de la orden de reparación del servicio de garantía realizada y deberá de conservarla.»
- «Así mismo, el propietario deberá de conservar documentación de los servicios de mantenimiento en caso de que surjan preguntas relacionadas con el mantenimiento. Estos deberán de incluir la fecha de servicio, kilometraje al tiempo del servicio y una descripción del servicio realizado y/o las partes instaladas.»
- «Estos documentos deben transferirse a cada propietario posterior de este Vehículo. MMDM se reserva el derecho de negar la cobertura de la garantía si el vehículo no se ha mantenido correctamente. **Sin embargo, la negación no se basará únicamente en la ausencia de registros de mantenimiento.**»
- «Para hacer efectiva esta garantía el propietario deberá presentar el vehículo y la póliza de garantías de vehículos nuevos Mitsubishi debidamente llenada y sellada por el distribuidor autorizado Mitsubishi de la República Mexicana.» (Póliza MMDM — CASO FORTUITO O FUERZA MAYOR, último párrafo).
- Mantener el vehículo en buenas condiciones mecánicas según el Manual del Propietario y realizar los servicios en un Distribuidor Mitsubishi Motors (Póliza MMDM, casos en que el distribuidor no está obligado; leído con 8.6).

**Lectura:** la obligación de mantener existe (9.3, 11, póliza) y su incumplimiento es causal (14.3), pero **la sola falta de registros no es incumplimiento**: se piden; si no llegan tras requerimiento formal, 14.4; si llegan y muestran un desfase, sección 8.

---

## 8. Mantenimientos

### 8.1 La obligación (Certificado 11, literal; Póliza MMDM — PRECAUCIONES DE SERVICIO)

- **Certificado 11 — MANTENIMIENTOS PERIÓDICOS:** «Para que el certificado contratado sea efectivo, el BENEFICIARIO se obliga a efectuar en el VEHÍCULO los trabajos o tareas de mantenimiento exigidas por el POR EL FABRICANTE SIGUIENDO SU PLAN DE MANTENIMIENTO PRECONIZADO, tanto en periodos de tiempo como en kilometraje.» (Es todo el texto: la 11 remite al plan del fabricante, que es el de la póliza.)
- **Póliza MMDM — Precauciones de servicio:** «Los servicios de inspección periódica designados en este manual son los requisitos mínimos que se deben realizar en un distribuidor de Mitsubishi Motors a fin de poder conservar la presente garantía.»
- **Póliza MMDM — Mantenimiento del sistema de control de emisiones:** «Los servicios de mantenimiento “programados” deben realizarse cada 6 (seis) meses o 10,000 (diez mil) kilómetros lo que pase primero para garantizar el funcionamiento correcto y continuo del sistema de control de emisiones. Estos y todos los demás servicios de mantenimiento incluidos en este documento, deben realizarse para proporcionar el mejor rendimiento y confiabilidad del vehículo.»
- «Para garantizar un rendimiento adecuado del control de emisiones, debe continuar con el mantenimiento programado más allá del período de 10 (diez) años mostrado, siguiendo el mismo patrón de programación de los primeros 10 (diez) años.» «La inspección y el servicio también deben realizarse siempre que se sospeche un mal funcionamiento.»

### 8.2 El intervalo

**Cada 10,000 km o 6 meses, lo que ocurra primero** (Póliza MMDM — Mantenimiento del sistema de control de emisiones; Registros de Mantenimiento: «10,000 km o 6 Meses … 200,000 km o 120 Meses»; coincide con el criterio del área del 27/10/2026). Es el intervalo base contra el que se mide cada tramo del historial.

**Plan de referencia salvo cuaderno de la unidad** (decisión del diseño, 28/10/2026): el programa transcrito en 8.3 es el del cuaderno de agosto de 2019. Si el expediente trae el cuaderno o la póliza de la unidad con otro intervalo u otras operaciones (otro año modelo, otro motor), **manda el de la unidad** y se dice. Un rótulo de factura («servicio de 20 mil») no es el plan.

### 8.3 Programa de mantenimiento recomendado (Póliza MMDM — PROGRAMA DE MANTENIMIENTO RECOMENDADO, S13–S20)

Leyenda del cuaderno: **I** = Inspección · **R** = Remplazo · **N/A** = No aplica · **\*** = Utilizar partes originales · **\*\*** = Según aplique · **R+** = Reemplazo para L200 · **(R)** = Solo por km · **(R+)** = Reemplazo por km para L200. Columnas: km × 1,000 (10 … 200) y meses (6 … 120); cada columna es un servicio.

**Mantenimiento de sistema de control de emisiones**

| Operación | 10/6 | 20/12 | 30/18 | 40/24 | 50/30 | 60/36 | 70/42 | 80/48 | 90/54 | 100/60 | 110–200 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Revisar el sistema de combustible para detectar fugas (tanque, tubería y conexión, y tapa del tubo de llenado del tanque de combustible) | | I | | I | | I | | I | | I | cada 20,000 |
| Revisar el sistema de control de emisiones por evaporación para detectar fugas y obstrucciones (excepto el canister) | | I | | I | | I | | I | | I | cada 20,000 |
| Reemplazar las bujías, tipo Convencional* | | R | | R | | R | | R | | R | cada 20,000 |
| Reemplazar las bujías, tipo 3 Electrodos* | | | | R | | | | R | | | 120, 160, 200 |
| Reemplazar las bujías de Platino e Iridio* | | | | | | | | | R+ | R | 180 (R+), 200 (R) |
| Inspeccionar que no existan ruidos extraños en los VVTi (compartimento de motor) | I | | I | | I | | I | | I | | cada 20,000 desde 110 |
| Reemplazar banda de tiempo L200 y Montero Sport (excepto vehículos con cadena de tiempo)** | | | | | | | | | | R | 200 |
| Comprobar el estado de las correas de transmisión (para el generador, la bomba de agua, y la bomba de dirección asistida**) | I | I | I | I | I | I | I | I | I | I | todos |
| Inspeccionar el cable de alto voltaje por daños y conexión apropiada (PHEV) | I | I | I | I | I | I | I | I | I | I | todos |
| Comprobar el nivel de refrigerante del motor trasero en el depósito, para PHEV también el motor delantero | I | I | I | I | I | I | I | I | I | I | todos |
| Comprobar el sistema de escape (parte de conexión del silenciador, los tubos del silenciador y las pantallas térmicas del convertidor) | I | I | I | I | I | I | I | I | I | I | todos |

**Mantenimiento general**

| Operación | Intervalo |
| --- | --- |
| Cambiar aceite de motor | **Cada 10,000 km o cada 6 meses** |
| Reemplazar filtro de aceite motor | **Cada 10,000 km o cada 6 meses** |
| Reemplazar el filtro de aire del compartimiento del motor | R en cada servicio (10 … 200) |
| Comprobar condición del nivel de aceite en Transmisión Manual y Automática** | I en cada servicio |
| Remplazar aceite de Transmisión Manual para L200 | I en cada servicio; (R) a 60,000, 120,000 y 180,000 km |
| Reemplazar el aceite de CVT dependiendo del modelo**: Outlander y Eclipse Cross cada 110 mil km; Mirage G3 y Mirage G4 cada 100 mil km | R a 100,000 (Mirage), 110,000 (Outlander, Eclipse Cross) y 200,000 |
| Reemplazar el filtro de aire (A/C) | R a 20, 40, 60, 80, 100 … (cada 20,000 km) |
| Comprobar nivel de aceite transferencia y condición (para vehículos con sistema de transferencia)** | I en cada servicio |
| Cambiar aceite transferencia (para vehículos con sistema de transferencia)** | I en cada servicio; (R+) a 60,000, 120,000 y 180,000 km |
| Inspeccionar condición de mangueras de refrigerante (mangueras de radiador, mangueras de calentador) | I en cada servicio |
| Cambiar refrigerante de motor | **Primeros 160,000 km o 5 años, luego cada 100,000 km** |
| Inspeccionar desgaste de balatas de freno de disco y rotores | I en cada servicio |
| Inspeccionar las balatas de los frenos del tambor trasero y los cilindros de las ruedas traseras en busca de desgaste y fugas en todas las ruedas | I en cada servicio |
| Remplazar el filtro de la bomba del motor a diésel* (Solo L200 Diesel) | R a 20, 40, 60, 80, 100 … (cada 20,000 km) |
| Remplazar el filtro de la bomba del motor a diésel* (Solo L200 Gasolina) | I en cada servicio; R a 60,000, 120,000 y 180,000 |
| Remplazar filtro de Gasolina (PHEV) | R a 60,000, 120,000 y 180,000 |
| Inspeccionar las mangueras de los frenos en busca de deterioro o fugas | I en cada servicio |
| Cambiar líquido de frenos | R a 50,000, 100,000, 150,000 y 200,000 km |

**Mantenimiento general último**

| Operación | Intervalo |
| --- | --- |
| Inspeccionar la junta de rótula y los sellos de la articulación de la dirección en busca de fugas de grasa y daños | I en cada servicio |
| Inspeccionar las fundas del eje de transmisión para detectar fugas de grasa y daños | I en cada servicio |
| Inspeccionar el sistema de suspensión por aflojamiento y daños | I en cada servicio |
| Comprobar funcionamiento de faros, direccionales, luz de freno y luces intermitentes | I en cada servicio |
| Comprobar funcionamiento de estéreo, luces interiores, aire acondicionado, tablero y techo panorámico | I en cada servicio |
| Lavado de unidad y motor (incluye desengrasante de motor) | Cada 10,000 km |
| Inspeccionar la fecha de vencimiento del sellador de reparación de neumáticos (vehículos con kit de reparación de neumáticos)** | Cada 12 meses |
| Rotar llantas | Cada 10,000 km |

**Prueba en carretera** (Póliza MMDM — Prueba en carretera): se incluye en la inspección periódica, después de los trabajos: juego libre del volante, efectividad del freno de servicio y de estacionamiento, manejabilidad del motor, instrumentos, medidores, indicadores, lámparas externas, calentadores y ventiladores.

**Registros de mantenimiento** (Póliza MMDM — REGISTROS DE MANTENIMIENTO): un recuadro por servicio, de «10,000 km o 6 Meses» a «200,000 km o 120 Meses», cada uno con Fecha, KM, OR (orden de reparación) y «Firma y sello Distribuidor». Un sello con esos cuatro datos acredita el servicio.

### 8.4 Desfases: los tres rangos de MMDM (Manual MMDM-MG-007-2025, literal) — decisión de Omar, 28/10/2026

«Políticas de garantía establecidas por MMDM para desfases en servicios de mantenimiento:»

- «Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de **1 a 1,000 kilómetros y/o de 1 a 31 días** respecto al plan de servicios de mantenimiento de MMDM, será considerado como **tolerancia en desfase** y la garantía procederá bajo este criterio en términos y condiciones de la garantía básica.»
- «Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de **1,001 a 2,000 kilómetros y/o de 32 a 62 días**, será considerado procedente por garantía bajo los términos y condiciones de **“Carta Compromiso”** la cual, deberá ser firmada por el cliente si es que acepta de conformidad los términos y condiciones estipulados en la misma. El formato de dicha carta ya se encuentra disponible y será distribuido por el área de garantías de MMDM bajo solicitud del distribuidor autorizado Mitsubishi Motors en México.»
- «Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de **2,001 a 6,000 kilómetros y/o de 63 a 186 días**, serán acreedores al programa **“Reactivación de Garantía”** definido en los siguientes puntos de este manual.»

Estos rangos **sustituyen** a la tolerancia de 1 mes / 1,000 KM del criterio del área del 27/10/2026 (que queda absorbida por el primer rango) y dan contenido a «en tiempo y forma» de la 9.3, la 11 y la 5.

**Tabla operativa**

| Desfase del tramo (km de más sobre 10,000 **o** días de más sobre 6 meses) | Rango | Tratamiento | Qué tiene que constar | Resultado del caso (si lo demás procede) |
| --- | --- | --- | --- | --- |
| 0 | En intervalo | Cumple | Comprobante del servicio | 🟢 |
| 1–1,000 km **o** 1–31 días | 1 · Tolerancia | «la garantía procederá … en términos y condiciones de la garantía básica» | Comprobante del servicio | 🟢 (sin carta ni trámite) |
| 1,001–2,000 km **o** 32–62 días | 2 · Carta Compromiso | Procede «bajo los términos y condiciones de “Carta Compromiso”» firmada por el cliente | La Carta Compromiso de **ese** VIN y **ese** desfase, firmada | 🟢 si la carta está en el expediente; 🟡 pidiéndola al distribuidor si no está (nunca 🔴 por falta de carta); 🔴 por 14.3 sólo si el cliente la declina expresamente |
| 2,001–6,000 km **o** 63–186 días | 3 · Reactivación | «acreedores al programa “Reactivación de Garantía”» (8.5) | Carta de Reactivación firmada + checklist aprobado + servicio de mantenimiento correspondiente (+ reacondicionamiento si aplica) | 🟢 cuando la reactivación consta (y la avería del folio se paga al **100 %**); 🟡 «candidato a Reactivación» mientras corre el proceso (el folio se queda en Validación con el comentario al distribuidor); 🔴 por 14.3 sólo si el distribuidor o el cliente declinan la reactivación, o si hay reincidencia acreditada |
| > 6,000 km **o** > 186 días | 4 · Fuera de rango | «Vehículos fuera del rango de desfase permitido» quedan excluidos del programa | — | 🔴 por 14.3 con la 11 (y la tabla en el Informe) |

**Cómo se mide** (decisión del diseño, coherente con la tabla del área): cada tramo va del servicio anterior al siguiente (o a la avería). **Exceso en km** = recorrido del tramo − 10,000. **Exceso en días** = días del tramo − los días que hay entre la fecha del servicio anterior y esa misma fecha seis meses de calendario después (no se asume que 6 meses sean 180 días). Se evalúan por separado; si los dos exceden, **el rango es el mayor de los dos** y se escriben ambos. Un servicio adelantado reinicia el tramo desde su fecha y su kilometraje.

**Qué tramo cuenta** (decisión de Omar, 28/10/2026): el rango se decide por el **tramo que llega a la avería** (último servicio acreditado → avería) y por los tramos inmediatos que expliquen la falla. Un desfase **antiguo** en rangos 1–3, seguido de servicios en intervalo, se considera **subsanado**: no se pide Carta Compromiso ni reactivación retroactivas ni rechaza. Sólo un tramo antiguo **de rango 4** (más de 6,000 km o 186 días) sigue siendo causal de 14.3, porque ahí el propio Manual no da salida.

**Reincidencia** (Manual, paso 10): «En el caso de reincidencia (nuevo desfase) no habrá tolerancia: La garantía del vehículo quedará cancelada.» Sólo cuenta si consta en el expediente (una Carta Compromiso o una reactivación anterior de ese VIN) o lo dice el técnico; sin esa fuente es un aviso al técnico, no un resultado (decisión del diseño).

### 8.5 Programa de Reactivación de Garantía (Manual MMDM-MG-007-2025; íntegro en el Anexo C)

**Objetivo:** «Establecer los lineamientos, criterios y pasos a seguir para la reactivación de garantía de los vehículos Mitsubishi Motors cuando el cliente haya incumplido en tiempo y forma con algún servicio de mantenimiento dentro de un margen tolerado.» Aplica a «Todos los distribuidores autorizados Mitsubishi Motors en México.»

**Aplica** «para los casos en los que, tras el diagnostico técnico, se determine la posibilidad de reactivar la garantía mediante el cumplimiento de los requisitos establecidos por MMDM y GarantiPlus de México.» **Quedan excluidos:** «Vehículos fuera del rango de desfase permitido. Componentes no cubiertos por contrato de garantía. Situaciones en las que no sea posible realizar reacondicionamiento conforme a las políticas técnicas del fabricante.»

**Los diez pasos:**

1. **Recepción del vehículo.** «El distribuidor recibe un vehículo con una anomalía reportada por el cliente.»
2. **Diagnóstico inicial.** «El técnico realiza el diagnostico para determinar si la anomalía/condición reportada es o no atribuible a garantía.»
3. **Verificación de vigencia.** El administrador de garantías revisa «Que el vehículo se encuentre dentro de los limites de tiempo y kilometraje con respecto a la garantía original. Si presenta desfase, analizar a cuál de las Políticas de garantía … aplica o si es acreedor al programa “Reactivación de garantía”.»
4. **Identificación del rango.** «Entre 2,001 y 6,000 Km y/o entre 63 y 186 días. Si el desfase está fuera de estos rangos, este programa no es aplicable.»
5. **Oferta de reactivación.** Se informa al cliente que puede reactivar su garantía si su vehículo cumple con: «Un checklist que incluye revisión técnica especializada. Se realice el servicio de mantenimiento correspondiente al kilometraje que tenga la unidad en el momento de acudir al distribuidor. Que el vehículo sea reacondicionado con base en los resultados del checklist (Si aplica).»
6. **Condiciones de reacondicionamiento.** «GarantiPlus México cubre el 50% del costo de reacondicionamiento, solo en componentes cubiertos por garantía. El cliente cubre: El 50% restante del reacondicionamiento. *Los componentes de desgaste no están cubiertos por garantía ni por contrato.»
7. **Precio público al cliente:** «Precio del servicio de mantenimiento correspondiente vigente (+) Aplicación de checklist $1,650 (+) Precio de reactivación de garantía $2,000 (+) 50% del precio de reacondicionamiento (si aplica) = Precio público a cliente. Todas las cantidades descritas son + IVA. Nota: El pago de $2,000+IVA correspondiente a la reactivación de garantía que el cliente paga al distribuidor y deberá ser pagado a su vez a GarantiPlus por parte del distribuidor.»
8. **Envío de solicitud a GarantiPlus.** «Enviar la solicitud de reactivación inmediatamente al socio comercial de GarantiPlus, INVARAT encargado de la “Evaluación Remota para Reactivación de Garantía” a los correos: rodolfo.maldonado@invarat.mx, david.simancas@garantiplus.mx. Con copia a: mario.luna@garantiplus.mx, Jose.vences@na.mitsubishi-motors.com, Alexys.gonzalez@na.mitsubishi-motors.com.» Incluir: «Los datos del vehículo (modelo, VIN, kilometraje, etc.) y motivo de la solicitud: “Revisión por posible Reactivación de garantía”; Evidencia técnica (checklist, diagnostico); Documentación del servicio y reacondicionamiento; Carta firmada por el cliente.» «Se agenda la evaluación técnica con Invarat.» (Los detalles de la evaluación remota están en el PDF «Condiciones Generales Para Realizar la Valuación», que no forma parte de este archivo.)
9. **Firma y conservación de la Carta de Reactivación.** «Si la unidad aprueba el checklist, el cliente firma la Carta de Reactivación y conserva una copia de la misma para futuras reclamaciones. Se reparan los componentes requeridos: GarantiPlus paga el 50% de las piezas cubiertas por garantía. El cliente paga su parte y el 100% de los componentes de desgaste. El distribuidor conserva el original de la Carta Compromiso firmada por el cliente en el expediente del vehículo, durante el periodo restante de garantía.»
10. **Reincidencias.** «En el caso de reincidencia (nuevo desfase) no habrá tolerancia: La garantía del vehículo quedará cancelada.»

**Cómo encaja con una avería en SIGA** (decisión de Omar, 28/10/2026):
- El **50/50** del Manual aplica al **reacondicionamiento** que salga del checklist (componentes que el checklist encuentre deteriorados), no a la avería que originó el folio.
- La **avería del folio**, una vez reactivada la garantía (carta firmada, checklist aprobado, servicio hecho), **se paga al 100 %** como avería normal, a MSRP −10 % (`casos-mitsubishi.md` §6).
- Mientras corre el proceso, **el folio se queda en Validación (🟡)** con el comentario al distribuidor que lo informa como candidato a reactivación (`casos-mitsubishi.md` §4.6); se cierra 🟢 cuando constan la carta y el servicio, o 🔴 por 14.3 si el distribuidor o el cliente declinan.

### 8.6 Qué cuenta como servicio y qué lo acredita

- **Un servicio** es una visita de mantenimiento del plan (8.3) con fecha y kilometraje: cambio de aceite y filtro y las inspecciones o reemplazos de esa columna. Un cambio de aceite y filtro con fecha y kilometraje cuenta como servicio para medir el intervalo (es la operación cardinal del plan; lectura del diseño, **pendiente de confirmar con Omar**); que faltaran operaciones de la columna no convierte el tramo en desfase, aunque pueda ser causa de una exclusión específica (Póliza MMDM — DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO…) si esa omisión produjo la falla y está probado.
- **Lo acredita** cualquiera de: factura con los datos de 12.3.d (taller, vehículo con marca, modelo, placa y kilómetros, trabajos desglosados, fecha y firma o sello, fecha de entrega); sello del cuaderno de registros con fecha, KM y OR; orden de reparación del distribuidor; historial de servicio del distribuidor o de MMDM; los servicios consignados en el PRC. Si un mismo servicio aparece en varios documentos, es uno (no se duplica); si dos fuentes dan fecha o km distintos para el mismo servicio, se enseñan los dos y decide el técnico.
- **Servicio en taller independiente** (decisión del diseño): la póliza MMDM condiciona *su* garantía y la transferencia a que el mantenimiento se haga «en un Distribuidor de Mitsubishi Motors»; el certificado de GarantiPlus **no** lo exige (9.3, 11 y 12.3.d hablan del fabricante y de facturas). Para este contrato, **una factura de taller independiente con los datos de 12.3.d acredita el servicio**; se dice en el veredicto que el servicio no fue en distribuidor, y el técnico decide si lo lleva a Alexys.
- **Sin ningún comprobante:** no es incumplimiento (7.3); se piden una vez con el comentario de `casos-mitsubishi.md` §4.5; si tras requerimiento formal no llegan en 72 h, 14.4 a decisión del técnico.
- **Inicio del historial:** la Fecha de inicio de la garantía con el kilometraje de entrega (normalmente 0 o el de la inspección antes de la entrega); si la póliza de SIGA trae otro kilometraje inicial, se enseña.
- **La avería como última fila:** la fecha de la avería (registro en SIGA o la de la orden de entrada) con el kilometraje de la avería; el tramo último servicio → avería se mide igual que los demás.

---

## 9. Procedimiento en caso de avería

### 9.1 Del certificado (Certificado 12, literal)

«En caso de AVERÍA/AS del VEHÍCULO, y para que la misma quede cubierta por el certificado contratado de garantía, se deberá seguir, obligatoriamente, el siguiente procedimiento:»

- **12.1** En cuanto tenga conocimiento de la AVERÍA/AS, el BENEFICIARIO comunicará la misma a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., por cualquiera de los siguientes medios: i) Por Teléfono. en el +52 (55) 3300 5925, y ii) Por correo electrónico, a la dirección averias@garantiplus.mx
- **12.2** En dicha comunicación el BENEFICIARIO deberá facilitar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., al menos, la siguiente información: i) Nº de Garantía Mecánica, ii) Placas del VEHÍCULO, iii) Declaración de la AVERÍA/AS, iv) Lugar en el que se ha producido la AVERÍA/AS y v) Taller en el que está el VEHÍCULO. En caso de que el VEHÍCULO no esté todavía en ningún taller, podrá solicitar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. que le indique un taller en el que dejar el VEHÍCULO.
- **12.3** Una vez el VEHÍCULO esté en un taller, el responsable del mismo volverá a contactar con GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., para describir la AVERÍA/AS, por los mismos medios descritos en la letra anterior, debiendo aportar igualmente la siguiente documentación: a. Orden de entrada del VEHÍCULO, que contenga, al menos, la fecha de entrada del mismo, los kilómetros del VEHÍCULO y descripción de la avería. b. Presupuesto aproximado de la reparación, QUE DEBERÁ REALIZARSE SIN INTERVENIR NI DESMONTAR EL VEHÍCULO. c. Copia del Libro de Mantenimiento del VEHÍCULO (Si dispone del mismo). d. Copia de las facturas de las inspecciones que indica GarantiPlus México, S.A.P.I DE C.V., en el VEHÍCULO. Dichas facturas, de conformidad con la normativa vigente, deberán tener el siguiente detalle: i. Identificación del taller: Nombre, Denominación Social, R.F.C., domicilio fiscal, domicilio a efectos de notificaciones, etc. ii. Identificación del VEHÍCULO con expresión de la marca, modelo, PLACA y número de kilómetros. iii. Reparaciones incluidas en la factura, desglosando las piezas sustituidas y la mano de obra empleada. iv. Fecha y firma o sello del taller. v. Fecha de entrega del VEHÍCULO.
- **12.4** Hasta que la reparación de la AVERÍA/AS no esté autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., no se podrá realizar en el mismo ningún tipo de desmontaje, montaje, reparación y/o intervención; a no ser que GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. lo requiera para poder determinar el origen de la avería. Cualquier autorización a trabajar sobre el vehículo para efectuar (pruebas, desmontajes, diagnosis, etc.) anterior a la aceptación de la avería parte de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., siempre tendrá que ser dada por el propietario del vehículo. El VEHÍCULO tendrá que permanecer inmovilizado hasta que GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., resuelva el expediente.
- **12.5** Una vez GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., haya recibido la documentación indicada en los apartados anteriores, GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., estudiará el asunto y decidirá sobre la necesidad de realizar un desmontaje para determinar la causa de la AVERÍA/AS. GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., se compromete a resolver por escrito y motivadamente el expediente , autorizando o rechazando la reparación de la avería en el plazo máximo de 48 horas (que no incluirán domingos ni festivos) a contar desde la recepción de la documentación o posterior al desmontaje en caso de existir. La resolución escrita del expediente a la que se hace referencia en este párrafo será remitida por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. al taller desde el que se remitió la documentación sobre la AVERÍA/AS. En caso de que no se siga el procedimiento señalado o la reparación de la Avería no se encuentre cubierta por el certificado contratado el costo del desmontaje, montaje y/o intervención serán cubiertos por el Cliente, el propietario del Vehículo o el Beneficiario.
- **12.6** En caso de que la reparación de la AVERÍA/AS sea aceptada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en la resolución por escrito del expediente se detallarán las reparaciones o trabajos que habrá que efectuar sobre el VEHÍCULO para la reparación de la AVERÍA/AS, así como la valoración de dichas actuaciones. En ningún caso GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. se hará cargo de trabajos o reparaciones no autorizadas en la resolución escrita del expediente.
- **12.7** Una vez autorizada la reparación del VEHÍCULO por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., el taller realizará las reparaciones autorizadas por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **12.8** Una vez reparado el VEHÍCULO por el taller, éste enviará a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. el original de la factura de reparación debidamente firmada por el BENEFICIARIO, que incluirá únicamente las reparaciones autorizadas por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., y que nunca podrá ser de un importe superior a la valoración de la reparación realizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en su informe de resolución del expediente. Junto con la factura, el taller deberá remitir a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., una copia firmada por el BENEFICIARIO del informe de resolución del expediente.
- **12.9** La factura de reparación emitida por el taller deberá estar a nombre de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. como destinatario de la misma. Calle Bosques de Duraznos 61 - piso 1 - Col. Bosques de las Lomas - Miguel Hidalgo. Ciudad de México - 11700 – México.
- **12.10** Una vez GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., haya recibida toda la documentación a la que se hace referencia en las letras anteriores, procederá al pago de la factura de reparación, en el plazo de 15 días recepción factura.
- **12.11** En el caso de que el presupuesto de reparación de la AVERÍA/AS realizado por el taller sea superior al valor de la reparación autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., el BENEFICIARIO podrá optar por: i) Llevar el VEHÍCULO al taller que le indique GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. para realizar la reparación tal como la misma haya sido autorizada en el informe de resolución del expediente, corriendo a costa del BENEFICIARIO todos los gastos de desplazamiento del VEHÍCULO, o ii)Reparar el VEHÍCULO según el presupuesto del taller. En este caso, el BENEFICIARIO deberá aceptar expresamente y por escrito que la diferencia entre el presupuesto dado por el taller y la valoración de la reparación de la AVERÍA/AS autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., correrá íntegramente a su cargo. En este caso, el taller deberá confeccionar dos facturas, una por un importe igual a la valoración de la reparación de la AVERÍA/AS autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., que deberá entregar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.; y otra, que deberá entregar al BENEFICIARIO, por la diferencia asumida por éste.
- **12.12** GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., se reserva el derecho a utilizar los medios de reparación que considere oportunos, así como el derecho a proporcionar las piezas que deban sustituirse o repararse en la reparación autorizada.

**Lectura flexible del procedimiento:** la comunicación se da por hecha con el registro de la avería en SIGA por el distribuidor (el distribuidor hace de taller y de enlace del beneficiario); el presupuesto «sin intervenir ni desmontar» se lee como en `casos-garantiplus.md` (un desmontaje para determinar el origen, requerido por GarantiPlus **y** autorizado por el propietario, no es 14.1; uno hecho por el taller por su cuenta, probado, sí lo es); el plazo de 48 horas de 12.5 obliga a GarantiPlus, no al distribuidor; las 72 h de 14.4 corren desde un requerimiento formal.

### 9.2 De la póliza (Póliza MMDM — PRESTACIÓN DEL SERVICIO LUGAR Y HORARIO; CASO FORTUITO O FUERZA MAYOR; LIMITE DE RESPONSABILIDAD)

- «Para obtener el servicio de garantía, el propietario debe de llevar su Vehículo a cualquier distribuidor de Mitsubishi Motors en la República Mexicana en días hábiles y en los horarios establecidos en donde se realizará este servicio sin cargo de mano de obra o partes.»
- «La petición de servicio que haga el propietario debe de ser atendía dentro de los 10 días naturales posteriores a la solicitud de servicio excepto por demoras ocasionadas por causas de fuerza mayor, caso fortuito, accidentes, motines, manifestaciones, guerra u otras que salgan de su control.»
- «El Distribuidor autorizado Mitsubishi no será responsable del vehículo en caso de que no haya sido reclamado por el propietario dentro de los 60(sesenta) días naturales posteriores de haberle notificado al propietario respecto a la entrega del vehículo reparado.»
- Reparación de garantía de 30 días: «Si el vehículo reparado presenta fallas imputables a la reparación realizada por el Distribuidor autorizado Mitsubishi dentro de los 30 (treinta días) naturales posteriores a la entrega del vehículo al propietario siempre que el vehículo no sea reparado por terceros este tendrá derecho a ser reparado de nuevo sin costo alguno respecto de la falla original.»
- «En caso de que las piezas o refacciones del vehículo no puedan ser reparadas. a juicio del Distribuidor Mitsubishi Motors, éstas deberán ser remplazadas por refacciones originales Mitsubishi.»

---

## 10. Límites y valoración

### 10.1 Límites del certificado (Certificado 13, literal)

- **13.1** «La valoración de la reparación de la AVERÍA/AS del VEHÍCULO nunca podrá superar el valor de venta del VEHÍCULO que marque el libro azul que es la guía que indica los precios del VEHÍCULO correspondiente al año de la venta. En caso de que la valoración de la reparación de la AVERÍA/AS supere el valor de venta del VEHÍCULO, GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. pagará al BENEFICIARIO con una cuantía igual a la menor de las cantidades siguientes: i) el Límite por AVERÍA/AS del certificado contratado, ii) el Límite del contrato o iii) el valor de venta del VEHÍCULO.»
- **13.2** «En caso de que el VEHÍCULO no esté en los boletines identificados en el párrafo anterior, el valor de venta del VEHÍCULO se calculará sobre la base del valor medio de mercado excluyendo del muestreo tanto el valor más bajo como el valor más elevado. Este cálculo será realizado por un evaluador libremente elegido por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., asumiendo ésta los costos de dicha valoración.»
- Hoja resumen: límite por avería y límite de contrato = **valor de venta del vehículo**. No hay deducible en el certificado; si la póliza de SIGA de la unidad lo trae, se aplica sólo conforme a ella.

### 10.2 Valoración

La refacción se autoriza a **MSRP −10 %** de la lista de precios mensual de Mitsubishi, sin IVA, con IVA desglosado y total con IVA; la mano de obra, la del presupuesto validado; reparación parcial antes que conjunto completo cuando es viable; nada de duplicidades ni consumibles de servicio. Todo en `casos-mitsubishi.md` §6 (criterio del área del 27/10/2026 y herramientas del conector). Refacciones originales Mitsubishi (Póliza MMDM — LIMITE DE RESPONSABILIDAD).

### 10.3 Daños y perjuicios (Póliza MMDM — DAÑOS Y PERJUICIOS; Certificado 15.26–15.28)

«Los daños por perjuicios derivados de cualquier falla del vehículo no están cubiertos por la presente garantía. Dichos daños y perjuicios incluyen de manera enunciativa mas no limitativa los siguientes: Gastos de Transportación; Pérdida económica de sueldos o ingresos; Pérdida de tiempo; Gastos de gasolina, viaje, alojamiento, alimentación, llamadas telefónicas; Perdida o el daño a la propiedad personal, pérdida de ingresos comerciales; Derivados de colisión causada o relacionada con fallas de cualquier componente cubierta por esta póliza.»

---

## 11. Devoluciones, avisos, rescisión, jurisdicción y datos

- **Certificado 16 — DEVOLUCIONES:** «En caso de rescisión anticipada del contrato por causas ajenas a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., ésta no estará obligada a la devolución del importe pagado por el contrato.»
- **Certificado 17 — AVISOS:** «Las partes acuerdan que en caso de que llegasen, por cualquier motivo, a mudarse del domicilio que indicaron en el certificado contratado, deberán hacérselo saber a la otra parte con 30 días naturales de anticipación a que efectuaren el cambio respectivo.»
- **Certificado 18 — RESCISIÓN:** «Serán causa de rescisión automática del certificado contratado el incumplimiento a cualquiera de las obligaciones establecidas en el certificado contratado.»
- **Póliza MMDM — TERMINACIÓN:** «La presente Póliza de Garantía se rescindirá automáticamente en el caso de que cualquiera de las partes incumpla con cualquiera de las obligaciones o condiciones a su cargo. La presente Póliza de Garantía podrá darse por terminada si existe fraude, dolo y/o mala fe por parte del propietario o se le requiera que lo haga por parte de la autoridad.»
- **Certificado 19 — SUMISIÓN EXPRESA** y **Póliza MMDM — LEYES Y JURISDICCIÓN APLICABLE:** Código de Comercio y Código Civil Federal; tribunales de la Ciudad de México; Ley Federal de Protección al Consumidor (textos íntegros en los Anexos).
- **Certificado 20 — PROTECCIÓN DE DATOS:** Ley Federal de Protección de Datos Personales en Posesión de los Particulares (texto íntegro en el Anexo A).
- **Lectura:** «rescisión automática por cualquier incumplimiento» (18; 14.6) **no se usa como causal de rechazo por sí sola**: cada rechazo cita la causal concreta (sección 6). Lo mismo para «fraude, dolo y/o mala fe», que exige prueba.

---

## 12. Tabla de correspondencia: tema → certificado → póliza MMDM → cómo se cita

| Tema | Certificado (numeral) | Póliza MMDM (sección del Anexo B) | Manual | En `generar_resolucion` |
| --- | --- | --- | --- | --- |
| Definición de avería | 1.4 | COBERTURAS DE GARANTÍA («defectuosas por calidad de producto o manufactura») | — | `clausulasLiterales` con numeral «1», título «DEFINICIONES», texto de 1.4 |
| Compromiso de pago / objeto | 1.5, 4.1 | COBERTURAS DE GARANTÍA | — | `numerales: ["4.1"]`; 1.5 literal |
| Componentes excluidos | 2.1–2.9 | PARTES CON GARANTIA DIRECTA DEL FABRICANTE; CONSUMIBLES Y LUBRICANTES; MANTENIMIENTO | — | `numerales: ["2.8"]` etc.; sección MMDM por literal |
| Partes cubiertas (lista) | 1.5, 3 | PARTES CUBIERTAS | — | Literal con título «PARTES CUBIERTAS» si hace falta fundar una aceptación discutida |
| PHEV | 3.1, 3.2 | PARTES CUBIERTAS (batería alto voltaje; componentes eléctricos) | — | `numerales: ["3.1"]` |
| Duración, vigencia | 5.1, 5.2, 14.5 | COBERTURAS DE GARANTÍA (7 años; subgarantías) | — | `numerales: ["5.1", "14.5"]`; subgarantías por literal |
| Transferencia | — | COBERTURAS DE GARANTÍA; CESIÓN | — | Literal |
| Territorio | 7.1 | PRESTACIÓN DEL SERVICIO LUGAR Y HORARIO | — | `numerales: ["7.1"]` |
| Obligaciones del beneficiario | 9.1–9.6 | ORDEN DE REPARACIÓN DE GARANTÍA; INFORMACIÓN GENERAL | — | `numerales: ["9.3"]`; «la negación no se basará únicamente…» por literal |
| Desgaste normal, uso inadecuado | 10, 15.3 | DESGASTE; MANTENIMIENTO | — | `clausulasLiterales` numeral «10», título «OBLIGACIONES DE GARANTIPLUS»; `numerales: ["15.3"]` |
| Mantenimientos: obligación | 11, 9.3, 9.4 | MANTENIMIENTO DE SU VEHÍCULO (Precauciones de servicio; Mantenimiento del sistema de control de emisiones) | — | `clausulasLiterales` numeral «11», título «MANTENIMIENTOS PERIÓDICOS» |
| Mantenimientos: incumplimiento | 14.3 (14.4) | DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO O FALTA DE SEGUIMIENTO DEL PROGRAMA DE MANTENIMIENTO RECOMENDADO | Rangos 1–4; reactivación | `numerales: ["14.3"]` + 11 literal; la sección MMDM por literal si se quiere reforzar; el Manual en `desarrollo` |
| Procedimiento, desmontaje, inmovilizado | 12.1–12.12, 14.1, 14.2 | PRESTACIÓN DEL SERVICIO (10 días, 60 días, 30 días) | — | `numerales: ["14.1", "12.4"]` |
| Documentación no aportada | 14.4 | ORDEN DE REPARACIÓN DE GARANTÍA | — | `numerales: ["14.4"]` |
| Daño externo, accidente, mal uso | 1.4, 15.12–15.18 | ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE; DAÑO CAUSADO POR EL USO Y / O EL MEDIO AMBIENTE | — | `numerales: ["15.18"]` etc. |
| Modificaciones, accesorios, software | 15.6, 15.12, 15.23 | MODIFICACIONES; ACTUALIZACIONES | — | `numerales` |
| Epidémico, campañas | 15.1, 15.11 | CAMBIOS DE PRODUCCIÓN | — | Sólo con constancia; `numerales: ["15.11"]` |
| Ruidos, vibraciones | 1.4 (inutilidad operativa) | DAÑOS MENORES | — | 1.4 literal + `clausulasLiterales` numeral «Póliza MMDM», título «DAÑOS MENORES» |
| Odómetro alterado | — (14.3 por imposibilidad de verificar) | VEHÍCULOS CON ODÓMETRO ALTERADO | — | `clausulasLiterales` numeral «Póliza MMDM», título «VEHÍCULOS CON ODÓMETRO ALTERADO» |
| Mala reparación anterior | 15.2 | (casos en que el distribuidor no está obligado) | — | `numerales: ["15.2"]` |
| Límites, libro azul | 13.1, 13.2 | LIMITE DE RESPONSABILIDAD | — | `numerales: ["13.1"]` |
| Partidas nunca cubiertas | 15.7, 15.9, 15.10, 15.19–15.21, 15.24–15.28 | DAÑOS Y PERJUICIOS | — | `numerales: ["15.7"]` |
| Desfase de mantenimiento, carta, reactivación | 11, 14.3 | — | Rangos; pasos 1–10 | Chat y `desarrollo`: «conforme al Programa de Reactivación de Garantía de MMDM (MMDM-MG-007-2025)» |

---

## Anexo A · Certificado GARANTÍA REAL 7 (GarantiPlus México, febrero 2019), texto íntegro

Transcrito de `CERTIFICADO FEBRERO. 2019.pdf` (páginas 1–11; las 12–31 son el anexo de VIN y no se transcriben). Los ítems de cada sección llevan aquí su numeral **por posición (S.N)**, que es como se citan en el Informe (`numerales: ["14.3"]` = sección 14, ítem 3). Las secciones de un solo párrafo (4, 5, 6, 7, 10, 11) se citan como `4.1`, `5.1`/`5.2`, `6.1`, `7.1`, `10.1`, `11.1`, que es como las resuelve el conector; la 10 y la 11 se mandan además completas en `clausulasLiterales`, como pide `casos-mitsubishi.md`. El texto es literal, incluidas erratas del original. Cada página del original lleva el membrete «GARANTIPLUS MÉXICO, S.A.P.I DE C.V. · R.F.C. GME160927DW0 · Av. Presidente Masaryk Nº 111 – Piso 1 · Col. Chapultepec Morales. Ciudad de México · 11560 – México · Email: info@garantiplus.mx · CONTRATO DE GARANTÍA MECANICA SUSCRITO CON GARANTIPLUS MÉXICO» y el recuadro DATOS GENERALES (Fecha de Contrato 24/06/2019 · Limite por Avería: Valor Venta Vehículo · Producto Contratado: GARANTÍA REAL 7 · Límite de Contrato: Valor Venta Vehículo), y el pie «Leído y Conforme Vendedor · Leído y Conforme Comprador · GarantiPlus México».

### HOJA RESUMEN DEL CONTRATO DE GARANTÍA MECÁNICA

VEHÍCULO OBJETO DE CONTRATO: MARCA: MITSUBISHI · NUMERO DE SERIE (VIN): ANEXA A ESTE CONTRATO. *Los datos introducidos tendrán que coincidir fehacientemente con los del vehículo objeto de garantía. En caso de error será motivo de rescisión del contrato.

CONTRATANTE DEL CONTRATO – DISTRIBUIDOR: PUNTO DE VENTA: MITSUBISHI MOTORS DE MEXICO SA DE CV · R.F.C.: MMM1711282H8.

PERIODO DE VIGENCIA DEL CONTRATO: FECHA INICIO GARANTIA: ANEXA AL CONTRATO · FECHA FIN GARANTIA: ANEXA AL CONTRATO.

Siempre que se hayan realizado en el VEHÍCULO en tiempo y forma los servicios y mantenimientos; el PERIODO DE VIGENCIA DEL CONTRATO podrá comenzar a computarse hasta el momento en que expire la garantía del fabricante o alguna otra garantía de similar naturaleza, ya sea por sobrepasar el kilometraje o cumplirse el tiempo establecido en la misma. En cualquier caso, la Garantía Mecánica de GarantiPlus México, S.A.P.I. de C.V. será válida conforme a los términos y condiciones del presente Contrato.

ANEXO A ESTE CONTRATO*: AL FINAL DEL CONTRATO SE ANEXA EL LISTADO DE VINES GARANTIZADOS, INDICANDO EN CADA UNO DE ELLOS EL INICIO Y EL FIN DE GARANTÍA.

### 1.- DEFINICIONES:

- **1.1** CONTRATANTE: Tendrá la consideración de CONTRATANTE del contrato el vendedor del VEHÍCULO, que será el obligado al pago del precio del certificado contratado de garantía mecánica.
- **1.2** BENEFICIARIO: Tendrá la consideración de BENEFICIARIO el comprador del VEHÍCULO, quien será el destinatario de la garantía mecánica objeto del certificado contratado.
- **1.3** VEHÍCULO: A los efectos del certificado contratado, tendrá la consideración de VEHÍCULO únicamente el descrito en la HOJA RESUMEN DEL CONTRATO DE GARANTÍA MECÁNICA que, en todo caso, no podrá tener más de 450 C.V. de potencia o tener denominación industrial ya sea ligera o pesada.
- **1.4** AVERÍA/AS: Se entiende por avería mecánica, eléctrica, o electrónica, la inutilidad operativa (conforme a las especificaciones del fabricante) de la pieza garantizada, debido a una rotura imprevista / fortuita. No se incluye en esta definición la reducción gradual en el rendimiento operativo de la pieza garantizada que sea proporcional y equivalente a su antigüedad y kilometraje (se entiende a partir de la primera matriculación del vehículo, y no a partir del inicio del contrato de garantía), ni las averías derivadas de accidentes o cualesquiera influencias externas.
- **1.5** Mediante este contrato de Garantía GarantiPlus México se compromete a pagar los costos razonables de reparación de una avería cubierta relativa al vehículo garantizado, dentro de los límites de pago por avería y condiciones del mismo. Quedan cubiertas por el certificado contratado la reparación o sustitución de todas las piezas o componentes que presenten defectos como consecuencia de una avería fortuita en los elementos mecánicos, eléctricos o electrónicos.

### 2.- EXCLUSIONES:

Se excluyen de manera expresa los siguientes elementos:
- **2.1** Asientos completos y mecanismos (mecánicos)
- **2.2** Elementos internos del habitáculo y/o maletero (tapizados, guarnecidos, reposabrazos, salpicadero, consolas, soportes, tapas, aireadores, ceniceros, encendedor, lámparas)
- **2.3** Neumáticos, válvula de rueda (con o sin sensor)
- **2.4** Totalidad de los elementos de carrocería
- **2.5** Totalidad de cristales y lunas, incluida térmica
- **2.6** Faros, intermitentes, calaveras, lámparas
- **2.7** Molduras, embellecedores, espejos retrovisores completos, paragolpes
- **2.8** Consumibles (filtros, cartuchos, aceite, juntas), amortiguadores, escapes, discos de freno, pastillas, correas, servicio periódico, servicios intermedios, lubricantes, combustibles, aditivos, carga de circuito de a/a (salvo que sea necesario por avería cubierta), bujías, calentadores, batería, escobillas, plumas limpiaparabrisas
- **2.9** Elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas).

### 3.- COBERTURA PARA VEHÍCULOS PHEV

- **3.1** BATERÍA DE MANEJO ALTO VOLTAJE (para vehículo PHEV únicamente). a. La batería de la unidad equipada originalmente está garantizada para los primeros 7 AÑOS sin límite de kilómetros, a partir de la fecha de inicio de la garantía. b. La pérdida gradual de la retención de carga de la batería debido al tiempo y el uso NO está cubierta por esta GARANTÍA. c. Consulte el Manual del propietario para obtener más información sobre la pérdida de capacidad de la batería.
- **3.2** COMPONENTES ELECTRICOS (para vehículo PHEV únicamente). a. Los componentes Eléctricos (PHEV) equipados originalmente están garantizados para los primeros 7 AÑOS sin límite de kilómetros, a partir de la fecha de inicio de la garantía. b. COMPONENTES Eléctricos (PHEV) incluyen los siguientes: i. Motor eléctrico. ii. Motor eléctrico del sistema de refrigeración iii. Líneas de alta tensión. iv. Conexión regular de carga v. Inversor - PHEV-ECU vi. Conexión de carga rápida vii. Trans eje viii. Cargador a bordo /Convertidor DC-DC

### 4.- OBJETO DEL CERTIFICADO

- **4.1** GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. garantiza, dentro de los límites fijados en el presente documento, el pago de la reparación de las AVERÍA/AS.

### 5.- DURACIÓN DEL CERTIFICADO

- **5.1** El periodo de garantía cubierto por el certificado de garantía contratado será el indicado en el mismo. Por tanto, sólo estarán cubiertas las AVERÍA/AS que tenga el VEHÍCULO durante la vigencia del contrato.
- **5.2** Siempre que se hayan realizado en el VEHÍCULO en tiempo y forma los servicios y mantenimientos señalados.

### 6.- PERFECCIÓN Y EFECTOS DEL CERTIFICADO.

- **6.1** El certificado contratado se perfecciona por el consentimiento manifestado con la firma del mismo documento.

### 7.- DELIMITACIONES GEOGRÁFICAS

- **7.1** La garantía objeto del certificado contratado se extiende y limita a las AVERÍA/AS que tengan lugar dentro de la República Mexicana.

### 8.- OBLIGACIONES DEL CONTRATANTE

El CONTRATANTE, en relación con el certificado contratado, tiene las siguientes obligaciones:
- **8.1** Pagar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. el precio del certificado de garantía, y el I.V.A. correspondiente a dicho precio.
- **8.2** Con anterioridad a la venta del VEHÍCULO al BENEFICIARIO, deberá revisar el VEHÍCULO, y en caso de que el mismo tenga cualquier tipo de avería, tendrá la obligación de repararla antes de la venta.
- **8.3** El auto deberá de ser nuevo para poder ser objeto de contratación de garantía.

### 9.- OBLIGACIONES DEL BENEFICIARIO

El BENEFICIARIO, en relación con el certificado contratado, tiene las siguientes obligaciones:
- **9.1** Comunicar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. todas las AVERÍA/AS que tenga el VEHÍCULO durante el periodo de vigencia del certificado.
- **9.2** En caso de AVERÍA/AS, seguir estrictamente el PROCEDIMIENTO EN CASO DE AVERÍA/AS descrito en el punto 12 de este anexo.
- **9.3** Realizar en el VEHÍCULO los mantenimientos periódicos exigidos por el fabricante en tiempo y forma.
- **9.4** Conservar las facturas correspondientes a los trabajos o reparaciones de mantenimiento descritos en el apartado anterior.
- **9.5** Hacer un uso del VEHÍCULO razonable a las características del mismo.
- **9.6** En caso de AVERÍA/AS, no agravar la misma por un uso inadecuado o negligente del VEHÍCULO.

### 10.- OBLIGACIONES DE GARANTIPLUS

- **10.1** GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en relación con el certificado contratado, tiene la obligación de, en los términos y con los límites fijados en el mismo, hacerse cargo de la reparación de las AVERÍA/AS cubiertas, que dentro del periodo de vigencia del certificado pueda tener el VEHÍCULO, siempre y cuando dichas AVERÍAS no traigan causa en un uso inadecuado del VEHÍCULO, o en el deterioro y/o desgaste normal del mismo.

### 11.- MANTENIMIENTOS PERIÓDICOS

- **11.1** Para que el certificado contratado sea efectivo, el BENEFICIARIO se obliga a efectuar en el VEHÍCULO los trabajos o tareas de mantenimiento exigidas por el POR EL FABRICANTE SIGUIENDO SU PLAN DE MANTENIMIENTO PRECONIZADO, tanto en periodos de tiempo como en kilometraje.

### 12.- PROCEDIMIENTO EN CASO DE AVERÍA/AS

En caso de AVERÍA/AS del VEHÍCULO, y para que la misma quede cubierta por el certificado contratado de garantía, se deberá seguir, obligatoriamente, el siguiente procedimiento:
- **12.1** En cuanto tenga conocimiento de la AVERÍA/AS, el BENEFICIARIO comunicará la misma a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., por cualquiera de los siguientes medios: i) Por Teléfono. en el +52 (55) 3300 5925, y ii) Por correo electrónico, a la dirección averias@garantiplus.mx
- **12.2** En dicha comunicación el BENEFICIARIO deberá facilitar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., al menos, la siguiente información: i) Nº de Garantía Mecánica, ii) Placas del VEHÍCULO, iii) Declaración de la AVERÍA/AS, iv) Lugar en el que se ha producido la AVERÍA/AS y v) Taller en el que está el VEHÍCULO. En caso de que el VEHÍCULO no esté todavía en ningún taller, podrá solicitar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. que le indique un taller en el que dejar el VEHÍCULO.
- **12.3** Una vez el VEHÍCULO esté en un taller, el responsable del mismo volverá a contactar con GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., para describir la AVERÍA/AS, por los mismos medios descritos en la letra anterior, debiendo aportar igualmente la siguiente documentación: a. Orden de entrada del VEHÍCULO, que contenga, al menos, la fecha de entrada del mismo, los kilómetros del VEHÍCULO y descripción de la avería. b. Presupuesto aproximado de la reparación, QUE DEBERÁ REALIZARSE SIN INTERVENIR NI DESMONTAR EL VEHÍCULO. c. Copia del Libro de Mantenimiento del VEHÍCULO (Si dispone del mismo). d. Copia de las facturas de las inspecciones que indica GarantiPlus México, S.A.P.I DE C.V., en el VEHÍCULO. Dichas facturas, de conformidad con la normativa vigente, deberán tener el siguiente detalle: i. Identificación del taller: Nombre, Denominación Social, R.F.C., domicilio fiscal, domicilio a efectos de notificaciones, etc. ii. Identificación del VEHÍCULO con expresión de la marca, modelo, PLACA y número de kilómetros. iii. Reparaciones incluidas en la factura, desglosando las piezas sustituidas y la mano de obra empleada. iv. Fecha y firma o sello del taller. v. Fecha de entrega del VEHÍCULO.
- **12.4** Hasta que la reparación de la AVERÍA/AS no esté autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., no se podrá realizar en el mismo ningún tipo de desmontaje, montaje, reparación y/o intervención; a no ser que GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. lo requiera para poder determinar el origen de la avería. Cualquier autorización a trabajar sobre el vehículo para efectuar (pruebas, desmontajes, diagnosis, etc.) anterior a la aceptación de la avería parte de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., siempre tendrá que ser dada por el propietario del vehículo. El VEHÍCULO tendrá que permanecer inmovilizado hasta que GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., resuelva el expediente.
- **12.5** Una vez GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., haya recibido la documentación indicada en los apartados anteriores, GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., estudiará el asunto y decidirá sobre la necesidad de realizar un desmontaje para determinar la causa de la AVERÍA/AS. GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., se compromete a resolver por escrito y motivadamente el expediente , autorizando o rechazando la reparación de la avería en el plazo máximo de 48 horas (que no incluirán domingos ni festivos) a contar desde la recepción de la documentación o posterior al desmontaje en caso de existir. La resolución escrita del expediente a la que se hace referencia en este párrafo será remitida por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. al taller desde el que se remitió la documentación sobre la AVERÍA/AS. En caso de que no se siga el procedimiento señalado o la reparación de la Avería no se encuentre cubierta por el certificado contratado el costo del desmontaje, montaje y/o intervención serán cubiertos por el Cliente, el propietario del Vehículo o el Beneficiario.
- **12.6** En caso de que la reparación de la AVERÍA/AS sea aceptada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en la resolución por escrito del expediente se detallarán las reparaciones o trabajos que habrá que efectuar sobre el VEHÍCULO para la reparación de la AVERÍA/AS, así como la valoración de dichas actuaciones. En ningún caso GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. se hará cargo de trabajos o reparaciones no autorizadas en la resolución escrita del expediente.
- **12.7** Una vez autorizada la reparación del VEHÍCULO por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., el taller realizará las reparaciones autorizadas por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **12.8** Una vez reparado el VEHÍCULO por el taller, éste enviará a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. el original de la factura de reparación debidamente firmada por el BENEFICIARIO, que incluirá únicamente las reparaciones autorizadas por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., y que nunca podrá ser de un importe superior a la valoración de la reparación realizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en su informe de resolución del expediente. Junto con la factura, el taller deberá remitir a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., una copia firmada por el BENEFICIARIO del informe de resolución del expediente.
- **12.9** La factura de reparación emitida por el taller deberá estar a nombre de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. como destinatario de la misma. Calle Bosques de Duraznos 61 - piso 1 - Col. Bosques de las Lomas - Miguel Hidalgo. Ciudad de México - 11700 – México.
- **12.10** Una vez GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., haya recibida toda la documentación a la que se hace referencia en las letras anteriores, procederá al pago de la factura de reparación, en el plazo de 15 días recepción factura.
- **12.11** En el caso de que el presupuesto de reparación de la AVERÍA/AS realizado por el taller sea superior al valor de la reparación autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., el BENEFICIARIO podrá optar por: i) Llevar el VEHÍCULO al taller que le indique GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. para realizar la reparación tal como la misma haya sido autorizada en el informe de resolución del expediente, corriendo a costa del BENEFICIARIO todos los gastos de desplazamiento del VEHÍCULO, o ii)Reparar el VEHÍCULO según el presupuesto del taller. En este caso, el BENEFICIARIO deberá aceptar expresamente y por escrito que la diferencia entre el presupuesto dado por el taller y la valoración de la reparación de la AVERÍA/AS autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., correrá íntegramente a su cargo. En este caso, el taller deberá confeccionar dos facturas, una por un importe igual a la valoración de la reparación de la AVERÍA/AS autorizada por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., que deberá entregar a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.; y otra, que deberá entregar al BENEFICIARIO, por la diferencia asumida por éste.
- **12.12** GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., se reserva el derecho a utilizar los medios de reparación que considere oportunos, así como el derecho a proporcionar las piezas que deban sustituirse o repararse en la reparación autorizada.

### 13.- LÍMITES DEL CERTIFICADO

- **13.1** La valoración de la reparación de la AVERÍA/AS del VEHÍCULO nunca podrá superar el valor de venta del VEHÍCULO que marque el libro azul que es la guía que indica los precios del VEHÍCULO correspondiente al año de la venta. En caso de que la valoración de la reparación de la AVERÍA/AS supere el valor de venta del VEHÍCULO, GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. pagará al BENEFICIARIO con una cuantía igual a la menor de las cantidades siguientes: i) el Límite por AVERÍA/AS del certificado contratado, ii) el Límite del contrato o iii) el valor de venta del VEHÍCULO.
- **13.2** En caso de que el VEHÍCULO no esté en los boletines identificados en el párrafo anterior, el valor de venta del VEHÍCULO se calculará sobre la base del valor medio de mercado excluyendo del muestreo tanto el valor más bajo como el valor más elevado. Este cálculo será realizado por un evaluador libremente elegido por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., asumiendo ésta los costos de dicha valoración.

### 14. EXCLUSIONES GENERALES DEL CONTRATO

GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. podrá rechazar la reparación, y/o en su caso el pago de la AVERÍA/AS en los siguientes supuestos:
- **14.1** Cuando se haya realizado cualquier tipo de trabajo sobre el VEHÍCULO antes de la resolución del expediente por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **14.2** Cuando el VEHÍCULO no haya permanecido inmovilizado en el taller desde la comunicación de la AVERÍA/AS hasta la resolución del expediente por GARANTIPLUS MÉXICO, S.A.P.I. DE C.V.
- **14.3** Cuando el BENEFICIARIO no haya cumplido sus obligaciones en relación con los mantenimientos e inspecciones exigidas en el certificado contratado.
- **14.4** Cuando las facturas correspondientes a los mantenimientos periódicos o cualquier documentación exigida dentro del Articulo 12.-PROCEDIMIENTO EN CASO DE AVERÍAS/AS del certificado contratado, no estén debidamente cumplimentadas, o directamente no se aporten a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., en un plazo de 72h tras ser requeridas.
- **14.5** Cuando la AVERÍA/AS haya sido comunicada a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., transcurrido el plazo de duración del contrato, aun cuando la AVERÍA/AS haya acontecido con anterioridad a su expiración
- **14.6** Cuando haya habido cualquier tipo de incumplimiento por parte del CONTRATANTE o del BENEFICIARIO.

### 15.- OPERACIONES NO INCLUIDAS EN LA GARANTÍA

No estarán cubiertas por la garantía objeto del certificado contratado, y por tanto GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., no estará obligada a reparar ni a realizar el pago de las siguientes:
- **15.1** AVERÍA/AS y/o defectos previsibles, en el entendido de que se entenderá por avería o defecto previsible, aquellas que afecten a más de 50 vehículos de determinado modelo o que utilicen un mismo componente o que tengan una falla específica, ya sea por defectos de fabricación, ensamble y/o desgaste prematuro
- **15.2** AVERÍA/AS que sean consecuencia de una mala reparación anterior.
- **15.3** La sustitución, reparación, ajustes, reajustes o reparaciones de piezas realizados sobre piezas que hayan llegado al final de su vida útil como consecuencia de su función y usabilidad natural.
- **15.4** Los daños ocasionados por erosión, corrosión, deformación, oxidación, descomposición, herrumbre e incrustaciones, así como elementos que hayan perdido su morfología inicial (bujes, gomas, soportes, juntas, mangueras, retenes)
- **15.5** La sustitución de lubricantes y otros aditivos, bujías, bujías de encendido, filtros, cartuchos, aceites, juntas, carburantes, cargas de a/a, fugas de aceite, fugas de refrigerante o fugas de combustible, neumáticos, amortiguadores, discos de freno, pastillas de freno, correas de distribución, escapes, catalizadores, batería, plumas limpiaparabrisas, en definitiva, cualquier elemento consumible.
- **15.6** Las actualizaciones, programaciones o cargas de software de cualquier módulo electrónico del vehículo.
- **15.7** Los costos de diagnóstico cuando las averías no queden cubiertas por GarantiPLUS México S.A.P.I. de C.V.
- **15.8** AVERÍA/AS que se deriven del mal funcionamiento o falla de elementos no garantizados, o avería del motor originada por la falla de banda de distribución.
- **15.9** Las operaciones de mantenimiento periódicas, de carácter preventivo.
- **15.10** Los controles y/o reglajes, con o sin cambio de piezas.
- **15.11** Averías motivadas por defectos de serie, diseño defectuoso, vicios ocultos epidémicos, fallo epidémico, mismos que se entenderán como aquellas que afecten a más de 50 vehículos de determinado modelo o que utilicen un mismo componente o que tengan una falla específica, ya sea por defectos de fabricación, ensamble y/o desgaste prematuro., campañas del fabricante.
- **15.12** Cualquier daño sobre piezas garantizadas que se haya producido por la alteración o modificación de la especificación del fabricante.
- **15.13** Las AVERÍA/AS ocasionadas por seguir circulando cuando con los indicadores de avería, incidencia o alarma indiquen un mal funcionamiento.
- **15.14** Las AVERÍA/AS ocasionadas por mal uso o negligencia de utilización del vehículo por parte del propietario del titular del contrato.
- **15.15** Las AVERÍA/AS ocasionadas por el uso del vehículo en competiciones.
- **15.16** Las AVERÍA/AS ocasionadas por sobrecarga.
- **15.17** Las AVERÍA/AS ocasionadas por el uso de agentes abrasivos.
- **15.18** Las AVERÍA/AS ocasionadas por un accidente, robo, tentativa de robo, incendio, explosión, vandalismo o catástrofes naturales.
- **15.19** Las piezas que sean cambiadas en el momento de la reparación sin que hayan fallado.
- **15.20** Cualquier intervención efectuada “in situ” por cualquier servicio de asistencia en carretera.
- **15.21** Los servicios de grúa, remolque y gastos de transporte sobre el VEHÍCULO y ocupantes.
- **15.22** Averías producidas por combustibles o lubricantes no conformes con las indicaciones del fabricante o con alto grado de agua o contaminación de otros elementos químicos.
- **15.23** Sustitución, mantenimiento o reparación de accesorios o piezas no montados de origen, aun siendo elementos garantizados.
- **15.24** Ningún servicio de grúa.
- **15.25** Gastos de estacionamiento y/o almacenamiento del VEHÍCULO hasta su reparación.
- **15.26** Daños o pérdidas ocasionadas como consecuencia de la AVERÍA/AS o el retraso en su reparación.
- **15.27** Lucro cesante por no poder utilizar el VEHÍCULO.
- **15.28** Los daños a terceros que traigan causa en la AVERÍA/AS.

### 16.- DEVOLUCIONES

En caso de rescisión anticipada del contrato por causas ajenas a GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., ésta no estará obligada a la devolución del importe pagado por el contrato.

### 17.- AVISOS

Las partes acuerdan que en caso de que llegasen, por cualquier motivo, a mudarse del domicilio que indicaron en el certificado contratado, deberán hacérselo saber a la otra parte con 30 días naturales de anticipación a que efectuaren el cambio respectivo.

### 18.- RESCISIÓN:

Serán causa de rescisión automática del certificado contratado el incumplimiento a cualquiera de las obligaciones establecidas en el certificado contratado.

### 19.- SUMISIÓN EXPRESA:

LA LEGISLACION APLICABLE, DE LA JURISDICCION Y DE LOS TRIBUNALES COMPETENTES: Siendo el certificado contratado de naturaleza mercantil, las partes convienen que para todo lo no previsto en él, se sujetarán a lo dispuesto en el Código de Comercio o en su defecto por lo dispuesto por el Código Civil Federal, así mismo para el conocimiento de cualquier controversia que llegare a suscitarse con motivo de la interpretación del certificado contratado, las partes se someten a la jurisdicción de los Tribunales de la Ciudad de México, renunciando expresamente al fuero que pudiera corresponderles, en razón de sus domicilios presentes o futuros o bien, por cualquier otra causa. Manifestando el proveedor que en el certificado contratado no existen prestaciones desproporcionadas, inequitativas o abusivas, o cualquier otra cláusula o texto que viole las disposiciones de la Ley Federal de Protección al Consumidor, las Normas Oficiales Mexicanas y demás ordenamientos aplicables. Los Derechos y obligaciones como Cliente se rigen por las cláusulas del certificado contratado y en los términos señalados por la Ley Federal de Protección al Consumidor.

### 20.- PROTECCIÓN DE DATOS:

Con fundamento en la Ley Federal de Protección de datos Personales en Posesión de los Particulares, publicada en el Diario Oficial de la Federación el día 05 de Julio de 2010, los datos personales proporcionados entre las partes, en este acto serán tratados conforme a lo estipulado por la Ley antes señalada, los cuales no podrán ser transferidos a persona alguna, pero en cumplimiento de los ordenamientos legales, la información será guardada en el archivo correspondiente a cada una de las partes así como en la documentación adjunta y será proporcionada exclusivamente a las Autoridades que deban conocer del certificado contratado celebrado entre las partes.
La información y archivos son propiedad exclusiva de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., extendiéndose también esta titularidad a cuantas elaboraciones, evaluaciones, segmentaciones o procesos similares que, en relación con los mismos, realice, GARANTIPLUS MÉXICO, S.A.P.I. DE C.V., de acuerdo con los servicios que se pactan en el certificado contratado, declarando las partes que esta información es confidencial para todos los efectos, sujetos en consecuencia al más estricto secreto profesional, incluso una vez finalizada la presente relación contractual.
Leído que fue el presente contrato, así como enteradas las partes de su contenido y alcances legales, lo firman por duplicado.

### 21.- Anexo de la póliza de garantías

Listado de VIN garantizados con el inicio y el fin de garantía de cada uno (páginas 12–31 del PDF; no se transcribe).

---

## Anexo B · Póliza de Garantía Limitada de Vehículo Nuevo Mitsubishi y Cuaderno de Mantenimiento (MMDM, agosto 2019), texto por secciones

Transcrito de `Service-Warranty-Booklet.pdf` (48 páginas; «Service-Warranty-Booklet-es-mx.book», 21 de agosto de 2019). Los encabezados son los del cuaderno, en mayúsculas tal como aparecen: son los `titulo` que se usan en `clausulasLiterales` con `numeral: "Póliza MMDM"`. Las tablas del PROGRAMA DE MANTENIMIENTO RECOMENDADO (S13–S20) están transcritas en la sección 8.3 de este documento; los formatos de registro (informes de propietario, inspección antes de la entrega, registros de mantenimiento) se describen sin reproducir los campos vacíos.

Portada: «Todos los derechos reservados a Mitsubishi Motors De México, S.A. de C.V. (en adelante “MMDM”). La reproducción de la “Póliza de Garantías y Cuaderno de Mantenimiento” por cualquier medio electrónico o mecánico, así como el almacenamiento y recuperación de la información incluidos fotocopia, grabación, la traducción total o parcial no están permitidas sin la autorización escrita de MMDM.»

### INFORME DE REGISTRO (PRIMER, SEGUNDO Y TERCER PROPIETARIO)

Formatos para el uso del distribuidor y para el cliente con: Propietario, Firma, Dirección, Fecha de inicio, Fecha de terminación, Modelo del vehículo, Número de chasis, Número de motor, Número de licencia, Número de distribuidor, Nombre de distribuidor, Distribuidor, Firma, Sello.

### INSPECCIÓN ANTES DE LA ENTREGA

Formato con Propietario, Nombre y Firma, Fecha, Kilometraje, Distribuidor, Dirección, Modelo del vehículo, Número de chasis, Número de motor, Firma y Sello. «El distribuidor debe de mantener esta tarjeta en el historial del vehículo.»

### INTRODUCCIÓN

Su vehículo ha sido fabricado con los mejores materiales, con las últimas técnicas de ingeniería de automóviles y los métodos más avanzados de control de calidad, (en adelante el “vehículo”).

MMDM espera que disfrute su vehículo en los siguientes años y desea su satisfacción total por ello, lo invitamos a visitar un concesionario autorizado de Mitsubishi Motors en adelante “Distribuidor de Mitsubishi Motors” para todos sus servicios tanto, durante, como después del período de garantía.

LA SATISFACCIÓN DEL PROPIETARIO. En MMDM, estamos orgullosos de la calidad y de la mano de obra que está incorporada en cada vehículo y de nuestro compromiso corporativo de promover la satisfacción del propietario con nuestros productos y servicios.

Para garantizar el rendimiento continuo y la vida útil prolongada de su vehículo, MMDM le otorga una garantía generosa que se explica en la garantía limitada del fabricante y en un plan de mantenimiento completo para el cuidado de su vehículo a través de su distribuidor de Mitsubishi Motors.

El distribuidor Mitsubishi Motors que venda el vehículo debe llenar el registro del propietario y los servicios de mantenimiento para que el propietario reciba el servicio de acuerdo con la Garantía limitada del fabricante MMDM.

Póngase en contacto con el distribuidor de Mitsubishi Motors más cercano: Esta es la forma más directa y conveniente de obtener servicio. Los distribuidores de Mitsubishi Motors tienen la responsabilidad de proporcionar el servicio y las reparaciones que pueda necesitar. Le recomendamos que se ponga en contacto con el Asesor de servicio del Distribuidor de Mitsubishi Motors de su elección para obtener ayuda.

Puede también comunicarse a través del Centro de Contacto Mitsubishi al 01800 63 64878 (01800 63 MITSU). Asegúrese de tener su número de identificación de vehículo de 17 caracteres (VIN) disponible cuando llame. El VIN se puede encontrar en la esquina superior del tablero de instrumentos en el lado del conductor del vehículo y en el registro de su vehículo. El Centro de Contacto Mitsubishi estará preparado para investigar su inquietud y brindarle asistencia.

### PÓLIZA DE GARANTÍA LIMITADA DE VEHÍCULO NUEVO MITSUBISHI (en adelante "Garantía")

La presente garantía es otorgada por MMDM, una sociedad mercantil debidamente constituida conforme las leyes de la república mexicana con escritura N-2017100943, que se encuentra inscrita al Registro Federal de Contribuyente No. MMM1711282H8 con domicilio en Torre Omega Piso 7 OF 702-B, Calle Campos Elíseos No ext. 345 Colonia Polanco Chapultepec, Localidad Miguel Hidalgo C.P. 11560.

La garantía se otorga al propietario original o propietarios subsecuentes del Vehículo, en su caso, por el periodo restante de garantía.

La presente Póliza de Garantía deberá permanecer en su Vehículo y entregarse al nuevo propietario en caso de reventa.

Durante el plazo especificado en la presente garantía, MMDM, pagará directamente al distribuidor de Mitsubishi Motors la reparación de garantía cubierta en términos de lo dispuesto en esta póliza.

MMDM otorga al propietario original o subsecuente del vehículo registrado y operado normalmente en la República Mexicana a través de sus Distribuidores de Mitsubishi Motors, los servicios de reparaciones de garantía de partes en las que se demuestre que están defectuosas por calidad de producto o manufactura dentro del período de garantía aplicable a dichas partes, la cual será reparada o reemplazada sin costo alguno para el cliente por un distribuidor Mitsubishi Motors cumpliendo con la norma oficial mexicana respectiva y durante la vigencia especificada en la presente póliza, siempre y cuando se haya realizado el mantenimiento correcto y no aplique alguna de las exclusiones descritas más adelante.

### COBERTURA Y EXCLUSIONES DE GARANTÍA

#### COBERTURAS DE GARANTÍA

La cobertura de la Garantía de Vehículo será transferida automáticamente sin costo alguno, a los propietarios subsecuentes del vehículo, siempre que el mantenimiento requerido sea realizado por un Distribuidor de Mitsubishi Motors dentro de los límites de tiempo y kilometraje especificados en el manual del propietario y el de servicio.

MMDM garantiza que el Vehículo se encuentra protegido en términos generales por defectos de fabrica por calidad de materiales o mano de obra por un plazo de 7 (siete) años sin límite de kilometraje defensa a defensa*, contados a partir de la fecha de facturación del vehículo como se establece en el Registro del primer propietario de esta póliza (en adelante, “Fecha de inicio de la garantía") o puesta en marcha lo que ocurra primero.

Los paneles metálicos están garantizados por corrosión por 5 (cinco) años o 60,000 (sesenta mil) Kilómetros a partir de la fecha de inicio de la garantía.

La batería auxiliar (12 volts) de equipo original está garantizada por 24 (veinticuatro) meses a partir de la fecha de inicio de la garantía.

* Para el Smart Display Audio o Display Audio (estéreo) se encuentra protegido en términos generales por defectos de fabrica por calidad de materiales o mano de obra por un plazo de 3 (tres) años o 60,000 (sesenta mil) kilómetros lo que ocurra primero.

#### PARTES CUBIERTAS

COMPONENTES DE TREN MOTRIZ — MOTOR: Bloque de cilindros y todas piezas lubricadas internas incluyendo: Cigüeñal y rodamientos principales; Banda de Distribución y piezas relacionadas; Ejes de balancines; Conjuntos de cabeza de cilindro; Soportes del motor; Volante o placa de mando (incluido el engranaje de anillo); Bomba de combustible (s); Múltiple de admisión y escape; Válvulas de Admisión y escape; Bomba de aceite; Cubiertas de válvula y juntas de cubierta de válvula; Bomba de agua; Turbocompresor; Juntas y sellos de todos los componentes anteriores.

TRANSEJE / TRANSMISIÓN Y CAJA DE TRANSFERENCIA: Convertidor de par (incluido el engranaje de anillo); Caja de transeje y todas las piezas lubricadas internas, juntas y sellos; Soportes de transmisión, transmisión y caja de transferencia y todas las piezas lubricadas internas, juntas y sellos; Caja de transmisión y todas las piezas lubricadas internas, juntas y sellos.

OTROS COMPONENTES DE TREN MOTRIZ: Carcasa del eje y todas las piezas lubricadas internas, juntas y sellos; Cojinetes del eje; Ensamblajes de diferenciales y todas las piezas lubricadas internas, juntas y sellos; Conjuntos de eje de transmisión y eje de dirección (incluidas juntas de velocidad constante); Ensambles de propelas de eje y yugos (incluidas juntas de velocidad constante y / o juntas universales); Rodamientos centrales del eje de la propela.

BATERÍA DE MANEJO ALTO VOLTAJE (para vehículo PHEV únicamente): La batería del vehículo de equipo original está garantizada. La pérdida gradual de la retención de carga de la batería debido al tiempo y el uso NO está cubierta por esta GARANTÍA. Consulte el Manual del propietario para obtener más información sobre la pérdida de capacidad de la batería.

COMPONENTES ELÉCTRICOS (para vehículo PHEV únicamente): Los siguientes componentes eléctricos de equipo original del vehículo PHEV están garantizados: Motor eléctrico; Motor eléctrico del sistema de refrigeración; Líneas de alta tensión; Conexión regular de carga; Inversor - PHEV-ECU; Conexión de carga rápida; Transeje; Cargador a bordo / Convertidor DC-DC.

#### PARTES CON GARANTIA DIRECTA DEL FABRICANTE

Las partes que se enlistan a continuación no están cubiertas por la garantía de MMDM, la garantía la cubrirá directamente el fabricante de las partes: Neumáticos; Estéreos; Todas las partes que no sean instaladas originalmente en el vehículo nuevo.

#### PARTES Y SERVICIOS NO CUBIERTOS (EXCEPCIONES)

##### CONSUMIBLES Y LUBRICANTES

Algunos ejemplos incluyen, sin limitar:

CONSUMIBLES: Elemento del filtro de aire; Elemento de filtro de aceite; Elemento filtro de combustible; Correas de transmisión; Bujía (excluyendo Platino o Iridio tipo de enchufe con punta); Plato del embrague, pastillas de freno y forro de freno; Plumilla y mecanismo de Limpiaparabrisas; Fusible; Foco (excepto faros de haz sellado, halógeno y de descarga); Otras piezas consumibles.

LUBRICANTES: Aceite de motor; Aceite de transmisión manual; Fluido de transmisión automática; Fluido de frenos y embrague; Grasa; Refrigerante del motor; Aceite del engranaje diferencial; Aceite y / o Fluido de engranaje de dirección; Aceite para engranajes de transferencia; Batería electrolítica; Refrigerante; Líquido para lavaparabrisas; Combustible.

##### ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE

Algunos ejemplos incluyen, sin limitar: No operar el vehículo de acuerdo con el Manual del Propietario; Cualquier vehículo declarado como pérdida total y / o transferido como salvamento, debido a un accidente, inundación u otro evento catastrófico; Colisión, incendio, congelación, disturbios, explosiones u objetos que golpeen su vehículo; Uso indebido de su vehículo, como, por ejemplo, conducir sobre terracería, sobrepasar el límite de carga y/o pasajeros de acuerdo con las especificaciones del vehículo, correr o usar su vehículo como fuente de energía estacionaria; Alteración de su vehículo, que incluye, entre otros, la carrocería, el chasis, el sistema de frenos, la programación de software u otros componentes; Manipulación o alteración de los sistemas de control de emisiones, sistema eléctrico red CAN u otras partes que afectan a estos sistemas; Uso de combustibles, fluidos o lubricantes contaminados o inadecuados; Daño debido a productos químicos aplicados por el propietario (por ejemplo: ceras abrasivas, abrillantadores, selladores, etc.); Daño a las vestiduras; Vandalismo o robo.

##### DAÑO CAUSADO POR EL USO Y / O EL MEDIO AMBIENTE

Algunos ejemplos incluyen sin limitar: Las consecuencias del aire; Sal; Las consecuencias industriales; Piedras; Productos químicos; Riesgos viales; Siniestros; Lluvia ácida; Granizo; Savia de árbol; Insectos; Excrementos de pájaros; Rayo (descarga eléctrica); Arena; Inundaciones.

##### DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO O FALTA DE SEGUIMIENTO DEL PROGRAMA DE MANTENIMIENTO RECOMENDADO

La reparación de daños, que se debe a que las piezas o servicios utilizados no fueron los que se prescriben en el programa de mantenimiento recomendado de este manual, no están cubiertos por la garantía. Es responsabilidad del propietario mantener el vehículo como se establece más detalladamente en el programa de mantenimiento descritos en este manual. Tenga en cuenta que la cobertura de la garantía puede ser denegada si no se sigue el mantenimiento de acuerdo con el programa el vehículo nuevo Mitsubishi.

##### MODIFICACIONES

Los daños o problemas de desempeño que resulten de las modificaciones de su vehículo no están cubiertos por la garantía. Ejemplos de modificaciones al vehículo que pueden causar daños o problemas de rendimiento incluyen sin limitar, los siguientes: Falta de uso de piezas originales de Mitsubishi Motors; No usar los combustibles y fluidos requeridos; No usar neumáticos y ruedas del tamaño adecuado; Modificación de los sistemas de combustible, admisión, escape, emisión, suspensión, motor, tren de transmisión o cableado eléctrico; Modificación de cualquier computadora de a bordo / módulo de control, incluida la reprogramación, o reemplazo / adición de chips a cualquier computadora de a bordo / módulo de control; Las reparaciones, actualizaciones y modificaciones no aprobadas y / o incompatibles de su vehículo no están cubiertas por esta garantía, ni las reparaciones necesarias para corregir daños subsecuentes causados por dichas reparaciones; Blindajes; Instalación de accesorios no originales.

##### MANTENIMIENTO / DESGASTE / ACTUALIZACIONES

MANTENIMIENTO. Las piezas y la mano de obra necesarias para mantener el vehículo y el reemplazo de las piezas debido al desgaste normal no están cubiertos por la garantía y son responsabilidad del propietario. Algunos ejemplos incluyen, sin limitar: Alineación de neumáticos; Balatas / disco de freno desgastados; Limpieza y pulido; Revestimientos del disco del embrague desgastados; Afinaciones del motor; Lubricación (aceite, lubricante o refrigerante de motor, transmisión, frenos o embrague, diferencial, dirección, caja de transferencia, limpiaparabrisas); Reemplazo de filtros de aire o aceite, refrigerantes o fusibles; Reemplazo de bujías de encendido; Plumillas del limpiaparabrisas desgastadas; Banda / Cadena de tiempo; Correas de transmisión; Amortiguadores desgastados; Revisiones en general; Daños causados por una reparación o mantenimiento insuficientes o inadecuados (por ejemplo, negligencia en los servicios periódicos de inspección y mantenimiento descritos en esta póliza de garantías y cuaderno de mantenimiento del vehículo); Las piezas y el material utilizados en relación con dicho servicio (como se describe y especifica en “Su plan de servicio del vehículo” en esta póliza de garantías y cuaderno de mantenimiento).

ACTUALIZACIONES. Actualizaciones de software y mapas para sistemas de navegación (dichas actualizaciones se consideran un gasto cuya responsabilidad es del propietario); Las actualizaciones de hardware o software necesarias para admitir y / o conectar su Vehículo con dispositivos no suministrados por Mitsubishi Motors (como, por ejemplo, teléfonos celulares, reproductores de música, tabletas, computadoras portátiles y otras fuentes de audio, video y datos).

##### PINTURA Y OTROS ELEMENTOS DE APARIENCIA

Informe a su distribuidor autorizado de Mitsubishi Motors sin demora si identifica alguna imperfección en acabado de pintura, molduras u otros elementos de apariencia, ya que el deterioro normal debido al uso y la exposición no está cubierto por esta garantía ejemplo desprendimiento o corrosión de pintura debía a impactos.

##### CORROSIÓN

Corrosión debido a un accidente, daño, abuso, uso anormal, alteración del vehículo o falta de mantenimiento adecuado de este vehículo; Corrosión a consecuencia de la abrasión de la superficie, causada por residuos industriales, arena, sal, granizo y piedras; Corrosión debido al transporte prolongado y / o anormal de materiales corrosivos como productos químicos, ácidos, fertilizantes.

##### DESGASTE

Desgaste normal de cualquier parte, deterioro normal, decoloración, astillado, envejecimiento o daños en las piezas enchapadas, pintura, piezas de caucho, tapicería, cuero sintético y acabados suaves causados por el uso diario, el desgaste y la exposición del vehículo al medio ambiente.

##### DAÑOS MENORES

Pequeñas irregularidades que no afectan la calidad, el rendimiento o la función del vehículo o sus partes (por ejemplo, un ruido leve o vibración) o que aparecen en particular solo en operaciones anormales.

El Distribuidor de Mitsubishi Motors no está obligado a prestar el servicio de reparación en los siguientes casos: Cuando el vehículo no sea mantenido en buenas condiciones mecánicas de acuerdo con las instrucciones y recomendaciones del fabricante estipuladas en el manual del propietario; Cuando el propietario no realice los servicios de mantenimiento en un Distribuidor Mitsubishi Motors estipulados en la póliza de garantías y cuaderno de mantenimiento expedido por el fabricante del vehículo; Si el vehículo reparado presenta fallas imputables a la reparación realizada por el Distribuidor autorizado Mitsubishi dentro de los 30 (treinta días) naturales posteriores a la entrega del vehículo al propietario siempre que el vehículo no sea reparado por terceros este tendrá derecho a ser reparado de nuevo sin costo alguno respecto de la falla original; Si la falla que presenta el vehículo es ocasionada por una reparación previa en talleres no autorizados por MMDM; Si la reparación no es aprobada por el propietario del vehículo.

Daños causados por el uso de una pieza no aprobada por MMDM y que sea reparada o reemplazada por cualquier persona o entidad que no sea un Distribuidor de Mitsubishi Motors.

##### CAMBIOS DE PRODUCCIÓN

MMDM y sus distribuidores de Mitsubishi Motors se reservan el derecho de realizar cambios en los vehículos vendidos por ellos en cualquier momento sin incurrir en ninguna obligación de realizar cambios iguales o similares en los vehículos vendidos previamente por ellos.

##### VEHÍCULOS CON ODÓMETRO ALTERADO

Si no se puede determinar o representar fielmente el kilometraje del vehículo por alteración o paro del odómetro.

#### LIMITE DE RESPONSABILIDAD

En caso de que las piezas o refacciones del vehículo no puedan ser reparadas. a juicio del Distribuidor Mitsubishi Motors, éstas deberán ser remplazadas por refacciones originales Mitsubishi.

#### PRESTACIÓN DEL SERVICIO LUGAR Y HORARIO

Para obtener el servicio de garantía, el propietario debe de llevar su Vehículo a cualquier distribuidor de Mitsubishi Motors en la República Mexicana en días hábiles y en los horarios establecidos en donde se realizará este servicio sin cargo de mano de obra o partes.

El Distribuidor autorizado Mitsubishi no será responsable del vehículo en caso de que no haya sido reclamado por el propietario dentro de los 60(sesenta) días naturales posteriores de haberle notificado al propietario respecto a la entrega del vehículo reparado.

El servicio de garantía no aplica si las reparaciones fueron realizadas por terceros o distribuidores Mitsubishi fuera de la República Mexicana.

#### CASO FORTUITO O FUERZA MAYOR

La petición de servicio que haga el propietario debe de ser atendía dentro de los 10 días naturales posteriores a la solicitud de servicio excepto por demoras ocasionadas por causas de fuerza mayor, caso fortuito, accidentes, motines, manifestaciones, guerra u otras que salgan de su control.

El Distribuidor Mitsubishi no será responsable por cualquier retraso o incumplimiento que resulte directa o indirectamente por caso fortuito o fuerza mayor, en la inteligencia de que una vez superado estos eventos, se reanudará la prestación de los servicios objeto de la presente póliza de garantías.

Para hacer efectiva esta garantía el propietario deberá presentar el vehículo y la póliza de garantías de vehículos nuevos Mitsubishi debidamente llenada y sellada por el distribuidor autorizado Mitsubishi de la República Mexicana.

#### DAÑOS Y PERJUICIOS

Los daños por perjuicios derivados de cualquier falla del vehículo no están cubiertos por la presente garantía. Dichos daños y perjuicios incluyen de manera enunciativa mas no limitativa los siguientes: Gastos de Transportación; Pérdida económica de sueldos o ingresos; Pérdida de tiempo; Gastos de gasolina, viaje, alojamiento, alimentación, llamadas telefónicas; Perdida o el daño a la propiedad personal, pérdida de ingresos comerciales; Derivados de colisión causada o relacionada con fallas de cualquier componente cubierta por esta póliza.

#### CESIÓN

Los derechos que otorga esta póliza de garantías solo aplicarán para los vehículos descritos en el adverso de este documento y no podrán ser transferidos bajo ninguna circunstancia a otro vehículo.

La presente Póliza de Garantía podrá ser transferible a otra persona sin necesidad de aprobación por el distribuidor Mitsubishi a propietarios subsecuentes del vehículo.

#### TERMINACIÓN

La presente Póliza de Garantía se rescindirá automáticamente en el caso de que cualquiera de las partes incumpla con cualquiera de las obligaciones o condiciones a su cargo.

La presente Póliza de Garantía podrá darse por terminada si existe fraude, dolo y/o mala fe por parte del propietario o se le requiera que lo haga por parte de la autoridad.

### INFORMACIÓN GENERAL

#### LEYES Y JURISDICCIÓN APLICABLE

En caso de que surgiera alguna controversia sobre la interpretación, ejecución y cumplimiento de esta póliza de garantía, las partes se someten a las leyes y jurisdicción de los tribunales competentes de la Ciudad de México, renunciando a cualquier otro fuero que pudiera corresponderles por sus domicilios presentes o futuros o por cualquier otra causa.

Sus derechos y obligaciones como Propietario están sujetos a las cláusulas de la presente póliza de garantías y amparados en los términos señalados en la ley federal de protección al consumidor.

#### ORDEN DE REPARACIÓN DE GARANTÍA

Si el propietario debe realizar un servicio de garantía en este Vehículo, deberá de solicitar una copia de la orden de reparación del servicio de garantía realizada y deberá de conservarla.

Así mismo, el propietario deberá de conservar documentación de los servicios de mantenimiento en caso de que surjan preguntas relacionadas con el mantenimiento. Estos deberán de incluir la fecha de servicio, kilometraje al tiempo del servicio y una descripción del servicio realizado y/o las partes instaladas.

Estos documentos deben transferirse a cada propietario posterior de este Vehículo. MMDM se reserva el derecho de negar la cobertura de la garantía si el vehículo no se ha mantenido correctamente. Sin embargo, la negación no se basará únicamente en la ausencia de registros de mantenimiento.

### MANTENIMIENTO DE SU VEHÍCULO

Servicio de inspección previa a la entrega. Para obtener la máxima satisfacción de su nuevo vehículo un distribuidor de Mitsubishi Motors ha inspeccionado y preparado el vehículo de acuerdo con el programa de mantenimiento recomendado por MMDM.

Precauciones de servicio. El servicio de mantenimiento e inspección adecuada del vehículo son indispensables para una conducción segura y un menor costo total de funcionamiento. Los servicios de inspección periódica designados en este manual son los requisitos mínimos que se deben realizar en un distribuidor de Mitsubishi Motors a fin de poder conservar la presente garantía. La inspección y el servicio también deben realizarse siempre que se sospeche un mal funcionamiento. Para garantizar un rendimiento adecuado del control de emisiones, debe continuar con el mantenimiento programado más allá del período de 10 (diez) años mostrado, siguiendo el mismo patrón de programación de los primeros 10 (diez) años.

Mantenimiento del sistema de control de emisiones. Los servicios de mantenimiento “programados” deben realizarse cada 6 (seis) meses o 10,000 (diez mil) kilómetros lo que pase primero para garantizar el funcionamiento correcto y continuo del sistema de control de emisiones. Estos y todos los demás servicios de mantenimiento incluidos en este documento, deben realizarse para proporcionar el mejor rendimiento y confiabilidad del vehículo.

Revisión en estación de servicio. Los siguientes elementos deben ser inspeccionados por usted o un empleado de servicio cada vez que se agregue combustible: Nivel de aceite del motor (añadir si es necesario; consulte el Manual del propietario, “Aceite del motor”); Nivel de refrigerante del motor (agregue refrigerante adecuadamente mezclado al tanque de almacenamiento si es necesario; reemplace el refrigerante si está sucio u oxidado en el color; consulte “Refrigerante”); Nivel de líquido lavaparabrisas; Inspección de neumáticos (desgaste inusual y presión de inflado adecuada; consulte “Neumáticos”).

Mantenimiento Carrocería. Lavado: la mejor manera de preservar el acabado de su vehículo y ayudar a evitar la oxidación es mantenerlo limpio lavándolo con frecuencia; lave el vehículo solo con agua tibia o fría; no lave bajo los rayos directos del sol ni use jabones fuertes o detergentes químicos; cualquier producto de limpieza utilizado debe lavarse rápidamente y no debe dejarse secar en el acabado. Daño del acabado: las astillas de piedra, las fracturas o los arañazos profundos en el acabado deben repararse con prontitud; el metal desnudo se corroe rápidamente; las hojuelas y arañazos menores se pueden reparar con los materiales de retoque disponibles en su Distribuidor; el costo de dichas reparaciones se considera responsabilidad del propietario. Depósitos de material extraños: el cloruro de calcio y otras sales, los agentes para derretir el hielo, el aceite y el alquitrán del camino, la savia de los árboles, los excrementos de las aves, los productos químicos de las chimeneas industriales, la lluvia ácida y otros materiales extraños pueden dañar el acabado si se dejan sobre las superficies pintadas. Mantenimiento de bajos: los materiales corrosivos utilizados para la eliminación del hielo y el control del polvo pueden acumularse en las superficies inferiores de la carrocería; si no se eliminan, se puede producir una corrosión acelerada en líneas de combustible, marco, bandeja del piso y sistema de escape; lave completamente estos materiales de la parte inferior con agua corriente.

Conducir en países extranjeros. Diferentes países tienen vehículos diseñados para sus condiciones; los combustibles y lubricantes locales pueden no ser adecuados; se pueden producir daños si se utilizan los incorrectos; es posible que se requiera la modificación del vehículo por regulaciones locales; el servicio al cliente o ciertas partes pueden no estar disponibles. Verifíquelos con un distribuidor Mitsubishi Motors antes de su partida.

Prueba en carretera. La prueba de carretera se incluye en la inspección periódica. Esta prueba debe realizarse después de completar todo el trabajo relacionado con los elementos indicados como elementos de servicio para cada inspección periódica. Compruebe los siguientes elementos mientras conduce el vehículo: Comprobar el juego libre del volante; Comprobar la efectividad del freno de servicio y del sistema de freno de estacionamiento; Controlar la manejabilidad del motor; Verifique el estado de los instrumentos, medidores, indicadores, lámparas externas, calentadores y ventiladores.

### PROGRAMA DE MANTENIMIENTO RECOMENDADO

Tablas S13–S20 del cuaderno (OPERACIONES DE SERVICIO DE MANTENIMIENTO por km × 1,000 de 10 a 200 y meses de 6 a 120; leyenda I = Inspección, R = Remplazo, N/A = No aplica, * Utilizar partes originales, ** Según aplique, R+ Reemplazo para L200, (R) Solo por km, (R+) Reemplazo por km para L200). Transcritas en la sección 8.3 de este documento.

### REGISTROS DE MANTENIMIENTO

Veinte recuadros, uno por servicio: «10,000 km o 6 Meses», «20,000 km o 12 Meses», «30,000 km o 18 Meses», «40,000 km o 24 Meses», «50,000 km o 30 Meses», «60,000 km o 36 Meses», «70,000 km o 42 Meses», «80,000 km o 48 Meses», «90,000 km o 54 Meses», «100,000 km o 60 Meses», «110,000 km o 66 Meses», «120,000 km o 72 Meses», «130,000 km o 78 Meses», «140,000 km o 84 Meses», «150,000 km o 90 Meses», «160,000 km o 96 Meses», «170,000 km o 102 Meses», «180,000 km o 108 Meses», «190,000 km o 114 Meses», «200,000 km o 120 Meses». Cada uno con Fecha, KM, OR (Orden de reparación) y Firma y sello Distribuidor.

---

## Anexo C · Manual del Programa de Reactivación de Garantía (MMDM, MMDM-MG-007-2025, agosto 2025), texto íntegro

Transcrito de `Manual Para Reactivación de Garantía.pdf` (6 páginas). Índice: Objetivo del Manual (3); Alcance del Programa y políticas de garantía de desfases en servicios de mantenimiento (3); Proceso de Reactivación (4).

### Objetivo del Manual.

Establecer los lineamientos, criterios y pasos a seguir para la reactivación de garantía de los vehículos Mitsubishi Motors cuando el cliente haya incumplido en tiempo y forma con algún servicio de mantenimiento dentro de un margen tolerado. Así mismo, definir responsables, requisitos y condiciones económicas para brindar claridad y consistencia al proceso en beneficio del cliente final, el distribuidor y las marcas involucradas.

### Alcance del Programa y políticas de garantía de desfases en servicios de mantenimiento.

Este manual aplica a: • Todos los distribuidores autorizados Mitsubishi Motors en México.

Políticas de garantía establecidas por MMDM para desfases en servicios de mantenimiento:

• Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de 1 a 1,000 kilómetros y/o de 1 a 31 días respecto al plan de servicios de mantenimiento de MMDM, será considerado como tolerancia en desfase y la garantía procederá bajo este criterio en términos y condiciones de la garantía básica.

• Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de 1,001 a 2,000 kilómetros y/o de 32 a 62 días, será considerado procedente por garantía bajo los términos y condiciones de “Carta Compromiso” la cual, deberá ser firmada por el cliente si es que acepta de conformidad los términos y condiciones estipulados en la misma. El formato de dicha carta ya se encuentra disponible y será distribuido por el área de garantías de MMDM bajo solicitud del distribuidor autorizado Mitsubishi Motors en México.

• Vehículos Mitsubishi que presenten desfase de mantenimiento dentro del rango de 2,001 a 6,000 kilómetros y/o de 63 a 186 días, serán acreedores al programa “Reactivación de Garantía” definido en los siguientes puntos de este manual.

### Proceso de Reactivación.

• Este programa de reactivación aplica para los casos en los que, tras el diagnostico técnico, se determine la posibilidad de reactivar la garantía mediante el cumplimiento de los requisitos establecidos por MMDM y GarantiPlus de México.

Quedan excluidos de este programa: • Vehículos fuera del rango de desfase permitido. • Componentes no cubiertos por contrato de garantía. • Situaciones en las que no sea posible realizar reacondicionamiento conforme a las políticas técnicas del fabricante.

1. Recepción del Vehículo. El distribuidor recibe un vehículo con una anomalía reportada por el cliente.

2. Diagnóstico inicial. El técnico realiza el diagnostico para determinar si la anomalía/condición reportada es o no atribuible a garantía.

3. Verificación de Vigencia de Garantía. El administrador de garantías debe revisar lo siguiente: Que el vehículo se encuentre dentro de los limites de tiempo y kilometraje con respecto a la garantía original. Si presenta desfase, analizar a cuál de las Políticas de garantía establecidas por MMDM para desfases en servicios de mantenimiento aplica o si es acreedor al programa “Reactivación de garantía.

4. Identificación del Rango de Desfase. El asesor valida si el vehículo presenta un desfase dentro del rango que aplica este programa: • Entre 2,001 y 6,000 Km y/o entre 63 y 186 días. Si el desfase está fuera de estos rangos, este programa no es aplicable.

5. Oferta de Reactivación de Garantía. Se informa al cliente que puede reactivar su garantía, siempre y cuando su vehículo cumpla con: Un checklist que incluye revisión técnica especializada. Se realice el servicio de mantenimiento correspondiente al kilometraje que tenga la unidad en el momento de acudir al distribuidor. Que el vehículo sea reacondicionado con base en los resultados del checklist (Si aplica).

6. Condiciones de Reacondicionamiento. Una vez aplicado el checklist si se determina que el reacondicionamiento es necesario: GarantiPlus México cubre el 50% del costo de reacondicionamiento, solo en componentes cubiertos por garantía. El cliente cubre: El 50% restante del reacondicionamiento. *Los componentes de desgaste no están cubiertos por garantía ni por contrato.

7. Cálculo del Precio Público al Cliente. El precio final al cliente para reactivar la garantía se determina de la siguiente forma: Precio del servicio de mantenimiento correspondiente vigente (+) Aplicación de checklist $1,650 (+) Precio de reactivación de garantía $2,000 (+) 50% del precio de reacondicionamiento (si aplica) = Precio público a cliente. Todas las cantidades descritas son + IVA. Nota: El pago de $2,000+IVA correspondiente a la reactivación de garantía que el cliente paga al distribuidor y deberá ser pagado a su vez a GarantiPlus por parte del distribuidor.

8. Envío de Solicitud a GarantiPlus. Una vez completado los pasos del 1 al 7, el distribuidor deberá: Enviar la solicitud de reactivación inmediatamente al socio comercial de GarantiPlus, INVARAT encargado de la “Evaluación Remota para Reactivación de Garantía” a los correos: rodolfo.maldonado@invarat.mx · david.simancas@garantiplus.mx. Con copia a: mario.luna@garantiplus.mx · Jose.vences@na.mitsubishi-motors.com · Alexys.gonzalez@na.mitsubishi-motors.com. Incluir en la solicitud de reactivación enviada por correo: o Los datos del vehículo (modelo, VIN, kilometraje, etc.) y motivo de la solicitud: “Revisión por posible Reactivación de garantía” o Evidencia técnica (checklist, diagnostico). o Documentación del servicio y reacondicionamiento. o Carta firmada por el cliente. Se agenda la evaluación técnica con Invarat. Los detalles de cómo se realiza la evaluación técnica remota por parte de INVARAT, se encuentran en el archivo PDF: Condiciones Generales Para Realizar la Valuación, publicado junto con este manual.

9. Firma y Conservación de la Carta de Reactivación. Si la unidad aprueba el checklist, el cliente firma la Carta de Reactivación y conserva una copia de la misma para futuras reclamaciones. Se reparan los componentes requeridos: GarantiPlus paga el 50% de las piezas cubiertas por garantía. El cliente paga su parte y el 100% de los componentes de desgaste. El distribuidor conserva el original de la Carta Compromiso firmada por el cliente en el expediente del vehículo, durante el periodo restante de garantía.

10. Reincidencias. En el caso de reincidencia (nuevo desfase) no habrá tolerancia: La garantía del vehículo quedará cancelada.
