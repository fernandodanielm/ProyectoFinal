# Diagrama de Secuencias

* Diagrama de Secuencia - ConsultarAgendaProfesional 

![Diagrama de Secuencia - ConsultarAgendaProfesional](/imagenesDiagramasDeSecuencia/diagramadesecuencias1ConsultarAgendaProfesional.png)

[Enlace a la imagen de Diagrama de Secuencia - ConsultarAgendaProfesional ](https://1drv.ms/i/c/f2bf844ed8279638/EaruUIblhvJElRuRCFUjx1UBaracQXtmgwmm70QJOJGOhw?e=35GdWU)

# Descripción del Diagrama de Secuencia: Consulta Turnos Paciente

Este diagrama de secuencia ilustra la interacción entre diferentes participantes del sistema para el caso de uso "Consulta Turnos Paciente".

El proceso comienza cuando el **\_01\_Paciente** envía un mensaje "Selecciona 'Mis Turnos'" a la **\_02\_Interfaz del Sistema**.

Al recibir este mensaje, la **\_02\_Interfaz del Sistema** se activa y, posteriormente, el **\_01\_Paciente** envía otro mensaje "Solicitar Mis Turnos" a la misma interfaz.

La **\_02\_Interfaz del Sistema** recibe esta solicitud y envía un mensaje "consultarTurnosPaciente(PAC-123)" al **\_03\_Sistema**.

El **\_03\_Sistema** se activa y, a su vez, envía un mensaje "Consultar Turnos (PAC-123)" a la **\_06\_Base de Datos (de Turnos Asignados)**.

La **\_06\_Base de Datos (de Turnos Asignados)** responde al **\_03\_Sistema** con un mensaje punteado "Lista de Turnos del Paciente", indicando la devolución de la información solicitada.

Finalmente, el **\_03\_Sistema** envía un mensaje "mostrarTurnosPaciente(listaDeTurnos)" a la **\_02\_Interfaz del Sistema**, que se activa para mostrar la información de los turnos al paciente (esta última interacción visual con el paciente no se muestra explícitamente con una flecha saliente).

El diagrama muestra la secuencia de mensajes y las activaciones de los diferentes componentes del sistema involucrados en la consulta de los turnos de un paciente.

* Diagrama de Secuencia - Solicitar Turno 

![DDS-ST](/imagenesDiagramasDeSecuencia/diagramadesecuencias2SolicitarTurno.png)

[Enlace a la imagen de Diagrama de Secuencia - Solicitar Turno](https://1drv.ms/i/c/f2bf844ed8279638/EfdDOgWoQ8xFmf7OJECKWTUBYhLwI_801PLG_Ptcwa14ag?e=BEUle8)

# Descripción del Diagrama de Secuencia: Solicitar Turno

Este diagrama de secuencia ilustra el flujo de interacciones entre diferentes participantes del sistema para el caso de uso "Solicitar Turno".

El proceso comienza cuando el **\_01\_Paciente** interactúa con la **\_02\_Interfaz del Sistema** para seleccionar la opción de "Solicitar Turno". Esto se representa con un mensaje "Selecciona 'Solicitar Turno'".

A continuación, el **\_01\_Paciente** proporciona detalles sobre el turno deseado, incluyendo la fecha, hora y motivo. Estos se capturan en mensajes separados: "Selecciona Fecha: 2025-05-08", "Selecciona Hora: 14:30" y "Selecciona Motivo: Control de rutina".

Una vez que el **\_01\_Paciente** ha proporcionado todos los detalles, confirma la solicitud enviando un mensaje "Click en 'Confirmar Turno'" a la **\_02\_Interfaz del Sistema**.

La **\_02\_Interfaz del Sistema** recibe esta confirmación y envía un mensaje "solicitarTurno(pacienteId, 2025-05-08, 14:30, Control de rutina)" al **\_03\_Sistema**, que contiene la información del paciente y los detalles del turno solicitado.

El **\_03\_Sistema** se activa y a su vez, envía un mensaje "Guardar Solicitud de Turno" a la **\_04\_Base de Datos**, donde se persiste la solicitud.

Finalmente, la **\_04\_Base de Datos** responde al **\_03\_Sistema** (esta respuesta no se muestra explícitamente en el diagrama), y el **\_03\_Sistema** envía un mensaje "confirmacionSolicitud(CU-001-20250508-1430)" a la **\_02\_Interfaz del Sistema**, que contiene un identificador único de la solicitud.  La **\_02\_Interfaz del Sistema** recibe esta confirmación y la muestra al paciente (esta última interacción visual con el paciente no se muestra explícitamente con una flecha saliente).

El diagrama muestra la secuencia de pasos desde que el paciente inicia la solicitud hasta que se guarda en la base de datos y se genera una confirmación.


* Diagrama de Secuencia - Asignar Turno 

![DDS-AT](/imagenesDiagramasDeSecuencia/diagramadesecuencia3AsignarTurno.png)

[Enlace a la imagen de Diagrama de Secuencia - Solicitar Turno](https://1drv.ms/i/c/f2bf844ed8279638/EZmhJKbI7VFDswpEBVFW_wABj4kbhwwzPqduNIkiRQD6Dw?e=zUqfqS)

# Descripción del Diagrama de Secuencia: Asignar Turno

Este diagrama de secuencia ilustra el flujo de interacciones entre varios participantes del sistema para el caso de uso "Asignar Turno".

El proceso comienza cuando el **\_01\_Administrador/Recepcionista** interactúa con la **\_02\_Interfaz del Sistema** para iniciar la asignación de un turno. Esto se representa con los siguientes mensajes secuenciales: "Selecciona 'Asignar Turno'", "Selecciona Solicitud: SOL-005" y "Selecciona Profesional: PROF-123", seguido de la confirmación con "Click en 'Asignar Turno'".

La **\_02\_Interfaz del Sistema** recibe estas interacciones y envía un mensaje "mostrarDisponibilidad(2025-05-08, 14:30)" al **\_03\_Sistema** para obtener la lista de profesionales disponibles.

El **\_03\_Sistema** se activa y consulta la disponibilidad de profesionales enviando un mensaje "Consultar Disponibilidad (2025-05-08, 14:30)" a la **\_05\_Base de datos (de Profesionales)**.

La **\_05\_Base de datos (de Profesionales)** responde al **\_03\_Sistema** con un mensaje punteado "Lista de Profesionales Disponibles".

El **\_03\_Sistema** luego envía esta lista de vuelta a la **\_02\_Interfaz del Sistema** con el mensaje "Mostrar Profesionales Disponibles".

Tras la selección del profesional y la confirmación, la **\_02\_Interfaz del Sistema** envía un mensaje "asignarTurno(SOL-005, PROF-123)" al **\_03\_Sistema**.

El **\_03\_Sistema** se encarga de actualizar la información del turno. Envía un mensaje "UPDATE Solicitudes SET estado = 'Asignado', profesionalAsignado = 'PROF-123' WHERE solicitudId = 'SOL-005'" a la **\_04\_Base de Datos (de Solicitudes de Turno)** para actualizar el estado de la solicitud.

Además, el **\_03\_Sistema** inserta la información del turno asignado en la **\_06\_Base de Datos (de Turnos Asignados)** con el mensaje "INSERT INTO TurnosAsignados (solicitudId, profesionalId, fecha, hora) VALUES ('SOL-005', 'PROF-123', '2025-05-08', '14:30')".

Finalmente, el **\_03\_Sistema** notifica la asignación enviando un mensaje "enviarNotificacion(PAC-456, PROF-123, 2025-05-08, 14:30)" al **\_07\_Sistema de Notificaciones**, y envía una "Confirmación de Asignación" a la **\_02\_Interfaz del Sistema** para informar al administrador/recepcionista.

El diagrama ilustra la secuencia completa de pasos involucrados en la asignación de un turno, incluyendo la interacción con múltiples bases de datos y el sistema de notificaciones.

* Diagrama de Secuencia - Consultar Turno Paciente 

![DDS-CTP](/imagenesDiagramasDeSecuencia/diagramadecasodesecuencia4ConsultarTurnoPaciente.png)

[Enlace a la imagen de Diagrama de Secuencia - Consultar Turno Paciente](https://1drv.ms/i/c/f2bf844ed8279638/EbH6rhsPVvlIrpJ-PeZ9slABoCnnToivxH0HIvjM8CioDw?e=GJpc2h)

# Descripción del Diagrama de Secuencia: Consultar Turno Paciente

Este diagrama de secuencia ilustra el flujo de interacciones entre diferentes participantes del sistema para el caso de uso "Consultar Turno Paciente".

El proceso comienza cuando el **\_01\_Paciente** envía un mensaje "Selecciona 'Mis Turnos'" a la **\_02\_Interfaz del Sistema**.

A continuación, el **\_01\_Paciente** envía el mensaje "Solicitar Mis Turnos" a la **\_02\_Interfaz del Sistema**.

La **\_02\_Interfaz del Sistema** recibe esta solicitud y envía un mensaje "consultarTurnosPaciente(PAC-123)" al **\_03\_Sistema**.

El **\_03\_Sistema** se activa y, a su vez, envía un mensaje "Consultar Turnos (PAC-123)" a la **\_06\_Base de Datos (de Turnos Asignados)**.

La **\_06\_Base de Datos (de Turnos Asignados)** responde al **\_03\_Sistema** con un mensaje "Lista de Turnos del Paciente", indicando la devolución de la información solicitada.

Finalmente, el **\_03\_Sistema** envía un mensaje "mostrarTurnosPaciente(listaDeTurnos)" a la **\_02\_Interfaz del Sistema**, que recibe los datos y los muestra al paciente (esta última interacción no se representa con una flecha saliente).

El diagrama muestra la secuencia de pasos necesarios para que un paciente consulte sus turnos, desde la selección de la opción en la interfaz hasta la recuperación y presentación de la información.


* Diagrama de Secuencia - Registrar Nuevo Paciente 

![DDS-RNP](/imagenesDiagramasDeSecuencia/diagramadesecuencia5RegistrarNuevoPaciente.png)

[Enlace a la imagen de Diagrama de Secuencia - Registrar Nuevo Paciente](https://1drv.ms/i/c/f2bf844ed8279638/EbhKyaddW_pHlvfsSJgGpZ0BViyVYuIjVGo3cZ76vy26wg?e=oilhWx)

# Descripción del Diagrama de Secuencia: Registrar Nuevo Paciente

Este diagrama de secuencia ilustra el flujo de interacciones entre diferentes participantes del sistema para el caso de uso "Registrar Nuevo Paciente".

El proceso comienza cuando el **\_01\_Paciente** interactúa con la **\_02\_Interfaz del Sistema** para registrar un nuevo paciente.  El **\_01\_Paciente** envía los "Ingresar Datos" del paciente, que incluyen Nombre, Fecha de Nacimiento, Documento, etc., a la **\_02\_Interfaz del Sistema**.

La **\_02\_Interfaz del Sistema** recibe estos datos y envía un mensaje "registrarPaciente(Nombre=Juan Pérez, FechaNac=1980-05-05, Documento=12345678, ...)" al **\_03\_Sistema** para iniciar el proceso de registro.

El **\_03\_Sistema** recibe estos datos y a su vez, realiza una serie de operaciones. Primero, envía un mensaje "Verificar Documento Único (Documento=12345678)" a la **\_04\_Base de datos (de Pacientes)** para asegurar que no exista otro paciente con el mismo documento.

La **\_04\_Base de datos (de Pacientes)** responde con un mensaje "Documento Único" o "Documento Existente" al **\_03\_Sistema**, indicando el resultado de la verificación.  En este diagrama, se asume que el documento es único para continuar con el flujo de registro.

Si el documento es único, el **\_03\_Sistema** procede a guardar la información del paciente. Envía un mensaje "Guardar Paciente (ID=PAC-789, Nombre=Juan Pérez, ...)" a la **\_04\_Base de datos (de Pacientes)**.

La **\_04\_Base de datos (de Pacientes)** confirma la operación enviando un mensaje "Registro Guardado" al **\_03\_Sistema**.

Finalmente, el **\_03\_Sistema** envía un mensaje "confirmacionRegistro(ID=PAC-789)" a la **\_02\_Interfaz del Sistema**, que contiene el ID único del paciente registrado. La **\_02\_Interfaz del Sistema** recibe esta confirmación y la muestra al paciente (esta última interacción no se representa con una flecha saliente).

El diagrama ilustra la secuencia de pasos desde el ingreso de datos del paciente hasta la confirmación del registro, incluyendo la verificación de unicidad y el almacenamiento en la base de datos.