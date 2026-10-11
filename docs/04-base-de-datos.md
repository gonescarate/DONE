# DONE — Diseño de base de datos

**Versión:** 1.0  
**Estado:** Diseño inicial  
**Sistema gestor:** PostgreSQL  
**ORM propuesto:** Prisma

## 1. Objetivo

Diseñar una base de datos relacional que permita almacenar y gestionar la información de DONE de forma segura, organizada y ampliable.

La estructura se desarrollará progresivamente, creando inicialmente las tablas necesarias y añadiendo otras conforme se implementen nuevas funcionalidades.

## 2. Tablas principales

### 2.1. Usuarios (`users`)

Almacena la información básica de las cuentas.

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID | Identificador único |
| name | VARCHAR(100) | Nombre |
| email | VARCHAR(255) | Correo electrónico único |
| password_hash | TEXT | Contraseña cifrada mediante hash, si procede |
| created_at | TIMESTAMP | Fecha de creación |
| updated_at | TIMESTAMP | Última modificación |
| deleted_at | TIMESTAMP | Fecha de solicitud de eliminación |

Los usuarios registrados mediante Google no necesitan almacenar una contraseña local.

### 2.2. Tareas (`tasks`)

Almacena las gestiones pendientes de cada usuario.

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID | Identificador |
| user_id | UUID | Propietario de la tarea |
| title | VARCHAR(255) | Título |
| description | TEXT | Descripción |
| status | VARCHAR(30) | Estado |
| priority | VARCHAR(20) | Prioridad |
| due_date | TIMESTAMPTZ | Fecha límite |
| created_at | TIMESTAMPTZ | Fecha de creación |
| updated_at | TIMESTAMPTZ | Última modificación |

Estados iniciales: `pending`, `in_progress`, `completed`, `failed`.

### 2.3. Preferencias (`user_preferences`)

Almacena la configuración personalizada.

| Campo | Tipo | Descripción |
|---|---|---|
| user_id | UUID | Usuario |
| language | VARCHAR(10) | Idioma |
| timezone | VARCHAR(100) | Zona horaria |
| email_notifications | BOOLEAN | Avisos por correo |
| push_notifications | BOOLEAN | Avisos push |
| updated_at | TIMESTAMPTZ | Última modificación |

### 2.4. Conexiones externas (`external_connections`)

Registra los servicios vinculados por el usuario.

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID | Identificador |
| user_id | UUID | Propietario |
| provider | VARCHAR(50) | Proveedor externo |
| scopes | JSONB | Permisos autorizados |
| encrypted_credentials | TEXT | Credenciales protegidas |
| status | VARCHAR(30) | Estado de conexión |
| created_at | TIMESTAMPTZ | Fecha de conexión |
| updated_at | TIMESTAMPTZ | Última modificación |

Las credenciales y los tokens deberán cifrarse y protegerse. Nunca se devolverán directamente al frontend.

### 2.5. Operaciones de IA (`ai_operations`)

Registra las gestiones solicitadas a DONE.

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID | Identificador |
| user_id | UUID | Usuario |
| task_id | UUID | Tarea relacionada, si existe |
| operation_type | VARCHAR(50) | Tipo de operación |
| status | VARCHAR(30) | Estado |
| confirmation_status | VARCHAR(30) | Estado de autorización |
| created_at | TIMESTAMPTZ | Creación |
| updated_at | TIMESTAMPTZ | Última actualización |

Las operaciones que modifiquen información o actúen en servicios externos requerirán una autorización específica antes de ejecutarse.

### 2.6. Historial de acciones (`action_logs`)

Registra las acciones ejecutadas y su resultado.

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID | Identificador |
| operation_id | UUID | Operación relacionada |
| action_type | VARCHAR(100) | Acción |
| status | VARCHAR(30) | Resultado |
| error_code | VARCHAR(100) | Código de error, si existe |
| created_at | TIMESTAMPTZ | Fecha de ejecución |

No deberán almacenarse contraseñas, tokens ni información sensible innecesaria en los registros.

## 3. Tablas futuras

Se incorporarán conforme avance el desarrollo:

- `calendar_events`: eventos del calendario propio.
- `subscriptions`: suscripciones detectadas o introducidas.
- `notifications`: notificaciones.
- `chat_conversations`: conversaciones con la IA.
- `chat_messages`: mensajes de cada conversación.
- `reservation_requests`: solicitudes de reserva.
- `auth_accounts`: vinculación con proveedores de autenticación.
- `auth_sessions`: sesiones, si la estrategia elegida las requiere.

Los esquemas definitivos se diseñarán al implementar cada módulo.

## 4. Relaciones principales

- Un usuario puede tener muchas tareas.
- Un usuario puede tener varias conexiones externas.
- Un usuario tiene una configuración de preferencias.
- Un usuario puede solicitar múltiples operaciones de IA.
- Una tarea puede estar relacionada con varias operaciones de IA.
- Una operación de IA puede generar múltiples registros de acciones.

Estas relaciones se implementarán mediante claves primarias y foráneas.

## 5. Integridad de datos

Se utilizarán:

- Claves primarias para identificar registros.
- Claves foráneas para mantener las relaciones.
- Restricciones `NOT NULL` donde corresponda.
- Restricciones `UNIQUE` para impedir duplicados.
- Validación de estados y prioridades.
- Índices para optimizar las consultas habituales.

## 6. Seguridad

La base de datos no será accesible directamente desde el navegador.

Todas las consultas se realizarán a través del backend, que comprobará la identidad y los permisos del usuario.

Las consultas sobre información privada deberán filtrar por el usuario propietario.

Se utilizarán cuentas de base de datos con permisos limitados y variables de entorno para las credenciales.

Las contraseñas se almacenarán utilizando algoritmos seguros de hash, nunca mediante cifrado reversible ni texto plano.

## 7. Eliminación de cuentas

Se contempla un periodo de recuperación de hasta 30 días.

El campo `deleted_at` permitirá identificar las cuentas pendientes de eliminación definitiva.

El proceso deberá contemplar la revocación de conexiones externas y la eliminación o conservación justificada de los datos correspondientes, respetando los derechos legales aplicables.

## 8. Copias de seguridad

Se realizarán copias automáticas diarias de los datos persistentes.

Las copias deberán almacenarse de forma protegida y se comprobará periódicamente que pueden restaurarse.

Las copias de seguridad no deberán incluirse en el repositorio de GitHub.

## 
