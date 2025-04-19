####TEST
```asm
#include <iostream>
#include <vector>

// Definimos las dimensiones de la pantalla
const int SCREEN_WIDTH = 512;
const int SCREEN_HEIGHT = 256;
const int SCREEN_SIZE = 8192;  // 8,192 posiciones

// Definimos el arreglo de pantalla y el teclado
std::vector<int> SCREEN(SCREEN_SIZE, 0);
int KBD = 0;  // Representa el valor del teclado (por ejemplo, una tecla presionada)

void execute_machine_code() {
    // Aquí se realizaría la simulación del programa de máquina
    // Basado en la interpretación de las instrucciones de la máquina
    
    // Ejemplo básico de asignaciones para mostrar el uso de variables
    SCREEN[0] = 1;  // Activar el primer "pixel" en la pantalla
    SCREEN[1] = 1;  // Activar el segundo "pixel" en la pantalla

    // Leer entrada del teclado (simulación)
    if (KBD != 0) {
        // Si se presiona una tecla, realizar alguna acción
        std::cout << "Tecla presionada: " << KBD << std::endl;
    }
    
    // Mostrar el estado de la pantalla (simplificado)
    for (int i = 0; i < SCREEN_SIZE; ++i) {
        if (SCREEN[i] == 1) {
            std::cout << "Píxel encendido en posición " << i << std::endl;
        }
    }
}

int main() {
    // Ejemplo de cómo podríamos simular la entrada de teclado y la pantalla
    KBD = 1;  // Simulamos que se presiona una tecla

    // Ejecutamos el código de máquina
    execute_machine_code();

    return 0;
}
```

**Explicación:**
SCREEN: Es un arreglo de 8,192 posiciones (cada posición representa 16 píxeles) que simula la pantalla. Cada valor en este arreglo podría ser 0 (apagado) o 1 (encendido).

KBD: Es la variable que representa la entrada del teclado. En este caso, la entrada del teclado se simula con un valor que puede cambiar según el código de máquina.

Función execute_machine_code: Esta función simula la ejecución del código de máquina. En este ejemplo básico, enciende algunos píxeles en la pantalla y muestra el valor del teclado si se presiona una tecla.
