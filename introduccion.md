# Anexo - Introducción al Diseño Orientado a Objetos



## Descripción del Paradigma Orientado a Objetos

La Programación Orientada a Objetos (POO) es un paradigma de programación que organiza el software en torno a "objetos". Un objeto es una entidad que contiene datos (atributos) y las funciones (métodos) que operan sobre esos datos. En lugar de pensar en el programa como una secuencia de instrucciones, la POO se centra en modelar el mundo real a través de objetos que interactúan entre sí.

La POO es importante porque facilita:

* **Modularidad:** El código se organiza en unidades independientes (objetos), lo que facilita su comprensión, mantenimiento y reutilización.
* **Abstracción:** Permite enfocarse en las características esenciales de los objetos, ocultando la complejidad interna.
* **Encapsulamiento:** Protege los datos internos de un objeto, permitiendo el acceso a través de métodos definidos, lo que mejora la seguridad y evita modificaciones accidentales.
* **Reutilización:** Los objetos y las clases pueden ser utilizados en diferentes partes del programa o en otros proyectos.
* **Mantenibilidad:** Los cambios en un objeto tienden a tener un impacto limitado en otras partes del sistema, lo que facilita la corrección de errores y la adición de nuevas funcionalidades.

## Los Cuatro Fundamentos de POO

1.  **Encapsulamiento:**
    * **Descripción:** El encapsulamiento consiste en agrupar los datos (atributos) y los métodos (comportamiento) que operan sobre esos datos dentro de una unidad llamada clase. Además, restringe el acceso directo a los datos, obligando a interactuar con ellos a través de los métodos de la clase.
    * **Ejemplo del Mundo Real:** Imagina una **caja fuerte**. Contiene objetos valiosos (datos) y tiene una cerradura y una combinación (métodos) para acceder a ellos. No puedes acceder directamente al contenido de la caja fuerte sin usar la combinación correcta. De manera similar, en POO, los atributos de un objeto están protegidos y solo se pueden modificar o acceder a través de los métodos definidos en su clase.
    * **Boceto:** Representación visual de una caja fuerte con una flecha indicando la interacción a través de la cerradura/combinación.

    |**Clase**      |**Atributos**    |**Métodos**        |
    |---------------|-----------------|-------------------|
    |**CajaFuerte** |- objetosValiosos|+ abrir()          |
    |               |- combinacion    |+ cerrar()         |
    |               |                 |+ verificarCodigo()|

    ### Relación

    |**Elemento**|**Acción**     |**Destino**   |
    |------------|---------------|--------------|
    |**Persona** |Usa combinación|**CajaFuerte**|

    ### Explicación

    * Los atributos (`objetosValiosos` y `combinación`) están protegidos (indicados con - como privados).
    * Los métodos (`abrir()`, `cerrar()`, `verificarCodigo()`) son públicos (indicados con +) y definen la interacción con la clase.
    * La relación muestra cómo **Persona** interactúa con **CajaFuerte** utilizando los métodos.


2.  **Abstracción:**
    * **Descripción:** La abstracción se centra en mostrar solo la información esencial de un objeto al mundo exterior, ocultando los detalles complejos de su implementación interna. Permite manejar la complejidad al enfocarse en "qué hace" un objeto en lugar de "cómo lo hace".
    * **Ejemplo del Mundo Real:** Considera un **televisor**. Para usarlo, interactúas con botones como "Encender", "Apagar", "Cambiar Canal", "Subir Volumen". No necesitas saber cómo funcionan internamente los circuitos electrónicos para disfrutar de la televisión. Los botones representan la interfaz abstracta que te permite interactuar con la funcionalidad esencial del televisor.
    * **Boceto:** Diagrama de un televisor con los botones principales resaltados, simbolizando la interfaz visible, y una sección sombreada representando la complejidad interna oculta.

    |**Clase**    |**Atributos**      |**Métodos**     |
    |-------------|-------------------|----------------|
    |**Televisor**|- circuitosInternos|+ encender()    | 
    |             |- componentes      |+ apagar()      |
    |             |                   |+ cambiarCanal()|
    |             |                   |+ subirVolumen()|

    ### Relación

    |**Elemento**|**Acción** |**Destino**  |
    |------------|-----------|-------------|
    |**Usuario** |Usa botones|**Televisor**|

    ### Explicación

    * La **Clase Televisor** encapsula los **atributos privados** (`circuitosInternos` y `componentes`), ocultando los detalles técnicos de su funcionamiento.
    * Los **métodos públicos** (`encender()`, `apagar()`, `cambiarCanal()`, `subirVolumen()`) permiten a los usuarios interactuar con el televisor sin preocuparse por su implementación interna.
    * La relación muestra que el **Usuario** solo accede a la funcionalidad esencial del televisor mediante botones.

