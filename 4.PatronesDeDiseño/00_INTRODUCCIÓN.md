# Introducción a los patrones de Diseño

Los **Patrones de Diseño** son soluciones reutilizables a problemas los cuales es común encontrarse durante el diseño de software, *no son consideradas como código exacto, sino como plantillas que puedes utilizar para adaptar a un caso especifico a corde a tu nesecidad.*

***

## Función que Cumple en el Software
| **Propóosito** | **Explicación** |
|----------------|-------------------------|
| `📦 Reutilizar soluciones` | Evita el efecto de *Reinventar la Rueda* por medio de la implementación de soluciones ya probadas. |
| `👥 Mejorar la comunicación` | Al utilizar patrones estandar, ya conocidos, podemos facilitar el entendimiento del código al trabajar con equipos de desarrolladores. |
| `⚙ Mejorar la arquitectura` | Ayudan a que el software sea más flexible, escalable y mantenible. |

---

## Tipos de Patrones de Diseño

| **Tipo** | **Propósito** | **Ejemplos** |
|---------------|------------------------------|-----------------|
| [Patrones Creacionales](/4.PatronesDeDiseño/01_Creacionales.md) | Cómo se **crean** los *Objetos* |` Singleton`,`Factory Method`, `Abstract Factory`, `Builder Prototype`. |
| [Patrones Estructurales](/4.PatronesDeDiseño/02_Estructurales.md) | Cómo se **componen** los *Objetos* y las *Clases* | `Adapter`,`Composite`, `Decorator`, `Proxy`, `Facade`, `Bridge`, `Flyweight`. |
| [Patrones de Comportamiento](/4.PatronesDeDiseño/03_Comportamiento.md) | Cómo se **Comunican** los *Objetos* y como se comunican | `Observer`,`Strategy`, `Command`, `State`, `Iterator`, `Mediator`, `Template Method`, `Chain Responsibility`. |