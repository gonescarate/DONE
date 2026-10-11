# DONE — Manual de configuración del proyecto

**Versión:** 1.0  
**Entorno:** Windows 11 virtualizado con Oracle VirtualBox  
**Equipo:** 2 desarrolladores  
**Estado:** Procedimiento inicial pendiente de validar

## 1. Objetivo

Este manual explica cómo descargar, configurar y ejecutar DONE en las máquinas virtuales Windows de ambos desarrolladores.

Todos los comandos se ejecutarán dentro de Windows 11 virtualizado, utilizando PowerShell o la terminal de Visual Studio Code.

## 2. Requisitos previos

Antes de comenzar, ambos desarrolladores deberán tener:

- Máquina virtual Windows 11 funcionando.
- Visual Studio Code instalado.
- Git instalado y configurado.
- Node.js 24 LTS y npm instalados.
- PostgreSQL y pgAdmin instalados.
- Acceso al repositorio privado de DONE.

Verificación en PowerShell:

```powershell
git --version
node --version
npm --version
```

## 3. Descargar DONE desde GitHub

Cada desarrollador deberá clonar el mismo repositorio.

Abrir PowerShell y ejecutar:

```powershell
mkdir C:\Proyectos
cd C:\Proyectos
git clone URL_DEL_REPOSITORIO
cd DONE
```

Sustituir `URL_DEL_REPOSITORIO` por la dirección HTTPS del repositorio privado obtenida mediante el botón Code de GitHub.

Comprobar la conexión:

```powershell
git remote -v
git status
```

## 4. Inicialización de la aplicación

La aplicación utilizará inicialmente:

- Next.js.
- React.
- TypeScript.
- Node.js.
- npm.

**Importante:** la inicialización solo se realizará una vez en el repositorio compartido.

El desarrollador responsable preparará el proyecto Next.js y subirá los archivos mediante un pull request.

Si el repositorio contiene únicamente documentación, se inicializará Next.js en una carpeta temporal y se incorporarán sus archivos al repositorio respetando los documentos existentes.

Una vez incorporado el proyecto, ambos desarrolladores descargarán la misma configuración.

## 5. Instalación de dependencias

Desde la raíz del proyecto, cuando exista `package.json`, ejecutar:

```powershell
npm ci
```

Este comando instalará las dependencias registradas en `package-lock.json`.

Si el proyecto todavía no contiene dichos archivos, será necesario completar primero la inicialización.

No se modificarán individualmente las versiones de las dependencias sin registrar los cambios en Git.

## 6. Configuración de variables de entorno

DONE utilizará variables de entorno para configurar las conexiones y los servicios externos.

El repositorio incluirá un archivo:

`.env.example`

Cada desarrollador creará su propio archivo de configuración local según las instrucciones del proyecto.

Las variables podrán incluir:

- Conexión con PostgreSQL.
- Claves de autenticación.
- Configuración de Google.
- Claves de servicios de IA.
- Configuración de integraciones.

No se utilizarán claves reales en los archivos de ejemplo.

Los archivos que contengan credenciales deberán excluirse del control de versiones.

## 7. Configuración de PostgreSQL

Cada desarrollador tendrá su propia base de datos local.

La configuración detallada se realizará siguiendo:

`03-configuracion-bbdd.md`

Este manual documentará:

- Creación de la base de datos.
- Usuarios y permisos.
- Configuración de conexión.
- Migraciones.
- Verificación de funcionamiento.

No se compartirán contraseñas locales entre desarrolladores.

## 8. Configuración de Prisma

Se utilizará Prisma como herramienta propuesta de acceso a PostgreSQL.

Su instalación y configuración definitiva se realizará al implementar la primera conexión con la base de datos.

Las migraciones se almacenarán en Git para que ambos desarrolladores puedan aplicar la misma estructura.

## 9. Ejecución de DONE

Una vez que el proyecto Next.js y las variables necesarias estén configurados, ejecutar:

```powershell
npm run dev
```

Abrir en el navegador:

http://localhost:3000

La aplicación deberá mostrar la página inicial de DONE.

El servidor deberá permanecer ejecutándose mientras se utiliza la aplicación en desarrollo.

## 10. Actualización del proyecto

Antes de comenzar una nueva tarea, actualizar el repositorio siguiendo el procedimiento de trabajo colaborativo.

Desde la rama principal:

```powershell
git switch main
git pull origin main
```

Después se creará la rama correspondiente a la funcionalidad.

Para instalar dependencias actualizadas:

```powershell
npm ci
```

## 11. Reparto del trabajo

Ambos desarrolladores trabajarán en el mismo repositorio y participarán en todas las áreas del sistema.

Las funcionalidades se dividirán en tareas pequeñas dentro de GitHub Projects.

Los cambios se revisarán mediante pull requests antes de incorporarlos a `main`.

## 12. Problemas frecuentes

**No funciona npm:**

Comprobar Node.js y revisar la configuración de PowerShell.

**No se encuentra package.json:**

Comprobar que se está ejecutando el comando desde la raíz correcta y que la aplicación ya se ha inicializado.

**El puerto 3000 está ocupado:**

Comprobar si existe otro servidor en ejecución.

**La base de datos no conecta:**

Revisar que PostgreSQL está iniciado y que la configuración de conexión es correcta.

**Git no permite descargar el repositorio:**

Comprobar los permisos y la autenticación de GitHub.

## 13. Comprobación final

- [ ] Repositorio clonado.
- [ ] Acceso a GitHub funcionando.
- [ ] Proyecto Next.js inicializado.
- [ ] Dependencias instaladas.
- [ ] Variables de entorno configuradas.
- [ ] Base de datos local preparada.
- [ ] Aplicación accesible desde el navegador.
- [ ] Ambos desarrolladores pueden ejecutar DONE de forma independiente.

## 14. Resultado esperado

Al finalizar este procedimiento, ambos desarrolladores tendrán una copia funcional de DONE en sus respectivas máquinas virtuales Windows 11.

Las configuraciones personales y credenciales permanecerán separadas, mientras que el código y las migraciones se compartirán mediante GitHub.
