[Contenidos](../Contenidos.md) \| [Próximo (2 Contenedores)](02_Contenedores.md)

# 3.1 Introducción

Estructuras de datos, algoritmos, y las relaciones entre ellos.

Cuando estés diseñando algoritmos de procesamiento de datos vas a encontrarte con algo muy interesante: un algoritmo en particular funciona eficientemente sólo si los datos están almacenados de cierta forma, y otro algoritmo que resuelva el mismo problema puede requerir que almacenes los datos en otra estructura completamente diferente.

Los algoritmos imponen restricciones sobre la forma de almacenar los datos. Como contracara, muchas veces una forma particular de almacenar los datos sugiere de por sí un algoritmo de procesamiento. 

Los algoritmos y las estructuras de datos pueden ser conceptos independientes pero están íntimamente relacionadas al funcionar, e influyen drásticamente en la eficiencia de los programas que las usan. 

Un caso clásico es el de los algoritmos de búsqueda:

Si queremos saber si un número particular está presente en una lista de números, el hecho de tener esa lista de números ordenada permite usar métodos de búsqueda que son mucho más eficientes que si dicha lista estuviera desordenada.

Supongamos que nuestra lista de números es 
Numeros = [10, 20, 30, 40, 50, 60, 70, 80, 90]

Y estamos usando el siguiente algoritmo:

```code
	Avanzar una posición
	Es el numero que busco ?
		Si --> terminar (existe)
		No --> Loop
	Terminar (no existe)	
```

Si buscamos el `30`, el algoritmo visitaría las posiciones con: 10, 20, 30, y daría una respuesta (el número existe en la lista).

Si la lista estuviera desordenada, 
Numeros = [10, 90, 20, 80, 30, 70, 40, 60, 50]

El algoritmo visitaría: 10, 90, 20, 80, 30 y tardaría casi el doble en encontrar el número buscado. 

El hecho de _saber_ que la estructura de datos mantiene los datos ordenados, nos permite optimizar el algoritmo para ahorrar algunos pasos. Podemos decidir que el número _no_ está si encontramos un número mayor que el buscado:

```
	Avanzar una posición
	Es el numero que busco ?
		Si -- > Terminar (existe)
		No -- > Es mayor que el buscado ?
					Si --> Terminar (no existe)
					No --> Loop
```

Analizá qué posiciones visitaría el algoritmo si buscáramos p.ej. `33`.


El ejemplo muestra que una característica de la estructura de datos que usamos permite hacer más eficientes los algoritmos que trabajan con esa estructura. Es importante notar que sobre una lista desordenada esta optimzacion no se podría hacer, y sería necesario recorrer toda la lista hasta el final antes de poder decidir si un elemento existe o no.

En esta clase vamos a ver las tres estructuras de datos principales de Python, y algunos ejemplos de su uso.



[Contenidos](../Contenidos.md) \| [Próximo (2 Contenedores)](02_Contenedores.md)

