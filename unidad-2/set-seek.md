# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01  🐧
``` asm
@SCREEN
M=1
```
Este programa utiliza la etiqueta SCREEN para ubicar la dirección de memoria 16384, y después cambiar su valor a 1 (pinta ese pixel de negro).  

<img width="81" height="39" alt="image" src="https://github.com/user-attachments/assets/2be21c77-8bf4-444f-9a8a-8c713d5b2ed0" />


**En c++**:  
``` c++
screen = 1; //Tenemos que forzar al compilador para que guarde `screen` en la
	    //dirección de memoria 16384
```

### Actividad 02 🐧
``` asm
@SCREEN
M=-1
```
Hace básicamente lo mismo que el programa anterior, pero esta vez asignando el valor de -1, para dibujar una linea de 16 pixeles.  

<img width="61" height="32" alt="image" src="https://github.com/user-attachments/assets/36ce0188-5a81-4bf7-966c-f248aeb75c9d" />


**En c++**:  
``` c++
screen = -1; //Tenemos que forzar al compilador para que guarde `screen` en la
	     //dirección de memoria 16384
```

### Actividad 03 🐧  
Programa en **lenguaje ensamblador**:
``` asm
@SCREEN
M=-1
@CONTADOR
M=0

(LEER)


@KBD
D=M

@100
D=D-A
@DERECHA
D;JEQ


@KBD
D=M

@105
D=D-A
@IZQUIERDA
D;JEQ

@LEER
0;JMP




(DERECHA)
@CONTADOR
D=M
@SCREEN
A=D+A

M=0


@CONTADOR
M=M+1
D=M
@SCREEN
A=D+A

M=-1
@LEER
0;JMP


(IZQUIERDA)
@CONTADOR
D=M
@SCREEN
A=D+A
M=0

@CONTADOR
M=M-1
D=M
@SCREEN
A=D+A

M=-1

@LEER
0;JMP
```
Profe, honestamente se me olvidó traducirlo a c++, pero sé que es una extensión del código anterior. En esta versión, se busca que el programa cambie la dirección de memoria donde se guarda el valor -1, en función de si se está presionando la tecla **d** o la letra **i**.

### Actividad 04 🐧  
El código que nos piden es el mismo del ejemplo, esto porque la función de ambos programas en **c++** es la misma, y lo que cambia es la forma como el programa lo interpreta.
``` asm
// Adds1+...+100.
 @i // i refers to some memory location.
 M=1 // i=1
 @sum // sum refers to some memory location.
 M=0 // sum=0
 (LOOP)
 @i
 D=M // D=i
 @100
 D=D-A // D=i-100
 @END
 D;JGT // If(i-100)>0 gotoEND
 @i
 D=M // D=i
 @sum
 M=D+M // sum=sum+i
 @i
 M=M+1 // i=i+1
 @LOOP
 0;JMP // GotoLOOP
 (END)
 @END
 0;JMP // Infinite loop
```

### Actividad 05 🐧  
#### **Primer código**:
``` c++
int a = 10;
int* p;
p = &a;
*p = 20;
```

**Traducción**:
``` asm
@10
D=A
@16
M=D
@16
D=A
@17
M=D
@17
A=M
@20
D=A
M=D
```

#### **Segundo código**:
``` c++
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```
**Traducción**:
``` asm
@10
D=A
@16
M=D
@5
D=A
@17
M=D
@16
D=A
@18
M=D
@18
A=M
D=M
@17
M=D
```
Básicamente, este código lo que hace es declarar una variable **a**, y le asigna un puntero **p**. A través de este puntero, el programa accede al valor de **a** y se lo asigna a otra variable **b**. El puntero termina haciendo la función de mediador entre ambas variables.


