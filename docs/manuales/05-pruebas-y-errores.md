# DONE — Manual de pruebas y resolución de errores

**Versión:** 1.0  
**Estado:** Procedimiento inicial  
**Entorno:** Windows 11 en Oracle VirtualBox  
**Equipo:** 2 desarrolladores

## 1. Objetivo

Establecer los procedimientos para comprobar el correcto funcionamiento de DONE, detectar errores y resolver incidencias durante el desarrollo.

Ninguna funcionalidad deberá incorporarse a la rama principal sin superar las pruebas correspondientes.

## 2. Estrategia de pruebas

DONE combinará pruebas automáticas y manuales.

Las pruebas estarán organizadas en cinco categorías:

- Pruebas unitarias.
- Pruebas de integración.
- Pruebas funcionales.
- Pruebas de seguridad.
- Pruebas de inteligencia artificial y automatización.

Las herramientas y comandos definitivos se configurarán cuando se inicialice el código de la aplicación.

## 3. Pruebas unitarias

Permiten comprobar funciones individuales sin depender de otros componentes.

**Ejemplos:**

- Comprobar que una tarea no pueda crearse sin título.
- Validar el formato de un correo electrónico.
- Comprobar que se asigna correctamente la prioridad de una tarea.
- Verificar los cambios de estado permitidos.

**Herramienta propuesta:** Vitest.

Cada prueba deberá especificar:

1. Condiciones iniciales.
2. Datos de entrada.
3. Resultado esperado.
4. Resultado obtenido.

## 4. Pruebas de integración

Comprueban que diferentes componentes funcionan correctamente entre sí.

**Ejemplos:**

- Guardar una tarea desde el backend en PostgreSQL.
- Recuperar las tareas de un usuario.
- Comprobar la conexión con una API externa.
- Registrar una operación de IA.

Se utilizará una base de datos de pruebas independiente de los datos habituales de desarrollo.

## 5. Pruebas funcionales

Verifican que DONE cumple los requisitos especificados.

**Ejemplo: creación de tareas**

1. Iniciar sesión.
2. Abrir el panel de tareas.
3. Crear una tarea nueva.
4. Introducir título y fecha límite.
5. Guardarla.
6. Comprobar que aparece en el listado.
7. Cerrar y volver a abrir la aplicación.
8. Comprobar que la tarea sigue almacenada.

**Resultado esperado:** la tarea se guarda correctamente y pertenece al usuario que la creó.

## 6. Pruebas de interfaz

Se comprobará que DONE funciona tanto desde ordenador como desde móvil.

Aspectos que se revisarán:

- Adaptación a diferentes tamaños de pantalla.
- Navegación entre páginas.
- Formularios y botones.
- Mensajes de error.
- Accesibilidad básica.
- Compatibilidad con navegadores modernos.

**Herramienta propuesta:** Playwright.

## 7. Pruebas de seguridad

Se realizarán comprobaciones de:

- Inicio y cierre de sesión.
- Recuperación de cuentas.
- Control de acceso a rutas protegidas.
- Acceso a datos de otros usuarios.
- Protección de credenciales.
- Validación de datos.
- Permisos de servicios externos.

**Ejemplo:**

Un usuario A intenta acceder a una tarea perteneciente al usuario B.

**Resultado esperado:** el backend rechaza la operación y no devuelve datos privados.

## 8. Pruebas de inteligencia artificial

DONE deberá comprobar que las respuestas de la IA no se convierten automáticamente en operaciones autorizadas.

**Pruebas previstas:**

- Interpretación de solicitudes.
- Identificación de acciones necesarias.
- Solicitud de confirmación.
- Rechazo de operaciones sin autorización.
- Manejo de solicitudes ambiguas.
- Tratamiento de instrucciones maliciosas presentes en correos o páginas externas.

La autorización se comprobará desde el backend y no dependerá únicamente de lo indicado por el modelo de IA.

## 9. Pruebas de automatización

Las automatizaciones se probarán inicialmente con servicios simulados.

**Ejemplo: cancelación de suscripción**

1. El usuario solicita cancelar una suscripción de prueba.
2. DONE identifica el servicio.
3. La IA prepara la operación.
4. DONE solicita confirmación.
5. El usuario confirma.
6. El sistema ejecuta la acción simulada.
7. Se registra el resultado.

**Resultado esperado:** la acción no se ejecuta sin confirmación y no se repite accidentalmente.

Posteriormente se utilizarán integraciones reales compatibles.

## 10. Gestión de errores mediante GitHub Issues

Cada error identificado deberá registrarse en GitHub cuando requiera seguimiento.

