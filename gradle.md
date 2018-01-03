# Gradle

Build Tools

Gradle permite construir cosas simples de una forma hyper-personalizada

## Declarativo vs Imperativo

Ant y Maven dejan un legado.

Ant build es imperativo, paso vs paso. Un XML super largo.

Maven es declarativo, revolucionario, simplifica las cosas.

Gradle es declarativo, supuestamente la dirección correcta.

## Convenciones vs adaptabilidad

Un build declarativos tiene una 'opinion'. Esto es, un workflow. Una forma de hacer las cosas. Una intención.

Tiene sentido, pero muchas veces ese workflow se ajusta muy dificil a la forma de trabajar.

El workflow de un framework o un build tool esun concepto dificil de describir para un principiante.

Tal vez escriba un ejemplo más adelante. Yo consideraría a Glut un framework, por ejemplo.
Tiene un workflow bien definido. Lo inicializas, inicialisas la ventana, inicializas la funcion principal y ya.

Si tu juego necesita otras cosas, tendrás que jugar en torno a ese workflow, restando flexibilidad.

## Intro a la intro de Gradle

Realmente sigo sin entender muy bien un build tool. Tal vez sería mejor averiguar sobre Ant y sobre Maven, pero bueno.

Remontemonos a las épocas pre-GUI. Incluso así, un programa en c++ tienes que compilarlo y luego linkearlo a algo.

Al parecer es algo similar con Java.

Oh, ya entiendo. Mi odio a Java es por el curso de programación de la universidad de Standford.

Nunca logré que Eclipse funcionase. 

Y odié con toda mi alma lo poco accesible que es la programación para los principiantes.

Y la falta de un mapa. 

Dios. 

Qué les cuesta decir que primero estudiaremos los conceptos y luego nos preocupamos por la parte fea, el que funcione en una computadora.

Sobre todo esas páginas donde tienes que arrastrar bloques.

Ugh.

## Intro a Gradle

Gradle tiene una unidad central: Task. O tarea.

Al parecer Gradle es un programa que se encarga de todo lo que no nos gusta. 

Necesito una comparación entre lo que hace Gradle, Ant, Maven y la forma manual.

Task es un objeto... ¿what?

```bash

$ mkdir tasks
$ cd tasks
$ touch build.gradle
#$ mate build.gradle
$ nano build.gradle
$ gradle

```
En build.gradle...

```
/*
 * - A task is an object
 * - A Gradle build is... a program
 */

task helloWorld 
```

Al ejecutar gradle en la consola... ¿no pasa nada?

Ah, al tipo le demora por el disco duro externo jajaja

lifecycle messages

Entiendo ahora un poco... pero, ¿no puedo hacer esto con bash?

Tal vez sehace muy complicado hacerlo con bash...

COMMAND LINE SUGAR SYNTAX HOLLY SHIT

JAMAS SE ME HUBIESE OCURRIDO

ES SUPER GENIAL

Una Tarea es un objeto... un objeto ya creado programado dentro de Gradle

Eso significa que tiene una API
 
Al inicio pensé que el API era algo que definíamos nosotros.

Luego me di cuenta que el tipo esta refraseando lo evidente...

Ese doLast (¿también se puede resumir esto? Tipo dL), o el dependsOn... eso es el API

Y la documentación... viene con cada descarga de Gradle. 

Gradle Build Language Reference = DSL = Domain Specific Language Reference

¿Cómo lo abro? No sé

Un día de entrenamiento para leerse la API.

Uh, hay una forma apropiada de pensar sobre las capas de abstracción de Gradle.

Esto es algo que no me había puesto a pensar mucho, que incluso dentro de los lenguajes de programación hay varios niveles de abstracción... tiene sentido.

Nos piden que pensemos siempre en funciones u objetos, tenemos que estar saltando de un nivel a otro.

En fin, el ejemplo enterior era super bajo nivel... e imperativo

## Un nivel más

19:20, Gradle construye un arbol dirigido aciclico (un arbol, duh), y de esa forma no repite tareas aunque la especifiques...

Lo cual también te impide las recursividades... A depende de B y B depende de A. Aww.

Si tratas de hacer eso el build fallará.

Esto ocurre en la fase de configuración... ¿Gradle tiene un pipeline? O workflow... más palabras malas.

dependsOn es un collection

domain specific extension of groovy (groovy DSL)

= y << funcionan relativamente diferente, uno asigna y otro añade

Trata de que todo sea declarativo y que se pueda leer bien

Ohhh kernel level lock en discos externos... ¿los discos externos tienen un kernel?

Me quedé en 24:00