3.  **Herencia:**
    * **Descripción:** La herencia es un mecanismo que permite a una clase (clase hija o subclase) heredar atributos y métodos de otra clase (clase padre o superclase). Esto promueve la reutilización de código y la creación de jerarquías de clases con características comunes.
    * **Ejemplo del Mundo Real:** Piensa en diferentes tipos de **vehículos**. Un `Automóvil`, una `Motocicleta` y un `Camión` son todos vehículos. Comparten características comunes como tener ruedas, un motor y la capacidad de moverse. La clase `Vehículo` podría definir estos atributos y métodos generales, y las clases `Automóvil`, `Motocicleta` y `Camión` heredarían estas características, añadiendo sus propias particularidades (por ejemplo, un automóvil tiene cuatro puertas, una motocicleta tiene dos ruedas, un camión puede transportar carga pesada).
    * **Boceto:** Diagrama de herencia con una clase base "Vehículo" y flechas apuntando a las subclases "Automóvil", "Motocicleta" y "Camión".

    |**Clase Padre**|**Atributos** |**Métodos**|
    |---------------|--------------|-----------|
    |**Vehículo**   |- ruedas      |+ mover()  |
    |               |- motor       |+ frenar() |

    ### Clases Hijas (Heredan de Vehículo)

    |**Clase Hija** |**Atributos Adicionales**|**Métodos Adicionales**|
    |---------------|-------------------------|-----------------------|
    |**Automóvil**  |- puertas (4)            |+ encenderLuces()      |
    |**Motocicleta**|- ruedas (2)             |+ activarCasco()       |
    |**Camión**     |- capacidadCarga         |+ engancharRemolque()  |

    ### Relación

     |**Elemento** |**Acción**   |**Destino** |
     |-------------|-------------|------------|             
     |**Conductor**|Usa vehículo |**Vehículo**|

     ### Explicación

     * La **Clase Padre (Vehículo)** contiene atributos y métodos generales que serán heredados por las clases hijas.
     * Las **Clases Hijas (Automóvil, Motocicleta, Camión)** amplian la funcionalidad de Vehículo agregando atributos y métodos especificos.
     * La relación indica que un **Conductor** usa cualquiera de los vehículos, demostrando la aplicación del concepto de herencia.

4.  **Polimorfismo:**
    * **Descripción:** El polimorfismo (que significa "muchas formas") permite que objetos de diferentes clases respondan al mismo mensaje (llamada a un método) de manera diferente. Esto proporciona flexibilidad y extensibilidad al código.
    * **Ejemplo del Mundo Real:** Considera la acción de "hacer un sonido". Un `Perro` hace "guau", un `Gato` hace "miau" y un `Pájaro` hace "pío". Todos responden al mismo concepto de "hacer un sonido", pero la forma en que lo hacen es diferente según su tipo. En POO, podrías tener un método llamado `emitirSonido()` que se comporta de forma distinta cuando se invoca en un objeto de la clase `Perro`, `Gato` o `Pájaro`.
    * **Boceto:** Ilustración de un megáfono con flechas dirigidas a representaciones de un perro (con el texto "guau"), un gato ("miau") y un pájaro ("pío"), mostrando diferentes respuestas al mismo "mensaje".

    |**Clase Padre**|**Métodos**   |
    |---------------|--------------|
    |**Animal**     |+ emitirSonido|

    ### Clases Hijas (Implementan el Método)

    |**Clase Hija**|**Método emitirSonido()**|
    |--------------|-------------------------|
    |**Perro**     |Retorna "guau"           |
    |**Gato**      |Retorna "miau"           |
    |**Pájaro**    |Retorna "pío"            |

    ### Relación

    |**Elemento**|**Acción**   |**Destino**           |
    |------------|-------------|----------------------|
    |**Megáfono**|Envía mensaje|**Animal (Polimorfo)**|

    ### Explicación

    * La **Clase Padre (Animal)** define el método `emitirSonido()` como una interfaz o comportamiento general.
    * Las **Clases Hijas (Perro, Gato, Pájaro)** implementan este método de forma distinta, devolviendo sonidos específicos según la clase.
    * El megáfono simboliza un intermediario que envía el mismo mensaje a distintos tipos de objetos, demostrando cómo cada uno responde de manera única.

