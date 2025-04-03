# Principio Open/Close en Java

Las `Clases` deberian estar abiertas a la expanción y cerradas a la modificación.

### 🚨 Ejemplo INCORRECTO (Violación del OCP)
```java
class AreaCalculator {
    public double calculateArea(Object shape) {
        double area = 0;

        if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            area = Math.PI * c.radius * c.radius;
        } else if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            area = r.width * r.height;
        }

        return area;
    }
}

class Circle {
    double radius;

    public Circle(double radius) {
        this.radius = radius;
    }
}

class Rectangle {
    double width, height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
}
```

### ✅ Solución Correcta (Aplicando OCP)

```java
// Interfaz que define el comportamiento común
interface Shape {
    double calculateArea();
}

// Clases concretas
class Circle implements Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {
    private double width, height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }
}

// Ahora el calculador de áreas es completamente genérico
class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}

// Uso en el main
public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        Shape rectangle = new Rectangle(4, 6);

        AreaCalculator calculator = new AreaCalculator();

        System.out.println("Área del círculo: " + calculator.calculateArea(circle));
        System.out.println("Área del rectángulo: " + calculator.calculateArea(rectangle));
    }
}
```
---

### [Volver a la Unidad](/1.INTRODUCCION/Principios_Desarrollo.md)