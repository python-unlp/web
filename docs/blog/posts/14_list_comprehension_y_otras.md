---
date: 2024-03-05
categories:
  - Python
  - List comprehensions
---

# List comprehensions y otras

La notación por comprensión en Python esta directamente basada en la notación matemática de conjuntos por comprensión.

Esta guía se puede leer de 2 formas distintas dependiendo del tiempo y dedicación del lector:

1. Completa: Da un panorama completo que ayuda a entender por qué la sintáxis de las list comprehensions es como es y la contrasta con otras formas de resolver el mismo problema.
2. A partir de "Introducción menos ñoña": Muestra como usar las comprehensions de forma directa.

<!-- more -->

## Introducción ñoña

### Conjuntos por comprensión en las matemáticas

Como pequeño repaso, en matemáticas desde la escuela nos enseñan a escribir conjuntos de distintas formas, 2 de ellas son:

- Por extensión o enumeración: Se escriben explícitamente todos los elementos que pertenecen al conjunto entre llaves. Por ejemplo: `{1, 3, 5, 7, 9}`.
- Por comprensión: El conjunto se define escribiendo las condiciones que debe cumplir entre llaves. Siguiendo con el ejemplo anterior: `{números naturales impares menores que diez}`.

El último ejemplo se puede sofisticar más usando una notación más matemática para mayor precisión. Por ejemplo:

```
{n / n ∈ ℕ; n < 10; n es impar}
```

Esto se podría leer como "Todo n, tal que n pertenece a los reales, es menor que diez y es impar".

Como veremos la notación por comprensión de Python se parece mucho a este último ejemplo.

### Notación por comprensión en Python

La notación por comprensión en Python se puede usar para construir listas, conjuntos, diccionarios y generadores. Todos son muy similares, pero por simplicidad empezaremos definiendo listas.

Tomaremos el ejemplo de la sección anterior queremos generar una lista de los "números naturales impares menores que diez". Se puede escribir una list comprehension de Python que tenga esos valores
de la siguiente forma:

```python
[n for n in range(1, 10) if n % 2 != 0]
```

Si comparamos este código con la notación matemática de conjuntos por comprensión vemos que sigue más o menos el mismo patrón:

1. Primer va el valor que nos interesa, `n`.
2. Luego con el `for` obtenemos valores de `n` que son números naturales entre 1 y 10. Esto es como una combinación de `n ∈ ℕ` y `n < 10`.
3. Finalmente filtramos con el `if` los valores impares.

### Muchas formas de construir listas

Python permite crear listas de muchas formas distintas. Tal vez la más familiar para la mayoría de les alumnes sea la forma procedural.

#### Ejemplo procedural

```python
result = []
for n in range(10):
    if n % 2 != 0:
        result.append(n)
```

Al programar en forma procedural indicamos **cómo** realizar una tarea. Como programadores al leer un código con un `for` entendemos que ese código itera y hace "algo", pero no podemos adivinar qué hace hasta leer bien el código adentro y afuera de ese `for`.

#### Ejemplo con map y filter

Otra forma de resolver este problema sería usar un paradigma más parecido al funcional y usar funciones como `map`, `filter` y `reduce` para resolver este tipo de problemas:

```python
list(filter(lambda n: n % 2 != 0, range(1, 10)))
```

Acá en lugar de indicar el **cómo** indicamos **qué** queremos hacer. Queremos un rango de números del 1 al 10, de ese rango queremos filtrar los impares y a ese resultado lo queremos en una lista.

En este caso como programadores al leer la palabra `list` nos queda claro que estamos construyendo una lista y al leer `filter` queda claro que estamos filtrando información de alguna manera. Pero obviamente tenemos que estar familiarizados y acostumbrados a leer código con `lambda`, `filter`, `map` o `reduce` para entender este tipo de soluciones.

#### Volviendo a la list comprehension

La notación por comprensión es un concepto básico y difundido de las matemáticas. También es una notación que es usada distintos lenguajes de diferentes paradigmas.

```python
[n for n in range(1, 10) if n % 2 != 0]
```

De forma similar al ejemplo anterior, con la list comprehesion indico el **qué** y no tanto el **cómo**. Queda claro para el programador al ver los corchetes que estamos creando una lista, al ver el `range` veremos el conjunto de números inicial y por último al ver la condición del `if` vemos cómo filtraremos ese conjunto de números para quedarnos con el resultado final.

