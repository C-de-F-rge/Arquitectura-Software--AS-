# Patrones Creacionales

Son aquellos que se basan en cómo se crean los objetos. existen los siguientes patrones para brindar soluciones rapidas y eficientes:

***

## Singleton

| **Categoría** | **Detaller** |
|-----------|-----------------------|
| `¿Para qué sirve` | Garantiza que la clase tenga una unica instancia para todo el sistema y proporciona un punto de acceso global |
| `¿Cuándo Usarlo?` | 📌Cuando se necesite una unica instancia de un recurso(*como la conección a base de datos, logger, configuración Global*). <br> 📌Cuando quieres controlar estrictamente el acceso al recurso. |

---

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
