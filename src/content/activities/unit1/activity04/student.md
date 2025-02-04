####Test

**Pregunta 1**
¿Cuál es la función de cada tipo de instrucción?

**respuesta:**
Introducción al lenguaje Hack
El lenguaje Hack es un lenguaje de máquina muy simple. Su instrucción más importante es @valor, donde valor puede ser un número o un nombre que represente un número. Esta instrucción guarda el valor en un registro llamado A. Por ejemplo:

@17 guarda el número 17 en A

@sum (si sum es la dirección de memoria 17) también guarda 17 en A

Hack tiene dos tipos de instrucciones:

1. A-Instrucción (@valor)
Guarda un número en el registro A.
Sirve para:
Guardar constantes en A (@5 → A = 5).
Indicar la dirección de memoria donde queremos operar.

2. C-Instrucción (dest = comp ; jump)
Es la instrucción que realmente hace operaciones.
Contiene tres partes:
comp → qué calcular (por ejemplo, D-1).
dest → dónde guardar el resultado (D, M, A).
jump → cuándo saltar a otra parte del código.

**Pregunta 2**
¿Cómo se representa cada tipo de instrucción en binario?

**respuesta:**
*A-Instrucción*
0000000000000101  // 0 seguido de 15 bits con el número 5 en binario

*C-Instrucción*
1110110111010000

**Pregunta 3**
Proporciona al menos 3 ejemplos de cada tipo de instrucción, explicando qué hace cada una. Puedes usar las tablas de las páginas 67 y 69 del documento como referencia para los códigos de operación (comp), destinos (dest) y saltos (jump).

**respuesta:**

![image](https://github.com/user-attachments/assets/e7f802df-b1ea-4476-a575-7c836b55f78d)
