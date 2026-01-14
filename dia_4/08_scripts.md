
# Scripts 

Un script de shell es una serie de comandos escritos en un archivo; el
shell lee los comandos del archivo tal como lo haría si los
escribieramos en una terminal.

Los scripts de Bash comienzan con la siguiente línea, la cual indica que
el programa `/bin/bash` debe ejecutar los comandos en el archivo de
script.
```bash
    #!/bin/bash
```

***Estructura de un script en Bash***

```bash
    #!/bin/bash

    # Soy un comentario
    # Soy otro comentario

    Instruccion 1
    Instruccion 2
    ...
    Instrucción n
```

```admonish note title="Nota"
Se conoce como `shebang` al conjunto de caracteres `#!`. Con excepción del
shebang en la parte superior de un script, un # al comienzo de una
línea indica un comentario; es decir, el shell ignora cualquier cosa en
la línea después de #.
```

Para ejecutar un script utilizamos el comando `bash` seguido del nombre
del script. Por ejemplo:
```bash
    bash mi_script.sh
```

o de forma alternativa:
```bash
    ./mi_script.sh
```

Sin embargo, para esta última forma hay que asegurarse de que el archivo
tenga permisos de ejecución.

## Editores de texto

### nano

Nano es un editor de texto sencillo y fácil de usar que funciona en la 
terminal de Linux. Está pensado para usuarios principiantes o para ediciones 
rápidas de archivos de configuración y scripts.

Para crear/editar un documento, simplemente ejecutamos:
```bash
nano documento
```

- Guardar los cambios: `ctrl + O` (luego enter para confirmar)
- Salir de nano:  `ctrl + X` (Preguntará si guardar cambios)

### vim 

Vim es un editor de texto avanzado y muy potente, ampliamente utilizado 
por administradores de sistemas y desarrolladores. Se basa en distintos 
modos de operación (normal, inserción, visual, entre otros), lo que permite 
editar texto de forma extremadamente eficiente una vez dominado.

Para crear/editar un documento, simplemente ejecutamos:
```bash
vim documento
```
Cuando abres vim, por defecto estarás en el modo de comandos. Para insertar 
contenido, presiona la tecla `I`. Verás la palabra `INSERT` en la parte inferior 
del terminal, indicando que estás en modo de inserción. Una vez que termines, 
presiona Esc para volver al modo de comandos.

**Salir de vim**

- Cerrar vim sin guardar los cambios: `:q`
- Guardar los cambios y cerrar vim: `:wq`

## Variables

En matemáticas, se llama variable a cualquier símbolo que representa a
cualquier valor de los comprendidos en un conjunto.
```bash
    x=3.141592
    z=1.618034
```

En programación, una variable es un contenedor con nombre para un
conjunto particular de bits o tipo de datos.

### Asignación

Para asignar un valor a una variable, se debe seguir el formato:
```bash
    nombre_variable=valor
```

Una variable puede contener un número, un caracter o una cadena de
caracteres. Por ejemplo:
```bash
    nombre=juan
    edad=23
    tipo_sangre=A
    estatura=1.75
```

Otra manera de de asignar un valor a una variable es mediante el comando
**read**. A continuación se muestra utilización del comando mediante un
ejemplo:
```bash
#!/bin/bash

# Muestra mensaje solicitando el nombre
echo "Introduce tu nombre: "

# Guarda el valor ingresado en la variable 'nombre_usuario'
read nombre_usuario

# Muestra un mensaje
echo "!Hola, $nombre_usuario!"
```

Esto sirve para guardar en la variable *nombre_usuario* el valor
introducido. 

Una manera más sencilla de mostrar mensajes iteractivos y guardar el valor 
ingresado es con el parametro *-p* de *read*: 
```bash
#!/bin/bash

# Pide al usuario que introduzca su nombre
read -p "Introduce tu nombre: " nombre_usuario

