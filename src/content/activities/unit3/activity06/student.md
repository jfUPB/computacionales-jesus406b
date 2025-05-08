####TEST

**Experimento 5: Variables locales estáticas vs no estáticas**

Código relevante:
```cpp
void funcionSinStatic() {
    int var_no_estatica = 100;
    cout << "var_no_estatica: " << var_no_estatica << endl;
    var_no_estatica++;
}

void funcionConStatic() {
    static int var_estatica = 100;
    cout << "var_estatica: " << var_estatica << endl;
    var_estatica++;
}
```

Y dentro del `main()`:
```cpp
for (int i = 0; i < 5; i++) {
    cout << "Iteración " << i << endl;
    funcionSinStatic();
    funcionConStatic();
}
```

---

¿Qué ocurre?

Cada vez que se ejecuta el bucle, se llaman las dos funciones:

#### En `funcionSinStatic()`:
- `var_no_estatica` se crea **cada vez que se entra a la función**.
- Se inicializa en `100` SIEMPRE.
- Se imprime `100`, luego se incrementa a `101`, pero esa nueva versión **se pierde** porque se destruye al salir de la función.

#### En `funcionConStatic()`:
- `var_estatica` se inicializa **solo una vez**, la **primera vez que se entra** a la función.
- Se mantiene viva entre llamadas (memoria estática, no stack).
- Se incrementa en cada llamada.

---

Resultado esperado:

```
Iteración 0
var_no_estatica: 100
var_estatica: 100
Iteración 1
var_no_estatica: 100
var_estatica: 101
Iteración 2
var_no_estatica: 100
var_estatica: 102
Iteración 3
var_no_estatica: 100
var_estatica: 103
Iteración 4
var_no_estatica: 100
var_estatica: 104
```

---

Conclusión:

| Tipo de variable    | Vida                  | Valor se conserva | Dónde vive  |
|---------------------|------------------------|--------------------|--------------|
| Local no estática   | Solo mientras la función corre | ❌ No             | Stack        |
| Local estática      | Durante todo el programa       | ✅ Sí             | Segmento .data/.bss |

---

**Experimento 6: Modificar el segmento de Heap**

Código relevante:
```cpp
int* arrayHeap = new int[tam];  // memoria dinámica (heap)

...

delete[] arrayHeap;

cout << arrayHeap[0] << endl;   // ← problema aquí
```

---

¿Qué ocurre?

Después de ejecutar `delete[] arrayHeap;`, la memoria es **liberada**, pero el puntero `arrayHeap` **sigue apuntando a esa dirección**, aunque ya no te pertenece.

**Leer de ella puede causar un comportamiento indefinido.** A veces parecerá funcionar, otras causará errores o resultados basura.

---

Comenta esa línea:

```cpp
// cout << arrayHeap[0] << endl;  // ← Esta línea debe comentarse
```

---

Preguntas clave:

¿Diferencias entre Heap y Stack?

| Característica      | Heap                          | Stack                         |
|----------------------|-------------------------------|-------------------------------|
| Asignación           | Manual (`new`, `malloc`)      | Automática                    |
| Liberación           | Manual (`delete`, `free`)     | Automática (al salir del scope) |
| Tiempo de vida       | Hasta que tú lo liberes       | Solo dentro del scope         |
| Uso típico           | Arreglos grandes, estructuras compartidas | Variables locales pequeñas    |

---

¿Qué pasa si no usas `delete[]`?

- Fugas de memoria (memory leaks).
- Aumenta el uso de RAM.
- En programas largos o con bucles, puede hacer que el sistema se quede sin memoria.

---

¿Por qué usar `delete[]` en vez de `delete`?

- `delete[]` libera memoria asignada con `new[]`.
- `delete` se usa con memoria asignada con `new`.

Ejemplo:
```cpp
int* p = new int[5];    // ← se usa delete[]
int* q = new int;       // ← se usa delete
```

Usar `delete` en lugar de `delete[]` con arreglos puede causar **fallos de memoria** y **comportamiento indefinido**, porque no se llama correctamente al destructor de cada elemento del arreglo.

---

 Conclusión 

- Usa `static` si necesitas **conservar el estado** de una variable entre llamadas.
- El heap te da control sobre la memoria, pero **tú eres responsable** de liberarla.
- Siempre usa `delete[]` para arreglos dinámicos creados con `new[]`.

---

