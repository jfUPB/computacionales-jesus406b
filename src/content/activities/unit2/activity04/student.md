###TEST
Este código demuestra cómo un puntero puede almacenar la dirección de una variable y modificar su contenido.


```asm
section .data
    a dd 10      ; Variable entera a con valor inicial 10
    p dd 0       ; Puntero p inicializado en 0 (luego guardará la dirección de a)

section .text
    global _start

_start:
    ; Guardar la dirección de 'a' en 'p'
    mov eax, a    ; Cargar la dirección de 'a' en EAX
    mov [p], eax  ; Almacenar la dirección de 'a' en 'p'

    ; Modificar el valor de 'a' usando el puntero 'p'
    mov ebx, [p]  ; Cargar la dirección almacenada en 'p' en EBX
    mov dword [ebx], 20  ; Almacenar 20 en la dirección a la que apunta EBX

    ; Finalizar el programa
    mov eax, 1    ; syscall: exit
    xor ebx, ebx  ; Código de salida 0
    int 0x80      ; Llamada al sistema

```
Explicación:
Se define la variable a con un valor inicial de 10 y un puntero p que almacenará la dirección de a.
Se guarda la dirección de a en p.
Se usa p para modificar el contenido de a, almacenando 20 en la dirección a la que apunta.
Finalmente, el programa finaliza con la llamada al sistema exit.
