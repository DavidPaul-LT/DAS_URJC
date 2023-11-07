# Selección Tipo Middleware

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-11-07

## Context and Problem Statement

En la implementación del servidor en UML, existe un "middleware" que conecta las bases de datos con el propio servidor.¿Qué clase de middleware sería el óptimo y válido para llevar a cabo la tarea de comunicar el servidor y las bases de datos de forma eficiente?

## Decision Drivers

* RF05 - La compañía dispone de dos bases de datos separadas: Clientes y Pedidos.
* RF06 - En la base de datos de Clientes, se almacenan los datos de los clientes y los pagos realizados.
* RF07 - En la base de datos de Pedidos, se almacenan todos aquellos datos desvinculados de la base de datos de Clientes.

## Considered Options

* 0004-1-Middleware-de-datos
* 0004-2-Middleware-orientado-a-mensajes
* 0004-3-Middleware-intermediario-peticion-de-objetos

## Decision Outcome

Chosen option: "", because comes out best.

## Pros and Cons of the Options

### 0004-1-Middleware-de-datos

Un middleware de datos (Data Access Middleware, o DAM) funciona a modo de servidor intermediario entre el paquete de lógica de negocio y la(s) base(s) de datos.

* Good, because Las respuestas ofrecidas son por el middleware mismo. Son fácilmente adaptables a varios formatos.
* Good, because El middleware permite filtrar las solicitudes enviando bien peticiones síncronas o asíncronas a las bases de datos. Esto permite que, para datos en los que importa el seguimiento a tiempo real del acceso de los componentes a la base de datos, mantenga una comunicación síncrona, mientras que para cualquier otro caso menos exigente se pueda mantener una comunicación asíncrona.
* Bad, because Puede ser difícil de implementar un sistema que maneje tanto de forma asíncrona como síncrona las comunicaciones de la lógica de negocio con las bases de datos. Supone un esfuerzo superior y está expuesto a fallos más graves en el entorno de implementación debido a su complejidad.

### 0004-2-Middleware-orientado-a-mensajes

El middleware orientado a mensajes (Message Oriented Middleware, o MOM) ayuda a gestionar de forma eficiente el direccionamiento que los componentes tienen en los mensajes que se envían.

* Good, because En este caso, se realiza por el interés concreto de los componentes para solicitar datos de las bases de datos.
* Good, because El middleware es un componente fácilmente diversificable y/o distribuible lo cual ayuda a la acoplabilidad de los componentes del servidor y ayuda a evitar sobrecargas dentro del mismo.
* Bad, because El procesamiento de los mensajes en varios nodos distribuidos puede llegar a ser mal gestionado por el middleware y, por ende, ser un método más lento de comunicar mensajes de la lógica de negocio con las bases de datos.

### 0004-3-Middleware-intermediario-peticion-de-objetos

El middleware intermediario para solicitudes de objetos (Object Request Broker Middleware, u ORB) es de gran ayuda para la resolución de solicitudes a las bases de datos por parte de los componentes dado que estas solicitudes se pueden realizar sin el conocimiento del establecimiento de las bases de datos, sino que se realiza con un componente intermediario que conoce su ubicación y las gestiona de manera debida para otorgar información a los solicitantes.

* Good, because La encapsulación que el middleware ORB ofrece es muy buena para la seguridad en el acceso a las bases de datos puesto que estas no se verán expuestas, sino que la información pasará primero por este middleware, actuando como un filtro o un embudo.
* Bad, because Si el middleware se encuentra sobrecargado o fuera de servicio las bases de datos se encontrarán completamente fuera de servicio, no importa como estén estas.
