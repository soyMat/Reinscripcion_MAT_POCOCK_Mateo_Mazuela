# 01: Reinscribirse desde el detalle

**What to build:** permitir que un alumno vuelva a una actividad que había cancelado desde la pantalla de detalle. La misma inscripción debe volver a estar vigente si la actividad está habilitada, todavía no empezó y tiene cupo.

**Blocked by:** None (can start immediately).

**Status:** ready-for-agent

- [ ] Una inscripción cancelada muestra el botón "Reinscribirme" en el detalle cuando se cumplen las reglas.
- [ ] La acción se realiza por `POST`, usa la sesión del alumno y mantiene la protección CSRF.
- [ ] La reinscripción vuelve vigente la misma inscripción, elimina la cancelación y conserva la fecha original.
- [ ] El cupo disponible disminuye y nunca se crea una segunda inscripción.
- [ ] El alumno recibe el mensaje "Reinscripción confirmada" y vuelve al detalle.
- [ ] Si la actividad está deshabilitada, iniciada o sin cupo, no aparece el botón y se explica el motivo.
- [ ] Cuando coinciden varios rechazos, se usa el orden deshabilitada, iniciada y sin cupo.
- [ ] Se puede reinscribir dentro de las últimas 24 horas porque ese límite solo afecta a la cancelación.
- [ ] No se agregan campos, tablas ni migraciones.
- [ ] Las pruebas del servicio y del recorrido HTTP quedan verdes.
