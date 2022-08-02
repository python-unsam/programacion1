[Contenidos](../Contenidos.md) \| [Anterior (3 Errores)](03_Bugs.md) \| [Próximo (5 Cierre de la clase [falta])](05_Cierre.md)

# 3.4 Llamados desde consola [falta]

Ya vimos que el python se puede correr desde la consola. También podemos correr programas escritos en pythons desde la consola. Esto nos permite usarlos de manera muy práctica

## Llamados desde consola:

Se relaciona con la [Sección 1.5](../01_Intro_a_Python/05_Lineas_de_Comandos.md#la-línea-de-comandos).

Ya vimos en la [Sección 1.5](../01_Intro_a_Python/05_Lineas_de_Comandos.md#la-línea-de-comandos) que el python se puede correr desde la consola. También podemos correr programas escritos en pythons desde la consola. Esto nos permite usarlos de manera muy práctica

Quizas se puede poner este ejercicio:
### Ejercicio 3.10: Ejecución desde la línea de comandos con parámetros - SACAR DE ACA
*SACAR DE ACA*

En el programa `costo_camion.py`, el nombre del archivo de entrada `'../Data/camion.csv'` fue escrito en el código.

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

`sys.argv` es una lista que contiene los argumentos que le pasamos al script al momento de llamarlo desde la línea de comandos (si es que le pasamos alguno). Por ejemplo, desde una terminal de Unix (en Windows es similar), para correr nuestro programa y que procese el mismo archivo podríamos escribir:

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


Te dejamos un [video](https://youtu.be/D4WI4qsuwrQ) explicando cómo funciona el pasaje de parámetros por linea de comandos en python. 



[Contenidos](../Contenidos.md) \| [Anterior (3 Errores)](03_Bugs.md) \| [Próximo (5 Cierre de la clase [falta])](05_Cierre.md)

