# Mecánica operativa de SIGA para el cierre de averías

Referencia para el proyecto "Averías GarantiPlus — copiloto del técnico". Describe qué pantallas y botones existen en SIGA, qué hace cada uno, qué queda registrado y cómo se relaciona con el conector "Lector de Averías", tal como se verificó en el ambiente de pruebas (`pruebas.garantiplus.mx`) y en producción (`intranet.garantiplus.mx`) con cuentas del área de averías. Las dos tienen la misma estructura de pantallas; si algo difiere, prevalece lo que se ve en pantalla.

Este documento **no** cubre criterios de cobertura (qué cláusula excluye qué); eso se decide con el certificado de cada avería en mano (ver `03-criterios-dictamen.md`). Aquí se separan tres cosas que conviene no mezclar: lo que hace SIGA, lo que no puede hacer el navegador integrado de Claude, y las reglas del área.

## Ambientes

| Ambiente | Base | Cuándo |
| --- | --- | --- |
| Producción | `https://intranet.garantiplus.mx` | Por omisión. Es donde viven las averías reales. |
| Pruebas | `https://pruebas.garantiplus.mx` | Solo cuando el técnico lo pide. Copia de producción con fecha de corte (al 06/10/2026 la copia era de alrededor del 19-20/09/2026), misma estructura, mismas cuentas. Nada de lo que se hace ahí afecta a producción. |

- Los folios existen en los dos ambientes, pero estatus, renglones, documentos y Seguimiento pueden diferir (167410: aceptada en producción el 28/09 con facturas que en pruebas no existen). Se trabaja con el expediente del ambiente elegido.
- **El conector trabaja en los dos ambientes con todas sus herramientas** (desde octubre de 2026). Ninguna herramienta lleva parámetro de ambiente: el conector indica en su respuesta en cuál está (la ficha trae el enlace "Ver en SIGA" con el host). La regla del proyecto es que ese host y el de la pestaña del navegador sean el mismo; si no, se detiene el trabajo y se avisa.
- Identificar el ambiente solo por la URL es frágil: conviene decirlo en la bitácora de cada cierre.
- Los filtros por columna del listado no recargan la tabla; la pestaña "Activas" trae todas las averías no cerradas (910 el 06/10/2026 en pruebas), con el estatus en la columna "Estatus".

## Rutas

| Ruta | Uso |
| --- | --- |
| `/Averias/Averias` | Listado. Pestañas: Activas · Sin atender (48 hrs) · Sin seguimiento taller · Cerradas. Página inicial del flujo. |
| `/Averias/Averias/Details/{folio}` | Consulta de una avería (solo lectura). Es la que se abre al revisar y la que se recarga para comprobar que el Informe subido ya aparece. |
| `/Averias/Averias/Edit/{folio}` | Pantalla de trabajo. Título "Actualización de avería" mientras está abierta; "Visualización de avería" (solo lectura) cuando llega a un estatus terminal o cuando la sesión no tiene permiso. Aquí se ejecutan renglones, Observaciones y dictamen. |
| `/Averias/MotivosRechazo` | Catálogo vivo de motivos de rechazo (18 al momento de escribir esto). |
| `/Averias/Tecnicos` | Técnicos dados de alta (para "Reasignar técnico"). |
| `/Averias/RefaccionesNoPermitidas` | Menú "Refacciones prods. amplia": refacciones **no cubiertas** por producto de cobertura amplia. SIGA la usa para su intento de rechazo automático. |
| `/Averias/RefaccionesPermitidas` | Menú "Refacciones prods. limitada": refacciones **cubiertas** por producto de cobertura limitada. |

## Ciclo de vida

`Registrada → Validación → Aceptada → Taller → Cerrada`, o bien `Validación → No procede garantía`. `Cancelada` puede ocurrir desde cualquier estatus. Solo en **Validación** (ya con presupuesto cargado por el taller) se dictamina.

## Pantalla Details

Además de los datos de la avería, el contrato y el vehículo, trae: "Información del distribuidor" (producción, frecuencia, siniestralidad), "Información histórica" (averías previas, importe, pago), "Detalles de la avería" (fecha de registro, registrada por, técnico, **Atención comercial True/False**, presupuesto, total indemnización), **"Logs de resolución de averías"** (la bitácora del intento de rechazo automático de SIGA: `TryAutoResolution()` cuenta refacciones consumibles y no consumibles, revisa la configuración de rechazo del producto y el proyecto, compara las refacciones del presupuesto con las "no permitidas" del producto y rechaza solo si todas caen ahí; si no, "se solicitará la resolución manual"), "Taller" (kilometraje, taller, refacciones con estatus), "Registro de factura(s)", "Síntomas de la avería" (descripción del cliente, pieza y, debajo, la **causa de rechazo** capturada en el renglón), "Presupuesto" (I.V.A., M.O., refacciones, diversos, total con IVA; tablas de refacciones y servicios con estatus), "Documentos" y "Seguimiento de avería". En estatus terminal muestra además la sección "Reapertura de avería" con el botón "Reabrir avería".

