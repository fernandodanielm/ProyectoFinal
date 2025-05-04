1. **Paciente**

![Tarjeta CRC Paciente](/imagenesTarjetasCRC/tarjetaCRCPaciente.png)
[Enlace a la tarjeta CRC Paciente](https://1drv.ms/i/c/f2bf844ed8279638/EdcYzYC-Ew9OkUFTcWuKQTwBdAnSRSAhEIv8vGumg9a6bg?e=OKvdHX)

## Expliación de la Tarjeta CRC: Paciente

La tarjeta CRC para la clase `Paciente` describe la información y las interacciónes de un paciente dentro de nuestro sistema de gestión de turnos. Analicemos cada sección:
  * **Nombre de la Clase:** `Paciente`- Representa a una persona que utiliza el sistema para solicitar y gestionar sus turnos médicos.
  * **Superclase:** (Vacío)-En el diseño actual, la clase `Paciente` no hereda de ninguna otra clase directamente. Es una entidad principal por sí misma.
  * **Subclase:(Vacío)** - Tampoco tenemos sublaces que especialicen el comportamiento o la información de un `Paciente`. Todos los pacientes comparten los atributos básicos definidos aquí.
  * **Responsabilidades:** Estas son las principales piezas de información que un objeto `Paciente` debe conocer y las acciones que puede realizar:
   * **Conocer mi nombre completo para registrarme:** Almacena el nombre completo del paciente para su identificación.
   * **Conocer mi número de documento para identificarme:** Almacena el número de documento únicp del paciente (por ejemplo, DNI).
   * **Conocer mi fecha de nacimiento para el registro:** Almacena la fecha de nacimiento del paciente.
   * **Conocer mi teléfono para contacto:** Almacena el número de teléfono del paciente para comunicaciones.
   * **Conocer mi correo electrónico para contacto:** Almacena la dirección de correo electrónico del paciente para comunicaciones.
   * **Conocer mi historial de turnos:** Mantiene una lista de todos los turnos pasados y futuros asociados al paciente.
   * **Solicitar un nuevo turno:** Interactúa con la `AgendaTurnos` para iniciar el proceso de solicitud de un turno.
* **Colaboradores:** Estas son las otras clases con las que un objeto `Paciente` tiene una relación o necesita interactuar.
  * `Recepción`: Aunque no es una clase explicita en mi diagrama principal, representa el punto de entrada para el registro de un nuevo paciente.
  * `Turno`: Un `Paciente` tiene un historial de `Turno`s y está asociado a `Turno`s específicos.
  * `AgendaTurnos`: El `Paciente` colabora con `AgendaTurnos` para solicitar nuevos turnos.
* **Pensamiento del Objeto:** Esta sección refleja la "mentalidad" de un objeto `Paciente`:
  * "Soy un paciente que necesita registrarse." - Representa la acción inicial en el sistema.
  * "Tengo un DNI único." - Refleja la propiedad de identificación única.
  * "Nací en una fecha específica." - Representa un dato personal importante.
  * "Tengo un número de teléfono." - Representa un medio de contacto.
  * "Tengo una dirección de correo." - Representa otro medio de contacto.
  * "He tenido o tendré turnos." - Refleja la interacción con el sistema a lo largo del tiempo.
  * "Necesito pedir una consulta." - Representa una acción principal del paciente.
* **Propiedad:** Esta describe las características o atributos clave que definen a un objeto `Paciente`:
  * **Nombre completo:** El nombre completo del paciente
  * **Número de documento (DNI):** El identificador único del paciente.
  * **Fecha de nacimiento:** La fecha de nacimiento del paciente.
  * **Teléfono:** El número de teléfono del paciente.
  * **Correo electrónico:** La dirección de correo electrónico del paciente.
  * **Historial de turnos:** La colección de turnos asociados al paciente.
  * **Identificador único (ID):** Aunque no se menciona explícitamente en las responsabilidades, implicitamente cada paciente tendrá un ID único pa su identificación dentro del sistema.

  ## Código java en cual me base para hacer la tarjeta CRC de Paciente

```Java
import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;

class Paciente {
    private String nombreCompleto;
    private String numeroDocumento;
    private LocalDate fechaNacimiento;
    private String telefono;
    private String correoElectronico;
    private List<Turno> historialTurnos;
    private int idPaciente; // Propiedad implícita: Identificador único

    public Paciente(String nombreCompleto, String numeroDocumento, LocalDate fechaNacimiento, String telefono, String correoElectronico, int idPaciente) {
        this.nombreCompleto = nombreCompleto;
        this.numeroDocumento = numeroDocumento;
        this.fechaNacimiento = fechaNacimiento;
        this.telefono = telefono;
        this.correoElectronico = correoElectronico;
        this.historialTurnos = new ArrayList<>();
        this.idPaciente = idPaciente;
    }

    // Getters y setters (omitidos para brevedad)

    public List<Turno> getHistorialTurnos() {
        return historialTurnos;
    }

    public void agregarTurno(Turno turno) {
        this.historialTurnos.add(turno);
    }

    public int getIdPaciente() {
        return idPaciente;
    }
}
```


2. **ProfesionalSalud**
class Paciente 
![Tarjeta CRC ProfesionalSalud](/imagenesTarjetasCRC/tarjetaCRCProfesionalSalud.png)
[Enlace a la Tarjeta CRC ProfesionalSalud](https://1drv.ms/i/c/f2bf844ed8279638/Efm643ipH-VDjYlQsyEdC_UBKWJOdHX-drxLQXWW9prPIQ?e=F6Cdjd)

## Explicación de la Tarjeta CRC: ProfesionalSalud

La tarjeta CRC para la clase `ProfesionalSalud` describe la información y las interacciones de un profesional de la salud dentro nuestro sistema de gestión de turnos. Analicemos cada sección:
  * **Nombre de la Clase:** `ProfesionalSalud` - Representa a un médico u otro profesional que ofrece consultas dentro del sistema.
  * **Superclase: (Vacía)** - En el diseño actual, la clase `ProfesionalSalud` no hereda de ninguna otra clase directamente. Es una entidad principal por sí misma.
  * **Subclase: (Vacío)** - Tampoco tenemos subclases que especialicen el comportamiento o la información de un `ProfesionalSalud`. Todos los profesionales comparten los atributos básicos definidos aquí.
  * **Responsabilidades:** Estas son las principales piezas de información que un objeto `ProfesionalSalud` debe conocer y las acciones en las que puede estar involucrado:
    * **Conocer mi nombre completo para identificarme:** Almacena el nombre completo del profesional para su identificación.
    * **Conocer mi matrícula profesional para identificarme:** Almacena el número de matrícula único del profesional.
    * **Conocer mi especialidad:** Almacena el área de especialización médica del profesional.
    * **Conocer mi horario de atención:** Almacena los días y horas en los que el profesional está disponible para atender turnos.
    * **Conocer mi teléfono para contacto:** Almacena el número de teléfono del profesional para comunicaciones.
    * **Conocer mi correo electrónico para contacto:** Almacena la dirección de correo electrónico del profesional para comunicaciones.
    * **Consultar mi agenda de turnos:** Interactúa con `AgendaTurnos` para ver los turnos que tiene asignados.
* **Colaboradores:** Estas son las otras clases con la que un objeto `ProfesionalSalud` tiene una relación o necesita interactuar:
  * `AgendaTurnos`: El `ProfesionalSalud` colabora con `AgendaTurnos` para consultar su agenda de turnos.
  * `Turno`: Un `ProfesionalSalud` colabora con `AgendaTurnos` para consultar su agenda de turnos.
* **Pensamiento del Objeto:** Esta sección refleja la "mentalidad" de un objeto `ProfesionalSalud`:
  * "Soy un profesional de la salud." - Representa su rol en el sistema.
  * "Tengo una matrícula única." - Refleja su identificación profesional.
  * "Tengo una especialidad médica." - Describe su área de expertise.
  * "Tengo un horario para atender." - Representa su disponibilidad.
  * "Tengo un número de teléfono." - Representa un medio de contacto.
  * "Tengo una dirección de correo." - Representa otro medio de contacto.
* **Propiedad:** Esta describe las características o atributos clave que definen a un objeto `ProfesionalSalud`:
  * **Nombre completo:** El nombre completo del profesional.
  * **Matrícula profesional:** El identificador único del profesional.
  * **Especialidad:** El área de especialización médica.
  * **Horario de atención:** Los dias y horas de disponibilidad.
  * **Teléfono:** El número de teléfono del profesional.
  * **Correo electrónico:** La dirección de correo electrónico del profesional.
  * **Identificador único (ID):** Aunque no se menciona explicitamente en las responsabilidades, implicitamente cada profesional tendrá un ID único para su identificación dentro del sistema.

## Código Java en el que me base para hacer la tarjeta CRC
```Java
class ProfesionalSalud {
    private String nombreCompleto;
    private String matriculaProfesional;
    private String especialidad;
    private String horarioAtencion;
    private String telefono;
    private String correoElectronico;
    private int idProfesional; // Propiedad implícita: Identificador único

    public ProfesionalSalud(String nombreCompleto, String matriculaProfesional, String especialidad, String horarioAtencion, String telefono, String correoElectronico, int idProfesional) {
        this.nombreCompleto = nombreCompleto;
        this.matriculaProfesional = matriculaProfesional;
        this.especialidad = especialidad;
        this.horarioAtencion = horarioAtencion;
        this.telefono = telefono;
        this.correoElectronico = correoElectronico;
        this.idProfesional = idProfesional;
    }

    // Getters y setters (omitidos para brevedad)

    public int getIdProfesional() {
        return idProfesional;
    }
}
```

3. **Turno**
![Tarjeta CRC Turno](/imagenesTarjetasCRC/tarjetaCRCTurno.png)
[Enlace a la Tarjeta CRC Turno](https://1drv.ms/i/c/f2bf844ed8279638/EQIfYQFjOt9Mk9xoiBBJ4hwBPRhbw8ZqoNnBMAFyZnBn1g?e=iXkwyj)

## Explicación de la Tarjeta CRC: Turno
La tarjeta CRC para la clase `Turno` describe la información y las relaciones fundamentales de un evento de consulta en nuestro sistema de gestión de turnos. Analicemos cada sección:
  * **Nombre de la Clase:** `Turno` - Este nombre reprensenta un evento especfífico en el tiempo en el que un paciente se reunirá con un profesional de la salud por un motivo particular.
  * **Superclase: (Vacio) - En el diseño actual, la clase `Turno` no hereda de ninguna otra clase directamente. Es una entidad fundamental por sí misma.
  * **Subclase:** (Vacío) - Tampoco tenemos subclases que especialicen el comportamiento o la información de un `Turno`. Todos los turnos comparten los atributos y relaciones básicos definidos en esta clase.
  * **Responsabilidades:** Estas son las principales piezas de información que un objeto `Turno` debe conocer y gestionar:
   * **Conocer la fecha y la hora del turno:** Almacena el momento específico que se llevará a cabo la consulta.
   * **Conocer el motivo de la consulta:** Describe la razón por la cual el paciente solicitó el turno.
   * **Conocer el estado del turno: indica la situación actual del turno (por ejemplo, `SOLICITADO`, `ASIGNADO`, `CANCELADO`, `COMPLETADO`)
   * **Conocer al paciente asociado:** Mantiene una referencia al objeto `Paciente` que solicitó y asistirá al turno.
   * **Conocer al profesional asociado:** Mantienen una referencia al objeto `ProfesionalSalud` que atenderá el turno.
* **Colaboradores:** Estas son las otras clases con las que un objeto `Turno` tiene una relación o necesita interactuar:
  * `Paciente`: Un `Turno` siempre está asociado a un `ProfesionalSalud` una ves que ha sido asignado.
  * `AgendaTurnos`: La clase que gestiona el ciclo de vida de los turnos y, por lo tanto, interactúa con los objetos `Turno` para crear, asignar y actualizar su estado.
* **Pensamiento del Objeto:** Esta sección refleja la "mentalidad" de un objeto `Turno`:
  * "Tengo una fecha y hora asignada." - Representa la información temporal del evento.
  * "Necesito indicar por qué pido el turno." - Desde la perspectiva de la razón de la consulta.
  * "Mi turno tiene un estado." - Refleja el ciclo de vida del turno.
  * "Este turno es para un paciente." - Indica la relación con el solicitante.
  * "Este turno es con un profesional." - Indica la relación con el proveedor de la consulta
* **Propiedad:** Esta describe las características o atributos clave que definen un objeto `Turno`:
  * **Fecha y hora:** El momento específico del evento.
  * **Motivo de consulta:** La razón de la cita.
  * **Estado:** La situación actual del turno.
  * **Paciente:** La persona que recibe la atención.
  * **ProfesionalSalud:** La persona que brinda la atención.

## Código Java en el que me base para realizar la tarjeta CRC

```Java
import java.time.LocalDateTime;

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

    public LocalDateTime getFechaHora() {
        return fechaHora;
    }

    public String getMotivoConsulta() {
        return motivoConsulta;
    }

    public String getEstado() {
        return estado;
    }

    public void setEstado(String estado) {
        this.estado = estado;
    }

    public Paciente getPaciente() {
        return paciente;
    }

    public ProfesionalSalud getProfesional() {
        return profesional;
    }

    public void asignarProfesional(ProfesionalSalud profesional) {
        this.profesional = profesional;
        this.estado = "ASIGNADO";
    }
}
```


4. **AgendaTurnos**
![Tarjeta CRC AgendaTurnos](/imagenesTarjetasCRC/tarjetaCRCAgendarTurnos.png)
[Enlace a Tarjeta CRC AgendaTurnos](https://1drv.ms/i/c/f2bf844ed8279638/EcF9G0Z6hrlFn2BlqR0okAABnJRPSZKgASarb5HMVUisTw?e=ZEvYYp)

## Explicación de la Tarjeta CRC: AgendaTurnos
La tarjeta CRC para la clase AgendaTurnos nos ayuda a comprender su rol central del sistema. Analicemos cada sección:
* **Nombre de la Clase:** `AgendaTurnos` - Este nombre indica claramente que la clase es responsable de la gestión y organización de los turnos.
* **Superclase;** (Vacío)- En el diseño actual, `AgendaTurnos` no hereda de ninguna otra clase directamente, Es una clase independiente que cordina la lógica de negocio.
* **Subclase:** (Vacío) - Tampoco tenemos subclases que especialicen el comportamiento de `AgendarTurnos`. Su responsabilidad es general para la gestión de turnos.
* **Responsabilidades:** Estas son las acciones o tareas principales que la clase `AgendaTurnos` debe llevar a cabo:
  * **Registrar la solicitud de un turno:** Cuando un `Paciente` desea solicitar un turno, `AgendaTurnos` recibe esa solicitud.
  * **Asignar un turno a un profesional:** `AgendaTurnos` es responsable de emparejar un `Turno` solicitado con un `ProfesionalSalud` disponible, posiblemente verificando su horario.
  * **Consultar turnos de un paciente:** Permite a un `ProfesionalSalud` ver la lista de sus turnos programados (pasados y futuros).
  * **Consultar la agenda de un profesional:** Permite a un `ProfesionalSalud` ver su lista de turnos asignados.
  * **Guardar la información del turno:** `AgendaTurnos` delega la tarea de almacenar los datos del `Turno` a través de la interfaz `ITurnoRepository`.
  * **Cargar la información de un turno:** Similar a guardar, `AgendaTurnos` utiliza `ITurnoRepository` para recuperar la información de un `Turno` específico.
* **Colaboradores:** Estas son otras clases u interfaces con las que `AgendaTurnos` necesita interactuar para cumplir con sus responsabilidades:
 * `Paciente`: Para registrar solicitudes y consultar sus turnos.
 * `Turno`: Es la entidad principal que `AgendaTurnos` gestiona (crea, asigna, consulta).
 * `ProfesionalSalud`: Para asignar turnos y consultar su agenda.
 * `ITurnoRepository`: La interfaz que `AgendaTurnos` utiliza para la persistencia de los objetos `Turno`. No depende de una implementación concreta de la base de datos, adhiriéndose al Principio de Inversión de Dependencias (DIP).
* **Pensamiento del Objeto:** Esta sección refleja la perspectiva o la "mentalidad" de un objeto `AgendaTurnos`:
 * "Alguien quiere pedir un turno." - Representa la recepción de una solicitud.
 * "Necesito programar una consulta con un médico." - Describe la lógica de asignación.
 * "Quiero ver mis turnos." - Desde la perspectiva de un paciente consultando su agenda.
 * "Necesito ver mi horario de atención." - Desde la perspectiva de un profesional consultando su agenda.
 * "La información del turno debe guardarse." - La necesidad de persistencia.
 * "Necesito recuperar la información de un turno." - La necesidad de cargar datos.
* **Propiedad:** Esta describe una característica o rol clave de la clase `AgendaTurnos` dentro del sistema:
 * **Gestión central de turnos:** `AgendaTurnos` actúa como el punto central para todas las operaciones relacionadas con los turnos.
 * **Lógica de asignación:** Contiene la inteligencia para decidir cómo y cuaándo se asignan los turnos.
 * **Acceso a la lista de turnos por paciente:** Proporciona la funcionalidad para obtener los turnos de un paciente.
 * **Acceso a la lista de turnos por profesional:** Proporciona la funcionalidad para obtener la agenda de un profesional.
 * **Orquestación de la persistencia:** Delega y coordina el guardado de la información de los turnos.
 * **Orquestación de la recuperación:** Delega y coordina la carga de la información de los turnos.

 ## Código Java según la Tarjeta CRC de AgendaTurnos

 ```Java
import java.time.LocalDateTime;
import java.util.List;

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

    // Método para guardar un turno (delegado al repositorio)
    public void guardarTurno(Turno turno) {
        turnoRepository.guardarTurno(turno);
    }

    // Método para cargar un turno (delegado al repositorio)
    public Turno cargarTurno(int idTurno) {
        return turnoRepository.cargarTurno(idTurno);
    }
}
```


5. **ITurnoRepository(Interfaz)**
![Tarjeta CRC ITurnoRepository](/imagenesTarjetasCRC/tarjetaCRCIITurnoRepository(Interfaz).png)
[Enlace a Tarjeta CRC ITurnoRepository](https://1drv.ms/i/c/f2bf844ed8279638/Ef0zS8E0A_JCgmO_ssP2iDQBbhI7amX-lQyXBvf0QTgsgw?e=jeWVNO)

## Explicación de la Tarjeta CRC: ITurnoRepository (Interfaz)

La tarjeta CRC para la interfaz `ITurnoRepository` define el contrato que deben seguir las clases
responsables de la persistencia de la información de los turnos.
* **Nombre de la Clase:** `ITurnoRepository` (interfaz) - El sufijo "Interfaz" indica que no es una clase concreta, sino un contrato que define un conjunto de métodos que deben ser implementados por otras clases.
* **Superclase:(Vacío)** - Las interfaces en Java no extienden otras clases, aunque pueden extender otras interfaces.
* **Subclase:** `MySQLTurnoRepository`, `PostgreSQLTurnoRepository` - Estas son las clases concretas que implementan la interfaz `ITurnoRepository`. Esto significa que cada una de ellas proporcionará una forma específica de interactuar con su respectiva base de datos para guardar, cargar y consultar la información de los turnos.
* **Responsabilidades:** Estas son las acciones o los servicios que cuaslquier clase que implemente `IturnoRepository` debe proporcionar:
 * **Definir cómo se guarda un turno:** Especifica la firma del método para almacenar la información de un objeto `Turno`. La implementación concreta decidirá cómo se guarda (en una base de datos, un archivo, etc.).
 * **Definir cómo se carga un turno:** Especifica la firma del método para recuperar la información de un objeto `Turno` basado en su identificador (`int idTurno`).
 * **Definir cómo se obtienen turnos por paciente:** Específica la firma del método para recuperar todos los turnos asociados a un objeto `Paciente` específico.
 * **Definir cómo se obtienen turnos por profesional:** Especifica la firma del método para recuperar todos los turnos asociados a un objeto `ProfesionalSalud` específico.
* **Colaboradores:** Estas son las otras clases o entidades cons las que las implementaciones de `ITurnoRepository` necesitan interactuar:
 * `Turno`: La entidad principal cuya información se va a persistir y recuperar.
 * `Paciente`: Necesario para la responsabilidad de obtener turnos por profesional.
 * `ProfesionalSalud`: Necesario para la responsabilidad de obtener turnos por profesional.
* **Pensamiento del Objeto:** Esta sección refleja propósito de la interfaz:
 * "Un turno necesita ser almacenado." - Indica la necesidad de la persistencia.
 * "Necesito obtener la información de un turno." - Indica la necesidad de recuperación por ID
 * "Quiero buscar los turnos de un paciente." - Indica la necesidad de consultas por profesional.
* **Propiedad:** Esta describe el rol clave de la interfaz dentro del sistema:
 * **Abstracción de la persistencia:** `ITurnoRepository` actúa como una capa de abstracción, ocultando los detalles específicos de cómo se almacena y recuperan los datos. La clase `AgendaTurnos` (y otras que necesiten acceder a los datos de los turnos) dependen de esta interfaz, no de una implementación concreta de la base de datos.
 * **Abstracción de la consulta:** Similar a la persistencia, también abstrae la forma en que se realizan las consultas de turnos.

## Código Java según la Tarjeta CRC de ITurnoRepository (Interfaz)

```Java
import java.util.List;

interface ITurnoRepository {
    void guardarTurno(Turno turno);
    Turno cargarTurno(int idTurno);
    List<Turno> obtenerTurnosPorPaciente(Paciente paciente);
    List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional);
}
```


6. **MySQLTurnoRepository**
![Tarjeta CRC MySQLRepository](/imagenesTarjetasCRC/tarjetaCRCMySQLTurnoRepository.png)
[Enlace a Tarjeta CRC MySQLRepository](https://1drv.ms/i/c/f2bf844ed8279638/EXqkuLIzGrRMjC3cZBP6WggB41riruXZNtvjJo3Rm6PA0w?e=6fPDvr)

## Explicación de la tarjeta CRC: MySQLTurnoRepository
Las tarjeta CRC para la clase `MySQLTurnoRepository` describe cómo esta clase se encarga de la persistencia de los objetos `Turno` utilizando la base de datos MySQL en nuestro sistema de gestión de turnos. Analicemos cada sección:
  * **Nombre de la Clase:** `MySQLTurnoRepository` - Indica que esta clase es un repositorio espefífico para la tecnológia de base de datos MySQL
  * **Superclase:** `TurnoRepository` - Sería una clase abstracta o una interfaz (aunque en el diseño final se uso `ITurnoRepository`). Si es una clase abstracta, contendría la lógica común a los repositorios de turnos. Si fuera otra interfaz, `MySQLTurnoRepository` la implementaría junto con `ITurnoRepository`. Para mantener la coherencia con el diseño.
  * **Subclase: (Vacío)** - No hay subclases que especialicen el comportamiento de `MySQLTurnoRepository`.
  * **Responsabilidades:** Estas son las principales acciones que `MySQLTurnoRepository` debe llevar a cabo:
    * **Guardar un turno en MySQL:** Implementa la lógica para persistir la información de un objeto `Turno` en las tablas correspondientes de la base de datos MySQL.
    * **Cargar un turno desde MySQL:** Implementa la lógica para recuperar un objeto `Turno` desde la base de datos MySQL basándose en su identificador único.
    * **Obtener turnos por paciente desde MySQL:** Implementa la lógica para consultar y recuperar todos los objetos `Turno` asociados a un `Paciente` especifico desde la base de datos MySQL.
    * **Obtener turnos por profesional desde MySQL:** Implementa la lógica para consultar y recuperar todos los objetos `Turno` asociados a un `Paciente` específico desde la base de datos MySQL.
* **Colaboradores:** Estas son las otras clases o componentes con los que `MySQLTurnoRepository` necesita interactuar:
  * `Turno`: Los objetos `Turno` son los que se guardan y se cargan.
  * `Paciente`: Necesario para la responsabilidad de obtener turnos por paciente.
  * `ProfesionalSalud`: Necesario para la responsabilidad de obtener turnos por profesional.
  * Componentes de la base de datos MySQL (implícito): La clase necesita interactuar con el driver JDBC de MySQL para ejecutar comandos SQL y gestionar la conexión.
* **Pensamiento del Objeto:** Esta sección refleja la "mentalidad" de un objeto `MySQLTurnoRepository`:
  * "Guardo la información del turno en la base de datos MySQL." - Describe su función principal de persistencia.
  * "Obtengo la información del turno desde la base de datos MySQL." - Describe su función de recuperación por ID.
  * "Busco los turnos de un paciente en MySQL." - Describe su función de consulta por paciente.
  * "Busco los turnos de un profesional en MySQL." - Describe su función de consulta por profesional.
* **Propiedad:** Esta describe las características o conceptos clave asociados a `MySQLTurnoRepository`:
  * **Conexión a la base de datos MySQL:** Necesita establecer y gestionar una conexión con la instancia de la base de datos MySQL.
  * **Estructura de tablas de turnos en MySQL:** Depende de la existencia y el esquema de las tablas relacionadas con los turnos en la base de datos MySQL.
  * **Consultas SQL específicas de MySQL:** Utiliza la sintaxis y las caracteristicas especificas del lenguaje SQL soportado por MySQL para realizar las operaciones de persistencia y consulta.

## Código Java que use como base para crear la tarjeta CRC: MySQLTurnoRepository

```Java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

class MySQLTurnoRepository implements ITurnoRepository { // Asumiendo implementación de ITurnoRepository
    private Connection conexion;

    public MySQLTurnoRepository(String url, String usuario, String password) throws SQLException {
        this.conexion = DriverManager.getConnection(url, usuario, password);
    }

    @Override
    public void guardarTurno(Turno turno) {
        String sql = "INSERT INTO turnos (fecha_hora, motivo_consulta, estado, paciente_id, profesional_id) VALUES (?, ?, ?, ?, ?)";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setTimestamp(1, Timestamp.valueOf(turno.getFechaHora()));
            pstmt.setString(2, turno.getMotivoConsulta());
            pstmt.setString(3, turno.getEstado());
            pstmt.setInt(4, turno.getPaciente().getIdPaciente());
            if (turno.getProfesional() != null) {
                pstmt.setInt(5, turno.getProfesional().getIdProfesional());
            } else {
                pstmt.setNull(5, Types.INTEGER);
            }
            pstmt.executeUpdate();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    @Override
    public Turno cargarTurno(int idTurno) {
        String sql = "SELECT * FROM turnos WHERE id_turno = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, idTurno);
            ResultSet rs = pstmt.executeQuery();
            if (rs.next()) {
                // Lógica para crear un objeto Turno desde el ResultSet (requiere acceso a Paciente y Profesional por ID)
                // Esto podría implicar colaboradores adicionales o una forma de obtener estas entidades.
                return null; // Placeholder
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return null;
    }

    @Override
    public List<Turno> obtenerTurnosPorPaciente(Paciente paciente) {
        List<Turno> turnos = new ArrayList<>();
        String sql = "SELECT * FROM turnos WHERE paciente_id = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, paciente.getIdPaciente());
            ResultSet rs = pstmt.executeQuery();
            // Lógica para crear objetos Turno desde el ResultSet y agregarlos a la lista (requiere acceso a Profesional por ID)
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return turnos;
    }

    @Override
    public List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional) {
        List<Turno> turnos = new ArrayList<>();
        String sql = "SELECT * FROM turnos WHERE profesional_id = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, profesional.getIdProfesional());
            ResultSet rs = pstmt.executeQuery();
            // Lógica para crear objetos Turno desde el ResultSet y agregarlos a la lista (requiere acceso a Paciente por ID)
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return turnos;
    }
}
```

7. **PostgreSQLTurnoRepository**
![Tarjeta CRC PostgreSQLTurnoRepository](/imagenesTarjetasCRC/tarjetaCRCPostgreSQLTurnoRepository.png)
[Enlace a Tarjeta CRC PostgreSQLTurnoRepository](https://1drv.ms/i/c/f2bf844ed8279638/EROoFeuafWJBkQYcbPi2xCUBBGt96LkL-oBva839cHRVBQ?e=rdBP3t)

## Explicación de la Tarjeta CRC: PostgreSQLTurnoRepository
Las tarjeta CRC para la clase`PostgreSQLTurnoRepository` describe cómo esta clase se encarga de la persistencia de los objetos `Turno` utilizando la base de datos PostgreSQL en nuestro sistema de gestión de turnos. Analicemos cada sección:
* **Nombre de la Clase:** `PostgreSQLTurnoRepository` - Indica que esta clase es un repositorio específico para la tecnología de base de datos PostgreSQL.
* **Superclase:** `TurnoRepository` - Al igual que con `MySQLTurnoRepository`, asumo que `TurnoRepository` sería una clase abstracta o una interfaz (aunque en el diseño final se uso ITurnoRepository). La trataré como implementando `ITurnoRepository` para mantener la coherencia.
* **Subclase: (Vacío) - No tenemos subclases que especialicen el comportamiento de `PostgreSQLTurnoRepository`
* **Responsabilidades:** Estas son la principales acciones que `PostgreSQLTurnoRepository` debe llevar a cabo:
  * **Guardar un turno en PostgreSQL:** Implementa la lógica para persistir la información de un objeto `Turno` en las tablas correspondientes de la base de datos PostgreSQL.
  * **Cargar un turno desde PostgreSQL:** Implementa la lógica para recuperar un objeto `Turno` desde la base de datos PostgreSQL basándose en su identificador único.
  * **Obtener turnos por paciente desde PostgreSQL:** Implementa la lógica para consultar y recuperar todos los objetos `Turno` asociados a un `Paciente` específico dede la base de datos PostgreSQL.
  * **Obtener turnos por profesional desde PostgreSQL:** Implementa la lógica para consultar y recuperar todos los objetos `Turno` asociados a un `ProfesionalSalud` específico desde la base de datos PostgreSQL.
* **Colaboradores:** Estas son las otras clases o componentes con los que `PostgreSQLTurnoRepository` necesita interactuar:
* `Turno`: Los objetos `Turno` son los que se guardan y se cargan.
* `Paciente`: Necesario para la responsabilidad de obtener turnos por paciente.
* `ProfesionalSalud`: Necesario para la responsabilidad de obtener turnos por profesional.
* Componentes de la base de datos PostgreSQL (implicito): La clase necesita interactuar con el driver JDBC de PostgreSQL para ejecutar comandos SQL y gestionar la conexión.
* **Pensamiento del Objeto:** Esta sección refleja la "mentalidad" de un objeto `PostgreSQLTurnoRepository`:
  * "Guardando la información del turno en la base de datos PostgreSQL." - Describe su función principal de persistencia.
  * "Obtengo la información del turno desde la base de datos PostgreSQL." - Describe su función de recuperación por ID.
  * "Busco los turnos de un paciente en PostgreSQL." - Describe su función de consulta por paciente.
  * "Busco los turnos de un profesional en PostgreSQL." - Describe sun función de consulta por profesional.
* **Propiedad:** Esta describe las caracteristicas o conceptos clave asociados a `PostgreSQLTurnoRepository`:
  * **Conexión a la base de datos PostgreSQL:** Necesita establecer y gestionar una conexión con la instancia de la base de datos PostgreSQL.
  * **Estructura de tablas de turnos en PostgreSQL:** Depende de la existencia y el esquema de las tablas relacionadas con los turnos en la base de datos PostgreSQL.
  * **Consulta SQL especificas de PostgreSQL:** Utiliza la sintaxis y las caracteristicas específicas del lenguaje SQL soportado por PostgreSQL para realizar las operaciones de persistencia y consula.

## Código Java en el que use como estructura para hacer la tarjeta CRC y la explicación

```Java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

class PostgreSQLTurnoRepository implements ITurnoRepository { // Asumiendo implementación de ITurnoRepository
    private Connection conexion;

    public PostgreSQLTurnoRepository(String url, String usuario, String password) throws SQLException {
        this.conexion = DriverManager.getConnection(url, usuario, password);
    }

    @Override
    public void guardarTurno(Turno turno) {
        String sql = "INSERT INTO turnos (fecha_hora, motivo_consulta, estado, paciente_id, profesional_id) VALUES (?, ?, ?, ?, ?)";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setTimestamp(1, Timestamp.valueOf(turno.getFechaHora()));
            pstmt.setString(2, turno.getMotivoConsulta());
            pstmt.setString(3, turno.getEstado());
            pstmt.setInt(4, turno.getPaciente().getIdPaciente());
            if (turno.getProfesional() != null) {
                pstmt.setInt(5, turno.getProfesional().getIdProfesional());
            } else {
                pstmt.setNull(5, Types.INTEGER);
            }
            pstmt.executeUpdate();
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    @Override
    public Turno cargarTurno(int idTurno) {
        String sql = "SELECT * FROM turnos WHERE id_turno = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, idTurno);
            ResultSet rs = pstmt.executeQuery();
            if (rs.next()) {
                // Lógica para crear un objeto Turno desde el ResultSet (requiere acceso a Paciente y Profesional por ID)
                return null; // Placeholder
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return null;
    }

    @Override
    public List<Turno> obtenerTurnosPorPaciente(Paciente paciente) {
        List<Turno> turnos = new ArrayList<>();
        String sql = "SELECT * FROM turnos WHERE paciente_id = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, paciente.getIdPaciente());
            ResultSet rs = pstmt.executeQuery();
            // Lógica para crear objetos Turno desde el ResultSet
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return turnos;
    }

    @Override
    public List<Turno> obtenerTurnosPorProfesional(ProfesionalSalud profesional) {
        List<Turno> turnos = new ArrayList<>();
        String sql = "SELECT * FROM turnos WHERE profesional_id = ?";
        try (PreparedStatement pstmt = conexion.prepareStatement(sql)) {
            pstmt.setInt(1, profesional.getIdProfesional());
            ResultSet rs = pstmt.executeQuery();
            // Lógica para crear objetos Turno desde el ResultSet
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return turnos;
    }
}
```

### Enlace a archivo excel para ver todas las tarjetas CRC

[Enlace al archivo Tarjetas CRC](https://1drv.ms/x/c/f2bf844ed8279638/EW-LuJsNRAtHro9_5u8UIrYB9UnOIT7l6zB2yuRjUJ8TNw?e=Df4td3)
