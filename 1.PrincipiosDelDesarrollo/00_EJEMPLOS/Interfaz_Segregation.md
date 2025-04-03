# Principio de Interfaz Segregation en Java

El principio de `Intergaz Segregation` Indica que las Interfaces no deberian hacer que las clases integren métodos que no sean necesarios; por ello en caso de requerirse debe tenerse en cuenta una re-estructuración más simplificada y ordenada.

## 🚨 Ejemplo INCORRECTO (Violación del ISP)
`RobotWorker` se ve obligado a implementar el método eat(), aunque no tiene sentido para un robot.

```java
interface Worker {
    void work();
    void eat();
}

class OfficeWorker implements Worker {
    @Override
    public void work() {
        System.out.println("Trabajando en la oficina...");
    }

    @Override
    public void eat() {
        System.out.println("Comiendo en la cafetería...");
    }
}

class RobotWorker implements Worker {
    @Override
    public void work() {
        System.out.println("Trabajando sin descanso...");
    }

    @Override // ERROR: Los Robots no comen 🤖
    public void eat() {
        throw new UnsupportedOperationException("Los robots no comen.");
    }
}
```
--- 

## ✅ Solución Correcta (Aplicando ISP)
Para corregir esto, separamos la interfaz Worker en dos interfaces más pequeñas y específicas:

```java
// Interfaces separadas según responsabilidades
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

// Clases implementan solo lo que necesitan
class OfficeWorker implements Workable, Eatable {
    @Override
    public void work() {
        System.out.println("Trabajando en la oficina...");
    }

    @Override
    public void eat() {
        System.out.println("Comiendo en la cafetería...");
    }
}

class RobotWorker implements Workable {
    @Override
    public void work() {
        System.out.println("Trabajando sin descanso...");
    }
}
```
---

### [Volver a la Unidad](/1.INTRODUCCION/Principios_Desarrollo.md)