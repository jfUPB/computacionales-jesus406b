**Experimento 1: Modificar el Segmento de Código** 

Código relevante:

```asm
void* ptr = reinterpret_cast<void*>(&main);
cout << "Voy a modificar la memoria en la dirección: " << ptr << endl;
*reinterpret_cast<int*>(ptr) = 0;
```

**¿Qué ocurre?**
Al ejecutar este experimento, el programa generalmente se bloquea o lanza una excepción de violación de acceso (segmentation fault o access violation).

Algunos sistemas pueden simplemente terminar el programa con un error del sistema operativo.

**¿Por qué?**
El segmento de código (también llamado segmento de texto) es la región de memoria donde está el código ejecutable del programa.

En la mayoría de los sistemas modernos, esta región:

Tiene permisos de solo lectura y ejecución.

No permite escritura por seguridad (protección contra modificaciones accidentales o ataques como buffer overflows o code injection).

Por eso, cuando intentas modificar esa memoria (como cambiar el contenido de main), el sistema operativo lo detecta y lo impide.

**Experimento 2: Modificar el Segmento de Solo Lectura**

Código relevante:
```asm
char* ptr = (char*)&mensaje_ro;
cout << "Voy a modificar la memoria en la dirección: " << ptr << endl;
*ptr = 0;
```

**¿Qué ocurre?**
Aquí también se produce normalmente una violación de acceso o un comportamiento indefinido.

En algunos entornos (dependiendo del compilador y optimizaciones), el programa puede incluso parecer que "funciona" pero con resultados extraños o errores más adelante.

**¿Por qué?**
mensaje_ro es una constante global de solo lectura (const char* const).

El literal "Hola, memoria de solo lectura" está almacenado en el segmento .rodata (read-only data).

Este segmento, al igual que el segmento de código, no tiene permisos de escritura.

Al intentar modificar el contenido apuntado por el puntero (no el puntero en sí, sino el string que apunta), estás violando una restricción del sistema operativo, por lo tanto, obtienes un error.



