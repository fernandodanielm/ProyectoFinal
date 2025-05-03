# Principio de Responsabilidad Única (SRP)

El **Principio de Responsabilidad Única (SRP)** es uno de los cinco principios **SOLID** en programación orientada a objetos. Su objetivo es mejorar la modularidad y mantenibilidad del código.

## 🔹 Propósito del SRP
El SRP establece que **una clase debe tener solo una razón para cambiar**, es decir, debe encargarse de **una única responsabilidad** dentro del sistema.

## 🔹 Tipo de Principio SOLID
El SRP es un principio de **diseño estructural**, enfocado en mejorar la **cohesión** dentro del código y reducir el **acoplamiento** innecesario.

## 🔹 Problema y Solución

### 📌 Problema:
En muchos sistemas, una sola clase suele tener **múltiples responsabilidades**. Por ejemplo, una clase `GestorTurnos` podría encargarse de:
- Administrar turnos de pacientes.
- Generar reportes médicos.
- Enviar notificaciones de turnos.

Si se necesita cambiar el formato de reportes, **toda la clase se verá afectada**, incluso aquellas partes que no están relacionadas con reportes.

### ✅ Solución con SRP:
Para cumplir con SRP, se deben **separar las responsabilidades** en distintas clases:
- `AdministradorTurnos`: Gestiona turnos médicos.
- `GeneradorReportes`: Se encarga de los informes.
- `ServicioNotificaciones`: Envía alertas y recordatorios.

De esta manera, si queremos modificar la lógica de generación de reportes, **solo afectamos a `GeneradorReportes`**, sin alterar el resto del sistema. Esto mejora la **modularidad, escalabilidad y mantenibilidad** del código.

## ✨ Beneficios del SRP
- **Código más fácil de entender y mantener**.
- **Menos impacto de cambios**, al limitar los efectos a una sola clase.
- **Mejor reutilización**, ya que cada clase tiene una responsabilidad clara.



# Motivación del Principio de Responsabilidad Única (SRP)

## 📌 Problema en el sistema  
Nuestro sistema de gestión de turnos médicos enfrentaba un problema común en el desarrollo de software: algunas clases **tenían múltiples responsabilidades**, lo que generaba **dificultades en mantenimiento, escalabilidad y reutilización**.  

Por ejemplo, la clase `GestorTurnos` manejaba varias tareas diferentes:  
- Creación, modificación y cancelación de turnos.  
- Generación de reportes médicos.  
- Envío de notificaciones a pacientes.  

Este diseño hacía que **cualquier cambio en una de estas funcionalidades afectara el resto de la clase**, aumentando el riesgo de errores inesperados y dificultando la evolución del sistema.

## ✅ Solución con SRP  
Para solucionar este problema, aplicamos el **Principio de Responsabilidad Única (SRP)** y dividimos las responsabilidades en distintas clases:  
- `AdministradorTurnos`: Se encarga exclusivamente de la gestión de turnos.  
- `GeneradorReportes`: Maneja la generación de informes médicos.  
- `ServicioNotificaciones`: Gestiona el envío de recordatorios y alertas.  

Ahora, si necesitamos modificar la forma de generar reportes, **solo cambiamos `GeneradorReportes`**, sin afectar la lógica de gestión de turnos o notificaciones.

## 🌍 Ejemplo del mundo real  
Imagina un **hospital** donde el personal administrativo, los médicos y el equipo de soporte realizan tareas completamente distintas.  
- **El personal administrativo** gestiona los registros de pacientes.  
- **Los médicos** atienden consultas y actualizan historiales clínicos.  
- **El equipo de soporte** maneja la infraestructura tecnológica.  

Si una sola persona intentara hacer todas estas funciones a la vez, el sistema se volvería caótico y propenso a errores.  
Aplicar **SRP** en software es similar a definir **roles y tareas específicas** para cada equipo en un hospital, mejorando la eficiencia y evitando conflictos innecesarios.

## ✨ Beneficios de aplicar SRP  
✔ **Menos dependencias entre módulos** (evita que un cambio afecte todo el sistema).  
✔ **Código más organizado y fácil de mantener**.  
✔ **Facilidad para agregar nuevas funciones sin modificar lo existente**.  

