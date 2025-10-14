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
8. **En esta unidad estamos usando OpenGL moderno, pero ¿Qué es OpenGL Legacy? ¿Qué diferencias hay entre ambos?**: Según entendí, la diferencia radica en el pipeline (El flujo que sigue el programa para desarrollar gráficos). Mientras el moderno tiene un pipeline programable, el Legacy tiene un pipeline fijo, lo que nos permite, usando el moderno, más flexibilidad con las cosas que podamos lograr.
9. **¿Qué es el shader program? ¿Por qué es importante en OpenGL moderno?**: Básicamente, el shader program es un programa que nos permite representar las funciones como pixeles y vértices. Es el que le permite al programa saber qué tiene que dibujar.
10. **Trata de revisar el código setupTriangle(), intuitivamente ¿Qué crees que hace? ¿Qué crees que es el VAO y el VBO?**:


## Actividad 04
### 🧐✍️ Reporta en tu bitácora
Según entendí del video (porque no recuerdo mucho de las primeras unidades) la principal diferencia es que la CPU procesa las instrucciones de una manera más secuencial, mientras que la GPU está diseñada para procesar varias instrucciones simultaneamente.

### 🧐✍️ Reporta en tu bitácora
1.  **¿Cuáles son los tres pasos claves del pipeline de OpenGL? Explica en tus propias palabras cuál es el objetivo de cada paso:**
     1. Vertex shading: Determina la posición de los objetos que hay en pantalla.
     2. Rasterization: Pinta los objetos del color del material que tienen asignado.
     3. Fragment shading: Agrega los detalles importantes, tales como luces y sombras, para que la escena se vea más coherente visualmente.
2. **Ventajas del pipeline programable**: Según yo, las ventajas podrían ser más que nada tomando en cuenta que el pipeline sería más flexible, lo que nos permite agregar u omitir pasos según las necesidades de nuestro caso particular.
3. **Si fueras a describir el proceso de rasterización ¿Qué dirías?**: "Que la GPU defina el color del material de cada triángulo (los triángulos componen la escena 3D)".
4. **¿Qué son los fragmentos? ¿Es lo mismo un fragmento que un pixel? ¿Por qué?**: No son lo mismo; un fragmento es un conjunto de pixeles, provenientes del mismo triángulo (*explicado en el punto 3*), que comparten textura o color.
5. **Explica qué problema resuelve el Z-buffer y ¿Qué es el depth test?**: El depth test es la comparación entre la profundidad de los vértices de los triángulos, lo que permite determinar cuáles están más cerca de la cámara. Esto le permite a la GPU saber qué vértices debe procesar en determinado momento, evitando hacer cálculos innecesarios.
6. **¿Por qué se presenta el problema de la aliasing? ¿Qué es el anti-aliasing?**: El aliasing se presenta porque la forma que tenemos de representar el 3D en una pantalla es por medio de pixeles, por lo que pueden quedar bordes dientudos (estoy muy cansado para saber si esa palabra sí está bien usada). El anti-aliasing es un proceso que permite suavizar esos bordes, dividiendo (matemáticamente) los pixeles, y calculando nomeacuerdoqué con los lados de los triángulos.
7. **¿Qué relación hay entre la iluminación y el fragment shader? Siempre es necesario tener en cuenta la iluminación en un fragment shader? o puedo hacer un fragment shader sin iluminación? Explica que implicaciones tiene esto:** El fragment shader lo que hace es determinar cómo afecta la iluminación a los objetos de la escena, lo que da como resultado una escena más realista (o visualmente coherente, en cualquier caso). De poder, se puede hacer una escena sin fragment shader, pero esto nos daría una escena plana, sin mucha profundidad (que es lo que nos proporcionan las luces y sombras).
8. **¿Qué implica para la GPU que una aplicación tenga múltiples fuentes de iluminación?**: Dado que los specs y las sombras se calculan a partir de operciones matemáticas, que involucran el vector de las normales y la dirección de la iluminación, implica que la GPU tendría que hacer estas operaciones múltiples veces por cada uno de los triángulos que componen la escena, lo que multiplica el uso de recursos como un hp.

### 🧐✍️ Reporta en tu bitácora
1. **Escribe un resumen en tus propias palabras de lo que se necesita para dibujar un triángulo en OpenGL.**: Lo primero que se necesita es tener la información de los vértices del triángulo, que luego se mandan a un Buffer de vértices (**V**ertex **B**uffer **O**bject). Aquí toca decirle a OpneGL varias cosas, como el tamaño de la data que le va a llegar, el tipo de buffer o si el tamaño será estático o dinámico.

