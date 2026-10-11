# DONE — Manual de instalación del entorno virtualizado

**Versión:** 2.0  
**Sistema anfitrión:** Windows 10/11  
**Virtualizador:** Oracle VirtualBox  
**Sistema invitado:** Windows 11 de 64 bits  
**Equipo:** 2 desarrolladores

## 1. Objetivo

Configurar un entorno de desarrollo virtualizado para DONE que permita a ambos desarrolladores trabajar con las mismas herramientas y configuraciones.

Cada desarrollador utilizará una máquina virtual independiente.

## 2. Requisitos previos

Antes de instalar VirtualBox se comprobará:

- Procesador compatible con virtualización.
- Virtualización Intel VT-x o AMD-V disponible.
- Memoria RAM suficiente.
- Espacio libre en disco.
- Acceso a Internet.
- Disponibilidad de una licencia válida de Windows cuando corresponda.

Configuración recomendada de la máquina virtual:

| Recurso | Configuración |
|---|---|
| Nombre | DONE-DEV |
| Sistema operativo | Windows 11 (64 bits) |
| RAM | 8 GB, si el equipo físico lo permite |
| Procesadores virtuales | 4, si el equipo físico lo permite |
| Disco virtual | 100 GB dinámicos |
| Red | NAT |
| TPM | 2.0 |
| Arranque | EFI y Secure Boot |

La asignación exacta de recursos dependerá de las características de cada ordenador.

## 3. Instalación de VirtualBox

1. Acceder a https://www.virtualbox.org/wiki/Downloads
2. Descargar la versión estable para Windows.
3. Ejecutar el instalador.
4. Completar la instalación.
5. Reiniciar el ordenador si se solicita.
6. Abrir Oracle VirtualBox.

## 4. Descarga de Windows 11

1. Acceder a https://www.microsoft.com/software-download/windows11
2. Descargar la imagen ISO oficial de Windows 11.
3. Guardarla en el ordenador físico.
4. Comprobar que se ha descargado correctamente.

## 5. Creación de la máquina virtual

1. Abrir VirtualBox.
2. Seleccionar Nueva.
3. Introducir el nombre DONE-DEV.
4. Seleccionar Windows 11 de 64 bits.
5. Asociar la imagen ISO.
6. Configurar la memoria RAM.
7. Asignar los procesadores virtuales.
8. Crear el disco virtual.
9. Configurar TPM 2.0, EFI y Secure Boot según las opciones compatibles.
10. Iniciar la máquina virtual.

## 6. Instalación de Windows

1. Iniciar el instalador de Windows.
2. Elegir idioma y distribución de teclado.
3. Completar la instalación.
4. Configurar una cuenta de usuario.
5. Instalar las actualizaciones disponibles.
6. Comprobar la conexión a Internet.

## 7. Instalación de Guest Additions

Dentro de la máquina virtual:

1. Abrir el menú Dispositivos de VirtualBox.
2. Seleccionar Insertar imagen de CD de las Guest Additions.
3. Ejecutar el instalador desde Windows.
4. Reiniciar la máquina virtual.

Estas herramientas mejoran la integración, resolución de pantalla y manejo del ratón.

## 8. Instalación de herramientas de desarrollo

Dentro de Windows virtualizado, instalar:

- Visual Studio Code.
- Git.
- Node.js 24 LTS y npm.
- PostgreSQL.
- pgAdmin.

Utilizar exclusivamente las páginas oficiales de descarga.

## 9. Verificación de instalaciones

Abrir PowerShell y ejecutar:

```powershell
git --version
node --version
npm --version
psql --version
```

Comprobar también que VS Code y pgAdmin funcionan correctamente.

Si `psql` no se reconoce, revisar su ubicación y configuración en PATH.

## 10. GitHub

Cada desarrollador configurará su propia cuenta de GitHub dentro de la máquina virtual.

Se deberá comprobar el acceso al repositorio privado de DONE.

No se compartirán contraseñas ni tokens de acceso.

## 11. Seguridad del entorno

- Mantener Windows actualizado.
- Activar las protecciones de seguridad disponibles.
- No almacenar credenciales en el repositorio.
- Evitar carpetas compartidas innecesarias.
- Utilizar credenciales independientes.
- Realizar instantáneas de la máquina virtual antes de cambios importantes.
- No confundir las instantáneas con las copias de seguridad de PostgreSQL.

## 12. Comprobación final

- [ ] VirtualBox instalado.
- [ ] Máquina virtual DONE-DEV creada.
- [ ] Windows 11 funcionando.
- [ ] Conexión a Internet disponible.
- [ ] Guest Additions instaladas.
- [ ] VS Code instalado.
- [ ] Git configurado.
- [ ] Node.js y npm funcionando.
- [ ] PostgreSQL y pgAdmin funcionando.
- [ ] Acceso a GitHub comprobado.

## 13. Resultado esperado

Ambos desarrolladores dispondrán de un entorno Windows virtualizado preparado para instalar y ejecutar DONE.

La configuración del repositorio, las dependencias y la base de datos del proyecto se abordará en los manuales posteriores.
