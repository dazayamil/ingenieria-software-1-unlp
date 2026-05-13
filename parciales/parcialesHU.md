# Ingenieria de Software 1 - UNLP 2026

## Parciales resueltos de Historia de Usuario

### Parcial 1:  Seguimiento de licencias solicitadas

HU_01:
*ID:*  Solicitar licencia
*TITULO*: Como Empleado registrado quiero solicitar una licencia médica para justificar mis inasistencias y realizar el reposo adecuado.
*REGLAS DE NEGOCIO:*
    - el empleado debe tener más de 1 mes de antiguedad
    - el empleado no debe poseer licencias medicas vigentes

*CRITERIOS DE ACEPTACION:*
*Escenario 1:*  Solicitud de licencia exitosa
    DADO el empleado registrado de cuil 20-25421650-1, autenticado en el sistema, tiene 2 años de antiguedad y no posee licencias vigentes.
    CUANDO el empleado registrado ingresa cuil 20-25421650-1, tipo de licencia "presencial", fecha de inicio 05-06-2026, matricula medico 23265-1, diagnostico "Esguince de tobillo", seleccionar "Titular" y presiona "solicitar licencia"
    ENTONCES el sistema registra la solicitud y genera un codigo de licencia que envia por mail a la casilla del empleado junto con la confirmacion y dias otorgados.

*Escenario 2:*  Solicitud de licencia fallida por antiguedad insuficiente
    DADO el empleado registrado de cuil 20-94120040-1, autenticado en el sistema pero con antiguedad de 15 dias
    CUANDO el empleado registrado ingresa cuil 20-94120040-1, tipo de licencia "presencial", fecha de inicio 15-05-2026, matricula medico 50632-1, diagnostico "Gripe fuerte", salecciona "Titular" y presiona "solicitar licencia"
    ENTONCES el sistema deniega la solicitud e informa: "Solicitud de licencia rechazado por incumplimiento de antiguedad"

*Escenario 3:*  Solicitud de licencia fallida por poseer licencias vigentes
    DADO el empleado registrado de cuil 20-41899078-1, autenticado en el sistema pero con licencias vigentes
    CUANDO el empleado registrado ingresa cuil 20-41899078-1, tipo de licencia "presencial", fecha de inicio 12-05-2026, matricula medico 96035-1, diagnostico "Lumbalgia agudad", selcciona "familiar" y presionar "solicitar licencia"
    ENTONCES el sistema deniega la solicitud e informa: "Solicitud de licencia rechazado por poseer licencias vigentes"

HU_02:
*ID:*  Consultar licencias solicitadas
*TITULO*: Como Empleado administrativo quiero consultar las licencias solicitadas por un empleado para llevar adelante un control mensual de presentismo.
*REGLAS DE NEGOCIO:*
    - Solo se permite la impresion de un informe por mes por cada empleado.

*CRITERIOS DE ACEPTACION:*
*Escenario 1:*  Consulta de licencias exitosa
    //DADO que el empleado administrativo se encuentra autenticado y el CUIL 20-54812450-1 no registra informes impresos en el mes actual// PREGUNTAR SI VA DE ESTA FORMA?, 

    DADO el cuil 20-54812450-1 sin informe generado en el mes presente
    CUANDO el empleado administrativo ingresa cuil empleado 20-54812450-1, rango de fechas "05-03-2026" a "25-03-2026" y presiona "consultar licencias solicitadas"
    ENTONCES el sistema imprime un informe de las licencias solicitadas.

*Escenario 2:*  Consulta de licencias fallido por limite de informe alcanzado
    DADO el cuil 20-28321542-1 ya registra un informe impreso en el mes actual
    CUANDO el empleado administrativo ingresa cuil empleado 20-28321542-1, rango de fechas "01-02-2026" a "28-02-2026" y presiona "consultar licencias solicitadas"
    ENTONCES el sistema deniega el informe y notifica: "empleado ya cuenta con informe impreso en el mes"


