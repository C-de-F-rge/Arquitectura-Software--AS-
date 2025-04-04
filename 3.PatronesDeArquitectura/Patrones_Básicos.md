# Patrones de Arquitectura Básicos 

Estos son los más comunes y sirven como base para diseñar software escalable y mantenible:

| **Patrón** | **Descripción** | **Ventajas** | **Desventajas** |
|----------------------|---------------------|-----------|------------|
| `Monolítico` | Toda la aplicación se ejecuta en un solo proyecto o servidor. | ✔Facil de desarrollar y desplegar. <br> ✔Ideal para proyectos pequeños. | ❌Mayor complejidad en la gestión y comunicación entre servicios. | 
| `Cliente-Servidor` | Separa la lógica de un cliente(`interfaz`) y un servidor(`backend`) | ✔Permite distribuir la carga de trabajo. <br> ✔Facilita la evolución del cliente y servidor por separado. | ❌Puede generar problemas de latencia y dependencia de red. |
| `Capas(Layered Architecture)` | Divide la lógica en capas(`Presentación, lógica de negocio,datos`) | ✔ Organiza el código en módulos reutilizables. <br> ✔ Facilita pruebas y mantenimiento. | ❌ Puede generar sobrecarga en el rendimiento si hay demasiadas capas. |
| `MicroKernel (Plugin Architecture)` | Se basa en su núcleo mínimo con funcionalidades extendidas por plugins. | ✔Flexible y extensible sin afectar el núcleo. <br> ✔Ideal para sistemas modulares. | ❌puede aumentar la complejidad en la gestión de plugins. |
| `Model View Controller(MVC)` | Separa la aplicación en Modelo(`datos`), vista(`interfaz`) y controlador(`lógica`). | ✔Organización clara y modular. <br> ✔Separación de responsabilidades. | ❌Puede volverse dificil de gestionar en aplicaciones grandes. | 
| `MVVM(Model-view-viewModel)` | Variante de MVC usada en aplicaciones con fuerte separación de UI y lógica. | ✔Facilita pruebas y separación de lógica de UI. <br> ✔ Excelente para aplicaciones de frontend moderno. | ❌Mayor complejidad y curva de aprendizaje. |