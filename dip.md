# Principio de Inversión de Dependencias (DIP)

El **Principio de Inversión de Dependencias (DIP)** es uno de los principios **SOLID**, diseñado para reducir el acoplamiento entre módulos del sistema y mejorar la flexibilidad del código.

## 🔹 Propósito del DIP  
El DIP establece que **los módulos de alto nivel no deben depender de módulos de bajo nivel**, sino de abstracciones. Además, las clases deben **depender de interfaces o abstracciones en lugar de implementaciones concretas**.

## 🔹 Tipo de Principio SOLID  
Este principio pertenece a la categoría de **diseño estructural**, promoviendo la **desacoplación entre componentes** y facilitando la modificación del código sin afectar el resto del sistema.

## 📌 Problema y Solución  

### 📌 Problema:  
En nuestro sistema de gestión de turnos médicos, la clase `GestorTurnos` dependía directamente de `BaseDeDatos`. Esto significaba que, si cambiábamos la forma en que se almacenaban los turnos (por ejemplo, de SQL a MongoDB), **todo el código de `GestorTurnos` debía modificarse**, lo que generaba un alto impacto en el sistema.

### ✅ Solución con DIP:  
Para aplicar el **Principio de Inversión de Dependencias**, se crea una **interfaz `RepositorioTurnos`**, que define los métodos de acceso a la base de datos.  
Luego, en lugar de que `GestorTurnos` dependa directamente de `BaseDeDatos`, ahora depende de `RepositorioTurnos`, permitiendo que distintas implementaciones cumplan esa función:  
- `RepositorioSQL` → Usa una base de datos relacional.  
- `RepositorioMongoDB` → Usa una base de datos NoSQL.  

Ahora, si queremos cambiar la base de datos, **solo creamos una nueva implementación de `RepositorioTurnos` sin tocar `GestorTurnos`**, manteniendo el sistema flexible y escalable.

## ✨ Beneficios de aplicar DIP  
✔ **Reduce el acoplamiento entre clases y módulos**.  
✔ **Permite cambios en implementaciones sin afectar el código de alto nivel**.  
✔ **Facilita pruebas unitarias y mantenimiento del sistema**.  

# Motivación del Principio de Inversión de Dependencias (DIP)

## 📌 Problema en el sistema  
Nuestro sistema de gestión de turnos médicos enfrentaba un problema de **acoplamiento fuerte**, lo que hacía difícil modificar y expandir ciertas funcionalidades sin afectar múltiples partes del código.  
Por ejemplo, la clase `GestorTurnos` dependía directamente de la clase `BaseDeDatos`, lo que significa que si cambiábamos el motor de almacenamiento (de **MySQL** a **MongoDB**, por ejemplo), **todo el código del sistema debía ser modificado**.  
Esto generaba una alta fragilidad, dificultando cambios y haciendo que el sistema no fuera escalable.  

## ✅ Solución con DIP  
Para resolver este problema, aplicamos el **Principio de Inversión de Dependencias (DIP)**, que establece que **las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones**.  
La solución consistió en definir una **interfaz `RepositorioTurnos`**, que proporciona métodos generales para la gestión de turnos.  
En lugar de que `GestorTurnos` dependa de una implementación específica (`BaseDeDatos`), ahora solo depende de `RepositorioTurnos`, permitiendo múltiples implementaciones:  
- `RepositorioSQL` → Usa una base de datos relacional.  
- `RepositorioMongoDB` → Usa una base de datos NoSQL.  

Ahora, si queremos cambiar el motor de almacenamiento, **solo creamos una nueva implementación de `RepositorioTurnos` sin modificar `GestorTurnos`**, manteniendo el sistema modular y flexible.

## 🌍 Ejemplo del mundo real  
Imagina un sistema de **procesamiento de pagos**, donde inicialmente las transacciones solo se procesan con **tarjetas de crédito**.  
Si más adelante se quiere agregar soporte para **PayPal, transferencias bancarias y criptomonedas**, **modificar directamente el código de la clase `ProcesadorPagos` sería riesgoso y costoso**.  
La solución con **DIP** sería definir una interfaz `MetodoPago`, que sirva como capa de abstracción.  
Luego, cada método de pago se implementa en una clase separada:  
- `PagoTarjetaCredito`  
- `PagoPayPal`  
- `PagoTransferenciaBancaria`  
- `PagoCriptomonedas`  

Ahora, si más adelante se necesita agregar **Apple Pay**, simplemente se crea `PagoApplePay`, sin afectar el código principal del procesador de pagos.  

