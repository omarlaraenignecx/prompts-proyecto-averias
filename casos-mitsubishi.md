# Criterios y documentos — programa Mitsubishi (plantilla `mitsubishi`)

**Versión de este recurso: 2026-10-27 (v3: **la cuenta Mitsubishi entra en alcance** —sección 13—; el Informe sale con la cubierta y el rechazo Mitsubishi maquetados por el conector; la 10 se cita literal; v2: criterio operativo del área del 27/10/2026 incorporado completo; lista de precios en el conector).** Antes: 2026-10-26 (v1: preparado, con el certificado del programa y su numeración). Quien lo edite actualiza aquí la fecha y la nota de qué cambió.

> **La cuenta Mitsubishi está EN ALCANCE desde el 27/10/2026** (decisión de Omar; `instructions.md` §1). Un folio Mitsubishi se dictamina, se genera su Informe con la plantilla `mitsubishi` y se cierra en SIGA con el mismo flujo de tres mensajes de `instructions.md`, con las diferencias de la sección 13 de este archivo.

Todo lo que el conector y el área saben del programa Mitsubishi. Tiene dos fuentes, y cada regla dice de cuál sale:

- **El certificado del programa** (GARANTÍA REAL 7, febrero 2019), transcrito íntegro en el Anexo. Es el texto contractual que se cita.
- **«Criterios operativos para evaluación de averías Mitsubishi»** (`Criterios_Operativos_Mitsubishi_GarantiPlus.pdf`, 9 páginas, GarantiPlus México, «Uso operativo interno», **27 de octubre de 2026**): la guía del área para «revisar contratos, expedientes, evidencia, mantenimientos, presupuestos y emitir resoluciones consistentes en SIGA». En este archivo se cita como **«PDF del área»** o **`Criterio del área (PDF 27/10/2026)`**. Todo su contenido está aquí, punto por punto; las frases clave van literales entre «…».

**Nada de `casos-garantiplus.md` aplica aquí salvo que este archivo lo diga**: los criterios de GarantiPlus (intervalos de 12,000 km / 12 meses, la regla de «sin comprobantes no se evalúa», 12.5, 13.30, el orden de causales…) se apoyan en cláusulas que este certificado no tiene o en decisiones del área para otra cuenta. Donde el PDF del área y `casos-garantiplus.md` coinciden, se dice; donde difieren, manda este archivo para Mitsubishi.

**Glosario mínimo.** **MMDM** = Mitsubishi Motors de México. **PRC** y **PQR** = reportes técnicos del distribuidor Mitsubishi con el diagnóstico (síntoma, pruebas, causa raíz, piezas; a veces también kilometraje y servicios); el PDF del área habla además de «expedientes PRC relacionados». **MSRP** = precio de lista de la refacción en la lista de precios mensual de Mitsubishi. **DNP** = precio al distribuidor en esa misma lista. **SS** = número de parte que sustituye al de la fila (supersesión). **EGT** = sensor de temperatura de gases de escape. **MY25** = año modelo 2025. **Alexys** = la persona que, según el área, da el visto bueno a los rechazos Mitsubishi (este archivo no sabe más de ella; no se le atribuye otro cargo).

---

## 0. Principio rector y jerarquía de fuentes

### 0.1 Principio rector (PDF del área, portada)

> «Cada avería se evalúa con su propio contrato y con la evidencia de su expediente. Los criterios internos complementan el análisis, pero no sustituyen ni pueden contradecir las condiciones particulares de la cobertura.»

Y como regla general (PDF §1): «La procedencia no se determina únicamente por el nombre de la refacción ni por un antecedente de otra avería. Se debe reconstruir el caso desde cero, identificar el contrato aplicable, verificar la unidad y relacionar la causa de la falla con la cobertura y las exclusiones.»

**Qué es «su propio contrato» en Mitsubishi.** El programa **no tiene certificado individual por vehículo** (sección 1). El contrato aplicable a cada avería es, por tanto, **el certificado del programa (Anexo) más la póliza de esa avería en SIGA** (`policyId`, vigencia, kilometraje de inicio, lo que la ficha traiga) y, si existe en el expediente, la carátula o póliza de la unidad. Esa es la lectura que adopta este archivo; la tensión con la frase del PDF está en la sección 12.

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
| **1** | Contrato o póliza de la avería | «Vigencia, producto, coberturas, exclusiones, límites, obligaciones y plan de mantenimiento aplicable.» | El certificado del programa en `expediente_completo` (y en el Anexo) + la póliza de la ficha de SIGA (`policyId`, vigencia, km de inicio si los trae) + la carátula o póliza de la unidad si el taller o el área la subieron al expediente. |
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

Consecuencias aquí: (a) si un dato de la póliza o de la carátula de la unidad difiere de este archivo, manda la póliza; (b) si el técnico trae una instrucción formal posterior al 27/10/2026, manda ella sobre este archivo (se registra con fuente `Técnico`, con quién la emitió y su fecha); (c) quien edite este archivo la incorpora y sube la versión.

---

## 1. Qué es el programa y cómo se ve en SIGA

