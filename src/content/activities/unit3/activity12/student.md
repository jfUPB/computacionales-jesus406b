####TEST


**Ciclo de vida del objeto en el stack vs. heap**

Caso 1: Objeto en el **stack**

```cpp
{
    Punto pBloque(100, 200);
    pBloque.imprimir();
}
```

- El objeto `pBloque` se **crea en el stack** al entrar en el bloque `{}`.
- El constructor se invoca inmediatamente.
- Al salir del bloque, el objeto `pBloque` **sale del ámbito** y el **destructor se invoca automáticamente**, liberando la memoria asociada.

Esto ocurre porque las variables locales (no dinámicas) viven en el stack y **su ciclo de vida está ligado al bloque donde se declaran**.

---

Caso 2: Objeto en el **heap**

```cpp
Punto* pDinamico = new Punto(300, 400);
pDinamico->imprimir();
// ...
delete pDinamico;
```

- `pDinamico` es un **puntero almacenado en el stack**, pero apunta a un objeto creado en el **heap** con `new`.
- El objeto creado dinámicamente **no se destruye automáticamente** al salir del bloque.
- Debes llamar explícitamente a `delete` para liberar esa memoria, lo cual también invoca el **destructor**.

---

¿Compila esta versión?

```cpp
{
    Punto* pBloque2 = new Punto(500, 600);
    pBloque2->imprimir();
}
pBloque2->imprimir(); //
delete pBloque2;
```

**No compila.**  
Porque `pBloque2` fue declarado dentro del bloque `{}` y **no existe fuera de ese bloque**. Al intentar usarlo afuera, obtienes un **error de "identificador no declarado"**.

---

Versión modificada (válida):

```cpp
Punto* pBloque2 = nullptr;
{
    pBloque2 = new Punto(500, 600);
    pBloque2->imprimir();
}
pBloque2->imprimir();
delete pBloque2;

```

- Aquí `pBloque2` se **declara en el `main()`**, por lo que está accesible en todo el `main`.
- Dentro del bloque, se **inicializa con `new`**, creando un objeto en el heap.
- El objeto **sigue existiendo incluso al salir del bloque**, porque está en el **heap**, y sólo se elimina al hacer `delete`.



¿Por qué `pBloque` se destruye al salir del bloque pero `pBloque2` no?

- `pBloque` es un **objeto en el stack**. Al salir del bloque, su **destructor se llama automáticamente**.
- `pBloque2` es un **puntero en el stack** que apunta a un objeto en el **heap**. Al salir del bloque, **el puntero sigue existiendo** (porque fue declarado fuera) y el objeto en el heap también, **hasta que llames explícitamente a `delete`**.


¿Dónde se almacenan `pBloque2` y el objeto al que apunta?

- `pBloque2`: en el **stack**, porque es una variable local del `main()`.
- Objeto al que apunta (`new Punto(...)`): en el **heap**, porque fue creado con `new`.



Conclusión

| Aspecto              | Stack                              | Heap                              |
|----------------------|-------------------------------------|------------------------------------|
| Tiempo de vida       | Automático (ligado al bloque)       | Manual (hasta que se haga `delete`) |
| Ubicación            | Memoria de stack                    | Memoria dinámica (heap)            |
| Destructor           | Se invoca automáticamente           | Se invoca con `delete`             |
| Accesibilidad        | Sólo dentro del bloque              | Mientras el puntero exista         |

