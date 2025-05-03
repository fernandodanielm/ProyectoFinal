# Principio de Segregación de Interfaces (ISP)

El **Principio de Segregación de Interfaces (ISP)** es uno de los principios **SOLID**, diseñado para evitar que una clase implemente métodos que no necesita.

## 🔹 Propósito del ISP  
El ISP establece que **una interfaz nunca debe obligar a una clase a implementar métodos que no utiliza**. En lugar de tener una sola interfaz gigante con múltiples métodos, es mejor definir **varias interfaces más pequeñas y específicas** para cada funcionalidad.

## 🔹 Tipo de Principio SOLID  
Este principio pertenece a la categoría de **diseño estructural**, ayudando a reducir **el acoplamiento** en las clases y promoviendo **interfaces más cohesionadas**.

## 📌 Problema y Solución  

### 📌 Problema:  
Supongamos que en nuestro sistema de gestión de turnos médicos tenemos una interfaz `Usuario`, que define varios métodos:  
- `registrar()`,  
- `consultarTurno()`,  
- `crearTurno()`,  
- `generarReporte()`.  

Ahora, `Paciente` implementa `Usuario`, pero **no necesita el método `generarReporte()`**. Del mismo modo, `ProfesionalSalud` necesita `generarReporte()`, pero **no debería implementar `crearTurno()`** porque no gestiona turnos directamente.  

Esto **viola ISP**, ya que las clases están obligadas a implementar métodos innecesarios.

### ✅ Solución con ISP:  
Para resolver este problema, se dividen las responsabilidades en **interfaces más específicas**, en lugar de una sola interfaz `Usuario`:  
1. `InterfazTurno` → Para clases que gestionan turnos (`Paciente`, `PersonalAdministrativo`).  
2. `InterfazReportes` → Para clases que generan reportes (`ProfesionalSalud`).  

Ahora, cada clase **solo implementa la interfaz que realmente necesita**, evitando código innecesario y haciendo el sistema más modular.

## ✨ Beneficios de aplicar ISP  
✔ **Evita que las clases implementen métodos innecesarios**.  
✔ **Facilita la reutilización de código y reduce el acoplamiento**.  
✔ **Promueve el diseño modular y escalable**.  

 # Motivación del Principio de Segregación de Interfaces (ISP)

## 📌 Problema en el sistema  
Nuestro sistema de gestión de turnos médicos enfrentaba un problema relacionado con **interfaces mal diseñadas**. Habíamos creado una interfaz `Usuario`, que incluía varios métodos:  
- `registrar()`,  
- `consultarTurno()`,  
- `crearTurno()`,  
- `generarReporte()`.  

El problema surgía porque **no todos los actores necesitaban implementar todos los métodos**.  
- `Paciente` necesitaba `consultarTurno()`, pero **no `generarReporte()`**.  
- `ProfesionalSalud` necesitaba `generarReporte()`, pero **no `crearTurno()`**.  

Esto generaba **clases innecesariamente grandes**, donde las implementaciones estaban forzadas a incluir métodos que no utilizaban. Como resultado, el código se volvía difícil de modificar y escalar.

## ✅ Solución con ISP  
Para solucionar este problema, aplicamos el **Principio de Segregación de Interfaces (ISP)** y **dividimos la interfaz en varias interfaces más específicas**.  
En lugar de una única interfaz `Usuario`, creamos:  
- `InterfazTurno` → Para clases que gestionan turnos (`Paciente`, `PersonalAdministrativo`).  
- `InterfazReportes` → Para clases que generan reportes (`ProfesionalSalud`).  

Así, cada clase **solo implementa la interfaz que realmente necesita**, evitando código innecesario y haciendo el sistema más modular.

## 🌍 Ejemplo del mundo real  
Imagina un sistema de **vehículos eléctricos** donde cada vehículo tiene distintas funcionalidades. Si se crea una interfaz `Vehiculo` con métodos como `cargarBatería()`, `llenarTanqueCombustible()`, y `ajustarPresiónNeumáticos()`, **se estaría obligando a los autos eléctricos a implementar `llenarTanqueCombustible()`** aunque no lo necesitan.  

La solución con **ISP** sería dividir `Vehiculo` en múltiples interfaces:  
- `Electrico` → Contiene `cargarBatería()`.  
- `Combustible` → Contiene `llenarTanqueCombustible()`.  
- `Mantenimiento` → Contiene `ajustarPresiónNeumáticos()`.  

De esta manera, **cada vehículo implementa solo la interfaz que le corresponde**, sin depender de métodos irrelevantes.

## ✨ Beneficios de aplicar ISP  
✔ **Evita que las clases implementen métodos innecesarios**.  
✔ **Facilita la reutilización de código y reduce el acoplamiento**.  
✔ **Promueve el diseño modular y escalable**.  

 # Caso Real

 ## Parte 2 – Aplicación de Principios SOLID en el Diseño de Clases

### Principio de Segregación de Interfaces (ISP)

