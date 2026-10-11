# DONE — Manual de Git y trabajo colaborativo

**Versión:** 1.0  
**Entorno:** Windows 11 en Oracle VirtualBox  
**Equipo:** 2 desarrolladores  
**Plataforma:** GitHub y GitHub Projects

## 1. Objetivo

Establecer un procedimiento común para que los dos desarrolladores puedan trabajar simultáneamente en DONE, compartir código, revisar modificaciones y evitar conflictos.

Cada desarrollador trabajará desde su propia máquina virtual y utilizará el mismo repositorio de GitHub.

## 2. Herramientas necesarias

- Git instalado.
- Visual Studio Code.
- Cuenta personal de GitHub.
- Acceso al repositorio privado DONE.
- Autenticación configurada con GitHub.
- GitHub Projects para organizar tareas.

## 3. Configuración inicial de Git

Cada desarrollador deberá configurar su identidad.

Abrir PowerShell:

```powershell
git config --global user.name "Nombre Apellido"
git config --global user.email "correo@ejemplo.com"
```

Comprobar:

```powershell
git config --global --list
```

El correo utilizado debería estar asociado a la cuenta de GitHub correspondiente.

## 4. Clonar el repositorio

Cada desarrollador descargará su propia copia de DONE.

```powershell
mkdir C:\Proyectos
cd C:\Proyectos
git clone URL_DEL_REPOSITORIO
cd DONE
```

Sustituir `URL_DEL_REPOSITORIO` por la dirección HTTPS real del repositorio.

Este procedimiento solo debe realizarse una vez por ordenador.

## 5. Organización de ramas

La rama `main` contendrá el código revisado y aprobado.

Cada funcionalidad se desarrollará en una rama independiente.

Ejemplos:

- `feature/login`
- `feature/tasks`
- `feature/dashboard`
- `feature/ai-chat`
- `fix/login-error`
- `docs/update-manual`

No se desarrollarán funcionalidades directamente sobre `main`.

## 6. Crear una rama nueva

Antes de empezar, comprobar que no existen cambios locales pendientes.

```powershell
git status
```

Actualizar la rama principal:

```powershell
git switch main
git pull --ff-only origin main
```

Crear una rama:

```powershell
git switch -c feature/tasks
```

Comprobar la rama activa:

```powershell
git branch
```

## 7. Guardar modificaciones

Después de modificar archivos:

```powershell
git status
```

Añadir los archivos relacionados con la tarea:

```powershell
git add .
```

Crear un commit:

```powershell
git commit -m "feat: implementar gestion de tareas"
```

Es recomendable revisar los archivos añadidos antes de confirmar.

Ejemplos de mensajes:

- `feat: añadir inicio de sesión`
- `fix: corregir error de autenticacion`
- `docs: actualizar manual`
- `test: añadir pruebas de tareas`
- `refactor: reorganizar componentes`

## 8. Subir cambios a GitHub

Para subir una rama por primera vez:

```powershell
git push -u origin feature/tasks
```

Para posteriores actualizaciones:

```powershell
git push
```

Los cambios quedarán disponibles en GitHub, pero todavía no estarán incorporados a `main`.

## 9. Crear un pull request

Cuando una funcionalidad esté preparada:

1. Entrar en GitHub.
2. Abrir el repositorio DONE.
3. Seleccionar la rama desarrollada.
4. Pulsar Compare & pull request.
5. Explicar los cambios realizados.
6. Vincular la tarea correspondiente de GitHub Projects.
7. Solicitar la revisión del otro desarrollador.

El segundo desarrollador comprobará los cambios y las pruebas.

Si todo es correcto, se podrá integrar la rama mediante Merge pull request.

## 10. Revisión del código

Antes de aprobar un pull request se comprobará:

- Que el código cumple el objetivo de la tarea.
- Que no se han introducido errores evidentes.
- Que las pruebas funcionan.
- Que no se han subido contraseñas o archivos `.env`.
- Que los cambios no afectan negativamente a otras funcionalidades.
- Que la documentación se ha actualizado cuando corresponda.

El autor del código no deberá aprobar su propio trabajo como única revisión.

