# Cómo se redacta el Informe de Resolución, al estilo del área

**Versión de este recurso: 2026-10-28 (v2: la tabla de intervalos de mantenimiento la imprime el conector con `mantenimientos`; `desarrollo` queda para el párrafo del dictamen; ejemplo 171469 actualizado. Antes sin versión.)** Quien lo edite actualiza aquí la fecha y la nota de qué cambió.

El Informe es el documento que se sube a SIGA y que recibe el taller. Tiene que leerse como los que escribe el área, no como un resumen del chat. Esta guía sale de comparar resoluciones reales (157279, 159886, 160942, 161239, 162130, 162229, 162262, 162922, 163912, 164143, 164276, 171469 y las aceptadas 160579, 161305, 161833, 162526, 162559, 163549, 165694) con lo que genera el conector.

El generador no decide nada: recibe una decisión ya acordada con el técnico y la convierte en un documento verificable. Todo lo que entra (datos, cláusulas, importes) tiene fuente en el expediente; nada se inventa ni se completa por inferencia.

## 1. Lo que devuelve el conector (octubre 2026) y cómo se usa

- **Se genera directo el definitivo** (`generar_resolucion` sin `vistaPrevia`): una versión con huella y cuatro enlaces (7 días): **Ver en el navegador**, **Descargar PDF**, **Descargar Word**, **Bandeja de versiones**; nombre `RESOLUCIÓN {folio}.pdf / .docx`. El enlace "Ver en el navegador" **se abre de inmediato en una pestaña nueva del navegador integrado, si está disponible**, para que el técnico lo lea (si no lo está, se entrega el enlace y se dice); en el chat va el encabezado, los enlaces y la pregunta `¿Lo subo a SIGA? Sí / Cambiar algo`.
- **La vista previa (`vistaPrevia: true`) no se usa.** Su archivo se titula "borrador", no se puede subir, y en la prueba del 08/10/2026 llevó al técnico a descargarlo, renombrarlo y subirlo a mano (167311). Cada corrección es otro definitivo: la bandeja conserva todas las versiones y solo se sube la aprobada.
- El **PDF** es el archivo principal (es el formato de todas las resoluciones del área); Word es la copia editable.
- `subir_resolucion` carga en SIGA el PDF de un definitivo. Con el "Sí" del técnico, en el mismo turno: sin `confirmar` (dice qué versión subiría y si ya hay resoluciones) y, si es la misma versión que el técnico vio, con `confirmar: true`. No se puede deshacer y una versión no se sube dos veces. Después se comprueba que el archivo está en SIGA (`renglones_averia`, o la página recargada si el navegador integrado está disponible).
- La **aprobación del técnico vale para una versión**. Si después de aprobar cambia cualquier dato (un importe, una fecha, una cláusula), se regenera, se vuelve a abrir y se vuelve a aprobar.
- Las correcciones se hacen regenerando, nunca editando el archivo a mano; el técnico nunca descarga ni renombra nada.
- Lo que el conector **no** hace: tablas (un texto con `|` o saltos de línea se aplana en un solo párrafo), y el numeral `"9"` por `numerales` solo transcribe el encabezado de la cláusula, sin los incisos. Las dos cosas tienen remedio abajo.
- Lo que el conector **valida** y por lo que se niega: campos obligatorios vacíos (dice cuál), numerales que no existen en este certificado (dice cuál), subtotales que no cuadran. Sus errores son accionables: se corrige el dato y se repite, sin perder lo demás.

## 2. Estructura fija del Informe (la pone la plantilla)

1. Encabezado: DATOS DE AVERÍA / DATOS DEL VEHÍCULO. **Ningún campo vacío ni en 0** (ver esquema en las instrucciones §5.1).
2. "Una vez recibida toda la información facilitada y tras analizar la avería que nos ocupa y elementos afectados, con base al contrato, pasamos a indicar:"
3. **Frase de dictamen** = `componente` + `causaBreve` (improcedente) o `componente` + importe (procedente).
4. **Cuerpo** = párrafos de `desarrollo` (uno por elemento).
5. "Lo anterior es explícitamente motivo de una exclusión en los apartados que a continuación se indican:" + cláusulas transcritas (`numerales` + `clausulasLiterales`).
6. Cierre: "Expuesto lo anterior se informa que GarantiPlus México S.A.P.I. de C.V. no procede / procede con el pago…"

