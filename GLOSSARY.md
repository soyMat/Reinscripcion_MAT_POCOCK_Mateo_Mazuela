# Inscripciones UNTDF

Dominio de la demo docente: alumnos que reservan cupos en actividades y docentes que las habilitan.

## Language

**Actividad**:
Un encuentro ofrecido a la comunidad universitaria, con fecha de inicio, capacidad y estado de habilitación.
_Avoid_: Evento, curso, clase

**Inscripción**:
Relación única entre un alumno y una actividad. Puede estar vigente o cancelada; al reinscribirse, vuelve a estar vigente.
_Avoid_: Registro, reserva, alta

**Inscripción vigente**:
Inscripción que ocupa un cupo en la actividad y no está cancelada.
_Avoid_: Inscripción activa, reserva vigente

**Cancelación**:
Decisión del alumno de renunciar a su inscripción dentro de la ventana de cancelación. La inscripción deja de ocupar cupo y conserva el instante de la decisión mientras permanezca cancelada.
_Avoid_: Baja, anulación, borrado, desinscripción

**Reinscripción**:
Decisión del alumno de volver a una actividad que había cancelado. La misma inscripción vuelve a estar vigente y ocupa un cupo.
_Avoid_: Nueva inscripción, reactivación, segunda inscripción

**Ventana de cancelación**:
Período en el que el alumno puede cancelar: desde que se inscribe hasta 24 horas antes del inicio de la actividad.
_Avoid_: Plazo de baja, fecha límite

**Cupo disponible**:
Cantidad de lugares que una actividad todavía puede ofrecer: su capacidad menos las inscripciones vigentes.
_Avoid_: Vacante, lugar, disponibilidad (como sinónimo de cantidad)

**Alumno**:
Persona autenticada que se inscribe y cancela sus propias inscripciones.
_Avoid_: Estudiante, usuario

**Docente**:
Persona con acceso a la administración; habilita actividades y consulta inscripciones, pero no inscribe ni cancela por otros.
_Avoid_: Profesor, administrador
