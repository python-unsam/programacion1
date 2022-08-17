[Contenidos](../Contenidos.md) \| [Anterior (4 Números)](04_Numeros.md) \| [Próximo (6 Cadenas)](06_Strings.md)

# 1.5 Línea de comandos

En esta sección comenzamos a hablar de la terminal, o la línea de comandos del sistema operativo. Es un programa que podés instalar como cualquier otro, aunque tanto en Windows como en Linux y Mac OS se instala junto con el sistema operativo, y aunque es la forma más primitiva de interactuar con le usuarie, es también en muchos casos la más rápida, la más versátil, y la más segura.


### La línea de comandos:


La línea de comandos (command line) suele usarse para pedirle al sistema operativo cosas que se puedan escribir en una o dos líneas, tales como listar un directorio, moverse entre carpetas, borrar un archivo, ejecutar un programa.

Quienes usen Linux probablemente hayan usado "Terminal" para instalar o ejecutar algún programa. En sistemas Linux (Ubuntu en este caso) nos da esta bienvenida al ejecutarlo:
```
Bienvenido a Ubuntu 20.04.2 LTS (GNU/Linux 4.4.0)
Para ejecutar un commando como administrador (usuario "root") usar "sudo <commando>"
Ver "man sudo_root" para mas detalles.

oski@flaquita:~$
```

Quienes estén en Windows usen "Windows PowerShell".
```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Try the new cross-platform PowerShell https://aka.ms/pscore6

PS C:\Users\oski>
```

A las líneas  `oski@flaquita:~$`  en Linux y  `PS C:\Users\oski>`  en Windows se las llama _command prompt_ en inglés y es la forma que tiene la terminal de decirte "yo te estoy esperando a vos". Te está _preguntando_ (_prompting_) lo que debe hacer. 


### Dónde estamos

La línea de comandos facilita administrar archivos y espacios de almacenamiento, y lanzar programas. El sistema ejecuta los comandos que le digas sobre el directorio en el que estás, salvo que especifiques lo contrario.

_Nota_: Para los siguientes pasos puede serte útil abrir una instancia del programa Administrador de Archivos (File Manager en Windows o Nautilus, Dolphin o Thunar en Linux). Así verás lo que sucede en el disco en forma gráfica, además de lo que veas en la línea de comandos.

Normalmente al abrir una ventana terminal estamos en el directorio _home_ (hogar) del usuario correspondiente (`~` y `\Users\oski`) en el disco `C:`.

`oski@flaquita:~$`

`PS C:\Users\oski>`


## Abramos "Ejercicios.zip"

Vamos a pedir ver el contenido del directorio _home_:
`oski@flaquita:~$ ls`

`PS C:\Users\oski> dir`

Verás la lista de archivos y directorios en ese lugar. Solo para estar seguros, tratá de encontrar un directorio llamado `Ejercicios_Python`. No debería existir aún. 