## 11. Actualizar el proyecto

Antes de comenzar una nueva funcionalidad:

```powershell
git switch main
git pull --ff-only origin main
```

Después se creará la rama nueva.

Si ya existe una rama de trabajo, primero habrá que comprobar si contiene cambios sin guardar o commits pendientes.

Nunca se eliminarán cambios locales sin revisarlos.

## 12. Resolver conflictos

Un conflicto puede aparecer cuando dos desarrolladores modifican partes incompatibles del mismo archivo.

Procedimiento recomendado:

1. Comprobar el estado del repositorio.
2. Identificar los archivos afectados.
3. Revisar las dos versiones.
4. Decidir qué cambios deben conservarse.
5. Resolver el conflicto desde VS Code.
6. Ejecutar las pruebas.
7. Confirmar la resolución.

No utilizar comandos destructivos como `git reset --hard` sin comprobar previamente qué cambios se perderán.

## 13. Gestión de tareas con GitHub Projects

Utilizaremos las siguientes columnas:

- Backlog.
- To Do.
- In Progress.
- In Review.
- Done.

Cada tarea deberá tener:

- Nombre.
- Descripción.
- Responsable.
- Prioridad.
- Criterios de aceptación.

Cuando un desarrollador comience una tarea, la moverá a In Progress.

Cuando termine el código, creará un pull request y moverá la tarea a In Review.

Solo pasará a Done cuando esté revisada y aprobada.

## 14. Trabajo simultáneo

Ejemplo:

**Desarrollador 1:** desarrolla el inicio de sesión en `feature/login`.

**Desarrollador 2:** desarrolla la interfaz de tareas en `feature/tasks`.

Ambos trabajan en sus ramas.

Cada uno sube sus cambios y crea su propio pull request.

Una vez revisados, los cambios se integran progresivamente en `main`.

Se intentará evitar que ambos modifiquen simultáneamente los mismos archivos sin coordinación.

## 15. Archivos que no deben subirse

No se subirán:

- Archivos `.env` con secretos.
- Contraseñas.
- Tokens de acceso.
- Claves de servicios externos.
- Bases de datos privadas.
- Copias de seguridad.
- Archivos temporales innecesarios.

Se utilizará `.gitignore` para excluir archivos locales.

Si se publica accidentalmente una credencial, deberá revocarse o sustituirse inmediatamente. Borrarla en un commit posterior no será suficiente.

## 16. Buenas prácticas

- Realizar commits pequeños.
- Utilizar nombres de ramas descriptivos.
- Revisar `git status` antes de actuar.
- Evitar subir archivos innecesarios.
- No compartir credenciales personales.
- Revisar los cambios antes de integrarlos.
- Mantener actualizada la rama principal local.
- Comunicar cualquier modificación que pueda afectar al trabajo del otro.

## 17. Problemas frecuentes

**Git rechaza un push:**

Comprobar la rama y si existen cambios remotos pendientes.

**No aparecen los cambios del compañero:**

Comprobar que han sido integrados en `main` y actualizar la copia local.

**Se ha modificado un archivo incorrectamente:**

Revisar las diferencias antes de descartar cambios.

**Aparecen conflictos:**

Resolverlos manualmente, verificando que se conserva el comportamiento necesario.

**No funciona la autenticación:**

Revisar el método de acceso a GitHub y los permisos del repositorio.

## 18. Comprobación final

- [ ] Ambos desarrolladores tienen acceso al repositorio.
- [ ] Ambos han configurado su identidad de Git.
- [ ] El proyecto está clonado en cada máquina virtual.
- [ ] Se pueden crear ramas independientes.
- [ ] Se pueden realizar commits.
- [ ] Se pueden subir ramas.
- [ ] Los pull requests permiten revisar cambios.
- [ ] GitHub Projects está preparado.
- [ ] Se conoce el procedimiento para resolver conflictos.

## 19. Resultado esperado

Los dos desarrolladores podrán trabajar simultáneamente en DONE, compartiendo código y documentación mediante GitHub.

Las funcionalidades se revisarán antes de incorporarse a `main`, reduciendo el riesgo de errores y pérdida de trabajo.