## Secciones de la pantalla Edit, en orden

1. Datos de la avería (folio, estatus, fechas, síntomas descritos por el cliente/taller). La cabecera dice "Actualización de avería {folio} / Garantía {póliza} / Contrato {contrato}" con las etiquetas de estatus y técnico, y arriba los botones "Cancelar avería" y "Cerrar avería".
2. Datos del contrato y del vehículo.
3. Asignación de técnico (con botón "Reasignar").
4. **Refacciones y servicios**: tabla administrativa con un renglón por refacción y por servicio. Cada renglón tiene: concepto, importe del taller, campo "Autorizado" (prellenado con el importe del taller), estatus del renglón (vacío / Aceptada / Rechazada), causa de rechazo (si la hay) y dos botones de solo ícono: ✓ aceptar y 🗑 rechazar.
5. Presupuesto (resumen de solo lectura de lo que subió el taller).
6. **Documentos**: carga de archivo con "Tipo de archivo". Para esta cuenta, en Validación, el único tipo disponible es **Resolución**. Debajo, "Documentos registrados" lista todos los archivos del expediente (los del taller: Presupuesto, Evidencia, Varios; y los del área: Resolución).
7. Taller reparador.
8. **Resolución**: botones "Procede garantía" y "No procede garantía". **Solo se muestra cuando todos los renglones de refacciones y servicios ya tienen estatus** (Aceptada o Rechazada); mientras falte uno, el panel está oculto. SIGA no dice en pantalla qué falta: hay que mirar la tabla.
9. Indemnización aprobada.
10. **Observaciones**: campo de texto con botones "Enviar" (visible para el taller) y "Uso Interno".
11. **Seguimiento de la avería**: bitácora cronológica con fecha/hora, estatus anterior → nuevo, texto y usuario.
12. Botones generales al pie: "Cancelar avería", "Cerrar avería" (mientras está abierta) o "Reabrir avería" (cuando está en estatus terminal).

## Acciones a nivel renglón (paso previo al dictamen)

- **Aceptar refacción o servicio** (✓): valida los campos "Cantidad", "M.O." y "Autorizado" (prellenados con los montos del taller, editables) y pide confirmación con un **diálogo nativo** del navegador ("¿Está seguro de aprobar el servicio?" / la refacción). El renglón pasa a "Aceptada" y se muestran los "Precios aceptados" junto a los del taller. **El navegador integrado de Claude no muestra ni completa los diálogos nativos**: el clic no hace nada y debe darlo el técnico.
- **Rechazar refacción** (🗑): abre un cuadro propio de SIGA "¿Está seguro(a) de rechazar la refacción?" con el campo "Causa de rechazo". Ahí va **uno de los motivos del catálogo, escrito tal cual** (regla del área; la causa queda impresa en "Síntomas de la avería" de la pantalla Details y no se puede corregir). Es el único clic de renglón que el navegador integrado completa.
- **Rechazar servicio** (🗑): diálogo nativo "¿Está seguro de rechazar el servicio?", sin campo de causa. Lo hace el técnico.
- Aceptar o rechazar un renglón **no** escribe en el Seguimiento ni cambia el estatus general de la avería.
- Los botones ✓ y 🗑 no tienen texto accesible: no se encuentran buscando por nombre, hay que localizarlos visualmente en la tabla.
- El total autorizado que resulta de los renglones aceptados debe ser el mismo que imprime el Informe; SIGA no lo valida, por eso el resumen de cierre lo compara antes de ejecutar.

## Dictamen general (sección "Resolución")

