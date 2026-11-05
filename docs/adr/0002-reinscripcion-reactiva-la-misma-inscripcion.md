---
status: accepted
---

# La reinscripción reactiva la misma inscripción

Cuando un alumno se reinscribe, usamos la misma inscripción que había cancelado. Si la actividad sigue habilitada, todavía no empezó y tiene cupo, la inscripción vuelve a estar vigente. La cancelación anterior se borra porque solo nos interesa el estado actual. Así mantenemos una sola inscripción por alumno y actividad y no necesitamos agregar un historial.

## Considered Options

- **Reactivar la misma inscripción** (elegida): es la opción más simple y mantiene la regla de una inscripción por alumno y actividad, aunque se pierda el historial anterior.
- **Crear una inscripción nueva**: guarda cada ciclo, pero obliga a cambiar la unicidad, los conteos y varias pantallas.
- **Agregar un historial separado**: permite guardar todo, pero agrega complejidad que esta tarea no necesita.

## Consequences

- El alumno puede cancelar y reinscribirse más de una vez si sigue cumpliendo las reglas.
- Se conserva la fecha de la primera inscripción y no se guarda una fecha especial de reinscripción.
- Si vuelve a cancelar, solo queda guardada la cancelación más reciente.
- `seed_demo` respeta las cancelaciones y nunca reinscribe automáticamente.
- No se agregan campos, tablas ni migraciones.
- Las pantallas muestran el estado actual. Una inscripción reinscripta aparece vigente, con su fecha original y sin el historial anterior.
