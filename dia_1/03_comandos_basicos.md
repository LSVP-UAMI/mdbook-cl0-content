# Comandos básicos

## **¿Qué es un comando**

En el contexto de sistemas operativos basados en **Linux**, un comando
es una instrucción que se proporciona al sistema operativo para realizar
una tarea específica. Los comandos en **Linux** se ingresan a través de
una terminal o consola.

## Intérprete de comandos {#_intérprete_de_comandos}

En **Linux**, un intérprete de comandos, también conocido como shell, es
un programa que proporciona una interfaz de usuario para interactuar con
el sistema operativo. El shell acepta comandos ingresados por el
usuario, los interpreta y luego los ejecuta.

### Características del Intérprete de comandos: {#_características_del_intérprete_de_comandos}

**Prompt**

La línea de comandos muestra un indicador (prompt) que generalmente
muestra información sobre el usuario, la máquina y el directorio actual.
Este indicador está esperando a que el usuario ingrese un comando.

Ejemplo:

```
   maverick@rocky:~ $
```

Donde:

-   ***maverick*** es el nombre de usuario.
-   ***rocky*** es el nombre del host (equipo).

Encontraremos los siguientes símbolos `$` y `#`, los cuales tienen
diferentes significados:

**Prompt de usuario:**
-   Cuando se ve este símbolo `$`, nos indica que estás trabajando con 
    privilegios de usuarios normales.\

-   Los comandos que ejecutas con este prompt tiene acceso solo a los
    recursos y archivos a los que el usuario tiene permisos.

**Prompt de superusuario o root:**
-   Cuando ves este símbolo `#`, indica que estás trabajando con
    privilegios de superusuario o root.
-   Los comandos ejecutados con este prompt tiene acceso total al sistema
    y pueden realizar cambios críticos, como instalar o desinstalar
    programas, modificar configuraciones del sistema, etc.

``` admonish note title="NOTA"
Es muy importante tener precaución al utilizar el prompt de superusuario
`#`, ya que los comandos ejecutados con estos privilegios pueden
afectar al sistema de manera significativa. Por lo que te recomiendo
minimizar el uso de estos privilegios y solo utilizarlos cuando sea
necesario para evitar posibles problemas de seguridad o errores graves.
```

**Historial de comandos**

La mayoría de los shells mantienen un historial de comandos previos, lo
que facilita la recuperación y repetición de comandos anteriores.

## ¿Para qué sirven los comandos? {#_para_qué_sirven_los_comandos}

Permite al usuario interactuar con el sistema operativo y realizar
diversas operaciones, como la navegación por el sistema de archivos, la
manipulación de archivos y directorios, la gestión de procesos entre
otras funciones.

Ejemplos: *ls*, *cd*, *pwd*, *cp*, *mv*, *rm*, *mkdir*, *cat*, *touch*,...

## Sintaxis básica en Linux {#_sintaxis_básica_en_linux}
```
    $ comando [opciones] [argumentos]
```

| <!-- -->   | <!-- --> |
|:----------:|----------|
| Comando    | El nombre del comando que se va a ejecutar. |
| Opciones   | Modificadores que afectan el comportamiento del comando.|
| Argumentos | Datos que el comando necesita para realizar su tarea. |


## Entrada, Salida y Error Estándar {#_entrada_salida_y_error_estándar}

![Entrada, Salida y Error](./images/filesystem/estandarComandos.png)
***Figura 1. Entrada, Salida y Error Estándar***


## ¿Cómo saber las opciones del comando? *(man)* {#_cómo_saber_las_opciones_del_comando_emphasis_man_emphasis}

**Linux** cuenta con un gran número de comandos, por lo que saber todos
es complicado, por suerte existe **man** (manual) que nos dará
información del comando y las opciones con las que cuenta.
```
    $ man 'comando'
    $ man ping --> información del comando ping
```
-Para navegar a través de estas páginas usamos las flechas del teclado.\
-Para buscar dentro del manual basta con escribir una barra "/"
seguida del texto que queremos buscar.\
-Para pasar a la siguiente coincidencia presionamos la tecla "n" y
para regresar a la coincidencia anterior presionamos "shift + n".\
-Para salir presionamos "q".

*man* también es un comando, veamos el manual de *man*
```
$ man man

MAN(1)                                                      Utilidades de paginador del manual                                                     MAN(1)

NOMBRE
        man - interfaz de los manuales de referencia del sistema

SINOPSIS
        man [opciones de man] [[sección] página ...] ...
        man -k [opciones de apropos] regexp ...
        man -K [opciones de man] [sección] term ...
        man -f [whatis opciones] página ...
        man -l [opciones de man] archivo ...
        man -w|-W [opciones de man] página ...

