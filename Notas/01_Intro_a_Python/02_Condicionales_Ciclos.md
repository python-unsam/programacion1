[Contenidos](../Contenidos.md) \| [Anterior (1 Python)](01_Python.md) \| [Próximo (3 Un primer programa)](03_Hello_world.md)

# 1.2 Variables, condicionales y ciclos

En esta sección veremos tres conceptos centrales: variables, condicionales, y ciclos. Un programa es en el fondo una combinacion de estos tres elementos centrales: asignaciones de variables, ramificaciones condicionales, y repeticiones cíclicas. Suponemos que ya viste estos conceptos antes, pero empecemos por ahí.

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

Notá que cuando decimos "un valor" hablamos de una gran diversidad de objetos. A un nombre de variable le podés asignar números, texto, listas de valores o cosas más complejas aún. Lo veremos luego. Para saber el valor de una variable, escribimos su nombre.

```python
>>> c
32
>>> 

```

Durante este curso muchas veces mostraremos el comportamiento del intérprete como aquí arriba. _No es sólo para que lo veas._ La idea es que lo corrás vos misme mientras lées estas notas. ¡Probá  variantes! No es la lectura pasiva de este texto lo que vale, sino tu propia experiencia y tus dedos en el teclado.

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

("Error de nomenclatura: el nombre 'nombRe' no está definido")

Es importante que trates de entender estos mensajes. Programar es un diálogo entre el intérprete y vos. No tomes el mensaje de error como un simple "no funciona". En ese mensaje está la semilla de la solución. 

Los comandos de Python siempre se escriben con minúsculas. 

```python
>>> WHILE x < 0:   # ERROR
>>> while x < 0:   # OK
```


### Tipos de datos

Las variables pueden contener una gran diversidad de tipos de datos. Dos variables son del mismo "tipo" si contienen el mismo tipo de datos.

```python
>>> altura = 442           # Entero
>>> altura = 442.0         # Punto flotante
>>> altura = 'Muy, muy alto' # Cadena de caracteres (string)
```
No es necesario declarar el tipo de una variable (como sí lo es en otros lenguajes). El intérprete deduce el tipo según el valor del lado derecho de la asignación, y este tipo puede cambiar durante la vida de la variable.

Notá que asignamos distintos tipos de valores a la misma variable. Decimos que Python tiene tipado dinámico, es decir, el tipo percibido por el intérprete puede cambiar a lo largo de la ejecución dependiendo del valor asignado a la variable.


### Booleanos (bool)
Uno de los tipos de datos más importes es el booleano.

