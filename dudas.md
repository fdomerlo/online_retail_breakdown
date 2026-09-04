### Preguntas que surgen del análisis de datos

1. **«¿Por qué pusimos el sistema de almacén como origen si esto es una tabla de ventas?»**
* *Respuesta:* Porque en el dataset encontramos registros de ajuste de inventario con precio 0 y descripciones como *lost*, *damaged* o *adjust*. Eso demuestra que el archivo arrastra movimientos internos del almacén que no fueron transacciones comerciales.

2. **«¿Qué hicimos con las 240.000 filas sin Customer ID? ¿Por qué las imputamos?»**
* *Respuesta:* Las excluimos para el análisis de comportamiento longitudinal. Provienen del checkout como invitado. Imputarles un ID único (ej. 99999) crearía un "supercliente" artificial distorsionando la recencia y la frecuencia. Para el negocio son ventas reales (sirven para finanzas), pero inservibles para predecir retención de personas.

3. **«¿Qué diferencia hay entre una fila con cantidad negativa y una con precio cero?»**
* *Respuesta:* Las cantidades negativas con prefijo 'C' en el Invoice son notas de crédito o cancelaciones de ventas genuinas emitidas por facturación. Las filas con precio cero son asientos contables o de stock directo del depósito, muchas veces cargadas a mano. Son dos sistemas de origen distintos.
