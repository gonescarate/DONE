# DONE — Arquitectura del sistema

**Versión:** 1.0  
**Estado:** Arquitectura propuesta, pendiente de validación

## 1. Objetivo

Definir la estructura técnica de DONE para desarrollar una aplicación web segura, modular y ampliable, priorizando la rapidez de desarrollo y un presupuesto inicial de 0 €/mes.

## 2. Arquitectura general

DONE utilizará inicialmente una arquitectura monolítica modular.

Esto significa que la interfaz web y las APIs del backend pertenecerán a un mismo proyecto, aunque sus responsabilidades estarán separadas.

El sistema estará organizado en:

- Frontend: interfaz y navegación.
- Backend: lógica de negocio y APIs.
- Base de datos: persistencia de información.
- Módulo de IA: interpretación y planificación de solicitudes.
- Módulo de automatización: ejecución supervisada de gestiones.
- Módulo de integraciones: comunicación con servicios externos.

## 3. Tecnologías propuestas

- Next.js y React para la aplicación web.
- TypeScript como lenguaje principal.
- Node.js para la ejecución del backend.
- PostgreSQL como sistema gestor de bases de datos.
- Prisma como herramienta de acceso a datos.
- Auth.js como candidato para la autenticación.

Las tecnologías definitivas se validarán mediante una prueba técnica inicial.

## 4. Organización del código

El proyecto separará la interfaz, la lógica de negocio, el acceso a datos y los servicios externos.

Los módulos principales previstos son:

- Usuarios y autenticación.
- Tareas y calendario.
- Chat e inteligencia artificial.
- Automatizaciones.
- Correos electrónicos.
- Suscripciones.
- Reservas.
- Notificaciones.
- Seguridad y auditoría.

No será necesario implementar todos los módulos desde el primer día.

## 5. Base de datos

Se utilizará PostgreSQL.

La estructura inicial contemplará usuarios, tareas, preferencias, conexiones externas y registros de operaciones.

Las tablas y sus relaciones se definirán en el documento `04-base-de-datos.md`.

## 6. Inteligencia artificial

La IA interpretará solicitudes y propondrá planes de ejecución.

El backend comprobará los permisos y solicitará confirmación antes de ejecutar acciones.

La IA no accederá directamente a la base de datos ni ejecutará operaciones externas sin pasar por los controles del backend.

Se compararán modelos locales y APIs externas antes de elegir el proveedor.

## 7. Integraciones

Las conexiones con correo, calendarios, reservas y otros servicios se realizarán mediante módulos independientes.

Se priorizarán APIs oficiales y sistemas de autorización como OAuth cuando corresponda.

Las integraciones deberán permitir revocar conexiones y gestionar fallos.

## 8. Seguridad

- Autenticación mediante correo y contraseña o Google.
- Control de acceso a los datos de cada usuario.
- Confirmación previa a cualquier acción automatizada.
- Protección de credenciales y tokens.
- Comunicación cifrada mediante HTTPS en producción.
- Registro de operaciones y errores.
- Separación entre desarrollo y producción.
- Copias de seguridad diarias.

Los mecanismos concretos se detallarán en el documento de seguridad.

## 9. Infraestructura

Durante el desarrollo se utilizarán herramientas locales y servicios gratuitos cuando sea posible.

El alojamiento de producción queda pendiente de selección.

Se evaluarán los costes, límites gratuitos, condiciones comerciales, seguridad y disponibilidad antes de contratar o utilizar servicios externos.

## 10. Control de versiones

El código y la documentación estarán alojados en GitHub.

Cada funcionalidad se desarrollará en una rama independiente y se integrará en `main` mediante pull request.

Se utilizará GitHub Projects para organizar las tareas del equipo.

## 11. Pruebas

Se combinarán pruebas automáticas y manuales.

Antes de aprobar una funcionalidad se comprobarán su funcionamiento, seguridad y tratamiento de errores.

Las automatizaciones se probarán inicialmente con servicios simulados o entornos de prueba antes de realizar acciones reales.

## 12. Evolución

La arquitectura deberá facilitar nuevas integraciones y funcionalidades.

Si el crecimiento de DONE lo requiere, podrán separarse procesos de automatización o servicios independientes sin necesidad de rehacer toda la aplicación.
