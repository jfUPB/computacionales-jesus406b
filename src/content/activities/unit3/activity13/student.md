####TEST


**Ejemplo: Sistema de gestión de sensores**

Supongamos que estamos construyendo un programa para gestionar sensores de temperatura. Cada sensor puede activarse, registrar una lectura, y mostrar su historial. Además, hay una clase que lleva un conteo estático del total de sensores creados.



**Código fuente (C++)**

```cpp
#include <iostream>
#include <vector>

using namespace std;

class Sensor {
private:
    int id;
    vector<float> lecturas;
    static int contadorSensores;

public:
    Sensor(int id_) : id(id_) {
        contadorSensores++;
        cout << "Constructor: Sensor " << id << " creado.\n";
    }

    ~Sensor() {
        cout << "Destructor: Sensor " << id << " eliminado.\n";
        contadorSensores--;
    }

    void registrarLectura(float lectura) {
        lecturas.push_back(lectura);
    }

    void mostrarLecturas() const {
        cout << "Lecturas del Sensor " << id << ": ";
        for (float l : lecturas)
            cout << l << " ";
        cout << "\n";
    }

    static int obtenerContadorSensores() {
        return contadorSensores;
    }
};

int Sensor::contadorSensores = 0;

void modificarPorValor(int x) {
    x = 100;
}

void modificarPorReferencia(int &x) {
    x = 100;
}

int main() {
    // Stack
    Sensor sensor1(1); 

    // Heap
    Sensor* sensor2 = new Sensor(2);

    sensor1.registrarLectura(21.5);
    sensor1.registrarLectura(22.3);
    sensor2->registrarLectura(23.1);

    sensor1.mostrarLecturas();
    sensor2->mostrarLecturas();

    cout << "Total sensores activos: " << Sensor::obtenerContadorSensores() << endl;

    // Parámetro por valor y por referencia
    int variable = 10;
    modificarPorValor(variable);      // No cambia
    cout << "Después de modificarPorValor: " << variable << endl;

    modificarPorReferencia(variable); // Cambia a 100
    cout << "Después de modificarPorReferencia: " << variable << endl;

    delete sensor2;

    cout << "Total sensores activos: " << Sensor::obtenerContadorSensores() << endl;

    return 0;
}
```



**Explicación de conceptos aplicados**

| Concepto                         | Aplicación                                                                 |
|----------------------------------|----------------------------------------------------------------------------|
| **Clases y objetos**             | Se define la clase `Sensor` con métodos y atributos. Se crean objetos.    |
| **Paso por valor y referencia**  | Funciones `modificarPorValor` y `modificarPorReferencia` muestran diferencia. |
| **Constructores y destructores** | `Sensor(int)` y `~Sensor()` imprimen mensajes para seguir el ciclo de vida. |
| **Métodos y atributos**          | `registrarLectura`, `mostrarLecturas` y `obtenerContadorSensores` son métodos; `id` y `lecturas` son atributos. |
| **Stack y Heap**                 | `sensor1` está en el stack, `sensor2` se crea dinámicamente en el heap con `new`. |
| **Punteros y referencias**       | Uso de punteros (`sensor2`) y referencias (`int &x`).                       |
| **Variables estáticas**         | `contadorSensores` es estático y compartido por todos los objetos `Sensor`. |
| **Depuración**                   | Se puede seguir la ejecución con `cout`, útil para depurar creación y destrucción. |



**Análisis detallado de la memoria**

| Elemento                         | Segmento de Memoria      | Descripción                                                                 |
|----------------------------------|---------------------------|------------------------------------------------------------------------------|
| `sensor1`                        | **Stack**                 | Variable local automática, se destruye al salir del `main`.                |
| `sensor2`                        | **Heap**                  | Almacenado dinámicamente, debe liberarse manualmente con `delete`.         |
| `contadorSensores`              | **Segmento de datos**     | Variable estática, permanece en memoria durante toda la ejecución.         |
| `lecturas`                       | **Heap**                  | Vector dinámico, gestiona internamente memoria en heap.                    |
| `id`                             | **Stack/Heap**            | Miembro de clase, vive en stack si el objeto está en stack, o en heap si no. |
| Parámetros de funciones (`x`)    | **Stack**                 | Variables locales dentro del stack frame de la función.                    |

