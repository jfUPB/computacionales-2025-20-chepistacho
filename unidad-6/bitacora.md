# Bitácora de aprendizaje de la unidad 6

## Set-seek 🔎
### Actividad 01 🐧
**1. ¿Cómo puedes interactuar con la aplicación? Menciona específicamente las teclas y qué efecto parecen tener sobre las partículas:** La tecla `A` atrae las partículas, la tecla `R` las repele, la tecla `S` las detiene y la tecla `N`las devuelve a su movimiento normal.  
**2. ¿Observas los diferentes tipos de “partículas”? ¿Se comportan todas igual inicialmente?:** A simple vista no ví ninguna diferencia, inicialmente hay tres tipos distintos de partícula: **star**, **planet** y **shooting star**.  
**3. Toma algunas capturas de pantalla de la aplicación en diferentes momentos (estado inicial, después de presionar ‘a’, ‘r’, ‘s’, ‘n’) y añádelas a tu bitácora.**:  
<img width="714" height="524" alt="image" src="https://github.com/user-attachments/assets/3c869b21-c518-41e0-b568-370cc523ace0" />  
<img width="809" height="498" alt="image" src="https://github.com/user-attachments/assets/632997fb-287e-48e6-9785-ca5d98f20814" />  
<img width="851" height="607" alt="image" src="https://github.com/user-attachments/assets/98a8bb0b-3035-4a8c-96c4-45f861e0bd25" />  
<img width="515" height="442" alt="image" src="https://github.com/user-attachments/assets/8db3c97d-7748-4234-bfed-4915a33e5789" />  
**4. ¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas? Formula una hipótesis inicial sobre cómo la aplicación cambia el comportamiento de las partículas:** Según recuerdo de lo que dijo el profe, se notifica a las instancias de partículas que se hizo un cambio de estado, con el patrón **observer** (como si fuera un periódico con suscripción).  

### Actividad 02 🐧
1. **Identifica los Roles**
   - El Subject es la clase `Subject`.
   - El Observer es igual, la clase `Observer`.
   - El ConcreteObserver creería que son las partículas, porque son las que reaccionan al cambio de estado.

2. **Sigue el flujo de notificación**
   - Se llama el método `notify`, que anuncia a los observers el cambio de estado.
   - A nivel técnico no sé qué hace exactamente, pero por la sintaxis entiendo que anuncia a los observadores que hubo un evento.
   - Cambia el estado a `new AttractState()`, más todo lo que implica ese cambio de estado.

3. **Registro y eliminación de observadores**
   - En el `setup` hay tres ciclos `for`, que añaden observadores en función de la cantidad de partículas de cada tipo.
   - El destructor es importante para evitar un consumo excesivo e innecesario de memoria dedicada a sujetos que ya no existen.

### Reporte 🧐🧪✍️
1. El patrón Observer busca evitar que todo un programa responda a eventos que solo le incumben a ciertas partes específicas del código.
2. x
3. <img width="509" height="631" alt="image" src="https://github.com/user-attachments/assets/5277039e-3435-4512-8516-273016da77df" />

4. La mayor ventaja de este patrón es que permite un mayor control sobre las partes del código que reaccionan a algún cambio en el estado, lo que facilita en cierto modo la comprensión y el flujo del programa.

## Actividad 03 🐧
1. Este patrón, según entendí, ahorra tiempo (y da más orden) al escribir un constructor por cada partícula, creando un método que permite instanciar varios objetos de una sola vez.
2. Pienso que es precisamente por lo que dije anteriormente: es mucho más fácil programar un método constructor y llamarlo cuando sea necesario en vez de volver a escribir líneas de código por cada vez que se necesite un nuevo objeto.
3. Efectivamente, primero tendría que modificar el método `createParticle` para definir cómo sería el `black_hole`, y después sí modifico el método `setup`, donde añado otro ciclo `for` para instanciarla las veces que haga falta.
4. Por un lado, ahorra algo de memoria al no tener que instanciar clases de comportamiento, además de ahorrar el trabajo de instanciarlas para poderlas llamar (pues, como dije antes, no se deben instanciar si son solo comportamiento).

## Actividad 04 🐧
1. Si entendí bien, el patrón State es útil cuando un programa va a tener muchos cambios de estado, evitando tener que escribir un montón de condicionales y solo escribiendo un bloque al principio para definir el cambio de estado.
2. x
3. Si tuviéramos un bloque gigante de condicionales, se complica considerablemente la escritura del código, e incluir nuevos estados sería un complique grandísimo, pues supondría incluir más condicionales anidados, en vez de simplemente definir una vez el estado y el cambio de estado.
4. x

## Actividad 05 🐧