- Es un **programa de garantía para unidades nuevas** vendidas por Mitsubishi Motors de México (producto «GARANTÍA REAL 7», certificado de febrero de 2019, vigente según el área). **No hay certificado individual por vehículo**: todas las averías comparten el condicionado del programa y el contrato en SIGA es el centinela **57227**.
- La ficha de `expediente_completo` marca la cuenta como **MITSUBISHI (programa, sin contrato individual)** y la plantilla del Informe como `mitsubishi`. `averias_pendientes` las lista con esa etiqueta.
- Para el Informe, **`numeroContrato` es el `policyId`** de la avería (el `contractId` es siempre el 57227 y no se imprime). Coincide con el PDF del área: «Número de contrato: Póliza o encabezado de la avería» (sección 10.2).
- La vigencia y el kilometraje de inicio no se pueden verificar contra un certificado individual: salen de la ficha de SIGA (póliza) o de una carátula de la unidad en el expediente y, si faltan, se dicen como «por confirmar»; nunca se inventan. El PDF exige «Vigencia confirmada» (checklist, punto 2): si no se puede confirmar con ninguna fuente, es un dato esencial faltante (sección 7.1, «Requiere información»), salvo que el técnico la confirme con otra fuente (fuente `Técnico`).
- El condicionado que el conector entrega para estas averías es el **certificado del programa** transcrito en el Anexo, con su propia numeración (1–20). El motor de `generar_resolucion` con `plantilla: "mitsubishi"` transcribe los numerales de **ese** texto: un numeral que no exista ahí se rechaza.
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

**Dos reglas del área sobre identidad y kilometraje que el certificado no escribe** (vigentes desde v1, decisión de Omar del 2026-09-25, y no derogadas por el PDF): «el odómetro no retrocede» (un kilometraje que baja entre documentos, o un km de avería menor que el de inicio, es alerta de integridad) y «ruidos, zumbidos y vibraciones no se cubren» (sección 5.5). Se aplican como `Criterio del área`, se marcan como «Cláusula especial del programa Mitsubishi» y no se cita un numeral que no exista.

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

## 4. Mantenimientos (PDF §3, y cláusulas 9.3, 9.4, 11, 12.3.c–d, 14.3 y 14.4 del certificado)

### 4.1 Lo que dice el certificado

- **Cláusula 11:** «Para que el certificado contratado sea efectivo, el BENEFICIARIO se obliga a efectuar en el VEHÍCULO los trabajos o tareas de mantenimiento exigidas por el POR EL FABRICANTE SIGUIENDO SU PLAN DE MANTENIMIENTO PRECONIZADO, tanto en periodos de tiempo como en kilometraje.» No trae tabla de intervalos ni carnet.
- **9.3** obliga a «Realizar en el VEHÍCULO los mantenimientos periódicos exigidos por el fabricante en tiempo y forma» y **9.4** a «Conservar las facturas correspondientes…».
- **12.3.c–d**: el taller aporta copia del libro de mantenimiento si lo hay y las facturas de las inspecciones con identificación del taller, del vehículo (marca, modelo, placa, kilómetros), reparaciones desglosadas, fecha y firma o sello.
- **14.3** permite rechazar «Cuando el BENEFICIARIO no haya cumplido sus obligaciones de mantenimientos e inspecciones»; **14.4**, cuando las facturas o la documentación del artículo 12 «no estén debidamente cumplimentadas o no se aporten en un plazo de 72 h tras ser requeridas».
- **8.3**: el vehículo es nuevo por definición («El auto deberá de ser nuevo…»).

### 4.2 Intervalo y tolerancia (recuadro «INTERVALO GENERAL MITSUBISHI» del PDF) — **actualizado en v2**

> «Cada 6 meses o 10,000 KM, lo que ocurra primero. Se considera una tolerancia máxima de 1 mes o 1,000 KM. Antes de aplicarlo, confirmar que el contrato o plan de la unidad no establezca una condición distinta.»

- **Esto resuelve lo que v1 dejaba abierto**: v1 decía que el intervalo era el del plan del fabricante («normalmente 10,000 km o 6 meses, pero se lee del manual») y que la tolerancia de 1,000 km / 30 días «no está decidido que aplique». Desde el PDF del 27/10/2026, el intervalo general Mitsubishi es **6 meses o 10,000 KM, lo que ocurra primero**, con **tolerancia máxima de 1 mes o 1,000 KM**, como `Criterio del área (PDF 27/10/2026)`, que da contenido al «plan de mantenimiento preconizado» de la cláusula 11.
- **Excepción obligatoria:** antes de aplicarlo se confirma que la póliza, la carátula o un plan del fabricante para esa unidad que esté en el expediente no fije otra cosa. Si lo fija, manda ese (y se dice). Un rótulo de factura («servicio de 20 mil») no es el plan.
- **Límites con tolerancia, tramo por tramo:**
  - **Kilometraje:** cumple hasta **11,000 KM** recorridos entre servicios consecutivos (10,000 + 1,000); **excedido desde 11,001 KM**.
  - **Tiempo:** cumple si el servicio siguiente (o la avería, en la última fila) cae **en o antes de la misma fecha del servicio anterior más 7 meses de calendario** (6 + 1 de tolerancia); excedido después. Los días naturales del tramo se calculan exactos y se escriben en la tabla, pero **el límite no es una cifra fija de días**: el PDF manda «Verificar manualmente los días; no aproximar meses ni asumir que 6 meses equivalen siempre a 180 días». Siete meses de calendario son entre 212 y 215 días según el tramo (15/03/2026 → 15/10/2026 son 214 días; 31/08/2025 → 31/03/2026 son 212). Si el día no existe en el mes de llegada (31 → febrero), se toma el último día de ese mes y se dice como «Supuesto». Esta forma de medir el mes es la lectura de este archivo para cumplir la regla del PDF; si el técnico o el área la leen distinto, manda su lectura.
  - Se reporta en el tramo si el exceso es por **tiempo**, por **kilometraje** o por **ambos** (es la columna OBSERVACIÓN).

