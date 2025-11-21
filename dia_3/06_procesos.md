# Procesos
```admonish info title="Definición"
>Un proceso representa un programa en ejecución. Es la abstracción a
>través de la cual se pueden administrar y monitorear la memoria, el
>tiempo de CPU y los recursos de entrada/salida.
```

## Elementos

El kernel registra varias piezas de información sobre cada proceso.
Estos son algunas de los más importantes:

-   El mapa del espacio de direcciones del proceso

-   El estado actual del proceso (dormido, detenido, en ejecución, etc)

-   La prioridad de ejecución del proceso

-   Información sobre los recursos que ha utilizado el proceso (CPU,
    memoria, etc.)

-   Información sobre los archivos y puertos de red que ha abierto el
    proceso

-   El dueño del proceso

### PID: ID de proceso

El kernel asigna un identificador único a cada proceso. La mayoría de
los comandos que manipulan procesos requieren que se especifique un PID
para identificar el objetivo de la operación. Los PID se asignan en
orden a medida que se crean los procesos.

### PPID: ID del proceso padre

En Linux cuando un proceso crea un nuevo proceso, al proceso recién
creado se le llama hijo y al proceso que lo lanzó, padre. El PPID es el
PID del proceso padre.

### UID: ID del propietario

El UID de un proceso es el ID de usuario que lo creó. En general, solo
el creador (propietario) y el superusuario pueden manipular el proceso.

## ¿Cómo muestro los procesos del sistema?

El comando `ps` muestra una *captura* de los procesos actuales en el
sistema:
```
    ps [OPCIONES]
```
### Ejemplo 1

Para mostrar todos los procesos del sistema, ejecute el comando:

```
ps aux
```


### Actividades
``` admonish example title="Participación"
¿Cómo muestro todos los proceso de un usuario en particular?
```

### Otra herramienta
Actualmente contamos con herramientas interactivas para vizualizar y administrar los procesos un ejemplo es `htop`

```
htop
```

## Señales

Las señales son solicitudes de interrupción a nivel de proceso. Se
definen alrededor de treinta tipos diferentes, y se utilizan de diversas
maneras:

-   Se pueden enviar entre procesos como medio de comunicación.

-   Pueden ser enviados por medio de la terminal al presionar ciertas
    combinaciones de teclas.

-   Pueden ser enviada por el administrador del sistema.

-   Pueden ser enviados por el núcleo cuando un proceso comete una
    infracción como la división por cero.

-   Pueden ser enviadas por el kernel para notificar a un proceso sobre
    una condición de interés, por ejemplo, cuando un proceso hijo
    termina.

Cuando se recibe una señal, puede suceder una de dos cosas. Si el
proceso receptor definió un comportamiento para la señal, entonces es
manejada por el proceso. De lo contrario, el kernel realiza alguna
acción predeterminada en nombre del proceso. El comportamiento por
defecto cambia dependiendo del tipo de señal.

### Señal INT

La señal INT es enviada por medio de la terminal cuando el usuario
presiona la combinación de teclas Ctrl-C. Es una solicitud para terminar
la ejecución actual.

### Señal TERM

La señal TERM es una solicitud para terminar la ejecución completamente.
Se espera que el proceso de receptor limpie su estado y salga.

### Señal KILL

La señal KILL finaliza la ejecución de un proceso. Un proceso no puede
ignorar, bloquear o manejar esta señal. El kernel es el encargado
terminar el proceso.

## ¿Cómo envío una señal?

El comando `kill` puede enviar cualquier señal a un proceso, aunque por
defecto envía una señal `TERM`:
```
    kill PID
    kill -s SEÑAL PID
```
Este comando puede ser utilizado por cualquier usuario en sus propios
procesos o por el superusuario en cualquier proceso.

### Actividades

Ejecute el siguiente comando:
```
    watch uptime &
```
para crear un nuevo proceso.

```admonish example title="Participación"

1 ¿Cómo puedo puedo verificar que el proceso está en ejecución?

2 ¿Cómo finalizo la ejecución del proceso?

```

