# Diagrama de Actividades

* Diagrama De Actividad - Asignar Turno / Casp de Uso 1

![Diagrama De Actividad - Asignar Turno / Caso de Uso 1 que se representa en diagrama de actividad](/imagenesdediagramasdeactividades/diagramadeactividades1AsignarTurno.png)

[Enlace al Caso de Uso 1 - AsignarTurno/Caso de Uso 1 que se representa en diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/ERGtplJaVGRLiO7R-Ns_DHMBO4D8ilo_49IJpvnjHs8Fug?e=9MfUfH)

# Descripción del Diagrama de Actividades: Asignar Turno

Este diagrama de actividades describe el proceso dentro del "System" para asignar un turno a un paciente. El flujo comienza con la actividad de "Asignar Turno".

Inicialmente, se debe "Seleccionar paciente". A continuación, el sistema realiza una verificación condicional: "¿El paciente existe y está activo en el sistema?".

* **Si** el paciente existe y está activo, el sistema procede a "Verificar Turnos Existentes del Paciente". Luego, se realiza otra verificación condicional: "¿El paciente ya tiene un turno asignado para esta fecha/hora?".
    * **Si** el paciente ya tiene un turno asignado, el flujo finaliza.
    * **No**, el flujo continúa.
* **No** (si el paciente no existe o no está activo), el flujo se dirige directamente a la actividad de "Seleccionar Profesional".

Después de "Seleccionar Profesional", se debe "Seleccionar Fecha/Hora" para el turno. El sistema entonces procede a "Validar disponibilidad". Una verificación condicional "¿Disponibilidad Confirmada?" sigue a esta actividad.

* **Si** la disponibilidad es confirmada, se debe "Ingresar Motivo" para la asignación del turno. Luego, se realiza la "Confirmar Asignación". Finalmente, se "Notificar Turno". Después de la notificación, el flujo finaliza.
* **No** (si la disponibilidad no es confirmada), el flujo regresa a la actividad de "Seleccionar Fecha/Hora" para intentar una nueva selección.

El diagrama finaliza con un nodo de fin, alcanzable tanto después de la notificación exitosa del turno como si el paciente ya tenía un turno asignado para la misma fecha y hora.

* Diagrama de Actividad - Cancelar Turno

![Diagrama de Actividad - Cancelar Turno / Caso de Uso 2 que se representa en diagrama de actividad](/imagenesdediagramasdeactividades/diagramadeactividades2CancelarTurno.png)

[Enlace al Caso de Uso 2 - Cancelar Turno / Caso de uso 2 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/EanDGSkpshZGucqGGBm9DtcBJ9Z7izzn7NTfaUOFtGocJw?e=vdGSDy)

# Descripción del Diagrama de Actividades: Cancelar Turno

Este diagrama de actividades describe el proceso dentro del "System" para cancelar un turno. El flujo comienza con dos actividades paralelas: "Cancelar Turno" y "Buscar Turno".

Después de estas actividades iniciales, el sistema realiza una verificación condicional: "¿Turno Encontrado?".

* **Si** se encuentra el turno, el flujo continúa hacia la actividad de "Verificar Elegibilidad". A continuación, se realiza otra verificación condicional: "¿Es Elegible para Cancelar?".
    * **Si** el turno es elegible para cancelar, el flujo se dirige a "Ingresar Motivo de Cancelación", seguido de "Confirmar Cancelación" y finalmente "Notificar Cancelación". Después de la notificación, el flujo finaliza.
    * **No** (si el turno no es elegible para cancelar), el flujo finaliza.
* **No** (si no se encuentra el turno), el flujo finaliza.

El diagrama finaliza en un nodo de fin, alcanzable en los casos en que el turno se cancela y se notifica, cuando el turno encontrado no es elegible para cancelar, o cuando no se encuentra ningún turno.

* Diagrama de Actividad - Consultar Historial Paciente

![Diagrama de Actividad - Consultar Historial Paciente / Caso de uso 3 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/diagramadeactividades3ConsultarHistorialdelPaciente.png)

[Enlace al Caso de Uso 3 - Consultar Historial Paciente / Caso de uso 3 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/ERmfd4_ftHxEj0njAOHi7aUBGkwlFFSML6zb67K8J7Cn2w?e=dxCQpk)

# Descripción del Diagrama de Actividades: Consultar Historial del Paciente

