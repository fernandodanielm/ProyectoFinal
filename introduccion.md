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

## Requisitos Iniciales del Sistema

1.  **Registro de Pacientes:** El sistema debe permitir registrar la información básica de un nuevo paciente (nombre completo, número de documento, fecha de nacimiento, teléfono, correo electrónico).
2.  **Registro de Médicos:** El sistema debe permitir registrar la información de un nuevo profesional de la salud (nombre, matrícula profesional, especialidad, horario de atención, teléfono, correo electrónico).
3.  **Solicitud de Turno:** Un paciente debe poder solicitar un turno especificando la fecha, hora deseada y el motivo de la consulta.
4.  **Asignación de Turnos:** El sistema debe permitir asignar un turno a un paciente con un médico específico, verificando la disponibilidad del médico en la fecha y hora solicitadas.
5.  **Consulta de Turnos:** Tanto los pacientes como los médicos deben poder consultar sus turnos programados (fecha, hora, médico/paciente, estado).

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


[Enlace para visualizar el boceto en línea](https://1drv.ms/i/c/f2bf844ed8279638/EYWt67Y45_hOi_NOFG8invUBEwNZQJin11c6xzvQbu9xDw?e=DtGMKS)

**Descripción del Boceto Inicial de Clases:**

Este boceto inicial presenta las clases fundamentales identificadas para el sistema de gestión de turnos:

* **Paciente:** Representa a los pacientes del centro de salud. Contiene atributos como nombre, documento, contacto y un historial de turnos asociados. Podría tener métodos como solicitarTurno(), cancelarTurno(), consultarHistorial().
* **ProfesionalSalud:** Representa a los profesionales de la salud, Contiente atributos como nombre, matricula, especialidad, horario y contacto. Pordría tener métodos como consultarAgenda(), verDetalleTurno().
* **Turno:** Representa una cita médica. Contiene atributos como fechaHora, estado, medico (referencia a ProfesionalSalud), paciente (referencia a Paciente) y motivo. Podría tener métpdps como confirmar(), cancelar(), obtenerDetalle().
* **AgendarTurnos:** Representa la agenda del sistema para gestionar los turnos. Podría tener métodos como asignarTurno(), cancelarTurno(), modificarTurno(), consultarTurnosPorPaciente(), consultarTurnosPorMedico().
* **PersonalAdministrativo:** Representa al personal administrativo que gestiona el sistema. Contiene atributos como nombre, usuario, contraseña y métodos como registrarPaciente(), registrarProfesional(), asignarTurno(), cancelarTurno().
* **Persona:** Una clase abstracta o superclase que contiene atributos comunes a Paciente, ProfesionalSalud y PersonalAdministrativo, como nombre, documento y fechaNacimiento.

Las relaciones iniciales visualizadas en el boceto (a través de líneas con flechas) sugieren asociaciones y herencia entre estas clase. Por ejemplo, Paciente y ProfesionalSalid heredan de Persona. Un Paciente y un ProfesionalSalid están asociados a un Turno. La AgendaTurnos gestiona los Turnos, y el PersonalAdministrativo interactúa con Pacientes, ProfesionalSalud y AgendaTurnos para gestionar el sistema.