- Requiere que exista **al menos un documento con tipo Resolución** en "Documentos registrados". Si no, al confirmar cualquiera de los dos cuadros SIGA responde con la alerta *"Debe cargar por lo menos un documento de resolución"* y no hace nada más. La alerta es nativa del navegador: desde el navegador integrado de Claude no se ve, solo se nota que el estatus no cambió.
- **"No procede garantía"**: abre el cuadro **"Rechazo de garantía"** con el desplegable **"Motivo de rechazo"** (catálogo completo de `/Averias/MotivosRechazo`; abre con "Campaña y/o Fallo epidemico" preseleccionado, hay que elegir el motivo correcto) y los botones "Cerrar" y "Rechazar". Al confirmar, el Seguimiento registra `Validación → No procede garantía` con el usuario de la sesión (a veces dos veces en el mismo segundo; lo escribe SIGA), y la pantalla pasa a "Visualización de avería".
- **"Procede garantía"**: abre el cuadro **"Atención comercial"** con la casilla "¿La aprobación requirió atención comercial?" y el botón "Aprobar". Al confirmar, el Seguimiento registra `Validación → Aceptada`. Este flujo se verificó por la estructura de la pantalla y por el caso 165694; antes de pulsar, describir al técnico lo que se ve y pedir su confirmación.
- El motivo del catálogo (dictamen general) y la "Causa de rechazo" de cada renglón deben ser el mismo texto.

## Catálogo de motivos de rechazo (al momento de escribir esto)

Campaña y/o Fallo epidémico · Componente excluido · Componente No incluido en cobertura · Daño por uso o degradación · Falta al proceso o incompleto (Cliente) · Falta de relación en kms · Falta de relación en VIN · Fuga excluida · Influencia Externa · Intervalo de Mantenimiento Excedido · Mala Reparación Anterior · Negligencia de uso · Periodo de Espera · Preexistente · Sin Vigencia · Siniestro · Falta al proceso o incompleto (Distribuidor) · Falta de relación en DOT.

Consultar el catálogo vivo en `/Averias/MotivosRechazo`; puede cambiar.

## Documentos

- El Informe de Resolución lo genera el conector (PDF y Word, con borrador en vista previa y versiones en una bandeja) y **lo sube el propio conector** con `subir_resolucion` por la API de SIGA, en la carpeta Resolución (el PDF, que es el formato de todas las resoluciones del área). El navegador integrado de Claude no puede adjuntar archivos.
- **La subida no se puede deshacer**: SIGA no deja borrar documentos. Si se sube una versión equivocada, se sube la correcta después y las dos quedan en el expediente. Por eso la subida se confirma por versión y una sola vez.
- Después de subir, **hay que recargar la página de la avería** (`Details/{folio}` o `Edit/{folio}`) para ver el archivo: aparece en "Documentos" / "Documentos registrados" con tipo Resolución, el nombre `RESOLUCIÓN {folio}.pdf` y la fecha/hora de carga. Sin recargar, la pantalla sigue mostrando la lista anterior.
- Si la herramienta de subida no estuviera disponible, el técnico lo sube desde su equipo: Documentos → Tipo de archivo "Resolución" → elegir archivo → guardar.
- Los documentos del taller (presupuesto, evidencia, varios) los sube el taller desde su propio portal; el área no los carga.
- **Videos del expediente**: el conector los lee por fotogramas (sin audio) y entrega un enlace para reproducir el video completo con sonido en el navegador (caduca en 7 días). Un video no es "ilegible": se describe lo que muestran los fotogramas y, si el sonido importa, se pasa el enlace al técnico.

## Observaciones

- "Enviar": el comentario queda en el Seguimiento y lo ve el taller.
- "Uso Interno": el comentario queda en el Seguimiento solo para GarantiPlus.
- En la tabla "Seguimiento de la avería" las dos se ven iguales (fecha, estatus anterior → actual, texto, usuario); no hay marca de "interno". Por eso se pregunta la audiencia antes de publicar y se anota en la bitácora.
- Los dos botones funcionan desde el navegador integrado (envían el formulario, sin diálogo nativo).
- Un comentario no cambia el estatus; el dictamen tampoco publica comentarios. Son dos operaciones separadas, y el orden del área es: documento → comentario → dictamen.

**Plantillas del área** (se usan tal cual):

- Rechazo (al cargar la Resolución, con "Enviar"): *"Hola, excelente día. Compartimos resolución del expediente y se explica en el archivo adjunto como resolución."*
- Aceptación (tras marcar "Procede garantía", con "Enviar"; texto literal del Seguimiento de 165694, 11/09/2026):
  > Buen día, una vez que la avería se encuentre en estatus "Aceptada" y se haya compartido la resolución, deberán cargar en el apartado de documentos los siguientes requisitos: Finiquito firmado por el cliente (se encuentra adjunto en la resolución), identificación oficial del cliente por ambos lados para cotejo de nombre y firma, datos bancarios para realizar la transferencia (Banco, Razón Social, Cuenta y CLABE Interbancaria), Constancia de Situación Fiscal y Opinión de Cumplimiento positiva. Una vez cargada la documentación anterior, deberán seleccionar la opción "Vehículo en Taller" y posteriormente "Aceptar". Al realizar esta acción se habilitarán nuevos campos para cargar la factura en formato PDF y XML. Es importante que, una vez cargados ambos archivos, seleccionen la opción "Enviar", ya que únicamente de esta forma quedarán visibles como archivos descargables para el área de pagos. La factura deberá emitirse por el monto aceptado en la resolución y con los siguientes datos: Razón Social: GARANTIPLUS MEXICO RFC: GME160927DW0 Calle: SIERRA CANDELA 80 Colonia: LOMAS DE CHAPULTEPEC III SECCION C.P. 11000 Alcaldía: Miguel Hidalgo Ciudad: Ciudad de México Uso CFDI: Gastos en general Método de pago: PPD Forma de pago: Transferencia Quedamos atentos a cualquier duda o comentario. Saludos.
