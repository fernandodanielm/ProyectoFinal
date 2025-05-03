## Casos de Escenario de Uso

### Caso de Escenario de Uso 1: Registro Exitoso de un Nuevo Paciente

* **Caso de Uso Base:** Registrar Paciente
* **Actor Principal:** Personal Administrativo
* **Escenario:** El Personal Administrativo registra exitosamente a un nuevo paciente en el sistema.
* **Flujo del Escenario:**
    1.  El Personal Administrativo hace clic en "Nuevo Paciente" en la interfaz.
    2.  El sistema presenta el formulario de registro.
    3.  El Personal Administrativo ingresa:
        * Nombre Completo: "Ana Pérez"
        * Número de Documento: "30123456"
        * Fecha de Nacimiento: "15/03/1985"
        * Teléfono: "1144445555"
        * Correo Electrónico: "ana.perez@email.com"
    4.  El Personal Administrativo hace clic en "Guardar".
    5.  El sistema valida que el número de documento y el correo electrónico tengan un formato correcto y no existan previamente en la base de datos.
    6.  El sistema almacena la información de Ana Pérez en la base de datos (creando una nueva instancia de la clase `Paciente`).
    7.  El sistema muestra el mensaje "Paciente registrado exitosamente con ID: [ID asignado]".
* **Postcondiciones:** Un nuevo objeto `Paciente` con la información de Ana Pérez ha sido creado y persistido en el sistema.

### Caso de Escenario de Uso 2: Asignación de un Turno Existente a un Paciente

* **Caso de Uso Base:** Asignar Turno
* **Actor Principal:** Personal Administrativo
* **Escenario:** El Personal Administrativo asigna un turno para el Dr. López (especialidad Cardiología) el día 05/05/2025 a las 10:00 a la paciente Ana Pérez.
* **Flujo del Escenario:**
    1.  El Personal Administrativo selecciona "Asignar Turno".
    2.  El sistema solicita la selección del paciente. El Personal Administrativo busca y selecciona a "Ana Pérez" (ID: [Su ID]).
    3.  El sistema solicita la selección del profesional. El Personal Administrativo selecciona al "Dr. López" (ID: [Su ID], Especialidad: Cardiología).
    4.  El sistema muestra la agenda del Dr. López para el 05/05/2025.
    5.  El Personal Administrativo selecciona el horario de las 10:00.
    6.  El sistema verifica la disponibilidad del Dr. López a las 10:00 (consultando la `AgendaTurnos` y los `Turno`s existentes). Asumimos que está disponible.
    7.  El Personal Administrativo ingresa el motivo del turno: "Control de rutina".
    8.  El Personal Administrativo hace clic en "Confirmar".
    9.  El sistema crea un nuevo objeto `Turno` con fecha/hora 05/05/2025 10:00, estado "Pendiente", motivo "Control de rutina", y referencias a la `Paciente` Ana Pérez y al `ProfesionalSalud` Dr. López. Este `Turno` se asocia a la `AgendaTurnos`.
    10. El sistema muestra el mensaje "Turno asignado exitosamente".
    11. El sistema envía una notificación por correo electrónico a ana.perez@email.com y al Dr. López (si la notificación por correo electrónico está implementada a través de la interfaz `ServicioNotificacion`).
* **Postcondiciones:** Un nuevo objeto `Turno` ha sido creado y asociado a la agenda. El paciente y el profesional han sido notificados (si corresponde).

### Caso de Escenario de Uso 3: Paciente Consulta su Historial de Turnos

* **Caso de Uso Base:** Consultar Historial del Paciente
* **Actor Principal:** Paciente (Ana Pérez)
* **Escenario:** La paciente Ana Pérez consulta su historial de turnos en el sistema.
* **Flujo del Escenario:**
    1.  Ana Pérez inicia sesión en el portal de pacientes.
    2.  Ana Pérez hace clic en "Mi Historial".
    3.  El sistema identifica a Ana Pérez por su ID de sesión.
    4.  El sistema consulta la base de datos y recupera todos los objetos `Turno` asociados al ID de Ana Pérez (posiblemente a través de la clase `HistorialTurnosPaciente` o directamente desde la relación `Paciente` - `Turno`).
    5.  El sistema muestra una lista de los turnos pasados y futuros de Ana Pérez, incluyendo fecha, hora, profesional y motivo.
* **Postcondiciones:** Se muestra a Ana Pérez su historial de turnos.

### Caso de Escenario de Uso 4: Personal Administrativo Cancela un Turno Próximo

* **Caso de Uso Base:** Cancelar Turno
* **Actor Principal:** Personal Administrativo
* **Escenario:** El Personal Administrativo cancela el turno de Ana Pérez con el Dr. López del 05/05/2025 a las 10:00 debido a una indisponibilidad del médico.
* **Flujo del Escenario:**
    1.  El Personal Administrativo selecciona "Cancelar Turno".
    2.  El sistema solicita la búsqueda del turno. El Personal Administrativo busca por paciente "Ana Pérez" y fecha "05/05/2025".
    3.  El sistema muestra el turno de Ana Pérez con el Dr. López a las 10:00.
    4.  El Personal Administrativo selecciona este turno y hace clic en "Cancelar".
    5.  El sistema verifica si la cancelación está permitida (por ejemplo, con suficiente antelación). Asumimos que sí.
    6.  El Personal Administrativo ingresa el motivo de la cancelación: "Indisponibilidad del médico".
    7.  El Personal Administrativo confirma la cancelación.
    8.  El sistema actualiza el estado del objeto `Turno` correspondiente a "Cancelado" en la base de datos.
    9.  El sistema muestra el mensaje "Turno cancelado exitosamente".
    10. El sistema envía una notificación por correo electrónico a ana.perez@email.com y al Dr. López notificando la cancelación (a través de `ServicioNotificacion`).
* **Postcondiciones:** El estado del turno ha sido actualizado a "Cancelado". El paciente y el profesional han sido notificados.

### Caso de Escenario de Uso 5: Personal Administrativo Registra un Nuevo Profesional de la Salud

* **Caso de Uso Base:** Registrar Profesional de la Salud
* **Actor Principal:** Personal Administrativo
* **Escenario:** El Personal Administrativo registra al Dr. Carlos Gómez (especialidad Pediatría) en el sistema.
* **Flujo del Escenario:**
    1.  El Personal Administrativo hace clic en "Nuevo Profesional".
    2.  El sistema presenta el formulario de registro de profesional.
    3.  El Personal Administrativo ingresa los datos personales:
        * Nombre Completo: "Carlos Gómez"
        * Número de Documento: "20987654"
        * Fecha de Nacimiento: "22/07/1978"
        * Teléfono: "1133332222"
        * Correo Electrónico: "carlos.gomez@email.com"
    4.  El Personal Administrativo ingresa los datos profesionales:
        * Matrícula Profesional: "MP12345"
        * Especialidad: "Pediatría"
        * Horario de Atención: (Se ingresa el horario según la interfaz, por ejemplo, "Lunes a Viernes de 9:00 a 17:00")
    5.  El Personal Administrativo hace clic en "Guardar".
    6.  El sistema valida que la matrícula profesional no exista previamente.
    7.  El sistema almacena la información del Dr. Carlos Gómez en la base de datos (creando una nueva instancia de la clase `ProfesionalSalud`).
    8.  El sistema muestra el mensaje "Profesional registrado exitosamente con ID: [ID asignado]".
* **Postcondiciones:** Un nuevo objeto `ProfesionalSalud` con la información del Dr. Carlos Gómez ha sido creado y persistido en el sistema.