### Parcial 2:  Gestion de turnos entre pacientes y profesionales
ENUNCIADO:
Te paso el enunciado de un parcial de HISTORIA DE USUARIO:
Una clinica medica privada desea desarrollar una aplicacion web para facilitar la gestion de turnos entre pacientes y profesionales de la salud. En la actualidad, los turnos se asignan unicamente de manera telefonica, lo que provoca demoras, errores y sobrecarga del personal administrativo.
La nueva solucion permitira a los pacientes autogestionar sus turnos y a los medicos administrar sus agendas de forma autonoma.
Para solicitar un turno, un paciente debe estar registrado y autenticado previamente (el registro y autenticacion no debe modelarse).
Los pacientes podran solicitar turnos con medicos de distintas especialidades, indicando, especialidad, medico, dia y hora. El sistema debe permiter que el paciente solicite solo un turno por especialidad por semana. Para poder solicitar un turno el paciente debe ser mayor a 18 años.
Los medicos registrados, previa autenticacion (el registro y la autenticacion no deben modelarse), podran ingresar a su panel para ver sus turnos. Para ello deberan ingresar una fecha y el sistema debera listar todos los turnos activos en esa fecha. El sistema debe permitir ingresar solo fechas del corriente año.

- Roles: Paciente registrado y Medico registrado.
- Requerimientos: Solicitar turno y Ver turnos.

HU_01:
*ID:*  Solicitar turnos
*TITULO*: Como paciente registrado quiero solicitar un turno medico para ser diagnosticado por mi malestar.
*REGLAS DE NEGOCIO:*
    - solo se permiten pacientes con edad mayor a 18 años.
    - solo se permite por paciente, un turno por especialidad en la semana.

*CRITERIOS DE ACEPTACION:*
*Escenario 1:*  solicitud exitoso
    DADO un paciente registrado, autenticado en el sistema, con edad de 21 años y con la especialidad no solicitada en la semana 
    CUANDO el paciente registrado ingresa especilidad "Cardiologia", medico "Gonzalez", dia "Jueves", hora "15 hs pm" y presiona "solicitar turno"
    ENTONCES el sistema registra el turno solicitado e informa la confirmacion al paciente.

*Escenario 2:*  solicitud fallida por ser menor de edad
    DADO un paciente registrado, autenticado en el sistema y con edad de 17 años.
    CUANDO el paciente registrado ingresa especilidad "Neurologia", medico "Flores", dia "Viernes", hora "17 hs pm" y presiona "solicitar turno"
    ENTONCES el sistema deniega la solicitud e informa: "Error de solicitud, debe ser mayor a 18 años"

*Escenario 3:*  solicitud fallida por limite de especialidad alcanzada
    DADO un paciente registrado, autenticado en el sistema, con edad de 30 años y con la especialidad ya solicitado en la semana
    CUANDO el paciente registrado ingresa especilidad "Dermatologia", medico "Lopez" dia "Lunes", hora "16 hs pm" y presiona "solicitar turno"
    ENTONCES el sistema deniega la solicitud e informa: "Error, se llego al limite de solicitud para la especialidad en la semana"

HU_02:
*ID:*  Ver turnos
*TITULO*: Como medico registrado quiero ver mis turnos registrados para gestionar mi agenda.
*REGLAS DE NEGOCIO:*
    - solo se permiten fechas del año corriente

*CRITERIOS DE ACEPTACION:*
*Escenario 1:*  Ver turnos exitoso
    DADO un medico registrado, autenticado en el sistema y las fecha selecciona corresponde al año corriente
    CUANDO el medico registrado ingresa fecha "20-05-2026" y presiona "Ver turnos"
    ENTONCES el sistema informa el listado de los turnos activos para la fecha.

*Escenario 2:*  Ver turnos fallido por fecha fuera del año corriente
    DADO un medico registrado, autenticado en el sistema y las fecha selecciona no corresponde al año corriente
    CUANDO el medico registrado ingresa fecha "20-05-2027" y presiona "Ver turnos"
    ENTONCES el sistema informa "Solo se permite ingresar fechas del año corriente".


### Parcial 3:  Cadena de gimnasios
![Parcial 3](parcial%201ra%20fecha%202025%20inge1.jpeg)

