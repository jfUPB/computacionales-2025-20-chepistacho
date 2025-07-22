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
**¿Qué sucede? ¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute? ¿Qué cambios observas en el contenido de la memoria y los registros? ¿Qué instrucciones se ejecutan en cada ciclo Fetch-Decode-Execute?**  
El programa suma dos valores, y almacena el resultado (3) en la dirección de memoria 16. Este valor se debe a que se suman los números 1 y 2, y después se le indica a la computadora que, en cierto punto del código, que guarde el resultado en la dirección con el número correspondiente al registro A: en este caso, la dirección 16.  
Los datos almacenados en la memoria RAM son datos temporales, que se borran al apagar el dispositivo, mientras que los datos almacenados en la memoria ROM se quedan guardados todo el tiempo.



### Actividad 02  

``` asm
@SCREEN
D=A
@i
M=D
(READKEYBOARD)
@KBD
D=M
@KEYPRESSED
D;JNE
@i
D=M
@SCREEN
D=D-A
@READKEYBOARD
D;JLE
@i
M=M-1
A=M
M=0
@READKEYBOARD
0;JMP

(KEYPRESSED)
@i
D=M
@KBD
D=D-A
@READKEYBOARD
D;JGE
@16
A=M
M=-1
@i
M=M+1
@READKEYBOARD
0;JMP
```
**Identifica una instrucción que use la ALU y explica qué hace.**  
Una instrucción podría ser D=D-A, la cual resta el valor de A al registro D. En el programa sirve para comparar posiciones entre D y A, y decidir si el cursor debe moverse.

**¿Para qué sirve el registro PC?**  
El registro PC sirve para guardar el registro de la sigueinte instrucción a ejecutar, con el fin de llevar un control sobre la parte del código en la que estamos.

**¿Cuál es la diferencia entre @i y @READKEYBOARD?**  
@i funciona como una variable para almacenar datos, mientras que @READKEYBOARD sirve para etiquetar una parte del programa.

**Describe qué se necesita para leer el teclado y mostrar información en la pantalla.**  
Para leer el teclado se accede a la dirección KBD, que contiene el valor de la última tecla presionada, y para mostrar en pantalla se escribe en SCREEN, donde se usa el valor -1 para encender un pixel y 0 para apagarlo.

**Identifica un bucle en el programa y explica su funcionamiento.**  
Hay un bucle que comienza en la etiqueta READKEYBOARD, y sirve para revisar constantemente si se está presionando una tecla y así actualizar la memoria de la pantalla.

**Identifica una condición en el programa y explica su funcionamiento.**  
``` asm
@KBD
D=M
@KEYPRESSED
D;JNE
```
Esta condición determina el funcionamiento del código en caso de que haya una tecla presionada. Si lo está, salta a la etiqueta KEYPRESSED, de lo contrario seguirá en el código que borra pixeles.
