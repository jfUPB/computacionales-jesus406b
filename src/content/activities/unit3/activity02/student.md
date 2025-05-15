####TEST

Aqui esta  el código para implementar las tres versiones de la función swap:

```cpp
#include <iostream>
using namespace std;

// Swap por valor
void swapPorValor(int a, int b) {
    int temp = a;
    a = b;
    b = temp;
    cout << "Dentro de swapPorValor: x = " << a << ", y = " << b << endl;
}

// Swap por referencia
void swapPorReferencia(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
    cout << "Dentro de swapPorReferencia: x = " << a << ", y = " << b << endl;
}

// Swap por puntero
void swapPorPuntero(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
    cout << "Dentro de swapPorPuntero: x = " << *a << ", y = " << *b << endl;
}

int main() {
    int x = 5, y = 10;

    // Mostrar valores iniciales
    cout << "Valor inicial de x = " << x << ", y = " << y << endl;

    // Llamada a swapPorValor (no modifica los valores originales)
    swapPorValor(x, y);
    cout << "Después de swapPorValor: x = " << x << ", y = " << y << endl;

    // Restaurar valores originales
    x = 5; y = 10;

    // Llamada a swapPorReferencia (modifica los valores originales)
    swapPorReferencia(x, y);
    cout << "Después de swapPorReferencia: x = " << x << ", y = " << y << endl;

    // Restaurar valores originales
    x = 5; y = 10;

    // Llamada a swapPorPuntero (modifica los valores originales)
    swapPorPuntero(&x, &y);
    cout << "Después de swapPorPuntero: x = " << x << ", y = " << y << endl;

    return 0;
}
```

**Respuestas a las preguntas planteadas:**

**¿Por qué la versión de swapPorValor no logra intercambiar los valores de x e y en main()?**

**RTA:** Porque en swapPorValor, los parámetros se pasan por valor. Esto significa que solo se intercambian las copias locales de x e y, y no las variables originales en main().

**¿Cómo y por qué logran las otras dos funciones (por referencia y por puntero) modificar las variables originales?**

**RTA:** En swapPorReferencia, los parámetros se pasan por referencia, lo que permite que los cambios en las variables dentro de la función afecten directamente a las variables originales en main().

En swapPorPuntero, los parámetros se pasan como punteros, lo que permite modificar las variables originales a través de sus direcciones de memoria.

**¿Cuáles son las ventajas y consideraciones de usar referencias versus punteros en este caso?**

**RTA:** Las referencias son más fáciles de usar y comprender, y se evitan errores relacionados con punteros nulos o dereferenciación.

Los punteros proporcionan más flexibilidad, especialmente cuando es necesario manipular direcciones de memoria y trabajar con estructuras de datos dinámicas.