Este principio es clave para construir sistemas escalables y eficientes. 🚀  

# Caso Real

## Parte 2 – Aplicación de Principios SOLID en el Diseño de Clases

### Principio de Responsabilidad Única (SRP)

* **Propósito y Tipo del Principio SOLID:** El Principio de Responsabilidad Única establece que una clase debe tener una y solo una razón para cambiar. Esto significa que una clase debería tener una única responsabilidad o un único trabajo. Al adherirnos a este principio, evitamos que una clase se vuelva demasiado acoplada y frágil, ya que múltiples responsabilidades podrían llevar a que cambios en una parte afecten inesperadamente a otras. El SRP es un principio de diseño de clases.

* **Motivación:** En nuestro sistema de gestión de turnos, la clase `Paciente` podría, sin una correcta aplicación del SRP, terminar gestionando tanto la información personal del paciente (nombre, documento, contacto, historial) como la lógica relacionada con la persistencia de estos datos (guardar en la base de datos, cargar desde la base de datos). El problema con esta aproximación es que si la forma en que persistimos los datos cambia (por ejemplo, migramos a una nueva base de datos o utilizamos un nuevo ORM), la clase `Paciente` tendría que modificarse, aunque estos cambios no estén directamente relacionados con la información fundamental del paciente. Esto dificulta el mantenimiento y aumenta el riesgo de introducir errores en la lógica de negocio de la clase `Paciente`.

* **Caso Real (Descripción Textual): Separando la Responsabilidad de Persistencia del Paciente**

    Actualmente, podríamos tener una clase `Paciente` que incluye tanto la lógica de negocio del paciente (sus atributos y comportamientos relacionados con su información) como la lógica para guardar y cargar su estado desde una base de datos.

    **Problema con un Diseño No SRP (Escenario Inicial Incorrecto):**

    Si la clase `Paciente` tuviera métodos como `guardarPacienteEnDB()` y `cargarPacienteDesdeDB()`, cualquier cambio en la tecnología de la base de datos o en el esquema de la tabla `Pacientes` requeriría modificar la clase `Paciente`. Esto significa que la clase `Paciente` tendría dos razones para cambiar: cambios en la información del paciente y cambios en la persistencia del paciente, violando el SRP.

    **Aplicación del SRP (Solución Correcta):**

    Para aplicar el Principio de Responsabilidad Única, podemos separar la responsabilidad de la persistencia en una clase separada:

    1.  **Clase `Paciente` (Responsabilidad: Lógica de Negocio del Paciente):** Esta clase se enfoca únicamente en la información y el comportamiento inherente a un paciente.

        ```java
        class Paciente {
            private String nombreCompleto;
            private String numeroDocumento;
            private LocalDate fechaNacimiento;
            private String telefono;
            private String correoElectronico;
            // ... otros atributos ...

            public Paciente(String nombreCompleto, String numeroDocumento, LocalDate fechaNacimiento, String telefono, String correoElectronico) {
                this.nombreCompleto = nombreCompleto;
                this.numeroDocumento = numeroDocumento;
                this.fechaNacimiento = fechaNacimiento;
                this.telefono = telefono;
                this.correoElectronico = correoElectronico;
            }

            // ... getters y setters ...

            // Métodos relacionados con la lógica del paciente (si los hubiera)
        }
        ```

    2.  **Clase `PacienteRepository` (Responsabilidad: Persistencia del Paciente):** Esta clase se encarga de la interacción con la base de datos para guardar y cargar la información de los pacientes.

        ```java
        class PacienteRepository {
            public void guardarPaciente(Paciente paciente) {
                // Lógica para guardar el paciente en la base de datos
                System.out.println("Guardando paciente " + paciente.getNombreCompleto() + " en la base de datos.");
            }

            public Paciente cargarPaciente(String numeroDocumento) {
                // Lógica para cargar el paciente desde la base de datos
                System.out.println("Cargando paciente con documento " + numeroDocumento + " desde la base de datos.");
                // ... código para crear y retornar una instancia de Paciente ...
                return new Paciente("Nombre de Ejemplo", numeroDocumento, LocalDate.now().minusYears(30), "123456789", "ejemplo@email.com");
            }
        }
        ```

