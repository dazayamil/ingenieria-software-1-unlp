# Ingenieria de Software - Tp2 Historias de Usuario

### Ejercicio 1 - Alquiler de Mobiliario

HU_1: ----------------------------------------------------
*ID:* dar alta mobiliario
*TITULO:* como encargado del mobiliario quiero registrar un nuevo mobiliario para mantener actualizado el inventario de la empresa
*REGLAS DE NEGOCIO:* 
    * Un mobiliario no puede estar registrado 2 veces con el mismo codigo.

*CRITERIOS DE ACEPTACION:* (registrar mobiliario)
*Escenario 1*: alta exitosa del mobiliario
    DADO el codigo mobiliario 2134 no registrado en el sistema y el encargado autenticado
    CUANDO el encargado registra el mobiliario con codigo 2134, tipo mesa,fecha 20/08/2025, fecha mantenimiento 01/09/2025, estado libre,precio 5000; y presiona "dar alta mobiliario"
    ENTONCES el sistema guarda el nuevo registro del mobiliario e informa al cliente "Mobiliario registrado exitosamente"

*Escenario 2*: Registro fallido por codigo repetido
    DADO el codigo mobiliario 2143 ya registrado en el sistema y el encargado mobiliario autenticado
    CUANDO el encargado registra el mobiliario con codigo 2134, tipo mesa, fecha 20/08/2025, fecha mantenimiento 01/09/2025, estado libre, precio 5000 y presiona "dar alta mobiliario"
    ENTONCES el sistema notifica el error por codigo mobiliario ya registrado.

*Escenario 3*: Registro fallido por encargado no autenticado
    DADO el codigo mobiliario 2143 no registrado en el sistema y el encargado mobiliario no autenticado
    CUANDO el encargado registra el mobiliario con codigo 2134, tipo mesa, fecha 20/08/2025, fecha mantenimiento 01/09/2025, estado libre, precio 5000 y presiona "dar alta mobiliario"
    ENTONCES el sistema notifica que para dar alta el mobiliario previamente debe autenticarse, da la opcion de autenticarse.
-----------------------------------------------------------------------

HU_2: ------------------------------------------------------------------
*ID:* Realizar reserva alquiler
*TITULO:* Como usuario quiero realizar una reserva de alquiler para un evento cercano
*REGLAS DE NEGOCIO:*
    * Una reserva tiene que tener como minimo 3 muebles

*CRITERIOS DE ACEPTACION:* (realizar reserva alquiler)
*Escenario 1*: Reserva exitosa
    DADO una reserva con 3 muebles y las condiciones de pago de reserva son las adecuadas
    CUANDO el usuario ingresa la fecha 10/10/2025, lugar Tolosa, cantidad dias 3, mobiliario 1 Mesa cantidad 5, mobiliario 2 sillas cantidad 20, mobiliario 3 manteles cantidad 5 y presionar "realizar reserva"
    ENTONCES el sistema redirige al usuario al pago con tarjeta de credito, espera respuesta, registra la reserva, setea a los mobiliarios en estado alquilado e informa al usuario "Reserva alquiler exitoso"

*Escenario 2:* Reserva fallida por incumplimiento de cantidad de muebles
    DADO una reserva con 2 muebles y las condiciones de pago de reserva son las adecuadas
    CUANDO el usuario ingresa la fecha 1/10/2025, lugar Tolosa, cantidad dias 3, mobiliario 1 Mesa cantidad 5, mobiliario 2 sillas cantidad 20 y presionar "realizar reserva"
    ENTONCES el sistema informa que para poder realizar la reserva como minimo tiene que alquilar 3 muebles.

*Escenario 3:* Reserva fallida por error en el pago
    DADO una reserva con 4 muebles y las condiciones de pago no son las correctas
    CUANDO el usuario ingresa la fecha 10/10/2025, lugar Tolosa, cantidad dias 3, mobiliario 1 Mesa cantidad 5, mobiliario 2 sillas cantidad 20, mobiliario 3 manteles cantidad 5, mobiliario 4 sillones cantidad 2 y presionar "realizar reserva"
    ENTONCES el sistema redirige al usuario al pago con tarjeta de credito, espera respuesta e informa "No se ha realizado el pago correctamente, no se pudo llevar realizar la reserva"
----------------------------------------------------------------------------

HU_3: ----------------------------------------------------------------------
*ID:* Pagar reserva
*TITULO:* Como usuario quiero realizar el pago de la reserva para efectuar el alquiler
*REGLAS DE NEGOCIO:*
    * Solo se aceptan tarjetas de credito

