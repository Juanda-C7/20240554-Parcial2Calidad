# Respuestas

## P2: fallas corregidas en Jenkinsfile

- `|| true` después de `bru run` ocultaba el código de error de Bruno y permitía que el pipeline continuara aunque fallaran pruebas.
- Jenkins publicaba `bruno/smoke/results.xml`, aunque la regresión genera `bruno/regresion/results.xml`, por lo que no mostraba sus resultados.
- La etapa `Build image` corría antes de `Regresion`, así que la imagen se construía antes de que las pruebas pudieran detener el pipeline.

## P3: builds

| Paso | Build | SHA de la revisión | Resultado / evidencia disponible |
|---|---:|---|---|
| 1. Jenkinsfile corregido | Pendiente de confirmar en Jenkins | `3884630b7809c91b353a87fbc36b826266451b19` | Falta confirmar número y resultado del build. |
| 2. Pruebas P1 | `#1` según la captura disponible | `91fb2b5c453883ab7c5bd3decb95d87f51aa90ad` | Rojo; falló `16-cobrar-ticket-sobre-tope.res.body.monto eq 60`. |
| 3. Corrección de `api.py` | `#3` según la captura disponible | `95cf4d3866af3ccf471823bef7f8658033c8a19` | Verde; resultado de tests sin fallas. |

SHA confirmados por Jenkins:

- Build rojo #1 (P1): `91fb2b5c453883ab7c5bd3decb95d87f51aa90ad`.
- Build verde #3 (`api.py` corregida): `95cf4d3866af3ccf471823bef7f8658033c8a19d`.

La captura roja disponible muestra un resumen del build, no la vista de Stages solicitada. Falta verificar en Jenkins el build del paso 1 y guardar las capturas requeridas de Stages con la barra de direcciones visible en `evidencia/jenkins/01-rojo.png` y `evidencia/jenkins/02-verde.png`.