Obviamente necesitamos un poco de práctica para entender este código, pero sólo es necesario saber cómo se escribe un `for`, un `if` y en qué orden leer el código para entenderlo.

## Introducción menos ñoña

### List comprehension básicas

La notación por comprensión tiene cómo minimo 2 partes, una expresión y un `for`:

```python
[expression for variable in iterable]
```

`expression` es el valor que guardaremos en la lista. Puede ser un valor arbitrario, la misma variable, una operación aplicada a esa variable, etc...

`variable` es el elemento actual en una iteración dada como en un `for` normal e `iterable` la lista, tupla, diccionario, generador, etc... que estamos iterando.

Por ejemplo abajo la primer list comprehension retorna una lista con los números del 0 al 19 y la segunda retorna esos mismos números pero elevados al cubo:

```python
numbers = [n for n in range(20)]
cubes = [n**3 for n in range(20)]
```

Esas líneas equivalen a la siguiente solución procedural:

```python
numbers = []
for n in range(20):
    numbers.append(n)

cubes = []
for n in range(20):
    cubes.append(n**3)
```

### Con `if` para filtrar

Muchas veces necesitamos filtrar los valores iterados para quedarnos los que cumplan una condición. Para eso podemos agregar un `if` (este `if` no tiene `else`). Por ejemplo si queremos una lista con todas las letras de un texto pasadas a mayúscula (descartando lo que no sea letra) podemos escribir:

```python
text = "La Plata es el principal centro político, administrativo y educativo de la provincia de Buenos Aires. De acuerdo al censo argentino 2022 cuenta con 772.618 habitantes, mientras que su área metropolitana, el Gran La Plata, alcanza los 938.287 habitantes."

uppercase_chars = [char.upper() for char in text if char.isalpha()]
```

Esta list comprehension equivale al siguiente código procedural:

```python
uppercase_chars = []
for char in text:
    if char.isalpha()
        uppercase_chars.append(char)
```

Notar que éste `if` que se utiliza para filtrar va siempre al final de la list comprehension.

### Iterar estructuras anidadas

Es posible recorrer estructuras más complejas con `for` anidados. Por ejemplo supongamos que dada una matriz (en una lista de listas) queremos obtener una lista con los números impares dentro de esa matriz:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
]

even_numbers = [n for row in matrix for n in row if n % 2 != 0]
```

Lo anterior equivale al siguiente código procedural:

```python
even_numbers = []
for row in matrix:
    for n in row:
        if n % 2 != 0:
            even_numbers.append(n)
```

Notar que los `for` se escriben en el mismo orden en la notación por comprensión y en la procedural y que el `if` (en caso de haber un `if`) va al final de todo.

## Otros objetos que se pueden definir por comprensión

Podremos definir:

* Conjuntos: `{x for x in range(20) if x % 2 == 0}` (números pares menores que 20)
* Diccionarios: `{k: v for k, v in original.items() if k.startswith("h")}` (creamos una copia del diccionario "original" que solo tiene las entradas cuya clave empieza con "h")
* Generadores: `(x ** 2 for x in itertools.count() if x % 2 == 0)` (creamos un generator que retorna el cuadrado de los números pares indefinidamente)

## ¿Por qué usaría comprehensions en Python?

* Principalmente usaremos esta notación para aportar legibilidad a nuestros programas. Es muy importante que los programas sean legibles y en general es más deseable expresar **qué** debe hacer el código en lugar de expresar **cómo** debe hacerlo.
* La forma procedural es a menudo poco clara en la intención (no queda claro si además de la lista se hacen otras cosas en el `for`) y es propensa a errores (es necesario por ejemplo recordar crear una lista vacía fuera del `for` y recordar hacer le `append`).
* `map`, `filter` y `reduce` son funciones que resultan familiares a quienes trabajaron con lenguajes de programación funcionales o influenciados por ellos. Pero pueden ser complicados de entender para quienes no vienen de ese mundo. Adicionalmente es necesario usar `lambdas` o funciones con nombre para usarlas agregando un poquito más de complejidad al programa.

Todo esto no significa que siempre se debe usar notación por comprensión, existen casos donde las otras opciones son más apropiadas y es nuestra tarea como programadores elegir entre ellas teniendo en cuenta:

* Funcionalidad requerida
* Legibilidad y expresividad
* Eficiencia (sólo si es necesario)