*CRITERIOS DE ACEPTACION:* (pagar reserva)
*Escenario 1:* Pago exitoso
    DADO la conexión con el servidor del banco exitosa, el numero 222555 correspondiente a una tarjeta de credito y la tarjeta con fondos suficientes para el pago
    CUANDO el usuario ingresa el numero de tarjeta 222555 y presiona "Pagar reserva"
    ENTONCES el sistema registra el pago, informa resultado de exito y retorna al usuario un numero unico de reserva para uso del alquiler.

*Escenario 2:* Pago fallido por numero de tarjeta de credito inexistente
    DADO la conexión con el servidor del banco exitosa y el número de tarjeta 111555 no correspondiente a una tarjeta de crédito,
    CUANDO el usuario ingresa el número de tarjeta 111555 y presiona “Pagar reserva”
    ENTONCES el sistema retorna un error por número de tarjeta inexistente

*Escenario 3:* Pago fallido por fondos insuficientes de tarjeta de crédito
    DADO la conexión con el servidor del banco exitosa, el número de tarjeta 666888 correspondiente a una tarjeta de crédito y sin fondos suficientes para el pago que se solicita hacer
    CUANDO el usuario ingresa el número de tarjeta 666888 y presiona “Pagar reserva”
    ENTONCES el sistema retorna un error por fondos insuficientes

*Escenario 4:* Pago fallido por fallo en la conexión con el servidor externo del banco
    DADO la conexión con el servidor del banco fallida
    CUANDO el usuario ingresa un número de tarjeta de credito 777888 y presiona “Pagar reserva”
    ENTONCES el sistema retorna un error por conexión no establecida
-----------------------------------------------------------------------------


HU_4----------------------------------------------------------------------
*ID:* Log in
*TITULO:* Como persona interna de la empresa quiero autenticarme al sistema para acceder a las funcionalidades de gestion de mobiliario y reservas
*REGLAS DE NEGOCIO:*
    * Solo los usuarios internos previamente registrados pueden autenticarse 
    * Despues de 3 intentos fallidos seguidos, la cuenta queda bloqueada ?

*CRITERIOS DE ACEPTACION:* (Log In)
*Escenario 1:* Inicio de sesión exitoso
    DADO que la persona interna ingresa usuario y contraseña correctos
    CUANDO la persona ingresa user juan contraseña ********** y presiona "Log In"
    ENTONCES el sistema lo autentica y lo redirige al panel de gestión

*Escenario 2:* Credenciales inválidas
    DADO que la persona interna ingresa usuario y contraseña 
    CUANDO intenta iniciar sesión
    Entonces el sistema muestra un mensaje de error: “Usuario o contraseña incorrectos”.

*Escenario 3:* Campos vacíos
    DADO que la persona interna deja usuario o contraseña vacíos
    CUANDO presiona “Iniciar sesión”
    ENTONCES el sistema muestra un mensaje de validación: “Debe ingresar usuario y contraseña”.
---------------------------------------------------------------------------------------

HU_4: -----------------------------------------------------------------------
*ID:* Log out
*TITULO:* Como persona interna de la empresa quiero cerrar sesion para ?
*REGLAS DE NEGOCIO:* 
    * El sistema debe finalizar sesion actual y liberar los recursos asociados
    * Despues de cerrar sesion, no se puede acceder a funcionalidades internas sin volver a iniciar sesion. 
*CRITERIOS DE ACEPTACION:* (Log out)
*Escenario 1:* Cierre de sesión exitoso
    DADO que la persona interna está autenticada en el sistema
    CUANDO presiona “Cerrar sesión”
    ENTONCES el sistema finaliza su sesión y lo redirige a la pantalla de inicio.

*Escenario 2:* Acceso posterior sin autenticación
    DADO que la persona interna cerró sesión
    CUANDO intenta acceder a funcionalidades internas (ej: alta de mobiliario)
    ENTONCES el sistema lo redirige a la pantalla de login



### Ejercicio 2 - Cadena hotelera

HU_1----------------------------------------------------------------------
*ID:* Reservar hospedaje
*TITULO:* Como usuario quiero realizar una reserva de hospedaje para asegurar mi estadía
*REGLAS DE NEGOCIO:*
    * Fecha de ingreso y egreso, debe estar en la lapso de 90 dias, basado en la fecha actual
    * La estadia debe ser maximo 15 dias

*CRITERIOS DE ACEPTACION:* (Reservar hospedaje)
*Escenario 1:* Reserva de hospedaje exitoso
    DADO que el usuario ingresa la fecha de ingreso 1/10/2025 y fecha de egreso 14/10/2025 y le fecha actual es 17/09/2025 y las condiciones de reserva son las adecuadas
    CUANDO el usuario pone fecha de ingreso 1/10/2025 y fecha de egreso 14/10/2025, hotel "Mar Azul" y cantidad de personas 5, y presionar "realizar hospedaje"
    ENTONCES el sistema procesa la reserva y, una vez finalizado el proceso de manera exitosa, envía al usuario un código de reserva junto con el enlace de pago a través de correo electrónico.

