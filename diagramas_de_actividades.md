# Diagrama de Actividades

* Diagrama De Actividad - Asignar Turno / Caso de Uso 1

![Diagrama De Actividad - Asignar Turno / Caso de Uso 1 que se representa en diagrama de actividad](/imagenesdediagramasdeactividades/1.AsignarTurno.png)

[Enlace al Caso de Uso 1 - AsignarTurno/Caso de Uso 1 que se representa en diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/EYF7ieHJqxlAhuNC6G5C028B5LMjQAVB0doubEvjT3m4Cg?e=Bti6tv)

# Descripción del Diagrama de Actividades: Asignar Turno

Este es un diagrama de actividades que describe el proceso de "Asignar Turno" en un sistema, involucrando al System (sistema), Paciente y Administrativo/Recepcionista.

A continuación, se describe paso a paso la secuencia de actividades:

Inicio del proceso (System):

El proceso comienza con la actividad Asignar Turno en el carril del System.
Solicitud de Turno (Paciente):

Paralelamente al inicio del proceso de asignación, el Paciente realiza una Solicitud de Turno. Esta es una actividad independiente del paciente que precede al proceso de asignación en el sistema.
Verificar turnos existentes del paciente (System):

Una vez que se inicia la asignación de turno, el System procede a Verificar turnos existentes del paciente.
Seleccionar Paciente (Administrativo/Recepcionista):

Simultáneamente, el Administrativo/Recepcionista inicia su parte del proceso con la actividad Seleccionar Paciente.
Decisión: ¿Paciente existente? (Administrativo/Recepcionista):

Después de Seleccionar Paciente, hay un punto de decisión en el carril del Administrativo/Recepcionista:
Si 'no' (el paciente no existe): El Administrativo/Recepcionista debe Registrar Nuevo Paciente. Una vez registrado, el flujo vuelve a Seleccionar Paciente (o en un flujo más completo, podría ir directamente a Seleccionar Profesional si el registro implica la selección inmediata).
Si 'sí' (el paciente existe): El flujo continúa hacia Seleccionar Profesional.
Validar Disponibilidad (System):

Desde la actividad Verificar turnos existentes del paciente (en el carril del System), el flujo se dirige a un punto de decisión. A partir de aquí, el flujo puede ir a Validar Disponibilidad o a Informar Turno Existente.
Este punto de decisión está sincronizado con el flujo del Administrativo/Recepcionista que viene de Seleccionar Profesional. Es decir, la validación de disponibilidad requiere que ya se haya seleccionado un profesional.
Decisión: ¿Turno existente o disponibilidad? (Sincronización System y Administrativo/Recepcionista):

Hay un punto de decisión que recibe información tanto de Verificar turnos existentes del paciente como de la parte de Validar Disponibilidad.
Si 'sí' (el paciente ya tiene un turno existente que cumple): El sistema pasa a Informar Turno Existente (en el carril del Administrativo/Recepcionista). Después de informar, el proceso culmina para este caso en Notificar Turno.
Si 'no' (no hay turno existente o el que hay no es válido, y la disponibilidad no es inmediata o necesita más datos): El flujo continúa hacia Seleccionar Fecha/Hora.
Seleccionar Profesional (Administrativo/Recepcionista):

Después de Seleccionar Paciente (y si el paciente existe), el Administrativo/Recepcionista procede a Seleccionar Profesional.
Seleccionar Fecha/Hora (Administrativo/Recepcionista):

Una vez que el profesional ha sido seleccionado (y si no se informó un turno existente que cumpla), el Administrativo/Recepcionista realiza la actividad Seleccionar Fecha/Hora.
Decisión: ¿Disponibilidad? (System):

Después de Validar Disponibilidad (en el carril del System), hay un punto de decisión:
Si 'no' (no hay disponibilidad): El flujo regresa a Seleccionar Fecha/Hora para que el administrativo elija otra fecha u hora.
Si 'sí' (hay disponibilidad): El flujo continúa hacia Ingresar Motivo.
Ingresar Motivo (Administrativo/Recepcionista):

