# 01: Reinscribirse desde el detalle

**What to build:** permitir que un alumno vuelva a una actividad que había cancelado desde la pantalla de detalle. La misma inscripción debe volver a estar vigente si la actividad está habilitada, todavía no empezó y tiene cupo.

**Blocked by:** None (can start immediately).

**Status:** ready-for-agent

- [x] Una inscripción cancelada muestra el botón "Reinscribirme" en el detalle cuando se cumplen las reglas.
- [x] La acción se realiza por `POST`, usa la sesión del alumno y mantiene la protección CSRF.
- [x] La reinscripción vuelve vigente la misma inscripción, elimina la cancelación y conserva la fecha original.
- [x] El cupo disponible disminuye y nunca se crea una segunda inscripción.
- [x] El alumno recibe el mensaje "Reinscripción confirmada" y vuelve al detalle.
- [x] Si la actividad está deshabilitada, iniciada o sin cupo, no aparece el botón y se explica el motivo.
- [x] Cuando coinciden varios rechazos, se usa el orden deshabilitada, iniciada y sin cupo.
- [x] Se puede reinscribir dentro de las últimas 24 horas porque ese límite solo afecta a la cancelación.
- [x] No se agregan campos, tablas ni migraciones.
- [x] Las pruebas del servicio y del recorrido HTTP quedan verdes.

## Comments

Implementado con TDD en los seams de servicio y HTTP. El chequeo completo terminó con 64 pruebas verdes y sin migraciones pendientes.