Tú solo controlas 3, 4 y 5. Ahí está toda la calidad.

## 3. Reglas de redacción

- **`componente`** se escribe como acción sobre la pieza, en minúsculas: "reemplazo de transmisión", "sustitución de alternador y banda", "sustitución de sensor radar", "reemplazo de bomba de agua y anticongelante, cárter, juntas y aceite". Nunca "caja de velocidades (transmisión)" ni paréntesis explicativos.
- **`causaBreve`** encaja tras "debido a que" y usa las fórmulas del área (sección 4). Cita hechos del expediente y el contrato. **Nunca** cites el Seguimiento ni "lo declarado por el taller en el seguimiento": el taller recibe este documento.
- **`desarrollo`**: párrafos cortos, uno por idea, en tercera persona y tono técnico. Sin viñetas de chat, sin "Supuesto:", sin fuentes entre paréntesis. La explicación detallada que vio el técnico en el chat no se copia: al taller solo llega el hecho y el fundamento.
- **Cláusulas**: siempre literales y completas, **del certificado de esta avería**. **Nunca "(...)"** ni resúmenes, y nunca un numeral "equivalente" tomado de otro contrato. Si un numeral tiene incisos, cita el inciso exacto (12.3, 13.6) y, si hace falta el contexto, el encabezado del artículo.
- **Cláusula 9** (mantenimientos): no uses `numerales: ["9"]`. Pásala en `clausulasLiterales` con `numeral: "9"`, `titulo: "MANTENIMIENTOS PERIÓDICOS"` y `texto` = el párrafo de entrada + el inciso que aplique (**SEMINUEVOS** o **NUEVOS**) + el inciso del carnet + "El incumplimiento de cualquiera de los requisitos anteriores invalidará este contrato.", copiados del certificado del caso. Así lo hace el área.
- **Orden**: el conector pone primero los `numerales` y después las `clausulasLiterales`. Para un rechazo por mantenimiento queda 12.3 y luego 9, igual que el área.
- **Fecha de cierre** = hoy. **Km de avería** = odómetro (o presupuesto / orden de ingreso). Si dos fuentes dan cifras distintas, se pregunta al técnico cuál va; no se elige en silencio.
- Datos personales (nombre del cliente, RFC, teléfono) nunca van en el cuerpo.

## 4. Fórmulas del área por tipo de caso

### 4.1 Improcedente por intervalo de mantenimiento excedido

`causaBreve`:
> el historial de servicios proporcionado muestra un intervalo de mantenimiento excedido por {tiempo | kilometraje}, según el análisis de intervalos mostrado más adelante. Esto ya que dicho contrato estipula la realización de servicios cada {10,000 km o 6 meses | 12,000 km o 12 meses}, lo que ocurra primero, y está previsto en los artículos que se transcriben

`mantenimientos` (**la tabla**; desde el 28/10/2026 la imprime el conector tras la frase de dictamen, con la cabecera «ANÁLISIS DE INTERVALOS DE MANTENIMIENTO», la marca, el modelo y el VIN del encabezado, el intervalo y las columnas FECHA · KM · DIAS · OBS · RECORRIDO; DIAS y RECORRIDO los calcula él):
```json
"mantenimientos": {
  "intervalo": { "meses": 6, "km": 10000 },
  "servicios": [
    { "fecha": "2026-01-30", "km": 108956 },
    { "fecha": "2026-10-02", "km": 113122, "obs": "KM AVERÍA · EXCEDIDO TIEMPO +64 DÍAS" }
  ]
}
```
- Filas: la primera es la primera factura (nuevo) o el inicio de garantía (seminuevo), con su km; una por servicio acreditado; **la última es la avería** con su fecha y su km. Entre 2 y 40, en orden cronológico, cada una con `fecha` y `km` (un servicio sin alguno de los dos no es fila: se nombra en el chat y se pide). Sólo en improcedente.
- `obs` la marca el técnico (Claude la propone con la tolerancia de la cuenta: `casos-garantiplus.md` §13 o `casos-mitsubishi.md` §4.2): ≤ 40 caracteres, una línea, sin `{}` ni `|`: `EXCEDIDO KM +2,450`, `EXCEDIDO TIEMPO +41 DÍAS`, `EXCEDIDO KM Y TIEMPO`; en la última fila, `KM AVERÍA` y, si ese tramo es el que excede, `KM AVERÍA · EXCEDIDO TIEMPO +64 DÍAS`. El exceso se mide contra el intervalo base (10,000 km / 6 meses de calendario); la tolerancia decide si lleva `obs`, no la cifra. Un tramo dentro de la tolerancia **no lleva `obs`** aunque el conector avise que supera el intervalo base.
- El conector pinta en rojo la OBS y, si la aritmética lo respalda, RECORRIDO (km) o DIAS (tiempo). Su respuesta enseña la tabla en «## Análisis de intervalos de mantenimiento»: cotéjala.

