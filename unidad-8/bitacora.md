# Bitácora de aprendizaje de la unidad 8
## Actividad 01
### 🧐🧪✍️ Reporta en tu bitácora
A ver, antes de ejecutarlo, creo que va a dibujar un círculo, y pasará algo (a saber qué) cuando presione el clic.  
Ahora, después de ejecutarlo, pude observar que la aplicación sí hacía algo cuando presionaba el clic: cambiaba el tamaño del círculo. Sin embargo, el programa se tostaba cuando intentaba calcular el nuevo tamaño del círculo. Esto porque la tarea del nuevo tamaño se estaba delegando a un solo hilo, y no era capaz de hacer ambas cosas al mismo tiempo.  

