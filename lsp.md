# Principio de Sustitución de Liskov (LSP)

El **Principio de Sustitución de Liskov (LSP)** es uno de los principios **SOLID** que garantiza que las subclases pueden sustituir a sus superclases sin alterar el comportamiento esperado del programa.

## 🔹 Propósito del LSP  
El LSP establece que **si una clase hija sustituye a una clase padre, el programa debe seguir funcionando sin errores ni cambios inesperados**. Es decir, cualquier instancia de una subclase debe poder reemplazar la instancia de su clase base sin causar problemas en el sistema.

## 🔹 Tipo de Principio SOLID  
Este principio pertenece a la categoría de **diseño estructural**, enfocándose en la correcta **herencia y polimorfismo**, asegurando la consistencia en el comportamiento de las clases.

## 📌 Problema y Solución  

### 📌 Problema:  
En un sistema de gestión de turnos médicos, supongamos que tenemos la clase `ProfesionalSalud`, que define métodos como `atenderPaciente()`. Luego, creamos una subclase `Especialista`, que hereda de `ProfesionalSalud`, pero su método `atenderPaciente()` **requiere parámetros adicionales** o **cambia el flujo del programa**.  

Si sustituimos `ProfesionalSalud` por `Especialista` en nuestro código sin verificar su comportamiento, el sistema podría **fallar o arrojar errores inesperados**, rompiendo el principio de sustitución.

### ✅ Solución con LSP:  
Para aplicar LSP correctamente:  
1. **Las subclases deben ser completamente compatibles con la clase padre**.  
2. **Ninguna subclase debe modificar los contratos de los métodos heredados**.  
3. **Si una subclase requiere restricciones adicionales, es mejor crear una nueva jerarquía en lugar de modificar la existente**.  

Siguiendo estas reglas, garantizamos que `Especialista` puede reemplazar `ProfesionalSalud` sin causar problemas en el código.

## ✨ Beneficios de aplicar LSP  
✔ **Evita errores al reemplazar objetos de una clase base con objetos de una subclase**.  
✔ **Permite una herencia más limpia y estructurada**.  
✔ **Facilita la escalabilidad sin romper el código existente**.  

# Motivación del Principio de Sustitución de Liskov (LSP)

## 📌 Problema en el sistema  
Nuestro sistema de gestión de turnos médicos enfrentaba un problema relacionado con la **herencia incorrecta y el comportamiento inesperado** de algunas subclases.  
Habíamos definido una clase `ProfesionalSalud`, que tenía métodos como `atenderPaciente()`. Posteriormente, creamos una subclase `Especialista`, que heredaba de `ProfesionalSalud`, pero modificaba el comportamiento de `atenderPaciente()` al **requerir parámetros adicionales** o **cambiar el flujo esperado del método**.  

Cuando utilizábamos un objeto de `Especialista` en lugar de `ProfesionalSalud`, el sistema **fallaba** porque algunos módulos no podían manejar las diferencias en los parámetros requeridos. Esto violaba la regla de que una subclase debe poder sustituir a su superclase sin afectar la funcionalidad del programa.

## ✅ Solución con LSP  
Para evitar estos errores, aplicamos el **Principio de Sustitución de Liskov (LSP)**, asegurándonos de que cualquier subclase de `ProfesionalSalud` mantuviera la **misma estructura de métodos** y comportamiento esperado.  
La solución fue diseñar la jerarquía de clases correctamente:  
1. **Definir interfaces claras** para que las subclases respeten el comportamiento esperado.  
2. **Evitar la alteración de los parámetros de métodos heredados** en las subclases.  
3. **Crear nuevas clases específicas en lugar de modificar la clase base**, si el comportamiento realmente debía ser distinto.  

## 🌍 Ejemplo del mundo real  
Imagina un sistema de **alquiler de vehículos**, donde la clase `Vehiculo` tiene un método `calcularCostoAlquiler(dias)`. Luego se crean subclases como `AutoEstandar` y `AutoLujo`, pero `AutoLujo` decide modificar el método `calcularCostoAlquiler(dias)` para incluir **un parámetro adicional sobre el seguro**.  

Si una aplicación espera cualquier `Vehiculo` y usa `AutoLujo`, **el sistema fallará** porque la firma del método ha cambiado.  
La solución con **LSP** sería definir una estructura más clara:  
- Mantener la firma del método igual para todas las clases.  
- Si `AutoLujo` tiene costos adicionales, se puede agregar un método separado como `calcularCostoSeguro()`.  

De esta manera, todas las clases **pueden sustituir a su superclase sin romper el sistema**.

## ✨ Beneficios de aplicar LSP  
✔ **Garantiza que las subclases respeten el comportamiento de la superclase**.  
✔ **Evita errores inesperados al sustituir una clase por otra**.  
✔ **Mejora la escalabilidad del sistema sin afectar la lógica existente**.  

# Caso Real

## Parte 2 – Aplicación de Principios SOLID en el Diseño de Clases

### Principio de Abierto/Cerrado (OCP)

* **Propósito y Tipo del Principio SOLID:** El Principio de Abierto/Cerrado establece que las entidades de software (clases, módulos, funciones, etc.) deben estar abiertas a la extensión, pero cerradas a la modificación. Esto significa que deberíamos poder añadir nueva funcionalidad sin necesidad de alterar el código existente. El OCP es un principio de diseño de clases y módulos.

* **Motivación:** En nuestro sistema, podríamos necesitar agregar nuevas formas de validar la información del paciente o del profesional, o quizás soportar diferentes tipos de informes o formatos de salida de datos. Si no aplicamos OCP, cada vez que necesitemos añadir una nueva validación o un nuevo formato de informe, tendríamos que modificar las clases existentes, lo que aumenta el riesgo de introducir errores y dificulta el mantenimiento a largo plazo.

