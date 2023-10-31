# 0003-Selección-Patrón-GestorPedidos

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-10-24

## Context and Problem Statement

Hay que establecer un patrón de diseño que resuelva la problemática de coordinar los microservicios cuya comunicación se centraliza en un componente denominado GestorPedidos.

## Decision Drivers

* RF03 - Se necesita implementar un componente que actúe como intermediario entre Clientes, Pedidos, Repartos e Incidencias.

## Considered Options

* 0003-1-Patrón-Mediator
* 0003-2-Patrón-Broker

## Decision Outcome

Chosen option: ""

## Pros and Cons of the Options

### 0003-1-Patrón-Mediator

El patrón Mediator redirige la comunicación directa que tienen los componentes a una colaboración indirecta usando un objeto mediador.

* Good, because La comunicación indirecta, centralizada en GestorPedidos, cumple con el principio de responsabilidad única haciendo que el componente mediador sea más fácil de mantener.
* Good, because Se reduce el acoplamiento innecesario de componentes evitando futuros problemas para mantener y escalar esos componentes.
* Bad, because Una caída del componente GestorPedidos podría suponer una pérdida importante de comunicaciones entre componentes.

### 0003-2-Patrón-Broker

El patrón Broker conecta varios componentes a un mismo módulo para posteriormente recibir información a través de él de parte de los demás componentes y realizar acciones en ellos.

* Good, because Transforma los mensajes en el lenguaje debido a la hora de comunicarse entre servicios.
* Good, because Divide los mensajes que le llegan de los diferentes servicios, los descompone en diferentes partes, y luego los envía al receptor debido para posteriormente juntarlo de vuelta y devolverlo al remitente. La transmisión se vuelve más rápida de esta forma.
* Bad, because La vulneración del módulo Broker puede causar un problema muy grande de seguridad y comunicación entre servicios causando en el compromiso del mismo servidor.
* Bad, because La conexión entre módulos debe ser fiable pues la pérdida de una de las partes del mensaje puede causar retraso a la hora de comunicar distintas acciones. Es vital que los mensajes lleguen a su debido tiempo.