### 4.3 Método de análisis (PDF §3, literal y completo)

1. «Ordenar todos los servicios cronológicamente.»
2. «Calcular los días naturales entre cada servicio y el recorrido entre kilometrajes consecutivos.»
3. «Comparar cada intervalo con el límite de tiempo y kilometraje, incluyendo la tolerancia autorizada.»
4. «Revisar desde el inicio de la cobertura cuando el contrato lo requiera; no evaluar únicamente los dos últimos servicios.»
5. «La avería debe incluirse como última fila para mostrar días y recorrido desde el último mantenimiento.»

Precisiones de este archivo:

- **Desde dónde se cuenta.** Como la cláusula 11 condiciona la efectividad del certificado y el vehículo es nuevo (8.3), se revisa **todo el historial desde el inicio de la cobertura** (fecha y KM inicial de la póliza o, si no los hay, la primera factura o entrega de la unidad), no sólo los dos últimos servicios. La primera fila es «Inicio» con el KM inicial si existe.
- **Fuentes de cada servicio** (prioridad 5 de la jerarquía): «Facturas, sellos, historial y datos consignados en PRC»; se verifican fechas y kilometrajes de cada uno. Un servicio sin fecha o sin KM legible se dice y se pide (sección 3.1, «historial legible»).
- **No cumplió vs. no acreditó** (se conserva de v1 y de `instructions.md` regla 14): comprobantes que muestran un tramo excedido = **no cumplió** → 14.3, motivo «Intervalo de Mantenimiento Excedido». Comprobantes requeridos por el área y no entregados en 72 h = **no acreditó** → 14.4, motivo «Falta al proceso o incompleto (Distribuidor)». Comprobantes que nadie ha pedido todavía = ninguna de las dos: se solicitan (3.1) y el caso es 🟡.
- **Fuera de la regla**: la bomba de combustible L200 diésel MY25 en campaña se autoriza «aun cuando existan incidencias de mantenimiento» (sección 5.3); una carta de compromiso o reactivación válida (4.6) puede cubrir un desfase.

### 4.4 La tabla de mantenimientos (PDF §3, plantilla literal)

| FECHA | KM | DÍAS | OBSERVACIÓN | RECORRIDO |
| --- | --- | --- | --- | --- |
| Inicio | KM inicial si existe | | | |
| Servicio 1 | KM servicio | Diferencia | Cumple / excedido | KM recorridos |
| Servicio 2 | KM servicio | Diferencia | Excedido tiempo o KM | KM recorridos |
| Avería | KM avería | Diferencia | KM AVERÍA | KM recorridos |

Cómo se llena: FECHA real (dd/mm/aaaa) en lugar de «Inicio / Servicio n / Avería» si el técnico lo prefiere, pero cada fila tiene que decir qué es; KM con «KM»; DÍAS = días naturales exactos desde la fila anterior; RECORRIDO = KM de la fila menos KM de la anterior; OBSERVACIÓN = «Cumple», «Excedido en tiempo», «Excedido en KM» o «Excedido en tiempo y KM»; en la fila de la avería, «KM AVERÍA» y, si el tramo abierto también excede, dicho exceso.

### 4.5 Formato obligatorio en rechazos por mantenimiento (PDF §3, literal)

- «Incluir la tabla completa dentro de la resolución.»
- «Las celdas excedidas deben resaltarse en rojo.»
- «En OBS indicar si el exceso corresponde a tiempo, kilometraje o ambos.»
- «Citar textualmente el artículo y numeral del contrato que obliga a realizar mantenimientos y permite rechazar por incumplimiento.» En este certificado: la **11** (obliga; con 9.3 si se quiere reforzar) y la **14.3** (permite rechazar). Es lo que citó el área en 166585 (14 ítem 3 y 11).
- «Verificar manualmente los días; no aproximar meses ni asumir que 6 meses equivalen siempre a 180 días.»

> **Brecha conocida del conector:** hoy `generar_resolucion` **no dibuja tablas ni celdas en rojo** dentro del Informe (un texto con `|` se aplana). Qué se hace mientras tanto: sección 10.4.

### 4.6 Carta de compromiso o reactivación (PDF §3, literal)

