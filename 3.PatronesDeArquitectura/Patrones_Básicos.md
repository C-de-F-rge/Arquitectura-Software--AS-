# Patrones Básicos

Estos son los más comunes y sirven como base para diseñar software escalable y mantenible:

| **Patrón** | **Descripción** | **Ventajas** | **Desventajas** |
|----------------------|---------------------|-----------|------------|
| `Monolítico` | Toda la aplicación se ejecuta en un solo proyecto o servidor. | ✔Facil de desarrollar y desplegar. <br> ✔Ideal para proyectos pequeños. | ❌Mayor complejidad en la gestión y comunicación entre servicios. | 
| `Event-Driven` | la comunicación entre componentes se basa en eventos en lugar de llamadas directas | ✔Alta Escalabilidad y Desacoplamiento. <br> ✔Ideal para sistemas distribuidos. | ❌Dificil de depurar y mantener debido a la asincronía. |
| `Hexagonal (Ports & Adapters)` | Separa la Lógica de negocio de las interfaces externas | ✔ Facilita cambios tecnológicos sin afectar la lógica central. <br> ✔ Alta modularidad y testabilidad. | ❌ Puede ser complejo de implementar en proyectos pequeños. |