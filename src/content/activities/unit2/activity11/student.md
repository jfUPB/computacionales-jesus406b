### Bitácora: Principales Conceptos Aprendidos y Traducción a Ensamblador Hack

En esta sección, además de los conceptos de punteros en C++, también se incorporará cómo se traducen estos conceptos al **lenguaje ensamblador Hack**. La programación en ensamblador Hack es un lenguaje de bajo nivel que interactúa directamente con la memoria, lo que nos permite ver cómo se manipulan los punteros y las variables a nivel de máquina.

---

### 1. **Punteros**
   - **En C++**:
     - Un puntero es una variable que almacena la **dirección de memoria** de otra variable. En lugar de almacenar un valor directamente, almacena la ubicación de ese valor en la memoria.
     - **Ejemplo en C++**:
       ```cpp
       int a = 10;
       int *p = &a;  // p apunta a la dirección de memoria de a
       ```
     - Aquí, `p` es un puntero que guarda la dirección de memoria de la variable `a`.
  
   - **En Ensamblador Hack**:
     - En Hack, no existen punteros explícitos como en C++, pero podemos simular punteros utilizando direcciones de memoria.
     - **Simulación en ensamblador Hack**:
       ```asm
       @16        // Dirección de 'a'
       M=10       // a = 10

       @17        // Dirección de 'p'
       M=16       // p apunta a la dirección de 'a'
       ```
     - Aquí, `p` es un puntero que guarda la dirección 16 (donde está `a`). El valor de `p` es simplemente la dirección de `a`.

---

### 2. **Desreferenciación**
   - **En C++**:
     - La desreferenciación se refiere al uso del operador `*` para acceder al **valor almacenado en la dirección de memoria** a la que apunta el puntero.
     - **Ejemplo en C++**:
       ```cpp
       int a = 10;
       int *p = &a;
       int b = *p;  // b toma el valor de a, que es 10
       ```
     - Aquí, `*p` accede al valor de `a` a través del puntero `p`.

   - **En Ensamblador Hack**:
     - En Hack, la desreferenciación se realiza al **acceder a la memoria** a través de un puntero (dirección de memoria) guardado en un registro o memoria.
     - **Simulación en ensamblador Hack**:
       ```asm
       @17        // Dirección de 'p' (que contiene la dirección de 'a')
       D=M        // D = valor almacenado en la dirección de p (que es 16)

       @D         // A = dirección de a (16)
       D=M        // D = valor en la dirección de a (que es 10)

       @18        // Dirección de b
       M=D        // b = *p, es decir, b = a = 10
       ```
     - Aquí, se accede a la dirección almacenada en `p`, que es `16`, y luego se accede al valor de `a`, que es 10.

---

### 3. **Operador `&` (Dirección de memoria)**
   - **En C++**:
     - El operador `&` se utiliza para obtener la **dirección de memoria** de una variable.
     - **Ejemplo en C++**:
       ```cpp
       int a = 10;
       int *p = &a;  // p recibe la dirección de memoria de a
       ```
     - Aquí, `&a` obtiene la dirección de memoria de `a` y la asigna al puntero `p`.

   - **En Ensamblador Hack**:
     - En Hack, obtener la dirección de memoria de una variable se hace directamente asignando la **dirección de memoria** a una variable o puntero.
     - **Simulación en ensamblador Hack**:
       ```asm
       @16        // Dirección de a
       M=10       // a = 10

       @17        // Dirección de p
       M=16       // p = &a, asigna la dirección de a (16) a p
       ```
     - Aquí, `p` toma la dirección de memoria de `a`, que es 16.

---

### 4. **Asignación a través de punteros**
   - **En C++**:
     - Se puede modificar el valor de una variable a través de un puntero, utilizando la desreferenciación (`*`).
     - **Ejemplo en C++**:
       ```cpp
       int a = 5;
       int *p = &a;
       *p = 10;  // Modifica el valor de a a 10
       ```

   - **En Ensamblador Hack**:
     - En Hack, podemos modificar el valor de una variable a través de un puntero cargando la dirección en un registro y luego asignando un nuevo valor en esa dirección de memoria.
     - **Simulación en ensamblador Hack**:
       ```asm
       @16        // Dirección de a
       M=5        // a = 5

       @17        // Dirección de p
       M=16       // p = &a, p contiene la dirección de a

       @17        // Dirección de p
       D=M        // D = dirección de a (16)

       @D         // Dirección de a
       M=10       // a = 10 (modificado a través de p)
       ```

     - Aquí, se modifica el valor de `a` a través de `p` asignando `10` a la dirección contenida en `p`.

---

### 5. **Lectura a través de punteros**
   - **En C++**:
     - Se puede leer el valor de una variable a través de un puntero utilizando la desreferenciación.
     - **Ejemplo en C++**:
       ```cpp
       int a = 10;
       int *p = &a;
       int b = *p;  // b recibe el valor de a, que es 10
       ```

   - **En Ensamblador Hack**:
     - En Hack, leer el valor a través de un puntero se hace accediendo a la memoria a la que apunta el puntero.
     - **Simulación en ensamblador Hack**:
       ```asm
       @16        // Dirección de a
       M=10       // a = 10

       @17        // Dirección de p
       M=16       // p = &a, p contiene la dirección de a

       @17        // Dirección de p
       D=M        // D = dirección de a (16)

       @D         // Dirección de a (16)
       D=M        // D = valor en a (10)

       @18        // Dirección de b
       M=D        // b = *p, es decir, b = a = 10
       ```

     - Aquí, `*p` se usa para leer el valor de `a` y asignarlo a `b`.

---

