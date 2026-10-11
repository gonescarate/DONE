# DONE — Plan de desarrollo y pruebas

**Versión:** 1.0  
**Estado:** Planificación inicial  
**Equipo:** 2 desarrolladores  
**Herramienta de gestión:** GitHub Projects

## 1. Objetivo

Establecer una metodología para desarrollar DONE progresivamente, organizar el trabajo entre los dos desarrolladores y garantizar que cada funcionalidad se comprueba antes de incorporarla a la aplicación.

## 2. Metodología de desarrollo

Utilizaremos una metodología ágil basada en tareas pequeñas.

Cada funcionalidad se dividirá en actividades concretas que puedan desarrollarse, revisarse y probarse individualmente.

Ambos desarrolladores participarán en las distintas áreas del proyecto, repartiendo responsabilidades según las tareas pendientes.

## 3. Organización mediante GitHub Projects

El tablero incluirá los siguientes estados:

- **Backlog:** funcionalidades previstas que todavía no se han planificado.
- **To Do:** tareas preparadas para comenzar.
- **In Progress:** tareas que se están desarrollando.
- **In Review:** tareas terminadas pendientes de revisión.
- **Done:** tareas completadas, probadas y aprobadas.

Cada tarea deberá contener:

- Título descriptivo.
- Objetivo.
- Descripción de lo que debe desarrollarse.
- Responsable.
- Prioridad.
- Requisitos relacionados.
- Criterios de aceptación.

## 4. Fases del desarrollo

### Fase 1 — Preparación técnica

Objetivo: disponer de un entorno de desarrollo funcional.

Actividades:
1. Preparar el repositorio.
2. Instalar las herramientas necesarias.
3. Crear el proyecto web.
4. Configurar el backend.
5. Configurar PostgreSQL.
6. Preparar las variables de entorno.
7. Comprobar la conexión entre aplicación y base de datos.

**Resultado:** aplicación inicial funcionando localmente.

### Fase 2 — Usuarios y tareas

Objetivo: construir la base funcional de DONE.

Actividades:
1. Implementar registro e inicio de sesión.
2. Crear la gestión de perfiles.
3. Implementar tareas.
4. Añadir categorías, prioridades y estados.
5. Desarrollar el panel principal.
6. Proteger las rutas privadas.

**Resultado:** aplicación donde cada usuario puede gestionar sus propias tareas.

### Fase 3 — Inteligencia artificial

Objetivo: incorporar un asistente capaz de comprender solicitudes.

Actividades:
1. Evaluar modelos de IA.
2. Crear el chat.
3. Conectar la IA con el backend.
4. Interpretar solicitudes.
5. Generar propuestas de acciones.
6. Implementar las confirmaciones.
7. Registrar las operaciones.

**Resultado:** asistente capaz de interpretar solicitudes y preparar gestiones.

### Fase 4 — Primera automatización

Objetivo: demostrar que DONE puede ejecutar una gestión real.

Actividades:
1. Seleccionar una gestión concreta.
2. Estudiar la integración correspondiente.
3. Implementar la conexión autorizada.
4. Preparar el flujo de ejecución.
5. Solicitar confirmación.
6. Ejecutar la operación.
7. Gestionar errores y registrar resultados.

**Resultado:** primera gestión automatizada completada con autorización del usuario.

### Fase 5 — Ampliación

Objetivo: incorporar progresivamente otras funcionalidades.

Actividades previstas:
- Gestión de correos.
- Calendario.
- Suscripciones.
- Reservas.
- Organización de planes.
- Notificaciones configurables.

Cada integración se desarrollará y probará individualmente.

### Fase 6 — Preparación de producción

Objetivo: disponer de una versión estable para pruebas controladas.

Actividades:
1. Revisar la seguridad.
2. Ejecutar pruebas completas.
3. Configurar el alojamiento seleccionado.
4. Preparar las copias de seguridad.
5. Configurar los registros de errores.
6. Desplegar la aplicación.
7. Comprobar el funcionamiento en móvil y ordenador.

**Resultado:** versión preparada para pruebas entre los dos desarrolladores.

