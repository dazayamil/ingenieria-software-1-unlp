# Ingenieria de Software 1 2025 

## Clase 1 - Teoria:

Temas a desarrollar:
1) Conceptos de Ingenieria de Software.
2) Requerimientos.
3) Modelo de proceso.
4) Calidad de software.

### ¿Qué es Software?

El software es el proceso de diseñar y/o desarrollar un sistema de computo para resolver una necesidad. La IEEE dice, el software son instrucciones, procedimientos, reglas, documentacion y datos asociados que forman parte de las operaciones de un sistema de computo.

El software no se fabrica ni se desgasta, se desarrolla y la unica forma de que muera, es cuando se deja de usar. Con el paso del tiempo, la tasa de fallos en el hardware es creciente, en cambio, el software tiene una  tasa de fallos menor y más estable, la unica forma de generar puntos de fallos es debido a requerimientos del cliente, cambios en el desarrollo, uso de nuevas tecnologias, formas, metodologias, etc.

*El problema no esta en el tiempo de operacion, sino en los cambios*

### Tipos de producto de Software

1) Genericos: Son sistemas creados por organizaciones o desarrolladores que posterior a su creacion, lo venden en el mercado.
2) Personalizados: Son sistemas creados para un cliente en particular.

En la actualidad, se esta desarrollando software con tipos genericos como base y posteriormente, se pasa al personalizado.

**_Software Libre_**

Tal como indica Richard Stallman, software libre comprende 4 libertadres:
1) Libertar para ejecutar el programa en cualquier sitio, con cualquier proposito y para siempre.
2) Libertad para estudiarlo y adaptarlo a nuestras necesidades.
3) Libertad para redistribucion, de modo que nos permite colaborar
4) Libertad para mejorar el programa y publicar mejoras.

**Computacion Ubicua:este termino se usa cuando diseñamos software en nuestro propio entorno, for example: heladeras, lavaropas, etc.**

### ¿Qué es la Ingenieria de Software?

Es la disciplina de la ingenieria, donde se emplean teorias, metodos y herramientas que comprende todos los aspectos de la produccion de software, desde las etapas iniciales, su evolución y el producto final, es decir, en funcionamiento.

**_ Como se forma el desarrollo de software en cuanto a participantes: _**
1) Gerentes ejecutivos (dueños del producto)
2) Gerente de proyecto (lider de equipo)
3) Profesionales especializados(DB, desarrolladores, tester, etc)
4) Cliente
5) Usuario finales

### Caracteristicas de un ingeniero/a de software:

* Dominar aspectos tecnicos
* Habilidades requeridas para entender el problema
* Diseñar la solucion a desarrollar
* Aspecto humanos
* Sentido de responsabilidad individual

Responsabilidad profesional y etica: Los IS deben aceptar responsabilidades mas amplias que las responsabilidades tecnicas, for example, no usar su capacidad y habilidad de forma deshonesta. Tener confidencialidad con los empleados y clientes, no realizar algun tipo de competencia en base a los conocimientos de los empleados, conocer los dereches sobre las patentes y copyright, no usar de forma inadecuada las computadoras.

### Tecnicas de comunicación:

Como ingeniero/a de software, debo comprender que al iniciar un proyecto debo entender y saber lo que el usuario QUIERE, COMO LO QUIERE, CUANDO Y PORQUÉ, todo esto se logra con la comunicación.

La *comunicación* es la base para la obtención de los requerimientos del cliente, pero tambien es la principal fuente de error, por no tener una comunicación clara y detallada.
NECESIDAD = REQUERIMIENTO = REQUISITO

Un *requerimiento* es una caracteristica solicitada del cliente, empleado en el sistema desarrollado para cumplir y/o satisfacer la necesidad del cliente. Las fuentes de requerimientos son: Documentación, Stakeholders, Espec. sistemas similares.

*Stakeholder* -> Persona o grupo que es afectado por el sistema de forma directa o indirectamente, los mismos puede ser, usuarios finales, ingenieros, gerentes, etc.

### Puntos de Vista:
1) Interactuadores: Representa a las personas u otros sistemas que interactúan directamente con el sistema, puede influir en los requerimientos del sistema de algun modo(STAKEHOLDER).

2) Indirecto: Representa a los stakeholders que no utilizan el sistema pero influyen de alguna forma en los requerimientos.

3) Dominio: Representa a las caracteristicas, restricciones y/o reglas del dominio que influyen en los requerimientos.

### Elicitacion de requerimientos:

A= Es el proceso de adquirir("eliciting") todo el conocomiento relevante necesario para producir un modelo de los requerimientos de un dominio de problema. La elicitacion de requerimientos, es una actividad principalmente de caracter social y no tecnologica.

B= Es el proceso de obtener, descubrir, recopilar y entender las necesidades, expectativas y restricciones que los clientes y usuarios finales tienen respecto al sistema que se va a desarrollar.

*Problemas de comunicación*
* Dificultad para expresar claramente las necesidades.
* No entender como la tecnologia los puede ayudar.
* Interes distintos en el sistema a desarrollar.
entre otras

*Tecnicas de elicitacion*
Recopilacion de informacion:
1) Metodos discretos: muestra de documentacion, formularios y los datos existentes; investigacion y visitas al lugar; observacion al ambiente de trabajo

Este tipo de metodo es "menos perturbador" que otras formas de ilicitacion (obtener) requerimientos. Se consideran insuficientes para recopilar información. Podemos observar tres puntos importantes: muestreo de la documentacion general y datos existentes, investigacion y visitas al sitio y observacion del ambiente de trabajo.

2) Metodo interactivos: cuestionarios, entrevistas, planeacion conjunta de requerimientos (JRP o JAD); lluvia de ideas. La base de este metodo es hablar con las personas en la organizacion y escuchar para comprender.

JRD = Planeacion Conjunta de Requerimientos: Proceso donde se juntan un grupo de personas con el proposito de analizar problemas y definir requerimientos.
- VENTAJAS: Ahorro de tiempo, usuarios involucrados, desarrollos creativos.
- DESVENTAJAS: Dificil organizar los horarios de todos, complejo encontrar un grupo integrado y organizado.

BRAINSTORMIN = Lluvia de Ideas: tecnica por el cual se reunen varios participantes generando ideas sin ningun analisis, ni guion, compartiendo pensamiento de manera global en un tiempo corto hasta que se agoten las ideas. Este proceso motiva o despierta en otros más ideas creativas, cuantas más ideas se sugieren, mejores resultados se conseguirán.

FASES: 
1) Descubrir hechos (problematicas - requerimientos)
2) Producir ideas (soluciones - opciones - implementacion de HU con requerimientos ya definidos)
3) Descubrir soluciones (desarrollar las soluciones y/o opciones elegidas en la fase 2)

2_A) CUESTIONARIO: Documento que permite al analista recabar informacion y opiniones de los encuestados. Con esto podemos lograr, recopilar hechos de gran cantidad de personas, detectar un sentimiento generalizado y problames entre usuarios y cuantificar respuestas
- VENTAJAS: respuesta rapida, economico, anonimos, estructurado de facil analisis
- DESVENTAJAS: numero bajo de respuestas, no responde a todas las preguntas, preguntas rigidas, no se puede realizar un analisis corporal, dificiles de preparar.

- TIPOS DE PREGUNTAS:
* Abierto: son las que dejan la posibilidad de tener mas de 1 respuesta
* Cerradas: limitan las opciones de respuesta en una sola (si o no)

*LO QUE SE OBTIENE: ACTITUD DE LAS PERSONAS QUE DICEN LO QUE QUIEREN, LO QUE CREEN QUE ES VERDAD, LO QUE REALMENTE HACEN Y CARACTERISTICAS DE LAS PERSONAS O COSAS*

Debemos usar cuestionarios cuando: las personas estan dispersas geograficamente, muchas personas involucradas, querer reconocer opiniones y problemas generales.

2_b) ENTREVISTA: Esta tecnica, es empleada en una interaccion con las personas de forma presencial, cara a cara, se basa en un formato de preguntas y respuestas, con el fin de conocer las opiniones y sentimientos del entrevistado.

- VENTAJAS: el entrevistado se siente parte, retroalimentacion, adaptacion de preguntas, informacion no verbal.
- DESVENTAJAS: costosas, tiempo y recursos humanos, no aplicable a distancia

- TIPO DE ENTREVISTAS:
* Estructuradas (cerradas): conjunto especifico de preguntas, pregunta puntual.
* No Estructuradas (abiertas): se lleva a cabo un tema general, sin preparacion de preguntas.

- TIPOS DE PREGUNTAS EN ENTREVISTAS:
* Abiertos: respuestas de cualquier manera.
* Cerrados: respuestas directas, cortas o de seleccion.
* Sondeo: obtener mas detalle sobre un tema puntual.

*SE OBTIENE: OPINIONES, OBJETIVOS, PROCEDIMIENTOS INFORMALES Y SENTIMIENTOS*

