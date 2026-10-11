# DONE — Manual de configuración de PostgreSQL

**Versión:** 1.0  
**Estado:** Procedimiento inicial pendiente de validar  
**Entorno:** Windows 11 en Oracle VirtualBox  
**Sistema gestor:** PostgreSQL 17  
**Herramienta de administración:** pgAdmin 4  
**Equipo:** 2 desarrolladores

## 1. Objetivo

Configurar una base de datos PostgreSQL local para cada desarrollador de DONE.

Ambos tendrán bases de datos independientes, con la misma estructura y configuración, evitando que los cambios de uno afecten directamente al otro.

Este manual explica la instalación, creación de usuarios, permisos, conexión, migraciones, seguridad y copias de seguridad.

## 2. Arquitectura de las bases de datos

Durante el desarrollo, cada máquina virtual tendrá su propia instancia de PostgreSQL.

**Desarrollador 1:**
- Máquina virtual: DONE-DEV
- Base de datos: done_dev
- Usuario: done_dev_user

**Desarrollador 2:**
- Máquina virtual: DONE-DEV
- Base de datos: done_dev
- Usuario: done_dev_user

Aunque utilicen los mismos nombres, serán bases de datos independientes porque estarán alojadas en máquinas virtuales diferentes.

Las contraseñas serán propias de cada desarrollador.

## 3. Instalación de PostgreSQL

Página oficial:

https://www.postgresql.org/download/windows/

Procedimiento:

1. Descargar el instalador compatible con Windows.
2. Ejecutar la instalación.
3. Seleccionar PostgreSQL Server y Command Line Tools.
4. Instalar pgAdmin si todavía no está disponible.
5. Definir una contraseña segura para el usuario administrador `postgres`.
6. Utilizar el puerto 5432 si está disponible.
7. Finalizar la instalación.

Verificar en PowerShell:

```powershell
psql --version
```

Si el comando no se reconoce, comprobar el PATH de Windows o utilizar la herramienta SQL Shell (psql) instalada con PostgreSQL.

## 4. Conexión mediante pgAdmin

1. Abrir pgAdmin 4.
2. Localizar el servidor PostgreSQL.
3. Conectarse con el usuario administrador `postgres`.
4. Introducir la contraseña configurada durante la instalación.
5. Comprobar que aparecen las bases de datos del servidor.

En caso de que el servidor no aparezca, registrar una conexión local utilizando `localhost` y el puerto 5432.

## 5. Creación del usuario de DONE

Desde pgAdmin, abrir Query Tool conectado como administrador a la base de datos `postgres`.

Ejecutar:

```sql
CREATE ROLE done_dev_user
WITH LOGIN PASSWORD 'CAMBIAR_POR_CONTRASENA_SEGURA'
CREATEDB;
```

Sustituir el texto de ejemplo por una contraseña propia y segura.

El permiso `CREATEDB` se utilizará únicamente en desarrollo para permitir las bases temporales que Prisma Migrate pueda necesitar.

No se concederá el permiso de superusuario.

## 6. Creación de la base de datos

Desde Query Tool, conectado a la base `postgres`, ejecutar:

```sql
CREATE DATABASE done_dev
OWNER done_dev_user;
```

Comprobar que la nueva base aparece en pgAdmin.

## 7. Comprobación de permisos

Conectarse a `done_dev` utilizando `done_dev_user`.

Ejecutar:

```sql
SELECT current_user, current_database();
```

Resultado esperado:

- Usuario: done_dev_user
- Base de datos: done_dev

El usuario debe poder crear y modificar los objetos del esquema que le pertenece.

## 8. Configuración de conexión con DONE

Una vez creado el proyecto Next.js, cada desarrollador configurará su conexión local mediante una variable de entorno.

Ejemplo:

```env
DATABASE_URL="postgresql://done_dev_user:TU_CONTRASENA@localhost:5432/done_dev?schema=public"
```

La contraseña deberá sustituirse por el valor real.

Si contiene caracteres especiales, deberán codificarse correctamente para su uso en una URL.

Nunca se subirán credenciales reales al repositorio GitHub.

La aplicación accederá a PostgreSQL desde el backend, no directamente desde el navegador.

## 9. Configuración de Prisma

Prisma se utilizará para definir los modelos de datos y gestionar las migraciones.

La instalación se realizará cuando el proyecto Next.js esté inicializado.

La configuración exacta dependerá de la versión de Prisma seleccionada.

