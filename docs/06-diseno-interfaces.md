# DONE — Diseño de interfaces (UI/UX)

**Versión:** 1.0  
**Estado:** Diseño inicial  
**Plataforma:** Aplicación web responsive

## 1. Objetivo

Diseñar una interfaz sencilla, intuitiva y moderna que permita al usuario organizar sus tareas y solicitar a la inteligencia artificial que realice gestiones cotidianas.

DONE debe facilitar la ejecución de acciones, evitando que el usuario tenga que navegar por numerosas pantallas.

## 2. Principios de diseño

- Simplicidad: mostrar únicamente la información necesaria.
- Claridad: diferenciar las tareas pendientes, en proceso y completadas.
- Accesibilidad: utilizar textos legibles, buen contraste y navegación mediante teclado.
- Consistencia: mantener los mismos componentes visuales en toda la aplicación.
- Transparencia: informar de las acciones que realizará la IA antes de solicitar confirmación.
- Adaptabilidad: funcionar correctamente en móvil y ordenador.

## 3. Pantallas principales

### 3.1. Página de bienvenida

Será la primera pantalla para los visitantes que no hayan iniciado sesión.

Elementos:
- Logotipo DONE.
- Breve explicación del servicio.
- Botones de registro e inicio de sesión.
- Presentación de las funcionalidades principales.

### 3.2. Registro e inicio de sesión

Permitirá acceder mediante:
- Correo electrónico y contraseña.
- Inicio de sesión con Google.

Incluirá recuperación de contraseña y mensajes de error claros.

### 3.3. Panel principal (Dashboard)

Será la pantalla principal del usuario.

Incluirá:
- Resumen de tareas pendientes.
- Gestiones en proceso.
- Próximos eventos y recordatorios.
- Acceso al chat con IA.
- Acciones rápidas para crear tareas y solicitar gestiones.

### 3.4. Chat con inteligencia artificial

Permitirá escribir solicitudes en lenguaje natural.

Ejemplos:
- "Cancela mi suscripción."
- "Organízame una cena para el viernes."
- "Revisa si tengo correos importantes."

La IA podrá responder, proponer acciones y mostrar formularios de confirmación.

### 3.5. Gestión de tareas

Permitirá:
- Crear tareas.
- Editar información.
- Asignar prioridades.
- Establecer fechas límite.
- Consultar estados.
- Marcar tareas como completadas.

### 3.6. Calendario

Mostrará los eventos, compromisos y recordatorios.

Permitirá crear eventos y, cuando se implemente la integración, sincronizarlos con calendarios externos autorizados.

### 3.7. Gestiones y automatizaciones

Mostrará las solicitudes enviadas a DONE.

Cada gestión tendrá un estado:
- Pendiente.
- Esperando confirmación.
- En proceso.
- Completada.
- Fallida.

El usuario podrá consultar los detalles de cada operación.

### 3.8. Conexiones externas

Permitirá conectar y desconectar servicios compatibles.

Mostrará:
- Servicio conectado.
- Permisos autorizados.
- Estado de conexión.
- Opción de revocar el acceso.

### 3.9. Configuración y perfil

Permitirá modificar:
- Datos personales.
- Preferencias.
- Notificaciones.
- Contraseña, cuando corresponda.
- Opciones de privacidad.
- Solicitud de eliminación de cuenta.

## 4. Navegación en ordenador

La interfaz utilizará un menú lateral con acceso a:

- Inicio.
- Chat IA.
- Mis tareas.
- Calendario.
- Gestiones.
- Configuración.

El contenido principal aparecerá a la derecha.

## 5. Navegación en móvil

La aplicación adaptará los componentes a pantallas pequeñas.

Se utilizará una navegación compacta con acceso a las funciones principales.

El chat deberá poder utilizarse cómodamente mediante teclado táctil.

## 6. Diseño de confirmaciones

Antes de ejecutar una acción, DONE mostrará:

1. Qué acción va a realizar.
2. Sobre qué servicio o recurso actuará.
3. Qué información utilizará.
4. Si existe algún coste o consecuencia relevante.
5. Botones para confirmar o cancelar.

El usuario deberá confirmar expresamente la operación.

## 7. Mensajes de error

Los errores deberán explicarse en un lenguaje comprensible.

DONE informará de qué ha ocurrido y ofrecerá alternativas cuando sea posible.

No mostrará mensajes técnicos internos ni información sensible.

## 8. Diseño visual

La identidad visual definitiva se decidirá durante la fase de prototipado.

Se buscará una apariencia moderna, limpia y profesional.

Se utilizarán componentes reutilizables para botones, formularios, tarjetas, menús y ventanas de confirmación.

## 9. Prototipos

Antes de programar las pantallas se crearán prototipos de:

- Bienvenida e inicio de sesión.
- Panel principal.
- Chat con IA.
- Gestión de tareas.
- Calendario.
- Confirmación de operaciones.

Se comprobarán las versiones para ordenador y móvil.

## 10. Criterios de aceptación

Una pantalla se considerará preparada cuando:

- Muestre correctamente la información prevista.
- Sea comprensible para el usuario.
- Funcione en móvil y ordenador.
- Permita navegar de forma coherente.
- Muestre los errores apropiadamente.
- Cumpla los requisitos básicos de accesibilidad.
- Respete las reglas de seguridad y autorización.

## 11. Evolución

Este documento define la estructura funcional de las interfaces.

El diseño visual definitivo y los prototipos se elaborarán antes de implementar las pantallas correspondientes.