HU_01:
*ID:*  Solicitar turno
*TITULO*: Como socio registrado quiero solicitar turno para reservar mi lugar en el gimnasio
*REGLAS DE NEGOCIO:*
    - el socio debe tener su cuota al dia.
    - Debe haber cupo disponible para la clase, dia y hora seleccionados.

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Solicitud de turno exitoso
    DADO un socio registrado que esta autenticado en el sistema y con la cuota del gimnasio al dia
    CUANDO el socio registrado ingresa sede "GYM 07", clase "funcional", dia "Lunes", hora "18:00" y presiona "Solicitar turno"
    ENTONCES el sistema registra la reserva e informa la confirmacion con los datos del turno.

*Escenario 2:* Solicitud de turno fallido por cuota adeudada
    DADO un socio registrado que esta autenticado en el sistema pero registra una deuda en su cuota
    CUANDO el socio registrado ingresa sede "GYM 12", clase "PIlates", dia "Martes", hora "17:00" y presiona "Solicitar turno"
    ENTONCES el sistema deniega la solicitud e informa: "Para solicitar turno debe estar al dia con la cuota".

*Escenario 3:* Solicitud de turno fallido por cupo agotado
    DADO un socio registrado que esta autenticado en el sistema pero el cupo agotado para la clase, dia y hora 
    CUANDO el socio registrado ingresa sede "GYM 04", clase "Funcional", dia "Viernes", hora "21:00" y presiona "Solicitar turno"
    ENTONCES el sistema deniega la solicitud e informa: "Cupo no disponible para la actividad y hora selccionada".

HU_02:
*ID:*  Cancelar turno
*TITULO*: Como socio registrado quiero cancelar mi turno para liberar el cupo y permitir que otros socios puedan utilizar el lugar.
*REGLAS DE NEGOCIO:*
    - La cancelacion solo es permitida con una anticipacion minima de 1 hora respecto al inicio de la clase.

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Cancelacion exitosa
    DADO un socio registrado que esta autenticado en el sistema y con las condiciones de cancelacion son adecuadas
    CUANDO el socio registrado ingresa dia "Lunes", hora "18:00" y presiona "Cancelar turno"
    ENTONCES el sistema libera el cupo, registra la cancelacion e informa "Cancelacion de turno exitoso".

*Escenario 2:* Cancelacion fallida por no cumplir el tiempo de anticipacion
    DADO un socio registrado que esta autenticado en el sistema y con las condiciones de cancelacion no adecuadas
    CUANDO el socio registrado ingresa dia "Lunes", hora "18:00" y presiona "Cancelar turno"
    ENTONCES el sistema deniega la cancelacion e informa "La cancelacion debe realizar con 1 hora de anticipacion al horario de clase"

HU_03:
*ID:*  Crear clase
*TITULO*: Como administrador registrado quiero crear nuevas clases para mantener actualizada la oferta de actividades
*REGLAS DE NEGOCIO:*
    - No se permiten clases superpuestas en la misma sala, dia y hora.
    - Un instructor no puede tener asignados mas de tres clases en un mismo dia

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Creacion de clase exitosa
    DADO un administrador registrado que esta autenticado en el sistema y la sala "A" esta libre el lunes a las 10hs
    CUANDO el administrador registrado ingresa sede "La plata", clase "Funcional", sala "A", dni instructor 91256413, capacidad maxima 20, dia "Lunes", hora "10:00" y presiona "Crear clase"
    ENTONCES el sistema registra la clase nueva e informa "Clase nueva creada con exito".

*Escenario 2:* Creacion de clase fallida por sala ocupada
    DADO que en la sala "B" ya existe una clase de "Yoga" el martes a las 16:00hs
    CUANDO el administrador registrado ingresa sede "City bell", clase "Funcional", sala "B", dni instructor 98521563, capacidad maxima 15, dia "Martes", hora "16:00" y presiona "Crear clase"
    ENTONCES el sistema deniega la solicitud e informa "Sala ocupada en el dia y hora seleccionado"

*Escenario 3:* Creacion de clase fallida por limite de instructor alcanzado
    DADO que el instructor con DNI "30.123.456" ya tiene 3 clases programdas para el dia lunes
    CUANDO el administrador registrado ingresa sede "Ringuelet", clase "Crossfit", sala "C", dni instructor "30.123.456", capacidad maxima 30, dia "Lunes", hora "19:00" y presiona "Crear clase"
    ENTONCES el sistema deniega la solicitud e informa "Instructor alcanzo el maximo de clase por dia permitido"






