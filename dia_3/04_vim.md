# Introducción a VIM

## 1. Historia y Filosofía de VIM
### 1.1 ¿Qué es VIM?
Vim (Vi Improved) es un editor de texto altamente configurable y eficiente, utilizado principalmente por programadores y administradores de sistemas. Está diseñado para ser rápido y potente, permitiendo editar texto directamente desde la línea de comandos sin necesidad de usar un ratón ni interfaces gráficas. Aunque se utiliza en muchos sistemas operativos, su origen está en los sistemas Unix, y se ha convertido en uno de los editores de texto más populares en ese entorno.

### 1.2 Breve historia de vi y VIM
El editor Vi fue creado en 1976 por Bill Joy, uno de los cofundadores de Sun Microsystems, mientras trabajaba en la Universidad de California, Berkeley. Joy desarrolló VIM como una versión visual mejorada del editor de texto ed, que ya existía en Unix. ed era un editor de líneas muy rudimentario, pero Joy quería algo más interactivo y eficiente, especialmente para editar archivos de configuración y código.

En 1991 Bram Moolenaar, inspirado por Vi, desarrolló Vim en 1991. Inicialmente lo lanzó como un "Vi mejorado" (de ahí su nombre Vi Improved), con características adicionales y más modernas, que hacían la edición de texto más poderosa y flexible.

Algunas de las mejoras que introdujo Vim sobre Vi incluyen:

+ **Resaltado de sintaxis** para varios lenguajes de programación.
+ **Deshacer ilimitado**, mientras que Vi solo permitía un nivel de deshacer.
+ **Ventanas divididas** y pestañas para trabajar con múltiples archivos a la vez.
+ **Soporte para plugins**, lo que permite a los usuarios extender sus funcionalidades.
+ **Modo visual**, para la selección de texto más intuitiva.
+ **Mejoras en el sistema de búsqueda y reemplazo**, incluyendo expresiones regulares.

### 1.3 La filosofía detrás de los editores modales
Vim pertenece a una categoría de editores modales, cuyo concepto central es la separación de modos en los que se realizan diferentes tareas. Esta filosofía contrasta con los editores convencionales, donde todas las acciones (escribir, navegar, editar) se realizan sin cambiar de contexto.

La filosofía detrás de los editores modales se centra en:

1. **Eficiencia de movimiento y edición**:
   - Los editores modales están diseñados para que el usuario pueda manipular el texto rápidamente sin necesidad de usar el ratón o depender de menús. En lugar de moverse de carácter en carácter con las teclas de flecha (como en muchos editores), en Vim se pueden usar comandos como `w`, `b`, `f`, y `gg` para mover el cursor de palabra en palabra, saltar líneas o ir directamente a cualquier parte del documento.
   - La capacidad de realizar acciones complejas con pocos comandos mejora la velocidad y fluidez de la edición.

2. **Manejo eficiente de operaciones frecuentes**:
   - En un editor modal como Vim, hay un modo especial para cada tarea. Esto permite realizar operaciones comunes (como moverte, copiar, pegar, cambiar de línea) de forma rápida y sin interrupciones. En un editor no-modal, las mismas teclas para moverse, escribir, o copiar tienen que ser manejadas de forma más torpe con combinaciones de teclas o menús contextuales.

3. **Reducción del movimiento innecesario**:
   - Los usuarios de Vim raramente necesitan mover sus manos fuera de la fila principal del teclado. Por ejemplo, en lugar de usar el ratón para seleccionar texto, puedes hacerlo con comandos rápidos del teclado en el **modo visual**.

4. **Modo de pensar diferente**:
   - Los editores modales te obligan a pensar de forma diferente sobre la edición de texto. En lugar de escribir directamente y luego usar el ratón para realizar correcciones o ajustes, primero se navega por el archivo en **modo Normal** y, cuando llegas a donde necesitas, entras en el **modo de Inserción** para modificar el contenido. Este enfoque puede parecer menos intuitivo al principio, pero a largo plazo resulta ser más productivo.



---