*Escenario 2:* Reserva de hospedaje fallido por estadia mayor a 15 dias
    DADO que el usuario ingresa la fecha de ingreso 1/10/2025 y fecha de egreso 20/10/2025 y le fecha actual es 17/09/2025 y las condiciones de reserva no son las adecuadas 
    CUANDO el usuario pone fecha de ingreso 1/10/2025 y fecha de egreso 20/10/2025, hotel "Mar Azul" y cantidad de personas 5, y presionar "realizar hospedaje"
    Entonces el sistema informa un error al usuario por exceder los dias maximos de estadia.

*Escenario 3:* Reserva de hospedaje fallida por exceder el lapso de 90 dias
    DADO que el usuario ingresa la fecha de ingreso 05/03/2026 y fecha de egreso 10/03/2026 y le fecha actual es 17/09/2025 y las condiciones de reserva no son las adecuadas 
    CUANDO el usuario pone fecha de ingreso 05/03/2026 y fecha de egreso 10/03/2026, hotel "Mar Azul" y cantidad de personas 5, y presionar "realizar hospedaje"
    Entonces el sistema informa un error al usuario por exceder el plazo de 90 dias de reserva
---------------------------------------------------------------------------------------


HU_2----------------------------------------------------------------------
*ID:* Realizar check in
*TITULO:* Como usuario quiero realizar el check in para disfrutar de mi estadia
*REGLAS DE NEGOCIO:*
    * Los check in solo deben realizarse en el horario de 10:00am hasta las 23:59pm

*CRITERIOS DE ACEPTACION:* (Realizar check in)
*Escenario 1:* Check in exitoso
    DADO que el usuario tiene el codigo de reserva 202020AB, con fecha actual y la hora son las adecuadas
    CUANDO el usuario ingresa el codigo de reserva 202020AB en el manual del hotel a las 10:30am
    ENTONCES el sistema informa la habitacion asignada, envia un mensaje a los conserjes para guiar al usuario y envia otro mensaje a los botones para llevar las valijas.

*Escenario 2:* Check in fallido por horario fuera de lo permitido
    DADO que el usuario tiene el codigo de reserva 303030BC, con fecha actual y la hora no son las adecuadas
    CUANDO el usuario ingresa el codigo de reserva 303030BC en el manual del hotel a las 07:30am
    ENTONCES el sistema informa que aun no se encuentra habilitado los ingresos al hotel

*Escenario 3:* Check in fallido por no estar en la fecha actual
    DADO que el usuario tiene el codigo de reserva 505050DF, con fecha distinta al actual 20/09/2025 y la hora son las adecuadas
    CUANDO el usuario ingresa el codigo de reserva 505050DF en el manual del hotel a las 15:00pm
    ENTONCES el sistema informa al usuario que no puede realizar el check in por no estar en la fecha adecuada
---------------------------------------------------------------------------------------

HU_3----------------------------------------------------------------------
*ID:* Realizar Check out
*TITULO:* Como conserje de la hotelera quiero realizar el check out para liberar habitaciones
*REGLAS DE NEGOCIO:*
    * Solo se puede realizar check out a habitacion sin gastos realizados

*CRITERIOS DE ACEPTACION:* (Realizar check out)
*Escenario 1:* Check out exitoso
    DADO que el conserje tiene el numero de habitacion 202020AB y no tiene gastos realizados
    CUANDO el conserje ingresa el numero de habitacion 202020AB y presionar "check out"
    ENTONCES el sistema enviada un mensaje a las mucamas de la hotelera para limpiar la habitacion

*Escenario 2:* Check out fallido por falta de pagos
    DADO que el conserje tiene el numero de habitacion 505050FG y tiene gastos realizados que no fueron pagos
    CUANDO el conserje ingresa el numero de habitacion 202020AB y presionar "check out"
    ENTONCES el sistema informa al conserje que no puede realizarse el check out por falta de pagos.
---------------------------------------------------------------------------------------

===========================================
2026:
### Ejercicio 3 - Venta de bebidas

1) Identificar roles:
    * Usuario no registrado: No tiene cuenta, puede registrarse(mayor a 18) y no puede comprar hasta registrarse
    * Usuario registrado: Tiene cuenta y puede iniciar sesion, puede comprar bebidas y ver su historial de comprar.
    * Usuario premium: Realiza todo lo anterior de usuario registrado, ademas tiene un descuento del 20%, si combina descuento por monto, se aplican ambos.

