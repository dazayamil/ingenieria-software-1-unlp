# Ingenieria de Software 1 2025 

## Clase 2 - Teoria:

### BRAINSTORMIN ------------

BRAINSTORMIN = Lluvia de Ideas: tecnica por el cual se reunen varios participantes generando ideas sin ningun analisis, ni guion, compartiendo pensamiento de manera global en un tiempo corto hasta que se agoten las ideas. Este proceso motiva o despierta en otros más ideas creativas, cuantas más ideas se sugieren, mejores resultados se conseguirán.

FASES:
1) Descubrir hechos (problematicas - requerimientos)
2) Producir ideas (soluciones - opciones - implementacion de HU con requerimientos ya definidos)
3) Descubrir soluciones (desarrollar las soluciones y/o opciones elegidas en la fase 2)

### Especificacion de requerimientos -----------

Objetivos: permitir que los desarrolladores expliquen como entendieron lo que el cliente quiere con el sistema, indicar a los diseñadores que funcionalidad y caracteristicas va a tener el sistema y por ultimo, indicar al equipo de prueba las validaciones a demostrar.

*Propiedades*
* Necesario: Su omision provoca una deficiencia
* Conciso: Facil de leer y entender
* Completo: No necesita ampliarse
* Consistente: No contradictorio con otro
* No ambiguo: Tiene una sola implementacion
* Verificable: Puede testearse a travez de inspecciones, pruebas, etc.

La *Documentacion de definicion de requerimientos* es el listado completo de todas las cosas que el cliente espera que el sistema haga, y la *Documentacion de especificacion de requemientos* es la parte tecnica, seria el desarrollo de cada uno de los item del listado anterior.

### Historia de Usuario = HU

Una historia de usuario, es una descripción corta y simple de un requerimiento del cliente implementadas en el sistema. Son utilizadas en metodologías de desarrollo agiles (example SCRUM).

**_ ALGUNOS CONCEPTOS _**

Las HU deben ser limitadas (cortas), son una forma rápida de administrar los requisitos de los clientes, permite responder de forma rápida a los cambios en los requerimientos, se deben involucrar los clientes para implementar una HU, tener tiempo de estimación, pasado dicho tiempo se debe considerar en dividir la HU.

**_ FORMA DE REDACTAR: _**

La HU debe saber responder 3 preguntas: Quien se beneficia, que se quiere y cual es el beneficio. 
- ESQUEMA: como (ROL) quiero (algo) para (beneficio)
example: como usuario registrado, quiero loguerme para empezar a utilizar la aplicación

**_ CARACTERISTICAS: _**
Son independientes una de otras, son negociables, valoradas por los clientes y usuarios, estimables, pequeñas y verificables.

**_ PASOS PARA CREAR HISTORIAS DE USUARIO _**
1) Identificar roles
2) Identificar funcionalidades/requerimientos del usuario
3) Escribir historia de usuario
4) Escribir criterios de aceptacion

#### Criterios de aceptacion:

En Ingeniería de Software, los criterios de aceptación son las condiciones que deben cumplirse para que una historia de usuario se considere terminada y aceptada. Se definen antes de empezar a programar, junto con la historia de usuario, y sirven como guía para que el equipo de desarrollo entienda qué espera realmente el cliente o el Product Owner.
Si una HU tiene mas de 6 criterios de aceptacion, considerar subdivir la HU.

PLANTILLA HU:
    ID: Identificador univoco, generalmente de la forma <verbo: acciones que realiza, crear, eliminar, actualizar, consultar,etc><sustantivo: el objeto sobre el cual se realiza esta accion, cliente, pedido, producto, etc> 
    TITULO: Descripcion de la historia de usuario de la forma: Como <rol> quiero <algo> para <beneficio>
    REGLAS DE NEGOCIO: Conjunto de reglas, normas, restricciones, politicas, que condicionan el modo de operacion y son definidas por el dominio (empresa, dueño, gerente, etc).

REVERSO CRITERIOS DE ACEPTACION:
    Escenario 1: titulo del criterio
        Dado <un contexto inicial>,
        Cuando <Ocurre un evento>,
        Entonces <Garantiza uno o mas resultados>
    Escenario N: titulo del criterio
        Dado <un contexto inicial>,
        Cuando <Ocurre un evento>,
        Entonces <Garantiza uno o mas resultados>

Dado = lo que tenemos antes de la acción.
Cuando = lo que sucede al ejecutar la acción.
Entonces = el resultado esperado de esa acción.

**_ Beneficios de la HU _**

Se puede implementar de manera rapida(dias o semanas), necesitan poco mantenimiento, mantienen una relacion cercana con el cliente, permite dividir proyectos en pequeñas entregas, permite estimar facilmente el esfuerzo de desarrollo y es ideal para proyectos con requisitos volatiles o no muy claros.

**_ Limitaciones _**

A tener en cuenta, sin criterios de aceptacion, se puede quedar abierta a distintas interpretaciones haciendo dificil de utilizar, se requiere contacto permanente con el cliente y desarrolladores competentes.

#### HU Épicas

Se denomia Épica a un conjunto de historias de usuario que se agrupan por algun denominador en común. Representa un objetivo alcanzable que nace de la necesidad del cliente, es un objeto que nos aproximamos y esperamos alcanzar algun dia.

* Las épicas suelen abarcar varios equipos de desarrollo
* Recogen normalmente muchas historias de usuario
* Los clientes determinan si eliminan o añaden historias dentro de cada épica
* Una épica sirve para estructurar los temas e iniciativas (objetivos)
* Las épicas también sirven para dar flexibilidad y agilidad al proyecto


## APUNTES EN CLASE ----------------------------------------------

Una historia de usuario no puede NO tener ningun criterio de aceptacion.
Siempre que tenemos una autenticación, tenemos un Log in / Log out. Una autenticacion de x usuario es una pre-condicion NO una regla de negocio.

Un requerimiento(requisito) es la necesidad del cliente de lo que espera del sistema que estamos desarrollando. Tenemos 2 tipos de requerimientos
1) Requerimientos funcionales: es la parte tecnica y desarrollo, lo que el sistema DEBE hacer y lo que NO debe hacer, ante distintas situaciones. Seria el QUE debe realizar el sistema
2) Requerimiento no funcional: caracteristicas NO TECNICAS a respetar a la hora de desarrollar e implementar el software. Es el COMO debe comportarse el sistema

### Ingenieria de requerimiento:

Ingenieria de requerimiento, es el proceso de transformar los requisitos del cliente a una especificacion completo, no ambiguo, consistente y precisa.
Es importante por que, nos permite especificar el proyecto de manera estructurada, mejor calidad y comunicacion del desarrollo de software y lo mas importante evitar rechazos de los clientes.

Estudio de Vialidad:
Teniendo una descripcion resumida de los requerimientos, se evalua si se puede desarrollar o no, en base a: desarrolladores, tiempo, presupuesto, etc.

Validacion != Verificacion
La validacion cumple con las necesidades del cliente, es el software esperado y correcto. Este proceso se realiza con los usuarios.
La verificacion cumple con los requerimientos diseñados y/o escritos, por ejemplo, es la prueba de que una funcionalidad devuelva lo esperado.
