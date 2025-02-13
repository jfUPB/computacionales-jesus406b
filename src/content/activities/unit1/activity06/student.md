Test

### **Respuestas a las preguntas**  

1. **¿Qué es el direccionamiento directo? ¿Cómo se usa en el lenguaje ensamblador Hack?**  
   El **direccionamiento directo** es un modo de direccionamiento en el que la instrucción hace referencia a una dirección de memoria específica. En el lenguaje ensamblador Hack, esto se logra usando la instrucción `@n`, donde `n` es la dirección de memoria a la que queremos acceder.  

   **Ejemplo:**  
   ```assembly
   @15  // Carga la dirección 15 en el registro A
   D=M  // Guarda el valor almacenado en la dirección 15 en el registro D
   ```
   En este caso, `D` ahora contiene el valor de la celda de memoria 15.  

2. **¿Qué significa `M=D` en lenguaje ensamblador Hack? ¿Y `D=M`?**  
   - `M=D` significa que el **contenido del registro D se almacena en la dirección de memoria apuntada por A**.  
   - `D=M` significa que el **contenido de la dirección de memoria apuntada por A se copia en el registro D**.  

   **Ejemplo:**  
   ```assembly
   @5   // Carga dirección 5 en el registro A
   D=M  // Copia el contenido de la dirección 5 en D
   @10  // Carga dirección 10 en el registro A
   M=D  // Guarda el valor de D en la dirección 10
   ```
   En este caso, el valor almacenado en la dirección de memoria 5 se transfiere a la dirección de memoria 10.  

3. **Explicación del concepto de "puntero" en el contexto de la memoria**  
   Un **puntero** es una dirección de memoria que almacena otra dirección de memoria. En el lenguaje ensamblador Hack, un puntero es una celda de memoria cuyo contenido es tratado como una dirección en la memoria. Esto es útil cuando queremos trabajar con estructuras de datos dinámicas, como arreglos o listas.  

   **Ejemplo de código en ensamblador Hack que ilustra el uso de un puntero:**  
   ```assembly
   @100   // Carga la dirección 100 en el registro A (puntero)
   D=A    // Guarda la dirección 100 en D
   @10    // Carga la dirección 10 en el registro A
   M=D    // Guarda el valor de D (100) en la dirección 10 -> Ahora M[10] = 100

   @10    // Carga la dirección 10 en el registro A
   A=M    // Mueve a la dirección almacenada en M[10], es decir, A = 100
   M=42   // Guarda el valor 42 en la dirección 100
   ```
   **Explicación del código:**  
   - Se guardala dirección `100` en la celda de memoria `10`, convirtiéndola en un puntero.  
   - Luego, accedemos a la dirección almacenada en `M[10]` y almacenamos el valor `42` en la dirección `100`.  

 
