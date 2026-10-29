# Criterios y documentos — programa Mitsubishi (plantilla `mitsubishi`)

**Versión de este recurso: 2026-10-28 (v4: el contrato de referencia del programa vive en `contrato-mitsubishi.md` (certificado + póliza MMDM + manual de reactivación, un solo contrato; el Anexo de este archivo pasa a ser un puntero); mantenimientos con los **tres rangos de desfase de MMDM** (Manual MMDM-MG-007-2025) en lugar de la tolerancia de 1 mes / 1,000 KM, con el método de la guía del área y **la tabla de intervalos la imprime el conector** (`mantenimientos` de `generar_resolucion`: la brecha de la 10.4 cerró el 28/10/2026); lectura flexible de cobertura (decisión de Omar, 28/10/2026); comentarios de «sin comprobantes» y «candidato a reactivación». v3.1: `buscar` en inglés; v3: la cuenta Mitsubishi entra en alcance; v2: criterio operativo del área del 27/10/2026 incorporado completo; lista de precios en el conector; v1 (26/10): preparado.)** Quien lo edite actualiza aquí la fecha y la nota de qué cambió.

> **La cuenta Mitsubishi está EN ALCANCE desde el 27/10/2026** (decisión de Omar; `instructions.md` §1). Un folio Mitsubishi se dictamina, se genera su Informe con la plantilla `mitsubishi` y se cierra en SIGA con el mismo flujo de tres mensajes de `instructions.md`, con las diferencias de la sección 13 de este archivo.

Todo lo que el conector y el área saben del programa Mitsubishi. Tiene cuatro fuentes, y cada regla dice de cuál sale:

- **El contrato de referencia** (`contrato-mitsubishi.md`): **en SIGA no hay contrato de cobertura Mitsubishi** (los técnicos lo dijeron y se les hace caso); ese archivo es el contrato. Fusiona el certificado del programa GARANTÍA REAL 7 (GarantiPlus, febrero 2019; Anexo A, numeración S.N que es la que se cita), la Póliza de Garantía Limitada MMDM (agosto 2019; Anexo B, sus secciones se citan por literal con `numeral: "Póliza MMDM"`) y el Manual del Programa de Reactivación de Garantía de MMDM (agosto 2025; Anexo C). Aquí se cita como `Certificado S.N`, `Póliza MMDM — SECCIÓN` y `Manual MMDM-MG-007-2025`.
- **«Criterios operativos para evaluación de averías Mitsubishi»** (`Criterios_Operativos_Mitsubishi_GarantiPlus.pdf`, 9 páginas, GarantiPlus México, «Uso operativo interno», **27 de octubre de 2026**): la guía del área para «revisar contratos, expedientes, evidencia, mantenimientos, presupuestos y emitir resoluciones consistentes en SIGA». En este archivo se cita como **«PDF del área»** o **`Criterio del área (PDF 27/10/2026)`**. Todo su contenido está aquí, punto por punto; las frases clave van literales entre «…». Su tolerancia de 1 mes / 1,000 KM quedó absorbida por los rangos de MMDM (sección 4.2).
- **«Prompt para Claude — Análisis de desfase de mantenimientos»** (`Prompt_Claude_Analisis_Mantenimientos_Mitsubishi.pdf`, 4 páginas, guía del área): el método paso a paso para extraer servicios, calcular intervalos, llenar la tabla, marcar en rojo, clasificar y redactar. Se cita como `Guía del área (prompt de mantenimientos)`; su esencia está en la sección 4.3.
- **Decisiones de Omar** (26/09, 27/10 y 28/10/2026), citadas con su fecha.

**Nada de `casos-garantiplus.md` aplica aquí salvo que este archivo lo diga**: los criterios de GarantiPlus (intervalos de 12,000 km / 12 meses, su tolerancia de 1,000 km / 30 días, 12.5, 13.30, el orden de causales…) se apoyan en cláusulas que este contrato no tiene o en decisiones del área para otra cuenta. Donde el PDF del área y `casos-garantiplus.md` coinciden, se dice; donde difieren, manda este archivo para Mitsubishi.

**Glosario mínimo.** **MMDM** = Mitsubishi Motors de México. **PRC** y **PQR** = reportes técnicos del distribuidor Mitsubishi con el diagnóstico (síntoma, pruebas, causa raíz, piezas; a veces también kilometraje y servicios); el PDF del área habla además de «expedientes PRC relacionados». **MSRP** = precio de lista de la refacción en la lista de precios mensual de Mitsubishi. **DNP** = precio al distribuidor en esa misma lista. **SS** = número de parte que sustituye al de la fila (supersesión). **EGT** = sensor de temperatura de gases de escape. **MY25** = año modelo 2025. **Alexys** = la persona que, según el área, da el visto bueno a los rechazos Mitsubishi (este archivo no sabe más de ella; no se le atribuye otro cargo; su correo aparece en el Manual de reactivación como copia de las solicitudes). **INVARAT** = socio comercial de GarantiPlus que hace la «Evaluación Remota para Reactivación de Garantía». **Carta Compromiso** y **Carta de Reactivación** = los documentos que firma el cliente en los rangos 2 y 3 de desfase (sección 4.2).

---

## 0. Principio rector y jerarquía de fuentes

### 0.1 Principio rector (PDF del área, portada)

> «Cada avería se evalúa con su propio contrato y con la evidencia de su expediente. Los criterios internos complementan el análisis, pero no sustituyen ni pueden contradecir las condiciones particulares de la cobertura.»

Y como regla general (PDF §1): «La procedencia no se determina únicamente por el nombre de la refacción ni por un antecedente de otra avería. Se debe reconstruir el caso desde cero, identificar el contrato aplicable, verificar la unidad y relacionar la causa de la falla con la cobertura y las exclusiones.»

**Qué es «su propio contrato» en Mitsubishi.** El programa **no tiene certificado individual por vehículo** y **SIGA no tiene contrato de cobertura para esta cuenta** (sección 1). El contrato aplicable a cada avería es, por tanto, **`contrato-mitsubishi.md`** (certificado del programa + póliza MMDM + manual de reactivación, leídos como un solo contrato) **más la póliza de esa avería en SIGA** (`policyId`, vigencia, kilometraje de inicio, lo que la ficha traiga) y, si existe en el expediente, la carátula o póliza de la unidad. Esa es la lectura que adopta este archivo; la tensión con la frase del PDF está en la sección 12.

### 0.2 Ficha del documento del área (PDF, portada)

| Documento | Alcance |
| --- | --- |
| Aplicación | «Averías Mitsubishi revisadas en SIGA México y expedientes PRC relacionados.» |
| Resultado | «Resolución aceptada, resolución rechazada o comentario de información faltante.» |
| Formato | «Word para revisión y edición; PDF cuando los datos estén completos y confirmados.» (Cómo encaja con el conector, que genera los dos a la vez: sección 10.) |
| Control | «No modificar estatus ni cargar archivos sin autorización expresa.» (Encaja con los dos pasos del conector: sección 7.4.) |

Contenido que declara el PDF: jerarquía de información y documentación mínima; mantenimientos, tolerancias y cartas de compromiso; cobertura técnica, campañas y casos especiales; presupuestos, MSRP −10 %, mano de obra y autorizaciones especiales; reglas de aceptación, rechazo, comentarios y formato de resolución; checklist operativo antes de emitir el documento. Cada uno tiene aquí su sección.

### 0.3 Jerarquía de revisión (PDF §1, tabla; las seis prioridades con su «uso obligatorio»)

| Prioridad | Fuente | Uso obligatorio (literal del PDF) | Cómo llega en el conector |
| --- | --- | --- | --- |
| **1** | Contrato o póliza de la avería | «Vigencia, producto, coberturas, exclusiones, límites, obligaciones y plan de mantenimiento aplicable.» | **`contrato-mitsubishi.md`** (el contrato de referencia: certificado del programa —el mismo que el conector entrega en `expediente_completo`— + póliza MMDM + manual de reactivación) + la póliza de la ficha de SIGA (`policyId`, vigencia, km de inicio si los trae) + la carátula o póliza de la unidad si el taller o el área la subieron al expediente. |
| **2** | Expediente de SIGA | «Datos de la avería, VIN, estatus, presupuesto, documentos y seguimiento.» | Ficha e índice de `expediente_completo`; estado operativo (renglones, Resolución, panel) con `renglones_averia`; Seguimiento en `Details` con el navegador integrado si está disponible. |
| **3** | PRC, PQR y diagnóstico | «Síntoma, pruebas realizadas, causa raíz, componentes afectados, manipulación y recomendación técnica.» | Documentos del expediente (`expediente_completo`; lo que quede fuera, `leer_documento`). |
| **4** | Evidencia | «Odómetro, VIN, fotos, videos, códigos de falla, piezas desmontadas y condición física.» | Imágenes y fotogramas de video en `expediente_completo`; un tramo o más resolución con `leer_documento`; el audio sólo con el enlace `/video`. |
| **5** | Mantenimientos | «Facturas, sellos, historial y datos consignados en PRC; verificar fechas y kilometrajes.» | Documentos del expediente; el PRC también puede traer servicios. |
| **6** | Criterios y comunicaciones vigentes | «Campañas, boletines, acuerdos con MMDM y autorizaciones de Alexys, sin contradecir el contrato.» | Este archivo (casos especiales de la sección 5.3) y lo que el técnico diga (fuente `Técnico`). |

Reglas de uso de la jerarquía:

- Cada razón del veredicto lleva su fuente (`instructions.md` regla 3). En Mitsubishi se usan además `Certificado del programa <numeral>`, `Póliza (SIGA)` y `Criterio del área (PDF 27/10/2026)`.
- Si dos fuentes se contradicen en un dato que cambia el veredicto o el Informe (VIN, km, fecha, importe), no se elige en silencio: se muestran los dos valores y decide el técnico.
- La prioridad 6 complementa y **no puede contradecir** a la 1. Donde un caso especial vigente choca con el texto del certificado (sección 5.3), se dice en una viñeta y se aplica como `Criterio del área`, porque la nota de aplicación del PDF hace prevalecer también «la instrucción formal más reciente» (0.4); la decisión final es del técnico.
- Los antecedentes no deciden: «Un antecedente aceptado no crea cobertura universal» (sección 5.4).

### 0.4 Nota de aplicación (PDF, página 9)

> «Esta guía consolida criterios operativos vigentes para facilitar una revisión homogénea. Cuando exista contradicción, prevalece el contrato específico de la unidad y la instrucción formal más reciente emitida por las áreas autorizadas de Mitsubishi y GarantiPlus México.»

Consecuencias aquí: (a) si un dato de la póliza o de la carátula de la unidad difiere de este archivo, manda la póliza; (b) si el técnico trae una instrucción formal posterior al 28/10/2026, manda ella sobre este archivo (se registra con fuente `Técnico`, con quién la emitió y su fecha); (c) quien edite este archivo la incorpora y sube la versión.

### 0.5 Lectura flexible (decisión de Omar, 28/10/2026)

El área tiene **buena relación comercial con Mitsubishi** y quiere **rechazar menos**. Por eso el contrato de referencia (`contrato-mitsubishi.md` §0.3) y este archivo se leen así:

1. **Cobertura defensa a defensa salvo exclusión expresa y probada.** Todo elemento mecánico, eléctrico o electrónico montado de origen está cubierto salvo que esté en una lista de exclusión (cláusula 2 del certificado; «PARTES Y SERVICIOS NO CUBIERTOS» y «PARTES CON GARANTIA DIRECTA DEL FABRICANTE» de la póliza MMDM) **y** la exclusión esté probada. Las listas de partes cubiertas son ilustrativas.
2. **En duda, procede.** Si ningún texto excluye el componente ni la causa, y la evidencia no prueba una exclusión, el caso es 🟢 (si lo demás está completo).
3. **Una exclusión exige evidencia específica** (`contrato-mitsubishi.md` §6.4): golpe, manipulación, negligencia, epidemia o campaña se prueban, no se suponen.
4. **Antes de rechazar, se pide lo que falta** (🟡 con el comentario de la sección 3.3, 4.5 o 4.6). Un rechazo sale sólo con causal concreta, evidencia y, si es por mantenimiento, con el tramo fuera de los rangos de MMDM o con la carta o la reactivación declinadas.
5. **Entre dos lecturas que algún texto sostenga, la más favorable al beneficiario**, diciendo cuál texto la sostiene. Lo que el certificado prohíbe tajantemente no se relaja: fuera de vigencia (5, 14.5), siniestros (15.18), trabajos antes de la resolución probados (14.1), vehículo no inmovilizado (14.2).
6. **Flexible no es inventar**: ni cláusulas, ni intervalos, ni precios. El técnico decide siempre.

Qué cambia en la práctica respecto de v3: los desfases de mantenimiento se miden con los rangos de MMDM (4.2) y sólo el rango 4 rechaza; un componente que no está en ninguna lista se trata como cubierto (5.0); las reglas del área «ruidos no se cubren» y «el odómetro no retrocede» ya tienen cláusula en la póliza MMDM (5.5) pero siguen exigiendo que no haya componente fallado; y las reconciliaciones de `contrato-mitsubishi.md` §5.3 (soportes, juntas, banda de distribución, batería 12 V, bujías de iridio, estéreo) se aplican tal cual.

---

## 1. Qué es el programa y cómo se ve en SIGA

