# Diagrama de Secuencias

* Diagrama de Secuencia - Asignar Turno 

![Diagrama de Secuencia - ConsultarAgendaProfesional](/imagenesDiagramasDeSecuencia/1.AsignarTurno.png)

[Enlace a la imagen de Diagrama de Secuencia - ConsultarAgendaProfesional ](https://1drv.ms/i/c/f2bf844ed8279638/EeUcEgioszZIp858UsEsuGwBtUhDBTmDgRHLfKFdWaOdTw?e=wUjlPe)

# Descripción del Diagrama de Secuencia: Consulta Turnos Paciente
Este diagrama de secuencia describe el proceso de consulta de un turno existente. A continuación, se detalla paso a paso lo que ocurre:

:Paciente solicita una consulta de turno: El proceso inicia cuando un actor o sistema representado como :Paciente envía un mensaje solicitarConsultaTurno(idTurno: String) a la :InterfazUsuario. Este mensaje lleva como parámetro el ID del turno que se desea consultar.

:InterfazUsuario consulta el turno: La :InterfazUsuario recibe la solicitud y, a su vez, envía un mensaje ConsultarTurno(idTurno: String) al objeto :AgendarTurnos. Esto indica que la interfaz de usuario delega la lógica de negocio para consultar el turno a la clase o módulo AgendarTurnos.

:AgendarTurnos obtiene el turno del repositorio: El objeto :AgendarTurnos necesita recuperar la información del turno. Para ello, envía un mensaje obtenerTurnoPorId(idTurno: String) al :ITurnoRepository. Este último representa una interfaz o abstracción para acceder a los datos de los turnos (probablemente una base de datos o un servicio de almacenamiento).

:ITurnoRepository retorna el turno: El :ITurnoRepository procesa la solicitud y, una vez que encuentra el turno correspondiente al idTurno proporcionado, envía un mensaje de retorno return turno: Turno de vuelta a :AgendarTurnos. Este mensaje contiene el objeto Turno con todos sus detalles.

:AgendarTurnos muestra el detalle del turno: Una vez que :AgendarTurnos ha recibido el objeto Turno del repositorio, envía un mensaje mostrarDetalleTurno(turno: Turno) a la :InterfazUsuario. Esto indica que AgendarTurnos le pasa la información del turno a la interfaz para que esta lo presente al usuario.

Fin de la interacción:

La :InterfazUsuario muestra los detalles del turno al :Paciente.
La línea de vida de :Paciente termina, indicando que su interacción directa con el sistema ha concluido para esta operación.
La línea de vida de :AgendarTurnos y :ITurnoRepository también terminan, indicando que sus responsabilidades en esta secuencia han finalizado.
Finalmente, la línea de vida de :InterfazUsuario también termina, lo que sugiere que la consulta del turno ha sido completada y presentada al usuario.


* Diagrama de Secuencia - Solicitar Turno 

![DDS-ST](/imagenesDiagramasDeSecuencia/3.SolicitarTurno.png)

[Enlace a la imagen de Diagrama de Secuencia - Solicitar Turno](https://1drv.ms/i/c/f2bf844ed8279638/EVXaCNQ3yXJNvkoPY2t_E3IBVXk28l0qzU75VnFaOdq7qA?e=IUXRo8)

# Descripción del Diagrama de Secuencia: Solicitar Turno

Este diagrama de secuencia ilustra el proceso de "Solicitar Turno" en un sistema. A continuación, se describe paso a paso lo que sucede:

:Paciente inicia la solicitud de turno: El proceso comienza cuando el actor o sistema :Paciente envía el mensaje iniciarSolicitudTurno() a la :InterfazUsuario. Esto indica que el paciente desea comenzar el proceso para pedir un turno.

:InterfazUsuario solicita criterios de turno: La :InterfazUsuario responde al paciente enviándole el mensaje solicitarCriteriosTurno(profesional: String, fecha: Date, hora: Time). Esto le pide al paciente que ingrese la información necesaria para el turno, como el profesional deseado, la fecha y la hora.

:Paciente ingresa datos del turno: El :Paciente proporciona la información solicitada a través del mensaje ingresarDatosTurno(idProfesional: String, fecha: Date, hora: Time) a la :InterfazUsuario.

:InterfazUsuario solicita registrar el turno: Con los datos proporcionados por el paciente, la :InterfazUsuario envía el mensaje registrarTurno(idPaciente: String, idProfesional: String, fecha: Date, hora: Time) al objeto :AgendarTurnos. Esto delega la responsabilidad de registrar el turno a la clase o módulo AgendarTurnos.

:AgendarTurnos verifica la disponibilidad del profesional: Antes de crear el turno, :AgendarTurnos necesita saber si el profesional está disponible. Para ello, envía el mensaje consultarDisponibilidad(idProfesional: String, fecha: Date, hora: Time) al objeto :ProfesionalDeSalud. Este último es responsable de gestionar la disponibilidad de los profesionales.

:ProfesionalDeSalud retorna la disponibilidad: El objeto :ProfesionalDeSalud verifica su disponibilidad y retorna el resultado a :AgendarTurnos a través del mensaje return estaDisponible: Boolean.

:AgendarTurnos crea el turno (si está disponible):

Si estaDisponible es verdadero: :AgendarTurnos procede a crear una nueva instancia del objeto Turno. Esto se representa con el mensaje crear(idPaciente: String, idProfesional: String, fecha: Date, hora: Time) enviado al objeto :Turno.
El objeto :Turno recién creado retorna una instancia de sí mismo (return nuevoTurno: Turno) a :AgendarTurnos.
:AgendarTurnos guarda el turno: Una vez que el nuevoTurno ha sido creado, :AgendarTurnos envía el mensaje guardar(nuevoTurno: Turno) al :ITurnoRepository. Este repositorio es la interfaz para persistir los datos del turno (por ejemplo, en una base de datos).

:ITurnoRepository retorna la confirmación de guardado: El :ITurnoRepository guarda el turno y retorna un booleano (return turnoGuardado: Boolean) a :AgendarTurnos indicando si la operación fue exitosa.

:AgendarTurnos notifica el turno reservado: Asumiendo que el turno fue guardado exitosamente, :AgendarTurnos envía el mensaje notificarTurnoReservado(idTurno: String) a la :InterfazUsuario. Esto informa a la interfaz que el turno ha sido confirmado.

:InterfazUsuario muestra la confirmación al paciente: Finalmente, la :InterfazUsuario muestra la confirmación al :Paciente a través del mensaje mostrarConfirmacionTurno(idTurno: String).

Fin de la interacción: Las líneas de vida de todos los objetos (Paciente, InterfazUsuario, AgendarTurnos, Turno, ProfesionalDeSalud, ITurnoRepository) terminan, indicando que la secuencia ha finalizado.


* Diagrama de Secuencia - Cancelar Turno 

![DDS-AT](/imagenesDiagramasDeSecuencia/4.CancelarTurno.png)

[Enlace a la imagen de Diagrama de Secuencia - Solicitar Turno](https://1drv.ms/i/c/f2bf844ed8279638/EVXaCNQ3yXJNvkoPY2t_E3IBVXk28l0qzU75VnFaOdq7qA?e=KCWIiu)

# Descripción del Diagrama de Secuencia: Asignar Turno

Este diagrama de secuencia describe el proceso de "Cancelar Turno" en un sistema. A continuación, se detalla paso a paso lo que ocurre:

:Paciente inicia la cancelación del turno: El proceso comienza cuando el actor o sistema :Paciente envía el mensaje iniciarCancelacionTurno() a la :InterfazUsuario. Esto indica que el paciente desea comenzar el proceso para cancelar un turno.

:InterfazUsuario solicita el ID del turno: La :InterfazUsuario responde al paciente pidiéndole que proporcione el ID del turno a cancelar a través del mensaje solicitarIdTurno().

:Paciente ingresa el ID del turno: El :Paciente proporciona el ID del turno que desea cancelar enviando el mensaje ingresarIdTurno(idTurno: String) a la :InterfazUsuario.

:InterfazUsuario solicita cancelar el turno: Con el ID del turno proporcionado, la :InterfazUsuario envía el mensaje cancelarTurno(idTurno: String) al objeto :AgendarTurnos. Esto delega la responsabilidad de la cancelación del turno a la clase o módulo AgendarTurnos.

:AgendarTurnos obtiene el turno del repositorio: Para poder actualizar el estado del turno, :AgendarTurnos primero necesita obtener la información actual del turno. Para ello, envía el mensaje obtenerTurno(idTurno: String) al :ITurnoRepository.

:ITurnoRepository retorna el turno: El :ITurnoRepository busca el turno con el idTurno proporcionado y retorna el objeto Turno completo a :AgendarTurnos a través del mensaje return turno: Turno.

:AgendarTurnos actualiza el estado del turno: Una vez que :AgendarTurnos tiene el objeto Turno, envía un mensaje actualizarEstadoTurno(turno: Turno, estado: String = "cancelado") al propio objeto :Turno. Esto indica que el objeto Turno es responsable de cambiar su propio estado a "cancelado".

:Turno retorna el turno actualizado: El objeto :Turno actualiza su estado interno y retorna la instancia del turno con el estado modificado (return turnoActualizado: Turno) de vuelta a :AgendarTurnos.

:AgendarTurnos guarda el turno actualizado: Para persistir el cambio de estado, :AgendarTurnos envía el mensaje guardarTurno(turno: Turno) al :ITurnoRepository. Esto le indica al repositorio que actualice la información del turno en el almacenamiento.

:ITurnoRepository retorna la confirmación de guardado: El :ITurnoRepository guarda el turno actualizado y retorna un booleano (return turnoGuardado: Boolean) a :AgendarTurnos indicando si la operación de guardado fue exitosa.

:AgendarTurnos notifica la cancelación exitosa: Asumiendo que el turno fue guardado con el estado "cancelado", :AgendarTurnos envía el mensaje notificarCancelacionExitosa(idTurno: String) a la :InterfazUsuario. Esto informa a la interfaz que la cancelación ha sido confirmada.

:InterfazUsuario muestra la confirmación al paciente: Finalmente, la :InterfazUsuario muestra la confirmación de la cancelación al :Paciente a través del mensaje mostrarConfirmacionCancelacion(idTurno: String).

Fin de la interacción: Las líneas de vida de todos los objetos involucrados en la secuencia terminan, indicando que el proceso de cancelación del turno ha finalizado.

* Diagrama de Secuencia - Consultar disponibilidad profesional

![DDS-CTP](/imagenesDiagramasDeSecuencia/2.ConsultarDisponibilidadProfesional.png)

[Enlace a la imagen de Diagrama de Secuencia - Consultar Turno Paciente](https://1drv.ms/i/c/f2bf844ed8279638/Ec5weXQjHuFNj7IeL0FqHtEBEXPe2qd4mLWGxB71gQi9MQ?e=vb9Fy8)

# Descripción del Diagrama de Secuencia: Consultar Turno Paciente

Este diagrama de secuencia describe el proceso de "Consultar Disponibilidad Profesional". A continuación, se detalla paso a paso lo que ocurre:

:Administrativo inicia la consulta de disponibilidad: El proceso comienza cuando el actor o sistema :Administrativo envía el mensaje iniciarConsultaDisponibilidad() a la :InterfazUsuario. Esto indica que un administrativo desea consultar la disponibilidad de un profesional.

:InterfazUsuario solicita criterios de disponibilidad: La :InterfazUsuario responde al administrativo enviándole el mensaje solicitarCriteriosDisponibilidad(idProfesional: String, fecha: Date). Esto le pide al administrativo que ingrese el ID del profesional y la fecha para la cual desea consultar la disponibilidad.

:Administrativo ingresa criterios de disponibilidad: El :Administrativo proporciona la información solicitada a través del mensaje ingresarCriteriosDisponibilidad(idProfesional: String, fecha: Date) a la :InterfazUsuario.

:InterfazUsuario consulta la disponibilidad del profesional: Con los datos proporcionados por el administrativo, la :InterfazUsuario envía el mensaje consultarDisponibilidadProfesional(idProfesional: String, fecha: Date) al objeto :AgendarTurnos. Esto delega la responsabilidad de consultar la disponibilidad al módulo AgendarTurnos.

:AgendarTurnos obtiene los turnos ocupados: Para determinar la disponibilidad, :AgendarTurnos primero necesita saber qué turnos ya están ocupados para el profesional y la fecha dados. Para ello, envía el mensaje obtenerTurnosOcupados(idProfesional: String, fecha: Date) al :ITurnoRepository. Este repositorio es la fuente de información sobre los turnos existentes.

:ITurnoRepository retorna la lista de turnos ocupados: El :ITurnoRepository consulta sus datos y retorna una lista de los turnos ya ocupados para el profesional y la fecha especificados (return listaTurnosOcupados: List<Turno>) a :AgendarTurnos.

:AgendarTurnos obtiene los horarios laborales del profesional: Además de los turnos ocupados, :AgendarTurnos necesita conocer el horario laboral general del profesional para esa fecha. Para ello, envía el mensaje obtenerHorariosLaborales(idProfesional: String, fecha: Date) al objeto :ProfesionalDeSalud.

:ProfesionalDeSalud retorna los horarios laborales: El objeto :ProfesionalDeSalud (que gestiona la información de los profesionales) retorna la lista de los horarios laborales del profesional para la fecha consultada (return horariosLaborales: List<TimeRange>) a :AgendarTurnos.

:AgendarTurnos calcula la disponibilidad: Con la lista de horariosLaborales y turnosOcupados, :AgendarTurnos realiza una operación interna (representada por el mensaje a sí mismo) calcularDisponibilidad(horariosLaborales, turnosOcupados). En este paso, se resta los turnos ocupados de los horarios laborales para determinar los bloques de tiempo disponibles.

:AgendarTurnos retorna la disponibilidad calculada: Después de calcular la disponibilidad, :AgendarTurnos envía el mensaje return disponibilidad: List<TimeRange> de vuelta a la :InterfazUsuario. Esta lista de TimeRange representa los intervalos de tiempo en los que el profesional está disponible.

:InterfazUsuario muestra la disponibilidad al usuario: La :InterfazUsuario recibe la información de disponibilidad y la muestra al :Administrativo a través del mensaje mostrarDisponibilidad(disponibilidad: List<TimeRange>).

Fin de la interacción: Las líneas de vida de todos los objetos involucrados en la secuencia terminan, indicando que el proceso de consulta de disponibilidad ha finalizado.


* Diagrama de Secuencia - Registrar Paciente 

![DDS-RNP](/imagenesDiagramasDeSecuencia/5.RegistrarPaciente.png)

[Enlace a la imagen de Diagrama de Secuencia - Registrar Nuevo Paciente](https://1drv.ms/i/c/f2bf844ed8279638/EVFmJwQgarxHnKzGF7Cc1wIBcXJtTqoJg6rBxyMsuTXtow?e=YGKLd5)

# Descripción del Diagrama de Secuencia: Registrar Nuevo Paciente

Este diagrama de secuencia describe el proceso de "Registrar Paciente" en un sistema. A continuación, se detalla paso a paso lo que ocurre:

:Administrativo inicia el registro de paciente: El proceso comienza cuando el actor o sistema :Administrativo envía el mensaje iniciarRegistroPaciente() a la :InterfazUsuario. Esto indica que un administrativo desea comenzar el proceso para registrar un nuevo paciente.

:InterfazUsuario solicita los datos del paciente: La :InterfazUsuario responde al administrativo pidiéndole que proporcione los datos necesarios para el registro a través del mensaje solicitarDatosPaciente(nombre: String, apellido: String, DNI: String, fechaNac: Date, telefono: String, email: String).

:Administrativo ingresa los datos del paciente: El :Administrativo proporciona la información solicitada (nombre, apellido, DNI, fecha de nacimiento, teléfono, email) enviando el mensaje ingresarDatosPaciente(nombre: String, apellido: String, DNI: String, fechaNac: Date, telefono: String, email) a la :InterfazUsuario.

:InterfazUsuario registra al paciente: Con los datos proporcionados, la :InterfazUsuario envía el mensaje registrarPaciente(datosPaciente) al objeto :GestorPacientes. Esto delega la responsabilidad de registrar al paciente a la clase o módulo GestorPacientes. El parámetro datosPaciente probablemente es un objeto que encapsula toda la información del paciente.

:GestorPacientes verifica si el paciente ya existe: Antes de crear un nuevo paciente, el :GestorPacientes necesita verificar si ya existe un paciente con el mismo DNI para evitar duplicados. Para ello, envía el mensaje existePaciente(DNI: String) al :IPacienteRepository.

:IPacienteRepository retorna si el paciente existe: El :IPacienteRepository consulta sus datos y retorna un booleano (return existe: Boolean) a :GestorPacientes indicando si ya existe un paciente con ese DNI.

:GestorPacientes crea un nuevo paciente (si no existe):

Si existe es falso (el paciente no existe): :GestorPacientes procede a crear una nueva instancia del objeto Paciente. Esto se representa con el mensaje crear(nombre: String, apellido: DNI, fechaNac: Date, telefono: String, email) enviado al objeto :Paciente.
El objeto :Paciente recién creado retorna una instancia de sí mismo (return nuevoPaciente: Paciente) a :GestorPacientes.
:GestorPacientes guarda el nuevo paciente: Una vez que el nuevoPaciente ha sido creado, :GestorPacientes envía el mensaje guardar(nuevoPaciente: Paciente) al :IPacienteRepository. Este repositorio es la interfaz para persistir los datos del paciente (por ejemplo, en una base de datos).

:IPacienteRepository retorna la confirmación de guardado: El :IPacienteRepository guarda el paciente y retorna un booleano (return pacienteGuardado: Boolean) a :GestorPacientes indicando si la operación fue exitosa.

:GestorPacientes notifica el registro exitoso: Asumiendo que el paciente fue guardado exitosamente, :GestorPacientes envía el mensaje notificarRegistroExitoso(idPaciente: String) a la :InterfazUsuario. Esto informa a la interfaz que el registro ha sido completado.

:InterfazUsuario muestra la confirmación al administrativo: Finalmente, la :InterfazUsuario muestra la confirmación del registro al :Administrativo a través del mensaje mostrarConfirmacionRegistro(idPaciente: String).

Fin de la interacción: Las líneas de vida de todos los objetos involucrados en la secuencia terminan, indicando que el proceso de registro del paciente ha finalizado.