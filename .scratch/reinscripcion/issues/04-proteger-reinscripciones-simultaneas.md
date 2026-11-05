# 04: Proteger reinscripciones simultáneas

**What to build:** asegurar que la reinscripción siga siendo correcta cuando llegan varias solicitudes al mismo tiempo, especialmente cuando queda un solo cupo.

**Blocked by:** 01: Reinscribirse desde el detalle.

**Status:** ready-for-agent

- [x] Dos reinscripciones simultáneas del mismo alumno producen un éxito y un resultado de inscripción ya vigente.
- [x] Después de esos intentos sigue existiendo una sola inscripción para el alumno y la actividad.
- [x] Si una reinscripción compite con otra inscripción por el último cupo, solo una tiene éxito.
- [x] La cantidad de inscripciones vigentes nunca supera la capacidad.
- [x] Si la base está ocupada, la inscripción permanece cancelada y se puede reintentar.
- [x] Ningún resultado deja cambios parciales.
- [x] Las pruebas usan conexiones reales y siguen el patrón de concurrencia que ya tiene el proyecto.
- [x] La suite completa queda verde.

## Comments

- Se agregaron tres pruebas con conexiones SQLite reales: dos reinscripciones del mismo alumno, competencia por el último cupo y bloqueo recuperable con reintento. Las revisiones de especificación y estándares no encontraron faltantes ni violaciones. Verificación final: 74 pruebas verdes y sin migraciones nuevas.