## ✨ Beneficios de aplicar DIP  
✔ **Reduce el acoplamiento entre clases y módulos**.  
✔ **Permite cambios en implementaciones sin afectar el código de alto nivel**.  
✔ **Facilita pruebas unitarias y mantenimiento del sistema**.  

# Caso Real

## Parte 2 – Aplicación de Principios SOLID en el Diseño de Clases

### Principio de Inversión de Dependencias (DIP)

* **Propósito y Tipo del Principio SOLID:** El Principio de Inversión de Dependencias establece dos puntos fundamentales:
    1.  Los módulos de alto nivel no deben depender de los módulos de bajo nivel. Ambos deben depender de abstracciones.
    2.  Las abstracciones no deben depender de los detalles. Los detalles (las implementaciones concretas) deben depender de las abstracciones.
    El DIP es un principio de diseño de dependencias entre módulos y clases.

* **Motivación:** En nuestro sistema, la clase `AgendaTurnos` (un módulo de alto nivel que contiene la lógica de negocio para la gestión de turnos) necesita persistir la información de los turnos (un módulo de bajo nivel que se encarga de la interacción con la base de datos). Si `AgendaTurnos` dependiera directamente de una implementación concreta de la persistencia, cualquier cambio en esa implementación (por ejemplo, cambiar la base de datos) afectaría directamente a `AgendaTurnos`. El DIP busca desacoplar estos módulos haciendo que ambos dependan de abstracciones (interfaces).

* **Caso Real (Descripción Textual): Desacoplando la Lógica de Negocio de Turnos de la Implementación de Persistencia**

    Inicialmente, podríamos tener la clase `AgendaTurnos` directamente interactuando con una clase concreta `TurnoRepository` que se encarga de guardar y cargar la información de los turnos desde una base de datos específica (por ejemplo, MySQL).

    **Problema con un Diseño No DIP (Escenario Inicial Incorrecto):**

    ```java
    // Diseño inicial (violación de DIP)
    class AgendaTurnos {
        private MySQLTurnoRepository turnoRepository;

        public AgendaTurnos() {
            this.turnoRepository = new MySQLTurnoRepository();
        }

        public void asignarTurno(Paciente paciente, ProfesionalSalud profesional, LocalDateTime fechaHora, String motivo) {
            Turno nuevoTurno = new Turno(fechaHora, "Pendiente", motivo, paciente, profesional);
            turnoRepository.guardarTurno(nuevoTurno);
            // ... otra lógica de negocio ...
        }

        public Turno obtenerTurno(int idTurno) {
            return turnoRepository.cargarTurno(idTurno);
        }

        // ... otra lógica de gestión de turnos ...
    }

    class MySQLTurnoRepository {
        public void guardarTurno(Turno turno) {
            // Lógica específica para guardar el turno en la base de datos MySQL
            System.out.println("Guardando turno en MySQL: " + turno);
        }

        public Turno cargarTurno(int idTurno) {
            // Lógica específica para cargar el turno desde la base de datos MySQL
            System.out.println("Cargando turno desde MySQL con ID: " + idTurno);
            return new Turno(LocalDateTime.now(), "Pendiente", "Consulta", new Paciente("...", "...", LocalDate.now(), "...", "..."), new Medico("...", "...", "", "..."));
        }
    }
    ```

    En este diseño, `AgendaTurnos` depende directamente de la clase concreta `MySQLTurnoRepository`. Si decidimos cambiar la base de datos a PostgreSQL, tendríamos que modificar la clase `AgendaTurnos` para utilizar un `PostgreSQLTurnoRepository`, lo que viola el DIP.

    **Aplicación del DIP (Solución Correcta):**

    Para aplicar el Principio de Inversión de Dependencias, introducimos una abstracción (una interfaz) entre `AgendaTurnos` y la implementación concreta de la persistencia:

    1.  **Interfaz `ITurnoRepository`:** Definimos una interfaz que especifica las operaciones necesarias para la persistencia de los turnos.

        ```java
        interface ITurnoRepository {
            void guardarTurno(Turno turno);
            Turno cargarTurno(int idTurno);
        }
        ```

    2.  **Implementaciones Concretas:** Las clases de repositorio específicas implementan esta interfaz.

        ```java
        class MySQLTurnoRepository implements ITurnoRepository {
            @Override
            public void guardarTurno(Turno turno) {
                // Lógica específica para guardar el turno en la base de datos MySQL
                System.out.println("Guardando turno en MySQL: " + turno);
            }

            @Override
            public Turno cargarTurno(int idTurno) {
                // Lógica específica para cargar el turno desde la base de datos MySQL
                System.out.println("Cargando turno desde MySQL con ID: " + idTurno);
                return new Turno(LocalDateTime.now(), "Pendiente", "Consulta", new Paciente("...", "...", LocalDate.now(), "...", "..."), new Medico("...", "...", "", "..."));
            }
        }

        class PostgreSQLTurnoRepository implements ITurnoRepository {
            @Override
            public void guardarTurno(Turno turno) {
                // Lógica específica para guardar el turno en la base de datos PostgreSQL
                System.out.println("Guardando turno en PostgreSQL: " + turno);
            }

            @Override
            public Turno cargarTurno(int idTurno) {
                // Lógica específica para cargar el turno desde la base de datos PostgreSQL
                System.out.println("Cargando turno desde PostgreSQL con ID: " + idTurno);
                return new Turno(LocalDateTime.now().plusHours(1), "Confirmado", "Revisión", new Paciente("Otro", "...", LocalDate.now().minusYears(25), "...", "..."), new Enfermero("...", "...", "", "..."));
            }
        }
        ```

    3.  **Dependencia de la Abstracción en `AgendaTurnos`:** La clase `AgendaTurnos` ahora depende de la interfaz `ITurnoRepository`, no de una implementación concreta.

        ```java
        class AgendaTurnos {
            private ITurnoRepository turnoRepository;

            // La dependencia se inyecta (por constructor en este ejemplo)
            public AgendaTurnos(ITurnoRepository turnoRepository) {
                this.turnoRepository = turnoRepository;
            }

            public void asignarTurno(Paciente paciente, ProfesionalSalud profesional, LocalDateTime fechaHora, String motivo) {
                Turno nuevoTurno = new Turno(fechaHora, "Pendiente", motivo, paciente, profesional);
                turnoRepository.guardarTurno(nuevoTurno);
                // ... otra lógica de negocio ...
            }

            public Turno obtenerTurno(int idTurno) {
                return turnoRepository.cargarTurno(idTurno);
            }

            // ... otra lógica de gestión de turnos ...
        }
        ```