`desarrollo` (un párrafo; ya no se escribe la tabla línea por línea): "Del análisis de los comprobantes de mantenimiento se identificó que entre el servicio registrado el {fecha anterior} con {km} km y {el servicio registrado el {fecha} | la avería del {fecha}} con {km} km transcurrieron {días} días y se recorrieron {km} km. El contrato establece un intervalo de {10,000 km o 6 meses | 12,000 km o 12 meses}, lo que ocurra primero, {con una tolerancia de 1,000 km o 30 días}. Por lo tanto, el intervalo se excedió en {km} km y/o {días} días."

`numerales: ["12.3"]` (añade `"12.4"` si además hubo documentación requerida y no entregada en 72 h) + `clausulasLiterales` con la cláusula 9 completa como se indica en la sección 3. Sin más `desarrollo`.

### 4.2 Improcedente por causa excluida (desgaste, fuga, morfología)

`causaBreve` (fórmula del área):
> con base en el diagnóstico técnico proporcionado, {lo que se observó}, condición que corresponde a {un proceso de degradación progresiva | una pérdida de hermeticidad | la pérdida de la morfología inicial} del componente y no a una rotura súbita e imprevista

`desarrollo`, dos o tres párrafos, en este orden (así redactan 162922, 162130, 161932, 164276, 161239):
1. **Qué se observó**: lo que dice el diagnóstico del taller y lo que muestran fotos y videos, con sus términos ("polea agarrotada", "pastas de fricción adelgazadas", "fuga de refrigerante por la bomba de agua", "holgura entre piñón y cremallera").
2. **Por qué es progresivo o excluido**: cómo trabaja la pieza y por qué ese daño se desarrolla con el uso, la fricción, la temperatura o los ciclos; o por qué una fuga es pérdida de estanqueidad y no rotura interna.
3. **Consecuencia**: "La pérdida de funcionalidad se presenta de manera gradual como resultado del uso y condiciones de operación, sin existir una rotura súbita o evento imprevisto, tal como lo indica el contrato en los numerales que se transcriben." Si hay daños secundarios (banda, condensador), decir que son consecuencia directa de la causa excluida.

Cláusulas: `clausulasLiterales` con la **definición de AVERÍA/AS de la cláusula 1** (desde "Se entiende por avería mecánica…" hasta "…cualesquiera influencias externas.") + `numerales` con el inciso de 13 que aplique (13.4 vida útil, 13.5 morfología, 13.6 fugas y consumibles, 13.3 mala reparación, 13.19 siniestro, 13.14 seguir circulando) + `"8"` si quieres reforzar "deterioro y/o desgaste normal".

### 4.3 Improcedente por falta al proceso

`causaBreve`:
> se ha realizado un desmontaje y desarme del {componente} sin la debida autorización de GARANTIPLUS MÉXICO, S.A.P.I. DE C.V. ni la resolución del expediente correspondiente

o, para documentación no entregada:
> la documentación requerida el {fecha} (historial de mantenimientos, carta de diagnóstico y evidencia del componente) no fue aportada dentro del plazo de 72 horas previsto en el contrato

`desarrollo`: normalmente ninguno; si acaso un párrafo con las fechas (ingreso, registro, solicitud, vencimiento). `numerales: ["12.1", "10.4"]` o `["12.4"]`.