- Es un **programa de garantía para unidades nuevas** vendidas por Mitsubishi Motors de México (producto «GARANTÍA REAL 7», certificado de febrero de 2019, vigente según el área): GarantiPlus administra y resuelve en SIGA la garantía de 7 años sin límite de kilometraje «defensa a defensa» de MMDM (decisión de Omar, 28/10/2026). **No hay certificado individual por vehículo y en SIGA no hay contrato de cobertura de esta cuenta**: todas las averías cuelgan del contrato centinela **57227**, y el contrato que se aplica es **`contrato-mitsubishi.md`**.
- La ficha de `expediente_completo` marca la cuenta como **MITSUBISHI (programa, sin contrato individual)** y la plantilla del Informe como `mitsubishi`. `averias_pendientes` las lista con esa etiqueta.
- Para el Informe, **`numeroContrato` es el `policyId`** de la avería (el `contractId` es siempre el 57227 y no se imprime). Coincide con el PDF del área: «Número de contrato: Póliza o encabezado de la avería» (sección 10.2).
- La vigencia y el kilometraje de inicio no se pueden verificar contra un certificado individual: salen de la ficha de SIGA (póliza) o de una carátula de la unidad en el expediente y, si faltan, se dicen como «por confirmar»; nunca se inventan. El PDF exige «Vigencia confirmada» (checklist, punto 2): si no se puede confirmar con ninguna fuente, es un dato esencial faltante (sección 7.1, «Requiere información»), salvo que el técnico la confirme con otra fuente (fuente `Técnico`).
- El condicionado que el conector entrega para estas averías es el **certificado del programa**, transcrito íntegro en `contrato-mitsubishi.md` Anexo A con su propia numeración (1–20). El motor de `generar_resolucion` con `plantilla: "mitsubishi"` transcribe los numerales de **ese** texto: un numeral que no exista ahí se rechaza. Las cláusulas de la póliza MMDM (Anexo B) no están en el conector: van siempre en `clausulasLiterales` con `numeral: "Póliza MMDM"` y el `titulo` exacto de la sección.
- Plantillas del Informe: **`cubierta-mitsu.docx`** (procedente: informe con el cuadro de valoración, carta de recepción del vehículo y las tres páginas para cobro) y **`rechazo-mitsu.docx`** (improcedente: sólo el informe, sin cuadro, sin carta y sin páginas de cobro). Encabezado: sólo `numeroAveria`, `numeroContrato`, `fechaAveria`, `modelo`, `vin`, `kmAveria`, `fechaCierre` (sección 10).

---

## 2. Identidad de la unidad (PDF §1, «Reglas de identidad de la unidad»)

Las cuatro reglas del área, literales, y cómo se aplican con el conector:

1. **VIN único en todo el expediente.** «El VIN del presupuesto, PRC, PQR, fotografías, póliza y expediente debe corresponder a la misma unidad.» Se cruza el VIN de la ficha de SIGA con el de cada documento que lo traiga (presupuesto, PRC, PQR, foto del parabrisas o de la placa VIN, póliza o carátula). Las coincidencias no se reportan; una diferencia sí.
2. **Modelo corroborado.** «El modelo puede inferirse inicialmente por el VIN, pero debe corroborarse con póliza, carátula o evidencia cuando exista. No usar el modelo genérico de SIGA si los documentos permiten precisarlo.» El campo `modelo` del encabezado se toma del documento más preciso (póliza, carátula, PRC, presupuesto del distribuidor) y no del texto genérico de la ficha; si sólo hay VIN y ficha, se dice en una viñeta que el modelo sale de ahí. Nunca se «decodifica» un VIN de memoria para inventar una versión.
3. **Odómetro fuera de SIGA.** «Si el odómetro no aparece en el campo de SIGA, buscarlo en la fotografía del tablero, PRC, PQR, presupuesto o documento de recepción.» (En el conector, `kmAveria` nunca viene de SIGA: se lee del odómetro y, si no hay foto, de esos documentos.) Si dos fuentes difieren, se enseñan las dos y decide el técnico. Si no aparece en ninguna, se solicita (sección 3).
4. **KM siempre con su unidad.** «En la resolución, todos los kilometrajes deben escribirse con la unidad: por ejemplo, 69,090 KM.» El encabezado del Informe ya lo imprime así (el conector formatea `kmAveria` como «69,090 KM»). **En el cuerpo** (`causaBreve`, `desarrollo`) quien redacta escribe cada kilometraje con separador de miles y «KM» en mayúsculas: «10,000 KM», «11,240 KM recorridos», nunca «10 mil», «10000» ni «km».

**Inconsistencia de VIN (recuadro del PDF §1):**

> «Si un presupuesto, PRC o evidencia corresponde a otra unidad, no se emite una resolución definitiva. Se solicita el documento corregido e identificado con el VIN del expediente.»

Con el conector: resultado 🟡 «Requiere información» (sección 7.1); no se llama a `generar_resolucion`; se propone el comentario al distribuidor (sección 3.3) pidiendo el documento corregido con el VIN del expediente, y se publica con `comentar_averia` (dos pasos) sólo si el técnico elige «Enviar» o «Uso Interno». No se rechaza por «Falta de relación en VIN» (motivo del catálogo de SIGA) por una sola pieza documental de otra unidad: el PDF manda pedir la corrección. Si el técnico decide otra cosa, es suya (fuente `Técnico`).

**Dos reglas del área sobre identidad y kilometraje que el certificado no escribe** (vigentes desde v1, decisión de Omar del 2026-09-25, y no derogadas por el PDF): «el odómetro no retrocede» (un kilometraje que baja entre documentos, o un km de avería menor que el de inicio, es alerta de integridad) y «ruidos, zumbidos y vibraciones no se cubren» (sección 5.5). Desde v4 tienen cláusula en la póliza MMDM («VEHÍCULOS CON ODÓMETRO ALTERADO» y «DAÑOS MENORES») y se citan por literal (sección 5.5); siguen siendo criterio y decide el técnico.

---

## 3. Documentación mínima y comentarios de faltantes (PDF §2)

### 3.1 La tabla de los siete elementos (literal)

| Elemento | Qué debe comprobar | Si falta o es incongruente |
| --- | --- | --- |
| Contrato o póliza | Unidad, vigencia, cobertura, exclusiones y obligaciones. | No concluir procedencia contractual. |
| VIN | Coincidencia entre expediente y documentos. | Solicitar corrección; no mezclar unidades. |
| Odómetro | Kilometraje real al momento de la avería. | Obtener de evidencia; si no existe, solicitarlo. |
| Diagnóstico | Falla confirmada, causa raíz, pruebas y piezas afectadas. | Solicitar diagnóstico concluyente. |
| Presupuesto | Partidas, cantidades, precios, mano de obra e IVA. | Solicitar presupuesto detallado y corregido. |
| Mantenimientos | Fechas, KM, secuencia y cumplimiento de intervalos. | Solicitar facturas, sellos o historial legible. |
| Evidencia | Daño, códigos, fuga, ruido, desmontaje o mediciones. | Solicitar evidencia relacionada con la causa. |

Dos matices literales del PDF:

- «El expediente no tiene que contener siempre el mismo tipo de archivo; lo importante es que la evidencia disponible permita verificar identidad, kilometraje, diagnóstico, causa, mantenimiento y costo.»
- «Una fotografía aislada de una pieza rota no sustituye el diagnóstico cuando existe posibilidad de golpe, manipulación, impacto o daño externo.»

**Diferencia con GarantiPlus que conviene no perder:** en GarantiPlus, si no hay ningún comprobante de mantenimiento, el mantenimiento «no se evalúa ni bloquea el veredicto». **En Mitsubishi el PDF manda solicitarlos** («Solicitar facturas, sellos o historial legible») y pide «Historial de mantenimientos revisado completo» en el checklist. Por tanto, sin comprobantes de mantenimiento, el caso Mitsubishi va a 🟡 «Requiere información» salvo que otra causal ya decida el rechazo con evidencia suficiente (por ejemplo, componente expresamente excluido en la cláusula 2), o que aplique el caso especial de la bomba L200 (sección 5.3), que se autoriza «aun cuando existan incidencias de mantenimiento». Si el técnico decide otra cosa, fuente `Técnico`.

**«Contrato o póliza» faltante.** El certificado del programa llega siempre; lo que puede faltar es la póliza de la unidad (vigencia, inicio). Sin vigencia confirmable, «No concluir procedencia contractual»: no se emite un 🟢 por inferencia.

### 3.2 Cómo se redactan los comentarios de faltantes (PDF §2, literal)

- «Indicar exactamente qué documento o dato se requiere.»
- «Explicar para qué se necesita: confirmar causa, identidad, mantenimiento, costo o cobertura.»
- «No afirmar que la avería está rechazada si aún falta información esencial para concluir.»
- «Cuando la evidencia apunte con claridad a una conclusión pero falte un dato editable, puede prepararse un Word para revisión, señalando el dato pendiente fuera del texto final de la resolución.» (Con el conector: sección 7.3, «Datos o montos incompletos».)

Y de la sección «Comentarios» del PDF §6: «El comentario debe permitir que el distribuidor corrija el expediente sin adivinar lo solicitado. Debe ser corto, específico y verificable: documento, VIN, prueba, diagnóstico, dato o presupuesto requerido.»

### 3.3 Ejemplo de comentario del área (recuadro «SOLICITUD», literal)

> «Favor de compartir diagnóstico técnico concluyente, causa raíz de la falla, evidencia del componente afectado, odómetro y presupuesto corregido para el VIN del expediente. Con la información actual no es posible confirmar la procedencia.»

Cómo se usa con el conector:

- El comentario se arma con lo que falta **en ese folio** (sólo los elementos de 3.1 que falten o sean incongruentes, cada uno con su para qué), en el tono del ejemplo. Puede envolverse en la plantilla «Pendiente» del área (`instructions.md` §5.5: «Hola, buen día. Se revisó la avería {folio} y el expediente sigue incompleto para poder resolverla. Hace falta: {lista numerada}…»), siempre que la lista diga qué documento, para qué y con qué VIN. Lo que el técnico corrija se usa tal cual.
- Se publica con `comentar_averia` (ensayo sin `confirmar` → con `confirmar: true` y el `plan`), sólo tras «Enviar» o «Uso Interno» del técnico (`instructions.md` §4.3). El folio sigue en Validación; no se genera Informe.
- Nunca dice «rechazada» ni anticipa el resultado.

---

## 4. Mantenimientos (contrato §8; PDF §3; guía del área; Manual MMDM-MG-007-2025)

### 4.1 Lo que dice el contrato (`contrato-mitsubishi.md` §7–§8)

- **Certificado 11:** «Para que el certificado contratado sea efectivo, el BENEFICIARIO se obliga a efectuar en el VEHÍCULO los trabajos o tareas de mantenimiento exigidas por el POR EL FABRICANTE SIGUIENDO SU PLAN DE MANTENIMIENTO PRECONIZADO, tanto en periodos de tiempo como en kilometraje.» Remite al plan del fabricante, que es el de la póliza MMDM.
- **9.3** obliga a «Realizar en el VEHÍCULO los mantenimientos periódicos exigidos por el fabricante en tiempo y forma» y **9.4** a «Conservar las facturas correspondientes…». **12.3.c–d**: el taller aporta copia del libro de mantenimiento si lo hay y las facturas con identificación del taller, del vehículo (marca, modelo, placa, kilómetros), reparaciones desglosadas, fecha y firma o sello.
- **14.3** permite rechazar «Cuando el BENEFICIARIO no haya cumplido sus obligaciones en relación con los mantenimientos e inspecciones exigidas en el certificado contratado»; **14.4**, cuando las facturas o la documentación del artículo 12 «no estén debidamente cumplimentadas, o directamente no se aporten … en un plazo de 72h tras ser requeridas».
- **Póliza MMDM:** el plan es «cada 6 (seis) meses o 10,000 (diez mil) kilómetros lo que pase primero» (MANTENIMIENTO DEL SISTEMA DE CONTROL DE EMISIONES); las operaciones de cada servicio están en `contrato-mitsubishi.md` §8.3; los registros de sellos en REGISTROS DE MANTENIMIENTO. Y: «MMDM se reserva el derecho de negar la cobertura de la garantía si el vehículo no se ha mantenido correctamente. **Sin embargo, la negación no se basará únicamente en la ausencia de registros de mantenimiento.**» (ORDEN DE REPARACIÓN DE GARANTÍA).
- **8.3**: el vehículo es nuevo por definición («El auto deberá de ser nuevo…»), así que el historial se revisa desde la entrega.

### 4.2 Intervalo y rangos de desfase — **actualizado en v4** (decisión de Omar, 28/10/2026)

**Intervalo base: 6 meses o 10,000 KM, lo que ocurra primero** (Póliza MMDM; coincide con el recuadro «INTERVALO GENERAL MITSUBISHI» del PDF del área). **Plan de referencia salvo cuaderno de la unidad**: antes de aplicarlo se confirma que la póliza, la carátula o el cuaderno de la unidad que esté en el expediente no fijen otra cosa; si lo fijan, manda ese (y se dice). Un rótulo de factura («servicio de 20 mil») no es el plan.

**Los tres rangos de desfase de MMDM** (`Manual MMDM-MG-007-2025`, «Políticas de garantía establecidas por MMDM para desfases en servicios de mantenimiento», literales en `contrato-mitsubishi.md` §8.4 y Anexo C) **sustituyen a la tolerancia de 1 mes / 1,000 KM del PDF del área**, que queda absorbida por el primero:

| Desfase del tramo (km de más sobre 10,000 **o** días de más sobre 6 meses) | Rango | Tratamiento (Manual) | Qué tiene que constar en el expediente | Resultado del caso (si lo demás procede) |
| --- | --- | --- | --- | --- |
| 0 | En intervalo | Cumple | El comprobante del servicio | 🟢 |
| 1–1,000 km **o** 1–31 días | **1 · Tolerancia** | «será considerado como tolerancia en desfase y la garantía procederá bajo este criterio en términos y condiciones de la garantía básica» | El comprobante del servicio | 🟢, sin carta ni trámite; **no lleva `obs`** en la tabla del Informe |
| 1,001–2,000 km **o** 32–62 días | **2 · Carta Compromiso** | «procedente por garantía bajo los términos y condiciones de “Carta Compromiso” la cual, deberá ser firmada por el cliente» | La Carta Compromiso de **ese** VIN y **ese** desfase, firmada (el formato lo distribuye el área de garantías de MMDM a petición del distribuidor) | 🟢 si la carta está en el expediente (las tres comprobaciones de 4.6); 🟡 pidiéndola al distribuidor si no está (comentario de 4.6); **nunca 🔴 por falta de carta**; 🔴 por 14.3 sólo si el cliente la declina expresamente (consta en el Seguimiento o lo dice el técnico) |
| 2,001–6,000 km **o** 63–186 días | **3 · Reactivación de Garantía** | «serán acreedores al programa “Reactivación de Garantía”» (proceso de diez pasos: checklist $1,650 + IVA, reactivación $2,000 + IVA, servicio correspondiente, reacondicionamiento 50/50, solicitud a INVARAT, Carta de Reactivación; `contrato-mitsubishi.md` §8.5) | Carta de Reactivación firmada + checklist aprobado + servicio de mantenimiento correspondiente (+ reacondicionamiento si aplicó) | 🟢 cuando la reactivación consta, y **la avería del folio se paga al 100 %** (el 50/50 es sólo del reacondicionamiento); 🟡 «candidato a Reactivación» mientras corre el proceso (**el folio se queda en Validación** con el comentario de 4.6); 🔴 por 14.3 **sólo** si el distribuidor o el cliente declinan la reactivación, o si hay reincidencia acreditada |
| > 6,000 km **o** > 186 días | **4 · Fuera de rango** | «Vehículos fuera del rango de desfase permitido» quedan excluidos del programa | — | 🔴 por 14.3 con la 11 literal y la tabla en el Informe (4.4) |

**Cómo se mide cada tramo** (lectura de este archivo, coherente con la tabla del área):
- Cada tramo va de un servicio al siguiente, o del último servicio a la avería. **Exceso en km** = recorrido del tramo − 10,000. **Exceso en días** = días naturales del tramo − los días que hay entre la fecha del servicio anterior y esa misma fecha **seis meses de calendario** después (p. ej. 15/03/2026 → 15/09/2026 = 184 días; 31/08/2025 → 28/02/2026 = 181 días; si el día no existe en el mes de llegada, el último de ese mes). «Verificar manualmente los días; no aproximar meses ni asumir que 6 meses equivalen siempre a 180 días» (PDF del área).
- Km y días se evalúan **por separado**; si los dos exceden, el **rango es el mayor** y se escriben ambos. Un servicio adelantado reinicia el tramo desde su fecha y su kilometraje.
- Ejemplo: servicio el 12/06/2024 con 0 KM y el siguiente el 06/09/2024 con 10,152 KM → recorrido 10,152 (exceso 152 km → rango 1), 86 días (sin exceso) → **rango 1, cumple con tolerancia**, sin `obs`. Servicio el 02/10/2025 con 51,110 KM y el siguiente el 28/01/2026 con 63,451 KM → recorrido 12,341 (exceso **2,341 km → rango 3**), 118 días (sin exceso) → candidato a Reactivación.

**Qué tramo cuenta** (decisión de Omar, 28/10/2026): el rango del caso lo decide **el tramo que llega a la avería** (último servicio acreditado → avería) y los tramos inmediatos que expliquen la falla. Un desfase **antiguo** en rangos 1–3, seguido de servicios en intervalo, se considera **subsanado**: no se pide Carta Compromiso ni reactivación retroactivas, ni rechaza; se dice en una viñeta. Sólo un tramo antiguo **de rango 4** sigue siendo causal de 14.3 (el Manual no le da salida).

**Reincidencia** (Manual, paso 10): «En el caso de reincidencia (nuevo desfase) no habrá tolerancia: La garantía del vehículo quedará cancelada.» Cuenta **sólo** si consta en el expediente (una Carta Compromiso o una Carta de Reactivación anterior de ese VIN) o lo dice el técnico; sin esa fuente es un aviso al técnico («si esta unidad ya tuvo carta o reactivación, el Manual no da tolerancia»), no un resultado.

### 4.3 Método de análisis (guía del área, los nueve pasos, con el conector en cada uno)

Reglas obligatorias de la guía: «No inventes fechas, kilometrajes, intervalos, tolerancias, servicios, cláusulas ni numerales.» «Revisa cada avería con su propio contrato y documentación; no reutilices criterios de otra avería.» «Si un dato no puede comprobarse, escribe NO LOCALIZADO e indica qué documento hace falta.» «Distingue entre servicio excedido y evidencia insuficiente.»

1. **Identificar las reglas contractuales.** Del contrato de referencia: intervalo base 10,000 KM / 6 meses (4.2); rangos de desfase de MMDM (la «tolerancia» de la guía son aquí los rangos 1–3: límite total por km = 10,000 + el rango; por tiempo = 6 meses + el rango); fecha y km iniciales (entrega / inicio de la póliza); requisitos documentales (12.3.d); numerales del incumplimiento (11, 14.3, 14.4). Confirmar que la póliza o el cuaderno de la unidad no fijen otra cosa. «Si el contrato no establece una tolerancia, no agregues ninguna»: aquí el Manual sí la establece, por rangos.
2. **Extraer los mantenimientos.** De PRC, facturas, órdenes de servicio, fotografías de sellos, historial del distribuidor, comprobantes. Por cada servicio: número consecutivo, fecha, kilometraje, documento de origen, observaciones. «Si un mismo servicio aparece en varios documentos, no lo dupliques. Usa la fuente más legible y confiable y menciona las demás como respaldo.» Ordenar del más antiguo al más reciente e incluir como puntos de análisis **el inicio del contrato, cada mantenimiento comprobado y la fecha/kilometraje de la avería.**
3. **Validar la consistencia.** Fechas en orden cronológico y kilometraje que avanza; detectar km menores que el anterior, duplicados o datos de otra unidad; que fecha y km pertenezcan al mismo servicio y sean legibles; confirmar el km de avería con SIGA o la evidencia. «No corrijas inconsistencias por tu cuenta: señálalas en observaciones.» Un servicio sin fecha o sin km legible es **NO EVALUABLE**: se nombra, se pide (4.5) y **no entra como fila** de la tabla del conector (que exige fecha y km en cada fila); un tramo no evaluable que sea el que llega a la avería **bloquea el rechazo por mantenimiento** (resultado INFORMACIÓN INSUFICIENTE).
4. **Calcular cada intervalo.** «Días transcurridos = fecha del registro posterior − fecha del registro anterior. Kilómetros recorridos = kilometraje posterior − kilometraje anterior.» Exceso por km y por días como dice 4.2; «Solo muestra un excedente cuando el resultado sea mayor que cero.» Estados: **EN INTERVALO** (rango 0–1); **EXCEDIDO POR KM**, **POR TIEMPO** o **POR KM Y TIEMPO** (rangos 2–4, diciendo el rango); **NO EVALUABLE** (falta una fecha o un km indispensable).
5. **La tabla.** Columnas FECHA · KM · DÍAS TRANSCURRIDOS · KM RECORRIDOS · OBSERVACIONES; en el Informe la imprime el conector (4.4). Observaciones del vocabulario de la guía («EN INTERVALO», «EXCEDIDO POR KM EN 2,450 KM», «EXCEDIDO POR TIEMPO EN 37 DÍAS», «EXCEDIDO POR KM Y TIEMPO», «NO EVALUABLE», «EVIDENCIA INSUFICIENTE») en el chat; en la `obs` del conector sólo lo evaluable y en su forma corta (4.4): la fila sin `obs` ya dice «en intervalo», y lo no evaluable o sin comprobante no es fila. «Marca en rojo únicamente los valores excedidos. Si se exceden los kilómetros, pinta en rojo la celda KM RECORRIDOS; si se excede el tiempo, pinta DÍAS TRANSCURRIDOS.» «No marques en rojo servicios dentro de la tolerancia»: en Mitsubishi, **ningún tramo de rango 1 lleva `obs`**. «Usa separador de miles y no muestres decimales en kilómetros ni días.»
6. **Determinar el resultado.** **CUMPLE**: el tramo que llega a la avería y los inmediatos en rangos 0–1 (o 2–3 con carta o reactivación que constan), y ningún tramo antiguo de rango 4; los desfases antiguos en rangos 1–3 subsanados cuentan como cumplidos (4.2). **INCUMPLE**: el tramo que llega a la avería (o uno antiguo de rango 4) está en rango 4, o en rangos 2–3 con la carta o la reactivación declinadas. **INFORMACIÓN INSUFICIENTE**: falta un dato para calcular un tramo esencial, o el tramo está en rango 2–3 y la carta o la reactivación aún no constan. «Antes de emitir un rechazo, confirma que el intervalo realmente excede la tolerancia, que los registros pertenecen al vehículo, que no existe un servicio intermedio y que el contrato permite rechazar por ese incumplimiento con un numeral aplicable.»
7. **Colocar la tabla en la resolución.** La hace el conector con `mantenimientos` (4.4). La guía la quiere «después del párrafo de análisis de mantenimientos y antes del fundamento contractual»; el conector fija el orden: frase de dictamen → tabla → `desarrollo` (el párrafo) → cláusulas → cierre.
8. **Redactar el dictamen.** Si cumple, se dice que los registros están dentro de los intervalos y rangos de MMDM. Si incumple, el texto modelo de la guía **adaptado a los rangos de MMDM** (no es literal), en `desarrollo`: «Del análisis de los comprobantes de mantenimiento se identificó que entre el servicio registrado el {FECHA ANTERIOR} con {KM ANTERIOR} KM y el servicio registrado el {FECHA POSTERIOR} con {KM POSTERIOR} KM transcurrieron {DÍAS} días y se recorrieron {KM RECORRIDOS} KM. El contrato establece un intervalo de 10,000 KM o 6 meses, lo que ocurra primero, y el Programa de Reactivación de Garantía de MMDM (MMDM-MG-007-2025) admite desfases hasta 6,000 KM o 186 días. Por lo tanto, el intervalo se excedió en {EXCEDENTE KM} KM y/o {EXCEDENTE DÍAS} días, fuera de todo rango de tolerancia, carta compromiso o reactivación.» (o, en rangos 2–3 declinados: «… dentro del rango de {Carta Compromiso | Reactivación de Garantía}, que el distribuidor/cliente declinó el {fecha}»). Después, la 11 literal y el 14.3. «Si falta información, no emitas rechazo definitivo: genera un comentario con los documentos necesarios.»
9. **Control de calidad.** Todas las fechas y km coinciden con la evidencia; días y recorridos calculados entre registros consecutivos; intervalo y rangos del contrato de referencia (o del cuaderno de la unidad); celdas excedidas en rojo y ninguna marca roja incorrecta (ninguna en rango 1); el resultado de la tabla coincide con el dictamen; el numeral citado es del certificado del programa; la tabla se ve completa en el PDF.

### 4.4 La tabla de mantenimientos con el conector (`mantenimientos` de `generar_resolucion`) — **nuevo en v4**

Desde el 28/10/2026 `generar_resolucion` imprime la tabla del área dentro del Informe. Ya no hay brecha: **no se escribe el análisis línea por línea en `desarrollo`** (ahí va sólo el párrafo del texto modelo del paso 8).

**El parámetro:**

```json
"mantenimientos": {
  "intervalo": { "meses": 6, "km": 10000 },
  "servicios": [
    { "fecha": "2024-06-12", "km": 0 },
    { "fecha": "2024-09-06", "km": 10152 },
    { "fecha": "2024-11-19", "km": 19289 },
    { "fecha": "2025-03-13", "km": 29462 },
    { "fecha": "2025-07-02", "km": 40329 },
    { "fecha": "2025-10-02", "km": 51110 },
    { "fecha": "2026-06-13", "km": 69500, "obs": "KM AVERÍA · EXCEDIDO KM +8,390" }
  ]
}
```

En este ejemplo el tramo que llega a la avería (02/10/2025 con 51,110 KM → 13/06/2026 con 69,500 KM) recorre 18,390 KM en 254 días: exceso de **8,390 KM** (más de 6,000: **rango 4**) y de 72 días (rango 3); manda el mayor → rango 4 → 🔴 por 14.3. Los cinco tramos anteriores están en intervalo o en rango 1 (10,152 KM) y no llevan `obs`. Si el último tramo hubiera dado 2,341 KM de exceso (rango 3), el caso sería 🟡 candidato a Reactivación y **no** se generaría un improcedente con esta tabla (4.2).

Reglas del conector (las comprueba y se niega si no se cumplen):
- **Sólo con `veredicto: "improcedente"`**; en un procedente se rechaza el parámetro.
- `intervalo.meses` e `intervalo.km` enteros ≥ 1: **6 y 10000** (o lo que fije el cuaderno de la unidad).
- `servicios`: **de 2 a 40 filas**, en orden cronológico estricto (dos filas con la misma fecha o un km que baja = error que nombra la fila; el conector **no reordena ni corrige**). Cada fila con `fecha` (AAAA-MM-DD, fecha real de calendario) y `km` (entero ≥ 0). **Un servicio sin fecha o sin km no es fila** (4.3, paso 3).
- La **primera fila** es el inicio (entrega o inicio de la póliza, km 0 o el inicial); la **última fila es la avería** (fecha de registro en SIGA o de la orden de entrada, con el km de avería) y lleva `obs: "KM AVERÍA"` como en la plantilla del área.
- `obs`: opcional, **una sola línea, máximo 40 caracteres, sin `{`, `}` ni `|`**. Es la marca del técnico; **el conector nunca la pone ni la quita**. Vocabulario que cabe: `EXCEDIDO KM +2,341` · `EXCEDIDO TIEMPO +37 DÍAS` · `EXCEDIDO KM Y TIEMPO` · `EXCEDIDO KM +2,341 / +37 DÍAS` · en la última fila `KM AVERÍA` y, si ese tramo es el que excede, `KM AVERÍA · EXCEDIDO KM +8,390` (≤ 40 caracteres). Nada en rango 1 ni en intervalo. Si la avería se registró **el mismo día** que un servicio, el conector rechaza dos filas con la misma fecha: se omite la fila del servicio y se dice en `desarrollo`.
- El conector **calcula DIAS y RECORRIDO** de cada fila contra la anterior, imprime las tres filas de título (ANÁLISIS DE INTERVALOS DE MANTENIMIENTO · marca, modelo y VIN del encabezado · «INTERVALO ESTABLECIDO POR EL FABRICANTE: 6 MESES O 10,000 KM»), la cabecera FECHA · KM · DIAS · OBS · RECORRIDO y pinta en rojo **sólo en las filas con `obs`**: la celda OBS siempre; RECORRIDO si además ese tramo supera `intervalo.km`; DIAS si además supera `intervalo.meses` de calendario. Una fila sin `obs` nunca lleva rojo (el rango 1 sale limpio). Así, «KM AVERÍA» en la última fila sale en rojo (como en la plantilla del área) y, si el tramo hasta la avería también excede, su cifra también.
- **Avisos del conector** (se leen al técnico, no son errores): «el servicio N supera el intervalo por la aritmética y no trae obs» —en Mitsubishi es lo normal en rango 1 (10,152 > 10,000 sin `obs`): se le dice al técnico que es tolerancia de MMDM—; «el servicio N trae obs pero no supera el intervalo»; «el primer servicio no tiene anterior». La `obs` de la avería («KM AVERÍA») también produce aviso si ese tramo no excede: es esperado.

