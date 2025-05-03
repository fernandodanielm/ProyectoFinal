# Anexo - Principios SOLID

# Principios SOLID en Programación Orientada a Objetos

Los principios **SOLID** son cinco reglas fundamentales que ayudan a diseñar software más flexible, escalable y fácil de mantener. Aquí tienes una breve descripción de cada uno:

## 🔹 S - **Single Responsibility Principle (SRP)**
Cada clase debe tener **una única responsabilidad**. Una clase no debe mezclar múltiples funcionalidades, evitando la complejidad innecesaria.

## 🔹 O - **Open/Closed Principle (OCP)**
Las clases deben estar **abiertas para extensión pero cerradas para modificación**. Es decir, podemos agregar nuevas funcionalidades sin modificar el código existente.

## 🔹 L - **Liskov Substitution Principle (LSP)**
Las **subclases deben poder sustituir a la superclase** sin alterar el comportamiento esperado del sistema. En otras palabras, cualquier instancia de una subclase debe poder reemplazar la instancia de su clase padre sin generar errores.

## 🔹 I - **Interface Segregation Principle (ISP)**
Las interfaces deben ser **específicas para cada caso de uso**, evitando clases con métodos innecesarios. Es mejor tener múltiples interfaces pequeñas que una única interfaz grande y genérica.

## 🔹 D - **Dependency Inversion Principle (DIP)**
Las clases deben **depender de abstracciones, no de implementaciones concretas**. Esto mejora la modularidad del código y permite realizar cambios sin afectar la estructura principal del sistema.

## ✨ Beneficios de SOLID
- Código más **organizado y mantenible**.
- Mayor **flexibilidad** para agregar nuevas funcionalidades.
- Reducción de **acoplamiento**, facilitando cambios y mejoras sin afectar otras partes del sistema.

Estos principios forman la base del diseño orientado a objetos y ayudan a desarrollar software escalable y sostenible. 🚀

* [Responsabilidad Única (SRP)](/srp.md)
* [Abierto/Cerrado (OCP)](/ocp.md)
* [Sustitución de Liskov (LSP)](/lsp.md)
* [Segregación de Interfaces (ISP)](/isp.md)
* [Inversión de Dependencias (DIP)](/dip.md)