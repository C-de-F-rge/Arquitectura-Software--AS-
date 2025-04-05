# Patrones Creacionales

Son aquellos que se basan en cómo se crean los objetos. existen los siguientes patrones para brindar soluciones rapidas y eficientes:

***

## Singleton

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Garantiza que la clase tenga una unica instancia para todo el sistema y proporciona un punto de acceso global |
| `¿Cuándo Usarlo?` | 📌Cuando se necesite una unica instancia de un recurso(*como la conección a base de datos, logger, configuración Global*). <br> 📌Cuando quieres controlar estrictamente el acceso al recurso. |


### 🧪Ejemplo en Java

```java
public class Configuracion {

    // 1. Instancia privada y estática
    private static Configuracion instancia;

    // 2. Constructor privado
    private Configuracion() {
        System.out.println("Configuración cargada");
    }

    // 3. Método de acceso público
    public static Configuracion getInstance() {
        if (instancia == null) {
            instancia = new Configuracion();
        }
        return instancia;
    }
}
```
### 💡 Uso:
```java
public class Main {
    public static void main(String[] args) {
        Configuracion c1 = Configuracion.getInstance();
        Configuracion c2 = Configuracion.getInstance();

        System.out.println(c1 == c2);  // true (misma instancia)
    }
}
```

***

## Factory Method

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Permite crear objetos sin especificar la clase exacta del objeto que se va a crear. Delegamos la creación a las subclases. |
| `¿Cuándo Usarlo?` | 📌Cuando no sabemos de antemano que tipo de objeto necesitamos. <br> 📌Cuando quieres dejar la desición de creación a subclases. <br> 📌Cuando trabajas con `interfaces`, `clases abstractas` y necesitas flexibilidad. |

### 🧪Ejemplo en Java con Interfaces

```java
public interface Transporte { //Creamos una Interfaz
    void entregar();
}

public class Camion implements Transporte{ //Creamos unas implementaciones
    @Override
    public void entregar(){
        System.out.println("Entrega en Camión...");
    }
}

public class Barco implements Transporte {
    @Override
    public void entregar() {
        System.out.println("Entrega en barco.");
    }
}

public abstract class Logistica{ // Creamos una abstracción de la Interfaz
    public abstract Transporte crearTransporte();
}

public class LogisticaTerrestre extends Logistica{// Extendemos la abstracción.
    @Override
    public Transporte crearTransporte(){
        return new Camion();
    }
}

public class LogisticaMaritima extends Logistica{
    @Override
    public Transporte creararTransporte(){
        return new Barco();
    }
}

```

### 💡 Uso:
```java
public class Main {
    public static void main(String[] args) {
        Logistica logistica1 = new LogisticaTerrestre();
        Transporte t1 = logistica1.crearTransporte();
        t1.entregar();  // Entrega en camión.

        Logistica logistica2 = new LogisticaMaritima();
        Transporte t2 = logistica2.crearTransporte();
        t2.entregar();  // Entrega en barco.
    }
}
```
***

## Abstract Factory

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Permite crear familias de objetos realacionadas o dependientes sin especificar sus clases concretas. Es como una `Fabrica de Fabricas` |
| `¿Cuándo Usarlo?` | 📌Cuando el sistema debe ser independiente de como se crean, componen y representan sus productos. <br> 📌Cuando necesitas asegurarte que los objetos de una misma familia sean compatibles entre si. |


### 🧪Ejemplo en Java