**Flujo en el chat:** Claude arma la tabla en Markdown (fecha, km, días, recorrido, rango, obs propuesta) y la enseña en el veredicto; el técnico confirma o corrige las `obs` (son suyas); en el mensaje 2 `generar_resolucion` lleva `mantenimientos` con esas `obs`, y la sección «## Análisis de intervalos de mantenimiento» de la respuesta del conector enseña exactamente lo que se imprimió; el técnico lo revisa en el PDF. La tabla de parámetros del mensaje 2 lleva la línea «Rango de desfase (Manual MMDM): {1 | 2 | 3 | 4} — {tramo}» (sección 13).

**Qué va con la tabla** (10.3): `causaBreve` «el historial de servicios proporcionado muestra un intervalo de mantenimiento excedido por {kilometraje | tiempo | kilometraje y tiempo}, el cual se muestra en el análisis de intervalos de mantenimiento. Esto ya que el programa estipula la realización de los mantenimientos del fabricante cada 6 meses o 10,000 KM, lo que ocurra primero, y está previsto en los artículos que se transcriben»; `desarrollo` con el párrafo del paso 8; `numerales: ["14.3"]` (+ `"14.4"` si hubo requerimiento formal sin respuesta en 72 h); `clausulasLiterales` con la **11** completa (numeral «11», título «MANTENIMIENTOS PERIÓDICOS») y, si se quiere reforzar, `{ numeral: "Póliza MMDM", titulo: "DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO O FALTA DE SEGUIMIENTO DEL PROGRAMA DE MANTENIMIENTO RECOMENDADO", texto: … }` literal del Anexo B.

### 4.5 Sin comprobantes de mantenimiento (decisión de Omar, 28/10/2026)

En Mitsubishi el PDF del área manda «Solicitar facturas, sellos o historial legible» y la póliza MMDM dice que «la negación no se basará únicamente en la ausencia de registros de mantenimiento». Por tanto, sin ningún comprobante **el caso queda 🟡** (no se rechaza por mantenimiento; no se concluye 🟢 por inferencia salvo que otra causal decida con evidencia suficiente o aplique el caso especial de la bomba L200, 4.7), y Claude **propone el comentario** para pedirlos, que se publica en SIGA con `comentar_averia` (ensayo → `confirmar: true` + `plan`) **sólo tras la confirmación del técnico** («Enviar» o «Uso Interno»). Plantilla (en el tono de 3.3; se adapta al folio):

> Hola, buen día. Se revisó la avería {folio} (VIN {vin}) y el expediente no permite acreditar el cumplimiento del plan de mantenimiento del fabricante (cada 6 meses o 10,000 KM). Favor de compartir, para el VIN del expediente, el historial completo de servicios desde la entrega de la unidad: facturas u órdenes de reparación de cada mantenimiento con fecha y kilometraje, o las páginas del cuaderno de mantenimiento con los sellos del distribuidor (fecha, KM y OR). Se requieren para verificar los intervalos entre servicios conforme al contrato. Con la información actual no es posible confirmar la procedencia. Quedamos atentos.

Si tras un requerimiento formal (este comentario, con fecha) pasan 72 h sin respuesta, 14.4 queda a decisión del técnico (motivo «Falta al proceso o incompleto (Distribuidor)»). Si llegan y muestran un desfase, 4.2.

### 4.6 Carta Compromiso y Reactivación de Garantía

**Carta Compromiso (rango 2) y Carta de Reactivación (rango 3): las tres comprobaciones del PDF del área** («La existencia de una carta no vuelve procedente automáticamente la avería…»): (1) el desfase medido en la tabla está dentro del rango que la carta o el criterio vigente autoriza; (2) la unidad cumplió lo que la carta pedía (servicio correspondiente, checklist, reacondicionamiento si aplicó), con su comprobante; (3) la carta es de esta póliza y de este VIN. Si falla una, la carta no cubre el desfase y se dice cuál falló.

**Rango 2 sin carta en el expediente → 🟡** con este comentario (se publica sólo tras la confirmación del técnico):

> Hola, buen día. Se revisó la avería {folio} (VIN {vin}). El análisis de intervalos muestra un desfase de {N} KM / {N} días entre el servicio del {fecha} y el del {fecha}, dentro del rango de 1,001 a 2,000 KM o 32 a 62 días que MMDM considera procedente bajo Carta Compromiso. Favor de compartir la Carta Compromiso firmada por el cliente para este VIN (el formato lo entrega el área de garantías de MMDM a solicitud del distribuidor). Con la carta en el expediente se continúa con la resolución.

**Rango 3 → 🟡 «candidato a Reactivación de Garantía»** con este comentario (sólo tras la confirmación del técnico); el folio **se queda en Validación** mientras corre el proceso (`contrato-mitsubishi.md` §8.5):

> Hola, buen día. Se revisó la avería {folio} (VIN {vin}). El análisis de intervalos muestra un desfase de {N} KM / {N} días entre el servicio del {fecha} y {el servicio del {fecha} | la avería}, dentro del rango de 2,001 a 6,000 KM o 63 a 186 días del Programa de Reactivación de Garantía de MMDM (MMDM-MG-007-2025). Para continuar con la resolución favor de: realizar el checklist de revisión técnica y el servicio de mantenimiento correspondiente al kilometraje actual; enviar la solicitud de reactivación a INVARAT (rodolfo.maldonado@invarat.mx) y a GarantiPlus (david.simancas@garantiplus.mx), con copia a mario.luna@garantiplus.mx, Jose.vences@na.mitsubishi-motors.com y Alexys.gonzalez@na.mitsubishi-motors.com, con los datos de la unidad, el motivo «Revisión por posible Reactivación de garantía», el checklist, el diagnóstico y la documentación del servicio; y cargar en este expediente la Carta de Reactivación firmada por el cliente junto con el comprobante del servicio. Una vez reactivada la garantía se resolverá la avería.

Cuando la reactivación consta (carta firmada + checklist + servicio), el caso es 🟢 y **la avería del folio se valora al 100 %** (MSRP −10 %); el reacondicionamiento del checklist es aparte (50 % GarantiPlus en componentes cubiertos, 50 % cliente; desgaste 100 % cliente). Si el distribuidor o el cliente **declinan** (lo dice el Seguimiento o el técnico), el caso es 🔴 por 14.3 con la 11, y el `desarrollo` lo dice (4.3, paso 8). **Reincidencia:** 4.2.

### 4.7 Fuera de la regla

La bomba de combustible L200 diésel MY25 en campaña se autoriza «aun cuando existan incidencias de mantenimiento» (sección 5.3). «No cumplió» vs. «no acreditó» (de v1 e `instructions.md` regla 14): comprobantes que muestran un tramo de rango 4 (o rangos 2–3 declinados) = **no cumplió** → 14.3; comprobantes requeridos formalmente y no entregados en 72 h = **no acreditó** → 14.4; comprobantes que nadie ha pedido = ninguna de las dos: se piden (4.5) y el caso es 🟡.

---

## 5. Criterios técnicos de cobertura y casos especiales (contrato §4–§6; PDF §4; cláusulas 1, 2, 3, 10 y 15)

### 5.0 Cobertura defensa a defensa salvo exclusión expresa (decisión de Omar, 28/10/2026)

`contrato-mitsubishi.md` §4: todo elemento mecánico, eléctrico o electrónico montado de origen está cubierto («defensa a defensa», 7 años sin límite de km) salvo que esté en una lista de exclusión expresa (cláusula 2; «PARTES Y SERVICIOS NO CUBIERTOS», «PARTES CON GARANTIA DIRECTA DEL FABRICANTE») y la exclusión esté probada. Las listas de «PARTES CUBIERTAS» son ilustrativas. **Un componente que no está en ninguna lista está cubierto**: un rechazo por «componente excluido» exige nombrar el inciso o la sección que lo excluye. Las reconciliaciones de `contrato-mitsubishi.md` §5.3 se aplican tal cual (soportes cubiertos salvo pérdida de morfología probada; juntas y sellos cubiertos como parte de un componente cubierto; banda de distribución cubierta por defecto dentro de su intervalo; batería 12 V hasta 24 meses; bujías de platino o iridio; Smart Display Audio 3 años / 60,000 km; catalizador y DPF por defecto). Subgarantías con plazo propio en `contrato-mitsubishi.md` §3.2.

### 5.1 Principio (PDF §4, literal)

> «El diagnóstico debe explicar qué falló y por qué. No basta con que una pieza esté mencionada en el presupuesto: debe existir correspondencia entre síntoma, pruebas, daño observado y reparación propuesta.»

**Pieza cubierta ≠ causa cubierta.** Se evalúan las dos, en este orden:

1. **Componente** (contrato §4–§5): cubierto salvo que esté en la lista literal de la cláusula **2** (asientos y mecanismos, habitáculo y maletero, neumáticos y válvula, carrocería, cristales, faros e intermitentes, molduras y espejos, consumibles —filtros, aceite, juntas, amortiguadores, escapes, discos, pastillas, correas, servicio periódico, lubricantes, combustibles, aditivos, carga de a/a salvo que la necesite una avería cubierta, bujías, calentadores, batería, escobillas, plumas— y elementos que perdieron su morfología —bujes, gomas, soportes, juntas—) o en las listas de la póliza MMDM (consumibles y lubricantes; partes con garantía directa del fabricante), **con las reconciliaciones de `contrato-mitsubishi.md` §5.3** (5.0). No hay periodo de espera de 90 días ni lista de componentes por producto. En un **PHEV**, la cláusula **3** cubre batería de alto voltaje y componentes eléctricos (motor eléctrico, motor eléctrico del sistema de refrigeración, líneas de alta tensión, conexión regular de carga, inversor – PHEV-ECU, conexión de carga rápida, trans eje, cargador a bordo / convertidor DC-DC) 7 años sin límite de km desde el inicio de la garantía, pero **no** la pérdida gradual de retención de carga.
2. **Causa** (contrato §6): cláusula **1** (1.4: AVERÍA/AS = inutilidad operativa por rotura imprevista / fortuita; la reducción gradual proporcional a antigüedad y km no es avería, contada desde la primera matriculación; tampoco la derivada de accidentes o influencias externas), **10** (no cubre uso inadecuado ni deterioro o desgaste normal), los 28 ítems de la **15** (tabla 5.6) y las secciones de causa de la póliza MMDM (ALTERACIÓN, ABUSO O DAÑO POR ACCIDENTE; MODIFICACIONES; DAÑOS MENORES; VEHÍCULOS CON ODÓMETRO ALTERADO…). **Cada una exige la evidencia de `contrato-mitsubishi.md` §6.4**; sin ella, la causa se trata como cubierta.
3. **Criterio técnico del área** (5.2) y **casos especiales vigentes** (5.3).

### 5.2 Tabla de situaciones (PDF §4, literal y completa)

| Situación | Criterio operativo |
| --- | --- |
| Componentes menores | «Aplicar un criterio más permisivo cuando la evidencia confirma una falla interna y no existen indicios de golpe, manipulación, negligencia o exclusión expresa.» |
| Motor, transmisión o batería de alto voltaje | «Revisión estricta: diagnóstico concluyente, desmontaje cuando sea necesario, causa raíz, mantenimientos completos, evidencia y presupuesto detallado.» |
| Desgaste prematuro | «Antes de 140,000 KM no rechazar automáticamente por desgaste cuando el componente se encuentre en el listado Mitsubishi autorizado. Aun así, revisar mantenimiento, montaje, daño externo y exclusiones.» |
| Daño externo | «Golpe, colisión, objeto, deformación, manipulación o uso indebido requieren análisis de exclusión y evidencia específica.» |
| Daño consecuencial | «Distinguir el componente que originó la falla de piezas afectadas como consecuencia; justificar técnicamente la relación causal.» |
| Reparación parcial | «Preferir reparación viable frente al reemplazo completo cuando técnicamente sea segura y suficiente.» |

Cómo se aplica:

- **Componentes menores**: el PDF no los enumera. Lectura de este archivo: sensores, actuadores, módulos, interruptores y piezas eléctricas o mecánicas de bajo costo fuera de motor, transmisión y batería de alto voltaje. Con falla interna confirmada (código + medición, pieza que deja de funcionar) y sin indicios de golpe, manipulación, negligencia o exclusión expresa, un expediente delgado no basta para rechazar.
- **Motor, transmisión, batería de alto voltaje**: las seis exigencias son acumulativas. Falta una → 🟡 pidiendo exactamente esa (sección 3.2); el desmontaje, sólo «cuando sea necesario» y con la autorización de 12.4 (si el taller desmontó por su cuenta antes de la resolución, 14.1).
- **Desgaste prematuro antes de 140,000 KM**: **el «listado Mitsubishi autorizado» no está en el conector ni en el Conocimiento del proyecto**. Si el componente pudiera estar en él, se pregunta al técnico si lo está (fuente `Técnico`); no se supone ni en un sentido ni en otro. Si está y la unidad tiene menos de 140,000 KM, el desgaste no se rechaza automáticamente (ni por 1.4, ni por 10, ni por 15.3); se revisan igual mantenimiento, montaje, daño externo y exclusiones. Si no está, o la unidad pasa de 140,000 KM, se aplica el certificado.
- **Daño externo**: no basta la sospecha; hace falta evidencia específica (fotos de impacto, deformación, objeto, rastro de manipulación) para citar 15.12, 15.14, 15.18 o 1.4 («influencias externas»). Una «fotografía aislada de una pieza rota no sustituye el diagnóstico» cuando cabe golpe o manipulación (sección 3.1).
- **Daño consecuencial**: se separa la pieza que originó la falla de las afectadas. Si la originaria está cubierta, las consecuentes se valoran con ella si la relación causal está justificada técnicamente; si la originaria está excluida (por ejemplo, banda de distribución → motor, 15.8), las consecuentes siguen su suerte. Las «pérdidas consecuencia de la AVERÍA/AS o del retraso» (15.26) son otra cosa: daños indirectos, nunca piezas.
- **Reparación parcial**: si una reparación parcial es técnicamente viable, segura y suficiente, se autoriza ésa y no el conjunto completo (también es control obligatorio del presupuesto, sección 6.3). Si el taller pide el conjunto y no hay evidencia de que la parcial sea viable, se dice y decide el técnico; no se inventa una reparación alternativa ni su precio.

### 5.3 Casos especiales vigentes (PDF §4, tabla literal) — **actualizado en v2**

| Caso | Tratamiento |
| --- | --- |
| Bomba de combustible L200 diésel nueva generación MY25 | «Autorizar conforme a la campaña de satisfacción aplicable, aun cuando existan incidencias de mantenimiento, siempre que la unidad y la falla correspondan a la campaña.» |
| Sensor de temperatura de gases de escape | «Considerarlo cubierto cuando el diagnóstico corresponda al sensor EGT, aunque el sistema o presupuesto lo haya clasificado erróneamente como sensor de oxígeno.» |
| Portalentes y mangueras de A/C | «Considerarlos cubiertos conforme a la indicación de MMDM, verificando que la avería corresponda realmente a dichos componentes.» |
| Boletín o campaña técnica | «Verificar VIN, modelo, síntoma, componente y condiciones de aplicación. La sola existencia del boletín no basta si corresponde a otra unidad o falla.» |

Esto **resuelve lo que v1 tenía pendiente** («las condiciones especiales del programa que David quedó de mandar: bomba de combustible y otras»). Cómo se aplican:

- **Bomba L200 MY25**: se comprueba que la unidad es L200 diésel de nueva generación MY25 (VIN, póliza, carátula) y que la falla es la de la campaña de satisfacción. El texto de la campaña no está en el Conocimiento: si el expediente no la trae y el técnico no confirma que la unidad y la falla corresponden, es 🟡 (pedir al técnico o al distribuidor la campaña aplicable). Si corresponde, procede aunque haya tramos de mantenimiento excedidos; la viñeta lo dice («Caso especial vigente: bomba L200 MY25, campaña de satisfacción; mantenimiento con incidencias no bloquea»). Tensión con 15.11 («campañas del fabricante» no cubiertas): sección 12.
- **Sensor EGT clasificado como O2**: manda lo que dice el diagnóstico, no el rótulo del presupuesto o de SIGA. Si el diagnóstico corresponde al sensor de temperatura de gases de escape, se trata como cubierto (salvo otra causal: mantenimiento, daño externo…). En el Informe y en los renglones se nombra la pieza como la identifica el diagnóstico. (El rechazo de 166585, sensor O2, fue por mantenimiento: no contradice este caso.)
- **Portalentes y mangueras de A/C**: cubiertos «conforme a la indicación de MMDM», verificando que la avería sea realmente de esos componentes (y no, por ejemplo, del compresor o del condensador). Tensión con 2.9 y 15.4 (mangueras y elementos que pierden su morfología) y con 15.5 (fugas, cargas de a/a): sección 12. La carga de a/a necesaria para esa reparación sigue la salvedad de 2.8 («salvo que sea necesario por avería cubierta»).
- **Boletín o campaña técnica en general**: se verifican los cinco puntos (VIN, modelo, síntoma, componente, condiciones de aplicación). Un boletín de otra unidad o de otra falla no cuenta. Un boletín no convierte por sí solo la falla en «Campaña y/o Fallo epidémico» (15.11) ni en cubierta.

### 5.4 No generalizar (recuadro del PDF §4, literal)

> «Un antecedente aceptado no crea cobertura universal. Cada avería debe conservar trazabilidad con su contrato, VIN, diagnóstico y evidencia.»

Los folios que cita este archivo (166585, 162031) ilustran cómo cita el área; no deciden otro caso.

### 5.5 Las dos reglas del área que ahora tienen cláusula (póliza MMDM) — **actualizado en v4**

Decisión de Omar del 2026-09-25: «el odómetro no retrocede» y «ruidos, zumbidos y vibraciones no se cubren». Hasta v3 se aplicaban como «cláusula especial del programa» sin texto; desde v4 **tienen cláusula en la póliza MMDM** y se citan con `clausulasLiterales` (`numeral: "Póliza MMDM"`, `titulo` exacto, texto literal del Anexo B de `contrato-mitsubishi.md`):

- **Ruidos, zumbidos y vibraciones → «DAÑOS MENORES»:** «Pequeñas irregularidades que no afectan la calidad, el rendimiento o la función del vehículo o sus partes (por ejemplo, un ruido leve o vibración) o que aparecen en particular solo en operaciones anormales.» Más la 1.4 (la avería exige **inutilidad operativa**). **Lectura flexible:** sólo aplica cuando el diagnóstico no identifica una pieza inutilizada ni un defecto, sólo el síntoma; si el ruido viene de un componente que falló (rodamiento, soporte roto, junta homocinética, tensor), **es avería de ese componente y se cubre**.
- **El odómetro no retrocede → «VEHÍCULOS CON ODÓMETRO ALTERADO»:** «Si no se puede determinar o representar fielmente el kilometraje del vehículo por alteración o paro del odómetro.» Un kilometraje que baja entre documentos, o un km de avería menor que el de inicio, es alerta de integridad: se pide aclaración (3.3) antes de rechazar; si se confirma la alteración, se cita esta sección (y 14.3 por la imposibilidad de verificar los mantenimientos).

Siguen siendo criterio: se enseñan con su fuente y decide el técnico.

### 5.6 Causas y partidas: numeral del certificado → motivo de catálogo de SIGA

Traducción de la tabla de `casos-garantiplus.md` §6 a la numeración Mitsubishi (para escoger el motivo; **se cita siempre el numeral del Anexo A de `contrato-mitsubishi.md`**, y el motivo se escoge por el hecho):

| Causa documentada | Numeral Mitsubishi | Motivo de catálogo |
| --- | --- | --- |
| Componente en la lista de exclusiones | 2.N | Componente excluido |
| Defecto previsible (más de 50 vehículos, mismo componente o falla específica, defectos de fabricación, ensamble o desgaste prematuro) | 15.1 | Campaña y/o Fallo epidémico (o Preexistente, si el hecho es anterior a la cobertura); decide el técnico |
| Consecuencia de una mala reparación anterior | 15.2 | Mala Reparación Anterior |
| Fin de vida útil; erosión, corrosión, deformación; pérdida de morfología (bujes, gomas, soportes, juntas, mangueras, retenes) | 15.3, 15.4 | Daño por uso o degradación |
| Consumibles; fugas de aceite, refrigerante o combustible; batería, frenos, correas, escapes, catalizador | 15.5 | Componente excluido (Fuga excluida si es fuga) |
| Software, actualizaciones, programaciones | 15.6 | Componente No incluido en cobertura |
| Falla de un elemento no garantizado; motor dañado por falla de la banda de distribución | 15.8 | Componente No incluido en cobertura (o Componente excluido) |
| Defecto de serie, diseño defectuoso, vicio oculto o fallo epidémico, campaña del fabricante | 15.11 | Campaña y/o Fallo epidémico |
| Alteración de la especificación del fabricante; accesorios o piezas no de origen | 15.12, 15.23 | Influencia Externa |
| Siguió circulando con testigos encendidos | 15.13 | Negligencia de uso |
| Mal uso o negligencia, competiciones, sobrecarga, abrasivos | 15.14–15.17 | Negligencia de uso |
| Accidente, robo, incendio, explosión, vandalismo, catástrofe natural | 15.18 | Siniestro |
| Combustibles o lubricantes no conformes o contaminados | 15.22 | Influencia Externa |
| Trabajo sobre el vehículo antes de la resolución; vehículo no inmovilizado | 14.1, 14.2 (con 12.4) | Falta al proceso o incompleto (Distribuidor) |
| Mantenimientos o inspecciones no cumplidos | 14.3 (con 11) | Intervalo de Mantenimiento Excedido |
| Documentación del artículo 12 no aportada en 72 h tras requerirla | 14.4 | Falta al proceso o incompleto (Distribuidor) |
| Comunicada fuera de vigencia; ocurrida fuera de vigencia | 14.5; 5.1 | Sin Vigencia |
| No es avería (desgaste gradual, influencia externa) | 1 (definición 1.4), 10 | Daño por uso o degradación (o Influencia Externa) |
| Ruido, zumbido o vibración sin componente fallado | 1 (definición 1.4) + `Póliza MMDM — DAÑOS MENORES` (literal) | Daño por uso o degradación (decide el técnico) |
| Odómetro alterado o que retrocede, confirmado | `Póliza MMDM — VEHÍCULOS CON ODÓMETRO ALTERADO` (literal) + 14.3 | Falta de relación en VIN / Intervalo de Mantenimiento Excedido (decide el técnico) |
| Modificación, chip, reprogramación, accesorio no original, blindaje | 15.12, 15.23 + `Póliza MMDM — MODIFICACIONES` (literal) | Influencia Externa |
| Estéreo o neumático fuera de su plazo | `Póliza MMDM — PARTES CON GARANTIA DIRECTA DEL FABRICANTE` (literal) | Componente excluido (se orienta al distribuidor a la garantía directa del fabricante) |
| Desfase de mantenimiento en rangos 2–3 declinado, o de rango 4 | 14.3 (con 11) + `Manual MMDM-MG-007-2025` en `desarrollo` | Intervalo de Mantenimiento Excedido |

**Partidas que nunca se cubren aunque la avería proceda:** diagnóstico si la avería no procede (15.7), mantenimiento preventivo (15.9), controles y reglajes (15.10), piezas cambiadas sin fallar (15.19), asistencia in situ (15.20), grúa y transporte (15.21, 15.24), estacionamiento o almacenamiento (15.25), daños consecuencia de la avería o del retraso (15.26), lucro cesante (15.27), daños a terceros (15.28). La 14.6 («cualquier tipo de incumplimiento») nunca se usa sola.

---

## 6. Presupuesto, MSRP −10 % y la lista de precios en el conector (PDF §5)

### 6.1 La regla del área (recuadro «REFACCIONES», literal)

> «Para Mitsubishi, el precio autorizado de refacciones se calcula normalmente con MSRP menos 10 %. Confirmar que la base utilizada sea el MSRP correcto y que no se haya aplicado previamente el descuento.»

«Normalmente»: si el técnico trae una instrucción distinta para un folio (otro precio autorizado), se registra con fuente `Técnico` y vale sólo para ese folio.

### 6.2 Fórmula operativa (PDF §5, tabla literal)

| Concepto | Cálculo |
| --- | --- |
| Refacción autorizada | MSRP × 0.90 |
| Subtotal | Suma de refacciones autorizadas + mano de obra autorizada |
| IVA | Subtotal × tasa de IVA aplicable |
| Total autorizado | Subtotal + IVA, sujeto a límites y deducibles del contrato |

Notas:

- La lista de Mitsubishi da los precios **en moneda nacional y sin IVA**; MSRP × 0.90 es, por tanto, un precio **sin IVA**. En Mitsubishi la valoración se arma **sin IVA por partida, con el IVA desglosado y el total con IVA**: en `generar_resolucion` van `valoracion.partidas` sin IVA, `valoracion.iva` = subtotal × tasa y `valoracion.totalConIva` = subtotal + IVA. Esto choca con la regla general del proyecto («los importes de los presupuestos ya incluyen IVA; no se calcula IVA»): para Mitsubishi manda la fórmula del área (sección 12).
- **Tasa de IVA aplicable**: 16 % salvo que el presupuesto o el técnico indiquen otra (por ejemplo, región fronteriza). No se supone otra tasa.
- **Refacción autorizada** por renglón = MSRP unitario × 0.90 × cantidad autorizada. Se escriben los centavos tal cual salen del cálculo, redondeados a dos decimales, y la suma se comprueba («Comprobar que el importe escrito coincida con la suma de la tabla», sección 7.2).
- **Mano de obra autorizada**: el PDF no fija tarifa ni horas para Mitsubishi. Se valida contra el diagnóstico (que las operaciones correspondan a la reparación autorizada, sin duplicidad, separada de diagnóstico y consumibles, sección 6.3) y se autoriza la del presupuesto validado; cualquier ajuste lo decide el técnico (fuente `Técnico`).
- **Límites y deducibles**: la cláusula 13 limita la valoración al valor de venta del libro azul (13.1) o al valor medio de mercado (13.2). El certificado del programa no menciona deducible; si la póliza de la unidad lo trae, se aplica como diga y sólo conforme a esa póliza.