HU_1 -------------------------------------------------------------------------
*ID:* Registrar usuario
*TITULO:* Como usuario no registrado no quiero registrarme para poder comprar bebidas
*REGLAS DE NEGOCIO:*
    * el mail del usuario debe ser unico
    * el usuario a registrar debe ser mayor a 18 años

*CRITERIOS DE ACEPTACION:* (Registrar usuario)
*Escenario 1:* registro exitoso
    DADO el mail juanperez@gmail.com, no registrado en el sistema y la edad mayor a 18 años
    CUANDO el usuario no registrado ingresa nombre juan, apellido perez, mail juanperez@gmail.com, edad 19 y presiona "registrarse"
    ENTONCES el sistema procesa los datos, los guarda en la base de datos y despues el sistema envia por el mail ingresado la contraseña y notifica el registro exitoso

*Escenario 2:* registro fallido por mail repetido
    DADO el mail lucaspaz@gmail.com ya registrado en el sistema y la edad mayor a 18 años
    CUANDO el usuario no registrado ingresa nombre lucas, apellido paz, mail lucaspaz@gmail.com, edad 21 y presiona "registrarse"
    ENTONCES el sistema notifica que el mail ingresado ya se encuentra registrado en el sistema.

*Escenario 3:* registro fallido por edad menor a 18
    DADO el mail jorgepirez@gmail.com no registrado en el sistema y la edad menor a 18
    CUANDO el usuario no registrado ingresa nombre jorge, apellido pirez, mail jorgepirez@gmail.com, edad 17 y el usuario presiona "registrarme"
    ENTONCES el sistema detecta que no cumple con la edad y notifica que la ley xxxx impide la venta de bebidas alcoholicas a menores.
----------------------------------------------------------------------------------

HU_2 -----------------------------------------------------------------------------
*ID:* Log in
*TITULO:* Como usuario registrado o premiun quiero iniciar sesion para ingresar al sistema y poder comprar bebidas
*REGLAS DE NEGOCIO:*
    * Despues de 3 intentos fallidos seguidos, la cuenta queda bloqueada 

*CRITERIOS DE ACEPTACION:* (Log In)
*Escenario 1:* Log in exitoso
    DADO que el usuario registrado ingresa usuario y contraseña de manera correcta
    CUANDO el usuario ingresa user juan@gmail.com, contraseña juan123 y presiona "Log In"
    ENTONCES el sistema lo autentica y lo redirige al listado de bebidas

*Escenario 2:* Log in fallido por credenciales inválidas
    DADO que el usuario registrado ingresa usuario y contraseña de manera incorrecta 
    CUANDO el usuario ingresa user lucas@gmail.com contraseña lucas123 y presiona "Log In"
    Entonces el sistema muestra un mensaje de error: “Usuario o contraseña incorrectos”.

*Escenario 3:* Log in fallido por campos vacíos
    DADO que el usuario registrado deja usuario o contraseña vacíos
    CUANDO presiona “Log in"
    ENTONCES el sistema muestra un mensaje de validación: “Debe ingresar usuario y contraseña”.
-----------------------------------------------------------------------------------

HU_3: -----------------------------------------------------------------------------
*ID:* Log out
*TITULO:* Como usuario registrado quiero cerrar sesion para guardar mis compras
*REGLAS DE NEGOCIO:* 
    * El sistema debe finalizar sesion actual y liberar los recursos asociados
    * Despues de cerrar sesion, no se puede acceder a funcionalidades internas sin volver a iniciar sesion. 
*CRITERIOS DE ACEPTACION:* (Log out)
*Escenario 1:* Log out exitoso
    DADO que el usuario registrado esta logueado en el sistema
    CUANDO presiona “Cerrar sesión”
    ENTONCES el sistema finaliza su sesión y lo redirige a la pantalla de inicio.
------------------------------------------------------------------------------------

### Ejercicio 4 - Biblioteca

-   IDENTIFICAR ROLES: 
* ALUMNOS NO ASOCIADOS
* ALUMNOS ASOCIADOS

-   IDENTIFICAR FUNCIONALES:
* ASOCIAR ALUMNO
* PRESTAR LIBROS
* RETORNAR LIBRO

HU_1:
*ID:* Asociar alumno
*TITULO:* Como alumno no asociado quiero asociarme a la biblioteca para estar habilitado al prestamo de libros.
*REGLAS DE NEGOCIO:* - 

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Asociacion exitosa
    DADO un dni no vencido de un alumno no asociado
    CUANDO el alumno no asociado presenta el DNI 94512148
    ENTONCES el sistema asocia al alumno a la bilioteca, lo registra y se le asigna un numero de socio.

