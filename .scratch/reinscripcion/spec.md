# Reinscribirse después de cancelar

Status: ready-for-agent

## Problem Statement

Hoy, cuando un alumno cancela una inscripción, no puede volver a esa actividad. Esto pasa incluso si cambia de opinión, la actividad todavía no empezó y hay cupo. El sistema muestra la cancelación, pero bloquea cualquier nuevo intento.

## Solution

El alumno podrá reinscribirse desde el detalle de la actividad o desde "Mis inscripciones". Para hacerlo, la actividad debe estar habilitada, no haber comenzado y tener cupo. Se vuelve a usar la misma inscripción: conserva su fecha original, deja de estar cancelada y vuelve a ocupar un cupo.

## User Stories

1. Como alumno, quiero reinscribirme en una actividad que cancelé, para poder volver si cambio de opinión.
2. Como alumno, quiero reinscribirme desde el detalle de la actividad, para hacerlo mientras reviso su información.
3. Como alumno, quiero reinscribirme desde "Mis inscripciones", para no tener que buscar la actividad otra vez.
4. Como alumno, quiero ver el botón "Reinscribirme" solo cuando la acción sea posible, para no intentar algo que será rechazado.
5. Como alumno, quiero saber si no puedo reinscribirme porque la actividad está deshabilitada.
6. Como alumno, quiero saber si no puedo reinscribirme porque la actividad ya comenzó.
7. Como alumno, quiero saber si no puedo reinscribirme porque no quedan cupos.
8. Como alumno, quiero poder reinscribirme dentro de las últimas 24 horas, porque ese límite solo corresponde a la cancelación.
9. Como alumno, quiero recibir el mensaje "Reinscripción confirmada", para saber que la operación salió bien.
10. Como alumno, quiero volver a la pantalla desde la que pedí la reinscripción, para no perder el contexto.
11. Como alumno, quiero que se mantenga una sola inscripción por actividad, para que no haya registros duplicados.
12. Como alumno, quiero conservar la fecha de mi primera inscripción.
13. Como alumno, quiero que la cancelación anterior desaparezca al reinscribirme, porque las pantallas muestran mi estado actual.
14. Como alumno, quiero poder cancelar y reinscribirme más de una vez si sigo cumpliendo las reglas.
15. Como alumno, quiero que una inscripción hecha dentro de las últimas 24 horas siga respetando el límite para cancelar.
16. Como alumno, quiero que la reinscripción se haga con mi sesión y mediante una acción explícita, para que nadie pueda hacerlo por mí.
17. Como alumno, quiero que dos intentos simultáneos no creen dos inscripciones.
18. Como alumno, quiero que el último cupo se asigne a una sola persona, aunque haya pedidos al mismo tiempo.
19. Como alumno, quiero que un error temporal de la base no deje mi inscripción a medias.
20. Como alumno, quiero seguir viendo la fecha de cancelación mientras mi inscripción continúe cancelada.
21. Como docente, quiero que una reinscripción vuelva a ocupar un cupo de inmediato.
22. Como docente, quiero ver una inscripción reinscripta como vigente y con su fecha original.
23. Como docente, quiero que la administración siga siendo de solo lectura.
24. Como docente, quiero que `seed_demo` respete las cancelaciones existentes y no reinscriba alumnos por su cuenta.
25. Como docente, quiero que el catálogo siga mostrando la disponibilidad general sin agregar acciones personales.

## Implementation Decisions

- Se reactiva la misma inscripción cancelada. No se crea otra fila.
- Al reinscribirse se elimina la cancelación anterior, pero se conserva la fecha original de inscripción.
- No se agregan campos, tablas ni migraciones.
- La actividad debe estar habilitada, no haber comenzado y tener cupo.
- Si hay más de un motivo de rechazo, se informa en este orden: deshabilitada, iniciada y sin cupo.
- La ventana de 24 horas solo se usa para cancelar. No limita la reinscripción.
- El alumno puede repetir el ciclo de cancelar y reinscribirse mientras cumpla las reglas de cada acción.
- El servicio de inscripción también se encarga de la reinscripción y devuelve un resultado propio cuando sale bien.
- La operación mantiene la transacción actual. Si la base está ocupada, no debe quedar ningún cambio a medias.
- Dos reinscripciones simultáneas del mismo alumno dejan una sola inscripción vigente.
- Si dos alumnos compiten por el último cupo, solo uno lo obtiene.
- La acción usa `POST`, CSRF y la identidad de la sesión. Un `GET` nunca cambia el estado.
- Después de actuar, se vuelve al detalle o a "Mis inscripciones", según desde dónde se inició.
- El detalle y "Mis inscripciones" muestran el botón cuando se puede usar y el motivo cuando no se puede.
- Los textos de cancelación dejan de decir que el alumno nunca podrá reinscribirse.
- El catálogo no tendrá un botón de reinscripción.
- Docentes y administración ven solamente el estado actual y la fecha original.
- `seed_demo` conserva las inscripciones canceladas y no las reactiva.
- El README se actualiza para explicar el nuevo comportamiento.

## Testing Decisions

- Las pruebas revisan resultados visibles: estado de la inscripción, cupos, mensajes, redirecciones y contenido de las páginas.
- **Servicio**: cubre la reinscripción exitosa, las reglas de rechazo, la fecha original, los ciclos y los errores de base.
- **HTTP**: cubre los botones y mensajes del detalle y "Mis inscripciones", además de sesión, CSRF, `POST`, privacidad y redirecciones.
- **Concurrencia**: cubre dos reinscripciones del mismo alumno y la competencia por el último cupo usando conexiones reales.
- También se verifica que `seed_demo` no cambie una inscripción cancelada y que docente y administración vean el estado actual.
- Se reutilizan las pruebas y puntos de entrada que ya existen. No se agregan mocks para detalles internos.

## Out of Scope

- Crear una inscripción nueva para cada reinscripción.
- Guardar el historial completo de cancelaciones y reinscripciones.
- Guardar una fecha separada de reinscripción.
- Agregar campos, tablas o migraciones.
- Cambiar la ventana de cancelación.
- Permitir que un docente o administrador reinscriba a un alumno.
- Agregar el botón al catálogo.
- Incorporar lista de espera, notificaciones o correos.
- Cambiar las reglas generales de cupo, habilitación o inicio.

## Further Notes

- El vocabulario acordado está en `GLOSSARY.md`.
- La decisión de reutilizar la misma inscripción está en la ADR 0002.
- La especificación anterior de cancelación muestra el comportamiento viejo. Sus pruebas de bloqueo deben reemplazarse por las nuevas reglas.
- El número de pruebas indicado en el README ya no coincide con la suite actual y debe actualizarse.