Las variables booleanas se llaman así en honor al lógico inglés [George Boole](https://es.wikipedia.org/wiki/George_Boole). Pueden tomar dos valores: `True` o `False` (verdadero o falso).

```python
>>> a = True
>>> b = False
```

Las variables booleanas suelen usarse para contener el resultado de operaciones booleanas: comparaciones en general.

```python
>>> una = 3
>>> otra = 6
>>> una < otra
True
>>> una == otra
False
>>> a = (una == otra)
>>> a
False
```

El operador `==` devuelve True si ambos lados son iguales, y devuelve False si no lo son. No confundirlo con `=` que es usado para asignaciones. 

Internamente, los booleanos son evaluados como enteros con valores `1`, `0`.

```python
>>> c = 4 + True # 5
>>> d = False
>>> if d == 0:
>>>     print('d es False')
```

*No escribas código basado en esta convención. Sería bastante extraño.*

### Palabras reservadas

Habrás notado que `True` y `False` se escriben con mayúscula. Son _palabras reservadas_ que Python conoce. Ya tienen un significado asignado y por lo tanto no es posible usarlas como variables. Si le pedimos a Python que asigne un valor a una variable llamada `True` nos va a contestar que no puede:

```python
>>> True = 100
  File "<stdin>", line 1
    True = 100
    ^
SyntaxError: cannot assign to True
```
("Error sintáctico: no puedo asignar [un valor] a True")

Podés ver la lista completa de palabras reservadas si la pedís. `True` y `False` no son las únicas.

```python
>>> import keyword
>>> keyword.kwlist
```


### Imprimir en pantalla

La función `print` imprime una línea de texto con el valor pasado como parámetro.

```python
>>> print('Hello world!') # Imprime 'Hello world!'
```

El parámetro del `print` puede ser una variable. El texto impreso en ese caso será el valor de la variable y no su nombre.

```python
>>> x = 100
>>> print(x) # imprime el texto '100'
```

Si le pasás más de un valor al `print`, los imprime separándolos con espacios.

```python
>>> nombre = 'Juana'
>>> print('Mi nombre es', nombre) # Imprime el texto 'Mi nombre es Juana'
```

`print()` siempre termina la línea impresa pasando a la siguiente (_newline_), salvo que le especifiquemos otra cosa. Probá estos comandos para ver sus diferencias:

```python
>>> print('Hola mundo')
>>> print('Hola mundo', end='')
>>> print('Hola mundo', end='***')
>>> print('Hola mundo', end='\n')
>>> print('Hola mundo', end='\n\n')
>>> print('Hola mundo', end='\n\n\n')
>>> print('Hola mundo', end='\t')
>>> print('Hola mundo', end='\n\t')
```



### Condicionales

El comando `if` permite que ciertos fragmentos de un programa se ejecuten o no según el resultado de una condición. A esto lo llamamos _ejecución condicional_. 

```python
>>> una = 3
>>> otra = 6
>>> if una < otra:
...     print("una es menor que otra")
una es menor que otra
```

Examinemos estas dos líneas un momento. La primera línea comienza con un `if` y termina con un `:`. Entre el `if` y el `:` hay una comparación, `una < otra`, llamada "condición". Esta condición puede cumplirse o no. Sólo si esta condición se cumple Python ejecuta el bloque de código indentado que sigue.

_Probá:_ Cambiá el operador `<` por `==` ó `>` y los valores de `una` y `otra` y fijate en qué casos se ejecuta el `print()`.

El comando `else` define un bloque que sólo se ejecutará si la condición del `if` precedente _no_ se cumplió (_else_ en inglés significa _si no_)

```python
>>> if una < otra:
...     print('Gana otra')
... else:
...     print('Gana una')
Gana una
```

_Nota_: si este fragmento de código no funciona como esperás, revisá los valores guardados en `una` y `otra`. 

Podés realizar más comparaciones agregando condiciones extras con `elif`.

```python
>>> una = 3
>>> otra = 6
>>> if una > otra:
...     print('Gana una')
... elif una < otra:
...     print('Gana otra')
... else:
...     print('Empate!')
```

El comando `elif` viene de *else, if* y puede traducirse como "si no se cumplió la condición del *if* anterior, verificá si se cumple la siguiente" .

Las variables booleanas pueden reemplazar a una _condición_ en un condicional. 

```python
>>> variable_booleana = False # probá True también
>>> if variable_booleana:
...     print("La variable es verdadera")
... else:
...     print("La variable es false")
```

Recordemos que una variable booleana puede almacenar el resultado de una comparación:

```python
>>> una = 3
>>> otra = 6
>>> variable_booleana = (una > otra) # aca guardamos el resultado de la comparación
>>> if variable_booleana:
...     print('Gana una')
... elif una < otra:
...     print('Gana otra')
... else:
...     print('Empate!')
```


### Ciclos

Para ejecutar una porción de código reiteradamente mientras ciertas condiciones se cumplan podés usar el comando `while`. El `while` se comporta como un `if` mas un _ciclo_ (bucle o _loop_) que vuelve a ejecutar el bloque indentado si la condición del `while` sigue valiendo `True`.

```python
>>> while una < otra:
...     una = una + 1
...     print(una)
... print('una:', una, 'otra:', otra)
```

Los comandos indentados debajo del `while` se van a a ejecutar mientras la condición del `while` sea verdadera (`True`). Cuando esta condición sea falsa, ese bloque indentado no se ejecutará más y la ejecución continuará con el código que sigue.


### Indentación

La indentación se usa para marcar grupos de comandos que van juntos.
Considerá el ejemplo anterior:

```python
>>> while una < otra:
...     una = una + 1
...     print(una)
... print('una:',una,'otra:',otra)
```

La indentación agrupa los comandos siguientes como las operaciones a repetir:

```python
     una = una + 1
     print(una)
```

Como el comando  `print()` del final no está indentado, no pertenece al ciclo. 

### Indentando adecuadamente

Algunas recomendaciones sobre cómo indentar:

* Usá espacios y no el tabulador.
* Usá 4 espacios por cada nivel.
* Usá un editor de textos que entienda que estás escribiendo en Python.

El único requisito del intérprete de Python es que la indentación dentro de un mismo bloque sea consistente. Por ejemplo, esto es un error:

```python
>>> while una < otra:
...     una = una + 1
...         print(una)
```

Ahora que sabes como manejar  variables, condicionales, y ciclos en Python en la próxima sección vamos a usarlos para escribir algunos programas simples.



[Contenidos](../Contenidos.md) \| [Anterior (1 Python)](01_Python.md) \| [Próximo (3 Un primer programa)](03_Hello_world.md)

