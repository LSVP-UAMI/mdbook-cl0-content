# Scripts

Un script de shell es una serie de comandos escritos en un archivo; el
shell lee los comandos del archivo tal como lo haría si los
escribieramos en una terminal.

Los scripts de Bash comienzan con la siguiente línea, la cual indica que
el programa `/bin/bash` debe ejecutar los comandos en el archivo de
script.
```
    #!/bin/bash
```

***Estructura de un script en Bash***

```
    #!/bin/bash

    # Soy un comentario
    # Soy otro comentario

    Instruccion 1
    Instruccion 2
    ...
    Instrucción n
```

```admonish note title="Nota"
Se conoce como shebang al conjunto de caracteres #!. Con excepción del
shebang en la parte superior de un script, un # al comienzo de una
línea indica un comentario; es decir, el shell ignora cualquier cosa en
la línea después de #.
```

Para ejecutar un script utilizamos el comando `bash` seguido del nombre
del script. Por ejemplo:
```
    bash mi_script.sh
```

o de forma alternativa:
```
    ./mi_script.sh
```

Sin embargo, para esta última forma hay que asegurarse de que el archivo
tenga permisos de ejecución.

## Variables

En matemáticas, se llama variable a cualquier símbolo que representa a
cualquier valor de los comprendidos en un conjunto.
```
    $ x = 3.141592
    $ z = 1.618034
```

En programación, una variable es un contenedor con nombre para un
conjunto particular de bits o tipo de datos.

### Asignación

Para asignar un valor a una variable, se debe seguir el formato:
```
    nombre_variable=valor
```

Una variable puede contener un número, un caracter o una cadena de
caracteres. Por ejemplo:
```
    nombre=juan
    edad=23
    tipo_sangre=A
    estatura=1.75
```

Otra manera de de asignar un valor a una variable es mediante el comando
**read**. A continuación se muestra utilización del comando mediante un
ejemplo:
```
    $ read apellido
    $ Belmont
```

Esto sirve para guardar en la variable *apellido* el contenido
*Belmont*. Al pulsar la tecla Enter después del comando **read**, la
terminal quedará a la espera de que introduzcamos el valor que
almacenará la variable.

Cuando guardamos el resultado de un comando en una variable, el comando
va entre paréntesis y precedido de un **\$**. Ejemplo:
```
    $ ruta=$(pwd)
    $ echo $ruta
    /home/usuario
```

```admonish note title="Nota"
En Bash no es necesario declarar una variable, solo asignarle un valor.
```

### Valor

Para obtener el valor de una variable, utilizamos el símbolo **"$"**
seguido del nombre de la variable. Por ejemplo, para imprimir el valor
de una variable se utilizaría el siguiente formato:
```
    echo $mi_variable
```

Un caso particular sería:
```
    echo $edad
    23
```

## Variables especiales

Son variables que el shell establece internamente y que están
disponibles para el usuario.

***Tabla 1. Variables especiales del shell***

| **Variables** | **DEscripción** |
|:-------------:|-----------------|
| $0            | Nombre del script. |
| $n            | Argumento `n` pasado al script. |
| $#            | Número de argumentos pasados al script. |
| $@            | Todos los argumentos pasados al script. |
| $$            | ID de proceso del shell actual.   |
| $?            | Código de salida del último comando que el shell ejecutó.|

### Códigos de salida

Cuando un programa finaliza, éste deja un *código de salida*, un valor
numérico también conocido como *código de error* o *valor de salida*.
Cuando el código de salida es cero (0), generalmente significa que el
programa se ejecutó sin problemas. Sin embargo, si el programa tiene un
error, suele salir con un número distinto de 0.

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

## Ejercicios. {#_ejercicios}

Para los ejercicios primero copiamos el directorio
*/tmp/material-curso/dia4* a nuestro home:
```
    $ cd
    $ cp -r /tmp/material-curso/dia4 .
```

-   Realizar un script que haga lo siguiente:

    a.  Busque archivos con nombre *conejo* dentro del directorio
        *dia4/scripts* y muestrelos utilizando el comando **find**.
    ```admonish tip title="Pista"
    echo Se encontraron los siguientes conejos:

        find . -name conejo
    ```

    a.  Guarde los archivos (la ruta que regresa el comando) en un archivo
    temporal *conejos.tmp*
    ```admonish tip title="Pista"
        find . -name conejo \> conejos.tmp
    ```

    a.  Guarde la primer entrada en una variable llamada *archivo*.
    ```admonish tip title="Pista"
        archivo=\$(head -n 1 conejos.tmp)
    ```
    
    a.  Borre el archivo que coincide con la primer entrada (y con el valor
    de la variable *archivo*).
    ```admonish tip title="Pista"
        rm \$archivo       
    ```

    a.  Avise que se eliminó la primer coincidencia.

    b.  Utilice **find** para mostrar que el archivo se ha ido.

    c.  Borre el archivo temporal *conejos.tmp*
    ```admonish tip title="Pista"
        rm conejos.tmp
    ```

    -   Hacer un pequeño script que haga lo que sigue:

        a.  Intentar usar el comando type sobre curl (curl es el argumento
            del comando type) **y**, si se pudo lograr, que la terminal
            espere 3 segundos (usamos el comando **sleep 3** ).

        b.  Mostrar el contenido del archivo *about_periquito.txt* **y**, si
            se logra, que la terminal espere 7 segundos **y** si se logra,
            ejecutamos el comando **curl parrot.live**

