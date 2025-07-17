# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 01
Ciclo fetch-decode-execute
``` asm
@1
D=A
@2
D=D+A
@16
M=D
@END
(END)
0;JMP
```
¿Qué sucede? ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute? ¿Qué cambios observas en el contenido de la memoria y los registros? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?
El programa suma dos valores, y almacena el resultado (3) en la dirección de memoria 16. Este valor se debe a que se suman los números 1 y 2, y después se le indica a la computadora que, en cierto punto del código, que guarde el resultado en la dirección con el número correspondiente al registro A: en este caso, la dirección 16.



Los datos almacenados en la memoria RAM son datos temporales, que se borran al apagar el dispositivo, mientras que los datos almacenados en la memoria ROM se quedan guardados todo el tiempo.


