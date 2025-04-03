# Las Pruebas No-Funcionales

Las pruebas no funcionales son aquellas que evaluan aspectos que no tienen que ver con el funcionamiento del sistema, sino con su rendimiento, seguridad, usabilidad, escalabilidad, etc.


| **Tipo de Prueba** | **Descripción** | **Ejemplo en Java** |
|---------------------|----------------------------------------|-----------------------------------|
| `Pruebas de Rendimiento` | Miden la velocidad, capacidad de respuesta y estabilidad del sistema. | Utilizamos `JMeter` para simular multiples usuarios y analizar tiempos de respuesta. | 
| `Pruebas de Carga` | Evalúan el comportamiento del sistema bajo carga esperada. | Utilizamos `java GatlingTestSimulation.class` con `Gatling` para simular usuarios. |
| `Pruebas de Estrés` | Se aplican cargas extremas para medir el límite del sistema. | Utilizamos `JMeter` para aumentar el número de solicitudes concurrentes. |
| `Pruebas de Seguridad` | Buscan vulnerabilidades en el software contra ataques. | Utilizamos `OWASP ZAP` para detectar vulnerabilidades de seguridad en APIs y aplicaciones web. |
| `Pruebas de Usabilidad` | Evalúan la facilidad de uso e interfaz de usuario. | Utilizamos Pruebas de usuarios reales y la herramienta `HotJar` para analizar la interacción con la UI |
| `Pruebas de Compatibilidad` | Verifica el funcionamiento del sisteman en diferentes dispositivos, navegadores y sistemas operativos. | Utilizamos `Selenium Grid` para probar en diversos navegadores automáticamente. |
| `Pruebas de Recuperación` | Evaluan la capacidad del sistema para recuperar fallos | Utilizamos la simulación de caídas de servidor y recuperación con `Docker` y `Kubernetes`. |
| `Pruebas de Escalabilidad` | Determinan si el sistema puede manejar el crecimiento de usuarios y datos. | Utilizamos las pruebas con `Gatling` para medir como aumenta el rendimiento con más usuarios. |
| `Pruebas de Confiabilidad` | Analizan la estabilidad del sistema bajo uso continuo durante largos periodos de tiempo | Se ejecutan pruebas con `JUnit + Mockito` en escenarios prolongados. |