Si hay disponibilidad, el Administrativo/Recepcionista realiza la actividad Ingresar Motivo (para el turno).
Confirmar Asignación (Administrativo/Recepcionista):

Después de Ingresar Motivo, el Administrativo/Recepcionista realiza la actividad Confirmar Asignación.
Notificar Turno (System):

Tras la Confirmar Asignación por parte del administrativo, o si se detectó un Informar Turno Existente, el System realiza la actividad final Notificar Turno.
Fin del Proceso (System):

Finalmente, el proceso termina con el nodo de finalización de actividad, después de Notificar Turno.
En resumen, este diagrama muestra un flujo que involucra la verificación de la existencia de un paciente y sus turnos, la selección de un profesional y una fecha/hora, la validación de la disponibilidad (posiblemente con iteración si no hay disponibilidad), y la eventual notificación de la asignación del turno.

* Diagrama de Actividad - Cancelar Turno

![Diagrama de Actividad - Cancelar Turno / Caso de Uso 2 que se representa en diagrama de actividad](/imagenesdediagramasdeactividades/2.CancelarTurno.png)

[Enlace al Caso de Uso 2 - Cancelar Turno / Caso de uso 2 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/EZxxlahy9fxDlZmDzYJDlg4B1MbzfKukvZU0Hm8H0CstUg?e=KlHJgT)

# Descripción del Diagrama de Actividades: Cancelar Turno

Este es un diagrama de actividades que describe el proceso de "Cancelar Turno", involucrando al System (sistema), Paciente y Administrativo/Recepcionista.

A continuación, se describe paso a paso la secuencia de actividades:

Inicio del proceso (Paciente y Administrativo/Recepcionista):

El proceso puede iniciarse de dos maneras:
Desde el carril del Paciente, directamente con la actividad Cancelar Turno (representada por el nodo de inicio y la actividad).
Desde el carril del Administrativo/Recepcionista, con la actividad Iniciando Cancelación.
Buscar Turno (System):

Independientemente de cómo se inicie la cancelación, la primera acción del System es Buscar Turno. Esto implica localizar el turno que se desea cancelar.
Decisión: ¿Turno encontrado? (System):

Después de Buscar Turno, hay un punto de decisión en el carril del System:
Si 'no' (el turno no se encuentra): El flujo se dirige a Informar Turno No Encontrado en el carril del Administrativo/Recepcionista. Después de informar, el proceso termina para este camino.
Si 'sí' (el turno se encuentra): El flujo continúa hacia Verificar Elegibilidad Para Cancelar.
Verificar Elegibilidad Para Cancelar (System):

Una vez que el turno es encontrado, el System procede a Verificar Elegibilidad Para Cancelar. Esto puede incluir reglas de negocio como plazos de cancelación, estado actual del turno, etc.
Decisión: ¿Elegible para cancelar? (System):

Después de Verificar Elegibilidad Para Cancelar, hay otro punto de decisión en el carril del System:
Si 'no' (no es elegible para cancelar): El flujo se dirige a No elegibilidad para cancelar (en el carril del Paciente o una notificación interna). Posteriormente, el Paciente Recibe Notificación de Cancelación (en este caso, de no elegibilidad). El proceso termina.
Si 'sí' (es elegible para cancelar): El flujo continúa hacia Actualizar Estado del Turno Cancelado.
Ingresar Motivo de Cancelación (Administrativo/Recepcionista):

Si el proceso fue iniciado por el Administrativo/Recepcionista (Iniciando Cancelación), y el turno fue encontrado y es elegible, el Administrativo/Recepcionista procede a Ingresar Motivo de Cancelación.
Nota: El diagrama sugiere que esta actividad se ejecuta en paralelo o después de Buscar Turno y antes de la Confirmar Cancelación, y que su ejecución no depende de la "elegibilidad" de forma secuencial en este diagrama, aunque lógicamente podría estar ligada.
Confirmar Cancelación (Administrativo/Recepcionista):

