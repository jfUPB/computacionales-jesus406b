####TEST

####  ¿Cómo se crea la lista enlazada?

La lista se declara en el archivo `ofApp.h` como:

```cpp
std::list<glm::vec2> snake;
```

Esto crea una **lista enlazada (doblemente enlazada)** de elementos `glm::vec2` (posiciones 2D) usando la biblioteca estándar de C++ (`<list>`).

---

####  ¿Cómo se añaden los primeros nodos a la lista?

En el método `setup()` de `ofApp.cpp`:

```cpp
for (int i = 0; i < 20; i++) {
    snake.emplace_back(ofGetWidth() / 2, ofGetHeight() / 2);
}
```

Esto añade 20 nodos **en el centro de la ventana**, usando `emplace_back`, que agrega cada nodo al **final** de la lista.

---

####  ¿Cómo se añaden nodos adicionales a la lista?

Cuando el usuario presiona la tecla **'a'**, se ejecuta este código en `keyPressed()`:

```cpp
else if (key == 'a') {
    snake.emplace_back(ofRandomWidth(), ofRandomHeight());
}
```

Esto agrega un nuevo nodo con **posición aleatoria** al final de la lista.

---

####  ¿Cómo se eliminan nodos de la lista?

Cuando se presiona la tecla **'r'**, se elimina el último nodo:

```cpp
else if (key == 'r') {
    if (!snake.empty()) {
        snake.pop_back();
    }
}
```

---

####  ¿Cómo se limpia la lista?

Cuando se presiona la tecla **'c'**, se elimina **todo el contenido de la lista**:

```cpp
if (key == 'c') {
    snake.clear();
}
```

---

####  ¿Cómo se verifica si la lista está vacía?

Antes de eliminar un nodo, el código comprueba si la lista **no está vacía**:

```cpp
if (!snake.empty()) {
    snake.pop_back();
}
```

Se usa el método `empty()` para verificar si la lista contiene elementos.

---


