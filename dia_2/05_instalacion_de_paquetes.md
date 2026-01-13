# Instalación de Software en Linux

En Linux, la instalación de programas ha evolucionado desde la construcción manual de archivos hasta sistemas automatizados en la nube. Entender estos tres niveles es fundamental para cualquier administrador de sistemas.

## 1. Compilación desde el Código Fuente

La compilación permite obtener el código fuente, modificarlo y adaptarlo específicamente a nuestro hardware. Aunque ofrece un control total, requiere más tiempo y conocimientos técnicos para su ejecución y optimización.

### Herramientas del Proyecto GNU

* **GCC (GNU Compiler Collection):** Es la colección de compiladores que traduce el código fuente a binarios ejecutables; soporta lenguajes como C, C++, Fortran, Go y D.
* **Make:** Ayuda a automatizar la compilación en proyectos complejos mediante reglas definidas en un archivo llamado `Makefile`.
* **Autoconf / Configure:** Genera un script llamado `configure` que analiza el sistema y crea el `Makefile` adecuado según el hardware y el sistema operativo detectado.

### Ventajas y Desventajas de Compilar

| Ventajas | Desventajas |
| --- | --- |
| Los programas pueden ser adaptados a necesidades específicas. | Se necesitan conocimientos específicos para compilar con éxito. |
| Permite instalar versiones específicas o múltiples versiones simultáneas. | Es complicado administrar y actualizar todos los programas instalados así. |
| Se puede optimizar el software para el hardware actual. | Requiere mucho tiempo para realizar pruebas y configuraciones. |

## 2. Gestión de Paquetes Locales (Bajo Nivel)

Para resolver los problemas de administrar programas compilados a mano, surgieron los **paquetes**.

```admonish info title="¿Qué es un Paquete?"
Es un archivo que incluye todos los binarios previamente compilados, archivos de configuración, scripts de ejecución e información sobre las dependencias necesarias para que el programa funcione.
```

### Formatos y Comandos Básicos

Existen dos formatos principales utilizados por la mayoría de las distribuciones: **.deb** (familia Debian) y **.rpm** (familia RedHat).

| Acción | **Formato .deb** (`dpkg`) | **Formato .rpm** (`rpm`) |
| --- | --- | --- |
| **Instalar** | `dpkg --install paquete.deb` | `rpm -i paquete.rpm` |
| **Desinstalar** | `dpkg --remove nombre_paquete` | `rpm -e nombre_paquete` |
| **Listar instalados** | `dpkg -l` | `rpm -qa` |

## 3. Manejadores de Paquetes de Alto Nivel

Son herramientas que simplifican las tareas de búsqueda, descarga e instalación automática de dependencias conectándose a repositorios.

```admonish info title="¿Qué es un Repositorio?"
Es un servidor que funciona como un almacén de paquetes mantenido por los desarrolladores de la distribución para asegurar la compatibilidad y seguridad del software.
```

### Comandos de Uso Diario

| Acción | **APT** (Debian/Ubuntu) | **DNF** (RedHat/Fedora) | **Pacman** (Arch) |
| --- | --- | --- | --- |
| **Buscar paquete** | `apt search <nombre>` | `dnf search <nombre>` | `pacman -Ss <nombre>` |
| **Instalar** | `apt install <nombre>` | `dnf install <nombre>` | `pacman -S <nombre>` |
| **Desinstalar** | `apt remove <nombre>` | `dnf remove <nombre>` | `pacman -R <nombre>` |
| **Actualizar todo** | `apt update && apt upgrade` | `dnf update` | `pacman -Su` |

### Práctica

Instala las siguientes herramientas utilizando el manejador de paquetes de tu distribución:

1. Instala el paquete `fortune`.
2. Instala el paquete `cowsay`.
3. Prueba ambos programas juntos usando el siguiente comando: `fortune | cowsay`.

1. Busca e instala el programa `moon-buggy`
2. Ejecuta el programa `moon-buggy`