> «La existencia de una carta no vuelve procedente automáticamente la avería. Debe comprobarse que el desfase se encuentre dentro del rango autorizado por la propia carta o por el criterio vigente, que la unidad haya cumplido las condiciones solicitadas y que el documento corresponda al contrato y VIN evaluados.»

Tres comprobaciones, cada una con su fuente en el veredicto: (1) el desfase medido en la tabla está dentro del rango que la carta (o el criterio vigente) autoriza; (2) la unidad cumplió lo que la carta pedía (servicio de reactivación, revisión, etc., con su comprobante); (3) la carta es de esta póliza y de este VIN. Si falla una, la carta no cubre el desfase y se dice cuál falló. Si la carta no trae rango y el técnico no conoce un criterio vigente, es una duda para el técnico, no un «Supuesto».

---

## 5. Criterios técnicos de cobertura y casos especiales (PDF §4, y cláusulas 1, 2, 3, 10 y 15)

### 5.1 Principio (PDF §4, literal)

> «El diagnóstico debe explicar qué falló y por qué. No basta con que una pieza esté mencionada en el presupuesto: debe existir correspondencia entre síntoma, pruebas, daño observado y reparación propuesta.»

**Pieza cubierta ≠ causa cubierta.** Se evalúan las dos, en este orden:

1. **Componente** (certificado): primero la lista literal de la cláusula **2** (asientos y mecanismos, habitáculo y maletero, neumáticos y válvula, carrocería, cristales, faros e intermitentes, molduras y espejos, consumibles —filtros, aceite, juntas, amortiguadores, escapes, discos, pastillas, correas, servicio periódico, lubricantes, combustibles, aditivos, carga de a/a salvo que la necesite una avería cubierta, bujías, calentadores, batería, escobillas, plumas— y elementos que perdieron su morfología —bujes, gomas, soportes, juntas—). No hay periodo de espera de 90 días ni lista de componentes por producto. En un **PHEV**, la cláusula **3** cubre batería de alto voltaje y componentes eléctricos (motor eléctrico, motor eléctrico del sistema de refrigeración, líneas de alta tensión, conexión regular de carga, inversor – PHEV-ECU, conexión de carga rápida, trans eje, cargador a bordo / convertidor DC-DC) 7 años sin límite de km desde el inicio de la garantía, pero **no** la pérdida gradual de retención de carga.
2. **Causa** (certificado): cláusula **1** (1.4: AVERÍA/AS = inutilidad operativa por rotura imprevista / fortuita; la reducción gradual proporcional a antigüedad y km no es avería, contada desde la primera matriculación; tampoco la derivada de accidentes o influencias externas), **10** (no cubre uso inadecuado ni deterioro o desgaste normal) y los 28 ítems de la **15** (tabla 5.6).
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

### 5.5 Reglas del área que el certificado no escribe (se conservan de v1)

Decisión de Omar del 2026-09-25, no derogada por el PDF: «el odómetro no retrocede» (relación de kilometraje; en GarantiPlus es la 12.5 del genérico) y «ruidos, zumbidos y vibraciones no se cubren» (13.30 del genérico). Se aplican como `Criterio del área`, **se marcan como «Cláusula especial del programa Mitsubishi»** en el veredicto, **no se cita un numeral que no exista**, y decide el técnico. Para un ruido, la lectura de la cláusula 1.4 (la avería exige **inutilidad operativa**, no sólo un síntoma) sí es cita del certificado.

### 5.6 Causas y partidas: numeral del certificado → motivo de catálogo de SIGA

Traducción de la tabla de `casos-garantiplus.md` §6 a la numeración Mitsubishi (para escoger el motivo; **se cita siempre el numeral del Anexo**, y el motivo se escoge por el hecho):

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
| `buscar` | Texto libre en todas las columnas de texto, sin acentos y tolerando los acentos dañados del Excel («cigüeñal» encuentra «Cig£e‹al»). Para cuando el presupuesto no trae número de parte. |
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

1. **Consulta única.** Con el presupuesto leído, llama `consultar_precios_mitsubishi` con `numerosDeParte` = **todos** los números de parte de las refacciones del presupuesto, en una sola llamada. Si una refacción no trae número de parte, se busca con `buscar` y se enseña lo encontrado como candidato, sin darlo por bueno: decide el técnico o se pide el número de parte al distribuidor.
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
- «No usar motivos genéricos ni copiar numerales de otro contrato.» (Nada de «12.4» o «13.8» de GarantiPlus: sección 8.)
- «Citar el artículo y numeral exactos del contrato de la avería.»
- «Relacionar el hecho probado con la exclusión aplicable.»
- «Incluir tabla de mantenimientos cuando el rechazo se base en intervalos excedidos.» (Brecha del conector: sección 10.4.)
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
- **Datos o montos incompletos → Word editable.** El conector no genera un Informe con un campo del encabezado vacío (lo rechaza y dice cuál), y siempre produce Word y PDF a la vez. Si falta un dato de encabezado, no se genera: se pide (sección 3). Si lo que falta es un dato del cuerpo o un monto que el técnico quiere revisar, se puede generar y darle el enlace **«Descargar Word»** para revisión, con el dato pendiente señalado **en el chat, fuera del texto del Informe**; ese documento **no se sube** a SIGA hasta que el técnico confirme los campos y se regenere el definitivo con ellos (o hasta que él decida, ver 10.4).
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

