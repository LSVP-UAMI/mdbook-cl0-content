# Procesos

Un proceso representa un programa en ejecución. Es la abstracción a
través de la cual se pueden administrar y monitorear la memoria, el
tiempo de CPU y los recursos de entrada/salida.

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

    $ ps aux
    USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
    root           1  0.0  0.0 240824 13816 ?        Ss   jun23   0:05 /usr/lib/systemd/...
    root           2  0.0  0.0      0     0 ?        S    jun23   0:00 [kthreadd]
    root           3  0.0  0.0      0     0 ?        I<   jun23   0:00 [rcu_gp]
    root           4  0.0  0.0      0     0 ?        I<   jun23   0:00 [rcu_par_gp]
    root           5  0.0  0.0      0     0 ?        I<   jun23   0:00 [slub_flushwq]
    root           7  0.0  0.0      0     0 ?        I<   jun23   0:00 [kworker/...]
    root           9  0.0  0.0      0     0 ?        I<   jun23   0:00 [mm_percpu_wq]
    root          10  0.0  0.0      0     0 ?        S    jun23   0:00 [rcu_tasks_rude_]
    ...

### Actividades

**¿Cómo muestro todos los proceso de un usuario en particular?**
```admonish success title="Respuesta"
    1. ps uU USUARIO
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

### Señal TERN

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
    $ watch uptime &
```
para crear un nuevo proceso.

1.   ¿Cómo puedo puedo verificar que el proceso está en ejecución?

2.   ¿Cómo finalizo la ejecución del proceso?

```admonish success title="Respuestas"

1

        ps uU USUARIO
        ps u --pid PID`

2

        kill PID
        kill -s KILL PID
```