*Escenario 2:* Asociacion fallida, por dni ya asociado
    DADO un DNI no vencido, pero ya asociado al sistema
    CUANDO el alumno presenta el DNI 2312552
    ENTONCES el sistema informa un error al asociar debito a que dicho DNI ya esta asociado

*Escenario 3:* Asociacion fallida, por dni vencido
    DADO un DNI ya vencido
    CUANDO el alumno no asociado, presenta el DNI 246763
    ENTONCES el sistema informa que no puede ser asociado por DNI vencido.

HU_2:
*ID:* Prestar libro
*TITULO:* Como alumno asociado, quiero solicitar el prestamo de un libro para utilizar el mismo 
*REGLAS DE NEGOCIO:*
    * Solo a socios habilitados
    * No poseer más de 3 préstamos
    * No poseer préstamos vencidos

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Préstamo otorgado
    DADO un alumno habilitado y con las condiciones adecuadas para el prestamo del libro
    CUANDO el alumno con nro de socio 254, y solicita el prestamo de un libro
    ENTONCES el sistema otorga el prestamo de manera exitosa

*Escenario 2:* Préstamo no otorgado por alumno no habilitado por exceso de prestamos
    DADO un alumno no habilitado, con más de 3 prestamos otorgados y las condiciones son las adecuadas para el prestamo
    CUANDO el alumno con nro de socio 352, quiere solicitar el prestamo
    ENTONCES el sistema denega dicho prestamo por exceder el limite de prestamo

*Escenario 3:* Préstamo no otorgado por alumno no habilitado tener prestamos vencidos
    DADO un alumno no habilitado, con prestamos vencidos y las condiciones son las adecuadas para el prestamo
    CUANDO el alumno con nro de socio 852, quiere solicitar el prestamo
    ENTONCES el sistema denega dicho prestamo por poseer prestamos vencidos

*Escenario 4:* Préstamo no otorgado por mal estado de los libros
    DADO un alumno habilitado y las condiciones no son las adecuadas para el prestamo
    CUANDO el alumno con nro de socio 903, quiere solicitar el prestamo
    ENTONCES el sistema informa que no puede realizar el prestamo por poseer el libro en mal estado

HU_3:
*ID:* Retornar libro
*TITULO:* Como alumno asociado quiero retornar un libro para cumplir con los normas de la biblioteca
*REGLAS DE NEGOCIO:*
    * 

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Retorno de libro exitoso
    DADO un alumno asociado, que se encuentra dentro del lapso de tiempo antes del vencimiento y con un libro por devolver
    CUANDO el alumno asociado nro 325 y devuelve el libro "Clean Code"
    ENTONCES el sistema registra la devolucion del libro y libera al alumno de dicho prestamo

*Escenario 2:* Retorno de libro fallido por vencimiento cumplido
    DADO un alumno asociado, con un libro pendiente a devolver, pero ya cumplido el vencimiento
    CUANDO el alumno asociado nro 380 y devuelve el libro "Java"
    ENTONCES el sistema suspende al socio por un lapso de 15 dias y registra la devolucion del libro.

---------------------------------------------------------------------------------------------------------------------

### Ejercicio 5 - Manejo de licencias
HU_1:
*ID:* Solicitar licencia medica
*TITULO:* Como empleado quiero solicitar una licen medica para justificar mis inasistencias por salud
*REGLAS DE NEGOCIO:* 
    * el empleado deber tener mas de 1 mes de antiguedad
    * el empleado no debe terner licencia activa

*CRITERIOS DE ACEPTACION*
*Escenario 1:* Solicitud de licencia medica exitosa
    - DADO el empleado "Juan rodriguez", registrado y autenticado en el sistema, con mas de 1 mes de antiguedad y sin licenvia vigente
    - CUANDO el empleado "juan rodriguez" ingresa culi 20-52132645-4, tipo de licencia "presencial", fecha de inicio "05/05/2026", matricula medico 00325, diagnostico "dolor en espalda baja", para titular y presiona "solicitar licencia medica"
    - ENTONCES el sistema procesa los datos, registra la licencia, genera un codigo de licencia y lo envia al mail del empleado con la confirmacion y dias otorgados.

*Escenario 2* Solicitud de licencia medica fallida por no cumplir tiempo de antiguedad
    - DADO el empleado "Jose diaz", registrado y autenticado en el sistema, pero con el tiempo de antigueda menor a 1 mes
    - CUANDO el empleado "Jose diaz" ingresa culi 20-52369012-4, tipo de licencia "presencial", fecha de inicio "10/05/2026", matricula medico 10025, diagnostico "brazo izquierdo", para titular y presiona "solicitar licencia medica"
    - ENTONCES el sistema informa el rechazo de la licencia medica por no cumplir el tiempo de antiguedad.

