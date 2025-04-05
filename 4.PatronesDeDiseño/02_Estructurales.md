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

