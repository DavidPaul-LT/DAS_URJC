# Especificación Pasarela Pago

* Status: accepted
* Deciders: Ángel, Cristian
* Date: 2023-11-08

## Context and Problem Statement

Dentro del servidor se podrán realizar pagos para los pedidos que un usuario efectue. ¿Qué pasarela de pago se considera más efectiva a la hora de realizar los pagos?

## Decision Drivers

* RF10 - Existe un componente denominado "Pagos" que se basa en el empleo de una pasarela de pago externa que lleve los pagos.

## Considered Options

* 0006-1-Paypal
* 0006-2-Stripe
* 0006-3-Amazon-Pay

## Decision Outcome

Chosen option: "0006-2-Stripe", because Beneficia a la compañía.

### Positive Consequences

* La compañía goza de beneficios.

## Pros and Cons of the Options

### 0006-1-Paypal

La pasarela de pago más conocida en el internet goza de una gran reputación.

* Good, because La integración y la gestión es simple.
* Good, because Transferencias (casi) inmediatas.
* Good, because Seguridad abundante.
* Bad, because Debido a que se espera que funcione correctamente puede suponer comisiones más altas.

### 0006-2-Stripe

Esta pasarela es otra de las más conocidas y trabaja con millones de empresas (Business oriented).

* Good, because Al ser Business oriented, se puede gozar de ciertos beneficios como ser compatible con la mayoría, si no todas, de las tarjetas bancarias.
* Good, because Su API es integrable fácilmente.
* Good, because Es una pasarela más barata, con lo que supone menos gastos generales.

### 0006-3-Amazon-Pay

Es la pasarela de pago de la empresa más importante del mundo actualmente.

* Good, because Se pueden habilitar TODOS los métodos de pago para que no haya problemas a la hora de realizar transacciones.
* Good, because Integra automaticamente los datos del cliente, lo que quiere decir que no habrá que incluirlos de nuevo si el cliente decide que la pasarela lo recuerde, haciendo el proceso algo más ameno.
* Bad, because Puede llegar a ser una pasarela cara puesto que la comisiones tienden a ser altas.
