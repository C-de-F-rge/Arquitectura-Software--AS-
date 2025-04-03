# Las Pruebas Funcionales

Son las pruebas que se encargan de verificar que el software funcione, solamente enfocandose en el funcionamiento más no en el proceso.

| **Tipo de Prueba** | **Descripción** | **Ejemplo en Java** |
|---------------------|----------------------------------------|-----------------------------------|
| `Pruebas Unitarias` | Verifica el funcionamiento de un componente en concreto. | Utilizamos `JUnit` para probar métodos individuales. |
| `Pruebas de Integración` | Verifica la Interacción entre varios modulos y sistemas | Utilizamos `SpringBoot Test` para probar la conexión entre servicios y servidores. |
| `Pruebas del Sistema` | Verifica el sistema completo para asegurarse que cumple los requerimientos | Utilizamos `Selenium` para probar la aplicación de extremo a extremo. |
| `Pruebas de Aceptación` |  Se realizan desde la pespectiva del usuario final para determinar si el software cumple con las expectativas. | Utilizamos herramientas como `Cucumber` en esenarios de lenguaje natural |
| `Pruebas de Regresión` | Se ejecutan para asegurarse que los cambios más recientes no hayan afectado las funcionalidades previas o si es necesario realizar RollBack | Utilizamos `Junit` con `Suites` para ejecutar varias pruebas automáticamente |
| `Pruebas de Carga` | Evalua el rendimiento del sistema bajo ciertas condiciones de carga | Utilizamos `JMeter` o `Gatling` para simular multiples usuarios. | 
| `Pruebas de Seguridad` | Buscan vulnerabilidades en el software para protegerlo contra ataques. | Utilizamos herramientas como `OWASP ZAP` para detectar vulnerabilidades. |
| `Pruebas de Usabilidad` | Asegura que la Interfaz sea fácil de manejar y cumpla con las expectativas del usuario. | Utilizamos test con usuarios reales y herramientas como `Hotjar` para analizar interacciones. | 