*Escenario 3* Solicitud de licencia medica fallida por tener licencia vigente
    - DADO el empleado "Lucas Paz", registrado y autenticado en el sistema, con mas de 1 mes de antiguedad pero con licencia medica activa 
    - CUANDO el empleado "Lucas Paz" ingresa culi 20-20369710-4, tipo de licencia "presencial", fecha de inicio "12/05/2026", matricula medico 00236, diagnostico "brazo derecho", para titular y presiona "solicitar licencia medica"
    - ENTONCES el sistema informa el rechazo de la licencia medica por poseer una licencia activa.

HU_2:
*ID:* generar informe de licencias
*TITULO:* Como administrativo quiero consultar las licencias de un empleado para realizar el siguimiento y control de ausentismo.
*REGLAS DE NEGOCIO:* 
    * Solo se permite la impresion de 1 empleado por mes para cada empleado.

*CRITERIOS DE ACEPTACION*
*Escenario 1:* generacion de informe exitosa
    - DADO que el administrativo se encuentra autenticado y el empleado "Jose Diaz" cuil 20-50120520-1 no posee informes impresos en el mes actual.
    - CUANDO el administativo ingresa el cuil 20-50120520-1, define el rango de fechas "05/05/26" al "25/05/26" y presiona "solicitar informe" 
    - ENTONCES el sistema genera e imprime el informe solicitado.

*Escenario 2:* informe fallido por ya emitido en mes
    - DADO que el administrativo se encuentra autenticado y el empleado "Lucas Paz" cuil 20-25931065-1 ya posee un informe impreso registrado en el mes actual.
    - CUANDO el administativo intenta ingresar el cuil 20-41582960-1, rango de fechas "01/03/26" al "28/03/26" y presiona solicitar informe 
    - ENTONCES el sistema no permite la impresión e informa el error "Limite de impresión mensual alcanzado para este empleado".

---------------------------------------------------------------------------------------------------------------------

### Ejercicio 6 - Pago Electrónico

1) Identificar Roles:
    * Cliente
    * Empleado/Gerente
    * Sistema

HU_1: -------------------------------------------------------------------------------
*ID:* Realizar pago de impuesto o servicio
*TITULO:* Como cliente quiero realizar el pago de un impuesto o servicio para cancelar mis facturas
*REGLAS DE NEGOCIO:* 
    * Factura con 2do vencimiento vencido no puede cobrarse
    * Factura con 1er vencimiento vencido aplica regargo

*CRITERIOS DE ACEPTACION*
*Escenario 1:* Pago dentro del primer vencimiento (monto original)
    DADO un cliente con código de pago 556622 y el sistema ya conectado con la central de cobro mediante TOKEN requerido
    CUANDO el empleado/gerente ingresa el código de pago 556622 y el sistema recupera los datos de la factura, empresa edelap, nro cliente 2011, 1er vencimiento 30/09/2025, 2do vencimiento 05/10/2025, recargo $5.000, monto original $20.000, y hoy es 23/09/2025
    ENTONCES el sistema procesa el pago por el monto original ($20.000).

*Escenario 2:* Pago después del primer vencimiento (aplica recargo)
    DADO un cliente con código de pago 001188 y el sistema ya conectado con la central de cobro mediante TOKEN requerido
    CUANDO el empleado/gerente ingresa el código de pago 001188 y el sistema recupera los datos de la factura, empresa edelap, nro cliente 1990, 1er vencimiento 15/09/2025, 2do vencimiento 05/10/2025, recargo $5.000, monto original $20.0000, y hoy es 23/09/2025
    ENTONCES el sistema procesa el pago por el monto original + recargo ($25.000).

*Escenario 3:* Pago después del segundo vencimiento (rechazo)
    DADO un cliente con código de pago 115533 y el sistema ya conectado con la central de cobro mediante TOKEN requerido
    CUANDO el empleado/gerente ingresa el código de pago 115533 y el sistema recupera los datos de la factura, empresa edelap, nro cliente 1990, 1er vencimiento 15/08/2025, 2do vencimiento 05/09/2025, recargo $5.000, monto original $20.0000, y hoy es 23/09/2025
    ENTONCES el sistema rechaza el pago y muestra el mensaje 'La factura no puede cobrarse por estar vencida'.

*Escenario 4:* Pago fallido por error al conectarse con la central de cobro
    DADO un cliente con código de pago 885599 y el sistema sin poder conectarse a la central de cobro
    CUANDO el empleado/gerente ingresa el código de pago 115588559933 y el sistema trata de recuperar los datos de la factura
    ENTONCES el sistema informa error por no poder conectarse a la central de cobros.