**Cita siempre con la numeración de este certificado.** El área lo hace así en sus resoluciones Mitsubishi: 166585 (sensor O2, mantenimiento) citó **14** ítem 3 y **11**; 162031 (muelles, desgaste) citó **1**, **10** y **15**. Un Informe Mitsubishi que cite «12.4» o «13.8» está citando el contrato de otra cuenta. Esto es también lo que pide el PDF: «No usar motivos genéricos ni copiar numerales de otro contrato» y «Citar el artículo y numeral exactos del contrato de la avería».

---

## 9. Cómo se lee un caso Mitsubishi, paso a paso

Fusiona el flujo operativo del PDF (§7, nueve pasos, literales al inicio de cada paso) con la lectura del certificado (v1 §3) y las herramientas del conector. Es el mismo esqueleto de `instructions.md` §4 (revisar → generar → confirmar) con lo que cambia en Mitsubishi.

1. **«Abrir la avería y confirmar que pertenece a Mitsubishi y al VIN correcto.»** `expediente_completo({ claimId })` (una llamada por folio). La ficha dice «MITSUBISHI (programa, sin contrato individual)», plantilla `mitsubishi`, contrato 57227 y el `policyId`. Se cruza el VIN de la ficha con los documentos (sección 2).
2. **«Descargar y revisar todos los documentos y evidencias disponibles.»** Todo lo que trajo `expediente_completo` (presupuesto, PRC, PQR, diagnóstico, odómetro, facturas y sellos de servicio, fotos, fotogramas de video); lo que quedó fuera, en una sola llamada a `leer_documento`; el audio de un video, con su enlace `/video`. No se dictamina con documentos sin leer. Se comprueba la documentación mínima (tabla 3.1).
3. **«Leer el contrato aplicable y verificar vigencia, cobertura, exclusiones y obligaciones.»** Certificado del programa (Anexo) + póliza de SIGA (+ carátula si existe):
   - **Vigencia** (5.1; comunicación fuera de plazo → 14.5): con la póliza de la ficha o la carátula; si no se puede confirmar, sección 1.
   - **Componente**: cláusula **2** (y **3** si es PHEV).
   - **Causa**: cláusula **1** (1.4), **10**, los ítems de la **15** (tabla 5.6), los criterios técnicos (5.2), los casos especiales (5.3) y las reglas del área de 5.5.
   - **Proceso**: la **12** (orden de entrada, presupuesto **sin intervenir ni desmontar**, facturas de mantenimiento; 72 h tras requerirlas → 14.4; vehículo inmovilizado → 14.2; trabajo previo a la resolución → 14.1) y la **14** (fuera de vigencia → 14.5; incumplimiento → 14.6, nunca sola).
   - **Límites**: **13** (libro azul).
4. **«Analizar mantenimientos y elaborar la tabla cuando sea necesaria.»** Sección 4: intervalo 6 meses / 10,000 KM con tolerancia 1 mes / 1,000 KM (salvo que la póliza o el plan de la unidad digan otra cosa), todos los servicios desde el inicio de la cobertura, la avería como última fila, días calculados a mano, carta de compromiso si la hay. La tabla se enseña en el chat cuando hay incumplimiento o cuando el técnico la pide.
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
| Fundamento de rechazo | Contrato específico de la avería | `numerales` + `clausulasLiterales` del Anexo |

La cubierta Mitsubishi sólo tiene estos campos de encabezado: **`numeroAveria`, `numeroContrato` (= `policyId`), `fechaAveria`, `modelo`, `vin`, `kmAveria`, `fechaCierre`** (hoy). Los demás (`producto`, `marca`, `fechaInicio`, `kmInicial`) se ignoran con aviso; «MITSUBISHI» va fijo en la plantilla. Ningún campo vacío ni en 0.

### 10.3 Contenido según el veredicto