# Muestra un saludo usando el nombre introducido
echo "¡Hola, $nombre_usuario!"
```

De esta forma, tendríamos la pregunta y la variables en la misma línea.

Cuando guardamos el resultado de un comando en una variable, el comando
va entre paréntesis y precedido de un **\$**. Ejemplo:
```bash
    ruta=$(pwd)

    echo $ruta
    /home/usuario
```

```admonish note title="Nota"
En Bash no es necesario declarar una variable, solo asignarle un valor.
```

### Valor

Para obtener el valor de una variable, utilizamos el símbolo **"$"**
seguido del nombre de la variable. Por ejemplo, para imprimir el valor
de una variable se utilizaría el siguiente formato:
```bash
    echo $mi_variable
```

Un caso particular sería:
```bash
    edad=23

    echo $edad
    23
```

## Argumentos de un script
Son variables que se le pasan al ejecutar un script, para hacerlo
dinámico, accediendo a ellos con *variables especiales*, permitiendo 
automatizar tareas variando entradas como nombre de archivos o 
parámetros de configuración. La forma de leer cada argumento es: ***$1, $2 ... $n***
```bash
# Ejemplo de ejecución: 
./mi_script.sh hola 1234 archivo.txt verde
```

### Variables especiales

Son variables que el shell establece internamente y que están
disponibles para el usuario.

***Tabla 1. Variables especiales del shell***

| **Variables** | **Descripción** |
|:-------------:|-----------------|
| $0            | Nombre del script. |
| $n            | Argumento `n` pasado al script. |
| $#            | Número de argumentos pasados al script. |
| $@            | Todos los argumentos pasados al script. |
| $$            | ID de proceso del shell actual.   |
| $?            | Código de salida del último comando que el shell ejecutó.|

><center>
>
> **Ejercicios**
></CENTER>
>
>1. Crea un script `saludo.sh` que:
>   - Solicite al usuario los siguientes datos:
>       - Nombre
>       - Edad
>       - Carrera    
>   - Muestre el siguiente mesaje:
>       - ¡Hola "nombre", tienes "edad" años y estudias "carrera", saludos!

>2. Crea un script `info_sistema.sh` que muestre:
>   - Nombre del Host.
>   - Nombre del usuario. 
>   - Fecha.
>   - Directorio actual.
```admonish tip tittle="Pista"
Los datos a mostrar los obtienes con comandos.
```

>3. Crea un script llamado `argumentos.sh` que:
>   - Muestre el nombre del script.
>   - Muestre el primer argumento.
>   - Muestre el segundo argumento.
>   - Muestre el total de argumentos.
>   - Muestre Todos los argumentos.
>
> Ejecuta el script con al menos 3 argumentos.


## Control de flujo

### Condicionales

El condicional `if` en ejecuta código si una condición es verdadera, usando 
la estructura `if [ condición ]; then comandos; fi`, con `elif` para más condiciones 
y `else` para un bloque alternativo, siendo fundamental separar la condición de los 
corchetes con espacios y finalizar siempre con `fi`. 

```bash
if [ condición ]; then
    #comandos a ejecutar
    .
    .
elif [ condición ]; then
    #comandos a ejecutar
    .
    .
else # Bloque alterno
    #comandos a ejecutar
    .
    .
fi
```

| **Comparaciones comunes** | <!--> |
|:-------------------------:|-------|
| `-eq` | Igual |
| `-ne` | Distinto |
| `-gt` | Mayor que |
| `-lt` | Menor que | 
| `-ge` | Mayor o igual |
| `-le` | Menor o igual |
| `==`  | Igual (cadenas) |
| `!=`  | Diferente (cadenas) |
| `-f`  | Archivo existe |
| `-d`  | Directorio existe |


## Bucles

### for

El bucle `for` es una estructura fundamental para automatizar tareas repitiendo 
comandos sobre una lista de elementos (archivos, números, cadenas). Su sintaxis 
básica es:
```bash
for variables in elemento1 elemento2...
do
    # comandos a ejecutar para cada elemento
    echo "mensaje"
