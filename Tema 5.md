# Tema 5
***
##### Documentación
> La documentación es nuestra biblioteca de consulta en Python. Al escribir código, podemos recurrir a dicha biblioteca para solucionar dudas relacionadas al funcionamiento de métodos y los argumentos que reciben.

Si usas PyCharm, debes poner el cursor sobre el nombre del método del que deseas obtener información. Se desplegará una ventana flotante.

![Imagen Documentación](https://origin2.cdn.componentsource.com/sites/default/files/styles/image_large/public/images/product_description/jetbrains/pycharm/img_484761.png?itok=fzUvDh7R)

Esto funciona de la misma forma en otros IDEs.
Además, deberías tener cerca la documentación oficial de Python, o Biblioteca Estándar de Python, que contiene toda la información necesaria para que puedas ampliar conocimientos, o para ojearla si tienes dudas sobre algo específico. 
Puedes acceder a ella a través de este [enlace](https://docs.python.org/es/3.12/library/index.html).

Para completar el tema de la documentación, vamos a hablar sobre la documentación del código. Como has ido viendo los temas en orden, te habrás dado cuenta que en todos los ejemplos, o casi todos, hay líneas de texto que comienzan con un ‘#’, ¿verdad?, pues esto es un comentario de código.
Los comentarios son líneas de texto que se utilizan para explicar el código, y no se ejecutan. Se escriben precedidos por el símbolo “#”, y pueden estar al principio de una línea, o después del código. 

Sirve para hacer el cóigo más legible y comprensible para otros programadores:

``` python
# Esto es una línea de código
# Ahora hremos un print
print("Hola Python") # Esto también es un comentario
```

También existen los comentarios multilínea, que se pueden crear utilizando triple comillas simples o triples comillas dobles. Todo el texto entre estas triples comillas se considera un comentario y no se ejecutará:

``` python
"""
Este es un comentario
que incluye varias líneas de código
Puedes poner las líneas que quieras
sin tener que usar # en cada una.
"""
print("Hola Python")
```

> Es una buena práctica comentar tu código para explicar qué hace una función, o qué retorna, o explicar los parámetros que usa una función. Es muy útil, y es recomendable que comiences a poner en práctica la documentación del código junto con los comentarios

***

##### Funciones
> Es un bloque de código que solamente se ejecuta cuando es llamado. Puede recibir información (en forma de parámetro), y devolver datos una vez procesados como resultado.

``` python
def mi_funcion(argumento):

# Siendo def la palabra clave con la que definimos una función
# Siendo argumento la información que la función utiliza o transforma para devolver algo.
```

Para llamar a una función, basta con usar su nombre, dándole los argumentos que la misma requiera entre paréntesis:

``` python
mi_funcion(mi_argumento)
```

``` python
def suma(a, b):
    # Esta función recibe dos números y devuelve la suma de los mismos
    resultado = a + b
    return resultado

# Aquí hacemos print de la función
print(suma(3, 5))
>> 8

# También podemos almacenar ese valor
resultado_suma = suma(3, 5)
print("El resultado de la suma es:", resultado_suma)
>> El resultado de la suma es: 8

# Recuerda que la identación es obligatoria.
```

***

##### Return
> Para que una función pueda devolver un valor (y que pueda ser almacenado en una variable, por ejemplo), utilizamos la declaración return.

``` python
def mi_funcion():
    return algo

# La declaración return provoca la salida de la función
# Cualquier código que se encuentre después en el bloque de la función no se ejecutará.

resultado = mi_funcion()

# La variable resultado almacena el valor devuelto por la función mi_funcion()
```

***

##### Funciones dinámicas
> La integración de diferentes herramientas de control de flujo, nos permite crear funciones dinámicas y flexibles. Si debemos utilizarlas varias veces, lograremos un programa más limpio y sencillo de mantener, evitando repeticiones de código.

``` python
# Funciones
# Loops
# Estructuras condicionales
# Palabras clave ( return, break, continue, pass)

def mi_funcion(argumento):
    for item in...
        if a == b ...
            ...
        else:
            return ...
    return ...
```

Para llevarlo a un ejemplo, podemos hacer la secuencia de sucesión de Fibonacci en una función práctica, que nos muestre cómo podemos poner el código y controlarlo:

``` python
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n - 1) + fibonacci( n - 2)

# Ejemplo de uso
numero_fibonacci = 7
resultado = fibonacci(numero_fibonacci)
print(f"El {numero_fibonacci}-ésimo número de Fibonacci es: {resultado}")

>>El 7-ésimo número de Fibonacci es: 13
```

``` python
# Ejemplo de uso
videojuegos = [("Kingdom Hearts", 8.7), ("Crash Bandicoot", 8.6), ("God of War", 9.2), ("Animal Crossing", 9.5), ("Dead by Daylight", 8.2), ("Pokemon Esmeralda", 9.7)]

def maxima_puntuacion(videojuegos):
    # Si la tupla está vacía retorna None
    if not videojuegos:
        return None

    # Suponemos que este es el videojuego con mayor puntuación
    videojuego_max_puntuacion = videojuegos[0]

    # Recorremos la tupla
    for videojuego, puntuacion in videojuegos:
        if puntuacion > videojuego_max_puntuacion[1]:
            videojuego_max_puntuacion = (videojuego, puntuacion)

    # Retornamos el videojuego con máxima puntuación
    return videojuego_max_puntuacion

# Guardamos lo que retorna la función en la lista de videojuegos
resultado = maxima_puntuacion(videojuegos)
print(f"El videojuego con máxima puntuación es {resultado[0]}")
```

***

##### Interacción entre funciones
> Las salidas de una determinada función pueden convertirse en entradas de otras funciones. De esa manera, cada función realiza una tarea definida, y el programa se construye a partir de la interacción entre funciones.

``` python
def funcion_1():
    ...
    return a

def funcion_2(a):
    ...
    return b

def funcion_3(b):
    ...
    return c

def funcion_1(a, c):
    ...
    return d
```

Así puede parecer algo confuso, así que a continuación te pongo un ejemplo práctico que espero que te quede claro su uso.

``` python
from random import shuffle

# Lista inicial
elementos = ['-', '--', '---', '----']

# Mezclar elementos
def mezclar(lista):
    shuffle(lista)
    return lista

# Pedir intento
def probar_suerte():
    intento = ''

    while intento not in ['1', '2', '3', '4']:
        intento = input("Elige un número del 1 al 4: ")

    return int(intento)

# Comprobar intento
def comprobar_intento(lista, intento):
    if lista[intento - 1] == '-':
        print(f"Te toca pagar {lista[intento - 1]}")
    else:
        print(f"No te toca pagar {lista[intento - 1]}")

elementos_mezclados = mezclar(elementos)
seleccion = probar_suerte()
comprobar_intento(elementos_mezclados, seleccion)
```

En este ejemplo, vemos un sorteo de a quién le toca pagar, y le toca al que saque el elemento más corto.
Como ves, se usan varias funciones, y puedes ver también funciones que usan variables con datos guardados de otras funciones. De esta manera interactúan estas funciones creadas en el ejemplo, para hacer que el programa esté controlado y sea funcional.

***

##### Argumentos indefinidos *args
> En aquellos casos en los que no se conoce previamente el número exacto de argumentos que se deben pasar a una función, se debe utilizar la sintaxis *args para referirse a todos los argumentos adicionales después de los obligatorios.

El nombre *args no es obligatorio, pero sí es sugerido como buena práctica. Cualquier nombre iniciado en * se referirá a estos argumentos de cantidad variable.

La función recibirá los argumentos indefinidos *args en forma de tupla, a los que se podrá acceder o iterar de las formas habituales dentro del bloque de código de la función.

``` python
def mi_funcion(arg_1, arg_2, *args):
# arg_1 = "ejemplos"
# arg_2 = 25
# *args sería igual, por ejemplo, a 32, 89, 101 en conjunto
```

A modo de ejemplo tienes la siguiente función suma:

``` python
def suma(*args):
    resultado = 0
    for numero in args:
        resultado += numero
    return resultado

print(suma(1, 2, 3))
>> 6
print(suma(4, 5, 6, 7))
>> 22
print(suma(10, 20, 30, 40, 50))
>> 150
```

***

##### Arguentos indefinidos *kwargs
> Se utiliza para pasar una cantidad variable de argumentos de palabras clave a una función. Los argumentos se recopilan en un diccionario dentro de la función.

Al igual que para los *args, el nombre **kwargs no es obligatorio, pero sí es considerado buena práctica. Cualquier nombre iniciado en ** se referirá a estos argumentos de cantidad variable.

``` python
def atributos_personas(**kwargs):
# Los **kwargs por ejemplo podrían ser {'altura': '1.82m', 'peso': '80kg'}
```

Como se hizo antes, pondremos un ejemplo para que puedas entender de forma práctica los **kwagrs:

``` python
def funcion_kwargs(**kwargs):
    for clave, valor in kwargs.items():
        print(f"{clave}: {valor}")
funcion_kwargs(a=1, b=2, c=3)
>> a: 1
>> b: 2
>> c: 3
```

***