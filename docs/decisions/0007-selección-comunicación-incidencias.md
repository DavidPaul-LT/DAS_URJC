# Selección Comunicación Incidencias

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-11-08

## Context and Problem Statement

Dentro del componente que se ha denominado como "Incidencias" tiene su propia manera de comunicar estas mismas a los receptores necesarios. ¿Qué patrón puede ser de más ayuda para realizar la comunicación?

## Decision Drivers

* RF11 - Existe un componente llamado "Incidencias" que se encarga de notificar a los gestores de rutas de cualquier incidencia ocurrida.

## Considered Options

* 0007-1-Patrón-Observer
* 0007-2-Patrón-Publish-Subscribe

## Decision Outcome

Chosen option: "", because comes out best.

## Pros and Cons of the Options

### 0007-1-Patrón-Observer

El patrón Observer permite añadir un mecanismo por el cual una serie de elementos "suscritos" a un notificador relacionado a un evento reciben actualizaciones del estado de ese mismo evento de parte del notificador.

* Good, because Debido a la naturaleza de los pedidos, es conveniente que tanto los encargados como el cliente sepan qué ha sucedido con el pedido para actuar en consecuencia.
* Good, because Permite una comunicación eficiente debido a que los "suscriptores" no necesitan estar constantemente revisando el estado del evento, sino que se puede comprobar a voluntad.
* Bad, because Los suscriptores se notifican de forma aleatoria, o, es decir, no hay una relación de orden (es una relación de orden indeterminada).

### 0007-2-Patrón-Publish-Subscribe

Los remitentes envían mensjaes no programados a los suscriptores. Es parte del middleware MOM.

* Good, because Tiene buena escalabilidad.
* Good, because Su acoplamiento es suelto, con lo que se puede trasladar fácilmente.
* Bad, because Requiere que se utilice el middleware MOM en la mayoría de los casos, siendo poco conveniente en cualquier otro middleware.