- **Procedente** («sin texto técnico de justificación»): `valoracion.partidas` sólo con lo autorizado (refacciones a MSRP × 0.90, mano de obra autorizada; más de cinco refacciones → un renglón «Refacciones» con la suma), `valoracion.iva` y `valoracion.totalConIva` (sección 6.2). **Sin `desarrollo` ni `numerales`.** El conector imprime sólo el cuadro, sin desglose en texto ni conceptos no cubiertos, que es lo que pide el PDF («No agregar un párrafo explicando por qué se acepta»; checklist «Aceptación sin justificación técnica innecesaria»). Se comprueba que el total escrito coincide con la suma del cuadro. Con el límite del libro azul de la cláusula 13 si el importe se acerca al valor del vehículo.
- **Improcedente** («fundamento textual, numeral, evidencia y tabla cuando aplique»): `componente`, `causaBreve` y `desarrollo` con las fórmulas de `05-redaccion-informes.md`, cambiando la numeración y escribiendo «KM». `numerales` del Anexo: valen «14.3», «15.7», «11», «1»… y **no** valen «12.4» ni «13.8». La definición de AVERÍA/AS (cláusula 1, desde «Se entiende por avería mecánica…» hasta «…cualesquiera influencias externas.») y la **11** completa van en `clausulasLiterales` cuando se citan, igual que la 9 en GarantiPlus. El numeral de cierre del diagnóstico no cubierto es el **15.7**.
  - **Por mantenimiento**: `numerales: ["14.3"]` (añadir `"14.4"` si además hubo documentación requerida y no entregada en 72 h) + `clausulasLiterales` con la **11** literal (numeral «11», título «MANTENIMIENTOS PERIÓDICOS»). `causaBreve` (adaptada de 05 §4.1): «el historial de servicios proporcionado muestra un intervalo de mantenimiento excedido por {tiempo | kilometraje | tiempo y kilometraje}, según el análisis de intervalos mostrado más adelante. Esto ya que el programa estipula la realización de los mantenimientos del fabricante cada 6 meses o 10,000 KM, lo que ocurra primero, y está previsto en los artículos que se transcriben». `desarrollo`: el análisis de intervalos (10.4).
  - **Por causa** (desgaste, fuga, morfología, daño externo): definición de la cláusula 1 en `clausulasLiterales` + `numerales` con el ítem de la 15 (15.3, 15.4, 15.5, 15.2, 15.18, 15.13…) + la **10** en `clausulasLiterales` (numeral «10», título «OBLIGACIONES DE GARANTIPLUS», su párrafo literal) para reforzar «deterioro y/o desgaste normal» (como 162031: 1, 10 y 15).
  - **Por proceso**: `numerales: ["14.1", "12.4"]` (desmontaje o trabajo previo) o `["14.4"]` (documentación no aportada en 72 h).
  - **Por componente excluido**: el inciso de la cláusula **2** que lo excluye, literal.
- El cuerpo nunca cita el chat ni el Seguimiento; datos personales nunca.

### 10.4 Brecha conocida: la tabla de mantenimientos en rojo — y qué hacer mientras tanto

El PDF exige, en todo rechazo por mantenimiento, «la tabla completa dentro de la resolución» con «las celdas excedidas … en rojo». **El conector todavía no dibuja esa tabla dentro del Informe** (`generar_resolucion` no hace tablas: un texto con `|` o saltos de línea se aplana en un párrafo, y no colorea celdas). Mientras no se resuelva:

1. **En el chat**, la tabla completa de la sección 4.4 (FECHA · KM · DÍAS · OBSERVACIÓN · RECORRIDO), con la avería como última fila y las celdas excedidas marcadas (🔴 y en negritas), para que el técnico la revise.
2. **En el Informe**, el `desarrollo` describe los intervalos **una línea por fila**, con fechas, días y KM, y el tipo de exceso:
   - «ANÁLISIS DE INTERVALOS DE MANTENIMIENTO – MITSUBISHI {MODELO}, VIN {vin}. Intervalo del programa: 6 meses o 10,000 KM, lo que ocurra primero, con tolerancia de 1 mes o 1,000 KM.»
   - «Inicio de cobertura: {fecha} con {KM} KM.»
   - Una por servicio: «Servicio {n}: {fecha} con {KM} KM. Recorrido desde el anterior: {KM} KM en {días} días. {Cumple | EXCEDIDO EN TIEMPO | EXCEDIDO EN KILOMETRAJE | EXCEDIDO EN TIEMPO Y KILOMETRAJE}.»
   - La última, la avería: «Avería: {fecha} con {KM} KM. Transcurrieron {días} días y {KM} KM desde el último servicio: {INTERVALO EXCEDIDO EN … | cumple}.»
3. **Se le dice al técnico** en una línea que el Informe no lleva todavía la tabla en rojo que pide el criterio del área, y **él decide**: (a) subir el Informe así, con el análisis en texto; o (b) bajar el Word con el enlace **«Descargar Word»**, insertar la tabla con las celdas en rojo sin tocar el resto del formato (10.1), y subir él ese documento. Atención a (b): `subir_resolucion` sólo sube el PDF que generó el conector, **no un Word editado**; un documento editado lo tendría que subir el técnico a mano en SIGA (Documentos → Tipo «Resolución»), lo que contradice la regla general del proyecto («el Informe se sube con el conector, nunca a mano», sección 12). Una vez el documento Resolución está en SIGA, `rechazar_averia` puede ensayarse y ejecutarse igual. Claude no edita el Word ni lo sube.

---

## 11. Checklist final (PDF §8, los 22 puntos, con la herramienta o la sección que cubre cada uno)