Después de Ingresar Motivo de Cancelación, el Administrativo/Recepcionista realiza la actividad Confirmar Cancelación.
Actualizar Estado del Turno Cancelado (System):

Si el turno es elegible para cancelar, el System procede a Actualizar Estado del Turno Cancelado. Esta actividad representa la persistencia del cambio de estado del turno en el sistema.
Notificar Cancelación (System):

Después de Actualizar Estado del Turno Cancelado, el System realiza la actividad Notificar Cancelación.
Recibir Notificación de Cancelación (Paciente):

Tanto si la cancelación fue exitosa (Notificar Cancelación) como si el turno no era elegible (No elegibilidad para cancelar), el Paciente finalmente Recibe Notificación de Cancelación.
Fin del Proceso:

El proceso culmina en el nodo de finalización, al cual se llega desde Informar Turno No Encontrado o desde Recibir Notificación de Cancelación (después de una cancelación exitosa o una no elegibilidad).
En resumen, el diagrama muestra cómo el sistema busca un turno, verifica si puede ser cancelado y si lo es, actualiza su estado y notifica al paciente. También contempla escenarios donde el turno no se encuentra o no es elegible para cancelación. La intervención del Administrativo/Recepcionista añade la posibilidad de ingresar un motivo y confirmar la acción.

* Diagrama de Actividad - Consultar Historial Paciente

![Diagrama de Actividad - Consultar Historial Paciente / Caso de uso 3 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/3.ConsultarHistorial.png)

[Enlace al Caso de Uso 3 - Consultar Historial Paciente / Caso de uso 3 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/ER2YVb8RU2dMm1jIbEsHKIYBNuYmbQEaq5NXdrsyoPokJg?e=pgDyC3)

# Descripción del Diagrama de Actividades: Consultar Historial del Paciente

Este es un diagrama de actividades que describe el proceso de "Consultar Historial" de un paciente, involucrando al System (sistema), Paciente y Administrativo/Recepcionista.

A continuación, se describe paso a paso la secuencia de actividades:

Inicio del proceso (Paciente y Administrativo/Recepcionista):

El proceso puede ser iniciado por dos actores:
Desde el carril del Paciente, directamente con la actividad Consultar Historial (representada por el nodo de inicio y la actividad).
Desde el carril del Administrativo/Recepcionista, también con la actividad Consultar Historial (representada por el nodo de inicio y la actividad).
Recibir Solicitud De Consulta de Historial (System):

Independientemente de quién inicie la consulta, el System recibe la Solicitud De Consulta de Historial.
Buscar Paciente (System):

Una vez recibida la solicitud, el System procede a Buscar Paciente. Esto implica localizar al paciente cuyo historial se desea consultar.
Decisión: ¿Paciente encontrado? (System):

Después de Buscar Paciente, hay un punto de decisión en el carril del System:
Si 'no' (el paciente no se encuentra): El flujo se dirige a Informar Paciente no Encontrado en el carril del System. Desde aquí, el proceso termina, indicando que no se puede continuar sin el paciente.
Si 'sí' (el paciente se encuentra): El flujo continúa hacia Solicitar Rango de Fechas.
Solicitar Rango de Fechas (Administrativo/Recepcionista):

Si el paciente es encontrado, la actividad Solicitar Rango de Fechas se activa en el carril del Administrativo/Recepcionista. Esto sugiere que, para la consulta del historial, se necesita un rango de fechas específico.
Validar Rango de Fechas (System):

Una vez que se ha solicitado un rango de fechas (aunque el diagrama no muestra explícitamente el ingreso), el System realiza la actividad Validar Rango de Fechas. Esto asegura que las fechas proporcionadas sean válidas (ej., fecha de inicio anterior a la de fin, dentro de límites razonables, etc.).
Decisión: ¿Rango de fechas válido? (System):

