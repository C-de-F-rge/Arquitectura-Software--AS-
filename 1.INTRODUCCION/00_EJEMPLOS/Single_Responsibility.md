# Ejemplo de Principio de Single Responsability en Java

### **Clase ReportGenerator:** SOLAMENTE para `genera un Reporte`
```java
import java.io.File;
import java.io.IOException;

public class ReporGenerator{
    public static void main(String[] args){
        File reporte = new File("Reporte.Txt");

        try{
            if(reporte.createdNewFile()){
                System.out.println("Reporte Creado: " +  reporte.getName());
            }else{
                System.out.println("El Reporte ya Existe.");
            }   
        }catch(IOException e){
            System.out.println("Error al crear el reporte" + e.getMessage());
            e.printStackTrace();
        }
    }
}
```
---
### **Clase ReportWriter:** SOLAMENTE para escribier en el `reporte creado`
```java
import java.io.FileWriter;
import java.io.BufferedWriter;
import java.io.IOException;

public class ReportWriter {
    public static void main(String[] args) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("Reporte.txt", true))) {
            writer.write("Hola, este es un mensaje en el archivo.\n");
            writer.newLine();
            System.out.println("Texto escrito en el archivo.");
        } catch (IOException e) {
            System.out.println("Error al escribir en el archivo.");
            e.printStackTrace();
        }
    }
}
```
---
### **Clase ReportReader:** SOLAMENTE pare `leer un reporte`
```java
import java.io.FileReader;
import java.io.BufferedReader;
import java.io.IOException;

public class ReportReader {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("Report.txt"))) {
            String linea;
            while ((linea = reader.readLine()) != null) {
                System.out.println(linea);
            }
        } catch (IOException e) {
            System.out.println("Error al leer el archivo.");
            e.printStackTrace();
        }
    }
}
```