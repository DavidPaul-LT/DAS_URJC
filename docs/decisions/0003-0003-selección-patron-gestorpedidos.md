# 0003-Selección-Patrón-GestorPedidos

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-10-24

## Context and Problem Statement

Hay que establecer un patrón de diseño que resuelva la problemática de coordinar los microservicios cuya comunicación se centralizan en un componente denominado GestorPedidos.

## Decision Drivers

* RF05 - Se necesita implementar un componente que actúe como intermediario entre Clientes, Pedidos, Repartos e Incidencias.

## Considered Options

* 0001-1-Patrón-Mediator
* 0001-2-?

## Decision Outcome

Chosen option: ""

## Pros and Cons of the Options

### 0001-1-Patrón-Mediator

El patrón Mediator redirige la comunicación directa que tienen los componentes a una colaboración indirecta usando un objeto mediador incluido en el componente GestorPedidos.

* Good, because La comunicación indirecta, centralizada en GestorPedidos, cumple con el princio de responsabilidad única haciendo que el componente mediador sea más fácil de mantener.
* Good, because Se reduce el apoplamiento innecesario de componentes evitando futuros problemas para mantener y escalar esos componentes.
* Bad, because Una caída del componente GestorPedidos podría suponer una pérdida importante de comunicaciones entre componentes.