**Resultado:**

Al separar la responsabilidad de la persistencia en la clase `PacienteRepository`, la clase `Paciente` ahora tiene una única razón para cambiar: cuando la información o la lógica de negocio del paciente cambian. Los cambios en la tecnología de la base de datos o en la forma en que se almacenan los datos afectarán únicamente a la clase `PacienteRepository`. Esto hace que ambas clases sean más cohesivas, menos acopladas y más fáciles de mantener.

# Estructura de clase
[Enlace al diagrama UML Clas](https://1drv.ms/i/c/f2bf844ed8279638/EVZpKLHrUJtKtVFQPTpXhUkBOzl7YzhMQaMSNI5MiUklaw?e=mepCwR)

¡Hola desde Haedo! ¡Excelente! Aquí tienes un archivo Markdown (.md) con una breve descripción de cada Diagrama UML que construimos para ilustrar los principios SOLID, junto con código Java interpolado para dar más fundamento a cada diagrama:

Markdown

# Principios SOLID y Diagramas UML con Código Java

A continuación, se presenta una breve descripción de los Diagramas UML creados para ilustrar cada uno de los cinco principios SOLID en el contexto de nuestro sistema de gestión de turnos, junto con ejemplos de código Java interpolado.

# Principios SOLID en el Sistema de Gestión de Turnos

A continuación, se presenta la aplicación de los cinco principios SOLID en el diseño de clases de nuestro sistema de gestión de turnos, con diagramas UML y ejemplos de código Java interpolado.

## 1. Principio de Responsabilidad Única (SRP)

**Diagrama UML:**


@startuml
class Paciente {
  - telefono: String
  - correoElectronico: String
  - historialTurnos: List<Turno>
  --
  + Paciente(String, String, LocalDate, String, String)
  + getTelefono(): String
  + setTelefono(telefono: String): void
  + getCorreoElectronico(): String
  + setCorreoElectronico(correoElectronico: String): void
  + getHistorialTurnos(): List<Turno>
  + setHistorialTurnos(Turnos: List<Turno>): void
}

class PacienteRepository {
  + guardarPaciente(Paciente): void
  + cargarPaciente(String): Paciente
}

class ServicioPaciente {
  + registrarNuevoPaciente(String, String, LocalDate, String, String): Paciente
  + obtenerPacientePorDocumento(String): Paciente
}

ServicioPaciente ..> PacienteRepository : utiliza

note right of Paciente: Responsabilidad: Información del Paciente
note right of PacienteRepository: Responsabilidad: Persistencia del Paciente
@enduml

¡Hola desde Haedo! ¡Entendido! Aquí tienes todo el contenido que generamos sobre los principios SOLID, sus diagramas UML y el código Java interpolado, todo junto en un único archivo Markdown (.md):

Markdown

# Principios SOLID en el Sistema de Gestión de Turnos

A continuación, se presenta la aplicación de los cinco principios SOLID en el diseño de clases de nuestro sistema de gestión de turnos, con diagramas UML y ejemplos de código Java interpolado.

## 1. Principio de Responsabilidad Única (SRP)

**Diagrama UML:**

```java
class PacienteRepository {
    public void guardarPaciente(Paciente paciente) {
        // Lógica para guardar el paciente en la base de datos
        System.out.println("Guardando paciente " + paciente.getNombreCompleto() + " en la base de datos.");
    }

    public Paciente cargarPaciente(String numeroDocumento) {
        // Lógica para cargar el paciente desde la base de datos
        System.out.println("Cargando paciente con documento " + numeroDocumento + " desde la base de datos.");
        // ... código para crear y retornar una instancia de Paciente ...
        return new Paciente("Nombre de Ejemplo", numeroDocumento, LocalDate.now().minusYears(30), "123456789", "ejemplo@email.com");
    }
}

Descripción: El Principio de Responsabilidad Única establece que una clase debe tener una y solo una razón para cambiar. En este diagrama, la clase Paciente se encarga de la información del paciente, mientras que PacienteRepository se encarga de la persistencia. ServicioPaciente orquesta estas responsabilidades.

