####TEST

¿Qué ocurre después de llamar a la función `cambiarNombre(original, "cambiado")`?

El programa imprime:

```
Constructor: Punto original (70, 80) creado.
Punto original(70, 80)
Destructor: Punto cambiado(70, 80) destruido.
Punto original(70, 80)
```

El objeto **original** no cambia de nombre. La función **cambiarNombre** toma un **objeto por valor**, por lo que **se hace una copia del objeto original**. Esa copia recibe el nuevo nombre `"cambiado"`, pero **solo afecta a la copia**, no al original.



¿Por qué aparece el mensaje `Destructor: Punto cambiado(70, 80) destruido.`?

Porque el objeto `p` dentro de la función `cambiarNombre` es una **copia** del objeto original. Cuando la función termina, la copia se destruye, y el destructor se ejecuta para ese objeto (copia), no para el original.



¿Por qué `original` sigue existiendo luego de llamar a `cambiarNombre`?

Porque `original` está en el **`main()`**, fuera del alcance de la función `cambiarNombre`. Como no se modificó directamente, sigue intacto. Solo se modificó la **copia local** dentro de `cambiarNombre`.



¿En qué parte del mapa de memoria se encuentra `original` y en qué parte `p`?

- `original`: está en el **stack**, dentro del contexto de `main()`.
- `p`: está en el **stack** también, pero dentro del contexto de la función `cambiarNombre`.

No son el mismo objeto. `p` es una **copia**, no una referencia ni puntero.



Modificación: Paso por Referencia

```cpp
void cambiarNombre(Punto& p, string nuevoNombre) {
	p.name = nuevoNombre;
}
```

Ahora `p` **ya no es una copia**, sino una **referencia al objeto original**.

Resultado al ejecutar:

```
Constructor: Punto original (70, 80) creado.
Punto original(70, 80)
Punto cambiado(70, 80)
Destructor: Punto cambiado(70, 80) destruido.
```

Ahora sí se cambió el nombre a `"cambiado"` en el objeto original. Como `p` es una referencia, actúa **directamente sobre `original`**.



Modificación: Paso por Puntero

```cpp
void cambiarNombre(Punto* p, string nuevoNombre) {
	p->name = nuevoNombre;
}
```

Y en `main()` se llama así:

```cpp
cambiarNombre(&original, "cambiado");
```

Resultado al ejecutar:

```
Constructor: Punto original (70, 80) creado.
Punto original(70, 80)
Punto cambiado(70, 80)
Destructor: Punto cambiado(70, 80) destruido.
```

También se modifica el objeto original, porque estamos pasando la **dirección de memoria del objeto (`&original`)**. La función usa esa dirección para modificar directamente los atributos.



Diferencias entre pasar por Valor, Referencia y Puntero:

| Forma de paso     | ¿Se modifica el original? | ¿Se crea copia? | Sintaxis |
|-------------------|----------------------------|------------------|----------|
| Por valor         |  No                     |    Sí           | `f(Punto p)` |
| Por referencia    |  Sí                     |    No           | `f(Punto& p)` |
| Por puntero       |  Sí                     |    No           | `f(Punto* p)` y se pasa `&obj` |

Consejo práctico:

- Usa **por valor** si no necesitas modificar el objeto y el objeto es pequeño.
- Usa **por referencia o puntero** si quieres modificar el objeto o evitar el costo de copia (especialmente con objetos grandes).