- Pendiente (con "Enviar"): *"Hola, buen día. Se revisó la avería {folio} y el expediente sigue incompleto para poder resolverla. Hace falta: {lista numerada}. Favor de cargarla en SIGA para continuar con la evaluación. Quedamos atentos. Saludos."*

Si el técnico corrige un dato administrativo de la plantilla (domicilio, requisitos), se usa el corregido en ese folio y se avisa para actualizar este archivo; no se copian datos de un caso anterior sin revisarlos.

## Acciones administrativas

- **"Cancelar avería"**: motivo en texto libre, sin confirmación adicional. Seguimiento: `Cancelación de avería por el usuario {correo} razón: {motivo}`. Estatus → Cancelada.
- **"Cerrar avería"**: motivo en texto libre + factura PDF/XML opcional. Seguimiento: `Cierre de avería por el usuario {correo} razón: {motivo}`. Estatus → Cerrada. Normalmente se usa después del pago.
- Ninguna de las dos dictamina cobertura.
- **"Reabrir avería"**: único botón en estatus terminal (sección "Reapertura de avería" de la pantalla Details). Devuelve la avería a **Validación**; el Seguimiento registra `No procede garantía → Validación · Avería restablecida en validación por {correo}` y conserva los renglones y los documentos (visto en 164143 el 21/09/2026).

## Permisos

Solo el **técnico asignado** y la cuenta del área (`averias@garantiplus.mx`) pueden operar una avería. Con otro usuario de GarantiPlus la pantalla `Edit/{folio}` abre como "Visualización de avería" (solo lectura) aunque el estatus sea Validación, sin botones de renglón ni de dictamen; no es un error de SIGA y la pantalla no explica el motivo. Solución: entrar con la cuenta del área o reasignar la avería (visto el 06/10/2026 con un usuario de dirección).

## Qué puede hacer la cuenta del área según el estatus

| Estatus | Acciones |
| --- | --- |
| Registrada | Cancelar · Cerrar · Reasignar técnico |
| Validación (con presupuesto) | Lo anterior + aceptar/rechazar renglones + (con Resolución subida) Procede / No procede garantía |
| Aceptada / Taller | Cancelar · Cerrar (con factura) · Reasignar |
| Cancelada / Cerrada / No procede garantía | Solo "Reabrir avería" |

## Señales que no son errores

- Alerta de documento de resolución faltante → falta subir el Informe.
- El ✓ de un renglón o el 🗑 de un servicio no responde → diálogo nativo; lo hace el técnico.
- Solo "Resolución" en el desplegable de tipo de archivo → normal para esta cuenta.
- Un renglón rechazado no aparece en el Seguimiento → normal; verificar en la tabla.
- Título "Visualización de avería" → estatus terminal o sesión sin permiso.
- Avería ausente de "Activas" → está en "Cerradas".
- Dos entradas idénticas en el Seguimiento (`Validación → No procede garantía` dos veces en el mismo segundo) → las escribe SIGA, no es un doble clic; no repetir.
- No aparece el panel "Resolución" → falta un renglón por dictaminar.
- Al confirmar Procede / No procede no pasa nada → aviso nativo que no se ve; casi siempre falta el documento de Resolución.
- El Informe recién subido no aparece en "Documentos" → falta recargar la página.
- El mismo folio se ve distinto en pruebas y en producción → son dos copias; se trabaja con el ambiente elegido.

## Latencia y reintentos

SIGA no protege contra envíos duplicados: un segundo clic por latencia produce dos comentarios o dos transiciones. Regla: después de cada acción se recarga la página y se lee el Seguimiento o la tabla antes de decidir si hubo que repetir. Si un botón no produjo cambio visible, la causa más frecuente es un aviso nativo invisible, no una falla de red.

## Sobre el conector "Lector de Averías"