Después de Validar Rango de Fechas, hay un punto de decisión en el carril del System:
Si 'No' (el rango de fechas no es válido): El flujo se dirige a Informar de Fechas No Válido en el carril del System. Desde aquí, el flujo regresa a Validar Rango de Fechas o a un punto anterior para permitir corregir el rango de fechas (el diagrama muestra un ciclo directo a Validar Rango de Fechas).
Si 'Sí' (el rango de fechas es válido): El flujo continúa hacia Consultar Historial Del Paciente.
Consultar Historial Del Paciente (System):

Si el paciente es encontrado y el rango de fechas es válido, el System procede a Consultar Historial Del Paciente. Esta actividad implica la recuperación de los datos del historial médico o de interacciones del paciente dentro del rango de fechas especificado.
Formatear Historial Para Mostrar (System):

Una vez consultado el historial, el System realiza la actividad Formatear Historial Para Mostrar. Esto prepara los datos recuperados en un formato legible y presentable para el usuario.
Mostrar Historial (Administrativo/Recepcionista):

Finalmente, el Administrativo/Recepcionista realiza la actividad Mostrar Historial. Esta actividad representa la visualización de la información del historial formateado al usuario.
Fin del Proceso (Administrativo/Recepcionista):

El proceso culmina en el nodo de finalización, después de Mostrar Historial.
En resumen, este diagrama ilustra un proceso de consulta de historial que comienza con una solicitud, implica la búsqueda y validación de la existencia del paciente, la solicitud y validación de un rango de fechas, la consulta y formateo del historial por parte del sistema, y finalmente la visualización de este al usuario. Los caminos alternativos manejan casos de paciente no encontrado o rango de fechas inválido.

* Diagrama de Actividad - Consultar Disponibilidad Profesional

![Diagrama de Actividad - Consultar Disponibilidad Profesional / Caso de Uso 4 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/4.ConsultarDisponibilidadProfesional.png)

[Enlace al Caso de Uso 4 - Consultar Disponibilidad Profesional / Caso de Uso 4 que representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/Edi8WBD7fx1LrWe1s8oorkQBFjFxpAluixJomLCICs_hNw?e=QUJjcE)

# Descripción del Diagrama de Actividades: Consultar Historial

Este es un diagrama de actividades que describe el proceso de "Consultar Disponibilidad Profesional", involucrando a un Paciente, un Recepcionista/Administrativo y el System (sistema).

A continuación, se describe paso a paso la secuencia de actividades:

Inicio del proceso (Paciente y Recepcionista/Administrativo):

El proceso puede ser iniciado por dos actores:
Desde el carril del Paciente, directamente con la actividad Solicitar Consulta de Disponibilidad (representada por el nodo de inicio y la actividad).
Desde el carril del Recepcionista/Administrativo, con la actividad Recibir Solicitud de Consulta de Disponibilidad.
Recibir Solicitud de Consulta de Disponibilidad (System):

Independientemente de quién inicie la consulta, el System recibe la Solicitud de Consulta de Disponibilidad.
Buscar Profesional (System):

Una vez recibida la solicitud, el System procede a Buscar Profesional. Esto implica localizar al profesional cuya disponibilidad se desea consultar.
Decisión: ¿Profesional encontrado? (System):

Después de Buscar Profesional, hay un punto de decisión en el carril del System:
Si 'No' (el profesional no se encuentra): El flujo se dirige a un punto de sincronización, y luego al final del proceso, lo que implica que no se puede continuar con la consulta sin un profesional válido.
Si 'Sí' (el profesional se encuentra): El flujo continúa hacia Validar Rango Fechas.
Seleccionar Profesional (Recepcionista/Administrativo):

Desde la actividad Recibir Solicitud de Consulta de Disponibilidad en el carril del Recepcionista/Administrativo, el flujo continúa hacia Seleccionar Profesional.
Ingresar Criterios de Búsqueda (Recepcionista/Administrativo):

