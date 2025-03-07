# Tema 3

---

# Booleanos

<aside>
🐍 Son tipos de datos binarios ( True / False ), que surgen de operaciones logicas, o pueden declararse explícitamente.

</aside>

### Operadores lógicos

```python
== # igual a
!= # diferente a
> # Mayor que
< # Menor que
>= # Mayor o igual que
<= # Menor o igual que

and # Significa Y. Devuelve True si dos declaraciones son True
or # Significa O. Devuelve True si al menos una declaración es True
not # Significa No. Invierte el valor de un booleano
```

---

# Listas

<aside>
🐍 Son secuencias ordenadas de datos. Pueden ser datos de cualquier tipo: strings, integers, floats, booleanos, listas, objetos, etc. Son tipos de datos mutables.

</aside>

Las listas son **mutables, ordenadas** y admite **duplicados.**

La mutabilidad se refiere a la capacidad de cambiar, agregar o eliminar elementos después de que la lista ha sido creada. 

La ordenación hace referencia a que las listas en Python mantienen el orden de los elementos según el orden en el que fueron agregados. 

Y que admita duplicados significa que los datos pueden estar repetidos dentro de una lista.

```python
lista_1 = ["C", "C++", "Python", "Java"]
lista_2 = ["PHP". "SQL", "React", "Angular"]
```

Podemos acceder a los elementos de una lista a través de sus índices [inicio : fin : paso]. El primer elemento no tiene índice 1, tiene índice 0.

```python
print(lista_1[1:3])
>> ["C++", "Python"]
```

Podemos ver la cantidad de elementos con la propiedad **len()**

```python
print(len(lista_2))
>> 4
```

Podemos hacer concatenación de varias listas con el símbolo **+**

```python
print(lista_1 + lista_2)
>> ['C', 'C++', 'Python', 'Java', 'PHP', 'SQL', 'React', 'Angular']
```

Vamos a ver diferentes funciones con el siguiente ejemplo

```python
lista_1 = ["JavaScript", "Python", "Django", "Git"]
lista_2 = ["SQL", "PHP", "Visual Studio", "Eclipse"]
lista_3 = ["d", "z", "f", "a", "j"]
lista_4 = [100, 24, 42, -1, 0]
```

Para **agregar** un elemento a una lista en el último lugar se usa **append()**

```python
lista_1.append("Perl")
print(lista_1)
>> ["JavaScript", "Python", "Django", "Git", "Perl"]
```

Para **ordenar** los elementos de una lista en su lugar, es decir, modifica la lista original reorganizando sus elementos de manera ascendente (por defecto) o descendente, se usa el método **sort()**. Este método no devuelve un nuevo objeto, solo ordena la lista existente.

```python
lista_3.sort()
print(lista_3)
>> ["a", "d", "f", "j", "z"]
```

Para **eliminar** un elemento de la lista con su índice usamos **pop()**. Devuelve el elemento que se ha eliminado

```python
print(lista_1.pop(4))
>> "Perl"
```

Podemos **invertir** el orden de los elementos en el lugar con **reverse()**. ⚠No es lo opuesto a **sort()**

```python
lista_4.reverse()
print(lista_4)
>> [0, -1, 42, 24, 100]
```

Podemos **insertar** un elemento en una posición específica con **insert()**

```python
lista_1.insert(3, "Ruby") # Ruby ocupará el índice 3.
print(lista_1)
>> ["JavaScript", "Python", "Django", "Ruby", "Git"]
```

Para **eliminar** el primer elemento  con el valor especificado se usa **remove()**

```python
lista_2.remove("PHP")
print(lista_2)
>> ["SQL", "Visual Studio", "Eclipse"]
```

Con **index()** devolvemos la posición del primer elemento con el valor especificado

```python
ocurrencia = lista_3.index("f")
print(ocurrencia)
>> 2
```

Con **count()** devolvemos la cantidad de veces que aparece un elemento en una lista

```python
ocurrencia = lista_4.count(0)
print(ocurrencia)
>> 1
```

Esto son solo algunos métodos de listas que tenemos en Python. Si quieres ver más métodos puedes acudir a la documentación oficial de Python a través del enlace: 