### 6.3 Controles obligatorios del presupuesto (PDF §5, los seis, literal)

1. «Confirmar que cada partida corresponda al diagnóstico y no exista duplicidad.»
2. «Verificar cantidades, números de parte, precios unitarios, mano de obra e IVA.»
3. «Revisar si el presupuesto ya muestra el descuento de 10 % para evitar aplicarlo dos veces.»
4. «No autorizar conjuntos completos cuando una reparación parcial sea técnicamente viable.»
5. «Separar consumibles, diagnóstico y operaciones de mano de obra para evitar cobros duplicados.»
6. «Aplicar topes, deducibles o límites particulares únicamente conforme al contrato de esa avería.»

### 6.4 Las dos herramientas de precios del conector (nuevas, 27/10/2026)

El MSRP sale de la **lista de precios mensual de Mitsubishi**, un Excel enorme (octubre 2026: unos 160,000 renglones) que no cabe en el chat. El conector la guarda y la consulta como una base de datos. Con estas dos herramientas el conector pasa de trece a quince; mientras no estén publicadas, no se llaman (si no aparecen entre las herramientas del conector, se dice y el técnico consulta la lista a mano).

**`consultar_precios_mitsubishi`** — sólo lee la lista vigente (o una versión anterior). Parámetros:

| Parámetro | Para qué |
| --- | --- |
| `numerosDeParte` | Lista de números de parte (todos los del presupuesto **en una sola llamada**). Coincidencia exacta, sin importar guiones, espacios, puntos ni mayúsculas. Si una fila tiene `SS`, sigue la sustitución (hasta 5 saltos) y enseña también la fila sustituta. Los que no aparecen, los nombra. Un número de parte repetido en el Excel sale en todos sus renglones con la nota «repetido en el Excel»: no se suma dos veces. |
| `buscar` | Texto libre en todas las columnas de texto, sin acentos y tolerando los acentos dañados del Excel («cigüeñal» encuentra «Cig£e‹al»). Para cuando el presupuesto no trae número de parte. Las descripciones vienen en inglés: se busca por el nombre en inglés de la pieza («WATER PUMP», no «bomba de agua»); las palabras pueden ir en cualquier orden. |
| `filtros` | Columna + operador + valor (`contiene`, `igual`, `distinto`, `empieza`, `mayor`, `mayorIgual`, `menor`, `menorIgual`, `entre` con `hasta`, `vacio`, `noVacio`), por cualquier columna. |
| `columnas` | Qué columnas enseñar. |
| `ordenarPor` | Columna por la que ordenar. |
| `limite`, `desde` | Cuántos renglones (por omisión 25, máximo 200) y desde cuál (paginación). |
| `describir` | `true`: explica la lista (columnas presentes con tipo y ejemplos, mes y vigencia, versiones guardadas). Se usa cuando la lista cambió de formato o no se sabe qué columnas trae. |
| `version` | Consultar una versión anterior en lugar de la vigente (por ejemplo, la del mes del presupuesto, si el técnico lo pide). |

Columnas de la lista de octubre 2026 (pueden cambiar de un mes a otro; con `describir: true` el conector dice cuáles hay): `Numero de Parte`; `Descripcion` («NOMBRE EN INGLÉS;categoría en español», con acentos dañados en el Excel original); `SS` (número de parte que sustituye: supersesión); `Category` (Mechanical, Collision, Maintenance, Accessories, Dropship); `DNP` (precio al distribuidor); `MSRP` (precio de lista); `MAPFRE`, `GNP`, `CHUBB`, `QUALITAS`, `AXA` (en la lista de octubre, cada una = MSRP −10 %). Todos los precios en moneda nacional **sin IVA**. Cada renglón trae además la columna calculada por el conector **«MSRP −10 %»** (MSRP × 0.90), marcada como cálculo.

La cabecera de cada respuesta identifica la lista: **versión, mes, vigencia** (por ejemplo, «Precios validos del 09 al 31 de Octubre del 2026»), archivo y fecha de carga, y si los precios son sin IVA. Así se sabe qué lista se usó.

**`actualizar_precios_mitsubishi`** — baja de Google Drive el Excel más nuevo de la carpeta «Precios Mitsubishi» (o el que se nombre en `archivo`), lo lee, lo valida y lo deja vigente. Responde qué archivo cargó, **de qué mes es** y su vigencia, cuántos renglones y columnas trae y qué cambió respecto de la lista anterior; si ya era el vigente, lo dice y no hace nada. **Se niega** a dejarlo vigente si el archivo más nuevo es **de un mes anterior** al de la lista vigente o trae **muchos menos renglones** (menos de la mitad), salvo con **`forzar: true`**, que sólo se manda **si el técnico lo pide después de ver el aviso**. También se niega si el archivo no tiene columna de número de parte o no tiene renglones, o si no es `.xlsx` ni Hoja de cálculo de Google (un `.xls` o `.csv` hay que subirlo como `.xlsx`). No cambia SIGA: cambia la lista que el conector sirve a todos, por eso no se llama sin que el técnico lo pida. La lista es una sola para producción y pruebas.

**Dónde sube el técnico el Excel del mes** (dáselo tal cual si lo pide):

- Carpeta del proyecto: https://drive.google.com/drive/folders/1YJ4nl6u5FWoW7CSCwqqmj0GIWFYL15TB?usp=drive_link
- Subcarpeta **«Precios Mitsubishi»** (aquí va el Excel): https://drive.google.com/drive/folders/1bmvE9W8W5rLgXW03SKf7o6Ke8QvSunqD

Flujo para actualizar: el técnico sube el Excel nuevo a «Precios Mitsubishi» → pide «actualiza la lista de precios de Mitsubishi» → `actualizar_precios_mitsubishi` → se le lee entero lo que respondió (archivo, mes, vigencia, renglones, cambios o el aviso por el que se negó). Si se negó, se le enseña el motivo y sólo con su petición explícita se repite con `forzar: true`.

### 6.5 Regla de uso en todo caso Mitsubishi procedente

1. **Consulta única.** Con el presupuesto leído, llama `consultar_precios_mitsubishi` con `numerosDeParte` = **todos** los números de parte de las refacciones del presupuesto, en una sola llamada. Si una refacción no trae número de parte, se busca con `buscar` **en inglés** (como vienen las descripciones de la lista: «WATER PUMP», «BRAKE PAD», «CLUTCH DISC») y se enseña lo encontrado como candidato, sin darlo por bueno: decide el técnico o se pide el número de parte al distribuidor.
2. **Lista correcta.** Lee la cabecera: mes y vigencia. Si la lista vigente no cubre la fecha de la valoración (es de un mes que no corresponde, o su vigencia ya terminó), **dilo al técnico** y sugiérele subir la nueva a la carpeta y pedir la actualización; no se valora en silencio con una lista vencida. Usar una lista anterior (`version`) es decisión del técnico.
3. **Cotejo por refacción**, en una tabla en el chat: número de parte · descripción · cantidad · precio unitario del taller · MSRP · MSRP × 0.90 · diferencia · lectura. Se compara **en la misma base** (sin IVA contra sin IVA). Lecturas posibles:
   - Precio del taller = MSRP (salvo redondeo de centavos) → **se aplica el 10 %**: autorizado = MSRP × 0.90.
   - Precio del taller = MSRP × 0.90 → **el taller ya aplicó el descuento**: no se aplica otra vez; autorizado = MSRP × 0.90 (control 3 de 6.3; checklist «MSRP −10 % aplicado una sola vez»).
   - Precio del taller **menor** que MSRP × 0.90 → se dice; el área autoriza normalmente MSRP × 0.90, pero no se autoriza más de lo que pide el taller sin que el técnico lo decida.
   - Precio del taller entre ambos, o mayor que MSRP → se dice con la diferencia; autorizado = MSRP × 0.90 salvo decisión del técnico.
   - Si el presupuesto no desglosa IVA y no se sabe si su precio unitario lo incluye, no se compara en silencio: se enseñan los dos cálculos (con y sin IVA) y decide el técnico.
4. **Supersesión.** Si el número del presupuesto tiene `SS`, el conector enseña la fila sustituta; si sus MSRP difieren, se enseñan los dos y el técnico dice cuál vale.
5. **Número de parte que no está en la lista**: se dice tal cual («no aparece en la lista {mes}») y **no se inventa precio**. Opciones para el técnico: pedir al distribuidor el número de parte correcto, buscar por texto, o autorizar con otro criterio suyo (fuente `Técnico`).
6. **Valoración.** Partidas de refacción = MSRP × 0.90 × cantidad; mano de obra autorizada (6.2); subtotal; IVA; total. Se aplican límites del contrato (13) y, si existieran en la póliza, deducibles. Si el total supera **$100,000**, se activa la autorización especial (sección 7.3).
7. **Al Informe y a SIGA, la misma cifra.** El cuadro del Informe (sección 10) y los renglones de `aprobar_averia` llevan el precio autorizado (MSRP × 0.90), no el del taller; la tabla de parámetros del mensaje 2 enseña, renglón por renglón, el precio del taller junto al autorizado y la lista usada («MSRP −10 %, lista {mes}, versión {v}»). La regla de cuadre de `instructions.md` §4.4 sigue: suma de renglones (sin IVA) + IVA = total del Informe, al centavo. El precio que se escribe en cada renglón de SIGA sigue la forma en que el taller cargó ese renglón (unitario o importe, según lo que enseñe `renglones_averia`).

---

## 7. Resultado del análisis y autorizaciones (PDF §5 y §6)

### 7.1 Los tres resultados (PDF §6, tabla literal)

| Resultado | Cuándo aplica | Documento | En el proyecto |
| --- | --- | --- | --- |
| Aceptada | «Contrato vigente, componente cubierto, causa procedente, mantenimiento conforme o excepción autorizada, evidencia suficiente y presupuesto validado.» | «Resolución con campos y valoración; sin texto técnico de justificación.» | 🟢 PROCEDE (o PROCEDE parcial) → `generar_resolucion` procedente → `subir_resolucion` → `aprobar_averia`. |
| Rechazada | «Existe exclusión contractual demostrable, falta de mantenimiento acreditada, fuera de vigencia, preexistencia sustentada, daño externo u otro supuesto contractual.» | «Resolución con fundamento textual, numeral, evidencia y tabla cuando aplique.» | 🔴 NO PROCEDE → `generar_resolucion` improcedente → **visto bueno de Alexys** → `subir_resolucion` → `rechazar_averia`. |
| Requiere información | «Falta un dato esencial o existe contradicción de VIN, diagnóstico, mantenimiento, causa o presupuesto.» | «Comentario específico; no forzar aceptación ni rechazo.» | 🟡 PENDIENTE → comentario de la sección 3 con `comentar_averia`. |

«Mantenimiento conforme **o excepción autorizada**»: una carta de compromiso válida (4.6), el caso especial de la bomba L200 (5.3) o una excepción del técnico con quien la autorizó (🟢 PROCEDE (ATC) si es atención comercial).

### 7.2 Reglas por resultado (PDF §6, literal)

**Aceptaciones:**
- «Llenar número de avería, contrato, marca, modelo, VIN, fecha y KM de avería.» (La cubierta Mitsubishi lleva «MITSUBISHI» fijo como marca; los otros seis van en `encabezado`, más `fechaCierre`.)
- «Incluir la valoración con conceptos autorizados, mano de obra y total con IVA.»
- «No agregar un párrafo explicando por qué se acepta.» (En el conector: sin `desarrollo` ni `numerales`; el procedente sólo lleva el cuadro.)
- «Comprobar que el importe escrito coincida con la suma de la tabla.»

**Rechazos:**
- «No usar motivos genéricos ni copiar numerales de otro contrato.» (Nada de la numeración de GarantiPlus —su «12.4» de las 72 h es aquí 14.4; su «13.8» es 15.7—: sección 8.)
- «Citar el artículo y numeral exactos del contrato de la avería.»
- «Relacionar el hecho probado con la exclusión aplicable.»
- «Incluir tabla de mantenimientos cuando el rechazo se base en intervalos excedidos.» (La imprime el conector: 4.4 y 10.4.)
- «El visto bueno de Alexys es obligatorio antes de cambiar el estatus a rechazo.»

**Comentarios:** «El comentario debe permitir que el distribuidor corrija el expediente sin adivinar lo solicitado. Debe ser corto, específico y verificable: documento, VIN, prueba, diagnóstico, dato o presupuesto requerido.» (Sección 3.)

### 7.3 Autorizaciones especiales (PDF §5, tabla literal) y cómo entran en el flujo

| Supuesto | Acción |
| --- | --- |
| Monto superior a $100,000 | «Preparar el análisis y solicitar autorización especial antes de emitir la aceptación definitiva.» |
| Rechazo | «Obtener visto bueno de Alexys antes de ejecutar el rechazo en SIGA.» |
| Datos o montos incompletos | «Generar Word editable para revisión; no convertir a PDF definitivo hasta confirmar los campos.» |

Cómo se cumplen con el conector (pasos obligatorios del flujo, no opcionales):

