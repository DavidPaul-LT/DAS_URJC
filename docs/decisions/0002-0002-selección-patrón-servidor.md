# 0002-Selección-Patrón-Servidor

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-10-24

## Context and Problem Statement

Una vez seleccionada y aplicada la estructura externa del servidor, es el momento de seleccionar el patrón de conexión al servidor. ¿Qué patrón de comportamiento es el más útil y óptimo para la tarea?

## Decision Drivers

* RF01: Se pretende reemplazar la arquitectura monolítica con la que contaba el sistema por una basada en microservicios.
* RF04: El servidor deberá tener un gateway con conexión HTTP/REST

## Considered Options

* 0002-1-Solo-Gateway
* 0002-2-Gateway-con-Service-Discovery

## Decision Outcome

Chosen option: "", because comes out best.

## Pros and Cons of the Options

### 0002-1-Solo-Gateway

Únicamente se implementa un gateway al servidor en general.

* Good, because Es simple y fácil de implementar.
* Good, because Ofrece una interfaz uniforme.
* Good, because El acceso es único, con lo cual aplicar políticas se vuelve más sencillo (Solicitudes, Seguridad, etc.)
* Bad, because Su simplicidad implica que únicamente se encontrará el gateway, con lo cual se pierden funcionalidades como comprobar el estado de los microservicios.

### 0002-2-Gateway-con-Service-Discovery

El Gateway además tendrá acceso a un Server/Client Service Discovery (S/C SD, o "Descubrimiento de Servicios Cliente/Servidor), lo que conlleva que se podrá comunicar el estado de los microservicios asociados al servidor.

* Good, because El gateway estará informado de los servicios que funcionan y los que no para comunicarlo si es necesario.
* Good, because En caso de que un nodo de microservicio esté fuera de servicio o en mantenimiento, será comunicado a través del Service Discovery.
* Good, because La implementación tiene los beneficios del Gateway y se complementan con el Service Discovery.
* Bad, because La implementación del Service Discovery toma tiempo y debe adaptarse a los nodos. Esto supone un aumento en el esfuerzo requerido para implementar el Gateway.
