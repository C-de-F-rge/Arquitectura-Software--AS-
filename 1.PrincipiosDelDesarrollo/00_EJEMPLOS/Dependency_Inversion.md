# Principio Dependency Inversion en Java

Este principio Indica que las Interfaces deben ser abstracciones que no debendan de los detalles; al contrario, los detalles deben depender de estas y poder ser modificados sin necesidad de cambiar la Interfaz.

```java
// La INTERFAZ define la abstracción (solo métodos, sin implementación)
interface UserRepository {
    void getData();
}

// Implementación 1: MySQL
class MySQLRepository implements UserRepository {
    public void getData() {
        System.out.println("Obteniendo datos desde MySQL");
    }
}

// Implementación 2: PostgreSQL
class PostgreSQLRepository implements UserRepository {
    public void getData() {
        System.out.println("Obteniendo datos desde PostgreSQL");
    }
}

// Service: Consume las implementaciones  sin necesidad de afectar el Modulo principal (UserRepository);
class UserService {
    private UserRepository repository;

    public UserService(UserRepository repository) { // Recibe una implementación de UserRepository
        this.repository = repository;
    }

    public void getUserData() {
        repository.getData();
    }
}
```
---

### [Volver a la Unidad](/1.INTRODUCCION/Principios_Desarrollo.md)