-------------------------------------------------------------------------------------- 

HU_2: ---------------------------------------------------------------------------------
*ID:* Registrar pagos del dia en la central
*TITULO*: Como gerente quiero registrar los pagos del dia en la central de cobro para actualizar el sistema
*REGLAS DE NEGOCIO:*
    * El sistema no debe registrar 2 veces los pagos de los clientes en el dia.

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Registro de pagos exitoso
    DADO que el gerente ingresa la clave maestra **** de manera correcta y el sistema se conecto con la central de cobros mediante el TOKEN requerido
    CUANDO el gerente solicita registrar los pagos del dia, el sistema recupera las transacciones de los impuestos y servicios cobrados en el dia y las envia
    ENTONCES la central confirma la recepcion exitosa y el sistema lo registra como enviado.

*Escenario 2:* Registro de pagos fallido por reenvio de registros
    DADO que el gerente ingresa la clave maestra **** de manera correcta y el sistema se conecto con la central de cobros mediante el TOKEN requerido
    CUANDO el gerente solicita registrar los pagos del dia, que ya fueron enviados
    ENTONCES el sistema rechaza la operación e informa que los pagos ya fueron enviados y no pueden registrarse dos veces.

*Escenario 3:* Registro de pagos fallido clave maestra invalida
    DADO que el gerente ingresa la clave maestra **** incorrecta y el sistema se conecto con la central de cobros mediante el TOKEN requerido
    CUANDO el gerente solicita registrar los pagos del dia
    ENTONCES el sistema rechaza la solicitud e informa que la clave maestra es inválida.

*Escenario 4:* Registro de pagos fallido por error en la conexion con la central de cobro
    DADO que el gerente ingresa la clave maestra **** de manera correcta y el sistema no pudo conectarse con la central de cobros mediante el TOKEN requerido
    CUANDO el gerente solicita registrar los pagos del dia
    ENTONCES el sistema informa error de conexión con la central de cobros y los pagos quedan pendientes de envío.
--------------------------------------------------------------------------------------

HU_3: ---------------------------------------------------------------------------------
*ID:* Consultar estadisticas de impuestos y servicios cobrados
*TITULO*: Como gerente quiero consultar las estadisticas de impuestos y servicios cobrados para armar un informe
*REGLAS DE NEGOCIO:*
    * .



------------------------------------------------------------------------------------

### Ejercicio 10 - Manejo  de cancha de tenis

HU_01:
*ID:*  Registrar usuario
*TITULO*: Como usuario no registrado quiero registrarme al sistema para poder acceder a la solicitud de turnos.
*REGLAS DE NEGOCIO:*
    - el mail no puede repetirse
    - el usuario debe ser mayor igual a 18 años

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Registro de usuario exitoso
    DADO el mail "Juanp@gmail.com" no registrado al sistema y edad mayor a 18 años
    CUANDO el usuario no registrado ingresa nombre "Juan", apellido "Perez", mail "juanp@gmail.com", edad 23, domicilio "516 y 19" y presiona "registrarse"
    ENTONCES el sistema registra al usuario, genera una contraseña y se envia al mail del usuario.

*Escenario 2*: Registro fallido por mail ya registrado
    DADO el mail "Lucasf@gmail.com", registrado al sistema y edad mayor a 18 años
    CUANDO el usuario no registrado ingresa nombre "Lucas", apellido "Flores", mail "Lucasf@gmail.com", edad 24, domicilio "7 y 520" y presiona "registrarse"
    ENTONCES el sistema informa "el mail ya se encuentra registrado".

*Escenario 3*: Registro fallido por edad menor a 18
    DADO el mail "Pedrol@gmail.com", no registrado al sistema y edad menor a 18 años
    CUANDO el usuario no registrado ingresa nombre "Pedro", apellido "Lopez", mail "Pedrol@gmail.com", edad 17, domicilio "44 y 143" y presiona "registrarse"
    ENTONCES el sistema informa "Error, la edad minima para el registro es de 18 años".

HU_02:
*ID:*  Solicitar turno
*TITULO*: Como usuario registrado quiero solicitar turno en el sistema para asegurar mi lugar en la cancha.
*REGLAS DE NEGOCIO:*
    - el turno se debe solicitar con 2 dias de anticipacion

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Solicitar turno exitoso
    DADO que el usuario 'Juanp@gmail.com' autenticado en el sistema, la cancha seleccionada está libre y la fecha solicitada cumple con los 2 días de anticipación requeridos.
    CUANDO el usuario "Juanp@gmail.com" ingresa cancha 4, fecha "25/05/2026", hora "15:00" y presiona "solicitar turno"
    ENTONCES el sistema informa "Su turno ha sido registrado con éxito".

