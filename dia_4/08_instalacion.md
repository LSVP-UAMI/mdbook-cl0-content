# Instalación

## Compilación con GNU Tools
En linux la mayor parte de los programas son de software libre,
esto significa que podemos obtener el código fuente lo que nos 
permite modificar los programas y compilarlos para nuestro hardware.

### GCC (Gnu Compilers Collection)
*GCC* fue desarrollado como un compilador de lenguaje C para el proyecto 
GNU, con el tiempo paso a ser una colección de compiladores ya que empezó 
a dar soporte a mas lenguajes, actualmente en la versión 12.2 *gcc* 
puede compilar C, C++, Objective-C, Fortran, Ada, Go y D.

### ¿Que es Make?
Cuando un proyecto se vuelve grande o complejo se hace mas 
difícil compilarlo a mano, para estos casos existe *make*. 

*make* ayuda a automatizar la compilación de programas, los desarrolladores 
definen reglas para tareas especificas, estas reglas son usadas por *make* 
para saber que debe hacer.

Las reglas son definidas en un archivo llamado *Makefile* o *makefile*,
cuando vemos uno de estos archivos en el código fuente significa que 
podemos usar *make* para compilarlo.

Ejemplos de como compilar.
```
make
make all
```

Ejemplo de como instalar. (Debe estar definido en el *Makefile*)
```
make install
```

Si el *makefile* no tiene la operación *install* entonces la
instalación debe realizarse por otros medios. Esto puede hacerse copiando
los binarios al directorio donde deseamos hacer la instalación (usualmente
/usr/local/bin) y arreglando los permisos para que puedan ser ejecutados 
por cualquier usuario.

Los desarrolladores regularmente incluyen en el código fuente instrucciones 
para compilar e instalar el programa.

### Autoconf 
En muchas ocasiones las diferencias en el hardware y sistema operativo
hacen imposible para los desarrolladores el poder compilar el código 
usando solo un *makefile*, algunas formas de solucionar esto fueron 
escribir diferentes *makefile* para los diferentes escenarios o proveer uno
que fuera fácil de modificar. Con el tiempo evolucionó a scripts que
generan de forma automática el *makefile* haciendo un análisis de diferentes 
aspectos del sistema en el que se ejecutan.

*autoconf* nos ayuda a generar un *makefile* para esto genera un script 
llamado *configure*, este es el encargado de analizar el sistema y generar 
el *makefile* adecuado.

Para poder usar *autoconf* es necesario que los desarrolladores incluyan 
un archivo llamado *configure.ac* o *configure.in*.

*configure* algunas opciones para personalizar la instalación, estas 
opciones pueden ser consultadas con el siguiente comando.

```
 ./configure --help
```

#### Autoreconf
En ocasiones no es suficiente con ejecutar *autoconf*, para estos casos 
existe *autoreconf* esta herramienta se encarga de ejecutar *autoconf* 
junto con algunas otras herramientas que son necesarias en el proceso 
de generar un script de configuración.

Ejemplo de uso.
```
autoreconf -i
```

### Ventajas y desventajas de compilar los programas

#### Ventajas
* Los programas pueden ser adaptados a nuestras necesidades.
* Podemos instalar versiones especificas.
* Podemos tener múltiples versiones instaladas al mismo tiempo.
* Podemos optimizar los programas para nuestro hardware.

#### Desventajas
* Se necesitan conocimientos específicos para compilar.
* Se vuelve complicado administrar todos los programas que instalamos 
de esta forma.
* Se necesita experiencia para optimizar los programas.
* Se necesita tener mucho tiempo libre para hacer pruebas.

## Manejador de paquetes
Debido a los problemas que tiene compilar los programas con el tiempo 
surgieron los manejadores de paquetes, estos hacen mas fácil la tarea 
de administrar los programas que instalamos.

Un paquete incluye todos los archivos necesarios para la ejecución de 
un programa, esto incluye binarios previamente compilados, información 
sobre las dependencias y archivos de configuración.

Los paquetes también incluyen scripts que pueden ser ejecutados durante
cualquier punto de la instalación.

Los manejadores de paquetes tienen un modelo de dependencias, esto garantiza
que todas las librerías y otros programas de los que depende un paquete sean 
instalados previamente. 

### Formatos
En linux hay dos principales formatos de paquetes que son usados por 
la mayoría de las distribuciones son *rpm* y *deb*.

*rpm* fue creado para RedHat y es heredado por todas las distros basadas 
en esta. De la misma forma *deb* es el formato de Debian, y es compartido 
por sus derivadas.

Cada uno de estos formatos tiene una herramienta encargada de instalar 
y desinstalar los paquetes. Para *rpm* el instalador de paquetes es *rpm*
y *dpkg* es el respectivo de *deb*.

#### Comandos básicos
Instalar un paquete
```
rpm -i nombre_del_paquete.rpm
dpkg --install nombre_del_paquete.deb
```

Desinstalar un paquete
```
rpm -e nombre_del_paquete
dpkg --remove nombre_del_paquete
```

Listar los paquetes instalados
```
rpm -qa
dpkg -l
```

### Repositorios
Un repositorio es un servidor que funciona como un almacén de paquetes,
los repositorios son mantenidos por el equipo desarrollador de cada 
distribución, de esta forma controlan las versiones de cada paquete para
asegurarse de que son compatibles entre si. 

Por lo general las distros tienen una versión de cada paquete para 
cada tipo de arquitectura a la que dan soporte (64-bits, 32-bits, arm,
etc), también suelen almacenar varias versiones del mismo paquete.

### Manejadores de paquetes de alto nivel
Los manejadores de alto nivel ayudan a hacer mas simple las tareas 
de buscar y descargar paquetes, instalar dependencias de forma automática 
y hacer actualizaciones de paquetes.

Este tipo de manejadores de paquetes se conecta con los repositorios de
la distro para buscar y descargar los paquetes que queremos instalar,
además puede consultar si hay versiones mas recientes de los paquetes
que tenemos instalados para que estos sean actualizados.

Otra de sus funciones es que pueden consultar en que paquete se encuentra
algún archivo en específico, 

Los manejadores de paquetes para las principales distribuciones son los
siguientes.

Para RedHat y derivadas.
```
dnf
```

Para Debian y derivadas.
```
apt
```

Para Arch y derivadas.
```
pacman
```

#### Comando básicos
Buscar un paquete en los repositorios.
```
dnf search nombre_del_paquete
apt search nombre_del_paquete
pacman -Ss nombre_del_paquete
```

Instalar un paquete desde los repositorios.
```
dnf install nombre_del_paquete
apt install nombre_del_paquete
pacman -S nomre_del_paquete
```

Desinstalar un paquete.
```
dnf remove nombre_del_paquete
apt remove nombre_del_paquete
pacman -R nombre_del_paquete
```

Actualizar todos los paquetes instalados.
```
apt update && apt upgrade
dnf update
pacman -Su
```

Buscar un archivo dentro de los paquetes de los repositorios.
```
dnf provides nombre_del_archivo
apt-file search nombre_del_archivo
pacman -F nombre_del_archivo
```

#### Práctica
Instala los paquetes *fortune* y *cowsay* desde los repositorios.