DESCRIPCIÓN
        man  es el paginador de manuales del sistema.  Cada argumento de página dado a man normalmente es el nombre de un programa, utilidad o función. La
        página de manual asociada con cada uno de estos argumentos es, pues, encontrada y mostrada.  Si se proporciona una sección, man mirará solo en esa
        sección  del  manual.   La  acción  predeterminada es buscar en todas las secciones disponibles siguiendo un orden predefinido (véase DEFAULTS), y
        mostrar solo la primera página encontrada, incluso si la página existe en varias secciones.
...
```

Antes de empezar la aventura con Nemo, debemos descagar el material que
necesitamos, para ello crea una carpeta dentro de tu home con nombre
"Curso".
```
    $ mkdir Curso
```

Ahora vamos a copiar los archivos con la siguiente instrucción:
```
    $ cp -r /tmp/material-curso/dory Curso
```

## ¡Comencemos! {#_comencemos}

### ¿Dónde estamos? *(pwd)* {#_dónde_estamos_emphasis_pwd_emphasis}

El comando **pwd** (Print Work Directory) muestra la ruta absoluta del
lugar en que nos encontramos.
```
    $ pwd

    /home/dory
```
### ¿Cómo ver el contenido de los directorios? *(ls)* {#_cómo_ver_el_contenido_de_los_directorios_emphasis_ls_emphasis}

El comando **ls** (LiSt) lista el contenido que hay en la ruta
especificada (si no recibe una ruta, muestra lo que hay en el directorio
en que nos encontramos).
```
    $ ls

    Barco_Hundido    Corriente_Marina    Sherman_Wallaby_42_Sidney
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| ls | Despliega el contenido del directorio donde se encuentre. |
| ls /etc/apt | Despliegue el contenido de la ruta que se especifique. |
| ls -l | Utiliza formato de lista larga (muestra más detalles). |
| ls -a | No ignora entradas que empiecen con "." (archivos ocultos).|
| ls -t | Ordenar por tiempo de modificación (el más reciente primero). |
| ls -S | Ordena por tamaño de archivo.|

### ¿Cómo moverse entre los directorios? *(cd)* {#_cómo_moverse_entre_los_directorios_emphasis_cd_emphasis}

El comando **cd** (Change Directory) se utiliza para cambiar el
directorio actual en el que se encuentra.\
Ejemplo:
```
   cd Barco_Hundido
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| cd | En el caso que **cd** se ejecute sin parámetros, cambiará al directorio personal del usuario. |
| cd /etc/apt/ | Ir a la ruta especificada. Esta es una ruta absoluta ya que comienza con "/". |
| cd . | Directorio actual.                |
| cd .. | Cambia al directorio **padre** (un directorio arriba de donde estamos). |
| cd / | Cambia al directorio raíz.        |
| cd - | Cambia al directorio donde estábamos anteriormente. |

### Hora de crear un directorio *(mkdir)* {#_hora_de_crear_un_directorio_emphasis_mkdir_emphasis}

**mkdir** (MaKe DIRectory) se utiliza para crear directorios.\
```
   $ mkdir [opcion] nombreDirectorio
```
| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ mkdir nombreCarpeta | Crea un directorio llamado *nombreCarpeta*. |
| $ mkdir -p carpeta1/carpeta2 | Crea directorios de manera recursiva. |

### ¿Y los archivos? *(touch)* {#_y_los_archivos_emphasis_touch_emphasis}

**touch** (change file timestamps) se utiliza para crear archivos
vacíos.
```
   $ touch [opcion] 'nombreArchivo
```
| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ touch Documento | Crea un archivo llamado *Documento*.|
| $ touch ejemplo.txt | Crea un archivo llamado *ejemplo.txt*. |

### ¿Y si mejor creo una copia? *(cp)* {#_y_si_mejor_creo_una_copia_emphasis_cp_emphasis}

El comando **cp** (CoPy) lo utilizamos para copiar archivos y
directorios.
```
   $ cp [opcion] 'archivo/directorio' 'destino'
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ cp cancion musica/ | Copia el archivo *cancion* en el directorio *musica*. |
| $ cp -r temp/ aux/   | Copia el contenido del directorio *temp* en el directorio *aux* de manera recursiva. |

### ¿Cómo se puede mover un directorio o archivo? *(mv)* {#_cómo_se_puede_mover_un_directorio_o_archivo_emphasis_mv_emphasis}