- **Rechazo → visto bueno de Alexys.** En un 🔴, el mensaje 2 (documento + tabla de parámetros) añade una línea: `Visto bueno de Alexys: pendiente` (o `obtenido — {quién lo confirma y cuándo}`, si el técnico ya lo dijo). La pregunta cambia a: `¿Ya tienes el visto bueno de Alexys? Sí, confirmo / Todavía no / Corregir`. **Sin el visto bueno confirmado por el técnico no se sube el Informe ni se llama a `rechazar_averia`**, ni siquiera el ensayo. Con «Todavía no», el trabajo termina con el Informe generado y la tabla lista; cuando vuelva con el visto bueno, se retoma (otro ensayo, porque el plan vale 60 minutos). El visto bueno queda en la bitácora (columna «autorizó»: el técnico, y «VoBo Alexys» con lo que él haya dicho). Claude no lo da por obtenido ni lo infiere.
- **Monto superior a $100,000 → autorización especial.** Se compara el **total autorizado con IVA** del cuadro (el PDF no dice si es con o sin IVA; se toma el total por prudencia y se dice). Si lo supera, el mensaje 2 lleva `Autorización especial (> $100,000): pendiente`, y **no se sube el Informe ni se llama a `aprobar_averia`** hasta que el técnico confirme que la tiene y de quién (el PDF no dice quién la da; no se inventa). El Informe puede generarse para preparar el análisis.
- **Datos o montos incompletos → Word editable.** El conector no genera un Informe con un campo del encabezado vacío (lo rechaza y dice cuál), y siempre produce Word y PDF a la vez. Si falta un dato de encabezado, no se genera: se pide (sección 3). Si lo que falta es un dato del cuerpo o un monto que el técnico quiere revisar, se puede generar y darle el enlace **«Descargar Word»** para revisión, con el dato pendiente señalado **en el chat, fuera del texto del Informe**; ese documento **no se sube** a SIGA hasta que el técnico confirme los campos y se regenere el definitivo con ellos (o se regenera con el dato confirmado).
- **«No modificar estatus ni cargar archivos sin autorización expresa»** se cumple con los dos pasos del conector: `subir_resolucion`, `comentar_averia`, `rechazar_averia` y `aprobar_averia` primero ensayan o anuncian, y sólo ejecutan con `confirmar: true` tras el sí explícito del técnico (el «Confirmo» a la tabla, `instructions.md` §4.5). En Mitsubishi ese «Confirmo» sólo vale si la tabla ya dice «obtenido» en el visto bueno o en la autorización especial que corresponda.

### 7.4 Control de cambios (recuadro del PDF §7, literal)

> «Cuando el encargo sea únicamente revisar y preparar resoluciones, la actividad termina con la entrega de los archivos. No se carga la resolución, no se registra comentario y no se cambia el estatus.»

Si el técnico pide sólo «revisa y prepara», el turno termina con el veredicto, el Informe generado (enlaces Ver, PDF, Word, bandeja) y, si quiere, la tabla de parámetros; **no** se llama a `subir_resolucion`, `comentar_averia`, `rechazar_averia` ni `aprobar_averia`, ni siquiera para ensayar.

---

## 8. Numeración del certificado (la de este certificado es la que vale)

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

El certificado está íntegro, con esta numeración, en `contrato-mitsubishi.md` Anexo A. **Cita siempre con la numeración de este certificado.** El área lo hace así en sus resoluciones Mitsubishi: 166585 (sensor O2, mantenimiento) citó **14** ítem 3 y **11**; 162031 (muelles, desgaste) citó **1**, **10** y **15**. Un Informe Mitsubishi que cite «12.3» por mantenimientos o «13.8» por diagnóstico está citando el contrato de otra cuenta (aquí son 14.3 y 15.7). Esto es también lo que pide el PDF: «No usar motivos genéricos ni copiar numerales de otro contrato» y «Citar el artículo y numeral exactos del contrato de la avería».

---

## 9. Cómo se lee un caso Mitsubishi, paso a paso

Fusiona el flujo operativo del PDF (§7, nueve pasos, literales al inicio de cada paso) con la lectura del certificado (v1 §3) y las herramientas del conector. Es el mismo esqueleto de `instructions.md` §4 (revisar → generar → confirmar) con lo que cambia en Mitsubishi.

1. **«Abrir la avería y confirmar que pertenece a Mitsubishi y al VIN correcto.»** `expediente_completo({ claimId })` (una llamada por folio). La ficha dice «MITSUBISHI (programa, sin contrato individual)», plantilla `mitsubishi`, contrato 57227 y el `policyId`. Se cruza el VIN de la ficha con los documentos (sección 2).
2. **«Descargar y revisar todos los documentos y evidencias disponibles.»** Todo lo que trajo `expediente_completo` (presupuesto, PRC, PQR, diagnóstico, odómetro, facturas y sellos de servicio, fotos, fotogramas de video); lo que quedó fuera, en una sola llamada a `leer_documento`; el audio de un video, con su enlace `/video`. No se dictamina con documentos sin leer. Se comprueba la documentación mínima (tabla 3.1).
3. **«Leer el contrato aplicable y verificar vigencia, cobertura, exclusiones y obligaciones.»** `contrato-mitsubishi.md` (certificado del programa + póliza MMDM + manual) + póliza de SIGA (+ carátula si existe), con la lectura flexible de 0.5:
   - **Vigencia** (5.1; comunicación fuera de plazo → 14.5): con la póliza de la ficha o la carátula; si no se puede confirmar, sección 1.
   - **Componente**: cubierto salvo cláusula **2** o listas de la póliza MMDM, con las reconciliaciones (5.0); **3** si es PHEV.
   - **Causa**: cláusula **1** (1.4), **10**, los ítems de la **15** (tabla 5.6), los criterios técnicos (5.2), los casos especiales (5.3) y las reglas del área de 5.5.
   - **Proceso**: la **12** (orden de entrada, presupuesto **sin intervenir ni desmontar**, facturas de mantenimiento; 72 h tras requerirlas → 14.4; vehículo inmovilizado → 14.2; trabajo previo a la resolución → 14.1) y la **14** (fuera de vigencia → 14.5; incumplimiento → 14.6, nunca sola).
   - **Límites**: **13** (libro azul).
4. **«Analizar mantenimientos y elaborar la tabla cuando sea necesaria.»** Sección 4: intervalo 6 meses / 10,000 KM y **los rangos de desfase de MMDM** (salvo que la póliza o el cuaderno de la unidad digan otra cosa), todos los servicios desde el inicio de la cobertura, la avería como última fila, días calculados con el calendario, Carta Compromiso o Reactivación si la hay (4.6). La tabla se enseña en el chat cuando hay desfase en rangos 2–4 o cuando el técnico la pide, y **en el Informe la imprime el conector** (4.4).
5. **«Validar diagnóstico, causa, evidencia y presupuesto.»** Correspondencia síntoma–pruebas–daño–reparación (5.1); los seis controles del presupuesto (6.3); en un caso que pueda proceder, `consultar_precios_mitsubishi` con todos los números de parte y el cotejo de 6.5.
6. **«Determinar aceptación, rechazo o información faltante.»** Veredicto en el formato de `instructions.md` §2 (🟢 / 🔴 / 🟡), con la primera viñeta del contrato (certificado del programa + póliza) y cada razón con su fuente. En 🔴, el motivo de catálogo (tabla 5.6). En 🟡, el comentario de la sección 3.3. Se dicen, si aplican, el visto bueno de Alexys y la autorización especial que harán falta.
7. **«Generar la resolución en Word; convertir a PDF sólo cuando esté completa.»** `generar_resolucion` con `plantilla: "mitsubishi"` (sección 10): genera Word y PDF definitivos a la vez; el Word sirve para revisar y editar, y el PDF es el que se sube cuando todo está completo y confirmado. Se abre «Ver en el navegador» si hay navegador integrado, y se lee `renglones_averia` para la tabla de parámetros.
8. **«Solicitar visto bueno en rechazos y autorización especial en montos mayores a $100,000.»** Sección 7.3: líneas propias en la tabla de parámetros y sin ejecutar hasta que el técnico confirme que las tiene.
9. **«No modificar estatus ni subir documentos hasta recibir autorización expresa.»** Con el «Confirmo» del técnico (y, si corresponde, el visto bueno o la autorización ya confirmados): `subir_resolucion` sin `confirmar` → con `confirmar: true`; ensayo de `rechazar_averia` o `aprobar_averia`; cotejo con la tabla; confirmación con el `plan`; verificación leída entera; bitácora (`instructions.md` §4.5). Si el encargo era sólo revisar y preparar, se detiene en el paso 7 (sección 7.4).

**Motivo de catálogo de SIGA:** el mismo desplegable de 18 motivos de `instructions.md` §6.1; la causal se escoge por el hecho (tabla 5.6) y en el Informe se cita el ítem de la 14 o la 15 que lo sostiene.

---

## 10. El Informe de Resolución en Mitsubishi

### 10.1 Formato Mitsubishi aprobado (PDF §7, literal)

> «La resolución debe conservar el formato Mitsubishi previamente aprobado. No cambiar encabezado, logotipo, colores, distribución, tipografía ni estructura salvo una instrucción expresa.»

El conector usa la cubierta Mitsubishi del área, con su banda negra, su logotipo y su cuadro de datos: **`cubierta-mitsu.docx`** en un procedente (informe con cuadro de valoración, carta de recepción y páginas de cobro) y **`rechazo-mitsu.docx`** en un improcedente (sólo el informe), igual que en GarantiPLUS; elige según el `veredicto`. Desde el 27/10/2026 las dos salen maquetadas para que el PDF se vea como el Word (antes el cierre se encimaba al cuadro y el rechazo arrastraba la carta y el listado de cobro). No se pide al conector otro formato, y si el técnico edita el Word (10.4) tampoco se toca nada de eso.

### 10.2 Campos y su fuente (PDF §7, tabla literal, con el campo del conector)

| Campo | Fuente (PDF) | Campo de `generar_resolucion` |
| --- | --- | --- |
| Número de avería | Expediente SIGA | `encabezado.numeroAveria` |
| Número de contrato | Póliza o encabezado de la avería | `encabezado.numeroContrato` = `policyId` (nunca el 57227) |
| Modelo | VIN, póliza y evidencia; corroborar antes de emitir | `encabezado.modelo` (sección 2, regla 2) |
| VIN | Expediente y documentos coincidentes | `encabezado.vin` |
| Fecha de avería | Registro del expediente | `encabezado.fechaAveria` (fecha de registro en SIGA) |
| KM de avería | SIGA, odómetro, PRC, PQR o presupuesto | `encabezado.kmAveria` (el conector lo imprime «69,090 KM») |
| Valoración | Presupuesto validado y MSRP −10 % | `valoracion` (sección 6) |
| Fundamento de rechazo | Contrato específico de la avería | `numerales` + `clausulasLiterales` del Anexo A de `contrato-mitsubishi.md` (y las secciones de la póliza MMDM por literal) |

La cubierta Mitsubishi sólo tiene estos campos de encabezado: **`numeroAveria`, `numeroContrato` (= `policyId`), `fechaAveria`, `modelo`, `vin`, `kmAveria`, `fechaCierre`** (hoy). Los demás (`producto`, `marca`, `fechaInicio`, `kmInicial`) se ignoran con aviso; «MITSUBISHI» va fijo en la plantilla. Ningún campo vacío ni en 0.

### 10.3 Contenido según el veredicto

- **Procedente** («sin texto técnico de justificación»): `valoracion.partidas` sólo con lo autorizado (refacciones a MSRP × 0.90, mano de obra autorizada; más de cinco refacciones → un renglón «Refacciones» con la suma), `valoracion.iva` y `valoracion.totalConIva` (sección 6.2). **Sin `desarrollo` ni `numerales`.** El conector imprime sólo el cuadro, sin desglose en texto ni conceptos no cubiertos, que es lo que pide el PDF («No agregar un párrafo explicando por qué se acepta»; checklist «Aceptación sin justificación técnica innecesaria»). Se comprueba que el total escrito coincide con la suma del cuadro. Con el límite del libro azul de la cláusula 13 si el importe se acerca al valor del vehículo.
- **Improcedente** («fundamento textual, numeral, evidencia y tabla cuando aplique»): `componente`, `causaBreve` y `desarrollo` con las fórmulas de `05-redaccion-informes.md`, cambiando la numeración y escribiendo «KM». `numerales` del Anexo A de `contrato-mitsubishi.md`: valen «14.3», «15.7», «12.4» (la del desmontaje, que aquí sí existe), «11», «1»… y **no** valen los de GarantiPlus («12.4» como «documentación en 72 h» o «13.8»: en Mitsubishi esos hechos son 14.4 y 15.7). La definición de AVERÍA/AS (cláusula 1, desde «Se entiende por avería mecánica…» hasta «…cualesquiera influencias externas.») y la **11** completa van en `clausulasLiterales` cuando se citan, igual que la 9 en GarantiPlus. El numeral de cierre del diagnóstico no cubierto es el **15.7**.
  - **Por mantenimiento**: **`mantenimientos`** con la tabla (4.4) + `numerales: ["14.3"]` (añadir `"14.4"` si además hubo documentación requerida formalmente y no entregada en 72 h) + `clausulasLiterales` con la **11** literal (numeral «11», título «MANTENIMIENTOS PERIÓDICOS»), y opcionalmente «DAÑO CAUSADO POR MANTENIMIENTO INCORRECTO O FALTA DE SEGUIMIENTO DEL PROGRAMA DE MANTENIMIENTO RECOMENDADO» de la póliza MMDM. `causaBreve`: «el historial de servicios proporcionado muestra un intervalo de mantenimiento excedido por {kilometraje | tiempo | kilometraje y tiempo}, el cual se muestra en el análisis de intervalos de mantenimiento. Esto ya que el programa estipula la realización de los mantenimientos del fabricante cada 6 meses o 10,000 KM, lo que ocurra primero, y está previsto en los artículos que se transcriben». `desarrollo`: el párrafo del texto modelo (4.3, paso 8), con el rango del Manual y por qué no procedió carta ni reactivación. Sólo con un tramo de rango 4 o con rangos 2–3 declinados (4.2).
  - **Por causa** (desgaste, fuga, morfología, daño externo): definición de la cláusula 1 en `clausulasLiterales` + `numerales` con el ítem de la 15 (15.3, 15.4, 15.5, 15.2, 15.18, 15.13…) + la **10** en `clausulasLiterales` (numeral «10», título «OBLIGACIONES DE GARANTIPLUS», su párrafo literal) para reforzar «deterioro y/o desgaste normal» (como 162031: 1, 10 y 15); y, cuando la causa esté en la póliza MMDM (daños menores, odómetro alterado, modificaciones, abuso), su sección literal con `numeral: "Póliza MMDM"`. Siempre con la evidencia de `contrato-mitsubishi.md` §6.4.
  - **Por proceso**: `numerales: ["14.1", "12.4"]` (desmontaje o trabajo previo) o `["14.4"]` (documentación no aportada en 72 h).
  - **Por componente excluido**: el inciso de la cláusula **2** que lo excluye, literal.
