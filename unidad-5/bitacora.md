# Bitácora de aprendizaje de la unidad 5

## 1.  **Diagnóstico inicial**
### Parte 1:  
- El encapsulamiento es la restricción de acceso que tiene una variable o un método. No recuerdo un caso particular en el que a mí me haya sido útil 😢.
- La herencia se da cuando una clase (llamada clase hija), obtiene atributos y métodos de una clase que la "contiene" (llamada clase padre). Serviría para no tener que definir nuevamente variables o métodos que ya están definidos en la clase padre. Ejemplo: la clase "Perro" hereda todas las características de la clase "canino".
- El polimorfismo consite en redefinir un método **después** de haber sido heredado, ya que algunos métodos pueden tener distintos funcionamientos dependiendo de la clase hija que lo ejecute.

### Parte 2:  
``` c#
using System;
using System.Collections.Generic;

public abstract class Figura
{
    private string nombre;

    public string Nombre
    {
        get { return nombre; }
        protected set { nombre = value; }
    }

    public Figura(string nombre)
    {
        this.Nombre = nombre;
    }

    public abstract void Dibujar();
}

public class Circulo : Figura
{
    public double Radio { get; private set; }

    public Circulo(double radio) : base("Círculo")
    {
        this.Radio = radio;
    }

    public override void Dibujar()
    {
        Console.WriteLine($"Dibujando un {Nombre} de radio {Radio}.");
    }
}

public class Rectangulo : Figura
{
    public double Base { get; private set; }
    public double Altura { get; private set; }

    public Rectangulo(double b, double h) : base("Rectángulo")
    {
        this.Base = b;
        this.Altura = h;
    }

    public override void Dibujar()
    {
        Console.WriteLine($"Dibujando un {Nombre} de {Base}x{Altura}.");
    }
}

public class Programa
{
    public static void Main()
    {
        List<Figura> misFiguras = new List<Figura>();

        misFiguras.Add(new Circulo(5.0));
        misFiguras.Add(new Rectangulo(4.0, 6.0));
        misFiguras.Add(new Circulo(10.0));

        foreach (Figura fig in misFiguras)
        {
            fig.Dibujar();
        }
    }
}
```
**Encapsulamiento**:
- `public abstract class Figura`: Básicamente en cualquier parte del código donde definen una clase, un atributo o un método. En este caso, la palabra clave `public` nos indica un encapsulamiento público (cualquier parte del código puede acceder a esta clase).
- Básicamente se usan métodos accesores para evitar modificaciones no deseadas y más controladas al atributo.

**Herencia:**  
- Cuando se define la clase `Circulo` se pone la línea `public class Circulo : Figura`, lo que indica una herencia.
- Almacena el nombre, heredado de la clase Figura.

**Polimorfismo**:  
- Porque el método `Dibujar()` en la clase Figura es abstracto (no tiene una función exacta), y se comporta distinto en función de qué figura lo está usando (estas figuras heredan de la clase Figura), por lo que siempre se ejecutará la versión correcta en función de la figura que se esté mostrando.

### Parte 3:  
- Yo creería (ojo, **YO CREERÍA**) que se logra asignando un espacio de memoria específico para cada clase, lo que logra identificar todo ese espacio como parte de un mismo conjunto.
- El programa compara datos del espacio mencionado anteriormente, y dependiendo del que coincida con el que está buscando se ejecuta el `Dibujar()` de una manera o de otra. (en mi cabeza era más complejo, pero creo que simplemente volví a definir lo que era el polimorfismo)
- **AQUÍ ES QUE YA NO TENGO IDEA. DESDE AQUÍ PARTO**

## 2.  **La pregunta inicial**

## 3.  **Registro de exploración:** 
> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación
