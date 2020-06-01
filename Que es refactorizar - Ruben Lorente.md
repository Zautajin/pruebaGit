# Que es refactorizar?

Nombre a una colección de pequeñas técticas que sirven para mejorar el código que ya existe (escrito y en funcionamiento).

Son pequeños "tips", que se centran cada uno en un aspecto concreto, como pequeñas herramientas, llamadas "métodos".

En resumen, refactorizar es agilizar y optimizar el código **ya**  **escrito**, por el programador, hacer más cosas en menos tiempo por el programador

## La caja de herramientas

Diferentes herramientas para cada caso, no tienen un orden concreto, la que convenga en el momento concreto, ya que hay más de 75, aunque se recomienda aprender el uso de unas 30 "básicas" o de uso general.



# Por que y cuándo usar refactorización

Refactorizar no es estético, ya que no tiene sentido, ni buscar errores ni añadir características, pero mejorará encontrar o mejorar estos aspectos en el futuro.

Mejorar la estructura del código para un futuro mantenimiento o mejora del mismo.

Si un código no va a necesitar ser ampliado o mantenido, no es necesaria una refactorización del código.

En cambio, si sabemos que estamos creando un código que será ampliado o mantenido en el futuro, tendremos que considerar en la refactorización, pensando en el futuro del código y del programador.

En equipo, refactorizar es una buena excusa para que otros ojos repasen nuestro código, ya que  cuatro ojos ven más que dos.

No debemos repasar línea a línea, si no verlo más global y comprobar si nuestro código tiene "mal aspecto".



# El código con mal aspecto para la refactorización

Al igual que al leer un texto narrativo mal escrito una persona puede arrugar la nariz, un código puede provocar lo mismo a un programador que ve de un vistazo que el código está mal, no línea a línea, si no en general.

Por ejemplo:

- Código repetido
- Métodos largos
- Demasiados comentarios

<u>¿Quién dice que está bien o mal?</u>

Martin Fowler, con su libro *Refactoring improving the Design of Existing Code*, un catálogo de técnicas de refactorización.

*www.refactoring.com* - Una buena web con ejemplos a seguir aceptada por toda la comunidad.



# Pruebas automatizadas en la refactorización

### Realización de pruebas automatizadas

Al cambiar el código se corren riesgos, para probar nuestro código existen herramientas que automatizan estas pruebas:

- JUnit en Java
- NUnit en .NET
- RSpec en Ruby

Antes de nada, habrá que hacer un pase de pruebas, después refactorizar, y luego volver a comprobar que todo funciona como al principio.

Nada es infalible, así que mejor probar y testear las veces que sea necesarias, nunca guiarse por la intuición.



# La refactorización de extracción de método

Las técnicas de refactorización se pueden agrupar en:

- Nivel de método
- Nivel de clase
- Nivel de comunicación entre clases

Hay que preguntarse diferentes cosas, como si está bien nombrado, bien separado...

Extraer Método: Extraer líneas a un método por separado, aunque parezca más largo, se acaba trabajando de una manera más limpia y reutilizable.



# Usando IDE en el método extractor para la refactorización

En muchos IDEs tienes menús específicos para refactorizar, con en Eclipse.

Para extraer un método, seleccionas unas líneas de código que quieras extraer, y le das a Extract Method.

Así, el propio IDE genera el código y el método dentro del código.

Esto facilita la labor de refactorización por parte del IDE.



# Método de refactorización en línea

Muchas veces podemos simplificar el código eliminando métodos secundarios que son fácilmente substituibles y se pueden introducir en el propio código base, sin tener que extraer un nuevo método, ya que no añade ningún beneficio.



# Refactorización que quita temporales

Se desaconseja el uso de variables temporales, ya que las VT aumentan la tentación de escribir métodos más largos.

Debemos comprobar si nuestro código aceptaría una palabra clave, creando un método para mejorar su legilibilidad.



# Refactorización que añade temporales

Hay algunas variables que se aceptan de manera temporal, como las divisorias.

Si una variable se repite, aunque sea con diferentes operaciones, es recomendable crear variables con nombres significativos, que se expliquen, para aclarar el código y su uso.

Para evitar líneas de código múltiples, se pueden simplificar operaciones en métodos separados.



# Refactorización moviendo métodos

Empezaremos refactorizando con los métodos de extracción o reduciendo el numero de variables temporales.

La refactorización más común es la de *Refactorización moviendo métodos*.

Básicamente, es mover un método de una clase, en otra.

<u>¿Cuándo debe hacerse?</u>

Si un método tiene más referencias a otra clase, se crea lo que se llama "envidia de métodos", que es cuando un/os métodos piden más información a una clase que a la que está.

<u>¿Cómo se mueven?</u>

- Escanea el código
- Comprueba la superclase o la subclase (los impactos en el código anterior o posterior)
- Crea el nuevo método y renombrarlo si fuera necesario
- Copia el código
- Reemplaza las llamadas originales

<u>Datos adicionales</u>

- Hay que estar seguro de que los datos se llamen de la misma manera
- Si está en la clase equivocada, pero no existe una clase apropiada, utilizaremos el método de Extraer Clase
- Si se da la "Envidia de Características"



# Refactorización de extraer clases

Las clases irán creciendo conforme el proyecto vaya avanzando, hasta a veces aceptarán cosas que originalmente no estaban diseñadas para hacer.

Entonces es recomendable identificar los datos que parece que "sobren" y extraerlos en otra clase, haciendo luego las llamadas correspondientes.

A veces ocurre lo contrario, así que si se puede, otra clase lo absorberá siempre que sea necesario, esto es *Refactorización de clase en línea*.



# Haciendo las condiciones más fáciles de leer

### Descompón el condicional

Miramos la condición y el bloque, si se puede extraer en un método.

Comprobar los bloques del condicional, y extraerlos en métodos a la vez que rellenamos los bloques con llamadas a los métodos que contienen las operaciones o instrucciones, para aclarar mejor el código para un futuro.

### Consolida la expresión condicional

Si una serie de condicionales comparten resultado,  lo consolidaremos en un método condicional externo para simplificar la lectura y la estructura del código.

### Consolida los fragmentos duplicados condicionales

Si una línea está duplicada en diferentes bloques del condicional (en el true y en el else), lo que haremos será derivarlas a un atributo externo.



# Refactorización de mover campos

Muchas veces, el comportamiento y los datos suelen estar entrelazados.

En lugar de mover los métodos, moveremos los datos (campos).

Si se da la "Envidia de caracteríscitcas", que una clase está más preocupada de los métodos y campos de otra clase que de la suya propia.

Cuando alguno de los métodos de una clase, hacen referencia a un mismo campo de otra clase, sería más cómodo mover los campos a la clase dónde realmente hay más metodos que lo están utilizando.

Mover un campo es más fácil que mover un método, pero muchas veces los campos suelen estar encapsulados y es más difícil acceder a ellos.

<u>Mejorar el movimiento</u>

- Añadir métodos accesores antes de mover (getters/setters)
- Cambiar las referencias en vez de acceder directamente a las variables.

# Trabajando con cúmulos de datos 

Un cúmulo de datos es una zona del programa que tiene "mal aspecto".

Cuando detectamos que un conjunto de datos tiene lógica con ellos mismos, y no tiene relación con el resto de código, podemos extraerlos en otra clase propia para mayor limpieza.

Es aplicar el mismo método de extracción, pero a los datos directamente.

Crear variables de datos para luego llamarlos desde métodos.

Crear "marcos" cuando los parámetros se repiten, una clase con los datos que vamos a llamar en los parámetros.



# Simplificando llamadas al método y de los parámetros 

### Renombrar métodos

- No significa que hayamos cometido un error
- Si un método cambia de función, debería cambiar el nombre
- Se suele utilizar verbo+sustantivo
- "Nombra el método de la misma forma que hubieras llamado el comentario"

### Añadir y quitar parámetros

- Preferencia por listas breves de parámetros: Breves es más
- Si puedes quitar un parámetro, quítalo
- A veces es necesario añadir
- Utiliza alternativas de adición

### Parametrizar métodos

- Cuando métodos que hacen algo similar, se agrupan en un método y pasarlo como parámetro
- Puede darse el case de justo lo contrario, así que se puede extraer en diferentes métodos



# Subir y bajar métodos y campos 

Subir método y subir campo

En una jerarquía de clases y subclases, puede repetirse un campo. Si se da esta situación, se "sube" a la superclase los campos o métodos repetidos y que comparten varias subclases.

Bajar método y campo

Cuando una superclase tiene un campo/método, puede ser que sólo una de las subclases utilice ese método/campo, entonces lo empujamos a la subclase que sí lo utilice, y liberamos a las demás subclases de ese dato.



# Refinando jerarquías de clases 

Extracción de superclase

Cuando hay 2 o más clases con alguna similitud, se extraen esas similitudes a una superclase. Es como subir método/campo.

Extracción de subclase

Cuando nos damos cuenta que vamos a crear instancias de varios objetos de una clase existente, pero hay una falta de consistencia en el comportamiento.

Es decir, ver qué campos/métodos se utilizan en TODAS las subclases, y cuáles en sólo algunas, y se pasan estos campos a las que los van a utilizar



# Refactorización en las comunicaciones de clases

Comunicación = datos de una clase a otra

<u>Cadena de mensajes</u>

Cuando requerimos de una cadena de peticiones a otras clases, se vuelve frágil, así que simplificamos la cadena de mensajes.

<u>Man in the middle</u>

Cuando hay una clase que únicamente funciona para pasar información de una a otra clase. Eliminaremos esta clase si no aporta nada extra.



# Refactorización a gran escala

Las anteriores refactorizaciones están hechas a bajo nivel.

Para aplicar estas ideas a un nivel más elevado, es necesaria una gran planificación fuera del editor de código. Hay que planificar cómo será el futuro y como queremos enfrentarlo.

- No mezcles lógica de negocios y lógica de presentación
- Enfoques comunes: MVC, MVVM

El enfoque general, será un resumen de aplicación de todos los aspectos anteriores.

