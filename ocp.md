# Principio de Abierto/Cerrado (OCP)

# Principio de Abierto/Cerrado (OCP)

El **Principio de Abierto/Cerrado (OCP)** es uno de los pilares fundamentales de los principios **SOLID** en programación orientada a objetos. Permite que un sistema pueda evolucionar sin necesidad de modificar el código existente.

## 🔹 Propósito del OCP
El OCP establece que **las clases, módulos y funciones deben estar abiertas para extensión, pero cerradas para modificación**. Esto significa que podemos **agregar nuevas funcionalidades sin alterar el código original**, evitando introducir errores en partes del sistema que ya funcionan correctamente.

## 🔹 Tipo de Principio SOLID
Este principio pertenece a la categoría de **diseño estructural**, promoviendo la escalabilidad y sostenibilidad del código a lo largo del tiempo.

## 📌 Problema y Solución

### 📌 Problema:
Imagina que nuestro sistema de gestión de turnos médicos tiene una clase `GeneradorReportes`, que genera informes en **PDF**. Un día, surge la necesidad de permitir exportación en **Excel**, pero la clase actual solo tiene métodos para **PDF**.  
Si modificamos directamente `GeneradorReportes`, corremos el riesgo de **romper funcionalidades previas** o generar conflictos.

### ✅ Solución con OCP:
En lugar de modificar `GeneradorReportes`, aplicamos **polimorfismo** y creamos una **superclase abstracta `ExportadorReportes`**, con subclases especializadas:
- `ExportadorPDF`
- `ExportadorExcel`

Cada subclase maneja su formato específico **sin modificar el código original**. Así, si necesitamos agregar exportación a **CSV**, solo creamos `ExportadorCSV`, sin tocar las clases existentes.

## 🌍 Ejemplo del mundo real  
Imagina un sistema de **autos de alquiler** que inicialmente solo permite **autos estándar**. Si el negocio crece y se quiere ofrecer **autos eléctricos**, **SUVs** o **camionetas**, **no es necesario modificar la estructura base del sistema**.  
En cambio, simplemente se **extiende la funcionalidad**, agregando nuevas clases para cada tipo de vehículo sin alterar el código previo.

## ✨ Beneficios de aplicar OCP  
✔ **Facilita la evolución del sistema sin modificar su núcleo**.  
✔ **Evita errores en funcionalidades existentes**.  
✔ **Mayor flexibilidad para agregar nuevas características**.  

 

# Motivación del Principio de Abierto/Cerrado (OCP)

## 📌 Problema en el sistema  
Nuestro sistema de gestión de turnos médicos enfrentaba un problema de **rigidez y falta de escalabilidad**. Algunas clases estaban diseñadas de forma que **cualquier nueva funcionalidad requería modificar el código existente**, lo que aumentaba el riesgo de errores y dificultaba la evolución del sistema.  

Por ejemplo, la clase `GeneradorReportes` solo permitía exportación en **PDF**. Cuando surgió la necesidad de exportar en **Excel**, el código original debía ser **modificado**, generando posibles fallos en la exportación previa. Cada vez que se agregaba un nuevo formato de exportación, el código se volvía más difícil de mantener y propenso a errores.

## ✅ Solución con OCP  
Para resolver este problema, aplicamos el **Principio de Abierto/Cerrado (OCP)**, que nos permite **agregar nuevas funcionalidades sin modificar el código existente**.  
En lugar de editar `GeneradorReportes` directamente, creamos una **superclase `ExportadorReportes`**, de la cual derivan varias subclases:  
- `ExportadorPDF`  
- `ExportadorExcel`  
- `ExportadorCSV`  

Cada subclase maneja su propio formato de exportación. Así, si en el futuro agregamos una nueva opción, como **ExportadorJSON**, simplemente la implementamos sin tocar las clases ya existentes. Esto **protege el código original**, evitando errores y reduciendo el impacto de los cambios.

## 🌍 Ejemplo del mundo real  
Imagina un **sistema de pagos en línea** que inicialmente solo acepta **tarjetas de crédito**.  
Con el crecimiento del negocio, los usuarios piden más opciones como **PayPal, criptomonedas o transferencias bancarias**. Si el sistema original solo está diseñado para tarjetas de crédito, agregar nuevos métodos requeriría **modificar el código base**, arriesgando su estabilidad.  

