#### TEST


###  Reflexión 1: ¿Cómo se ve una lista enlazada con 3 nodos?

Una lista enlazada con 3 nodos se representa como una secuencia de nodos donde cada uno apunta al siguiente:

```
[Node1] → [Node2] → [Node3] → nullptr
```

* **Node1**: Contiene una posición (por ejemplo, `(x1, y1)`) y un puntero `next` que apunta a Node2.
* **Node2**: Contiene una posición `(x2, y2)` y `next` apuntando a Node3.
* **Node3**: Contiene una posición `(x3, y3)` y `next` apuntando a `nullptr`, indicando el final de la lista.

Si se agrega un cuarto nodo, Node4, se enlaza al final:

```
[Node1] → [Node2] → [Node3] → [Node4] → nullptr
```

---

###  Reflexión 2: ¿Cómo se ve un objeto de la clase `LinkedList` con 3 nodos?

El objeto `LinkedList` contiene:

* **head**: Apunta a Node1 (el primer nodo).
* **tail**: Apunta a Node3 (el último nodo).
* **size**: Tiene el valor 3.

Visualmente:

```
LinkedList
  ├── head → [Node1]
  ├── tail → [Node3]
  └── size = 3
```

---

###  Reflexión 3: ¿Qué pasaría si `LinkedList` no tuviera ciertos miembros?

* **Sin `head`**: No podrías acceder al inicio de la lista, lo que imposibilitaría recorrerla o realizar operaciones como inserciones al principio.
* **Sin `tail`**: Agregar nodos al final requeriría recorrer toda la lista para encontrar el último nodo, lo que sería ineficiente.
* **Sin `size`**: No podrías conocer directamente la cantidad de nodos, lo que dificultaría operaciones que dependen del tamaño de la lista.

---

###  Reflexión 4: ¿Por qué es necesario liberar la memoria de los nodos en el destructor?

En C++, la memoria asignada dinámicamente (usando `new`) no se libera automáticamente. Si no se libera explícitamente (usando `delete`), se producen **fugas de memoria**, lo que puede llevar a un consumo excesivo de memoria y posibles fallos del programa. El destructor de `LinkedList` llama a `clear()` para eliminar todos los nodos y liberar la memoria asociada.

---

###  Reflexión 5: ¿Por qué en C++ es necesario liberar la memoria manualmente?

C++ no cuenta con un recolector de basura como otros lenguajes (por ejemplo, C#). Por lo tanto, el programador es responsable de gestionar la memoria, asegurándose de liberar cualquier memoria asignada dinámicamente para evitar fugas y mantener el programa eficiente y estable.

---

###  Reflexión 6: ¿Qué hacen los métodos `setup()`, `update()`, `draw()` y `keyPressed()`?

* **`setup()`**: Inicializa la aplicación, en este caso, creando la serpiente con 20 nodos en el centro de la pantalla.
* **`update()`**: Actualiza la lógica de la aplicación. Aquí, cada nodo de la serpiente se interpola hacia la posición del mouse, creando un efecto de seguimiento.
* **`draw()`**: Renderiza la escena. Dibuja un fondo con un gradiente de color y la serpiente como una línea con círculos de colores que varían según la posición en la lista.
* **`keyPressed()`**: Maneja la entrada del teclado. Permite agregar (`'a'`), eliminar (`'r'`), borrar (`'c'`) nodos de la serpiente o guardar una imagen (`'s'`).

---

###  Reflexión 7: ¿Cómo funciona la interpolación con `glm::mix`?

La función `glm::mix(a, b, t)` realiza una interpolación lineal entre los vectores `a` y `b` con un factor `t` (entre 0 y 1). En el contexto de la serpiente:

```cpp
current->position = glm::mix(glm::vec3(current->position, 0.0f), glm::vec3(target, 0.0f), interpolationFactor);
```

Esto mueve gradualmente cada nodo hacia la posición del nodo anterior (o del mouse para el primer nodo), creando un efecto de movimiento suave y continuo.

---

###  Reflexión 8: ¿Cómo se ve la lista antes y después de `push_back()` y `pop_back()`?

* **`push_back()`**:

  * *Antes* (size = 2): `Node1 → Node2 → nullptr`
  * *Después* (size = 3): `Node1 → Node2 → Node3 → nullptr`

* **`pop_back()`**:

  * *Antes* (size = 3): `Node1 → Node2 → Node3 → nullptr`
  * *Después* (size = 2): `Node1 → Node2 → nullptr`

Estas operaciones modifican la estructura de la lista y actualizan los punteros `head`, `tail` y el valor de `size` en consecuencia.

---

###  Reflexión 9: ¿Qué hace `clear()`?

El método `clear()` recorre la lista desde `head`, eliminando cada nodo y liberando su memoria. Al final, establece `head` y `tail` en `nullptr` y `size` en 0, dejando la lista vacía y lista para ser reutilizada sin residuos de memoria.

---

