#### TEST

### Código relevante:

```cpp
// Variables globales
int global_inicializada = 42;          // Segmento de datos (.data)
int global_no_inicializada;            // Segmento BSS (.bss)
```

Y dentro de `main()`:
```cpp
cout << "global_inicializada: " << global_inicializada << endl;
cout << "global_no_inicializada: " << global_no_inicializada << endl;

global_inicializada = 69;
global_no_inicializada = 666;
```

 ¿Qué ocurre y por qué?

- `global_inicializada` se almacena en el **segmento .data**, que es para variables **globales o estáticas inicializadas**.
- `global_no_inicializada` se almacena en el **segmento .bss**, que es para variables **globales o estáticas NO inicializadas**. El sistema las inicializa automáticamente en cero.

 Resultado al ejecutar:

Primera vez:
```
global_inicializada: 42
global_no_inicializada: 0
```

Después de modificar:
```
global_inicializada: 69
global_no_inicializada: 666
```

 Conclusión:

Puedes leer y modificar variables globales desde cualquier parte del programa (si tienes acceso a su scope), porque viven en un segmento de memoria accesible durante **toda la ejecución del programa**.

---

 **Experimento 4: Modificar la variable local estática de una función por fuera de ella**

### Código:

```cpp
void funcionConStatic() {
    static int var_estatica = 100;
    cout << "Dirección de var_estatica (static): " << &var_estatica << endl;
}

int main() {
    var_estatica = 42; // <-- ¡Esto genera un error!
}
```

 ¿Qué ocurre y por qué?

El compilador marca un **error**:

```
error: 'var_estatica' was not declared in this scope
```

 ¿Por qué?

- `var_estatica` es una variable **local estática** de la función `funcionConStatic`.
- Las variables locales estáticas **persisten** entre llamadas, pero **no son visibles fuera de la función donde fueron declaradas** (tienen **duración estática**, pero **alcance local**).

 ¿Qué pasa al entrar y salir de la función?

- Una **variable local normal** se crea cada vez que entras y se destruye al salir de la función (está en la **pila / stack**).
- Una **variable local `static`** se inicializa una sola vez y **conserva su valor entre llamadas**, pero sigue siendo inaccesible desde fuera.

### Ejemplo funcional:

```cpp
void funcionConStatic() {
    static int var_estatica = 100;
    cout << "Valor: " << var_estatica << endl;
    var_estatica++;
}
```

Cada llamada a `funcionConStatic()` imprimirá un valor que va incrementando.

---

 Resumen:

| Tipo de Variable                 | Vida                | Visibilidad               | Segmento de Memoria |
|----------------------------------|----------------------|----------------------------|----------------------|
| Local normal                     | Mientras la función | Solo dentro de su función | Stack                |
| Global                           | Todo el programa     | Global                    | .data / .bss         |
| Local `static`                   | Todo el programa     | Solo dentro de su función | .data / .bss         |