done
```
Donde la variable toma cada valor de la lista en cada iteración, ejecutando los 
comandos definidos. 

#### Bucle for estilo C

Esta sintaxis se parece a la de lenguajes como ***C, C++*** o ***java***, y es útil 
cuando se necesita un control más preciso sobre el índice, el límita y el incremento.
```bash
for ((EXPRESION1; EXPRESION2; EXPRESION3))
do
    # comandos a ejecutar
done
```

### while
El bucle `while` repite un bloque de código mientras una condición sea verdadera, 
evaluando la condición antes de cada iteración, y es ideal cuando no se sabe de 
antemano cuántas veces se repetirá.
```bash
while [ condición ]
do
    # comandos a ejecutar
    # Actualiza la variable de la condición para evitar bucle infinito,
done
```

```admonish info tittle="Importante"
En Bash, se utiliza **doble paréntesis** `(( ))` para realizar operacioes aritméticas
porque, por defecto, Bash trata las variables como cadenas de texto (strings).
```

><center>
>
> **Ejercicios**
></CENTER>
>
>4. Crea un script `comparar.sh` que:
>   - Reciba un número como argumento
>   - Indique si el número es mayor, menor o igual a 10

>5. Crea un script `archivo.sh` que:
>   - Reciba el nombre de un archivo.
>   - Verifique si existe
>   - Si existe, muestra información del archivo.
>   - Si no existe muestra un mensaje de error.

>6. Crea un script `cuante_atras.sh` que:
>   - Reciba un número.
>   - Muestre una cuenta regresiva hasta llegar a 0.

## Códigos de salida

Cuando un programa finaliza, éste deja un *código de salida*, un valor
numérico también conocido como *código de error* o *valor de salida*.
Cuando el código de salida es cero (0), generalmente significa que el
programa se ejecutó sin problemas. Sin embargo, si el programa tiene un
error, suele salir con un número distinto de 0.

Bash guarda el código de salida del último comando ejecutado en la variable 
especial `$?`.

Ejemplos comunes:
```bash
ls
echo $?

cat archivo_que_no_existe
echo $?
```

## Operadores lógicos

### AND

El operador lógico `&&` (and) funciona de la siguiente forma:
```
    COMANDO_1 && COMANDO_2
```

El shell ejecuta el `COMANDO_1`:

1.  Si su código de salida es 0, entonces el shell ejecuta el
    `COMANDO_2`.

2.  En caso contrario, el shell no ejecuta el `COMANDO_2`.

### OR

El operador lógico `||` (or) funciona de la siguiente forma:
```
    COMANDO_1 || COMANDO_2
```

El shell ejecuta el `COMANDO_1`:

1.  Si su código de salida es 0, el shell no ejecuta el `COMANDO_2`.

2.  En caso contrario, el shell ejecuta el `COMANDO_2`.

## Redireccionamiento
Permite cambiar el origen o destino de la entrada (teclado), salida estándar
(pantalla), y salida de error de los comandos.

### Salida Estándar (stdout)
- `>` (sobreescribe): comando > archivo.txt
- `>>` (añade): comando >> archivo.txt

### Entrada Estándar (stdin)
- `<` (lee desde archivo): comando < archivo.txt

### Salida de Error (stderr)
- `2>` (sobreescribe): comando 2> error.log
- `2>>` (añade): comando 2>> error.log

><center>
>
> **Ejercicios**
></CENTER>
>
>7. Escribe un script `contar_lineas.sh` que:
>   - Reciba un archivo como argumento
>   - Si el archivo existe, sobreescriba en el archivo `salida.txt` el numero 
>   de líneas del archivo recibido.
>   - Revisa el archivo `salida.txt`
>
> Para contar el número de líneas de un archivo utilizamos `wc -l`.

>8. Crea un script `mostrar.sh` que:
>   - Intente mostrar un archivo recibido como argumento
>   - Si falla, guarda el error de **cat** al final del archivo
>   `error.log` y muestre en pantalla *"Error al mostrar el archivo"*
>   - Revisa el archivo `error.log`

