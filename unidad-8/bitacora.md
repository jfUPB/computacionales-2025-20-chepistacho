# Bitácora de aprendizaje de la unidad 8
## Actividad 01
### 🧐🧪✍️ Reporta en tu bitácora
A ver, antes de ejecutarlo, creo que va a dibujar un círculo, y pasará algo (a saber qué) cuando presione el clic.  
Ahora, después de ejecutarlo, pude observar que la aplicación sí hacía algo cuando presionaba el clic: cambiaba el tamaño del círculo. Sin embargo, el programa se tostaba cuando intentaba calcular el nuevo tamaño del círculo. Esto porque la tarea del nuevo tamaño se estaba delegando a un solo hilo, y no era capaz de hacer ambas cosas al mismo tiempo.  

### 🧐🧪✍️ Reporta en tu bitácora
Pues no se traba (aparentemente), pero el círculo no cambia de tamaño hasta un poco después (era por lo del paralelismo o la concurrencia, pero no me acuerdo 😢).  

### 🧐🧪✍️ Reporta en tu bitácora
El paralelismo es que varios núcleos hacen varias tareas, concentrándose cada uno en su tareíta. La concurrencia es que un solo núcleo se encarga de hacer varias tareas a la vez.
