# Ingenieria de Software 1 2025

## Clase 4 - Teoria: Diagrama de Transicion de Estados (DTE)

- Maquinas de Estado Finito: Describe al sistema como un conjunto de estados donde el sistema reacciona a ciertos eventos posibles (externos o internos)

f(Si, Cj) = Sk 
Al estar en el estado Si, la variación de la condición Cj hace que el sistema cambie al estado Sk.

- Maquinas de Estado Finito: un automata finito (AF) puede ser descrito como una 5-tupla (S, {, T, s, A)
{ es un alfabeto;
S es un conjunto de estados;
T es la función de transición;
s es el estado inicial;
A es un conjunto de estados de aceptación o finales;

- ESTADO
Los estados son las diferentes condiciones o situaciones bien definidas en las que puede encontrarse un sistema o un componente de software. El sistema permacene en este estado hasta que un estimulo lo obliga a cambiar

- EVENTO
Es un suceso significativo que debe tenerse en cuenta, que influye en el comportamiento y evolución del sistema

- TRANSICION
Las transiciones se producen como consecuencia de eventos. Pueden o no, tener un procesamiento asociado
(State2) --- Evento[Condicion]/ Accion ---> (State3)

* Evento: Obligatorio
* Condición: Opcional, depende del problema, puede haber transiciones sin condiciones
* Acción: Opcional, puede haber transiciones sin acciones.

*- Como contruir un DTE (Diagrama de Transicion de Estados) -*
1 Identificar estados
2 Si hay un estado complejo se puede explotar
3 Identificar estado inicial (desde el estado inicial, se identifican los cambios de estado con flechas)
4 Se analizan las condiciones y las acciones para pasar de un estado a otro
5 Se verifica la consistencia (estan todos los estados, se pueden alcanzar a todos los estados, etc).

El foco del DTE es el comportamiento y la evolución del sistema modelado, de modo que los estados representan las diferentes condiciones internas o fases por las que atraviesa ese sistema o componente de software.

### OTRAS DEFINICIONES & CONVENCIONES:
- ESTADO: Condición o situación en la que se encuentra una entidad u objeto durante un período de tiempo. Nombrar: verbos en gerundio (-ando, -endo). SIEMPRE PENSAR: QUE ESTA HACIENDO O ESPERANDO EL SISTEMA DURANTE ESE ESTADO?

- Transicion: Cambio de un estado a otro disparado por un evento.

- Evento: Suceso que provoca un cambio de estado (por ejemplo, “botón presionado”, “pago recibido”). Es el disparador del cambio de estado, es algo que sucede y el sistema detecta. Se debe escribir en forma impersonal, por que el sistema no lo provoca, sino que lo recibe(generalmente de un usuario o del entorno). Se escribe: "Se + verbo en pasado simple + complemento". Importante: el evento no es una acción del sistema

- Accion: Actividad que ocurre como consecuencia de una transición. Se ejecuta “mientras cambia de estado”. La acción representa una tarea o proceso que realiza el sistema como respuesta al evento y transición. Verbo en infinitivo (termina en: ar, er, o ir) + sustantivo Ej: mostrar mensaje, registrar pago, imprimir ticket, enviar alerta.

- Condicion: Requisito que debe cumplirse para que ocurra una transición (por ejemplo, saldo > 0). Expresión lógica que el sistema evalúa. Una condición no causa el cambio por si sola, sino debe cumplirse para que ocurra la transición. Ejemplo [tecla == "enter"], [monto >= total], [temperatura > 50 grados]

Estado inicial, punto de partida del objeto. Estado final, estado donde el objeto completa su ciclo de vida.


- VENTAJAS:
Mejora la comprensión: ofrece un mapa visual que hace fácil entender como un sistema reacciona a diferentes eventos
* Previene errores: ayuda a encontrar fallos de lógica y caminos que no deberían existir, todo esto en la etapa de diseño, lo que ahorra tiempo y esfuerzo en la codificación
* Valida el diseño: confirma que todos los requisitos del sistema han sido considerados y que el comportamiento es coherente.
* Facilita las pruebas: proporciona un plan de crear pruebas, asegurando que se validan todas las interacciones posibles del sistema. 


