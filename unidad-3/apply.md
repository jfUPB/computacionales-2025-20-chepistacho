# Unidad 3


## 🛠 Fase: Apply

### Actividad integradora

``` c++
#include <iostream>
#include <string>

class Personaje {
public:
    std::string nombre;
    int* estadisticas;

    Personaje(std::string n, int vida, int ataque, int defensa) {
        nombre = n;
        estadisticas = new int[3];
        estadisticas[0] = vida;
        estadisticas[1] = ataque;
        estadisticas[2] = defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << estadisticas[0]
            << ", ATK: " << estadisticas[1]
            << ", DEF: " << estadisticas[2]
            << "]" << std::endl;
    }
};

void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe = heroe;
    copiaHeroe.nombre = "Copia de Aragorn";

    std::cout << "Saliendo del encuentro..." << std::endl;
}

int main() {
    simularEncuentro();
    std::cout << "\nSimulación terminada." << std::endl;
    return 0;
}
```

1. **Diagnóstico del problema (análisis):** por un lado, se encontró que cuando uno crea un personaje, este se reserva un espacio en el `Heap` para guardar las estadísticas. Sin embargo, ese espacio se lo queda cada vez que se instancia un perosnaje (culpa de la ausencia de un método destructor), por lo que el programa irá gastando más RAM constantemente.  
El error que se encontró en el método `simularEncuentro()`, pues el método crea una copia del objeto **heroe** CON LOS DATOS ALMACENADOS EN LA MISMA DIRECCIÓN DE MEMORIA. Esto provoca que, si se busca borrar la esta memoria, el programa fallará.



2.
 ``` c++
#include <string>
#include <iostream>

class Personaje {
public:
    Personaje(std::string n, int vida, int ataque, int defensa)
        : nombre(n), vida(vida), ataque(ataque), defensa(defensa) {
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    void imprimir() const {
        std::cout << "Personaje " << nombre
            << " [Vida: " << vida
            << ", ATK: " << ataque
            << ", DEF: " << defensa
            << "]" << std::endl;
    }

    const std::string& getNombre() const { return nombre; }
    int  getVida()   const { return vida; }
    int  getAtaque() const { return ataque; }
    int  getDefensa()const { return defensa; }

    void setNombre(const std::string& n) { nombre = n; }
    void setVida(int v) { vida = v; }
    void setAtaque(int a) { ataque = a; }
    void setDefensa(int d) { defensa = d; }

private:
    std::string nombre;
    int vida;
    int ataque;
    int defensa;
};

int main() {
    Personaje heroe("Aragorn", 100, 20, 15);
    heroe.imprimir();
    heroe.setVida(80);
    std::cout << "\nle pegan\n";
    heroe.imprimir();
    return 0;
}

```
    
