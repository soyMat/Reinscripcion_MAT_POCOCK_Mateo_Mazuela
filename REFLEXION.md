# Reflexión

A diferencia del ejemplo, decidimos permitir cancelar y reinscribirse tanto desde el detalle como desde "Mis inscripciones", sin agregar otra pantalla de confirmación.
La pregunta del grill que no se me había ocurrido fue qué pasaba si una reinscripción competía por el último cupo.
Esa pregunta nos llevó a probar concurrencia real y confirmar que solo una operación puede ganar.
La retro propuso que la skill `implement` también recuerde cerrar el ticket local y revisar documentación que puede quedar vieja, como el número de tests.
