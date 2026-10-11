# DONE — Especificación de requisitos

**Versión:** 1.0  
**Estado:** Documento inicial  
**Equipo:** 2 desarrolladores

## 1. Objetivo

Este documento define los requisitos funcionales y no funcionales de DONE, una aplicación web con inteligencia artificial que permite organizar tareas y ejecutar gestiones cotidianas con autorización del usuario.

Los requisitos están organizados por fases para permitir un desarrollo progresivo.

## 2. Requisitos funcionales

### Fase 1 — Usuarios y gestión de tareas

**RF-01. Registro de usuarios**  
El sistema permitirá crear cuentas mediante correo electrónico y contraseña o mediante Google.

**RF-02. Autenticación**  
Los usuarios podrán iniciar sesión, cerrar sesión y recuperar el acceso a sus cuentas.

**RF-03. Gestión de perfiles**  
Cada usuario podrá consultar y modificar sus datos personales y preferencias.

**RF-04. Gestión de tareas**  
Los usuarios podrán crear, consultar, modificar y eliminar tareas pendientes.

**RF-05. Organización de tareas**  
El sistema permitirá asignar categorías, fechas límite, prioridades y estados a las tareas.

**RF-06. Panel principal**  
DONE dispondrá de un panel que muestre las tareas, gestiones pendientes y accesos a sus funcionalidades principales.

**RF-07. Calendario propio**  
La aplicación incluirá un calendario para visualizar y organizar eventos, tareas y recordatorios.

### Fase 2 — Inteligencia artificial

**RF-08. Chat con IA**  
Los usuarios podrán interactuar con DONE mediante lenguaje natural.

**RF-09. Interpretación de solicitudes**  
La IA identificará la intención del usuario y propondrá las acciones necesarias.

**RF-10. Planificación de gestiones**  
DONE podrá dividir solicitudes complejas en pasos individuales.

**RF-11. Confirmación de acciones**  
El sistema solicitará autorización explícita antes de ejecutar cualquier acción en nombre del usuario.

**RF-12. Gestión de incertidumbre**  
Cuando la IA no pueda determinar cómo continuar, explicará el problema, propondrá alternativas y solicitará una decisión.

**RF-13. Historial de operaciones**  
Se registrarán las operaciones realizadas por la IA y sus resultados.

### Fase 3 — Integraciones y automatización

**RF-14. Conexión con servicios externos**  
Los usuarios podrán conectar servicios compatibles mediante sistemas de autorización seguros.

**RF-15. Información manual**  
DONE permitirá introducir información manualmente cuando no exista una integración disponible.

**RF-16. Gestión de correo electrónico**  
DONE podrá leer y resumir correos autorizados, redactar respuestas, detectar tareas pendientes y enviar, archivar o eliminar mensajes previa confirmación.

**RF-17. Sincronización de calendarios**  
Los usuarios podrán conectar calendarios externos para consultar disponibilidad y sincronizar eventos.

**RF-18. Gestión de suscripciones**  
El usuario podrá introducir suscripciones manualmente o permitir que DONE las identifique mediante correos autorizados.

**RF-19. Cancelación de suscripciones**  
DONE intentará ejecutar cancelaciones automáticamente tras recibir confirmación, cuando el servicio correspondiente lo permita.

**RF-20. Búsqueda de reservas**  
El sistema permitirá buscar y comparar restaurantes, actividades y otros servicios compatibles.

**RF-21. Ejecución de reservas**  
DONE podrá realizar reservas tras recibir autorización explícita del usuario y comprobar que el servicio admite esa operación.

**RF-22. Organización de planes**  
DONE propondrá fechas y horarios, consultará calendarios autorizados y ayudará a seleccionar lugares y actividades.

### Fase 4 — Personalización y seguimiento

**RF-23. Notificaciones configurables**  
Cada usuario podrá elegir entre los canales de notificación disponibles.

**RF-24. Preferencias personales**  
DONE almacenará las preferencias que el usuario decida proporcionar.

**RF-25. Seguimiento de gestiones**  
El sistema permitirá consultar las gestiones pendientes, completadas, fallidas y aquellas que requieran intervención.

**RF-26. Gestión de errores**  
Cuando una operación falle, DONE utilizará reintentos seguros cuando corresponda, informará del problema y ofrecerá alternativas.

