# Ingenieria de Software 1 - TP 3 Casos de Uso

## Parte 1: Definiciones generales

b) Los Casos de Uso (CU) son objetivos y/o funcionaliadades del sistema, donde interactua un actor y el sistema para lograr ficho CU. La utilizacion de los Caso de Uso, son con actores, diagramas y escenario, para que un CU sea considerado correcto, debe tener su escenerio correspondiente.
Una funcionalidad o servicio que el sistema ofrece al actor.

c) Un actor, es quien inicia los casos de uso previamente ya declarados y identificados. Un actor en quien interactua con el sistema por medio de los casos de uso. Estos pueden ser, una persona, sistema externo, dispositivo, etc. Actor: toda entidad que interactua directamente con el sistema.

Un Escenario, es la descripcion completa del Caso de Uso, sus interacciones y variaciones en el flujo normal del sistema.

d) Relaciones en los Casos de Uso son:
* Asociacion: Se utiliza cuando un actor interactua directamente con una funcionalidad

* Extends: Es como una variacion o excepcion. Se utiliza cuando una funcionalidad adicional se activa bajo ciertas condiciones. Example "Reservar habitacion" <<extend>> "Aplicar descuento".

* <<Uses>>: Se utiliza cuando un caso de uso tiene un subproceso obligatorio que se repite en varios casos. Ejemplo CU. "Pagar reserva" <<uses>> "Validar tarjeta"

* Herencia: Un actor o caso de uso, hereda caracteristicas de otro mas general.

e) Beneficios de los casos de uso:
    * Herramienta para capturar requerimientos funcionales.
    * Descompone el alcance del sistema en piezas más manejables.
    * Medio de comunicación con los usuarios.
    * Utiliza lenguaje común y fácil de entender por las partes.
    * Permite estimar el alcance del proyecto y el esfuerzo a realizar.
    * Define una línea base para la definición de los planes de prueba.
    * Define una línea base para toda la documentación del sistema.
    * Proporciona una herramienta para el seguimiento de los requisitos.