* **Propósito y Tipo del Principio SOLID:** El Principio de Segregación de Interfaces establece que ninguna clase cliente debería ser forzada a depender de métodos que no utiliza. Esto significa que es mejor tener múltiples interfaces específicas para cada cliente que una interfaz general que contenga métodos que algunos clientes no necesitan. El ISP es un principio de diseño de interfaces.

* **Motivación:** En nuestro sistema, podríamos tener diferentes tipos de clientes que interactúan con la información de los `ProfesionalSalud`. Por ejemplo, la `AgendaTurnos` necesita acceder al horario de atención y a la especialidad (si es un médico), mientras que un componente de generación de informes podría necesitar acceder al nombre completo y al número de documento para fines de identificación. Si tuviéramos una única interfaz `ProfesionalSaludInterfaz` con todos los métodos posibles, algunos clientes se verían obligados a depender de métodos que no utilizan.

* **Caso Real (Descripción Textual): Separando las Interfaces para Diferentes Clientes de ProfesionalSalud**

    Inicialmente, podríamos definir una única interfaz `ProfesionalSaludInterfaz` que contenga todos los métodos relevantes para cualquier cliente que necesite interactuar con la información de un profesional de la salud.

    **Problema con un Diseño No ISP (Escenario Inicial Incorrecto):**

    Si tuviéramos una interfaz como la siguiente:

    ```java
    // Diseño inicial (violación de ISP)
    interface ProfesionalSaludInterfaz {
        String getNombreCompleto();
        String getNumeroDocumento();
        String getHorarioAtencion();
        String getEspecialidad(); // Solo relevante para Médicos
        String getAreaEnfermeria(); // Solo relevante para Enfermeros
        // ... otros métodos para informes, auditoría, etc. ...
    }
    ```

    La clase `AgendaTurnos`, que principalmente necesita el `horarioAtencion` y la `especialidad` (para asignar turnos médicos), se vería obligada a depender de la existencia del método `getAreaEnfermeria()`, aunque no lo utilice. De manera similar, un componente de informes que solo necesita el `nombreCompleto` y el `numeroDocumento` dependería de métodos como `getHorarioAtencion()`, `getEspecialidad()` y `getAreaEnfermeria()`, que son irrelevantes para su funcionalidad. Esto genera acoplamiento innecesario y hace que las interfaces sean menos cohesivas.

    **Aplicación del ISP (Solución Correcta):**

    Para aplicar el Principio de Segregación de Interfaces, podemos dividir la interfaz `ProfesionalSaludInterfaz` en múltiples interfaces más pequeñas y específicas para los diferentes clientes:

    1.  **Interfaz `InfoBasicaProfesional`:** Contiene los métodos básicos de identificación.

        ```java
        interface InfoBasicaProfesional {
            String getNombreCompleto();
            String getNumeroDocumento();
        }
        ```

    2.  **Interfaz `InfoAgendaProfesional`:** Contiene los métodos necesarios para la gestión de la agenda.

        ```java
        interface InfoAgendaProfesional {
            String getHorarioAtencion();
        }
        ```

    3.  **Interfaz `InfoMedico`:** Contiene los métodos específicos para los médicos.

        ```java
        interface InfoMedico {
            String getEspecialidad();
        }
        ```

    4.  **Interfaz `InfoEnfermero`:** Contiene los métodos específicos para los enfermeros.

        ```java
        interface InfoEnfermero {
            String getAreaEnfermeria();
        }
        ```

    Las clases concretas (`Medico`, `Enfermero`, etc.) implementarían las interfaces relevantes. Por ejemplo:

    ```java
    class Medico implements InfoBasicaProfesional, InfoAgendaProfesional, InfoMedico {
        private String nombreCompleto;
        private String numeroDocumento;
        private String horarioAtencion;
        private String especialidad;

        // ... constructor y getters ...

        @Override
        public String getNombreCompleto() { return nombreCompleto; }

        @Override
        public String getNumeroDocumento() { return numeroDocumento; }

        @Override
        public String getHorarioAtencion() { return horarioAtencion; }

        @Override
        public String getEspecialidad() { return especialidad; }
    }

    class Enfermero implements InfoBasicaProfesional, InfoAgendaProfesional, InfoEnfermero {
        private String nombreCompleto;
        private String numeroDocumento;
        private String horarioAtencion;
        private String areaEnfermeria;

        // ... constructor y getters ...

        @Override
        public String getNombreCompleto() { return nombreCompleto; }

        @Override
        public String getNumeroDocumento() { return numeroDocumento; }

        @Override
        public String getHorarioAtencion() { return horarioAtencion; }

        @Override
        public String getAreaEnfermeria() { return areaEnfermeria; }
    }
    ```

    Los clientes ahora dependerían solo de las interfaces que realmente necesitan. La `AgendaTurnos` dependería de `InfoAgendaProfesional` y `InfoMedico` (para turnos médicos). El componente de informes dependería de `InfoBasicaProfesional`.

**Resultado:**

Al segregar las interfaces, hemos evitado que los clientes dependan de métodos que no utilizan. Esto reduce el acoplamiento entre las clases y las interfaces, haciendo que el sistema sea más flexible, mantenible y fácil de refactorizar. Cada interfaz tiene un propósito específico, lo que mejora la cohesión y la comprensión del diseño.