Receta verificada (167410, 06/10/2026, rechazo documental): `numerales: ["12.4"]` (el conector transcribe el encabezado de la 12 y el inciso 4 completo) más la **cláusula 9 completa** en `clausulasLiterales`, sin `desarrollo`. `causaBreve`: *"no se aportó a GarantiPlus México la documentación requerida para acreditar el cumplimiento de los mantenimientos periódicos exigidos por el contrato (historial y facturas de servicio de la unidad), solicitada el {fecha 1} y nuevamente el {fecha 2}, sin respuesta dentro del plazo de 72 horas previsto en los artículos que se transcriben"*. Sale en 3 páginas: frase, 12.4, 9 y cierre. Motivo de catálogo: Falta al proceso o incompleto (Distribuidor).

### 4.4 Improcedente por componente excluido o periodo de espera

`causaBreve`:
> el componente reclamado se encuentra expresamente excluido en la cláusula 1 del certificado de garantía suscrito

o
> la avería se presentó dentro del periodo de espera de 90 días establecido para {transmisiones DSG/CVT | la dirección electroasistida}, contado desde el inicio de vigencia del {fecha}

Cláusulas: `clausulasLiterales` con el inciso de la cláusula 1 que lo excluye (o el 12.9 en productos que lo ponen ahí), copiado del certificado.

### 4.5 Procedente (completo o parcial)

- `componente`: "sustitución de {pieza}" ("sustitución de módulo de palanca de velocidades", "sustitución de inyectores de combustible").
- `valoracion.partidas`: **solo lo autorizado**. Las partidas que no se autorizan (diagnóstico 13.8, consumibles 13.6, piezas sin fallar 13.20) **no se mandan**: ni con `autorizada: false` ni con `nota`. Se dicen al técnico en el veredicto y se rechazan en los renglones de SIGA, pero el Informe no las menciona. Regla del área (Miguel, 08/10/2026, folio 170116): el documento procedente lleva el encabezado, la frase con el importe y la valoración de lo autorizado; nada de "Detalle de otros conceptos", "Conceptos no cubiertos" ni explicaciones de por qué sí aplica.
- **Si el presupuesto trae muchas líneas** (más de cinco o seis refacciones, tornillería, grasas, calibraciones), **consolida**: una partida `refaccion` "Refacciones" con la suma de las autorizadas y una partida `manoDeObra` "Mano de obra". Con pocas líneas, una por refacción está bien. Así la tabla cabe en la primera página y el conector no agrupa nada como "Otros conceptos (n)".
- `totalConIva`: si el presupuesto no desglosa IVA, los importes ya lo incluyen y `totalConIva` = suma de partidas autorizadas. Si lo desglosa, las `partidas` van antes de IVA como las rotula el presupuesto, `valoracion.iva` = IVA de lo autorizado (16 % del subtotal autorizado cuando se excluyó alguna partida; el del presupuesto si se autoriza todo) y `totalConIva` = subtotal + IVA. Ese total es el que se marca en los renglones de SIGA y el que confirma el técnico en el resumen de cierre: una sola cifra en los tres lugares.
- **Sin `desarrollo`, sin `numerales`**. El área no explica por qué acepta.

**Verificado el 06/10/2026 (165728) y el 08/10/2026 (170116):** el conector imprime la tabla de valoración (partidas numeradas, MANO DE OBRA, TOTAL C/IVA) y después las páginas fijas del formato de aceptación del área: carta de recepción del vehículo, listado de documentación requerida para pago, pasos para la carga de documentos en SIGA y proceso SIGA. **Defectos conocidos del conector (pendientes de plantilla):** debajo de la tabla repite el desglose en texto; con partidas de tipo `diverso` las agrupa como "Otros conceptos (n)" y añade una página "Detalle de otros conceptos"; con partidas no autorizadas añade "Conceptos no cubiertos". Los tres se evitan desde aquí mandando solo lo autorizado y consolidado; no los compenses con `desarrollo`. El archivo sale como `RESOLUCIÓN {folio}.pdf` / `.docx`, y `subir_resolucion` lo carga en SIGA con ese nombre.

## 5. Antes de generar el definitivo (lista de control; se repite en cada regeneración)

