[Contenidos](../Contenidos.md) \| [Anterior (3 Errores)](03_Bugs.md) \| [Próximo (5 Cierre de la clase)](05_Cierre.md)

# 3.4 Llamados desde consola [falta]

Ya vimos que el Python se puede correr desde la consola. También podemos correr programas escritos en pythons desde la consola. Esto nos permite usarlos de manera muy práctica

## Llamados desde consola:

Se relaciona con la [Sección 1.5](../01_Intro_a_Python/05_Lineas_de_Comandos.md#la-línea-de-comandos).

Ya vimos en la [Sección 1.5](../01_Intro_a_Python/05_Lineas_de_Comandos.md#la-línea-de-comandos) que Python se puede correr desde la consola. También podemos pasarle como parámetro, al invocarlo, el nombre de un script que queremos que ejecute. Esto nos permite usarlo de manera muy práctica. Abrí una ventana terminal y probá esto:

```code
PS ...\Clase03> py ../Clase01/rebotes.py
1 60.0
2 36.0
3 21.6
4 12.96
5 7.776
6 4.6656
7 2.7994
8 1.6796
9 1.0078
10 0.6047
```

Fijate que estamos en la carpeta de la clase 3 (`\Clase03>`) y le estamos pidiendo a Python que ejecute el script `rebotes.py` que hiciste en la clase 1, y que está en ese directorio (`../Clase01/rebotes.py`). La salida es el resultado de esa ejecución.

Ahora vamos a darle un poco más de flexibilidad a `rebotes.py`.

Escribí el siguiente código y guardalo con el nombre `parametros.py`

```python
import sys

print (sys.argv)
```

Ahora ejecutalo desde la línea de comandos con

```
PS ...\Clase03> py parametros.py
['parametros.py']
```

Y ahora probá:
```
PS ...\Clase03> py parametros.py uno dos tres
['parametros.py', 'uno', 'dos', 'tres']
```

Sin entrar en detalles, lo que hace el script es imprimir una variable (`sys.argv` del módulo `sys`). Esa variable es una lista (por eso los corchetes en la salida `['parametros.py']`) y esa lista contiene los parámetros que le dimos a Python al invocarlo (`
['parametros.py', 'uno', 'dos', 'tres']`). Notá que el primer parámetro en la lista (con índice `0`) es el nombre del script a ejecutar.

Esto es interesante porque implica que un script puede acceder a los parámatros que hayas escrito en la línea de comandos, incluso a su propio nombre. 

Cambiemos este pequeño script para que haga un cálculo con los parámetros que le pases:

```python
import sys

param1 = int(sys.argv[1])
param2 = int(sys.argv[2])

print (param1 * param2)
```

Y volvé a probarlo como antes.

No funciona, verdad ? Porqué ? Que dice el Traceback ? (probálo!). Dice que hubo una excepción de tipo `ValueError` porque la función `int()` no puede interpretar la cadena `uno` y por lo tanto el script se detiene.

Podríamos evitar que esta excepción detenga el programa, pero por ahora no compliquemos el script, y pasémosle parámetros que pueda usar:

```
...\Clase03> py parametros.py 4 3
12
```

## Ejercicios:
Usando estas ideas, modificá `rebotes.py` para que la altura inicial de la pelota no sea ya 100 metros, sino que la puedas especificar al invocar el script, de modo de obtener este comportamiento:

```code
...\Clase03> py rebotes.py 300
1 180.0
2 108.0
3 64.8
4 38.88
5 23.328
6 13.9968
7 8.3981
8 5.0389
9 3.0233
10 1.814
```

Atención a la forma de invocar el script ! 
Qué acaba de pasar acá ? Qué hemos hecho: hemos "exportado" una función escrita en Python y ahora la podemos invocar desde la línea de comandos pasándole los parámetros necesarios. Poderoso!


Esta modificación para recibir parámetros desde la línea de comandos tiene una ventaja y una desventaja. La ventaja esta clara. La desventaja tal vez también: ahora _es obligatorio_ pasarle parámetros por línea de comandos. 

En general, los programas tienen cierto comportamiento si uno les pide que hagan algo en particular, y otro comportamiento si uno no les pide nada (por ejemplo, en el caso de `zip` que usamos en la clase 1, si no le pedimos que haga nada en particular nos dá una ayuda)

Podemos lograr este comportamiento midiendo la longitud de la lista `sys.argv`, o checkeando que cumpla ciertas características.

### Ejercicio 3.10: Parámetros por omisión
Antes de asignar un valor a la altura inicial de la pelota, medí la longitud de la lista de parámetros. Si _omitimos_ pasarle el parámetro para la altura inicial, que use el valor por omisión de 100 metros. Si le pasamos una altura, entonces que use ésa. 

### Ejercicio 3.11: Ejecución desde la línea de comandos con parámetros
En el programa `costo_camion.py` del ejercicio [Ejercicio 2.9](../02_Estructuras_y_Funciones/04_Funciones.md#ejercicio-29-funciones-de-la-biblioteca), el nombre del archivo de entrada `'../Data/camion.csv'` fue escrito en el código.

```python
# costo_camion.py
import csv

def costo_camion(nombre_archivo):
    ...
    # Tu código
    ...

costo = costo_camion('../Data/camion.csv')
print('Costo total:', costo)
```

Esto está bien para ejercitar, pero en un programa real probablemente no harías eso ya que querrías una mayor flexibilidad. Una posibilidad es pasarle al programa el nombre del archivo que querés procesar como un parámetro cuando lo llamás desde la línea de comandos.

Copiá el contenido de `costo_camion.py` a un nuevo archivo llamado `camion_commandline.py` que incorpore la lectura de parámetros por línea de comando según la sugerencia del siguiente ejemplo:

```python
# camion_commandline.py
import csv
import sys

def costo_camion(nombre_archivo):
    ...
    # Tu código
    ...

if len(sys.argv) == 2:
    nombre_archivo = sys.argv[1]
else:
    nombre_archivo = '../Data/camion.csv'

costo = costo_camion(nombre_archivo)
print('Costo total:', costo)
```

Como vimos antes, `sys.argv` es una lista que contiene los argumentos que le pasamos al script al momento de llamarlo desde la línea de comandos (si es que le pasamos alguno). Por ejemplo, desde una terminal de Unix (en Windows es similar), para correr nuestro programa y que procese el mismo archivo podríamos escribir:

```bash
bash $ python3 camion_commandline.py ../Data/camion.csv
Costo total: 47671.15
bash $
```

O con el archivo `missing.csv`:
```bash
bash $ python3 camion_commandline.py ../Data/missing.csv
...
Costo total: 30381.15
bash $
```
Si no le pasamos ningún archivo, va a mostrar el resultado para `camion.csv` porque lo indicamos con la línea `nombre_archivo = '../Data/camion.csv'`.

Guardá tu programa en el archivo `camion_commandline.py` para entregar al final de la clase.


Te dejamos un [video](https://youtu.be/D4WI4qsuwrQ) explicando cómo funciona el pasaje de parámetros por línea de comandos en Python. 



[Contenidos](../Contenidos.md) \| [Anterior (3 Errores)](03_Bugs.md) \| [Próximo (5 Cierre de la clase)](05_Cierre.md)