```java
//Interfaces de objetos 
public interface boton{
    void pintar();
}

public interface checkbox{
    void seleccionar();
}

//Implementacion para objetos de color claro.
public class BotonClaro implements Boton {
    @Override
    public void pintar() {
        System.out.println("Botón claro pintado.");
    }
}

public class CheckboxClaro implements Checkbox {
    @Override
    public void seleccionar() {
        System.out.println("Checkbox claro seleccionado.");
    }
}

//Implementación de objetos de color oscuro.
public class BotonOscuro implements Boton {
    @Override
    public void pintar() {
        System.out.println("Botón oscuro pintado.");
    }
}

public class CheckboxOscuro implements Checkbox {
    @Override
    public void seleccionar() {
        System.out.println("Checkbox oscuro seleccionado.");
    }
}

//Abstract Factory
public interface GUIFactory {
    Boton crearBoton();
    Checkbox crearCheckbox();
}

//Factories Concretas
public class TemaClaroFactory implements GUIFactory {
    @Override
    public Boton crearBoton() {
        return new BotonClaro();
    }

    @Override
    public Checkbox crearCheckbox() {
        return new CheckboxClaro();
    }
}

public class TemaOscuroFactory implements GUIFactory {
    @Override
    public Boton crearBoton() {
        return new BotonOscuro();
    }

    @Override
    public Checkbox crearCheckbox() {
        return new CheckboxOscuro();
    }
}

//Cliente
public class Aplicacion {
    private Boton boton;
    private Checkbox checkbox;

    public Aplicacion(GUIFactory factory) {
        boton = factory.crearBoton();
        checkbox = factory.crearCheckbox();
    }

    public void renderizarUI() {
        boton.pintar();
        checkbox.seleccionar();
    }
}
```
### 💡 Uso:
```java
public class Main {
    public static void main(String[] args) {
        GUIFactory factory = new TemaOscuroFactory();  // o TemaClaroFactory
        Aplicacion app = new Aplicacion(factory);
        app.renderizarUI();
    }
}
```

***

## Builder Prototype

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Se utiliza para construir objetos complejos paso a paso, separando la construcción del objeto de su presentación. |
| `¿Cuándo Usarlo?` | 📌Cuando un objeto tiene muchas opciones de construcción o configuración. <br> 📌Cuando quieres evitar constructores con demasiados parametros. <br> 📌Cuando quieres reutilizar un mismo proceso de construcción para diferentes representaciones. |


### 🧪Ejemplo en Java

```java
//Producto
public class Computadora {
    private String cpu;
    private String ram;
    private String almacenamiento;

    public void setCpu(String cpu) {
        this.cpu = cpu;
    }

    public void setRam(String ram) {
        this.ram = ram;
    }

    public void setAlmacenamiento(String almacenamiento) {
        this.almacenamiento = almacenamiento;
    }

    public void mostrarInfo() {
        System.out.println("CPU: " + cpu + ", RAM: " + ram + ", Almacenamiento: " + almacenamiento);
    }
}

//Builder(Interface)
public interface ComputadoraBuilder {
    void construirCpu();
    void construirRam();
    void construirAlmacenamiento();
    Computadora obtenerComputadora();
}

//Builder Concreto(Implementaciones)
public class ComputadoraGamingBuilder implements ComputadoraBuilder {
    private Computadora computadora = new Computadora();

    @Override
    public void construirCpu() {
        computadora.setCpu("Intel i9");
    }

    @Override
    public void construirRam() {
        computadora.setRam("32GB");
    }

    @Override
    public void construirAlmacenamiento() {
        computadora.setAlmacenamiento("1TB SSD");
    }

    @Override
    public Computadora obtenerComputadora() {
        return computadora;
    }
}

//Director
public class Director {
    private ComputadoraBuilder builder;

    public Director(ComputadoraBuilder builder) {
        this.builder = builder;
    }

    public void construirComputadora() {
        builder.construirCpu();
        builder.construirRam();
        builder.construirAlmacenamiento();
    }

    public Computadora obtenerComputadora() {
        return builder.obtenerComputadora();
    }
}

```
### 💡 Uso:
```java
public class Main {
    public static void main(String[] args) {
        ComputadoraBuilder builder = new ComputadoraGamingBuilder();
        Director director = new Director(builder);
        director.construirComputadora();
        Computadora pc = director.obtenerComputadora();
        pc.mostrarInfo();  // CPU: Intel i9, RAM: 32GB, Almacenamiento: 1TB SSD
    }
}
```