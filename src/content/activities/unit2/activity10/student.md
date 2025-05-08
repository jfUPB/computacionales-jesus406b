#### TEST

### Código ensamblador propuesto

```asm
// -------- Inicio --------
(inicio)
@KBD
D=M
@NO_KEY
D;JEQ           // Si no hay tecla, saltar

// Guardar tecla presionada en R13 (arg)
@R13
M=D

// Guardar dirección de retorno
@retorno_pantalla
D=A
@R14
M=D

// Llamar a pantalla
@pantalla
0;JMP

(retorno_pantalla)
@inicio
0;JMP

(NO_KEY)
@inicio
0;JMP

// -------- Función pantalla --------
(pantalla)
// Leer el argumento desde R13
@R13
D=M

// Comprobar si es 'p' (112)
@112
D=D-A
@PINTAR
D;JEQ

// Comprobar si es 'b' (98)
@R13
D=M
@98
D=D-A
@BORRAR
D;JEQ

// Ninguna acción
@R14
A=M
0;JMP

(PINTAR)
// Llenar pantalla con -1
@SCREEN
D=A
@R0
M=D           // R0 = dirección actual
@8192
D=A
@R1
M=D           // R1 = contador

(LOOP_PINTAR)
@R0
A=M
M=-1          // Pintar

@R0
M=M+1         // Avanzar a siguiente dirección
@R1
MD=M-1        // Decrementar contador
@LOOP_PINTAR
D;JGT

@R14
A=M
0;JMP

(BORRAR)
// Llenar pantalla con 0
@SCREEN
D=A
@R0
M=D
@8192
D=A
@R1
M=D

(LOOP_BORRAR)
@R0
A=M
M=0           // Borrar

@R0
M=M+1
@R1
MD=M-1
@LOOP_BORRAR
D;JGT

@R14
A=M
0;JMP
```
