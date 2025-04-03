# PRINCIPIOS DEL DESARROLLO DE SOFTWARE 

En el desarrollo de software existen algunas buenas prácticas que permiten organizar de una mejor manera tanto equipos como procedimientos tanto de diseño como desarrollo; Estos elementos/principios son aquellos que diferencian un software de alta calidad de los demás.

***

## Los Principios SOLID

| Principio | Nombre | Descripción  | Ejemplo de Java |
|-----------|--------|-------------|----------------|
| **S** | **Single Responsibility** | Una __clase__ debe tener una sola razón para cambiar. | Una clase `ReportGenerator` solamente va a generar reportes, mientras que una clase `ReportPrinter` solamente los va a imprimir. |
| **O** | **Open/Close** | El __código__ debe estar abierto a la extención pero cerrado a la modificación. | Utilizamos la herencia de `Interfaces` en lugar de modificar clases ya existentes. | 
| **L** | **Lisvok Sustitution** | Una __subClase__ debe poder remplazar su __claseBase__ sin afectar el comportamiento esperado. | Una subClase `Cuadrado` no debería alterar la lógica de `Rectangulo` para dar un resultado esperado. |
| **I** | Interface Segregation | Las `interfaces` debe ser específicas, no forzar las clases a implementar métodos inecesarios. | En vez de implementar una Interfaz `Worker` con muchos métodos, es mejor dividirla en `Eater` y `Sleeper` |
| **D** | **Dependency Inversion** | Los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones. Las abstracciones no deben depender de los detalles. Los detalles deben depender de las abstracciones. | En lugar de depender de una clase concreta `MySQLDatabase`, se usa una interfaz `Database`. |

---

## Ejemplos de Aplicación:


- [Single Responsibility Principle(`SRP`)](/1.INTRODUCCION/00_EJEMPLOS/Single_Responsibility.md)

- [Open/Close Principle(`OCP`)](/1.INTRODUCCION/00_EJEMPLOS/Open_Close.md)

- [Lisvok Sustitution Principle(`LSP`)](/1.INTRODUCCION/00_EJEMPLOS/Lisvok_Sustitution.md)

- [Interfaz Segregation Principle(`ISP`)](/1.INTRODUCCION/00_EJEMPLOS/Interfaz_Segregation.md)

- [Dependency Inversion Principle(`DIP`)](/1.INTRODUCCION/00_EJEMPLOS/Dependency_Inversion.md)