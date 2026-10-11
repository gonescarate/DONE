# DONE — Plan de seguridad y privacidad

**Versión:** 1.0  
**Estado:** Diseño inicial  
**Proyecto:** DONE  
**Equipo:** 2 desarrolladores

## 1. Objetivo

Establecer las medidas de seguridad necesarias para proteger los usuarios, los datos personales y las operaciones realizadas por DONE mediante inteligencia artificial.

La seguridad deberá estar presente desde las primeras fases del desarrollo.

## 2. Autenticación de usuarios

DONE permitirá iniciar sesión mediante:

- Correo electrónico y contraseña.
- Cuenta de Google.

**Medidas de seguridad:**
- Las contraseñas nunca se almacenarán en texto plano.
- Se utilizará un algoritmo seguro de hash de contraseñas, como Argon2id.
- Las sesiones tendrán mecanismos de expiración e invalidación.
- Se limitarán los intentos de inicio de sesión para reducir ataques automatizados.
- La recuperación de contraseñas utilizará enlaces temporales de un solo uso.

Para el inicio de sesión con Google se utilizará OpenID Connect.

## 3. Autorización y control de acceso

Cada usuario podrá acceder únicamente a sus propios datos.

El backend comprobará la identidad y los permisos en cada operación protegida.

No será suficiente ocultar información desde la interfaz.

**Ejemplo:** un usuario no podrá consultar las tareas de otro modificando el identificador de una petición.

## 4. Seguridad de la base de datos

PostgreSQL almacenará la información de forma estructurada y protegida.

Se aplicarán las siguientes medidas:

- Acceso mediante usuarios de base de datos con permisos limitados.
- Credenciales almacenadas fuera del código fuente.
- Consultas parametrizadas mediante el sistema de acceso a datos.
- Conexiones cifradas cuando corresponda.
- Separación entre bases de datos de desarrollo y producción.
- Restricciones de integridad y control de acceso desde el backend.

La base de datos de producción no será accesible públicamente sin controles de seguridad apropiados.

## 5. Seguridad de las operaciones de IA

DONE podrá interpretar solicitudes, proponer soluciones y preparar acciones.

Sin embargo, el modelo de IA no tendrá autorización directa para ejecutar operaciones sensibles.

**Flujo obligatorio:**

1. El usuario solicita una gestión.
2. La IA interpreta la solicitud.
3. El backend prepara y valida la operación.
4. DONE muestra al usuario la acción exacta que se realizará.
5. El usuario confirma expresamente.
6. El backend vuelve a comprobar permisos y condiciones.
7. Se ejecuta la operación autorizada.
8. Se registra el resultado.

Las confirmaciones deberán identificar la acción, su destinatario y los parámetros importantes.

Una confirmación no autorizará operaciones distintas de las mostradas.

## 6. Seguridad frente a instrucciones maliciosas

Los correos electrónicos, documentos y páginas externas se considerarán información no confiable.

DONE no deberá obedecer instrucciones encontradas dentro de estos contenidos que pretendan modificar sus permisos o provocar acciones no solicitadas.

La IA solo podrá utilizar herramientas autorizadas por el backend.

Las acciones externas deberán validarse independientemente de la respuesta del modelo.

## 7. Integraciones con servicios externos

Las conexiones con Gmail, Google Calendar y otros servicios utilizarán los mecanismos oficiales de autorización disponibles.

Se solicitarán únicamente los permisos necesarios para cada funcionalidad.

Los usuarios podrán:

- Consultar sus conexiones activas.
- Desconectar servicios.
- Revocar permisos.
- Volver a autorizar una conexión cuando sea necesario.

Los tokens de acceso se almacenarán cifrados cuando deban conservarse y nunca se mostrarán directamente en el navegador.

## 8. Protección de datos personales

DONE recopilará únicamente la información necesaria para prestar sus servicios.

Se deberán establecer:

- Política de privacidad.
- Finalidades y bases jurídicas de los tratamientos.
- Plazos de conservación.
- Procedimientos para ejercer derechos de protección de datos.
- Medidas de seguridad y respuesta ante incidentes.
- Evaluación de proveedores que traten datos personales.

El sistema deberá permitir gestionar solicitudes de acceso, rectificación, supresión y portabilidad cuando proceda.

## 9. Eliminación de cuentas

Se ha establecido como objetivo ofrecer un periodo de recuperación de hasta 30 días.

Este periodo no impedirá atender las solicitudes de supresión conforme a los plazos y obligaciones legales aplicables.

Se definirán procedimientos para:

- Desactivar cuentas.
- Revocar conexiones externas.
- Eliminar los datos cuando corresponda.
- Tratar la información conservada en copias de seguridad.
- Mantener únicamente la información cuya conservación esté justificada legalmente.

## 10. Copias de seguridad

DONE realizará copias de seguridad automáticas diariamente.

Las copias deberán:

- Almacenarse fuera del repositorio GitHub.
- Estar protegidas contra accesos no autorizados.
- Contar con medidas de cifrado adecuadas.
- Poder restaurarse mediante un procedimiento documentado.

Se realizarán pruebas periódicas de restauración.

## 11. Registro de errores y operaciones

Se almacenarán registros técnicos y de operaciones de la IA para facilitar la investigación de incidencias.

Estos registros incluirán información como:

- Identificador de operación.
- Usuario responsable.
- Tipo de acción.
- Fecha y estado.
- Resultado o código de error.

No deberán registrar contraseñas, tokens, mensajes privados completos u otros datos sensibles sin una necesidad justificada.

## 12. Seguridad durante el desarrollo

El equipo utilizará GitHub con ramas por funcionalidad y pull requests.

Normas principales:

- No subir archivos `.env` con secretos.
- Utilizar `.gitignore`.
- Revisar dependencias y vulnerabilidades.
- Separar desarrollo y producción.
- No utilizar datos reales de usuarios para pruebas sin justificación y protección.
- Mantener los permisos del repositorio limitados.
- Activar autenticación multifactor en las cuentas administrativas.

## 13. Pruebas de seguridad

Antes de publicar una funcionalidad, se comprobará:

- Que un usuario no pueda acceder a datos ajenos.
- Que las sesiones puedan cerrarse correctamente.
- Que las operaciones requieran confirmación válida.
- Que los permisos externos puedan revocarse.
- Que no se expongan credenciales.
- Que los errores no revelen información confidencial.
- Que las automatizaciones no repitan operaciones sensibles accidentalmente.

## 14. Incidentes de seguridad

Se establecerá un procedimiento para detectar, registrar y responder a incidentes.

El procedimiento contemplará:

1. Identificación del incidente.
2. Contención del problema.
3. Análisis del impacto.
4. Corrección.
5. Recuperación.
6. Documentación y notificaciones legales cuando sean necesarias.

## 15. Referencias técnicas

- OWASP Application Security Verification Standard (ASVS).
- OWASP Top 10 for Large Language Model Applications.
- Reglamento General de Protección de Datos (RGPD).
- Agencia Española de Protección de Datos (AEPD).

## 16. Evolución del documento

Este documento define las medidas previstas, no certifica que ya estén implementadas.

Cada control se implementará y comprobará durante el desarrollo. El documento deberá actualizarse cuando se seleccionen las herramientas de autenticación, proveedores de IA e infraestructura de producción.