- El cuerpo nunca cita el chat ni el Seguimiento; datos personales nunca.

### 10.4 La tabla de mantenimientos en el Informe, con el conector — **actualizado en v4**

Hasta v3 el conector no dibujaba la tabla y el análisis iba línea por línea en `desarrollo`; el técnico tenía que editar el Word para meterla en rojo. **Desde el 28/10/2026 la imprime `generar_resolucion`** con el parámetro `mantenimientos` (4.4): tras la frase de dictamen, con la forma de la plantilla del área (tres filas de título, cabecera FECHA · KM · DIAS · OBS · RECORRIDO, FECHA y KM en azul, excedidos en rojo, cabecera repetida si salta de página), y la respuesta del conector enseña la misma tabla en «## Análisis de intervalos de mantenimiento» para cotejarla. No hay que editar el Word ni subir nada a mano: `subir_resolucion` sube el PDF que el conector generó, y `rechazar_averia` sigue igual.

Qué queda del técnico: las `obs` (marca lo excedido en rangos 2–4; nada en rango 1), confirmar la tabla en el chat antes de generar y revisarla en el PDF. Qué hace Claude: proponer las `obs` según los rangos (4.2), armar `mantenimientos` con el inicio, cada servicio evaluable y la avería como última fila, y leer al técnico los avisos del conector.

---

## 11. Checklist final (PDF §8, los 22 puntos, con la herramienta o la sección que cubre cada uno)

| # | Punto (literal del PDF) | Cómo se cumple aquí |
| --- | --- | --- |
| 1 | Contrato correcto de la avería revisado. | `contrato-mitsubishi.md` (certificado del programa —el de `expediente_completo`— + póliza MMDM + manual) + póliza de la ficha (`policyId`) + carátula si existe (0.1, 9.3). |
| 2 | Vigencia confirmada. | Póliza de SIGA o carátula; si no se puede confirmar, 🟡 (sección 1). |
| 3 | VIN coincidente en expediente, presupuesto y evidencia. | Cruce de la ficha con cada documento de `expediente_completo` / `leer_documento` (sección 2). |
| 4 | Modelo corroborado con VIN o documentos. | Póliza, carátula, PRC o presupuesto; nunca el modelo genérico de SIGA si hay algo más preciso (sección 2). |
| 5 | KM de avería identificado y escrito con “KM”. | Odómetro u otra fuente; el encabezado lo imprime «69,090 KM»; en el cuerpo se escribe así (sección 2). |
| 6 | Diagnóstico y causa raíz suficientemente sustentados. | PRC, PQR, diagnóstico (sección 5.1–5.2); si no, 🟡. |
| 7 | Evidencia relacionada con el componente y la causa. | Fotos, videos, códigos, mediciones (secciones 3.1, 5.2). |
| 8 | Historial de mantenimientos revisado completo. | Todos los servicios desde el inicio de la cobertura (sección 4.3); sin comprobantes, el comentario de 4.5. |
| 9 | Días y recorridos calculados correctamente. | Días naturales exactos con el calendario del tramo, sin 180 días por 6 meses; rango de MMDM por tramo (4.2); los calcula también el conector (4.4). |
| 10 | Carta de compromiso o reactivación validada contra el desfase. | Las tres comprobaciones de 4.6; rango 2 sin carta y rango 3 sin reactivación son 🟡 con su comentario. |
| 11 | Componente cubierto y no excluido en el contrato aplicable. | Cláusulas 2 y 3 (5.1); casos especiales (5.3). |
| 12 | Campaña o boletín validado para VIN, modelo y síntoma. | Los cinco puntos de 5.3. |
| 13 | MSRP -10 % aplicado una sola vez. | `consultar_precios_mitsubishi` + cotejo de 6.5 (¿el taller ya lo aplicó?). |
| 14 | Mano de obra, cantidades, IVA y total recalculados. | Fórmula 6.2; cuadre de la tabla de parámetros (6.5, paso 7). |
| 15 | Topes o deducibles del contrato aplicados, si corresponden. | Cláusula 13 y póliza (6.2). |
| 16 | Aceptación sin justificación técnica innecesaria. | Procedente sin `desarrollo` ni `numerales`; el conector sólo imprime el cuadro (10.3). |
| 17 | Rechazo con artículo y numeral textual del contrato. | `numerales` y `clausulasLiterales` del Anexo A de `contrato-mitsubishi.md`; las cláusulas de la póliza MMDM por literal (8, 10.3). |
| 18 | Tabla de mantenimiento incluida y excedidos en rojo, si aplica. | `mantenimientos` en `generar_resolucion`: el conector imprime la tabla y pinta en rojo las `obs` del técnico y la cifra que las respalda (4.4, 10.4). |
| 19 | Visto bueno de Alexys previsto para rechazo. | Línea propia en la tabla de parámetros; sin él no se sube ni se rechaza (7.3). |
| 20 | Autorización especial prevista si el monto supera $100,000. | Línea propia en la tabla; sin ella no se sube ni se aprueba (7.3). |
| 21 | Formato Mitsubishi conservado. | Cubiertas `cubierta-mitsu*.docx` del conector; si se edita el Word, sin tocar encabezado, logotipo, colores, distribución, tipografía ni estructura (10.1). |
| 22 | No se modificó SIGA sin autorización expresa. | Dos pasos con `confirmar: true` sólo tras el «Confirmo»; control de cambios (7.3, 7.4). |

---

## 12. Lo que todavía no se sabe y las tensiones abiertas (no inventar)

**Resuelto el 28/10/2026 (v4):**

- **El contrato.** En SIGA no hay contrato de cobertura Mitsubishi; el contrato es `contrato-mitsubishi.md` (certificado + póliza MMDM + manual, un solo contrato). La tensión «cada avería con su propio contrato» vs. «programa sin certificado individual» se resuelve así.
- **Tolerancia e intervalo.** Intervalo 6 meses / 10,000 KM; los **rangos de desfase de MMDM** sustituyen a la tolerancia de 1 mes / 1,000 KM del PDF del área (4.2). Qué tramo cuenta, reincidencia y la avería al 100 % tras reactivar: 4.2 y 4.6.
- **La tabla en rojo.** La imprime el conector (4.4, 10.4). Ya no hay que editar el Word ni subir a mano.
- **Sin comprobantes.** 🟡 con el comentario de 4.5, publicado sólo tras la confirmación del técnico.
- **Ruidos y odómetro.** Tienen cláusula en la póliza MMDM (5.5).
- **Condiciones especiales del programa** (bomba L200 y otras): casos especiales de 5.3 (desde v2).

**Sigue sin saberse:**

- Cómo se verifica la **vigencia** cuando la ficha no trae fecha de inicio de la póliza y no hay carátula ni factura (sección 1; `contrato-mitsubishi.md` §3.5).
- El **«listado Mitsubishi autorizado»** de componentes para desgaste prematuro antes de 140,000 KM (5.2).
- El texto de la **campaña de satisfacción** de la bomba L200 MY25 y la **indicación de MMDM** sobre portalentes y mangueras de A/C (5.3).
- **Quién da la autorización especial** para montos superiores a $100,000, y si el umbral es con o sin IVA (7.3).
- Cómo se identifica y registra el **visto bueno de Alexys** (canal, forma); aquí sólo se registra lo que el técnico diga.
- La **tarifa de mano de obra** para Mitsubishi (6.2).
- El formato de la **Carta Compromiso** y de la **Carta de Reactivación** (el Manual dice que los distribuye MMDM; no están en el Conocimiento): se validan por su contenido (VIN, desfase, firma).
- Si MMDM publica **cuadernos por año modelo** con otro plan: por eso el programa de 2019 es «plan de referencia salvo cuaderno de la unidad» (4.2).

**Tensiones entre las fuentes, el conector y las reglas del proyecto** (se dicen al técnico cuando aparezcan; no se resuelven en silencio):

1. **Rangos de MMDM vs. tolerancia del PDF del área.** Mandan los rangos: decisión de Omar (28/10/2026) y nota de aplicación del PDF («prevalece … la instrucción formal más reciente emitida por las áreas autorizadas de Mitsubishi y GarantiPlus»; el Manual es instrucción formal de MMDM). Si el área vuelve a instruir otra cosa, se incorpora.
2. **«Servicios en Distribuidor Mitsubishi» (póliza MMDM) vs. certificado** (facturas con los datos de 12.3.d). Para este archivo, la factura de taller independiente acredita el servicio (`contrato-mitsubishi.md` §8.6) y se dice; el técnico decide si lo lleva a Alexys.
3. **«La negación no se basará únicamente en la ausencia de registros» vs. 🟡 hasta que lleguen.** Se cumple lo primero (no se rechaza) sin concluir 🟢 por inferencia: se piden una vez y 14.4 sólo tras requerimiento formal (4.5).
4. **Visto bueno de Alexys y autorización especial > $100,000 vs. el «Confirmo» único de v4.** En Mitsubishi el «Confirmo» no basta por sí solo (7.3).
5. **IVA.** En Mitsubishi manda la fórmula del área: partidas sin IVA, IVA desglosado y total con IVA (6.2).
6. **Casos especiales vs. texto del certificado.** La bomba L200 «conforme a la campaña de satisfacción» choca con 15.11; portalentes y mangueras de A/C con 2.9 y 15.4; el desgaste prematuro antes de 140,000 KM con 1.4, 10, 15.1 y 15.3. Los casos especiales son instrucción formal del área y de MMDM y se aplican como `Criterio del área (PDF 27/10/2026)`; con la lectura flexible (0.5), además, en duda procede.
7. **Certificado vs. póliza MMDM en una misma pieza** (soportes, juntas, banda de distribución, batería 12 V, bujías de iridio, estéreo): la lectura más favorable que alguno de los dos textos sostenga, diciendo cuál (`contrato-mitsubishi.md` §5.3). Lo tajante del certificado (vigencia, siniestros, trabajos previos probados) no se relaja.
8. **Reactivación en curso vs. folio en Validación.** El folio se queda 🟡 durante semanas; la regla de rezago del área (`planificacion_averias`) lo verá como abierto: se deja constancia en el comentario y en la bitácora de que está «en reactivación».
9. **Inconsistencia de VIN.** El catálogo de SIGA tiene «Falta de relación en VIN», pero el PDF manda pedir el documento corregido y no emitir resolución definitiva (sección 2).
10. **Marca en el encabezado.** El PDF pide llenar «marca» en las aceptaciones; la cubierta Mitsubishi la trae fija («MITSUBISHI») y el conector ignora `marca`: se cumple sin mandarla.

---

## 13. El flujo con Mitsubishi en alcance (desde el 27/10/2026; v4 el 28/10/2026)

Lo mismo de `instructions.md` (tres mensajes, tabla de parámetros, `causas` por refacción, `motivo` del catálogo), con estas diferencias:

1. El contrato es `contrato-mitsubishi.md` (0.1); la plantilla es `mitsubishi`; el encabezado lleva sólo los siete campos de la sección 10.2; `numeroContrato` = `policyId`.
2. Toda cita es con la numeración del Anexo A de ese archivo (sección 8); las cláusulas de la póliza MMDM van por literal con `numeral: "Póliza MMDM"`.
3. Cobertura defensa a defensa salvo exclusión expresa y probada (0.5, 5.0).
4. Mantenimiento con la sección 4: intervalo 6 meses / 10,000 KM, **rangos de desfase de MMDM** (4.2), método de la guía (4.3), **tabla en el Informe con `mantenimientos`** (4.4), comentarios de «sin comprobantes» (4.5) y de carta o reactivación (4.6). En el veredicto, un desfase se reporta con su rango: «tramo {fecha} → {fecha}: {N} KM / {N} días, exceso {N} KM → rango {1–4} (MMDM): {tolerancia | Carta Compromiso | Reactivación | fuera de rango}».
5. En procedentes, `consultar_precios_mitsubishi` con todos los números de parte y la valoración a MSRP × 0.90 con IVA desglosado (sección 6); `actualizar_precios_mitsubishi` cuando el técnico suba la lista del mes.
6. La tabla de parámetros del mensaje 2 añade, según el caso, «Precio autorizado: MSRP −10 % (lista {mes})», «Visto bueno de Alexys», «Autorización especial (> $100,000)» y, en un rechazo por mantenimiento, **«Rango de desfase (Manual MMDM): {rango} — {tramo}; carta/reactivación: {no aplica | declinada el {fecha}}»**; el «Confirmo» no ejecuta sin lo que corresponda (7.3). El control de cambios de 7.4.
7. El resultado 🟡 sigue la tabla 3.1 del área (incluidos los comprobantes de mantenimiento) y los comentarios de 3.3, 4.5 y 4.6, siempre publicados sólo tras la confirmación del técnico.

Pendiente: cerrar un rechazo por mantenimiento (con la tabla del conector), una aprobación y un caso en rango 3 (comentario de reactivación) de punta a punta en `pruebas`; el primer caso real se revisa con especial cuidado; las dudas de la sección 12.

---

## Anexo

El certificado del programa (GARANTÍA REAL 7, febrero 2019) ya no se transcribe aquí: está **íntegro en `contrato-mitsubishi.md`, Anexo A**, con la numeración S.N por posición que se cita en el Informe, junto con la hoja resumen, la póliza MMDM (Anexo B) y el Manual de reactivación (Anexo C). Este archivo no mantiene una segunda copia para que no diverjan.