La incidencia contendrá:

- Título.
- Descripción.
- Pasos para reproducir el problema.
- Resultado esperado.
- Resultado obtenido.
- Capturas o registros relevantes, sin datos sensibles.
- Prioridad.
- Responsable.

Los errores podrán clasificarse como:

**Crítico:** compromete seguridad, datos o funciones esenciales.

**Alto:** impide utilizar una funcionalidad importante.

**Medio:** afecta al comportamiento sin bloquear completamente el uso.

**Bajo:** problema menor, visual o de usabilidad.

## 11. Procedimiento para corregir errores

1. Registrar la incidencia.
2. Reproducir el fallo.
3. Identificar su causa.
4. Crear una rama de corrección.
5. Implementar la solución.
6. Incorporar una prueba para evitar regresiones cuando corresponda.
7. Ejecutar las pruebas afectadas.
8. Crear un pull request.
9. Solicitar revisión.
10. Integrar los cambios aprobados.

Ejemplo de rama:

`fix/error-creacion-tarea`

## 12. Pruebas automáticas

Se configurarán progresivamente herramientas como:

- Vitest.
- React Testing Library.
- Playwright.
- GitHub Actions.

Una vez instaladas, se definirán los comandos correspondientes en `package.json`.

No se asumirán comandos de pruebas hasta que estén efectivamente configurados.

## 13. Integración continua

Se utilizará GitHub Actions cuando estén preparadas las pruebas automatizadas.

El objetivo será ejecutar comprobaciones cuando se cree o actualice un pull request.

Inicialmente se comprobarán:

- Errores de TypeScript.
- Reglas de ESLint.
- Pruebas unitarias.
- Compilación de la aplicación.

Más adelante se incorporarán pruebas de integración y navegador.

## 14. Pruebas de regresión

Después de introducir cambios importantes, se comprobará que las funcionalidades existentes siguen funcionando.

**Ejemplo:**

Después de modificar la autenticación, verificar que los usuarios todavía pueden acceder a sus tareas.

## 15. Pruebas antes de producción

Antes de publicar una nueva versión se verificará:

- Que la aplicación puede compilarse.
- Que las pruebas relevantes funcionan.
- Que las migraciones de base de datos están preparadas.
- Que los permisos y las credenciales están correctamente configurados.
- Que no existen errores críticos conocidos.
- Que las automatizaciones respetan las confirmaciones.
- Que existe un procedimiento de recuperación ante fallos.

## 16. Resolución de problemas frecuentes

### La aplicación no inicia

Comprobar que Node.js está instalado y que las dependencias del proyecto están disponibles.

Revisar los mensajes de error de la terminal.

### PostgreSQL no conecta

Comprobar el servicio PostgreSQL, el puerto, la base de datos y las credenciales.

### La aplicación no reconoce una variable de entorno

Comprobar que la variable está definida en el archivo correspondiente y reiniciar el servidor cuando sea necesario.

### Una prueba falla

Revisar el resultado esperado, los datos de entrada y los cambios recientes.

No eliminar una prueba únicamente para que el conjunto de pruebas aparezca como correcto.

### Una automatización falla

Registrar el problema, comprobar si la acción se ejecutó parcialmente y evitar reintentos que puedan duplicar sus efectos.

## 17. Reparto de responsabilidades

Ambos desarrolladores serán responsables de comprobar sus cambios.

El desarrollador que implemente una funcionalidad realizará las primeras pruebas.

El otro desarrollador revisará el pull request y comprobará los aspectos relevantes antes de aprobarlo.

## 18. Criterios de aceptación

Una funcionalidad se considerará terminada cuando:

- Cumpla los requisitos previstos.
- Supere las pruebas relevantes.
- No presente errores críticos conocidos.
- Respete los controles de seguridad.
- Haya sido revisada mediante pull request.
- Tenga su documentación actualizada.

## 19. Comprobación final

- [ ] Estrategia de pruebas definida.
- [ ] Herramientas de pruebas configuradas cuando corresponda.
- [ ] Procedimiento para registrar errores establecido.
- [ ] Revisión de pull requests organizada.
- [ ] Pruebas de autorización contempladas.
- [ ] Pruebas de IA y automatización definidas.
- [ ] Procedimiento previo al despliegue documentado.

## 20. Resultado esperado

DONE contará con un procedimiento de calidad que permita detectar y solucionar errores durante el desarrollo.

Las pruebas se ampliarán conforme se implementen nuevas funcionalidades.

El objetivo será mantener una aplicación estable, segura y verificable.