## 5. Organización de Git

Se utilizarán ramas independientes por funcionalidad.

Ejemplos:

- `feature/authentication`
- `feature/tasks`
- `feature/dashboard`
- `feature/ai-chat`
- `fix/login-validation`

El procedimiento será:

1. Crear una rama desde `main`.
2. Desarrollar una funcionalidad.
3. Ejecutar las pruebas correspondientes.
4. Crear un pull request.
5. Revisar los cambios.
6. Integrarlos en `main` cuando estén aprobados.

Se evitarán los cambios directos sobre `main` durante el desarrollo habitual.

## 6. Tipos de pruebas

### 6.1. Pruebas unitarias

Comprobarán funciones individuales.

Ejemplo: verificar que una tarea no pueda crearse sin título.

### 6.2. Pruebas de integración

Comprobarán la comunicación entre componentes.

Ejemplo: verificar que el backend guarda correctamente una tarea en PostgreSQL.

### 6.3. Pruebas funcionales

Comprobarán que las funcionalidades cumplen los requisitos establecidos.

Ejemplo: crear, modificar y completar una tarea desde la interfaz.

### 6.4. Pruebas de seguridad

Comprobarán la autenticación, autorización y protección de los datos.

Ejemplo: impedir que un usuario consulte las tareas pertenecientes a otra cuenta.

### 6.5. Pruebas de automatización

Comprobarán que las operaciones de IA respetan las confirmaciones y gestionan correctamente los errores.

Inicialmente se utilizarán servicios simulados para evitar acciones externas accidentales.

### 6.6. Pruebas de interfaz

Comprobarán el funcionamiento en diferentes tamaños de pantalla y navegadores.

También se revisarán la accesibilidad y los mensajes de error.

## 7. Herramientas de pruebas

Se evaluarán herramientas compatibles con la arquitectura seleccionada.

Candidatas:

- Vitest para pruebas unitarias.
- React Testing Library para componentes.
- Playwright para pruebas de navegador.
- GitHub Actions para ejecutar comprobaciones automáticamente.

La selección definitiva se realizará durante la configuración técnica.

## 8. Criterios de aceptación

Una funcionalidad podrá considerarse terminada cuando:

1. Cumpla los requisitos definidos.
2. Supere las pruebas relevantes.
3. No presente errores críticos conocidos.
4. Respete las medidas de seguridad.
5. Haya sido revisada mediante pull request.
6. Se haya actualizado la documentación necesaria.
7. Funcione correctamente en el entorno correspondiente.

## 9. Gestión de errores

Los errores encontrados se registrarán como incidencias en GitHub.

Cada incidencia contendrá:

- Descripción del problema.
- Pasos para reproducirlo.
- Resultado esperado.
- Resultado obtenido.
- Prioridad.
- Responsable.
- Estado de resolución.

Los errores críticos de seguridad o integridad de datos deberán resolverse antes de publicar una versión afectada.

## 10. Control de calidad

Antes de integrar cambios en `main`, deberán ejecutarse las comprobaciones pertinentes.

Se recomienda automatizar progresivamente:

- Análisis estático del código.
- Comprobación de tipos.
- Pruebas unitarias.
- Pruebas de integración.
- Compilación de la aplicación.

## 11. Seguimiento del proyecto

GitHub Projects permitirá consultar:

- Funcionalidades pendientes.
- Trabajo asignado a cada desarrollador.
- Tareas bloqueadas.
- Errores detectados.
- Funcionalidades terminadas.

El equipo revisará periódicamente las prioridades y el progreso.

## 12. Mantenimiento

Una vez que DONE funcione en producción, será necesario:

- Actualizar dependencias.
- Corregir vulnerabilidades.
- Revisar errores.
- Comprobar las copias de seguridad.
- Evaluar el rendimiento.
- Mantener actualizada la documentación.

## 13. Evolución

Este plan podrá modificarse según los resultados de las pruebas y las necesidades del proyecto.

La prioridad será conseguir una primera versión funcional, segura y ampliable antes de incorporar numerosas automatizaciones.
