# Relaciones en Casos de Uso

📘 APUNTE RESUMIDO DE RELACIONES EN CASOS DE USO (UML)
* ✅ 1. Asociación -----------------------------------------------------------------------------

Definición:
Relación que indica que un actor participa o interactúa con un caso de uso.

Uso:
Actor → Caso de uso
Nunca entre casos de uso.

Idea clave:
➡ Quién realiza o inicia el caso de uso.

* ✅ 2. Include (<<include>> / uses) -------------------------------------------------------------

Definición:
Un caso de uso A incluye a otro caso de uso B como un paso obligatorio dentro de su flujo.

Cuándo usarlo:
Cuando un CU siempre necesita ejecutar otro CU.
Para evitar redundancia y reutilizar partes comunes.

Idea clave:
➡ Obligatorio. A no puede ejecutarse sin B.
➡ B es parte del flujo principal de A.

Ejemplo mental:
“Registrar usuario” incluye “Validar datos”.

* ✅ 3. Extend (<<extend>>) -----------------------------------------------------------------------

Definición:
Un caso de uso B agrega o modifica comportamiento del caso de uso A, pero solo bajo una condición.

Cuándo usarlo:
Para variaciones opcionales.
Para comportamientos condicionales, alternativos o excepcionales.
El caso de uso base funciona solo, sin el extendido.

Idea clave:
➡ Opcional. Solo ocurre si se cumple una condición.
➡ B depende de A; B no puede ejecutarse sin A.

Ejemplo mental:
“Finalizar compra” puede extenderse con “Aplicar descuento” si el cliente es VIP.

* ✅ 4. Herencia (Generalización) ---------------------------------------------------------------------

Definición:
Un caso de uso o actor especializado hereda el comportamiento de un caso de uso o actor más general.

Cuándo usarlo:
Cuando existen variantes del mismo comportamiento.
Para agrupar casos similares y evitar duplicación.

Idea clave:
➡ “Es un tipo de…”
➡ Los casos de uso hijos heredan los pasos comunes del padre.

Ejemplo mental:
“Realizar pago” generaliza → “Pago con tarjeta” y “Pago con transferencia”.