Después de Seleccionar Profesional, el Recepcionista/Administrativo realiza la actividad Ingresar Criterios de Búsqueda. Esto podría incluir el nombre del profesional, especialidad, etc.
Seleccionar Rango de Fechas (Recepcionista/Administrativo):

Una vez ingresados los criterios, el Recepcionista/Administrativo procede a Seleccionar Rango de Fechas para la consulta de disponibilidad.
Validar Rango Fechas (System):

El System recibe el rango de fechas (implícitamente desde Seleccionar Rango de Fechas o Ingresar Criterios de Búsqueda) y realiza la actividad Validar Rango Fechas. Esto asegura que las fechas proporcionadas sean válidas.
Decisión: ¿Rango de fechas válido? (System):

Después de Validar Rango Fechas, hay otro punto de decisión en el carril del System:
Si 'No' (el rango de fechas no es válido): El flujo se dirige a Informar Rango de Fechas No Válido en el carril del System. Desde aquí, el flujo regresa al punto de sincronización, lo que sugiere que el proceso termina o se le pide al usuario que ingrese un rango válido nuevamente.
Si 'Sí' (el rango de fechas es válido): El flujo continúa hacia Consultar Agenda del Profesional.
Consultar Agenda del Profesional (System):

Si el profesional es encontrado y el rango de fechas es válido, el System procede a Consultar Agenda del Profesional. Esta actividad implica acceder a los registros de la agenda para esa fecha y profesional.
Identificar Horarios Disponibles (System):

Una vez consultada la agenda, el System realiza la actividad Identificar Horarios Disponibles. Esto implica procesar la agenda para determinar los bloques de tiempo en los que el profesional no tiene compromisos.
Formatear Disponibilidad para Mostrar (System):

Después de identificar los horarios disponibles, el System realiza la actividad Formatear Disponibilidad para Mostrar. Esto prepara los datos en un formato legible para el usuario.
Mostrar Disponibilidad (Recepcionista/Administrativo):

Finalmente, el Recepcionista/Administrativo realiza la actividad Mostrar Disponibilidad. Esta actividad representa la visualización de los horarios disponibles al usuario.
Fin del Proceso:

El proceso culmina en el nodo de finalización, al cual se llega desde Mostrar Disponibilidad o si el Profesional no Encontrado o Informar Rango de Fechas No Válido.
En resumen, este diagrama ilustra un proceso de consulta de disponibilidad que comienza con una solicitud, implica la búsqueda del profesional, el ingreso y validación de criterios y rango de fechas, la consulta de la agenda y la identificación de horarios disponibles por parte del sistema, y finalmente la visualización de esta información al usuario. Los caminos alternativos manejan casos de profesional no encontrado o rango de fechas inválido.

* Diagrama de Actividad - Registrar Profesional de la Salud 

![Diagrama de Actividad - Registrar Profesional de la Salud / Caso de Uso 5 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/5.RegistroProfesionaldeSalud.png)

[Enlace al Caso de Uso 5 - Registrar Profesioanl de la Salud / Caso de Uso 5 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/Ed3Hjl3di59Mqmyq57sQlYEBuwkET-O_KraYF8dhjM2_Eg?e=aVYpxV)

# Descripción del Diagrama de Actividades: Registrar Profesional de la Salud

Este es un diagrama de actividades que describe el proceso de "Registro de Profesional de la Salud", involucrando a un Administrativo/Recepcionista, el Profesional de la Salud y el System (sistema).

A continuación, se describe paso a paso la secuencia de actividades:

Inicio del proceso (Administrativo/Recepcionista y Profesional de la Salud):

El proceso inicia en el carril del Administrativo/Recepcionista con la actividad Recibir Solicitud de Registro.
Simultáneamente, el Profesional de la Salud inicia con la actividad Proporcionar Datos de Registro.
Solicitar Datos al Profesional (Administrativo/Recepcionista):

