####TEST

Aqui esta  el código para implementar las tres versiones de la función swap:


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
