# Bitácora de aprendizaje de la unidad 7
## Actividad 01  
1. Incluye una captura de pantalla del ejemplo funcionando en tu máquina:  
   <img width="390" height="399" alt="image" src="https://github.com/user-attachments/assets/38f3937c-a9f9-49b6-b87b-a0b69240d335" />
2. Observa el proyecto, trata de entenderlo, pero ten presente que lo analizaremos más adelante.
   La verdad sea dicha, no entiendo casi nada del código.
3. ¿Qué preguntas te surgen al ver el código?. Anota al menos tres preguntas que te gustaría investigar más adelante (no te preocupes que la idea de esta unidad es que las resuelvas).:
   - ¿Qué diablos es el framebuffer?
   - ¿Cómo funciona el shaderProg?
   - ¿Qué son Callbacks y para qué sirven, precisamente?

## Actividad 02
Hasta donde me acuerdo (mi memoria no es la mejor):  
Descargamos tres dependencias externas (glad, glfw34 y glm-101-light), las cuales contienen librerías y archivos necesarios para poder crear un archivo usando OpenGL. Después de descargarlas, le especificamos al Visual en dónde tenía que buscar los archivos importantes, para que no se embalara a la hora de compilar ni ejecutar los programas que allí creemos.  
Personalmente, la que más me llamó la atención fue GLAD, que la veo como una especie de espía, que nos pasa las funciones de los drivers debajo de la mesa.  

## Actividad 03
### 🧐🧪✍️ Primer experimento
Bueno, cuando me pongo a molestar con los parámetros de la línea `glViewport(0, 0, bufferWidth, bufferHeight);`, contrario a lo que yo creía, la ventana queda del mismo tamaño (lo que hace sentido, pues no movimos nada relacionado con la ventana), y el triángulo cambia de tamaño, proporcional al valor por el que multiplique o divida el `bufferWidth` y el `bufferHeight`.  

### 🧐🧪✍️ Segundo experimento
Básicamente, OpenGL nos permite el uso de herramientas que nos ayudan a desarrollar gráficos. El framebuffer es el espcaio en la memoria en el que se van a pintar los pixeles que conformarán nuestra obra de arte, y la GPU se encargará de llevar a cabo esta Mona Lisa, la cual se mostrará en pantalla cuando esté ready. 

En este momento, me pregunto qué pasaría si moviera algo de la línea `GLFWwindow* mainWindow = glfwCreateWindow(SCR_WIDTH, SCR_HEIGHT, "Ventana", NULL, NULL);`.

### 🧐🧪✍️ Tercer experimento
Antes de leer el experimento, me dio por ver qué pasaría si cambiaba el número de vértices, y efectivamente, si es menor a tres, la figura desaparece (porque es imposible dibujar un polígono de dos lados), mientras que, de tres para arriba, se queda como triángulo.  
Ahora bien, si cambio la primitiva que se va a mostrar, el dibujo cambia (obviamente). Si pongo `GL_LINES`, se dibuja una línea horizontal, mientras que si pongo `GL_POINTS`, no aparece nada.

### 🧐🧪✍️ Cuarto experimento
1. **¿Qué es el contexto OpenGL?**: Es el contexto en el que se van a ejecutar ciertas acciones, con el fin de que la computadora dibuje algo.
2. **¿Cuál es el rol de la biblioteca GLFW y qué ventaja tiene usarla?**: Básicamente nos ayuda con funciones que nos sirven para crear la ventana donde se va a mostrar nuestro trabajo, sin necesidad de escribir nuevo código para cada caso específico.
3. **¿Por qué crees que OpenGL necesita un contexto (recuerda la analogía del taller de arte)?**: Según esa analogía, es porque sin el contexto, OpenGL no tiene donde trabajar (un artista sin su taller), por lo que no podríamos dibujar nada.
4. **¿En últimas qué será el framebuffer y a qué te recuerda de las dos primeras unidades del curso?**: El framebuffer termina siendo una porción de memoria, y me recuerda muchoa cómo dibujábamos al principio del curso en el lenguaje ensamblador, especificando la posición en memoria de los pixeles que queremos pintar.
5. **¿Qué relación entre en el viewport y el framebuffer?**: Según entendí, el viewport es la parte (en pantalla) que se va a pintar, lo que requiere informarle al framebuffer qué porción de memoria se requiere para esto.
6. **¿En todo la analizado hasta ahora qué rol juega los drivers de la GPU y la GPU misma?**: Básicamente, los drivers de la GPU contienen funciones, las cuales nos re sirven para poder dibujar más cosas, y la GPU es literalmente el artista que crea las obras que nosotros le pedimos.
7. **¿Por qué crees que sea necesario activar el VSync? ¿Si no lo activas y la imagen es estática qué crees que pase, y si es dinámica?**: Aquí desde mi ignorancia, si la imagen es estática, sería importante para que no empiece a titilar o a hacer cosas raras, y si es dinámica, para que se vea fluido el movimiento.
8. **En esta unidad estamos usando OpenGL moderno, pero ¿Qué es OpenGL Legacy? ¿Qué diferencias hay entre ambos?**: Según entendí, la diferencia radica en el pipeline (no sé qué es eso). Mientras el moderno tiene un pipeline programable, el Legacy tiene un pipeline fijo (supongo que esto lo entenderé más adelante).
9. 
