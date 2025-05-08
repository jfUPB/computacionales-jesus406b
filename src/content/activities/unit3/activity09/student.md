Comparación de la copia de objetos en C++ y C#



**C++**

Comportamiento del programa:
En C++, cuando se hace una copia como:

```cpp
Punto copia = original;
```

Se llama al **constructor de copia por defecto** (implícito si no está definido). Esto crea un **nuevo objeto independiente** en memoria, con los mismos valores que `original`.

Luego, al modificar `copia`:

```cpp
copia.name = "copia";
copia.x = 100;
copia.y = 200;
```

el objeto `original` **no se ve afectado**. Eso demuestra que `copia` es **una copia profunda (deep copy)** en cuanto a los datos simples (valores primitivos como `int` y `string` en este contexto).

Pero atención: si la clase tuviera punteros dinámicos o recursos del sistema (memoria, archivos, etc.), **deberías implementar manualmente el constructor de copia, el operador de asignación y el destructor (la "regla de tres")** para evitar errores como "shallow copy".

Luego, se modifica el puntero `p` que apunta a `original`:

```cpp
Punto* p = &original;
p->x = 300;
```

Esto **sí modifica a `original`**, porque `p` apunta al mismo objeto.

---

Conclusión en C++:

- `copia = original` → crea un **objeto nuevo**, independiente (deep copy para tipos simples).
- Cambios en `copia` **no afectan a `original`**.
- Si se usa un puntero, como `p = &original`, entonces **se modifica el objeto original**.

---

**C#**

### Comportamiento del programa:
En C#, cuando haces:

```csharp
Punto copia = original;
```

**NO se crea un nuevo objeto**, sino que `copia` **referencia al mismo objeto** que `original`. Es decir, se realiza una **copia por referencia**.

Por eso, al hacer:

```csharp
copia.name = "copia";
copia.x = 100;
```

estás **modificando el mismo objeto** al que `original` apunta. Por tanto, `original` **también refleja esos cambios**.

### ¿Por qué pasa esto?
Porque en C#, las **clases son tipos por referencia**. Si quieres una copia real e independiente del objeto, debes hacerlo manualmente (ej. implementando una interfaz como `ICloneable`, o escribiendo un método de clonación).



Conclusión en C#:

- `copia = original` → **ambas variables apuntan al mismo objeto en memoria**.
- Cambios en `copia` **sí afectan a `original`**.
- Para tener una copia independiente, se requiere un **método de clonación manual**.



Comparación directa

| Aspecto                   | C++                               | C#                                    |
|---------------------------|------------------------------------|----------------------------------------|
| Tipo de copia por defecto | Copia por valor (deep para simples) | Copia por referencia                   |
| ¿Modifica al original?    | No                                 | Sí                                     |
| Objeto nuevo en memoria   | Sí                                 | No (es la misma referencia)            |
| Requiere clonación manual | Solo si hay punteros o recursos    | Sí, siempre, si quieres copia real     |
| Clase por defecto         | Tipo por valor                     | Tipo por referencia                    |

