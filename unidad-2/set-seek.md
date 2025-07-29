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
