[Contenidos](../Contenidos.md) \| [Anterior (1 Python)](01_Python.md) \| [Próximo (3 Un primer programa)](03_Hello_world.md)

# 1.2 # Variables, Condicionales y Ciclos

En esta sección veremos tres conceptos centrales: definición de variables y asignación de valores y operaciones, condicionales, y ciclos. Un programa es en el fondo una combinacion de estos tres elementos centrales: asignaciones de variables, ramificaciones condicionales, y repeticiones cíclicas. Suponemos que ya viste estos conceptos antes, pero empecemos por ahí.

### Condicionales:

### Variables

Una variable es un nombre para un valor. Los nombres de las variables pueden estar formados por letras (minúsculas y mayúsculas) de la _`a`_ a la _`z`_. También pueden incluir el guión bajo `_` y se pueden usar números, salvo en el primer caracter.

```python
>>> altura = 442 # válido
>>> _altura = 442 # válido
>>> altura2 = 442 # válido
>>> 2altura = 442 # inválido
```

Para asignar valores a variables en Python escribimos el operador de asignación `=`

```python
>>> a = 12
>>> b = 20
>>> c = a + b

```

El valor del lado derecho es asignado a la variable del lado izquierdo. Nunca al revés.

Notá que cuando decimos "un valor" hablamos de una gran diversidad de objetos. A un nombre de variable le podés asignar booleanos, números, texto, otras variables, incluso fragmentos de un programa. Lo veremos luego. Para saber el valor de una variable, escribimos su nombre.

```python
>>> c
32
>>> 

```

Durante este curso muchas veces mostraremos el comportamiento del intérprete como aquí arriba. _No es sólo para que lo veas._ Lanzá Python y tipeálos ! Experimentá variantes ! No es la lectura pasiva de este texto lo que vale, sino tu propia experiencia y tus dedos en el teclado.

### Python distingue mayúsculas de minúsculas

Mayúsculas y minúsculas son diferentes para Python. Por ejemplo, todas las siguientes variables son diferentes.

```python
>>> nombre = 'David'
>>> Nombre = 'Diego'
>>> NOMBRE = 'Rosita'
```

Si Python no conoce una variable porque nunca se la presentaste, te lo va a decir con un mensaje de error.

```python
>>> nombre = 'David'
>>> nombre
'David'
>>> nombRe
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'nombRe' is not defined
>>>
```

("Error de Nomenclatura: el nombre 'nombRe' no está definido")

Es importante que trates de entender estos mensajes. Programar es un diálogo entre el intérprete y vos. No tomes el mensaje de error como un simple "no funciona". En ese mensaje está la semilla de la solución. 

Los comandos de Python siempre se escriben con minúsculas. 

```python
>>> WHILE x < 0:   # ERROR
>>> while x < 0:   # OK
```

_Nota_: Por claridad, en adelante omitiremos el simbolo con que Python te indica que te está esperando (`>>>`) y el símbolo de continuación de bloque (`...`).

### Tipos de datos

Las variables pueden contener una gran diversidad de tipos de datos. Dos variables son del mismo "tipo" si contienen el mismo tipo de datos.

```python
altura = 442           # Entero
altura = 442.0         # Punto flotante
altura = 'Muy, muy alto' # Cadena de caracteres (string)
```
No es necesario declarar el tipo de una variable (como sí lo es en otros lenguajes). El intérprete deduce el tipo según el valor del lado derecho de la asignación, y este tipo puede cambiar durante la vida de la variable.

Notá que asignamos distintos tipos de valores a la misma variable. Decimos que Python tiene tipado dinámico, es decir, el tipo percibido por el intérprete puede cambiar a lo largo de la ejecución dependiendo del valor asignado a la variable.


### Booleanos (bool)
Uno de los tipos de datos mas usados es el booleano.

