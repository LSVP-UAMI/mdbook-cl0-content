# Instalación de paquetes

## Compilación con GNU Tools

En Linux muchos de los programas son de software libre, esto significa
que podemos obtener el código fuente lo que nos permite modificar los
programas y compilarlos para nuestro hardware.

### ¿Qué es compilar? {#_qué_es_compilar}

Compilar es el proceso de transformar un programa informático escrito en
un lenguaje en un conjunto de instrucciones en otro formato o lenguaje.
Un compilador es un programa de computadora que realiza dicha tarea.

En particular cuando hablamos de compilar nos referimos a traducir
código escrito en un lenguaje de programación a código que puede ser
ejecutado por la computadora.

### ¿Cuáles son los compiladores de GNU? {#_cuáles_son_los_compiladores_de_gnu}

**GNU Compiler Collection** (**GCC**) fue desarrollado como un
compilador de lenguaje **C** para el proyecto GNU, con el tiempo paso a
ser una colección de compiladores, ya que empezó a dar soporte a más
lenguajes, actualmente en la versión 12.2 **gcc** puede compilar **C**,
**C++**, **Objective-C**, **Fortran**, **Ada**, **Go** y **D**.

### ¿Es lo mismo con proyectos más complejos? {#_es_lo_mismo_con_proyectos_más_complejos}

Cuando un proyecto se vuelve grande o complejo se hace más difícil
compilarlo a mano, para estos casos existe **make**.

**make** ayuda a automatizar la compilación de programas, los
desarrolladores definen reglas para tareas específicas, estas reglas son
usadas por **make** para saber que debe hacer.

Las reglas son definidas en un archivo llamado **Makefile** o
**makefile**, cuando vemos uno de estos archivos en el código fuente
significa que podemos usar **make** para compilarlo.

Ejemplos de como compilar.

```
    make
    make all
```

Ejemplo de como instalar. (Debe estar definido en el **Makefile**)

```
    make install
```

Si el **makefile** no tiene la operación **install** entonces la
instalación debe realizarse por otros medios. Esto puede hacerse
copiando los binarios al directorio donde deseamos hacer la instalación
(usualmente /usr/local/bin) y arreglando los permisos para que puedan
ser ejecutados por cualquier usuario.

Los desarrolladores regularmente incluyen en el código fuente
instrucciones para compilar e instalar el programa.

### ¿Make funciona en cualquier computadora? {#_make_funciona_en_cualquier_computadora}

En muchas ocasiones las diferencias en el hardware y sistema operativo
hacen imposible para los desarrolladores el poder compilar el código
usando solo un **makefile**, algunas formas de solucionar esto fueron
escribir diferentes **makefile** para los diferentes escenarios o
proveer uno que fuera fácil de modificar. Con el tiempo evolucionó a
scripts que generan de forma automática el **makefile** haciendo un
análisis de diferentes aspectos del sistema en el que se ejecutan.

**autoconf** nos ayuda a generar un **makefile**, para esto genera un
script llamado **configure**, este es el encargado de analizar el
sistema y generar el **makefile** adecuado.

Para poder usar **autoconf** es necesario que los desarrolladores
incluyan un archivo llamado **configure.ac** o **configure.in**.

El script **configure** incorpora algunas opciones para personalizar la
instalación, estas opciones pueden ser consultadas con el siguiente
comando.

``` 
    ./configure --help
```

**Autoreconf**

En ocasiones no es suficiente con ejecutar **autoconf**, para estos
casos existe **autoreconf** esta herramienta se encarga de ejecutar
**autoconf** junto con algunas otras herramientas que son necesarias en
el proceso de generar un script de configuración.

Ejemplo de uso.

```
    autoreconf -i
```