[5. Estructuras de datos](https://docs.python.org/es/3/tutorial/datastructures.html)

---

# index()

<aside>
🐍 Usamos el método index() para explorar strings, ya que permite hallar el índice de aparición de un caracter o cadena de caracteres dentro de un texto dado.

</aside>

```python
string.index(value, start, end)
# Sienddo string una variable que almacena un string
# siendo value el caracter o los caracteres buscados
# start es el índice desde el que se comienza a buscar
# end es el índice hasta el cual realiza la búsqueda. No se incluye.
cadena = "hola hola caracola"
print(cadena.index("l")
>> 2

print(cadena.index("l", 3)
>> 7

print(cadena.index("l", 3, 12)
>> 7

# Si no encuetra el valor lanza un error
```

Con **rindex()** hacemos lo mismo pero la búsqueda es en sentido inverso

```python
string.rindex(value, start, end)

cadena = "hola hola caracola"
print(cadena.rindex("l")
>> 16
```

Tanto el **start** como el **end** son opcionales.

Además, podemos devolver un caracter en el índice que le indiquemos al string

```python
string[i]
# Siendo i el índice

cadena ="hola hola caracola"
print(cadena[5])
> h
```

---

# Strings: Propiedades

Cuando trabajes con strings en Python, debes tener presente lo siguiente:

1. **Son inmutables:** Una vez creados, no pueden modificarse sus partes, pero sí pueden reasignarse los valores de las variables a través de métodos de strings.

```python
# Si hacemos lo siguiente nos dará un error
cadena = "Hola"

cadena[0] = "h"

>> TypeError: 'str' object does not support item assignment
```

1. **Son concatenables:** Es posible unir strings con el símbolo +

```python
cadena_1 = "Hola"
cadena_2 = "Python"
concatenacion = cadena_1 + " " + cadena_2

print(concatenacion)
>> Hola Python
```

1. **Son mutiplicables:** Es posible concatenar repeticiones de un string con el símbolo *

```python
cadena_1 = "Hola "
print(cadena_1 * 3)
>> Hola Hola Hola
```

1. **Son multilineales:** Pueden escribirse en varias líneas al encerrarse entre triples comillas simples (’’’ ‘’’) o dobles (””” “””)

```python
cadena_multilinea_doble = """Este es un ejemplo
con triple comilla doble
para crear una cadena de varias líneas."""
print(cadena_multilinea_doble)
>> Este es un ejemplo
con triple comilla doble
para crear una cadena de varias líneas.

# También puede hacerse con las comillas simples

cadena_multilinea_doble = '''Este es un ejemplo
con triple comilla doble
para crear una cadena de varias líneas.'''
print(cadena_multilinea_doble)
>> Este es un ejemplo
con triple comilla doble
para crear una cadena de varias líneas.
```

1. **Se puede determinar su longitud:** a través de la función **len()**

```python
cadena = "Esta es mi cadena de texto"
print(len(cadena))
>> 26
```

1. **Se puede verificar su contenido:** A través de las palabras claves **in** y **not in**. El resultado de esta verificación es un booleano (True / False)

```python
# Uso de in
cadena = "Hola Python"
resultado = "Python" in cadena
print(resultado)
>> True

# Uso de not in
cadena = "Hola Python"
resultado = "JavaScript" in cadena
print(resultado)
>> False
```

---

# Strings: Métodos

Podemos hacer distinciones entre los métodos de strings

## Métodos de análisis

**count():** Retorna el **número de veces que se repite** un conjunto de caracteres especificado.

```python
resultado = "Hola Python".count("Hola")
print(resultado)
>> 1
```

**find()** e **index():** Retornan la **ubicación** (comenzando desde cero) en la que se encuentra el argumento indicado. La diferencia es que **index** lanza un **ValueError** cuando el argumento no es encontrado, mientras **find** retorna **-1**

```python
resultado = "Hola Python".find("JavaScript")
print(resultado)
>> -1

# Recordad que es case sensitive, es decir, es sensible a mayúsculas
resultado = "Hola Python".find("python")
print(resultado)
>> -1 # Pues estamos buscando python con la p en minúsculas.
```

**rfind()** y **rindex():** Busca el conjunto de caracteres pero **desde el final.**

```python
resultado = "C:/python36/python/python.exe".rfind("/")
print(resultado)
>> 18
```

**startswith( )** y **endswith( )** indican si la cadena en cuestión comienza o termina con el conjunto de caracteres pasados como argumento, y retornan True o False en función de ello.

```python
resultado = "Hola Python".startswith("Hola")
print(resultado)
>> True

# Con endswith()
resultado = "Hola Python".endswith("Hola")
print(resultado)
>> False
```

**isdigit():** Devuelve **True** si todos los caracteres de la cadena son dígitos, o pueden formar números. Incluidos aquellos correspondientes a lenguas orientales.

```python
resultado = "abc123".isdigit()
print(resultado)
>> False
```

**isnumeric()**; Determina si todos los caracteres de la cadena son **números**, incluyendo también los caracteres de connotación numérica que no necesariamente son dígitos, como una fracción.

```python
resultado = "Ⅴ".isnumeric() # 5 en romano. No es la letra V
print(resultado)
>> True
```

**isdecimal():** Determina si todos los caracteres de la cadena son decimales; es decir, formados por dígitos del 0 al 9.

```python
resultado = "1234".isdecimal()
print(resultado)
>> True
```

Aquí te dejo una tabla para que diferencies isnumeric(), isdecimal(), isdigit():

| isdecimal() | isdigit() | isnumeric() | Ejemplo |
| --- | --- | --- | --- |
| True | True | True | "038", "੦੩੮", "０３８” |
| False  | True | True | "⁰³⁸", "🄀⒊⒏", "⓪③⑧” |
| False | False | True | "↉⅛⅘", "ⅠⅢⅧ", "⑩⑬㊿", "壹貳參” |
| False | False | False | "abc", "38.0", "-38” |

**isalnum():** Devuelve True si todos los caracteres de la cadena son alfanuméricos

```python
resultado = "1234abc".isalnum()
print(resultado)
>> True
```

**isalpha():** Devuelve True si todos los caracteres de la cadena son alfabéticos

```python
resultado = "1234abc".isalpha()
print(resultado)
>> False
```

**islower():** Devuelve True si todos los caracteres de la cadena son **minúsculas**

```python
resultado = "abcdef".islower()
print(resultado)
>> True
```

**isupper():** Devuelve True si todos los caracteres de la cadena son **mayúsculas**

```python
resultado = "ABCDE".isupper()
print(resultado)
>> True
```

**isprintable():** Devuelve True si todos los caracteres de la cadena son imprimibles, es decir, que no son caracteres especiales indicados por \

```python
resultado = "Hola \t Python!".isprintable()
print(resultado)
>> False
```

isspace(): **Devuelve True si todos los caracteres de la cadena son espacios**

```python
resultado = "Hola Python".isspace()
print(resultado)
>> False
```

### Métodos de transformación

<aside>
🐍 Como los strings son inmutables, los métodos a continuación no actúan sobre el objeto original, sino que retornan uno nuevo.

</aside>

**capitalize():** Retorna la cadena con su primera letra en mayúscula

```python
# Si hacemos lo siguiente
cadena = "hola Python"
cadena.capitalize()
print(cadena)
>> hola Python # Al ser inmutable no se modifica la cadena.

resultado = cadena.capitalize()
print(resultado)
>> Hola Python # Así sí sería posible
```

**encode():** Codifica la cadena con el mapa de caracteres especificado y retorna una instancia del tipo bytes

```python
cadena = "hola Python"
resultado = cadena.encode("utf-8")
print(resultado)
>> b'hola Python'
```

**replace():** Reemplaza una cadena por otra

```python
cadena = "Hola JavaScript"
resultado = cadena.replace("JavaScript", "Python")
print(resultado)
>> Hola Python
```

**lower():** Retorna una copia de la cadena con todas sus letras en minúsculas

```python
cadena = "HOLA PYTHON"
resultado = cadena.lower()
print(resultado)
>> hola python
```

**upper():** Retorna una copia de la cadena con todas sus letras en mayúsculas

```python
cadena = "hola python"
resultado = cadena.upper()
print(resultado)
>> HOLA PYTHON
```

**swapcase():** Cambia las mayúsculas por minúsculas y viceversa

```python
cadena = "Hola Python"
resultado = cadena.swapcase()
print(resultado)
>> hOLA pYTHON
```

strip( ), lstrip( ) y rstrip( ): remueven los espacios en blanco que preceden y/o suceden a la cadena.

```python
cadena = " hola Python "
resultado = cadena.strip()
print(resultado)
>> 'hola Python' # Usamos las comillas para que se vea la diferencia sin espacios
```

**center(), ljust(), rjust():** Alinean una cadena en el centro, la izquierda o la derecha. Un segundo argumento indica con qué caracteres se deben llenar los espacios vacíos, que por defecto es un espacio en blanco

```python
cadena = "Python"
resultado = cadena.center(10, "*")
print(resultado)
>> **Python**

# A la derecha
cadena = "Python"
resultado = cadena.rjust(10, "*")
print(resultado)
>> ****Python

# A la izquierda
cadena = "Python"
resultado = cadena.ljust(10, "*")
print(resultado)
>> Python****
```

### Métodos de separación y unión

**split():** Divide una cadena según un caracter separador (por defecto son espacios en blanco). Un segundo argumento indica cuál es el máximo de divisiones que puede tener lugar (-1 por defecto para representar una cantidad ilimitada). Devuelve una lista de subcadenas.

```python
cadena = "Hola Pyhton\nHola Python"
resultado = cadena.split()
print(resultado)
>> ['Hola', 'Pyhton', 'Hola', 'Python']

# Veamos otro ejemplo
	cadena = "Hola, cómo estás, hermano?"
	resultado = cadena.split(',')
	print(resultado)
>> ['Hola', ' cómo estás', ' hermano?']

# Y otro más
cadena = "2022-02-04"
resultado = cadena.split("-")
print(resultado)
>> ['2022', '02', '04']
```

**splitlines( ):** divide una cadena con cada aparición de un salto de línea. Devuelve una lista de subcadenas.

```python
cadena = "Hola \nPython"
resultado = cadena.splitlines()
print(resultado)
>> ['Hola ', 'Python']
```

**partition( ):** retorna una tupla de tres elementos: el bloque de caracteres anterior a la primera ocurrencia del separador, el separador mismo, y el bloque posterior.

```python
cadena = "Hola Python. Hola JavaScript"
resultado = cadena.partition(" ")
print(resultado)
>> ('Hola', ' ', 'Python. Hola JavaScript')
```

**rpartition( ):** opera del mismo modo que el anterior, pero partiendo de derecha a izquierda.

```python
cadena = "Hola Python. Hola JavaScript"
resultado = cadena.rpartition(" ")
print(resultado)
>> ('Hola Python. Hola', ' ', 'JavaScript')
```

**join( ):** debe ser llamado desde una cadena que actúa como separador para unir dentro de una misma cadena resultante los elementos de una lista. Devuelve los elementos en una sola cadena.

```python
cadena = ", "
resultado = cadena.join(["C", "Python", "Java", "JavaScript"])
print(resultado)
>> C, Python, Java, JavaScript
```

---

# Substrings

<aside>
🐍 Podemos extraer porciones de texto utilizando las herramientas de manipulación de strings, conocidas como slicing.

</aside>

```python
string[start:stop:step]
# Siendo string la variable que guarda una cadena
# Siendo start el índice de inicio del sub-string (incluído)
# Siendo stop el índice del final del sub-string (no incluído)
# Siendo step los pasos

saludo = "Hola_Python"
resultado = saludo[2:6]
print(resultado)
>> la_P

resultado = saludo[3::3]
print(resultado)
>> ayo

# Algo interesante que podemos hacer con slicing
resultado = saludo[::-1]
print(resultado)
>> nohtyP_aloH
```

---

# Tuplas

<aside>
🐍 O *tuples,* son estructuras de datos que almacenan múltiples elementos en una única variable. Se caracterizan por ser ordenadas e inmutables. Esta característica las hace más eficientes en memoria y a prueba de daños.

</aside>

```python
mi_tupla = (1, "dos", [12.56, "ocho"], (5.8, 12))
print(mi_tupla)
>> (1, 'dos', [12.56, 'ocho'], (5.8, 12))
```

Podemos acceder a sus datos. **Indexado**

```python
print(mi_tupla[2][0])
>> 12.56
```

Podemos hacerle **casting** (conversión de tipos de datos)

```python
lista = list(mi_tupla)
print(lista)
>> [1, 'dos', [12.56, 'ocho'], (5.8, 12)] # Ahora sería una lista, por tanto, mutable
```

Se le pueden extraer datos (unpacking)

```python
a, b, c, d = mi_tupla
print(a)
>> 1
```

---

# Diccionarios

<aside>
🐍 Son estructuras de datos que almacenan información en pares clave:valor. Son útiles para guardar y recuperar información a partir de los nombres de las claves. No usan índices

</aside>

```python
mi_diccionario = {"curso":"Python", "clase":"Diccionarios"}
```

Podemos agregarle nuevos datos, o modificarlos

```python
mi_diccionario["recursos"] = ["apuntes", "ejercicios"]
print(mi_diccionario)
>> {'curso': 'Python', 'clase': 'Diccionarios', 'recursos': ['apuntes', 'ejercicios']}
```

Podemos acceder a sus valores a través del nombre de las claves:

```python
print(mi_diccionario["recursos"][1])
>> ejercicios
```

Con los métodos keys(), values(), items(), podemos listar los nombres de las claves, los valores y pares clave:valor

```python
# Keys()
diccionario = {'a': 1, 'b': 2, 'c': 3}
claves = diccionario.keys()
print(claves)
>> dict_keys(['a', 'b', 'c'])

# Values()
diccionario = {'a': 1, 'b': 2, 'c': 3}
valores = diccionario.values()
print(valores)
>> dict_values([1, 2, 3])
# Items()
diccionario = {'a': 1, 'b': 2, 'c': 3}
elementos = diccionario.items()
print(elementos)
>> dict_items([('a', 1), ('b', 2), ('c', 3)])
```

<aside>
🐍 A partir de Python 3.7+, los diccionarios son tipos de datos ordenados, en el sentido que dicho orden se mantiene según su orden se inserción.

</aside>

---

# Sets y métodos

<aside>
🐍 Son otro tipo de estructuras de datos. Se diferencian de listas, tuplas y diccionarios porque son una colección mutable de elementos inmutables, no ordenados y sin datos repetidos.

</aside>

```python
set_1 = {1, 2, "tres"}
set_2 = {3, "tres"}
```

### Métodos

Podemos agregar un elemento al set con **add()**

```python
set_1.add(5)
print(set_1)
>> {1, 2, 5, 'tres'} o {1, 2, "tres", 5}
```

Con el método **clear()** removemos todos los elementos de un set:

```python
set_1.clear()
print(set_1)
>> set()
```

Podemos crear una copia del set con **copy()**

```python
set_3 = set_1.copy()
print(set_3)
>> {1, 2, 'tres'}
```

Con **difference(set)** retornamos el set formado por todos los elementos que únicamente existen en el set primero

```python
set_3 = set_1.difference(set_2)
print(set_3)
>> {1, 2}
```

También está **difference_update(set)** que remueve del primero todos los elementos comunes al 1 y 2

```python
set_1.difference_update(set_2)
print(set_1)
>> {1, 2}

```

Con **discard(item)** removemos un elemento del set

```python
set_1.discard("tres")
print(set_1)
>> {1, 2}
```

**intersection(set)** retorna el set formado por todos los elementos que existen en el 1 y en el 2 simultáneamente

```python
set_3 = set_1.intersection(set_2)
print(set_3)
>> {'tres'}
```

**intersection_update(set):** mantiene únicamente los elementos comunes al set 1 y set 2

```python
set_2.intersection_update(set_1)
print(set_2)
>> {'tres'}
```

Con **isdisjoint(set)** devolvemos True si el set 1 y el set 2 no tienen elementos en común

```python
conjunto = set_1.isdisjoint(set_2)
print(conjunto)
>> False
```

También podemos devolver True **con** issubset(set) si todos los elementos del set 2 están presentes en el set 1

```python
es_subset = set_2.issubset(set_1)
print(es_subset)
>> False
```

Y con **issuperset(set)** devolvemos True si el set 1 contiene todos los elementos del set 2

```python
es_superset = set_1.issuperset(set_2)
print(es_superset)
>> False
```

**pop()** elimina y retorna un elemento al azar del set

```python
aleatorio = set_1.pop()
print(aleatorio)
>> {1} # Si ejecutas de nuevo te puede devolver otro
```

Con **remove(item)** eliminamos un elemento del set, y si no existe arroja un error

```python
set_1.remove("tres")
print(set_1)
>> {1, 2}
```

**symmetric_difference(set)** retorna todos los elementos del set 1 y set 2, excepto aquellos que son comunes a los dos

```python
set_3 = set_2.symmetric_difference(set_1)
print(set_3)
>> {1, 2, 3}
```

Con **symmetric_difference_update(set)** eliminamos los elementos comunes al set 1 y set 2, agregando los que no están presentes en ambos a la vez

```python
set_2.symmetric_difference_update(set_1)
print(set_2)
>> {1, 2, 3}
```

**union(set)** retorna un set resultado de combinar el set 1 y el set 2, eliminando los datos duplicados

```python
set_3 = set_1.union(set_2)
print(set_3)
>> {1, 2, 'tres', 3}
```

**update(set)** inserta en el set 1 los elementos del set 2

```python
set_1.update(set_2)
print(set_1)
>> {1, 2, 3, 'tres'}
```