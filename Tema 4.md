# Tema 4

***

### Operadores de comparación
> Sirven para comparar dos o más variables. El resultado de esta comparación es un booleano (True / False)

```python
== # Igual a
!= # Diferente a
> # Mayor que
< # Menor que
>= # Mayor o igual que
<= # Menor o igual que
```

Si la comparación resulta verdadera, devuelve el resultado True. Si es falsa, el resultado es False.

```python
mi_booleano = 5 >= 6
prit(mi_booleano)
>> False
```
***

### Operadores lógicos
> Estos operadores permiten tomar decisiones basadas en múltiples condiciones

**And** devuelve **True** si todas las condiciones son veraderas.
```python
a = 6 > 5
b = 30 == 15 * 3
mi_booleano = a and b
print(mi_booleano)
>> False
```

**Or** devuelve **True** si al menos una condición es cierta

```python
a = 6 > 5
b = 30 == 15 * 3
mi_booleano = a or b
print(mi_booleano)
>> True
```

**Not** devuelve **True** si el valor del booleano es **False**, y **False** si es **True**.


```python
mi_booleano = not a
print(mi_booleano)
>> False
```

***

### Control de flujo

> Determina el orden en que el código de un programa se va ejecutando. En  Pyhton, el flujo está controlado por estructuras condicionales, loops y funciones.

##### Estructuras condicionales

```python
if expresion:
    # Código a ejecutarse
elif expresion:
    # Código a ejecutarse
elif expresion:
    # Código a ejecutarse
else:
    # Código a ejecutarse

# Expresión da rresultados booleanos (True / False)
# Los dos puntos : dan paso al código que se ejecuta si la expresión es True
# else y elif son opcionales
# Pueden incluirse varios elif
# La identación es obligatoria en Python
```

***

##### Loops for
Los loos, o bucles, son secuencias de instrucciones de código que se ejecutan repetidas veces.
Los iterables en Python, son objetos que se pueden recorrer o iterar a lo largo de sus elementos.


```python
for item in iterable:
    expresion

# Siendo item cada uno de los elementos que compone el iterable
# Siendo iterable una lista, una tupla, un diccionario, un set...
# La identación es obligatoria
# Los dos puntos dan paso a la expresión
# La expresión es el código que se ejecuta en cada iteracción.
```

***

##### Loops while
> Es una estructura de control de flujo que se utiliza para repetir un bloque de código mientas una conición específica sea verdadera.


```python
while condicion:
    expresion:

# La iddentación es obligatoria
# La expresión se ejecutará hasta que sea false.
```

Hay una serie de instrucciones especiales:
* Si el código llega a una instrucción break se producirá la salida del bucle.
* La instrucción continue interrumpe la iteración actual dentro del bucle, llevando el programa a la parte superior del bucle.
* La instrucción pass no altera el programa, pues ocupa un lugar donde se espera una declaración, pero no se desea realizar una acción.


```python
contador = 0
while True:
    print("Contador", contador)
    if contador == 2: break
    contador += 1
>> Contador 0
Contador 1
Contador 2
# Ejemplo con la instrucción break
# La coma (,) en el print actua como un separador, y añade un espacio.
# Recuerda que con la coma hacemos una concatenación
```

```python
contador = 0
while contador < 5:
    contador += 1
    if contador == 3: continue
    print("Contador", contador)

>> Contador 1
Contador 2
Contador 4
Contador 5

# Ejemplo con la instrucción continue
# Si es solo una expresión, el if se puede usar en la misma línea
```

```python
contador = 0
while contador < 5:
    if contador == 2:
        pass
    else:
        print("Contador", contador)
    contador += 1

>> Contador 0
Contador 1
Contador 3
Contador 4

# Ejemplo con la instrucción pass
```

No confundamos pass con continue. La sentencia continue hace que el programa salte a la siguiente iteración del bucle, mientras que pass simplemente no hace nada y permite que el flujo de control continúe sin interrupciones.

***

##### Range ()
> Esta función devuelve una secuencia de números dados 3 parámetros. Se utiliza para controlar el número de ejecuciones de un loop o para crear rápidamente una serie de valores.

```python
range(valor_inicio, valor_final, paso)
# Siendo valor_inicio el número a partir del cual inicia el rango(incluido)
# Siendo valor_final el número antes el cual el rango finaliza (no incluido)
# Siendo paso la diferencia entre cada valor consecutivo de la secuencia
```

```python
print(list(range(1, 13, 3)))
>> [1, 4, 7, 10]
```

El único parámetro obligatorio es valor_final. Los valores predeterminados para valor_inicio y paso son 0 y 1 respectivamente.

***

##### Enumerate ()
> Esta función nos facilita llevar la cuenta de las iteraciones, a través de un contador de índices de un iterable, que se puede usar de manera directa en un loop, o convertirse en una lista de tuplas con el método list()

```python
enumerate(iterable, inicio)
# Siendo iterable cualquier objeto que pueda ser iterado
# Siendo inicio el valor [int] de inicio del índice (por defecto empieza en 0)
```

Aquí te dejo dos ejemplos distintos para que veas bien el funcionamiento de esta función. Uno con un string y otro con un bucle.

```python
print(list(enumerate("Hola")))
>> [(0, 'H'), (1, 'o'), (2, 'l'), (3, 'a')]
```

```python
for indice, numero in enumerate([7.89, 12, 22.23]):
	print(indice, numero)
>> 0 7.89
>> 1 12 
>> 2 22.23
```

***