Aplicando **OCP**, se crea una **superclase `ProcesadorPago`** y cada método de pago es una subclase:  
- `PagoTarjetaCredito`  
- `PagoPayPal`  
- `PagoTransferenciaBancaria`  
- `PagoCriptomonedas`  

De esta manera, si más adelante se agrega **PagoApplePay**, simplemente se implementa la subclase correspondiente **sin afectar el código previo**, garantizando la estabilidad del sistema.

## ✨ Beneficios de aplicar OCP  
✔ **Permite agregar nuevas funcionalidades sin modificar el código existente**.  
✔ **Reduce el riesgo de errores en partes del sistema que ya funcionan correctamente**.  
✔ **Facilita la evolución del software, haciéndolo más flexible y escalable**.  

# Caso Real

## Parte 2 – Aplicación de Principios SOLID en el Diseño de Clases

### Principio de Abierto/Cerrado (OCP)

* **Propósito y Tipo del Principio SOLID:** El Principio de Abierto/Cerrado establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas a la extensión, pero cerradas a la modificación. Esto significa que deberíamos poder añadir nueva funcionalidad sin necesidad de alterar el código existente. El OCP es un principio de diseño de clases y módulos.

* **Motivación:** En nuestro sistema, podríamos necesitar agregar nuevas formas de validar la información del paciente o del profesional, o quizás soportar diferentes tipos de informes o formatos de salida de datos. Si no aplicamos OCP, cada vez que necesitemos añadir una nueva validación o un nuevo formato de informe, tendríamos que modificar las clases existentes, lo que aumenta el riesgo de introducir errores y dificulta el mantenimiento a largo plazo.

* **Caso Real (Descripción Textual): Agregando un Nuevo Método de Notificación de Turnos**

    Nuestro sistema de gestión de turnos actualmente notifica a los pacientes y profesionales sobre la asignación y cancelación de turnos a través de correo electrónico, utilizando la clase `EmailNotificador` que implementa la interfaz `ServicioNotificacion`.

    En el futuro, surge la necesidad de ofrecer a los usuarios la opción de recibir notificaciones también a través de mensajes de texto (SMS).

    **Aplicación del Principio de Abierto/Cerrado (OCP):**

    Para implementar esta nueva funcionalidad sin modificar el código existente de la interfaz `ServicioNotificacion` ni la clase `AgendaTurnos` (que es la que utiliza el servicio de notificación), podemos aplicar el Principio de Abierto/Cerrado de la siguiente manera:

    1.  **Extensión mediante una Nueva Clase:** Creamos una nueva clase llamada `SMSNotificador` que también implementa la interfaz `ServicioNotificacion`. Esta nueva clase contendrá la lógica específica para enviar mensajes de texto utilizando un servicio de SMS (que podría ser una biblioteca o una API externa). La interfaz `ServicioNotificacion` permanece sin cambios.

        ```java
        class SMSNotificador implements ServicioNotificacion {
            @Override
            public void enviarNotificacion(String mensaje, String destinatario) {
                // Lógica para enviar el mensaje SMS al destinatario
                System.out.println("Enviando SMS a " + destinatario + ": " + mensaje);
            }
        }
        ```

    2.  **Configuración en la AgendaTurnos:** La clase `AgendaTurnos` (o el componente encargado de la notificación) se puede configurar para utilizar diferentes implementaciones de `ServicioNotificacion`. Esto podría hacerse mediante inyección de dependencias, permitiendo que se instancien y utilicen tanto `EmailNotificador` como `SMSNotificador` según la preferencia del usuario o la configuración del sistema. El código de la `AgendaTurnos` que invoca el método `enviarNotificacion` de la interfaz `ServicioNotificacion` no necesita ser modificado para soportar el nuevo método de notificación por SMS.

    **Resultado:**

    Al seguir este enfoque, hemos extendido la funcionalidad de notificación de nuestro sistema para incluir SMS sin necesidad de alterar el código existente de la interfaz `ServicioNotificacion` o la clase `AgendaTurnos`. Simplemente creamos una nueva clase (`SMSNotificador`) que se adhiere a la interfaz ya definida. Esto cumple con el Principio de Abierto/Cerrado: el sistema está abierto a la extensión (añadiendo nuevos métodos de notificación) pero cerrado a la modificación (el código base para la notificación no se cambia). Esto facilita la adición de futuras formas de notificación (como notificaciones push o por WhatsApp) de la misma manera, haciendo que el sistema sea más flexible y mantenible.