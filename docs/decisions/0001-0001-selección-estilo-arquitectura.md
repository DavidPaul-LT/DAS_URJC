# 0001-Selección-Estilo-Arquitectura

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-10-18

## Context and Problem Statement

Hay que establecer un estilo arquitectónico para el sistema de la compañía de productos alimenticios. Dado que se quiere transformar la arquitectura monolítica de la compañía, el objetivo de esta decisión es elegir entre los modelos arquitectónicos existentes cuál es la mejor opción.

## Decision Drivers

* RF01 - Reemplazar la arquitectura existente del sistema Se pretende reemplazar la arquitectura monolítica con la que contaba el sistema por una basada en microservicios.
* RF02 - División del sistema en componentes El sistema incorporará los componentes de clientes, pedidos, repartos, rutas de reparto, estadísticas, incidencias y pagos.
* RF03 - Creación de un componente para la gestión de los pedidos Es necesario incorporar un componente que sirva de intermediario entre los componentes de clientes, pedidos, reparto e incidencias.

## Considered Options

* 0001-1-Arquitectura-Cliente-Servidor-tres-capas
* 0001-2-Arquitectura-Cliente-Servidor-dos-capas
* 0001-03-Arquitectura-por-capas

## Decision Outcome

Chosen option: ""

## Pros and Cons of the Options

### 0001-1-Arquitectura-Cliente-Servidor-tres-capas

El sistema se repartirá en microservicios y empleará la arquitectura Cliente - Servidor, bajo la cual, un componente intermediador (segunda capa) se encargará de procesar las peticiones de los componentes cliente ( primera capa). La arquitectura contará con una tercera capa que gestiona el acceso a las bases de datos.

* Good, because El acceso a las funcionalidades de un componente cliente se realiza a través de un componente servidor que velará por la gestión segura de las diversas peticiones de los clientes.
* Good, because Los componentes cliente compartirán los recursos del servidor común, lo que facilita el mantenimiento y la escalabilidad del sistema.
* Bad, because Una caída del servidor podría suponer una pérdida importante de comunicaciones entre componentes, lo que inutilizaría el sistema.

### 0001-2-Arquitectura-Cliente-Servidor-dos-capas

Frente al modelo propuesto en la opción anterior, esta arquitectura C/S se limitaría a procesar las peticiones de los clientes y se abstendrá realizar accesos a las bases de datos, dado que relevará esta responsabilidad a otros componentes.

* Good, because Conserva gran parte de las ventajas expuestas anteriormente de arquitecturas C/S mientras mantiene las bases de datos accesibles en caso de inoperancia del servidor central.
* Bad, because Fuerza diversificar las relaciones que guardan los componentes con las bases de datos complicando el mantenimiento y la escalabilidad del sistema.

### 0001-03-Arquitectura-por-capas

El sistema se divide en diversas capas: una de intermediación, otra de lógica de negocio y otra de utilidades para los clientes PC y móvil.

* Good, because La separación en capas favorece la creación de una capa de mensajería (Gestión pedidos) que ayuda a que el procesamiento se realice en varios nodos que podrían ayudar a diversificar la carga evitando así la necesidad de usar un servidor centralizado.
* Bad, because Puede suponer añadir complejidad adicional al sistema, podría entorpecer los esfuerzos por hacer grandes cambios estructurales.
