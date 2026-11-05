# 03: Completar el ciclo de reinscripción

**What to build:** completar el recorrido para que una inscripción pueda pasar varias veces entre vigente y cancelada sin romper las reglas existentes ni mostrar información vieja.

**Blocked by:** 01: Reinscribirse desde el detalle.

**Status:** ready-for-agent

- [ ] El alumno puede cancelar y reinscribirse más de una vez mientras cumpla las reglas de cada acción.
- [ ] Una reinscripción dentro de las últimas 24 horas no permite cancelar fuera de la ventana.
- [ ] Siempre se conserva la fecha de la primera inscripción.
- [ ] Si vuelve a cancelar, solo queda guardada la cancelación más reciente.
- [ ] Los textos de cancelación dejan de afirmar que nunca será posible reinscribirse.
- [ ] Docentes y administración ven el estado actual, la fecha original y ninguna cancelación anterior después de reinscribir.
- [ ] La administración sigue siendo de solo lectura.
- [ ] `seed_demo` conserva una inscripción cancelada y nunca la reactiva por su cuenta.
- [ ] La documentación de uso explica la reinscripción y deja de describirla como bloqueada.
- [ ] La suite completa queda verde y el número de pruebas documentado se actualiza.
