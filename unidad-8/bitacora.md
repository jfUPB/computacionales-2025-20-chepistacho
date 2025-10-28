# Bitácora de aprendizaje de la unidad 8
## Actividad 01
### 🧐🧪✍️ Reporta en tu bitácora
A ver, antes de ejecutarlo, creo que va a dibujar un círculo, y pasará algo (a saber qué) cuando presione el clic.  
Ahora, después de ejecutarlo, pude observar que la aplicación sí hacía algo cuando presionaba el clic: cambiaba el tamaño del círculo. Sin embargo, el programa se tostaba cuando intentaba calcular el nuevo tamaño del círculo. Esto porque la tarea del nuevo tamaño se estaba delegando a un solo hilo, y no era capaz de hacer ambas cosas al mismo tiempo.  

### 🧐🧪✍️ Reporta en tu bitácora
Pues no se traba (aparentemente), pero el círculo no cambia de tamaño hasta un poco después (era por lo del paralelismo o la concurrencia, pero no me acuerdo 😢).  

### 🧐🧪✍️ Reporta en tu bitácora
El paralelismo es que varios núcleos hacen varias tareas, concentrándose cada uno en su tareíta. La concurrencia es que un solo núcleo se encarga de hacer varias tareas a la vez.  

## Actividad 02
### 🧐🧪✍️ Reporta en tu bitácora
So, la parte del código que protege el acceso al `circleSize` es el sigueinte:  
``` c++
lock();
    ofSeedRandom();
    circleSize = ofRandom(20, 70);
    unlock();
  std::cout << "Circle size: " << circleSize << std::endl;
```
Y, con respecto a lo otro, yo creería que la sincronización con un recurso compartido sí afecta el rendimiento del programa, pues esto sería otro proceso en sí (ponele, no tengo idea).  

### 🧐🧪✍️ Reporta en tu bitácora
Bueno, esto recuerdo que lo vimos en clase. Básicamente lo que pasa es que, cuando quitamos el lock, el contador no llega al número esperado (4000000), porque los hilos quieren trabajar todos al mismo tiempo, y se "atrancan". Mientras tanto, si el lock está activado, el contador, por más que se demore un poco más, llega al valor que esperamos.  

### 🧐🧪✍️ Reporta en tu bitácora
Esto lo entendí mejor con la analogía que hiciste vos (sí, vos, Juanferfranco.github), y es suponer que mucha gente tiene que ir al mismo baño al mismo tiempo; si tenemos un seguro, sabremos que, aunque se demoren , todos harán sus necesidades tranquilamente, mientras que, si no tenemos seguro, quedarán muchos sin poder entrar tranquilos. En este caso, los hilos representan esa gente, y la función `startTest` es el baño que estos deben usar.

## Actividad 03
### 🧐🧪✍️ Reporta en tu bitácora
- Ya ejecuté el código. Muestra la representación de un fractal todo bonito y todo exótico. Ambas versiones muestran el mismo resultado, aunque en la versión secuencial, al recalcular el fractal, tiene un bajón considerable de fps, mientras que la paralela se mantiene estable.
- 