1. El folio del Informe es el folio abierto; contrato, producto y VIN del encabezado son los de la ficha de SIGA y del certificado leído.
2. Encabezado completo; km inicial < km avería; fechas en orden (inicio ≤ avería ≤ cierre).
3. La frase de dictamen se lee de corrido y empieza con "reemplazo de…" / "sustitución de…".
4. El cuerpo no menciona el chat, el Seguimiento, "Supuesto", fuentes entre paréntesis ni viñetas.
5. Las cláusulas están completas, sin "(...)", y son las del certificado de este caso (numeración de este producto).
6. En mantenimiento: la tabla del conector trae todos los servicios y la avería; los días y km cuadran con los comprobantes; las `obs` en rojo son las que marcó el técnico y ninguna cae dentro de la tolerancia.
7. En procedente: solo partidas autorizadas (consolidadas si son muchas); suman el total; el total es el que irá a los renglones de SIGA; nada de "Detalle de otros conceptos" ni "Conceptos no cubiertos".
8. El veredicto del documento (`procedente` / `improcedente`) coincide con el color del veredicto acordado con el técnico.
9. El definitivo se abrió en el navegador y el técnico dijo que sí.

## 6. Ejemplo completo (171469, rechazo por mantenimiento, equivalente al que redactó el área)

Parámetros de `generar_resolucion`:
- `claimId` 171469 · `plantilla` garantiplus · `veredicto` improcedente · `componente` "reemplazo de transmisión"
- `causaBreve`: "el historial de servicios proporcionado muestra un intervalo de mantenimiento excedido por tiempo, según el análisis de intervalos mostrado más adelante. Esto ya que dicho contrato estipula la realización de servicios cada 10,000 km o 6 meses, lo que ocurra primero, y está previsto en los artículos que se transcriben"
- `mantenimientos`: `{ intervalo: { meses: 6, km: 10000 }, servicios: [{ fecha: "2026-01-30", km: 108956 }, { fecha: "2026-10-02", km: 113122, obs: "KM AVERÍA · EXCEDIDO TIEMPO +64 DÍAS" }] }` (30/01 + 6 meses = 30/07/2026; del 30/07 al 02/10 van 64 días, más de los 30 de tolerancia; 245 días en total, sin ningún servicio acreditado). El conector imprime la tabla con el título, «CHEVROLET AVEO LSGHD52H5LD031639», el intervalo, la fila de inicio y la de la avería con 245 días y 4,166 km, la OBS y DIAS en rojo.
- `desarrollo`: ["Del análisis de los comprobantes de mantenimiento se identificó que entre el inicio de garantía del 30/01/2026 con 108,956 km y la avería del 02/10/2026 con 113,122 km transcurrieron 245 días y se recorrieron 4,166 km sin ningún servicio de mantenimiento acreditado. El contrato establece un intervalo de 10,000 km o 6 meses, lo que ocurra primero, con una tolerancia de 1,000 km o 30 días. Por lo tanto, el intervalo se excedió en tiempo."]
- `numerales`: ["12.3"]
- `clausulasLiterales`: [{numeral "9", titulo "MANTENIMIENTOS PERIÓDICOS", texto = párrafo de entrada + inciso SEMINUEVOS + inciso del carnet + "El incumplimiento de cualquiera de los requisitos anteriores invalidará este contrato.", copiados del certificado 679982}]
- `encabezado`: 171469 · 679982 · EXCELLENCE SEDANES GM M2 12 · CHEVROLET · AVEO · LSGHD52H5LD031639 · 2026-01-30 · 2026-10-02 · 2026-10-06 · 108956 · 113122

Resultado: frase de dictamen, tabla de intervalos, párrafo, 12.3 primero, cláusula 9 completa, cierre "no procede". Es el mismo contenido que el PDF que redactó el técnico para ese folio. Flujo completo: definitivo abierto en el navegador → "¿Lo subo a SIGA?" → "Sí" → `subir_resolucion` sin confirmar y, con la misma versión, con `confirmar: true` → recargar `Details/171469` y ver `RESOLUCIÓN 171469.pdf` → resumen de cierre → renglones, comentario y dictamen en `Edit/171469`.