Las variables booleanas se llaman así en honor al lógico inglés [George Boole](https://es.wikipedia.org/wiki/George_Boole). Pueden tomar dos valores: `True` o `False` (verdadero o falso).

```python
a = True
b = False
```

Las variables booleanas suelen usarse para contener el resultado de operaciones booleanas: comparaciones en general.

```python
una = 3
otra = 6
una < otra
True
una == otra
False
a = (una == otra)
a
False
```

El operador `==` devuelve True si ambos lados son iguales, devuelve False si no lo son. No confundirlo con `=` usado para asignaciones. 

Internamente, los booleanos son evaluados como enteros con valores `1`, `0`.

```python
c = 4 + True # 5
d = False
if d == 0:
    print('d es False')
```

*No escribas código basado en esta convención. Sería bastante extraño.*

### Palabras Reservadas

Habrás notado que `True` y `False` se capitalizan. Son _palabras reservadas_ que Python conoce. Ya tienen un significado asignado y por lo tanto no es posible usarlas como variables. Si le pedimos a Python que asigne un valor a una variable llamada `True` nos va a contestar que no puede:

```python
True = 100
  File "<stdin>", line 1
    True = 100
    ^
SyntaxError: cannot assign to True
```
("Error sintáctico: no puedo asignar [un valor] a True")

Podés ver la lista completa de palabras reservadas si la pedís. `True` y `False` no son las únicas.

```python
import keyword
keyword.kwlist
```


### Imprimir en pantalla

La función `print` imprime una línea de texto con el valor pasado como parámetro.

```python
print('Hello world!') # Imprime 'Hello world!'
```

El parámetro del `print` puede ser una variable. El texto impreso en ese caso será el valor de la variable y no su nombre.

```python
x = 100
print(x) # imprime el texto '100'
```

Si le pasás más de un valor al `print`, los separa con espacios.

```python
nombre = 'Juana'
print('Mi nombre es', nombre) # Imprime el texto 'Mi nombre es Juana'
```

`print()` siempre termina la línea impresa pasando a la siguiente.

```python
print('Hola')
print('Mi nombre es', 'Juana')
```

Esto imprime:

```code
Hola
Mi nombre es Juana
```

Este salto de línea entre ambos comandos puede ser suprimido o reemplazado (en este caso por un espacio):

```python
print('Hola', end=' ')
print('Mi nombre es', 'Juana')
```

Este código va a imprimir:

```code
Hola Mi nombre es Juana
```


### Condicionales

El comando `if` permite que ciertas secciones de un programa se ejecuten o no según el resultado de una condición. A esto lo llamamos _ejecución condicional_. 

```python
una = 3
otra = 6
if una < otra:
    print("una es menor que otra")
una es menor que otra
```

Examinemos estas dos líneas un momento. La primera línea comienza con un `if` y termina con un `:`. Entre el `if` y el `:` hay una comparación (`una < otra` llamada "condición") que puede cumplirse o no. Sólo si esta condición se cumple Python ejecuta el bloque de código indentado.

_Probar:_ Cambiá el operador `<` por `==` ó `>` y los valores de `una` y `otra` y fijate en qué casos se ejecuta el `print()`.

El comando `else` define un bloque que sólo se ejecutará si la condición del `if` precedente _no_ se cumplió.

```python
if una < otra:
    print('Gana otra')
else:
    print('Gana una')

Gana una
```

_Nota_: si este fragmento de código no funciona como esperás, revisá los valores guardados en `una` y `otra`. 

Podés verificar condiciones mutuamente excluyentes agregando condiciones extras con `elif`.

```python
una = 3
otra = 6
if una > otra:
    print('Gana una')
elif una < otra:
    print('Gana otra')
else:
    print('Empate!')
```

El comando `elif` viene de *else, if* y puede traducirse como "sólo si no se cumple la condición del *if* anterior, verificá si se cumple la siguiente".

Una forma de entender las variables booleanas es pensarlas como el resultado de la ejecución condicional de código:

```python
a = False
if una == otra:
    a = True
```


### Ciclos

Para ejecutar una porción de código únicamente si ciertas condiciones se cumplen podés usar el comando `while`. El `while` se comporta como un `if` mas un _ciclo_ (bucle o _loop_) que vuelve a ejecutar el bloque indentado si la condición del `while` sigue valiendo `True`.

```python
while una < otra:
    una = una + 1
    print (una)

print ('una:',una,'otra:',otra)
```

Los comandos indentados debajo del `while` se van a a ejecutar mientras la condición del `while` sea verdadera (`True`).


### Indentación

La indentación se usa para marcar grupos de comandos que van juntos.
Considerá el ejemplo anterior:

```python
while una < otra:
    una = una + 1
    print (una)

print ('una:',una,'otra:',otra)
```

La indentación agrupa los comandos siguientes como las operaciones a repetir:

```python
    una = una + 1
    print (una)
```

Como el comando  `print()` del final no está indentado, no pertenece al ciclo. La línea en blanco que dejamos entre ambos solo está para facilitar la lectura y no afecta la ejecución.

### Indentando adecuadamente

Algunas recomendaciones sobre cómo indentar:

* Usá espacios y no el tabulador.
* Usá 4 espacios por cada nivel.
* Usá un editor de textos que entienda que estás escribiendo en Python.

El único requisito del intérprete de Python es que la indentación dentro de un mismo bloque sea consistente. Por ejemplo, esto es un error:

```python
while num_billetes * grosor_billete <= altura_obelisco:
    print(dia, num_billetes, num_billetes * grosor_billete)
        dia = dia + 1 # ERROR
    num_billetes = num_billetes * 2
```


Ahora que manejás variables, condicionales, y ciclos y tenés algunos de los elementos básicos de Python en la próxima sección vamos a usarlos para escribir algunos programas simples.



[Contenidos](../Contenidos.md) \| [Anterior (1 Python)](01_Python.md) \| [Próximo (3 Un primer programa)](03_Hello_world.md)