* **Caso Real (Descripción Textual): Agregando un Nuevo Tipo de Validación para Pacientes**

    En nuestro sistema, la clase `Paciente` requiere validación al momento de su registro. Actualmente, tenemos implementaciones para validar el formato del documento y el formato del correo electrónico.

    **Problema con un Diseño No OCP (Escenario Inicial Incorrecto):**

    Si la lógica de validación estuviera implementada directamente dentro de una clase `PacienteValidator` con una serie de condicionales para cada tipo de validación, cada vez que necesitemos agregar una nueva validación (por ejemplo, verificar la validez de la fecha de nacimiento), tendríamos que modificar la clase `PacienteValidator` añadiendo un nuevo `if` o `else if`. Esto viola el OCP porque estamos modificando una clase existente para extender su funcionalidad.

    ```java
    // Diseño inicial (violación de OCP)
    class PacienteValidator {
        public boolean esPacienteValido(Paciente paciente) {
            if (!esFormatoDocumentoValido(paciente.getNumeroDocumento())) {
                return false;
            }
            if (!esFormatoEmailValido(paciente.getCorreoElectronico())) {
                return false;
            }
            // Si necesitamos validar la fecha de nacimiento, tendríamos que añadir aquí otro 'if'
            // if (!esFechaNacimientoValida(paciente.getFechaNacimiento())) { ... }
            return true;
        }

        private boolean esFormatoDocumentoValido(String documento) {
            // ... lógica de validación del documento ...
            return documento != null && documento.matches("\\d{8}");
        }

        private boolean esFormatoEmailValido(String email) {
            // ... lógica de validación del email ...
            return email != null && email.contains("@");
        }

        // Si necesitamos validar la fecha de nacimiento, tendríamos que añadir aquí otro método
        // private boolean esFechaNacimientoValida(LocalDate fechaNacimiento) { ... }
    }
    ```

    **Aplicación del OCP (Solución Correcta):**

    Para aplicar el Principio de Abierto/Cerrado, podemos diseñar el sistema de validación utilizando una interfaz y múltiples clases concretas para cada tipo de validación:

    1.  **Interfaz `ValidadorPaciente`:** Definimos una interfaz para todas las validaciones de pacientes.

        ```java
        interface ValidadorPaciente {
            boolean esValido(Paciente paciente);
        }
        ```

    2.  **Clases de Validación Concretas:** Creamos clases que implementan la interfaz para cada regla de validación específica.

        ```java
        class ValidadorFormatoDocumento implements ValidadorPaciente {
            @Override
            public boolean esValido(Paciente paciente) {
                return paciente.getNumeroDocumento() != null && paciente.getNumeroDocumento().matches("\\d{8}");
            }
        }

        class ValidadorFormatoEmail implements ValidadorPaciente {
            @Override
            public boolean esValido(Paciente paciente) {
                return paciente.getCorreoElectronico() != null && paciente.getCorreoElectronico().contains("@");
            }
        }

        class ValidadorFechaNacimiento implements ValidadorPaciente {
            @Override
            public boolean esValido(Paciente paciente) {
                return paciente.getFechaNacimiento() != null && !paciente.getFechaNacimiento().isAfter(LocalDate.now());
            }
        }
        ```

    3.  **Uso de los Validadores:** La clase o servicio que realiza la validación puede recibir una lista de `ValidadorPaciente` y ejecutarlos.

        ```java
        class ServicioValidacionPaciente {
            public boolean esPacienteValido(Paciente paciente, List<ValidadorPaciente> validadores) {
                for (ValidadorPaciente validador : validadores) {
                    if (!validador.esValido(paciente)) {
                        return false; // O podríamos acumular errores
                    }
                }
                return true;
            }
        }
        ```

**Resultado:**

Con este diseño, para agregar una nueva validación (por ejemplo, validar el formato del teléfono), simplemente creamos una nueva clase `ValidadorFormatoTelefono` que implementa `ValidadorPaciente`. No necesitamos modificar la interfaz `ValidadorPaciente` ni la clase `ServicioValidacionPaciente`. El sistema está abierto a la extensión (añadiendo nuevos validadores) pero cerrado a la modificación (el código existente de validación no se altera).

# Estructura de clases
![Diagrama LSP](/imagenesPricipioSolid/DiagramaUMLCLASSLSP.png)

[Enlace al diagrama](https://1drv.ms/i/c/f2bf844ed8279638/EXEWyxYQ8WFMk6L96LrVnHEBWdSbrLSywJGnKO4IS3zHFA?e=9OWqtb)

```Java
class ProfesionalSalud {
    private String nombreCompleto;
    private String numeroDocumento;
    // ...

    public Map<String, String> obtenerInformacionProfesional() {
        return Map.of("nombre", nombreCompleto, "documento", numeroDocumento);
    }
}

class Medico extends ProfesionalSalud {
    private String especialidad;

    @Override
    public Map<String, String> obtenerInformacionProfesional() {
        Map<String, String> info = super.obtenerInformacionProfesional();
        info.put("especialidad", especialidad);
        return info;
    }
}

class AgendaTurnos {
    public void asignarTurno(Paciente paciente, ProfesionalSalud profesional, LocalDateTime fechaHora, String motivo) {
        System.out.println("Asignando turno a: " + profesional.obtenerInformacionProfesional().get("nombre"));
    }
}

Descripción: El Principio de Sustitución de Liskov establece que los objetos de una superclase deben poder ser reemplazados por objetos de sus subclases sin alterar la correctitud del programa. Aquí, Medico y Enfermero son subtipos de ProfesionalSalud y pueden ser utilizados indistintamente por AgendaTurnos-