---
templateKey: about-page
title: Guías
---
# 

# IncreaseCard

Existen varias APIs a las que podrás consultar en base a la información que estés precisando.

**API de Payments**\
\
Esta api te da toda la información de las liquidaciones que las procesadoras te emitieron, es decir, las clearings diarias. Dentro de cada Clearing, puedes filtrar para obtener o no el detalle de los movimientos (movements) que la componen , es decir, el detalle de las transacciones, deducciones y contracargos.

> Si vas a automatizar la búsqueda de payments, siempre te recomendamos hacerlo buscando todos los días por fecha de creación el día anterior. Esta es la única forma de asegurarse no perder nunca una liquidación ya que alguna tarjeta podría agregar una liquidación con fecha de pago hoy el día de mañana y si buscas solo por fecha de pago nunca llegarías a ese dato.

**Cómo puedo controlar la clearing?** Podés validar según el campo “is_balanced”. Este booleano te indica si en la clearing se cumplen los siguientes puntos:

* Suma del monto de las transacciones (movements) = Total presentado
* Suma de descuentos (movements) = Total de descuentos
* Total presentado - Total descontado = Total Earn

> Es importante que valides siempre **la versión de los payments**(liquidaciones) antes de registrarlos en tu sistema. Puede suceder que una liquidación tenga una actualización en Increase. Si eso sucede y esa liquidación es reprocesada, entonces se generará una nueva liquidación con un payment_id diferente, pero que hace referencia a la misma liquidación bancaria. Debes validar si es la misma liquidación bancaria a partir de los siguientes 4 campos:\
>
> * Clearing number
> * Payment date
> * Provider
> * Nro de establecimiento

También podrás buscar un payment en específico utilizando el ID de increase. <Ver ejemplo>

**API de Movements**\
Esta api te da toda la información de los movimientos (movements) que componen una liquidación,es decir, el detalle de las transacciones, deducciones y contracargos.

Puedes hacer una consulta por un período, o mismo buscando un movimiento en específico según el ID de Increse

**Api de Chargebacks**\
 Esta API te da toda la información de contracargos que hayas tenido en las liquidaciones. A qué llamamos contracargos? A todos los reversos de la tarjeta, que pueden ser por cualquiera de los siguiente 4 motivos: devoluciones, desconocimientos de compra (contracargos), ajustes, o rechazos.

Puedes obtener los contracargos de un período, o puedes buscar un contracargo en específico según el ID de Increase.

**API de Impuestos**\
Acá te presentaremos todos los impuestos sumarizados de determinado período.