En las versiones actuales, la conexión y las migraciones pueden configurarse mediante `prisma.config.ts`.

Se verificará la configuración oficial antes de generar las primeras migraciones.

## 10. Creación de tablas

Las tablas se crearán a partir de los modelos definidos en Prisma.

Su estructura funcional está documentada en:

`docs/04-base-de-datos.md`

No se crearán manualmente las tablas definitivas desde pgAdmin, salvo cuando exista una necesidad documentada.

De esta manera, ambos desarrolladores podrán reproducir la estructura a partir del mismo código.

## 11. Migraciones

Las migraciones permiten mantener la misma estructura de base de datos en los dos ordenadores.

Durante el desarrollo se utilizará Prisma Migrate.

Comando previsto para generar y aplicar una migración:

```powershell
npx prisma migrate dev --name nombre_migracion
```

Para aplicar las migraciones existentes sin crear nuevas:

```powershell
npx prisma migrate deploy
```

Los archivos de migración se guardarán en GitHub.

No se modificarán manualmente migraciones ya compartidas y aplicadas sin acordarlo con el equipo.

En producción se utilizará un procedimiento específico de despliegue y nunca se ejecutará `migrate dev`.

## 12. Seguridad de PostgreSQL

Se aplicarán las siguientes medidas:

- Mantener PostgreSQL actualizado.
- Utilizar contraseñas seguras y diferentes para cada desarrollador.
- No utilizar el administrador `postgres` como usuario habitual de la aplicación.
- No conceder permisos de superusuario a DONE.
- Mantener la base de datos local sin exposición pública.
- Almacenar las credenciales fuera del código fuente.
- Proteger las copias de seguridad.
- Utilizar credenciales y permisos distintos en producción.

El permiso `CREATEDB` utilizado para el desarrollo no deberá concederse automáticamente al usuario de producción.

## 13. Copias de seguridad

Para crear una copia de seguridad local se podrá utilizar pgAdmin o `pg_dump`.

Ejemplo desde PowerShell, una vez que `pg_dump` esté disponible:

```powershell
pg_dump -h localhost -U done_dev_user -d done_dev -F c -f done_dev.backup
```

La herramienta solicitará la contraseña cuando corresponda.

Los archivos de copia deberán guardarse fuera del repositorio.

Antes de establecer copias automáticas se definirá una ubicación segura y una política de conservación.

## 14. Restauración de datos

Las copias generadas en formato personalizado podrán restaurarse mediante pgAdmin o `pg_restore`.

Antes de restaurar:

1. Seleccionar la base de datos de destino.
2. Comprobar que existe una copia válida.
3. Asegurarse de no sobrescribir datos importantes.
4. Ejecutar el procedimiento de restauración correspondiente.
5. Comprobar que las tablas y registros están disponibles.

Las restauraciones se probarán inicialmente en una base de datos temporal, nunca directamente sobre producción.

## 15. Problemas frecuentes

**No se puede conectar al servidor:**

Comprobar que PostgreSQL está iniciado y que utiliza el puerto configurado.

**Contraseña incorrecta:**

Revisar las credenciales del usuario correspondiente.

**La base de datos no existe:**

Comprobar su nombre desde pgAdmin.

**Error de permisos:**

Verificar el propietario de la base y los permisos del usuario.

**Prisma no puede crear una base temporal:**

Comprobar los permisos necesarios para las shadow databases utilizadas por Prisma Migrate.

**La aplicación no conecta:**

Revisar `DATABASE_URL`, el servicio PostgreSQL y la configuración de Prisma.

## 16. Comprobación final

Cada desarrollador deberá verificar:

- [ ] PostgreSQL instalado.
- [ ] pgAdmin funcionando.
- [ ] Servidor local accesible.
- [ ] Usuario done_dev_user creado.
- [ ] Base done_dev creada.
- [ ] Conexión con done_dev_user comprobada.
- [ ] Variables de entorno preparadas cuando exista la aplicación.
- [ ] Migraciones aplicadas cuando se implementen.
- [ ] Copias de seguridad configuradas cuando proceda.

## 17. Resultado esperado

Cada desarrollador dispondrá de una base de datos local independiente para DONE.

Ambos compartirán la estructura mediante las migraciones almacenadas en GitHub, manteniendo separados los datos y las contraseñas.

La configuración de producción se diseñará posteriormente, con credenciales, permisos y procedimientos de seguridad específicos.
