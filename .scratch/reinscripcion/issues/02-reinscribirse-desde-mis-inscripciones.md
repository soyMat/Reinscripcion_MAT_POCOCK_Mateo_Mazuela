# 02: Reinscribirse desde Mis inscripciones

**What to build:** ofrecer la misma posibilidad de reinscripción desde "Mis inscripciones", para que el alumno pueda volver sin buscar la actividad en el catálogo.

**Blocked by:** 01: Reinscribirse desde el detalle.

**Status:** ready-for-agent

- [x] Cada inscripción cancelada muestra "Reinscribirme" cuando la acción está disponible.
- [x] Si no puede reinscribirse, se muestra el motivo correspondiente en la misma pantalla.
- [x] Una reinscripción exitosa vuelve a "Mis inscripciones" y muestra el mensaje de confirmación.
- [x] La acción usa las mismas reglas y el mismo servicio que el detalle.
- [x] Las inscripciones vigentes conservan sus acciones actuales.
- [x] El alumno solo puede ver y modificar sus propias inscripciones.
- [x] El catálogo sigue sin mostrar una acción personal de reinscripción.
- [x] Las pruebas HTTP de la pantalla, los mensajes y la privacidad quedan verdes.

## Comments

- Implementado con ciclos TDD sobre la interfaz HTTP. La revisión de especificación no encontró faltantes; la revisión de estándares llevó a compartir la presentación de la reinscripción entre ambas pantallas. Verificación final: 67 pruebas verdes y sin migraciones nuevas.