**RF-27. Eliminación de cuentas**  
El usuario podrá solicitar la eliminación de su cuenta. Se contempla un periodo de recuperación de hasta 30 días, sujeto al cumplimiento de la normativa de protección de datos.

**RF-28. Suscripción mensual**  
El sistema contemplará un modelo de suscripción mensual, cuyas condiciones y sistema de cobro se definirán antes del lanzamiento comercial.

## 3. Requisitos no funcionales

**RNF-01. Compatibilidad**  
DONE funcionará como aplicación web responsive en navegadores modernos de ordenador y móvil.

**RNF-02. Seguridad de autenticación**  
Las contraseñas se almacenarán mediante algoritmos seguros de hash. Se protegerán las sesiones y los accesos a la aplicación.

**RNF-03. Protección de datos**  
La aplicación protegerá la información personal y cumplirá las obligaciones legales aplicables.

**RNF-04. Autorización**  
Cada usuario accederá únicamente a sus datos y a las operaciones para las que tenga permisos.

**RNF-05. Seguridad de integraciones**  
Las credenciales y los tokens de acceso a servicios externos estarán protegidos y no se expondrán al frontend ni a otros usuarios.

**RNF-06. Trazabilidad**  
El sistema registrará los errores técnicos y las operaciones de la IA sin almacenar información sensible innecesaria.

**RNF-07. Copias de seguridad**  
Se realizarán copias de seguridad automáticas diariamente. También deberá verificarse que los datos pueden restaurarse.

**RNF-08. Mantenibilidad**  
El código estará organizado en componentes y módulos que faciliten su modificación y ampliación.

**RNF-09. Escalabilidad**  
La arquitectura permitirá incorporar nuevas funcionalidades e integraciones sin rediseñar completamente el sistema.

**RNF-10. Experiencia de usuario**  
La interfaz será sencilla, comprensible y adaptada a dispositivos móviles y ordenadores.

**RNF-11. Gestión de fallos**  
Las operaciones fallidas no se marcarán como completadas. Se evitará repetir acciones que puedan provocar reservas, cancelaciones o envíos duplicados.

**RNF-12. Entornos separados**  
Existirán entornos diferenciados de desarrollo y producción, con configuraciones y datos independientes.

**RNF-13. Calidad del software**  
Cada funcionalidad deberá superar pruebas manuales y automáticas antes de aprobarse.

**RNF-14. Control de versiones**  
El desarrollo utilizará GitHub, ramas por funcionalidad y pull requests revisadas antes de integrar cambios en `main`.

**RNF-15. Presupuesto inicial**  
Durante las primeras etapas se priorizarán tecnologías y servicios gratuitos, manteniendo un presupuesto operativo objetivo de 0 €/mes.

## 4. Priorización del desarrollo

**Prioridad 1 — Base del sistema**
- Usuarios y autenticación.
- Gestión de tareas.
- Panel principal.
- Base de datos.
- Seguridad básica.
- Pruebas.

**Prioridad 2 — Primera IA funcional**
- Chat con IA.
- Interpretación de solicitudes.
- Planificación de acciones.
- Confirmación del usuario.
- Historial de operaciones.

**Prioridad 3 — Automatización**
- Conexión con servicios externos.
- Correo electrónico.
- Calendarios.
- Suscripciones.
- Reservas y organización de planes.

**Prioridad 4 — Ampliación**
- Personalización.
- Notificaciones avanzadas.
- Optimización de automatizaciones.
- Suscripción y preparación comercial.

## 5. Criterios generales de aceptación

Un requisito se considerará terminado cuando:

1. La funcionalidad esté implementada.
2. Haya superado las pruebas manuales y automáticas correspondientes.
3. No presente errores críticos conocidos.
4. Respete las medidas de seguridad definidas.
5. Se haya revisado e integrado mediante pull request.
6. Su documentación esté actualizada.

## 6. Consideraciones finales

Los requisitos representan las funcionalidades previstas para DONE, no necesariamente todas las que estarán terminadas en la primera entrega.

La primera versión deberá demostrar que la aplicación puede organizar tareas, utilizar inteligencia artificial y completar al menos una gestión real con autorización del usuario.

Las decisiones técnicas pendientes, especialmente los servicios de IA, alojamiento e integraciones, se resolverán en el documento de arquitectura.
