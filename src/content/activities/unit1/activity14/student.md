#### TEST

**Análisis de errores y debugging – Unidad sobre ensamblador Hack**

Durante la fase APPLY, cometí varios errores, pero dos de los más significativos fueron:

**1. Error al manipular punteros indirectos:**
En un programa donde debía recorrer un arreglo usando un puntero, usé incorrectamente `A=i` en lugar de `A=M`. Esto hacía que el programa apuntara a una dirección fija en lugar de a la dirección contenida en el puntero. Me di cuenta del error al observar que los valores que modificaba no coincidían con los del arreglo. Lo corregí reemplazando la línea por `@i` seguido de `A=M`.

**2. Confusión con el orden de instrucciones en comparaciones:**
En un `if`, escribí primero el salto condicional antes de la operación de comparación. Por ejemplo, usé `@END` seguido de `D;JEQ` sin haber cargado previamente un valor en `D`. Esto causaba saltos inesperados. Al revisar paso a paso en el simulador, noté que `D` no contenía ningún valor útil. Corregí el flujo cargando primero el valor con `D=M` o `D=A`, según el caso, y luego haciendo el salto.

**Lecciones aprendidas:**
Estos errores me enseñaron a **leer el flujo del programa de manera más rigurosa** y a no asumir que los registros contienen lo que necesito. También aprendí la importancia de seguir la lógica paso a paso, como si la máquina no "supiera nada", lo que es cierto.

**Prevención de errores futuros:**
Para evitar errores similares, pienso usar más comentarios en mi código y seguir la estrategia de verificar cada sección del código en el simulador antes de continuar. Además, ahora soy más consciente de lo importante que es inicializar correctamente los registros antes de usarlos.

**Importancia del debugging en el desarrollo de software:**
El debugging es fundamental porque permite entender no solo qué falla, sino cómo y por qué falla. En este proceso, uno aprende más que simplemente al escribir código correcto. En el simulador de Hack, usé principalmente **el seguimiento paso a paso (step)** y la observación de **los valores en RAM y en los registros A y D**. Esto me permitió visualizar cómo fluía la información y detectar en qué momento exacto el programa no hacía lo esperado.