## 2. Instalación y Primeros Pasos
### 2.1 ¿Cómo instalar VIM?
La instalación de Vim se hace mediante los repositorios oficiales y el manejador de paquetes correspondiente según la distribución, esto es posible dado que Vim es un programa muy común.

### 2.2 Primera ejecución de VIM
Para ejecutar Vim se hace desde la línea de comandos mediante el comando `vim` o de la siguiente manera

```
$ vim archivo
```
Para salir se hace en el modo Normal con los siguientes comandos:

| Comando | Descripción |
|  :---:  |:-----------:|
| :w | Guarda los cambios en el archivo |
| :q | Sale de Vim|
| ZZ | Guarda los cambio y sale de Vim |
| ZQ | Sale sin guardar |

### 2.3 El archivo `.vimrc`
Elinación de la compatibilidad con Vi
```
set nocompatible
```
Compatibilidad con español
```
set encoding=utf-8
```
Aumento del historial de comandos
```
set history=100
```

Muestra el número de línea
```
set number
```

Muestra números relativos
```
set relativenumber
```

Activa el mouse
```
set mouse=a
```

Habilita las indentaciones de manera automática de las nuevas lineas
```
set autoindent
```
Resalta la línea actual
```
set cursorline
```

Resalta la columna actual
```
set cursorcolumn
```

Muestra la barra de estado
```
set laststatus=2
```

Habilita la sintaxis
```
syntax enable
```

Muestra los parentesis correspondientes
```
set showmatch
```

## 3. Modos de Operación
### 3.1 Modo Normal (Comand)
Es el modo por defecto de VIM y es donde nos podemos mover a través del texto, eliminar palabras, copiar líneas y ejecutar comandos de manipulación de texto.

Funciones principales:

+ Moverse por el archivo
+ Editar texto

> Para acceder al modo normal se hace presionando `Esc`

### 3.2 Modo Inserción (Insert)
Este es el modo en el que se edita texto directamente, como se haría en cualquier otro editor de texto, cualquier tecla que se presione aparecerá en el archivo.

> Para salir se hace presionando `Esc`

### 3.3 Modo Visual (Visual)
Este modo permite seleccionar bloques de texto para copiarlos borrarlos o realizar otras acciones sobre ellos.

Funciones principales:

+ Copiar
+ Pegar
+ Aumentar/Disminuir la sangría

> Para entrar se hace presionando `v` en modo normal, para salir se hace presionando `Esc`

### 3.4 Modo Línea de Comandos
En modo línea de comandos podemos ejecutar comandos específicos, como guardar el archivo, salir de VIM, buscar, reemplazar, entre otros. Sin embargo, es donde radica el poder y la versatilidad de VIM.

Funciones principales:

+ Guardar
+ Salir
+ Buscar
+ Modificar la sesión
+ Restablecer los cambios

> Para entrar se hace presionando `:` en modo normal, para salir se hace presionando `Esc`

---

## 4. Navegación Básica en VIM
### 4.1 Movimientos con las teclas h, j, k, l
Vim tiene una forma diferente de mover el cursor por el archivo, el cual se basa en la fila principal del teclado, de manera que siempre sea eficiente el desplazamiento.

| Comando | Descripción |
|  :---:  |:-----------:|
| h | Izquierda |
| j, CTRL N, +, ENTER | Abajo |
| k, CTRL P, -, BACKSPACE | Arriba |
| l | Derecha |

Es importante mencionar que la mayoría de los comando de Vim se pueden ejecutar varias veces en una sola instrucción, la manera de hacer esto es mediante argumentos numéricos que anteceden al comando en cuestión. Por ejemplo: El comando `j` "baja" el cursor una línea, pero si colocamos un número **n** antes de `j` bajará **n** lineas.

### 4.2 Saltos entre palabras y líneas
En normal querer movernos rápido cuando se trabaja con archivos, Vim permite movernos de palabra en palabra o incluso saltar a líneas del archivo concretas la forma de hacer eso es mediante comando en el modo normal. Estos comandos se normalmente son la primera letra de una plabra en inglés, por ejemplo el comando `e` proviene de *end*, `w` proviene de *word*. A continuación se muestran algunos comando de movimiento:

| Comando | Descripción |
|  :---:  |:-----------:|
| w | Avanza una palabra \* |
| W | Avanza una palabra \+ |
| b | Retrocede una palabra \* |
| B | Retrocede una palabra \+ |
| e | Avanza al final de la palabra \* |
| E | Avanza al final de la palabra \+ |
| **n**G | Nos mueve a la línea **n** |
| :**n** | Nos mueve a la línea **n** |

### 4.3 Navegar a través de archivos (dentro de un mismo archivo)
Es posible despalzarnos partes específicas del archivo mediante comandos

| Comando | Descripción |
|  :---:  |:-----------:|
| gg | Nos mueve al comienzo del documento |
| G | Nos mueve al final del documento |
| **n**G | Nos mueve a la línea **n** |
| :**n** | Nos mueve a la línea **n** |
| 0 | Nos mueve al principio de la línea |
| ^ | Nos mueve al primer caracter no vacio de la línea actual |
| - | Nos mueve al primer caracter no vacio de la línea anterior |
| $ | Nos mueve al final de la línea |
| { | Nos mueve al principio del parrafo |
| } | Nos mueve al final del parrafo |
| \'\' | Nos mueve a la línea anterior de ejucutar alguno de los comando anteriores |
| H | Nos mueve al primer carácter de la primera línea de la pantalla |
| M | Nos mueve al primer carácter de la línea que se encuentra a la mitad de la pantalla |
| L | Nos mueve al primer carácter de la última línea de la pantalla |

#### 4.3.1 "Mover la pantalla"
A veces es necesario movernos por el archivo o incluso acomodarlo para tener una mejor vista de lo que estamos haciendo para desplazarnos de forma rápida por el documento, para eso existen los siguientes comandos:

> Aviso
>
> Este curso está basado en el libro **Learning the vi and Vim Editors** de la editorial O'Reilly en el cual se maneja la siguiente nomenclatura:
>
> + \^G significa mantener presionada la tecla `CTRL` y presionar la tecla `G`
> + Para hacer referencia a alguna tecla siempre se hace con la letra mayúscula, por ejemplo: `A` hace referencia a la *a*, para hacer referencia a la *A* se hace de la siguiente manera `SHIFT-A`

| Comando | Descripción |
|  :---:  |:-----------:|
| CTRL g | Muestra la línea actual |
| CTRL f | Avanza una pantalla |
| CTRL b | Retrocede una pantalla |
| CTRL d | Avanza media pantalla |
| CTRL u | Retrocede media pantalla |
| CTRL e | Sube la pantalla una línea |
| CTRL y | Baja la pantalla una línea |
| z | Mueve la línea actual a la parte superior de la pantalla |
| z. | Mueve la línea actual a la parte superior de la pantalla |
| z- | Mueve la línea actual al centro de la pantalla |

---

## 5. Inserción de Texto
### 5.1 Comandos para insertar texto
Para insertar texto es necesario ingresar al modo Inserción, esto se puede hacer mediante los siguientes comando:

| Comando | Descripción |
|  :---:  |:-----------:|
| i | Nos coloca en modo Inserción antes del cursor |
| a | Nos coloca en modo Inserción después del cursor |
| c | Cambia el carácter en el que está el cursor |
| C | Elimina los caracters que se encuetren a continuación del cursor (de la misma línea) y nos coloca en modo Inserción |
| s | Elimina el carácter donde se encuentra el cursor y nos coloca en modo Inserción |
| S | Elimina la línea donde se encuentra el cursor y nos coloca en modo Inserción |
| R | Nos coloca en modo Inserción pero va sobre escribiendo los carácteres |

### 5.1 Comandos para insertar texto en distintas posiciones
Los siguiente comando son útiles para ahorrar tiempo al entrar en modo Inserción en posiciones comunes al editar código o archivos

