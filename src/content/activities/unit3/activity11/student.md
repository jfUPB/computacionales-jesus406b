####TEST

**¿Qué puedes concluir de los miembros estáticos y de instancia de una clase en C++?**

- Los **miembros de instancia** (como `valor`) son únicos para cada objeto, y se almacenan en la memoria del objeto (stack o heap, según dónde se cree el objeto).
- Los **miembros estáticos** (como `total`) son compartidos por **todas las instancias** y se almacenan una sola vez en un área especial de memoria (segmento de datos estáticos).
- Permiten separar el comportamiento que depende del objeto del que es común a todos.

**¿Qué ventajas y desventajas tienen?**

**Ventajas:**
- Permiten compartir datos entre todas las instancias sin necesidad de pasarlos como parámetros.
- Útiles para implementar contadores globales, configuraciones comunes, o recursos compartidos.

**Desventajas:**
- No pueden acceder directamente a miembros de instancia.
- Pueden provocar errores si se usan incorrectamente en programas con múltiples hilos (problemas de concurrencia).

**¿Cuándo es útil usarlos?**
- Cuando necesitas un valor o función que sea común a todas las instancias, como un contador de objetos creados o una tabla de configuración compartida.

---

**¿En qué segmento de memoria se almacenan `c1`, `c2`, `c3` y `Contador::total`?**

- `c1` y `c2` están almacenados en el **stack**, ya que son objetos locales dentro de `main()`.
- `c3` está almacenado en el **stack**, pero **lo que almacena es una dirección**.
- El objeto al que apunta `c3` (creado con `new Contador(15)`) se encuentra en el **heap**.
- `Contador::total` está almacenado en el **segmento de datos estáticos**, ya que es un miembro estático de la clase y existe independientemente de las instancias.



