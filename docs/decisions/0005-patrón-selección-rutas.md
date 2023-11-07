# Patrón Selección Rutas

* Status: proposed
* Deciders: Ángel, Cristian
* Date: 2023-11-07

## Context and Problem Statement

El componente de rutas precisa de 2 implementaciones de algoritmos de optimización basados en la demora del camión, las carreteras, entre otros factores. Es importante determinar cuál es su ámbito de aplicación y manejo de los mismos. ¿Qué patrón se utilizará para este propósito?

## Decision Drivers

* RF08 - Existe un componente llamado "Rutas" que se encarga de determinar las rutas que realizan los camiones al realizar sus repartos.
* RF09 - El componente "Rutas" hará uso de dos algoritmos de optimización.

## Considered Options

* 0005-1-Patrón-Strategy
* 0005-2-Patrón-Command

## Decision Outcome

Chosen option: "", because comes out best.

## Pros and Cons of the Options

### 0005-1-Patrón-Strategy

Se basa en un diseño de comportamiento que ayuda a discernir entre qué algoritmo dentro de una familia concreta de ellos resulta una mejor elección para realizar una tarea en concreto.

* Good, because Los algoritmos son intercambiables.
* Good, because Se pueden aislar detalles concretos de la implementación de los algoritmos.
* Bad, because Hay que tener en cuenta el factor que elige la estrategia a usar. Si esto está mal seleccionado, el servicio sufre de demoras en la ruta.
* Bad, because Si se utilizan pocos algoritmos, el patrón se ve obsoleto puesto que es probable que la implementación del patrón complique innecesariamente el programa, sobre todo si los algoritmos rara vez cambian.

### 0005-2-Patrón-Command

Es un patrón de diseño de comportamiento que se basa en la similitud a una superclase que conecta a unas clases más pequeñas y dicta la forma de implementar un algoritmo más genérico delegando la responsabilidad de concretar el algoritmo a las clases herederas.

* Good, because Si la clase ancestra es una desarrollada, el algoritmo generado tiene muy pocos cambios que atender y, por tanto, es sólida entre las distintas elecciones que ofrezcan las hijas como solución.
* Bad, because Si el padre es escricto de más puede delimitar la libertad de los hijos, haciendo que pierdan su sentido.
* Bad, because La plantilla del padre se puede volver más compleja cuando más grande sea. Los hijos, en consecuencia, se vuelven más difíciles de escalar.
