####TEST

**VERIFICACION DE QUE EL CODIGO S EEJECUTO CORRECTAMENTE**
![act1](https://github.com/user-attachments/assets/21b451b9-2c06-482a-bb70-1b8a1dd5d82a)

![act1 2](https://github.com/user-attachments/assets/be7c4e02-f721-401f-bdec-f4484b337ae8)


Claro, aquí tienes un resumen de la explicación sobre las opciones de depuración en Visual Studio, usando el ejemplo de `int a = 10;` y `int b = 7;`.

### Opciones de Depuración:

1. **F5 (Iniciar/Reanudar ejecución)**: Inicia o reanuda la ejecución del programa hasta el siguiente breakpoint o el final. Es útil para continuar después de una pausa.
   
2. **F10 (Ejecutar siguiente línea - Step Over)**: Ejecuta la siguiente línea sin entrar en funciones. Útil cuando no deseas ver el interior de una función.

3. **F11 (Entrar en la función - Step Into)**: Ejecuta la siguiente línea y entra en las funciones llamadas. Te permite ver la ejecución dentro de la función.

4. **Shift + F5 (Detener ejecución)**: Detiene el programa de inmediato. Útil si necesitas detener la depuración.

5. **Ctrl + F5 (Ejecutar sin depuración)**: Ejecuta el programa normalmente, sin pausas ni breakpoints.

6. **Ventana Autos**: Muestra las variables locales y sus valores, actualizándose según el punto de ejecución.

7. **Ventana Locals**: Muestra todas las variables locales en el contexto actual, proporcionando una visión completa.

8. **Ventana Watch**: Te permite monitorear variables específicas o expresiones durante la ejecución.

9. **Call Stack**: Muestra la pila de llamadas, es decir, las funciones que han sido llamadas hasta el punto actual de ejecución.

### Ejemplo con el código:

```cpp
#include <iostream>

int sum(int a, int b)
{
    return a + b;
}

int main()
{
    int a = 10;
    int b = 7;
    std::cout << "La suma de " << a << " y " << b << " es " << sum(a, b) << "\n";
}
```

1. Coloca un **breakpoint** en `int a = 10;`.
2. Usa **F5** para iniciar la ejecución hasta el breakpoint.
3. Usa **F10** para ejecutar línea por línea sin entrar en funciones. 
4. Usa **F11** para entrar en la función `sum` y ver cómo se ejecuta.
5. Observa las variables en **Autos** y **Locals**.

Estas herramientas son esenciales para depurar y entender cómo se ejecuta tu código.



**VERIFICACION DE QUE EL CODIGO  DE EJEMPLO SE EJECUTO CORRECTAMENTE**
![act1 3](https://github.com/user-attachments/assets/662fb7b5-1d0b-40d3-b34c-519ea4c55444)
![act1 4](https://github.com/user-attachments/assets/f08c4631-eb7a-49d5-9f77-f1abf5d7d20b)