| # | Punto (literal del PDF) | Cómo se cumple aquí |
| --- | --- | --- |
| 1 | Contrato correcto de la avería revisado. | Certificado del programa en `expediente_completo` + póliza de la ficha (`policyId`) + carátula si existe (0.1, 9.3). |
| 2 | Vigencia confirmada. | Póliza de SIGA o carátula; si no se puede confirmar, 🟡 (sección 1). |
| 3 | VIN coincidente en expediente, presupuesto y evidencia. | Cruce de la ficha con cada documento de `expediente_completo` / `leer_documento` (sección 2). |
| 4 | Modelo corroborado con VIN o documentos. | Póliza, carátula, PRC o presupuesto; nunca el modelo genérico de SIGA si hay algo más preciso (sección 2). |
| 5 | KM de avería identificado y escrito con “KM”. | Odómetro u otra fuente; el encabezado lo imprime «69,090 KM»; en el cuerpo se escribe así (sección 2). |
| 6 | Diagnóstico y causa raíz suficientemente sustentados. | PRC, PQR, diagnóstico (sección 5.1–5.2); si no, 🟡. |
| 7 | Evidencia relacionada con el componente y la causa. | Fotos, videos, códigos, mediciones (secciones 3.1, 5.2). |
| 8 | Historial de mantenimientos revisado completo. | Todos los servicios desde el inicio de la cobertura (sección 4.3). |
| 9 | Días y recorridos calculados correctamente. | Días naturales exactos, sin 180 días por 6 meses; tabla 4.4. |
| 10 | Carta de compromiso o reactivación validada contra el desfase. | Las tres comprobaciones de 4.6. |
| 11 | Componente cubierto y no excluido en el contrato aplicable. | Cláusulas 2 y 3 (5.1); casos especiales (5.3). |
| 12 | Campaña o boletín validado para VIN, modelo y síntoma. | Los cinco puntos de 5.3. |
| 13 | MSRP -10 % aplicado una sola vez. | `consultar_precios_mitsubishi` + cotejo de 6.5 (¿el taller ya lo aplicó?). |
| 14 | Mano de obra, cantidades, IVA y total recalculados. | Fórmula 6.2; cuadre de la tabla de parámetros (6.5, paso 7). |
| 15 | Topes o deducibles del contrato aplicados, si corresponden. | Cláusula 13 y póliza (6.2). |
| 16 | Aceptación sin justificación técnica innecesaria. | Procedente sin `desarrollo` ni `numerales`; el conector sólo imprime el cuadro (10.3). |
| 17 | Rechazo con artículo y numeral textual del contrato. | `numerales` y `clausulasLiterales` del Anexo (8, 10.3). |
| 18 | Tabla de mantenimiento incluida y excedidos en rojo, si aplica. | **Brecha del conector**: tabla en el chat + análisis línea por línea en el Informe; el técnico decide si edita el Word (10.4). |
| 19 | Visto bueno de Alexys previsto para rechazo. | Línea propia en la tabla de parámetros; sin él no se sube ni se rechaza (7.3). |
| 20 | Autorización especial prevista si el monto supera $100,000. | Línea propia en la tabla; sin ella no se sube ni se aprueba (7.3). |
| 21 | Formato Mitsubishi conservado. | Cubiertas `cubierta-mitsu*.docx` del conector; si se edita el Word, sin tocar encabezado, logotipo, colores, distribución, tipografía ni estructura (10.1). |
| 22 | No se modificó SIGA sin autorización expresa. | Dos pasos con `confirmar: true` sólo tras el «Confirmo»; control de cambios (7.3, 7.4). |

---

## 12. Lo que todavía no se sabe y las tensiones abiertas (no inventar)

**Resuelto por el PDF del 27/10/2026** (antes estaba aquí como pendiente):

- **Tolerancia**: 1 mes o 1,000 KM (sección 4.2). v1 decía que no estaba decidido si la de GarantiPlus (1,000 km / 30 días) aplicaba; ya no es esa: es la del PDF.
- **Intervalo general**: 6 meses o 10,000 KM, lo que ocurra primero, salvo que el contrato o el plan de la unidad digan otra cosa (sección 4.2).
- **Condiciones especiales del programa** (lo que David quedó de mandar: bomba de combustible y otras): son los casos especiales vigentes de la sección 5.3.

**Sigue sin saberse:**

- Cómo se verifica la **vigencia** cuando la ficha no trae fecha de inicio de la póliza y no hay carátula (sección 1).
- El **«listado Mitsubishi autorizado»** de componentes para desgaste prematuro antes de 140,000 KM: no está en el Conocimiento ni en el conector (5.2).
- El texto de la **campaña de satisfacción** de la bomba L200 MY25 y la **indicación de MMDM** sobre portalentes y mangueras de A/C: el tratamiento está en el PDF, pero no sus condiciones de aplicación (5.3).
- **Quién da la autorización especial** para montos superiores a $100,000, y si el umbral es con o sin IVA (7.3).
- Cómo se identifica y registra el **visto bueno de Alexys** (canal, forma); aquí sólo se registra lo que el técnico diga.
- La **tarifa de mano de obra** para Mitsubishi (el PDF habla de «mano de obra autorizada» sin fijarla) (6.2).

**Tensiones entre el PDF, el certificado, el conector y las reglas del proyecto** (se dicen al técnico cuando aparezcan; no se resuelven en silencio):