*Escenario 2*: Solicitud fallida por cancha ocupada
    DADO que el usuario "lucasl@gmail.com" autenticado en el sistema, la cancha seleccionada ocupada y la fecha solicitada cumple con los 2 días de anticipación requeridos.
    CUANDO el usuario "lucasl@gmail.com" ingresa cancha 2, fecha "27/05/2026", hora "18:00" y presiona "solicitar turno"
    ENTONCES el sistema informa "Cancha ocupada", por favor seleccione otro dia y horario.

*Escenario 3*: Solicitud fallida por incumplimiento de dias de anticipacion
    DADO que el usuario "Pedrog@gmail.com" autenticado en el sistema, la cancha seleccionada esta libre y la fecha solicitada no cumple con los 2 días de anticipación requeridos.
    CUANDO el usuario "Pedrog@gmail.com" ingresa cancha 1, fecha "13/05/2026", hora "21:00" y presiona "solicitar turno"
    ENTONCES el sistema denega la solicitud e informa "no cumple con los dias de anticipacion requeridos".

HU_03:
*ID:*  Iniciar sesion
*TITULO*: Como usuario registrado quiero iniciar sesion en el sistema para utilizar las funcionalidades disponibles.
*REGLAS DE NEGOCIO:*
    - solo se permiten 3 intentos

*CRITERIOS DE ACEPTACION:*
*Escenario 1:* Inicio de sesion exitoso
    DADO el usuario 'Juanp@gmail.com' registrado en el sistema y credenciales correctos
    CUANDO el usuario "Juanp@gmail.com" ingresa username: "JuanP@gmail.com", password: "123456" y presiona "iniciar sesion"
    ENTONCES el sistema autentica al usuario y lo redirige al panel de gestion.

*Escenario 2* Inicio de sesion fallido por username inexistente - 1 er fallo
    DADO el usuario 'Lucasf@gmail.com' no registrado en el sistema
    CUANDO el usuario "Lucasf@gmail.com" ingresa username: "Lucasf@gmail.com", password: "120246" y presiona "iniciar sesion"
    ENTONCES el sistema informa "username inexistente"
    en el entonces el sistema tiene que contabilizar los intentos fallidos para el inicio de sesion?

*Escenario 3* Inicio de sesion fallido por contraseña incorrecta - 2 do fallo
    DADO el usuario 'Pedrot@gmail.com' registrado en el sistema y credenciales incorrectos
    CUANDO el usuario "Pedrot@gmail.com" ingresa username: "Pedrot@gmail.com", password: "2002058" y presiona "iniciar sesion"
    ENTONCES el sistema informa "contraseña incorrecta"

*Escenario 4* Inicio de sesion fallido por credenciales incorrectos - 3 er fallo
    DADO el usuario 'Luisv@gmail.com' registrado en el sistema y credenciales incorrectos
    CUANDO el usuario "Luisv@gmail.com" ingresa username: "uisv@gmail.com", password: "89251" y presiona "iniciar sesion"
    ENTONCES el sistema informa "username o contraseña incorrecta"

*Escenario 5* Inicio de sesion fallido por bloqueo de cuenta
    DADO el usuario 'Josep@gmail.com' registrado en el sistema y credenciales correctos
    CUANDO el usuario "Josep@gmail.com" ingresa username: "Josep@gmail.com", password: "223655" y presiona "iniciar sesion"
    ENTONCES el sistema informa "cuenta bloqueada por llegar al limite maximo de intentos"


HU_04
*ID:* Cerrar sesión
*TÍTULO:* Como Usuario registrado quiero cerrar mi sesión para proteger la privacidad de mis datos y evitar el uso no autorizado de mi cuenta
*REGLAS DE NEGOCIO:*
    -

*CRITERIOS DE ACEPTACIÓN:*
*Escenario 1:* Cierre de sesión exitoso
    DADO que el usuario 'Juanp@gmail.com' se encuentra autenticado en el sistema
    CUANDO el usuario presiona el botón "Cerrar sesión".
    ENTONCES el sistema finaliza la sesión activa y redirige al usuario a la pantalla de inicio pública del sistema web

*Escenario 2:* Verificación de seguridad post-cierre
    DADO que el usuario ha finalizado su sesión correctamente
    CUANDO intenta acceder directamente a la funcionalidad de "Solicitar turno" sin loguearse nuevamente.
    ENTONCES el sistema le deniega el acceso y lo redirige automáticamente a la pantalla de inicio de sesión