# Requisitos Iniciales del Sistema

## Explicación de mi Diagrama UML del Sistema de Gestión de Turnos

Mí diagrama UML representa la estructura de clases clave diseñadas para cumplir con los requisitos iniciales de nuestro sistema de gestión de turnos médicos. El diagrama se centra en las entidades principales, sus atributos y las relaciones entre ellas, facilitando el registro de pacientes y profesionales de la salud, la solicitud y asignación de turnos, y la consulta de la información programada.

## Clases Principales y sus Responsabilidades:

**Paciente:** Esta clase modela a los pacientes del sistema. Contiene atributos esenciales para el registro, como `nombreCompleto`, `numeroDocumento`, `fechaNacimiento`, `telefono`, y `correoElectronico`. Además, mantiene una lista de `historialTurnos`, lo que permite rastrear los turnos pasados y futuros del paciente.

**ProfesionalSalud:** Esta clase representa a los médicos u otros profesionales de la salud que ofrecen consultas. Al igual que el paciente, almacena información de registro básica (`nombreCompleto`, `telefono`, `correoElectronico`). Adicionalmente, incluye detalles específicos de su rol, como `matriculaProfesional`, `especialidad`, y `horarioAtencion`, cruciales para la asignación de turnos.

**Turno:** Esta clase representa un turno específico en el sistema. Contiene la información temporal del turno (`fechaHora`), el motivo de la consulta (`motivoConsulta`), y su estado actual (`estado`, por ejemplo, `SOLICITADO`, `ASIGNADO`, `CANCELADO`). Lo más importante es que establece relaciones (asociaciones) con las instancias de `Paciente` y `ProfesionalSalud`, indicando quién solicitó el turno y con quién está programado.

**AgendaTurnos:** Esta clase actúa como el cerebro de la lógica de negocio relacionada con los turnos. Su responsabilidad principal es gestionar el ciclo de vida de los turnos. Para ello, depende de una interfaz llamada `ITurnoRepository` para la persistencia de los datos de los turnos. Los métodos clave de `AgendaTurnos` incluyen:

* `solicitarTurno()`: Permite a un paciente iniciar una solicitud de turno.
* `asignarTurno()`: Asigna un turno solicitado a un profesional de la salud, probablemente verificando su disponibilidad.
* `consultarTurnosPaciente()`: Permite a un paciente ver sus turnos programados.
* `consultarTurnosProfesional()`: Permite a un profesional de la salud ver su agenda de turnos.

**ITurnoRepository (Interfaz):** Esta interfaz define un contrato para las operaciones de persistencia relacionadas con la clase `Turno`. Declara métodos como `guardarTurno()`, `cargarTurno()`, `obtenerTurnosPorPaciente()`, y `obtenerTurnosPorProfesional()`. Al ser una interfaz, no especifica cómo se implementan estas operaciones en una base de datos concreta.

**MySQLTurnoRepository y PostgreSQLTurnoRepository (Clases):** Estas clases son implementaciones concretas de la interfaz `ITurnoRepository`. Cada una contiene la lógica específica para interactuar con una base de datos en particular (MySQL y PostgreSQL, respectivamente). Esto permite que el sistema sea flexible y pueda cambiar la base de datos subyacente con una mínima modificación en la lógica de negocio principal (`AgendaTurnos`), adhiriéndose al Principio de Inversión de Dependencias (DIP).

## Flujo de Interacción Implícito:

Cuando un paciente solicita un turno, la clase `AgendaTurnos` recibe la solicitud y, utilizando una instancia de un repositorio concreto (inyectada a través de la interfaz `ITurnoRepository`), guarda la información del nuevo turno. Al asignar un turno, `AgendaTurnos` actualiza el estado del turno y asocia el paciente y el profesional de la salud correspondientes, persistiendo estos cambios a través del repositorio. Tanto pacientes como profesionales pueden consultar sus turnos llamando a los métodos de `AgendaTurnos`, que a su vez utiliza el repositorio para obtener la información almacenada.

## En Resumen:

Mi diagrama UML modela un sistema robusto y flexible para la gestión de turnos, separando las responsabilidades de la lógica de negocio de la persistencia de datos a través del uso de interfaces y permitiendo la interacción entre pacientes, profesionales de la salud y los turnos programados. Cumple con los requisitos iniciales del sistema al proporcionar las estructuras necesarias para el registro, la solicitud, la asignación y la consulta de turnos.

## Base para el diagrama UML Class

```Java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.List;

class Paciente {
    private String nombreCompleto;
    private String numeroDocumento;
    private LocalDate fechaNacimiento;
    private String telefono;
    private String correoElectronico;
    private List<Turno> historialTurnos;

    public Paciente(String nombreCompleto, String numeroDocumento, LocalDate fechaNacimiento, String telefono, String correoElectronico) {
        this.nombreCompleto = nombreCompleto;
        this.numeroDocumento = numeroDocumento;
        this.fechaNacimiento = fechaNacimiento;
        this.telefono = telefono;
        this.correoElectronico = correoElectronico;
        this.historialTurnos = new ArrayList<>();
    }

    // Getters y setters (omitidos para brevedad)

    public List<Turno> getHistorialTurnos() {
        return historialTurnos;
    }

    public void agregarTurno(Turno turno) {
        this.historialTurnos.add(turno);
    }
}

class ProfesionalSalud {
    private String nombreCompleto;
    private String matriculaProfesional;
    private String especialidad;
    private String horarioAtencion;
    private String telefono;
    private String correoElectronico;

    public ProfesionalSalud(String nombreCompleto, String matriculaProfesional, String especialidad, String horarioAtencion, String telefono, String correoElectronico) {
        this.nombreCompleto = nombreCompleto;
        this.matriculaProfesional = matriculaProfesional;
        this.especialidad = especialidad;
        this.horarioAtencion = horarioAtencion;
        this.telefono = telefono;
        this.correoElectronico = correoElectronico;
    }

    // Getters y setters (omitidos para brevedad)
}

class Turno {
    private LocalDateTime fechaHora;
    private String motivoConsulta;
    private String estado;
    private Paciente paciente;
    private ProfesionalSalud profesional;

    public Turno(LocalDateTime fechaHora, String motivoConsulta, Paciente paciente) {
        this.fechaHora = fechaHora;
        this.motivoConsulta = motivoConsulta;
        this.paciente = paciente;
        this.estado = "SOLICITADO";
    }

    // Getters y setters (omitidos para brevedad)

    public void asignarProfesional(ProfesionalSalud profesional) {
        this.profesional = profesional;
        this.estado = "ASIGNADO";
    }

    public Paciente getPaciente() {
        return paciente;
    }

    public ProfesionalSalud getProfesional() {
        return profesional;
    }

    public LocalDateTime getFechaHora() {
        return fechaHora;
    }

    public String getEstado() {
        return estado;
    }

    public void setEstado(String estado) {
        this.estado = estado;
    }
}

interface ITurnoRepository {
    void guardarTurno(Turno turno);
    Turno cargarTurno(int idTurno);
    List<Turno> obtenerTurnosPorPaciente(Paciente paciente);
    List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional);
}

class MySQLTurnoRepository implements ITurnoRepository {
    // Simulación de la lógica de la base de datos MySQL
    @Override
    public void guardarTurno(Turno turno) {
        System.out.println("Guardando turno para paciente " + turno.getPaciente().getNombreCompleto() + " en MySQL.");
    }

    @Override
    public Turno cargarTurno(int idTurno) {
        System.out.println("Cargando turno con ID " + idTurno + " desde MySQL.");
        return null; // Simulación
    }

    @Override
    public List<Turno> obtenerTurnosPorPaciente(Paciente paciente) {
        System.out.println("Obteniendo turnos para paciente " + paciente.getNombreCompleto() + " desde MySQL.");
        return new ArrayList<>(); // Simulación
    }

    @Override
    public List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional) {
        System.out.println("Obteniendo turnos para profesional " + profesional.getNombreCompleto() + " desde MySQL.");
        return new ArrayList<>(); // Simulación
    }
}

class PostgreSQLTurnoRepository implements ITurnoRepository {
    // Simulación de la lógica de la base de datos PostgreSQL
    @Override
    public void guardarTurno(Turno turno) {
        System.out.println("Guardando turno para paciente " + turno.getPaciente().getNombreCompleto() + " en PostgreSQL.");
    }

    @Override
    public Turno cargarTurno(int idTurno) {
        System.out.println("Cargando turno con ID " + idTurno + " desde PostgreSQL.");
        return null; // Simulación
    }

    @Override
    public List<Turno> obtenerTurnosPorPaciente(Paciente paciente) {
        System.out.println("Obteniendo turnos para paciente " + paciente.getNombreCompleto() + " desde PostgreSQL.");
        return new ArrayList<>(); // Simulación
    }

    @Override
    public List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional) {
        System.out.println("Obteniendo turnos para profesional " + profesional.getNombreCompleto() + " desde PostgreSQL.");
        return new ArrayList<>(); // Simulación
    }
}

class AgendaTurnos {
    private final ITurnoRepository turnoRepository;

    public AgendaTurnos(ITurnoRepository turnoRepository) {
        this.turnoRepository = turnoRepository;
    }

    public Turno solicitarTurno(Paciente paciente, LocalDateTime fechaHora, String motivoConsulta) {
        Turno nuevoTurno = new Turno(fechaHora, motivoConsulta, paciente);
        turnoRepository.guardarTurno(nuevoTurno);
        paciente.agregarTurno(nuevoTurno);
        System.out.println("Turno solicitado para " + paciente.getNombreCompleto() + " el " + fechaHora);
        return nuevoTurno;
    }

    public boolean asignarTurno(Turno turno, ProfesionalSalud profesional) {
        // Aquí iría la lógica para verificar la disponibilidad del profesional
        turno.asignarProfesional(profesional);
        turnoRepository.guardarTurno(turno);
        System.out.println("Turno asignado a " + profesional.getNombreCompleto() + " el " + turno.getFechaHora());
        return true;
    }

    public List<Turno> consultarTurnosPaciente(Paciente paciente) {
        System.out.println("Consultando turnos para el paciente " + paciente.getNombreCompleto());
        return turnoRepository.obtenerTurnosPorPaciente(paciente);
    }

    public List<Turno> consultarTurnosProfesional(ProfesionalSalud profesional) {
        System.out.println("Consultando turnos para el profesional " + profesional.getNombreCompleto());
        return turnoRepository.obtenerTurnosPorProfesional(profesional);
    }
}

public class SistemaGestionTurnos {
    public static void main(String[] args) {
        // Ejemplo de uso
        Paciente paciente1 = new Paciente("Juan Pérez", "12345678", LocalDate.of(1990, 5, 15), "123-456-7890", "juan.perez@email.com");
        ProfesionalSalud medico1 = new ProfesionalSalud("Dra. Ana López", "MP12345", "Cardiología", "Lunes a Viernes 9-17", "987-654-3210", "ana.lopez@hospital.com");

        ITurnoRepository turnoRepository = new MySQLTurnoRepository(); // Podríamos cambiar a PostgreSQL sin modificar AgendaTurnos
        AgendaTurnos agenda = new AgendaTurnos(turnoRepository);

        LocalDateTime fechaHoraSolicitud = LocalDateTime.of(2025, 5, 10, 10, 0);
        Turno turnoSolicitado = agenda.solicitarTurno(paciente1, fechaHoraSolicitud, "Control de rutina");

        if (turnoSolicitado != null) {
            agenda.asignarTurno(turnoSolicitado, medico1);
        }

        agenda.consultarTurnosPaciente(paciente1);
        agenda.consultarTurnosProfesional(medico1);
    }
}

/*
Me basé en este programa Java para poder realizar el diagrama UML Class.
Este código Java ilustra la implementación de las clases y la interfaz que se describieron en la explicación del diagrama UML.
Se pueden observar las entidades Paciente, ProfesionalSalud, Turno, la interfaz ITurnoRepository y una implementación concreta (MySQLTurnoRepository).
La clase AgendaTurnos orquesta la lógica de negocio, utilizando la interfaz para interactuar con la capa de persistencia.
Este código refleja la estructura y las responsabilidades definidas en el diagrama UML Class del sistema de gestión de turnos.
*/
```

## Casos de Uso

1.  **Nombre del caso de uso:** Registrar Nuevo Paciente
    * **Actor(es) involucrado(s):** Recepcionista
    * **Descripción breve:** La recepcionista registra la información de un nuevo paciente en el sistema.
    * **Flujo principal de eventos:**
        1.  La recepcionista selecciona la opción "Registrar Paciente".
        2.  El sistema muestra un formulario para ingresar los datos del paciente (nombre completo, número de documento, fecha de nacimiento, teléfono, correo electrónico).
        3.  La recepcionista ingresa los datos del paciente.
        4.  La recepcionista confirma el registro.
        5.  El sistema guarda la información del paciente.
        6.  El sistema muestra un mensaje de éxito.
    * **Precondiciones:** La recepcionista tiene acceso al sistema.
    * **Postcondiciones:** El nuevo paciente está registrado en el sistema.

2.  **Nombre del caso de uso:** Solicitar Turno
    * **Actor(es) involucrado(s):** Paciente
    * **Descripción breve:** El paciente solicita un nuevo turno médico.
    * **Flujo principal de eventos:**
        1.  El paciente accede a la opción "Solicitar Turno".
        2.  El sistema muestra opciones para seleccionar la especialidad y/o el médico.
        3.  El paciente selecciona la especialidad y/o el médico deseado.
        4.  El sistema muestra la disponibilidad de turnos.
        5.  El paciente selecciona una fecha y hora disponible y especifica el motivo del turno.
        6.  El paciente confirma la solicitud.
        7.  El sistema registra la solicitud de turno con estado "pendiente".
        8.  El sistema muestra un mensaje de confirmación de la solicitud.
    * **Precondiciones:** El paciente está registrado en el sistema.
    * **Postcondiciones:** Se ha registrado una solicitud de turno pendiente para el paciente.

3.  **Nombre del caso de uso:** Asignar Turno
    * **Actor(es) involucrado(s):** Recepcionista
    * **Descripción breve:** La recepcionista asigna un turno pendiente a un paciente con un médico y horario específicos.
    * **Flujo principal de eventos:**
        1.  La recepcionista selecciona la opción "Gestionar Turnos" y visualiza las solicitudes pendientes.
        2.  La recepcionista selecciona una solicitud de turno.
        3.  El sistema muestra la disponibilidad del médico solicitado (o permite seleccionar otro médico disponible).
        4.  La recepcionista selecciona una fecha y hora disponible para el médico.
        5.  La recepcionista confirma la asignación.
        6.  El sistema actualiza el estado del turno a "confirmado", asigna el médico y el horario al paciente.
        7.  El sistema genera una notificación para el paciente y el médico.
        8.  El sistema muestra un mensaje de éxito.
    * **Precondiciones:** Existe una solicitud de turno pendiente. El médico seleccionado está disponible en la fecha y hora elegidas. La recepcionista tiene acceso al sistema.
    * **Postcondiciones:** El turno ha sido asignado al paciente con el médico y horario especificados, y su estado es "confirmado". Se han generado notificaciones.

4.  **Nombre del caso de uso:** Cancelar Turno
    * **Actor(es) involucrado(s):** Paciente, Recepcionista
    * **Descripción breve:** Un paciente o la recepcionista cancelan un turno existente.
    * **Flujo principal de eventos (Cancelación por Paciente):**
        1.  El paciente accede a la opción "Mis Turnos" y selecciona el turno que desea cancelar.
        2.  El paciente confirma la cancelación.
        3.  El sistema actualiza el estado del turno a "cancelado".
        4.  El sistema genera una notificación para el paciente y el médico.
        5.  El sistema muestra un mensaje de confirmación de la cancelación.
    * **Flujo principal de eventos (Cancelación por Recepcionista):**
        1.  La recepcionista selecciona la opción "Gestionar Turnos" y busca el turno que desea cancelar.
        2.  La recepcionista selecciona el turno y elige la opción "Cancelar Turno".
        3.  La recepcionista (opcionalmente) ingresa un motivo de cancelación.
        4.  La recepcionista confirma la cancelación.
        5.  El sistema actualiza el estado del turno a "cancelado".
        6.  El sistema genera una notificación para el paciente y el médico.
        7.  El sistema muestra un mensaje de confirmación de la cancelación.
    * **Precondiciones:** El turno que se intenta cancelar existe y no ha finalizado. El actor tiene acceso al sistema.
    * **Postcondiciones:** El estado del turno es "cancelado". Se han generado notificaciones.

5.  **Nombre del caso de uso:** Consultar Historial de Turnos del Paciente
    * **Actor(es) involucrado(s):** Paciente, Recepcionista
    * **Descripción breve:** Un paciente o la recepcionista consultan el historial de turnos de un paciente específico.
    * **Flujo principal de eventos (Consulta por Paciente):**
        1.  El paciente accede a la opción "Historial de Turnos".
        2.  El sistema muestra el historial de turnos del paciente.
    * **Flujo principal de eventos (Consulta por Recepcionista):**
        1.  La recepcionista busca un paciente por su nombre o número de documento.
        2.  La recepcionista selecciona al paciente.
        3.  La recepcionista selecciona la opción "Ver Historial de Turnos".
        4.  El sistema muestra el historial de turnos del paciente.
    * **Precondiciones:** El paciente está registrado en el sistema. El actor tiene acceso al sistema.
    * **Postcondiciones:** Se muestra el historial de turnos del paciente solicitado.

## Boceto Inicial del Diseño de Clases

Este es el boceto inicial del diseño de clases, incrustado como una imagen y con un enlace para su visualización.

![Boceto de Diagrama UML del sistema](/imagendebocetoUMLdelsistema/Diagram%202025-05-03%2016-03-28.png)

[Enlace para visualizar el boceto en línea](https://1drv.ms/i/c/f2bf844ed8279638/EXJ8u0SUJxtAhqW12xZfhBEBFSX3FENsatti8k6ySnlCdg?e=R8YbMy)

**Descripción del Boceto Inicial de Clases:**

Este boceto inicial presenta las clases fundamentales identificadas para el sistema de gestión de turnos:

* **Paciente:** Representa a los pacientes del centro de salud. Contiene atributos como nombre, documento, contacto y un historial de turnos asociados. Podría tener métodos como solicitarTurno(), cancelarTurno(), consultarHistorial().
* **ProfesionalSalud:** Representa a los profesionales de la salud, Contiente atributos como nombre, matricula, especialidad, horario y contacto. Pordría tener métodos como consultarAgenda(), verDetalleTurno().
* **Turno:** Representa una cita médica. Contiene atributos como fechaHora, estado, medico (referencia a ProfesionalSalud), paciente (referencia a Paciente) y motivo. Podría tener métpdps como confirmar(), cancelar(), obtenerDetalle().
* **AgendarTurnos:** Representa la agenda del sistema para gestionar los turnos. Podría tener métodos como asignarTurno(), cancelarTurno(), modificarTurno(), consultarTurnosPorPaciente(), consultarTurnosPorMedico().
* **PersonalAdministrativo:** Representa al personal administrativo que gestiona el sistema. Contiene atributos como nombre, usuario, contraseña y métodos como registrarPaciente(), registrarProfesional(), asignarTurno(), cancelarTurno().
* **Persona:** Una clase abstracta o superclase que contiene atributos comunes a Paciente, ProfesionalSalud y PersonalAdministrativo, como nombre, documento y fechaNacimiento.

Las relaciones iniciales visualizadas en el boceto (a través de líneas con flechas) sugieren asociaciones y herencia entre estas clase. Por ejemplo, Paciente y ProfesionalSalid heredan de Persona. Un Paciente y un ProfesionalSalid están asociados a un Turno. La AgendaTurnos gestiona los Turnos, y el PersonalAdministrativo interactúa con Pacientes, ProfesionalSalud y AgendaTurnos para gestionar el sistema.