##### Zip ()
> Esta función crea un iterador formado por los elementos agrupados del mismo índice, provenientes de dos o más iterables. La función se detiene en el momento en el que se agota el iterable con menor cantidad de elementos.

```python
deportes = ["Baseball", "Baloncesto", "Fútbol"]
lenguajes = ["Java", "Python", "JavaScript", "PHP", "SQL"]
for deporte, lenguaje in zip(deportes, lenguajes):
	print(f'Deporte: {deporte}, y Lenguaje: {lenguaje}')

>> Deporte: Baseball, y Lenguaje: Java
>> Deporte: Baloncesto, y Lenguaje: Python
>> Deporte: Fútbol, y Lenguaje: JavaScript

# Si lo ves bien, no continua porque el array de deportes ya se ha agotado.
```

***

##### Min () y Max ()
> La función min() retorna el item con el valor más bajo dentro de un iterable, y max() funciona igual solo que nos devuelve el valor más alto del iterable. Si el iterable contiene strings, la comparación se realiza alfabéticamente.

```python
ciudades = {"Jerez": 212730, "Córdoba": 1914778}
valores = [6**3, 25**2, 12755, 986*2]

print(min(ciudades.keys()))
>> Córdoba

print(max(ciudades.values()))
>> 1914778

print(max(valores))
>> 12755
```

*** 

##### Random 
> Python nos facilita un módulo (conjunto de funciones disponibles para usarlas) que nos permite generar selecciones pseudo-aleatorias* entre valores o secuencias.

```python
from random import * 

# Siendo random el nombre del módulo
# Siendo * todos los métodos (pueden importarse de manera independiente)
```

**randint(min, max)** devuelve un integer entre dos valores dados (ambos límites incluidos)

```python
from random import randint
print(randint(4, 8))
>> 5 # Puede dar desde el 4 al 8
```

**uniform(min, max)** nos devuelve un float entre un valor mínimo y uno máximo (ambos incluidos)
```python
from random import uniform
print(uniform(3, 9))
>> 7.084372887608455 # Puede dar cualquiera del 3 al 9 de forma flotante
```

**random()** devuelve un float entre 0 y 1 (el 0 está incluido pero el 1 no)

```python
from random import random
print(random())
>> 0.1545438631603282 # Puede ser un número flotante cualquiera del 0 al 1 (no se incluye)
```


con **choice(secuencia)** devolvemos un elemento al azar de una secuencia de valores (ya sean tuplas, listas, rangos, etc.)

```python
from random import choice
print(choice(["Hola", 89, "Python", 5.34, True]))
>> Python # Puede ser cualquier valor de la lista. Si lo ejecutas más veces se verá
```

**shuffle(secuecia)** coge una secuencia de valores mutables, como una lista, y la retorna cambiando el orden de sus elementos aleatoriamente. Es como barajar una baraja de cartas.

```python
from random import shuffle
lista = ["as de oros", "as de copas", "as de bastos", "as de espadas"]
shuffle(lista)
print(lista)
>> ['as de copas', 'as de bastos', 'as de espadas', 'as de oros']
```

> * → La mecánica en cómo se generan los valores aleatorios viene predefinida en “semillas”. Sirve para todos los usos habituales, pero no debe emplearse con fines de seguridad o criptográficos, ya que son vulnerables

***
##### Comprensión de listas
> La comprensión de listas ofrece una sintaxis más breve en la creación de una nueva lista basada en valores disponibles en otra secuencia. Se consigue brevedad a costa de una menor interpretabilidad

```python
nueva_lista = [expresion for item in iterable if condicion == True]
# Siendo expresión el valor que se incluirá en la nueva lista
# Siendo elemento la variable que representa cada elemento del iterable
# Siendo iterable cualquier objeto que se pueda iterar, como una lista
# Siendo condicion una expresión opcional que filtra elementos del iterable.

# Hay un caso especial con else:
nueva_lista = [expresion if condicion == True else otra_expresion for item in iterable] 
```

```python
# Comprensión de lista básica
cuadrados = [num**2 for num in range(1, 6)]
print(cuadrados)
>> [1, 4, 9, 16, 25]

# Comprensión de lista con condición
pares = [num for num in range(1, 11) if num %2 == 0]
print(pares)
>> [2, 4, 6, 8, 10]

# Comprensión de lista con expresión condicional
resultados = ['par' if num % 2 == 0 else 'impar' for num in range(1,6)]
print(resultados)
>> ['impar', 'par', 'impar', 'par', 'impar']

# Comprensión de lista anidada
matriz = [[j for j in range(1, 4)] for i in range(3)]
print(matriz)
>> [[1, 2, 3], [1, 2, 3], [1, 2, 3]]
```

La comprensión de listas es muy versátil y se puede usar en una variedad de situaciones para crear y transformar listas de manera eficiente y legible

*** 

##### Match
> En Python 3.10 se incorpora la coincidencia de patrones estructurales mediante las declaraciones match y case. Esto permite asociar acciones específicas basadas en las formas o patrones de tipos de datos complejos.


```python
numero = 3

match numero:
    case 1:
        print("Lunes")
    case 2:
        print("Martes")
    case 3:
        print("Miércoles")
    case 4:
        print("Jueves")
    case 5:
        print("Viernes")
    case 6:
        print("Sábado")
    case 7:
        print("Domingo")
    case _:
        print("Número inválido")

>> Miércoles
```

Match es especialmente útil cuando se tienen múltiples condiciones que verificar. Es más flexible que las declaraciones if…elif…else, ya que permite la desestructuración de datos y combinaciones de patrones más complejas.

***