- Lee y escribe en la API de SIGA, **en producción o en pruebas**; su respuesta dice en cuál (enlace "Ver en SIGA"). Si la pantalla y el conector difieren en el estado operativo, manda la pantalla y se reporta.
- Siete herramientas. **`expediente_completo({ claimId })`** trae en una sola respuesta la ficha, el índice de documentos (con enlaces `/video`), el certificado completo anonimizado y el contenido de todos los documentos (PDF como texto o imagen, imágenes, videos en 3 fotogramas con su segundo), ordenados por peso para el dictamen; tope 20 imágenes o 15 MB por llamada, y al final nombra lo que quedó fuera. `datos_averia`, `listar_documentos` y `leer_documento` siguen existiendo, pero solo `leer_documento` tiene uso después de `expediente_completo` (lo que quedó fuera, `anchoMax`, `segundos`, `fotogramas`; tope 8 imágenes o 10 MB). `generar_resolucion` produce el Informe definitivo (sin `vistaPrevia`): versión/huella y cuatro enlaces (ver en el navegador, PDF, Word y bandeja de versiones; 7 días), archivo `RESOLUCIÓN {folio}.pdf`. La vista previa (`vistaPrevia: true`) existe pero no se usa en el flujo: su visor se titula "borrador" y no se puede subir. **`subir_resolucion({ claimId, confirmar?, version? })`** carga en SIGA el PDF de un definitivo: llamada sin `confirmar` = dice qué versión subiría (por omisión la última), con enlace, y si ya hay resoluciones en la avería; llamada con `confirmar: true` = sube. No cambia el estatus de la avería. Es lo único que el conector escribe en SIGA y no se puede deshacer.
- Cada llamada es un permiso que aprueba el técnico: una por folio para abrir, una para lo pendiente, un definitivo por versión y dos de subida (en el mismo turno). Para que no tenga que aprobar cada llamada: en claude.ai, Ajustes → Conectores → Lector de Averías → marcar las herramientas como "Permitir siempre". Todas son de solo lectura salvo `generar_resolucion` (crea el PDF/Word en el servidor del conector) y `subir_resolucion` (carga ese PDF en SIGA).
- La ficha indica la plantilla del Informe (`garantiplus` o `mitsubishi`). Los contratos Mitsubishi no tienen certificado individual; `numeroContrato` es el `policyId`. "Bridgestone llantas" es un producto distinto con su propio condicionado. Ambos fuera de alcance por ahora.
- El kilometraje de la avería (`kmAveria`) no viene de SIGA: se lee del odómetro (o del presupuesto / orden de ingreso si no hay foto) y se manda en el encabezado. Un Informe nunca se genera con ese dato vacío ni en 0, y `kmInicial` siempre es menor que `kmAveria`. Las instrucciones del proyecto traen el esquema obligatorio completo del encabezado, con fuente y validación por campo.
- El conector prellena el encabezado desde SIGA, pero cualquier campo que no venga en SIGA sale vacío o en 0 en el documento. Por eso se mandan **todos** los campos en `encabezado` en cada llamada, tomados primero del certificado (HOJA RESUMEN) y después de SIGA.
- En un Informe procedente, el cuerpo que arma la plantilla del conector incluye un desglose en texto de las partidas y la frase de cierre. Ese texto lo pone el conector, no Claude: si sobra, es un cambio en la plantilla del conector. Claude no debe añadir `desarrollo` en procedentes para no duplicarlo.
- `averias_pendientes` lista todas las cuentas y marca las de Mitsubishi como "MITSUBISHI (programa, sin contrato individual)". El alcance actual del proyecto es solo GarantiPlus MX: esas entradas y las de llantas Bridgestone se omiten al mostrar la lista.
- `generar_resolucion` se niega a transcribir un numeral que no exista en el condicionado de este certificado; en ese caso se usa `clausulasLiterales` con el texto exacto. Con `numerales: ["9"]` solo transcribe el encabezado de la cláusula: la 9 y la definición de AVERÍA/AS van siempre en `clausulasLiterales` (ver `05-redaccion-informes.md`). No hace tablas: el análisis de intervalos va una línea por servicio en `desarrollo`.
- **IVA**: los importes de los presupuestos ya vienen con IVA incluido en todas las cuentas. En un procedente se manda `valoracion.totalConIva` igual a la suma de las partidas autorizadas y no se manda `iva`; el aviso "No mandaste el IVA" del conector es informativo. Nunca se pide el IVA al técnico ni al taller.
- Los enlaces del Informe caducan a los 7 días; la bandeja conserva todas las versiones del folio. La aprobación del técnico vale para una versión concreta: cualquier cambio posterior crea otra versión y requiere nueva aprobación antes de subir.