**Resultado:**

Con este diseño, `AgendaTurnos` (el módulo de alto nivel) depende de la abstracción `ITurnoRepository`, y las implementaciones concretas (`MySQLTurnoRepository`, `PostgreSQLTurnoRepository` - módulos de bajo nivel) también dependen de la misma abstracción. Esto desacopla la lógica de negocio de la gestión de turnos de la implementación específica de la persistencia. Ahora podemos cambiar la base de datos simplemente proporcionando una nueva implementación de `ITurnoRepository` a la clase `AgendaTurnos` sin necesidad de modificar su código fuente. Esto hace que el sistema sea más flexible, robusto y fácil de adaptar a futuros cambios en la infraestructura de persistencia.

# Estructura de clase
[Enlace al diagrama](https://1drv.ms/i/c/f2bf844ed8279638/EUXqanLyl-BOol_rll1-ALIBQ5VCTZKi72L1RKZ3L7WKfQ?e=jRmjeb)

```Java
interface ITurnoRepository {
    void guardarTurno(Turno turno);
    Turno cargarTurno(int idTurno);
}

class MySQLTurnoRepository implements ITurnoRepository {
    @Override
    public void guardarTurno(Turno turno) {
        // Lógica para guardar en MySQL
    }
    @Override
    public Turno cargarTurno(int idTurno) {
        // Lógica para cargar desde MySQL
        return new Turno(/* ... */);
    }
}

class AgendaTurnos {
    private final ITurnoRepository turnoRepository;

    public AgendaTurnos(ITurnoRepository turnoRepository) {
        this.turnoRepository = turnoRepository;
    }

    public void asignarTurno(Paciente paciente, ProfesionalSalud profesional, LocalDateTime fechaHora, String motivo) {
        Turno turno = new Turno(/* ... */);
        turnoRepository.guardarTurno(turno);
    }
}

Descripción: El Principio de Inversión de Dependencias establece que los módulos de alto nivel no deben depender de los módulos de bajo nivel. Ambos deben depender de abstracciones. Aquí, AgendaTurnos (alto nivel) depende de la interfaz ITurnoRepository (abstracción), y los repositorios concretos (bajo nivel) también dependen de esta interfaz.



