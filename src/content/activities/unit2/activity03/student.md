####TEST
Análisis de la conversión de while a for

El programa en C original con while:

```asm
// Suma de 1 a 100
int i = 1;
int sum = 0;

while (i <= 100) {
    sum += i;
    i++;
}
```

La conversión a for es:
```asm
// Suma de 1 a 100
int sum = 0;
for (int i = 1; i <= 100; i++) {
    sum += i;
}
```
Ambas versiones son equivalentes, ya que el for simplemente agrupa la inicialización (int i = 1;), la condición (i <= 100;) y la actualización (i++) dentro de su estructura. Esto mejora la legibilidad y reduce posibles errores.

Versión en ensamblador (x86 NASM, modo 32 bits)

```asm
section .data
    sum dd 0      ; Variable para almacenar la suma

section .text
    global _start

_start:
    mov ecx, 1    ; i = 1
    mov eax, 0    ; sum = 0

for_loop:
    cmp ecx, 101  ; Si i > 100, salir del bucle
    jge end_loop

    add eax, ecx  ; sum += i
    inc ecx       ; i++
    jmp for_loop  ; Repetir

end_loop:
    ; Salida segura del programa
    mov ebx, eax  ; Retornar resultado en ebx
    mov eax, 1    ; syscall de salida
    int 0x80
```
Comparación de while vs for en ensamblador

La conversión del while a ensamblador es casi idéntica a la del for, ya que ambos siguen la misma estructura de comparación y salto condicional. La principal diferencia es que en la versión con for, la inicialización de i se hace antes de la etiqueta del bucle, mientras que en while, podría estar fuera del control directo del bucle. Sin embargo, la traducción a ensamblador resulta esencialmente igual.

Conclusión

En C, for y while son intercambiables en muchos casos.

En ensamblador, ambas estructuras se traducen en un conjunto de instrucciones muy similares.

Usar for mejora la claridad del código en alto nivel sin afectar el desempeño.

Recomendación

Se recomienda ejecutar ambas versiones en un simulador (como NASM con GDB) para verificar su correcto funcionamiento.

