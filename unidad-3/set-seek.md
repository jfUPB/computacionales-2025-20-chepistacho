# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 05 🐧  
1. **¿Cuál será la salida final en la consola de este programa?**: El programa va a imprimir varios mensajes, mostrando cómo cambian las variables cuando se pasan de diferentes maneras a las funciones (por valor, por referencia y por puntero).
Después también va a imprimir cómo cambia una variable “estática” cada vez que se llama a la función del contador.

2. **Escribe la salida completa que esperas**: val_A: 20 val_B: 30 val_C: 30

3. <img width="561" height="631" alt="image" src="https://github.com/user-attachments/assets/9ed54543-8882-400e-9bdd-399fc9e0f6d9" />


4. **Compara la salida real con tu predicción. Si hubo diferencias, explica por qué ocurrieron. Evidencia clave: capturas de pantalla antes y después de los puntos de interés (¿Cuáles son esos puntos? -> tu tarea analizarlo).**: Básicamente sí fue acertada la predicción, sin embargo, el funcionamiento del código es más complejo que lo que se explica en la predicción. Los resultados fueron los esperados.

5. a

6. **Explica con tus propias palabras el comportamiento de contador_estatico. ¿Por qué “recuerda” su valor entre llamadas a la función ejecutarContador? ¿En qué se diferencia de una variable local normal?**: Básicamente, `contador_estatico` es una variable estática, lo que implica que siempre tendrá su valor guardado en el mismo espacio de memoria, por lo que solo se inicializa una vez y "recordará" el valor que tenía.
   La principal diferencia con una variable local, es que esas se guardan en el *Stack*, y pierden su valor cuando termina la función, mientras que las variables globales y estáticas se guardan en el mismo lugar, donde no se vuelven a inicializar cada que se ejecuta una función.

