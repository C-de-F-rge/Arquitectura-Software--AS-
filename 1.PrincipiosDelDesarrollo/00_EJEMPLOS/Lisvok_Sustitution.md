## Orincipio de Lisvok Sustitution en Java

Este principio indica que una clase hija no deberia tener que modificar una clase padre para oider realizar la acción y dar el resultado esperado.

## 🚨 Ejemplo INCORRECTO (Violación del LSP)
Imagina que tenemos una clase Rectangle y una subclase Square.

```java
class Rectangle {
    protected int width;
    protected int height;

    public void setWidth(int width) {
        this.width = width;
    }

    public void setHeight(int height) {
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}

class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        super.width = width;
        super.height = width; // Siempre igualar altura y ancho
    }

    @Override
    public void setHeight(int height) {
        super.height = height;
        super.width = height; // Siempre igualar ancho y altura
    }
}
```

### 🚨 ¿Por qué esto rompe el LSP?
Si el código espera un `Rectangle` pero recive un `square` este va a cambiar
todo su comportamiento.

```java
Rectangle rect = new Square();
rect.setWidth(5);
rect.setHeight(10);
System.out.println(rect.getArea()); // ¡El área esperada era 5 * 10 = 50, pero devuelve 100!
```
---

## ✅ Solución Correcta
En lugar de hacer que Square herede de Rectangle, podríamos usar una interfaz o clases separadas:

```java
interface Shape {
    int getArea();
}

class Rectangle implements Shape {
    protected int width;
    protected int height;

    public void setWidth(int width) { this.width = width; }
    public void setHeight(int height) { this.height = height; }
    
    @Override
    public int getArea() { return width * height; }
}

class Square implements Shape {
    private int side;

    public void setSide(int side) { this.side = side; }

    @Override
    public int getArea() { return side * side; }
}
```
---

### [Volver a la Unidad](/1.INTRODUCCION/Principios_Desarrollo.md)