Vamos a usar los programas `zip` y `unzip` que se instalan con el sistema operativo. Los podés [bajar de acá](http://infozip.sourceforge.net/) aunque no debiera ser necesario. Con ellos vamos a abrir el paquete [Ejercicios.zip](../Ejercicios.zip) para armar la estructura de directorios donde ordenar las soluciones a los ejercicios de cada clase. Fijate dónde guarda el browser `Ejercicios.zip` al bajarlo. (suele ser en Downloads ó Descargas)

`PS C:\Users\flacus> unzip -l Downloads/Ejercicios.zip`

Te va a mostrar una lista con los archivos y directorios contenidos en `Ejercicios.zip` 

Fijate lo que hicimos: le pedimos al sistema operativo que ejecute un programa llamado `unzip` y que a ese programa le pase dos parámetros (`-l`  y  `Downloads/Ejercicios.zip`)

Ahora pidámosle que extraiga uno de esos archivos:

`unzip -x downloads/Ejercicios.zip ejercicios_python/readme.txt`

Notá que cambiamos el `-l` (listar) por un `-x` (extraer).
Vas a ver el archivo `readme.txt` en el directorio que acaba de crear (`ejercicios_python` dentro del directorio en que estás trabajando).

Ahora pidámosle que abra todo el contenido el paquete. Si no le decimos que queremos un archivo en particular, unzip extrae todo.

`unzip -x downloads/Ejercicios.zip`

Unzip inicia la extracción, crea los directorios que son necesarios para ubicar los archivos que extrae, y extrae los archivos del .zip en cada uno.  Encuentra que uno de ellos ya existe y te pregunta cómo querés solucionar el problema :

`replace ejercicios_python/readme.txt? [y]es, [n]o, [A]ll, [N]one, [r]ename:`

Contestále `y`

Listo. Unzip recreó toda la estructura de directorios contenida en el .zip y puso cada archivo en su lugar. Sólo escribiste una línea para que lo haga.

Generalicemos esto que hicimos recién.


### Comandos, directorio de trabajo y parámetros.

_Nota:_ Habrás notado que en esta sección el sistema usa el separador `\` pero nosotros usamos `/`. Esto nos permite escribir la misma línea en Linux y en Windows dado que ambos entienden `/`

En general para pedir cosas al sistema operativo decile *qué, dónde y cómo*: QUE querés que haga, DONDE querés que lo haga, y COMO querés que lo haga (con variaciones, por supuesto):

comando [donde] [parámetros]

_comando_: qué queremos que haga.
_donde_: archivos y/o directorios sobre los que queremos que actúe.
_parámetros_ detalles sobre como queremos que actúe.

comando: `unzip`
donde: `downloads/Ejercicios.zip`
como: `-x`

Tanto _dónde_ como _parámetros_ son muchas veces opcionales. Si omitimos especificarlos toman sus valores por omisión (tambien llamados "por defecto"). 

Veamos algunos ejemplos.


### ¿Qué hay acá? 
Para saber qué contiene un directorio, usá `ls` (_list_, lista). Devuelve una lista con los archivos y directorios contenidos donde vos digas. Veamos el directorio recién creado.

```code
C:\Users\oski> dir ejer*

    Directory: C:\Users\oski


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        2022-07-30   6:06 AM                ejercicios_python
```

```code
dir ejercicios_python/


    Directory: C:\Users\oski\ejercicios_python


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        2021-02-23   3:32 PM                Clase01
d-----        2021-02-23   3:34 PM                Clase02
d-----        2021-02-23   3:34 PM                Clase03
d-----        2021-02-23   3:34 PM                Clase04
d-----        2021-02-23   3:34 PM                Clase05
d-----        2021-02-23   3:34 PM                Clase06
d-----        2021-02-23   3:34 PM                Clase07
d-----        2021-02-23   3:34 PM                Clase08
d-----        2021-02-23   3:34 PM                Clase09
d-----        2021-02-23   3:34 PM                Clase10
d-----        2021-02-23   3:34 PM                Clase11
d-----        2021-03-10   9:53 AM                Data
-a----        2021-03-10   9:16 AM            106 readme.txt

```


## Cambiar el directorio de trabajo

Si queremos cambiar el directorio en el que estamos trabajando, usamos el comando `cd` (_change directory_, cambiar directorio). Por ejemplo, para ir al directorio destinado a resolver los ejercicios de la Clase 1 podrías decir:

```
cd ejercicios_python/Clase01
```

obteniendo

`PS C:\Users\oski\Ejercicios_Python\Clase01>`

Que es donde queremos estar.

_Nota: Mi nombre de usuario en este Windows es `oski` Adaptá el nombre al usuario que vos uses, o al directorio de trabajo (home) en tu Windows._


## Ver el contenido de un archivo
El comando `type` te muestra lo que un archivo contiene. Evita que tengas abrir un editor y buscar el archivo sólo para verlo.

```
PS C:\Users\oski\ejercicios_python\clase10> type readme.txt
esta carpeta contiene los archivos .py correspondientes a la ejercitaciÃ³n de la clase 10
```
_Nota:_ La palabra "ejercitación"se lee mal por un problema de "encoding" o codificación de datos. Veremos esto mas adelante.


## Borrar un archivo
Si querés borrar rápidamente un archivo decile
```
del nombredelarchivo
```

Donde nombredelarchivo es el camino completo al archivo (fully qualified filename) por ejemplo `del c:/users/flacus/ejercicios_python/clase10/readme.txt`

Si ya estás en el directorio donde está el archivo que querés borrar, no necesitás especificarlo:

```
PS C:\users\flacus\ejercicios_python\clase10>del readme.txt
``` 

_Nota: Windows no es case-sentitive (sensible a mayusculas) para nombres de archivos y directorios. Linux SI_.


## Caminos absolutos y caminos relativos

Notemos algo que es un poco sutil y aún así muy importante. Como decíamos antes, los comandos se ejecutan sobre el directorio en que estás. Por ejemplo, si estamos en un directorio donde existe un archivo `readme.txt` podemos simplemente decir 

``` 
PS C:\Users\oski\ejercicios_python\clase01> type readme.txt
``` 

Sin embargo, si queremos ver un archivo `readme.txt` que está en _otro_ directorio (por ejemplo en `clase02`), tenemos que especificar dónde está. Hay dos formas de referirnos a la ubicación de un archivo o directorio. Una es usando su nombre completo, lo que se llama un camino ó ("pathname") absoluto:

``` 
PS C:\Users\oski\ejercicios_python\clase01> type C:/Users/oski/ejercicios_python/clase02/readme.txt
``` 

Notar que estamos parados en `C:\Users\oski\ejercicios_python\clase01` y nos estamos refiriendo al `readme.txt` que está en "el directorio de al lado" `C:\Users\oski\ejercicios_python\clase02\`


Otra forma de referirnos a un directorio es especificar cómo llegar allí desde donde estamos:

``` 
PS C:\Users\oski\ejercicios_python\clase01> type readme.txt
``` 
Se refiere al archivo `readme.txt` ubicado en este mismo directorio ó si queremos un `readme.txt` que está en un directorio aledaño:

``` 
PS C:\Users\oski\ejercicios_python\clase01> type ../clase02/readme.txt
``` 

Esto significa que _desde donde estamos_, vamos a "subir un directorio" (`../`) y luego bajar a `clase02/` y trabajar con el archivo `readme.txt` que está ahí. Notá que eliminamos toda la parte del nombre del archivo que también está incluída en el directorio donde estamos, y la reemplazamos por `../`

Esta última forma, llamada "relative pathname" o camino relativo (relativo a donde estamos), es muy útil cuando tenés un conjunto de archivos en directorios cercanos (como los de las clases de esta materia) y se usará mucho en [Sección 3.4](../03_Contenedores_y_Errores/04_Llamados_desde_cmd.md#llamados-desde-consola)




[Contenidos](../Contenidos.md) \| [Anterior (4 Números)](04_Numeros.md) \| [Próximo (6 Cadenas)](06_Strings.md)

