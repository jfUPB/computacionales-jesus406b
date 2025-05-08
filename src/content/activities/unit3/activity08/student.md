####TEST
Capturas y Comparaciones de Dirección de Memoria

**En el depurador:**
- Coloca breakpoints justo después de:

 ![image](https://github.com/user-attachments/assets/31b8cd0e-05f0-42a4-a6af-de435e8531a3)


**Observamos en la pestaña Locals:**
- `pStack`: verás algo como `0x00ffd4b0` (es un valor de ejemplo). Esta dirección es **una ubicación en el stack.**
- `pHeap`: verás algo como `0x00fa3000` (ejemplo), que **es una dirección en el heap** donde está almacenado el objeto creado con `new`.



Explicación de Stack vs Heap

Stack:
- Manejado automáticamente.
- Memoria rápida de asignar y liberar.
- Vida útil limitada al bloque donde se declaró.
- En el ejemplo, `pStack` es **un objeto completo**, al que accedes directamente (`pStack.imprimir()`).

 Heap:
- Memoria dinámica: tú decides cuándo crear y liberar.
- Más flexible pero más lenta.
- Necesita `new` y `delete`.
- En el ejemplo, `pHeap` es **un puntero** que **apunta** a un objeto creado dinámicamente. Lo accedes con `->`.

---

¿Qué son pStack y pHeap?

| Variable   | ¿Es un objeto? | ¿Es una referencia/puntero? | ¿A qué hace referencia?                         |
|------------|----------------|-----------------------------|--------------------------------------------------|
| `pStack`   | Sí          |     No                       | Es el objeto en sí, en el stack.                |
| `pHeap`    | No          |     Sí (puntero)             | Apunta a un objeto `Punto` en el heap.          |

---

Explorando `Memory1` en Visual Studio

1. En el depurador, ve a `Debug > Windows > Memory > Memory1`.
2. En la barra de dirección, se escribe:  
   ```
   &pHeap
   ```
   Presiona Enter.

3. Verás:
   - En esa dirección está el contenido de la variable `pHeap`, que es la **dirección real del objeto** en el heap.
   Se puede comparar este contenido con la dirección de `pHeap` que aparece en la pestaña **Locals**.

¿Qué significa eso?

Estamos viendo cómo el puntero `pHeap` contiene la dirección del objeto en memoria dinámica. Ese número hexadecimal (por ejemplo, `0x00fa3000`) **es la dirección física** del objeto en el heap, y es diferente a la dirección de `pStack` en el stack.

Conclusión

Este ejercicio demuestra:

- La **vida, dirección y acceso** a objetos en stack vs heap.
- Que `pStack` es un objeto real en stack, y `pHeap` es un puntero que apunta a un objeto en el heap.
- La importancia de liberar la memoria con `delete` para evitar fugas.