Este diagrama de actividades describe el proceso dentro del "System" para que un usuario consulte el historial de un paciente. El flujo comienza con la actividad "Consultar Historial del Paciente", seguida de "Buscar Paciente".

A continuación, el sistema realiza una verificación condicional: "¿Paciente Encontrado?".

* **Si** se encuentra el paciente, el flujo se divide. Una rama va a "Seleccionar Rango de Fechas". Después de seleccionar el rango, se verifica condicionalmente si "¿Rango de Fechas Válido?".
    * **Si** el rango de fechas es válido, el sistema procede a "Mostrar Historial". Después de mostrar el historial, el flujo finaliza.
    * **No** (si el rango de fechas no es válido), el flujo finaliza.
* **No** (si no se encuentra el paciente), el flujo finaliza.

El diagrama finaliza en un nodo de fin, alcanzable en los casos en que el historial se muestra exitosamente (después de encontrar un paciente y seleccionar un rango de fechas válido), o si no se encuentra el paciente, o si el rango de fechas seleccionado no es válido.

* Diagrama de Actividad - Consultar Disponibilidad Profesional

![Diagrama de Actividad - Consultar Disponibilidad Profesional / Caso de Uso 4 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/diagramadeactividades4ConsultarDisponibilidadProfesional.png)

[Enlace al Caso de Uso 4 - Consultar Disponibilidad Profesional / Caso de Uso 4 que representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/EcKgvd8TfFhDlShJWeli4EEBt9Z28unEtSy1jd4W6Kfh5g?e=kBumRV)

# Descripción del Diagrama de Actividades: Consultar Disponibilidad Profesional

Este diagrama de actividades describe el proceso dentro del "System" para consultar la disponibilidad de un profesional. El flujo comienza con la actividad "Consultar Disponibilidad Profesional", seguida de "Seleccionar Profesional".

A continuación, el sistema realiza una verificación condicional: "¿Profesional Encontrado?".

* **Si** se encuentra el profesional, el flujo continúa hacia "Seleccionar Rango de Fechas". Después de seleccionar el rango, se verifica condicionalmente si "¿Rango de Fechas Válido?".
    * **Si** el rango de fechas es válido, el sistema procede a "Mostrar Disponibilidad". Después de mostrar la disponibilidad, el flujo finaliza.
    * **No** (si el rango de fechas no es válido), el flujo finaliza.
* **No** (si no se encuentra el profesional), el flujo finaliza.

El diagrama finaliza en un nodo de fin, alcanzable en los casos en que la disponibilidad se muestra exitosamente (después de encontrar un profesional y seleccionar un rango de fechas válido), o si no se encuentra el profesional, o si el rango de fechas seleccionado no es válido.

* Diagrama de Actividad - Registrar Profesional de la Salud 

![Diagrama de Actividad - Registrar Profesional de la Salud / Caso de Uso 5 que se representa en un diagrama de actividad](/imagenesdediagramasdeactividades/diagramadeactividades5RegistrarProfesionaldelaSalud.png)

[Enlace al Caso de Uso 5 - Registrar Profesioanl de la Salud / Caso de Uso 5 que se representa en un diagrama de actividad](https://1drv.ms/i/c/f2bf844ed8279638/Ef8ScgX3qMlMr3Rx82xCOdgBfN1hSahLdR44KOXqHs3Q8w?e=K9YtO3)

# Descripción del Diagrama de Actividades: Registrar Profesional de la Salud

Este diagrama de actividades describe el proceso dentro del "System" para registrar un nuevo profesional de la salud. El flujo comienza con la actividad "Registrar Profesional de la Salud".

A continuación, se deben "Ingresar Datos Personales" del profesional. El flujo continúa con "Ingresar Datos Profesionales". Después de ingresar ambos tipos de datos, el sistema procede a "Validar Datos".

Se realiza una verificación condicional: "¿Datos Válidos?".

* **Si** los datos son válidos, el sistema procede a "Crear Perfil del Profesional". Después de crear el perfil, el flujo finaliza.
* **No** (si los datos no son válidos), el flujo regresa a la actividad de "Ingresar Datos Personales" para corregir la información.

El diagrama finaliza en un nodo de fin, alcanzable después de crear exitosamente el perfil del profesional. El proceso de ingreso de datos personales y profesionales se repite hasta que los datos ingresados sean considerados válidos.