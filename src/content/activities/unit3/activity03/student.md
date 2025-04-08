####TEST

CAPTURA DE PANTALLA  DE LA EJECUCION DEL PROGRAMA

![image](https://github.com/user-attachments/assets/84f93e56-8af0-42c7-a02c-aae192bc3258)

```asm
 **Mapa de Memoria del Programa C++**
 +---------------------------------------------+
| **Stack** (crece hacia abajo)               |
| Dirección de variable local 'c'     → 0x0000003A44AFFA24 |
| Dirección de variable local 'b'     → 0x0000003A44AFFA04 |
| Dirección de variable local 'a'     → 0x0000003A44AFF9E4 |
+---------------------------------------------+
| **Heap** (crece hacia arriba)               |
| arrayHeap[0] = 0         → 0x0000020DFF5797B0 |
| arrayHeap[1] = 1         → 0x0000020DFF5797B4 |
| arrayHeap[2] = 2         → 0x0000020DFF5797B8 |
| arrayHeap[3] = 3         → 0x0000020DFF5797BC |
| arrayHeap[4] = 4         → 0x0000020DFF5797C0 |
| arrayHeap[5] = 5         → 0x0000020DFF5797C4 |
| arrayHeap[6] = 6         → 0x0000020DFF5797C8 |
| arrayHeap[7] = 7         → 0x0000020DFF5797CC |
| arrayHeap[8] = 8         → 0x0000020DFF5797D0 |
| arrayHeap[9] = 9         → 0x0000020DFF5797D4 |
+---------------------------------------------+
| **Segmento de datos (globales y estáticas)**|
| var_estatica (static)       → 0x00007FF7098AF004 |
| global_inicializada         → 0x00007FF7098AF000 |
| global_no_inicializada      → 0x00007FF7098AF4C0 |
+---------------------------------------------+
| **Segmento de solo lectura (.rodata)**      |
| mensaje_ro (const char*)     → 0x00007FF7098ABBC0 |
+---------------------------------------------+
| **Segmento de código (Text)**               |
| (No se mostró en la salida, pero suelen estar |
|  en direcciones más bajas, como 0x00007FF7...) |
+---------------------------------------------+
```
