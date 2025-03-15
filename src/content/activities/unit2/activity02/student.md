####TEST

**Bitácora: Análisis del Programa en Ensamblador**

1. Direcciones de memoria de las variables i y sum
En el simulador, las variables i y sum se asignan a direcciones de memoria específicas en la RAM. La asignación de estas direcciones varía dependiendo de la implementación del simulador, pero generalmente las primeras direcciones disponibles en la RAM (después de los registros predefinidos) son utilizadas para almacenar variables. En este caso, i y sum se encuentran en dos ubicaciones de memoria separadas. Se puede determinar sus direcciones observando el estado de la RAM durante la ejecución del programa.

2. Diferencia entre la dirección de una variable y su contenido
La dirección de una variable es el lugar físico en la memoria donde se almacena su valor, mientras que el contenido de la variable es el valor que se encuentra almacenado en esa dirección en un momento dado. Por ejemplo, si i está almacenada en la dirección de memoria 16 y su contenido es 5, significa que la posición 16 de la RAM contiene el valor 5.

3. Implementación de la condición i <= 100
La condición i <= 100 se implementa en ensamblador a través de los siguientes pasos:

1)Se carga el valor de i en el registro D:

```asm
@i
D=M
```

(Esto coloca el valor de i en el registro D.)

2)Se resta 100 de D:
@100
D=D-A
(Esto calcula i - 100.)

3)Se evalúa si D > 0:
@END
D;JGT
(Si i - 100 es mayor que 0, significa que i > 100, por lo que el programa salta a END, terminando el bucle.)

Si i es menor o igual a 100, el programa sigue ejecutando las instrucciones dentro del bucle (LOOP), sumando i a sum y aumentando i en 1 antes de volver a evaluar la condición.

Conclusión
Este ejercicio permite comprender cómo un programa escrito en un lenguaje de alto nivel como C++ se traduce a instrucciones de bajo nivel en ensamblador. Además, ayuda a visualizar la relación entre direcciones de memoria y contenido, así como la forma en que se implementan estructuras de control como los bucles y las comparaciones.

