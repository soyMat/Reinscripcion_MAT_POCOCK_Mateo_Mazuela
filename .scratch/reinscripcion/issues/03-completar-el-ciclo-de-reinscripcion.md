# 03: Completar el ciclo de reinscripción

**What to build:** completar el recorrido para que una inscripción pueda pasar varias veces entre vigente y cancelada sin romper las reglas existentes ni mostrar información vieja.

**Blocked by:** 01: Reinscribirse desde el detalle.

**Status:** ready-for-agent

- [x] El alumno puede cancelar y reinscribirse más de una vez mientras cumpla las reglas de cada acción.
- [x] Una reinscripción dentro de las últimas 24 horas no permite cancelar fuera de la ventana.
- [x] Siempre se conserva la fecha de la primera inscripción.
- [x] Si vuelve a cancelar, solo queda guardada la cancelación más reciente.
- [x] Los textos de cancelación dejan de afirmar que nunca será posible reinscribirse.
- [x] Docentes y administración ven el estado actual, la fecha original y ninguna cancelación anterior después de reinscribir.
- [x] La administración sigue siendo de solo lectura.
- [x] `seed_demo` conserva una inscripción cancelada y nunca la reactiva por su cuenta.
- [x] La documentación de uso explica la reinscripción y deja de describirla como bloqueada.
- [x] La suite completa queda verde y el número de pruebas documentado se actualiza.

## Comments

- Se completó con TDD sobre servicio y HTTP, reutilizando las pruebas existentes de administración y `seed_demo`. Las revisiones de especificación y estándares no encontraron faltantes ni violaciones. Verificación final: 71 pruebas verdes y sin migraciones nuevas.