Para mover de lugar un archivo o directorio utilizamos el comando **mv**
(MoVe).
```
    $ mv [opcion] 'archivo/directorio' 'destino'
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ mv archivo ruta/del/destino | Mueve *archivo* a *ruta/del/destino*. |
| $ mv carpeta1 carpeta2 | Mueve la *carpeta1* a *carpeta2*  |

### Renombrar un directorio o archivo *(mv)* {#_renombrar_un_directorio_o_archivo_emphasis_mv_emphasis}

Con **mv** (MoVe) también podemos renombrar un archivo o directorio.
```
   $ mv [opcion] 'nombre' 'nuevoNombre'
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ mv version1 version2 | Cambia el nombre de el archivo *version1* a *version2*.|

### Eliminemos algo *(rmdir)* {#_eliminemos_algo_emphasis_rmdir_emphasis}

**rmdir** (ReMove DIRectory) lo utilizaremos para eliminar directorios
vacíos, es decir, aquellos que no contengan subdirectorio ni archivos.
```
   $ rmdir [opcion] 'directorioVacio'
```
### Eliminar archivos *(rm)* {#_eliminar_archivos_emphasis_rm_emphasis}

Con **rm** (ReMove) podemos eliminar archivos, además de directorio que
no estén vacíos.
```
   $ rm [opcion] 'archivo'
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ rm documento.txt | Elimina el archivo *documento.txt*. |
| $ rm -r carpeta/ | Elimina de manera recursiva el directorio *carpeta/* y todo su contenido. |
| $ rm -i aux.txt | Solicita confirmación antes de eliminar el archivo *aux.txt*. |

```admonish warning title="Nota"
La opción **-r** (recursivo) es esencial cuando se utiliza rm para
eliminar directorios y su contenido. Sin está opción, **rm** no
eliminará directorios.
```

**Advertencia**

Antes de eliminar cualquier archivo o directorio, hay que estar
completamente seguros de que ya no son necesarios, pues tanto **rmdir**
con **rm** no solicitan algún tipo de confirmación y todo lo eliminado
no se podrá recuperar.

### ¿Qué está escrito aquí? *(cat)* {#_qué_está_escrito_aquí_emphasis_cat_emphasis}

El comando **cat** (conCATenate) se utiliza para concatenar y mostrar el
contenido de archivos.
```
    $ cat [opcion] file
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ cat *ejemplo.txt* | Muestra el contenido del archivo *ejemplo.txt*. |

### ¿Existe otra forma de ver el contenido de mi archivo? *(less)* {#_existe_otra_forma_de_ver_el_contenido_de_mi_archivo_emphasis_less_emphasis}

Si, **less** (LESS is more) también nos permite visualizar el contenido
de los archivos.
```
    $ less [opcion] file
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ less hola.c | Muestra en contenido de hola.c |

```admonish note title="Nota"
Presionamos *q* para salir de less.
```

**Diferencias entre *cat* y *less***

| **cat** | **less** |
|:--------|:---------|
| Su función principal es concatenar y mostrar el contenido de archivos en la salida estándar (generalmente la pantalla). | Permite visualizar el contenido de archivos de manera paginada, lo que facilita la navegación por grandes cantidades de datos. A diferencia de *cat*, *less* muestra el contenido de manera que se puede desplazar hacia arriba y hacia abajo.
|**cat archivo1 archivo2** muestra el contenido de **archivo1** seguido por el contenido de **archivo2**.      | **less archivo.txt** permite ver el contenido de *archivo.txt* de manera paginada, facilitando la lectura y la navegación. |
|Muestra todo el contenido de los archivos de una vez. Puede ser útil para archivos pequeños o cuando simplemente se quiere ver rápidamente el contenido completo.|  Permite desplazarse hacia arriba y hacia abajo, realizar búsquedas y ofrece otras funciones de visualización más avanzadas. |

### ¿Dónde lo encuentro? *(find)* {#_dónde_lo_encuentro_emphasis_find_emphasis}

Para buscar directorios o archivos utilizaremos el comando **find**
(encontrar).
```
    $ find [ruta] [opciones] -name 'patron'
```

| **Comando** | **Descripción**|
|:-----------:|----------------|
| $ find /home/usuario -name '*.txt' | Busca todos los archivos con extensión '.txt' en el directorio especificado.|

### Limpiemos la pantalla *(clear)* {#_limpiemos_la_pantalla_emphasis_clear_emphasis}

**clear** (limpiar) lo utilizaremos para limpiar la pantalla.
```
    $ clear
```

Otra manera de limpiar la pantalla es utilizando ***ctrl + l*** , se
borra el contenido visible en la terminal, pero el historial de comandos
y resultados anteriores sigue estando disponible. Este atajo es útil
para limpiar la pantalla y hacerla más legible, especialmente cuando se
han ejecutado muchos comandos y la salida en la terminal se vuelve
extensa. Es una forma rápida y conveniente de mantener la interfaz de
usuario limpia.
