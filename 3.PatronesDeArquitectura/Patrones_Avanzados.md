# Patrones de Arquitectura Avanzados

Estos patrones son más complejos y usados en sistemas de alto rendimiento y escalabilidad:

| **Patrón** | **Descripción** | **Ventajas** | **Desventajas** |
|----------------------|---------------------|-----------|------------|
| `Microservicios` | Divide la aplicación en servicios pequeños e independientes. | ✔ Escalabilidad y flexibilidad. <br> ✔ Cada servicio puede desarrollarse con tecnología independiente. | ❌Mayor complejidad en la gestión y comunicación entre servicios. | 
| `Event-Driven` | la comunicación entre componentes se basa en eventos en lugar de llamadas directas | ✔Alta Escalabilidad y Desacoplamiento. <br> ✔Ideal para sistemas distribuidos. | ❌Dificil de depurar y mantener debido a la asincronía. |
| `Hexagonal (Ports & Adapters)` | Separa la Lógica de negocio de las interfaces externas | ✔ Facilita cambios tecnológicos sin afectar la lógica central. <br> ✔ Alta modularidad y testabilidad. | ❌ Puede ser complejo de implementar en proyectos pequeños. |
| `CQRS(Comand Query Responsibility Segregation)` | Separa las operaciones de lectura y escritura | ✔Mejora de rendimiento en Base de Datos. <br> ✔Facilita la escalabilidad en sistemas con muchas lecturas. | ❌Aumenta la complejidad al manejar dos modelos de datos diferentes. |
| `Saga` | Maneja transacciones distribuidas en microservicios mediante eventos | ✔Garantiza consistencia en sistemas distribuidos. <br> ✔Permite manejar fallos sin bloquear el sistema. | ❌Requiere arquitectura bien definida y puede ser difícil de depurar. | 
| `Serverless` | Despliega funciones en la nube sin gestionar servidores. | ✔Reducción de costos, pago solo por uso. <br> ✔Escalabilidad automética. | ❌Dependencia de provedores cloud <br> ❌Tiempo de respuesta variable(cold starts). |
| `Clean Architecture` | Divide el software en capas concentricas con separación de responsabilidades. | ✔Alata mantenibilidad y desacoplamiento <br> ✔Facilita la evolución del software | ❌Mayor curva de aprendizaje y tiempo de implementación inicial. |
| `Onion Architecture` | Similar a Clean Architecture pero enfatiza en la independencia del núcleo de negocio. | ✔Modularidad extrema y testabilidad. <br> ✔Separación total de dependencias externas. | ❌Puede ser excesivo para proyectos pequeños o medianos. |