1. **«Cada avería se evalúa con su propio contrato» vs. programa sin certificado individual.** El contrato aplicable es el certificado del programa + la póliza de SIGA (+ carátula si existe). Lo particular de la unidad (vigencia, inicio, plan) sólo puede venir de la póliza o de documentos del expediente.
2. **«Word para revisión; PDF cuando esté completo» vs. el conector, que genera los dos a la vez.** Se cumple en espíritu: el Word (enlace «Descargar Word») es para revisar y editar, y el PDF sólo se sube cuando todo está completo y confirmado. Pero `05-redaccion-informes.md` dice que las correcciones se hacen regenerando, nunca editando a mano; en Mitsubishi el PDF del área admite el Word editable. Para un dato o monto pendiente, regenerar con el dato confirmado; editar el Word a mano sólo si el técnico lo decide (10.4).
3. **Tabla de mantenimientos en rojo** exigida por el PDF vs. el conector, que no hace tablas. Si el técnico edita el Word para meterla, ese documento no lo sube el conector y tendría que subirse a mano, contra la regla 12 de `instructions.md`. Hay que decidirlo con el área (o resolverlo en el conector) antes de abrir la cuenta (10.4).
4. **Visto bueno de Alexys y autorización especial > $100,000 vs. el «Confirmo» único de v4.** En Mitsubishi el «Confirmo» a la tabla no basta por sí solo: tiene que constar el visto bueno (rechazo) o la autorización (monto alto). Son pasos obligatorios antes de ejecutar en SIGA (7.3).
5. **IVA.** La regla general del proyecto es que los importes de los presupuestos ya incluyen IVA y no se calcula; la fórmula del PDF calcula IVA sobre un subtotal hecho con precios de lista **sin IVA** (MSRP × 0.90). En Mitsubishi manda la fórmula: partidas sin IVA, IVA desglosado y total con IVA (6.2).
6. **Casos especiales vs. texto del certificado.** La bomba L200 «conforme a la campaña de satisfacción» choca con 15.11 («campañas del fabricante» no cubiertas); portalentes y mangueras de A/C «cubiertos conforme a la indicación de MMDM» chocan con 2.9 y 15.4 (mangueras, morfología) y quizá con 15.5 (fugas); el desgaste prematuro antes de 140,000 KM choca con 1.4, 10, 15.1 («desgaste prematuro» en defectos previsibles) y 15.3. La nota de aplicación hace prevalecer «el contrato específico de la unidad y la instrucción formal más reciente»: los casos especiales son instrucción formal del área y de MMDM, y se aplican como `Criterio del área (PDF 27/10/2026)`, diciéndolo en una viñeta; si el técnico decide lo contrario, manda él.
7. **Sin comprobantes de mantenimiento.** En GarantiPlus no bloquea; en Mitsubishi el PDF manda solicitarlos (3.1). No se trasladan reglas de una cuenta a otra.
8. **Reglas del área sin cláusula** (v1 §3.6): «ruidos, zumbidos y vibraciones no se cubren» y «el odómetro no retrocede» siguen como criterio del área (5.5), sin numeral propio en el certificado.
9. **Inconsistencia de VIN.** El catálogo de SIGA tiene «Falta de relación en VIN», pero el PDF manda pedir el documento corregido y no emitir resolución definitiva (sección 2).
10. **Marca en el encabezado.** El PDF pide llenar «marca» en las aceptaciones; la cubierta Mitsubishi la trae fija («MITSUBISHI») y el conector ignora `marca`: se cumple sin mandarla.

---

## 13. El flujo con Mitsubishi en alcance (desde el 27/10/2026)

Lo mismo de `instructions.md` (tres mensajes, tabla de parámetros, `causas` por refacción, `motivo` del catálogo), con estas diferencias:

1. La plantilla es `mitsubishi`; el encabezado lleva sólo los siete campos de la sección 10.2; `numeroContrato` = `policyId`.
2. Toda cita es con la numeración del Anexo (sección 8).
3. Mantenimiento con el criterio de la sección 4 (6 meses / 10,000 KM, tolerancia 1 mes / 1,000 KM), no el de `casos-garantiplus.md` §13; y la tabla en el chat, con la brecha de 10.4.
4. En procedentes, `consultar_precios_mitsubishi` con todos los números de parte y la valoración a MSRP × 0.90 con IVA desglosado (sección 6); `actualizar_precios_mitsubishi` cuando el técnico suba la lista del mes.
5. La tabla de parámetros añade, según el caso, «Precio autorizado: MSRP −10 % (lista {mes})», «Visto bueno de Alexys» y «Autorización especial (> $100,000)», y el «Confirmo» no ejecuta sin ellos (7.3). El control de cambios de 7.4.
6. El resultado 🟡 sigue la tabla 3.1 del área (incluidos los comprobantes de mantenimiento) y el comentario de 3.3.

Al abrirlo (27/10/2026) quedó así lo que esta sección pedía antes:
- Las dos herramientas de precios, publicadas en producción con la lista de octubre cargada.
- `instructions.md` (v4.4) y `01-mecanica-siga.md` ya tratan a Mitsubishi como cuenta en alcance.
- El conector genera el Informe Mitsubishi maquetado (cubierta y rechazo). Sigue sin dibujar la tabla de mantenimientos en rojo: se hace como dice 10.4.
- Pendiente: cerrar un rechazo y una aprobación Mitsubishi de punta a punta en `pruebas` (el primer caso real se revisa con especial cuidado), y las dudas de la sección 12.

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
