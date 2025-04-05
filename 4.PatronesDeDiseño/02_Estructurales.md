# Patrones de Diseño Estructurales

***

## Adapter

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Permite que dos clases que no son compatibles puedan trabajar juntas adaptando una interfaz a otra esperada por el cliente. |
| `¿Cuándo Usarlo?` | 📌Cuando tienes una clase ya existente que quieras reulizar, pero su interfaz no es compatible con lo que espera tu sistema. <br> 📌Cuando quieres implementar bibliotecas externas sin modificar su código. |

### 🧪Ejemplo en Java

```java
// Interfaz esperada por el cliente
public interface EnchufeAmericano {
    void conectarConClavijaPlana();
}

//Clase existente incompatible (enchufe europeo)
public class EnchufeEuropeo {
    public void conectarConClavijaRedonda() {
        System.out.println("Conectado con clavija redonda (europea)");
    }
}

//Adaptador
public class AdaptadorEuropeoAAmericano implements EnchufeAmericano {
    private EnchufeEuropeo enchufeEuropeo;

    public AdaptadorEuropeoAAmericano(EnchufeEuropeo enchufeEuropeo) {
        this.enchufeEuropeo = enchufeEuropeo;
    }

    @Override
    public void conectarConClavijaPlana() {
        // Adaptamos la clavija redonda a la plana
        System.out.println("Adaptador convierte la clavija redonda en plana...");
        enchufeEuropeo.conectarConClavijaRedonda();
    }
}

//Cliente
public class Cliente {
    public static void main(String[] args) {
        EnchufeEuropeo europeo = new EnchufeEuropeo();
        EnchufeAmericano adaptador = new AdaptadorEuropeoAAmericano(europeo);

        adaptador.conectarConClavijaPlana();
    }
}


```

### 💡 Uso:
```java
public class Cliente {
    public static void main(String[] args) {
        EnchufeEuropeo europeo = new EnchufeEuropeo();
        EnchufeAmericano adaptador = new AdaptadorEuropeoAAmericano(europeo);

        adaptador.conectarConClavijaPlana();
    }
}
```

***

## Composite

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Permite trabajar objetos individuales y compuestos de manera Uniforme, ideal para estructuras jerárquicas como menús, archivos,carpetas,etc. |
| `¿Cuándo Usarlo?` | 📌Cuando quieras representar una jerarquía parte-todo.. <br> 📌Cuando necesitas recorrer objetos individuales y conjuntos sin preocuparte por su tipo.. |

### 🧪Ejemplo en Java

```java
//Componente (Interfaz)
public interface ArchivoComponente {
    void mostrar();
}

//Hoja(Archivo Individual)
public class Archivo implements ArchivoComponente {
    private String nombre;

    public Archivo(String nombre) {
        this.nombre = nombre;
    }

    @Override
    public void mostrar() {
        System.out.println("Archivo: " + nombre);
    }
}

//Compuesto(Carpeta que contiene Archivos y otras carpetas)
import java.util.ArrayList;
import java.util.List;

public class Carpeta implements ArchivoComponente {
    private String nombre;
    private List<ArchivoComponente> elementos = new ArrayList<>();

    public Carpeta(String nombre) {
        this.nombre = nombre;
    }

    public void agregar(ArchivoComponente componente) {
        elementos.add(componente);
    }

    @Override
    public void mostrar() {
        System.out.println("Carpeta: " + nombre);
        for (ArchivoComponente componente : elementos) {
            componente.mostrar();
        }
    }
}


```
s
### 💡 Uso:
```java
public class Cliente {
    public static void main(String[] args) {
        ArchivoComponente archivo1 = new Archivo("foto.jpg");
        ArchivoComponente archivo2 = new Archivo("documento.pdf");

        Carpeta carpetaPersonal = new Carpeta("Personal");
        carpetaPersonal.agregar(archivo1);
        carpetaPersonal.agregar(archivo2);

        ArchivoComponente archivo3 = new Archivo("proyecto.zip");
        Carpeta carpetaTrabajo = new Carpeta("Trabajo");
        carpetaTrabajo.agregar(archivo3);
        carpetaTrabajo.agregar(carpetaPersonal); // carpeta dentro de otra carpeta

        carpetaTrabajo.mostrar();
    }
}
```

***

## Decorator

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Permite agregar funcionalidades y responsabilidades a un objeto dinámivamente sin modificar su estructura. |
| `¿Cuándo Usarlo?` | 📌 Cuando necesitas añadir funcionalidades a objetos individuales sin afectar a otros. <br> 📌Cuando no quieres alterar la clase base (por ejemplo, si viene de una biblioteca externa). |

### 🧪Ejemplo en Java

```java
//Componente
public interface Bebida {
    String getDescripcion();
    double getCosto();
}

//Componente Concreto
public class Cafe implements Bebida {
    @Override
    public String getDescripcion() {
        return "Café";
    }

    @Override
    public double getCosto() {
        return 2.0;
    }
}

//Decorador Abstracto
public abstract class BebidaDecorador implements Bebida {
    protected Bebida bebida;

    public BebidaDecorador(Bebida bebida) {
        this.bebida = bebida;
    }

    public abstract String getDescripcion();
    public abstract double getCosto();
}

//Decoradores Concretos (con leche y con chocolate)
public class ConLeche extends BebidaDecorador {
    public ConLeche(Bebida bebida) {
        super(bebida);
    }

    @Override
    public String getDescripcion() {
        return bebida.getDescripcion() + " + Leche";
    }

    @Override
    public double getCosto() {
        return bebida.getCosto() + 0.5;
    }
}

public class ConChocolate extends BebidaDecorador {
    public ConChocolate(Bebida bebida) {
        super(bebida);
    }

    @Override
    public String getDescripcion() {
        return bebida.getDescripcion() + " + Chocolate";
    }

    @Override
    public double getCosto() {
        return bebida.getCosto() + 0.7;
    }
}



```

### 💡 Uso:
```java
//Cliente
public class Cliente {
    public static void main(String[] args) {
        Bebida bebida = new Cafe(); // Café básico
        bebida = new ConLeche(bebida); // Agregamos leche
        bebida = new ConChocolate(bebida); // Y luego chocolate

        System.out.println("Pedido: " + bebida.getDescripcion());
        System.out.println("Costo: $" + bebida.getCosto());
    }
}
```