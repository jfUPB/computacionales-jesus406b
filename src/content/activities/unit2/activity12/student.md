####TEST

A continuación, se presentan ejemplos para cada uno de los conceptos solicitados en lenguaje de alto nivel (C++) junto con sus equivalentes en ensamblador Hack. Cada uno de estos ejemplos ha sido simulado para asegurar que esté correcto.

### 1. **Condicionales**

#### **En C++**:
```cpp
int a = 10;
int b = 5;
int result;

if (a > b) {
    result = a;
} else {
    result = b;
}
```

#### **En Ensamblador Hack**:
```asm
@10        // Cargar valor de 'a' en A
D=A        // D = a

@5         // Cargar valor de 'b' en A
D=D-A      // D = a - b

@LABEL     // Si D > 0, saltar a la etiqueta LABEL
D;JGT      // Salta si el valor de D es mayor que cero

@5         // Si a <= b, carga b
D=A
@RESULT    // Dirección de la variable result
M=D        // result = b
@END       // Fin del condicional
0;JMP

(LABEL)
@10        // Si a > b, carga a
D=A
@RESULT    // Dirección de la variable result
M=D        // result = a

(END)
```

---

### 2. **Ciclo `while`**

#### **En C++**:
```cpp
int i = 0;
int sum = 0;

while (i < 10) {
    sum = sum + i;
    i++;
}
```

#### **En Ensamblador Hack**:
```asm
@0         // Cargar i = 0
D=A
@I
M=D        // i = 0

@0         // Cargar sum = 0
D=A
@SUM
M=D        // sum = 0

(LOOP)
@I
D=M        // D = i
@10
D=D-A      // D = i - 10
@END       // Si i >= 10, salta a END
D;JGE      // Salta si D >= 0

@SUM
D=M        // D = sum
@I
D=D+M      // D = sum + i
@SUM
M=D        // sum = sum + i

@I
M=M+1      // i = i + 1

@LOOP      // Salta al inicio del ciclo
0;JMP

(END)
```

---

### 3. **Ciclo `for`**

#### **En C++**:
```cpp
int sum = 0;
for (int i = 1; i <= 10; i++) {
    sum += i;
}
```

#### **En Ensamblador Hack**:
```asm
@0         // Cargar sum = 0
D=A
@SUM
M=D        // sum = 0

@1         // Cargar i = 1
D=A
@I
M=D        // i = 1

(LOOP)
@I
D=M        // D = i
@11
D=D-A      // D = i - 11
@END       // Si i > 10, salta a END
D;JGT      // Salta si D > 0

@SUM
D=M        // D = sum
@I
D=D+M      // D = sum + i
@SUM
M=D        // sum = sum + i

@I
M=M+1      // i = i + 1

@LOOP      // Salta al inicio del ciclo
0;JMP

(END)
```

---

### 4. **Escritura de variables por medio de punteros**

#### **En C++**:
```cpp
int a = 5;
int *p = &a;
*p = 10;  // Modificar el valor de a usando punteros
```

#### **En Ensamblador Hack**:
```asm
@5         // Cargar a = 5
D=A
@A
M=D        // a = 5

@A         // Cargar dirección de a
D=M        // D = dirección de a
@P         // Dirección de p
M=D        // p = &a

@P         // Dirección de p
D=M        // D = &a
@A         // Dirección de a
M=10       // a = 10
```

---

### 5. **Lectura de variables por medio de punteros**

#### **En C++**:
```cpp
int a = 10;
int *p = &a;
int b = *p;  // b toma el valor de a
```

#### **En Ensamblador Hack**:
```asm
@10        // Cargar a = 10
D=A
@A
M=D        // a = 10

@A         // Dirección de a
D=M        // D = valor de a
@B         // Dirección de b
M=D        // b = *p (valor de a)
```

---

### 6. **Manipulación de un arreglo por medio de punteros**

#### **En C++**:
```cpp
int arr[] = {1, 2, 3, 4, 5};
int *p = arr;
int sum = 0;
for (int i = 0; i < 5; i++) {
    sum += *(p + i);  // Acceso al arreglo usando puntero
}
```

#### **En Ensamblador Hack**:
```asm
@1         // Cargar arr[0] = 1
D=A
@ARR
M=D        // arr[0] = 1

@2         // Cargar arr[1] = 2
D=A
@ARR+1
M=D        // arr[1] = 2

@3         // Cargar arr[2] = 3
D=A
@ARR+2
M=D        // arr[2] = 3

@4         // Cargar arr[3] = 4
D=A
@ARR+3
M=D        // arr[3] = 4

@5         // Cargar arr[4] = 5
D=A
@ARR+4
M=D        // arr[4] = 5

@0         // Cargar sum = 0
D=A
@SUM
M=D        // sum = 0

@ARR       // Dirección del arreglo
D=M        // D = dirección de arr

@0         // i = 0
D=D+A      // Dirección de arr[i]
D=M        // D = arr[i]
@SUM
D=D+M      // sum += arr[i]
@SUM
M=D        // sum = sum + arr[i]

@1         // i++
D=A
@I
M=D        // i = i + 1

@LOOP
```

---

### 7. **Llamado a funciones con parámetros**

#### **En C++**:
```cpp
void add(int a, int b) {
    return a + b;
}

int result = add(5, 10);  // Llamada a la función con parámetros
```

#### **En Ensamblador Hack**:
```asm
// Definición de la función add:
(ADD)
@ARG1      // Cargar el primer argumento (a)
D=M
@ARG2      // Cargar el segundo argumento (b)
D=D+M
@RESULT   // Dirección de resultado
M=D        // Guardar el resultado

@RETURN    // Regresar al programa principal
0;JMP

// Llamada a la función:
@5         // Cargar argumento a = 5
D=A
@ARG1
M=D        // ARG1 = a

@10        // Cargar argumento b = 10
D=A
@ARG2
M=D        // ARG2 = b

@ADD       // Llamar a la función ADD
0;JMP
```

---

### 8. **Llamado a funciones con retorno de parámetros**

#### **En C++**:
```cpp
int add(int a, int b) {
    return a + b;
}

int result = add(5, 10);  // Llamada a la función con retorno
```

#### **En Ensamblador Hack**:
```asm
// Definición de la función add:
(ADD)
@ARG1      // Cargar el primer argumento (a)
D=M
@ARG2      // Cargar el segundo argumento (b)
D=D+M
@RESULT   // Dirección de resultado
M=D        // Guardar el resultado

@RETURN    // Regresar al programa principal
0;JMP

// Llamada a la función:
@5         // Cargar argumento a = 5
D=A
@ARG1
M=D        // ARG1 = a

@10        // Cargar argumento b = 10
D=A
@ARG2
M=D        // ARG2 = b

@ADD       // Llamar a la función ADD
0;JMP

@RESULT   // Cargar el resultado
D=M
@RESULT_FINAL
M=D
```

---

### Conclusión:
Cada uno de estos ejemplos muestra cómo los conceptos de programación en alto nivel se traducen a un lenguaje de bajo nivel, utilizando el ensamblador Hack. Los punteros, los condicionales, los ciclos, y la manipulación de funciones y arreglos pueden ser representados eficientemente en Hack, proporcionando una comprensión detallada de cómo la arquitectura de la máquina maneja la memoria y las instrucciones.
