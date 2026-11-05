# 04: Proteger reinscripciones simultáneas

**What to build:** asegurar que la reinscripción siga siendo correcta cuando llegan varias solicitudes al mismo tiempo, especialmente cuando queda un solo cupo.

**Blocked by:** 01: Reinscribirse desde el detalle.

**Status:** ready-for-agent

- [ ] Dos reinscripciones simultáneas del mismo alumno producen un éxito y un resultado de inscripción ya vigente.
- [ ] Después de esos intentos sigue existiendo una sola inscripción para el alumno y la actividad.
- [ ] Si una reinscripción compite con otra inscripción por el último cupo, solo una tiene éxito.
- [ ] La cantidad de inscripciones vigentes nunca supera la capacidad.
- [ ] Si la base está ocupada, la inscripción permanece cancelada y se puede reintentar.
- [ ] Ningún resultado deja cambios parciales.
- [ ] Las pruebas usan conexiones reales y siguen el patrón de concurrencia que ya tiene el proyecto.
- [ ] La suite completa queda verde.
