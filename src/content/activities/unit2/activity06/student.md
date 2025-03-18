####TEST
```asm
1️ int *pvar;
**RTA:** Declara un puntero pvar que puede apuntar a un entero. (No apunta a nada aún).

2️ *pvar = var;
**RTA:**  Guarda el valor de var en la dirección de memoria a la que pvar apunta. (Asegúrate de que pvar apunta a algo válido antes).

3️ var2 = *pvar;
**RTA:**  Asigna a var2 el valor almacenado en la dirección a la que apunta pvar. (Básicamente, lee el valor desde el puntero).

4️ pvar = &var3;
**RTA:**  Hace que pvar apunte a la dirección de var3. (Ahora pvar tiene la dirección de var3).
```
 Resumen rápido:
```asm
**RTA:** int *pvar; → "Tengo un puntero a entero."
**RTA:** *pvar = var; → "Guardo un valor en la dirección del puntero."
**RTA:** var2 = *pvar; → "Leo el valor de la dirección del puntero."
**RTA:** pvar = &var3; → "Apunto el puntero a otra variable."
```
