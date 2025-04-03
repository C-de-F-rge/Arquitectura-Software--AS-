# PRINCIPIOS DE LA PROGRAMACIÓN

En la Programación existen algunas buenas prácticas que permiten
organizar de una mejor manera tanto equipos como procedimientos 
tanto de diseño como desarrollo; Estos elementos/principios son 
aquellos que diferencian un software de alta calidad de los demás.

***

## Los Principios SOLID

| Principio | Nombre | Descripción  | Ejemplo de Java |
|-----------|--------|-------------|----------------|
| **S** | **Single Responsibility** | Una __clase__ debe tener una sola razón para cambiar. | Una clase `ReportGenerator` solamente va a generar reportes, mientras que una clase `ReportPrinter` solamente los va a imprimir. |
| **O** | **Open/Close** | El __código__ debe estar abierto a la extención pero cerrado a la modificación. | Utilizamos la herencia de `Interfaces` en lugar de modificar clases ya existentes. | 
| **L** | **Lisvok Sustitution** | Una __subClase__ debe poder remplazar su __claseBase__ sin afectar el comportamiento esperado. | Una subClase `Cuadrado` no debería alterar la lógica de `Rectangulo` para dar un resultado esperado. |
