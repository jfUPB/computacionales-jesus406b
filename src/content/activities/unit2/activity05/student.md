####TEST
traducción del programa en lenguaje ensamblador
```asm
section .data
    a dd 10    ; Declaración de la variable a con valor 10
    b dd 5     ; Declaración de la variable b con valor 5
    p dd 0     ; Puntero p inicializado en 0

section .text
    global _start

_start:
    ; p = &a (guardar la dirección de 'a' en 'p')
    mov eax, a   ; Cargar la dirección de 'a' en eax
    mov [p], eax ; Guardar la dirección en 'p'

    ; b = *p (leer el valor de la dirección almacenada en 'p')
    mov eax, [p] ; Cargar la dirección almacenada en 'p'
    mov ebx, [eax] ; Cargar el valor apuntado por 'p' en ebx
    mov [b], ebx  ; Guardar el valor en 'b'

    ; Terminar el programa
    mov eax, 1    ; Llamada al sistema: sys_exit
    xor ebx, ebx  ; Código de salida 0
    int 0x80      ; Interrupción para salir
```