Después de recibir la solicitud, el Administrativo/Recepcionista solicita los datos necesarios al profesional con la actividad Solicitar Datos al Profesional.
Proporcionar Datos de Registro (Profesional de la Salud):

El Profesional de la Salud proporciona los datos de registro. Esta actividad se conecta con Recibir Datos de Registro en el System.
Ingresar Datos del Profesional (Administrativo/Recepcionista):

Una vez que el Profesional de la Salud ha proporcionado los datos, el Administrativo/Recepcionista procede a Ingresar Datos del Profesional en el sistema.
Especialidades Asociadas (Administrativo/Recepcionista):

Después de ingresar los datos generales, el Administrativo/Recepcionista realiza la actividad Especialidades Asociadas, indicando que se deben ingresar o seleccionar las especialidades del profesional.
Confirmar Datos Ingresados (Administrativo/Recepcionista):

Finalmente, el Administrativo/Recepcionista realiza la actividad Confirmar Datos Ingresados, lo que valida la información antes de enviarla al sistema para su procesamiento.
Recibir Datos de Registro (System):

El System recibe los datos de registro. Esta actividad es el punto de entrada para el procesamiento del sistema.
Validar Datos del Profesional (System):

Una vez recibidos los datos, el System procede a Validar Datos del Profesional. Esto puede incluir la verificación de formato, obligatoriedad de campos, etc.
Decisión: ¿Datos Válidos? (System):

Después de Validar Datos del Profesional, hay un punto de decisión en el carril del System:
Si 'no' (los datos no son válidos): El flujo regresa a Proporcionar Datos de Registro (en el carril del Profesional de la Salud), lo que sugiere que se deben corregir y volver a ingresar los datos.
Si 'sí' (los datos son válidos): El flujo continúa hacia Verificar Existencia Previa del Profesional.
Verificar Existencia Previa del Profesional (System):

Si los datos son válidos, el System procede a Verificar Existencia Previa del Profesional. Esto es para asegurarse de que el profesional no esté ya registrado en el sistema (por ejemplo, verificando su número de identificación).
Decisión: ¿Profesional ya Registrado? (System):

Después de Verificar Existencia Previa del Profesional, hay otro punto de decisión en el carril del System:
Si 'Si' (el profesional ya está registrado): El flujo se dirige a Profesional Ya Registrado (en el carril del System). Desde aquí, el proceso termina, ya que no se puede registrar al mismo profesional dos veces.
Si 'No' (el profesional no está registrado): El flujo continúa hacia Guardar Registro Profesional.
Guardar Registro Profesional (System):

Si el profesional no está registrado, el System procede a Guardar Registro Profesional. Esto implica persistir los datos del nuevo profesional en la base de datos o almacenamiento del sistema.
Asignar Identificador Único (System):

Después de Guardar Registro Profesional, el System realiza la actividad Asignar Identificador Único. Este identificador es crucial para la gestión futura del profesional en el sistema.
Notificar Registro Exitoso (System):

Una vez que el registro ha sido guardado y se ha asignado un identificador, el System realiza la actividad Notificar Registro Exitoso.
Confirmar Registro (Profesional de la Salud):

Paralelamente a la notificación de éxito del sistema, el Profesional de la Salud realiza una Confirmar Registro. Esta es una actividad independiente del profesional, posiblemente de acuse de recibo o de una acción final por su parte.
Fin del Proceso:

El proceso culmina en el nodo de finalización, al cual se llega desde Notificar Registro Exitoso o desde Profesional Ya Registrado.
En resumen, este diagrama ilustra un proceso de registro de un profesional de la salud que involucra la recolección de datos por parte de un administrativo, la validación de esos datos por el sistema, la verificación de duplicados, el guardado del registro y la asignación de un identificador único, culminando con una notificación de éxito o de que el profesional ya estaba registrado.