| Comando | Descripción |
|  :---:  |:-----------:|
| I | Nos coloca en modo Inserción al inicio de la línea actual |
| A | Nos coloca en modo Inserción al final de la línea actual |
| o | Abre una nueva línea en modo insertar debajo de la línea actual del cursor |
| O | Abre una nueva línea en modo insertar arriba de la línea actual del cursor |

---

## 6. Copiar, Cortar y Pegar
### 6.1 Comandos para copiar y pegar
Para copiar y pegar Vim tiene un portapapeles propio donde almacena el texto copia o cortado

| Comando | Descripción |
|  :---:  |:-----------:|
| y | Copia algo, puede ser una palabra o un bloque |
| d | Corta algo, puede ser una palabra o un bloque |
| yy | Copia la línea actual |
| dd | Corta la línea actual |
| Y | Copia la línea actual |
| D | Corta la línea actual |
| p | Pega lo copiado después del cursor |
| P | Pega lo copiado antes del cursor |

### 6.2 Copiar y cortar palabras, líneas y bloques de texto
Como ya se ha mencionado, los comando o acciones de Vim se pueden usar juntos para crear comando o instrucciones más complejas con el mínimo te interacciones con el teclado, a continuación se muestran algunos ejemplos:

| Comando | Descripción |
|  :---:  |:-----------:|
| yw | Copia una palabra |
| y$ | Copia del cursor hasta el final de la línea actual |
| y0 | Copia del cursor hasta el principio de la línea actual |
| y} | Copia del cursor hasta el final del parrafo actual |
| dw | Corta una palabra |
| d$ | Corta del cursor hasta el final de la línea actual |
| d0 | Corta del cursor hasta el principio de la línea actual |
| d} | Corta del cursor hasta el final del parrafo actual |

---

## 7. Deshacer y Rehacer
### 7.1 Comandos para deshacer y rehacer
Los comando para deshacer y rehacer son muy sencillos y se muestran a continuación

| Comando | Descripción |
|  :---:  |:-----------:|
| u | Deshace el último cambio en el documento |
| CTRL r | Rehace |
| :e! | Regresa los cambios hasta la última vez que el archivo fue guardado |

---

## 8. Búsqueda y reemplazo
### 8.1 Búsqueda básica en VIM
La busqueda básica en Vim se hace igual que en y los manuales, es decir, con `/` en modo Normal, otros comandos son

| Comando | Descripción |
|  :---:  |:-----------:|
| /**patrón** | Busca el **patrón** hacia adelante |
| ?**patrón** | Busca el **patrón** hacia atrás |
| n | Repite la busqueda en la misma dirección |
| N | Repite la busqueda en la dirección contraria |
| f**n** | Mueve el cursor a la siguiente coincidencia de **n** en la línea actual (**n** puede ser cualquier carácter) |
| F**n** | Mueve el cursor a la coincidencia anterior de **n** en la línea actual (**n** puede ser cualquier carácter) |
| t**n** | Mueve el cursor al carácter anterior a la siguiente coincidencia de **n** en la línea actual (**n** puede ser cualquier carácter) |
| T**n** | Mueve el cursor al carácter previo a la coincidencia anterior de **n** en la línea actual (**n** puede ser cualquier carácter) |

### 8.2 Búsqueda de palabras bajo el cursor
Cuando tenemos el cursor sobre una palabra que deseamos buscar, es posible hacerlo sin la tener que escribir `/patrón` solo con presionar `*`

### 8.3 Reemplazo de texto en todo el archivo
Buscar y reemplazar es una operación común dentro del mundo de la programación o la edición de archivos, esto se hace de la siguiente manera:

```
:rango s/patrón/reemplazo/opciones
```
Adicionalmente se pueden incluir opciónes en este comando al final, algunas de estas opciones son

Rango:
+ **n**,**m** Se aplica entre las lineas **n** y **m** 
+ `%` Indica que el reemplazo se aplica a las todas las lineas del archivo

Opcions:
+ `g` Reemplaza todas las ocurrencias de la línea
+ `c` Solicita confirmación antes de cada sustitución
+ `i` No distingue entre mayúsculas y minúsculas
+ `l` Distingue entre mayúsculas y minúsculas

---
