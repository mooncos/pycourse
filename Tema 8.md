# Tema 8
***
### Instalar Paquetes
Una de las grandes ventajas de Python como lenguaje de programación, es que cuenta con una amplia comunidad activa, que desarrolla paquetes que añaden muchas más funcionalidades.
**PyPi** (**Python Package Index)** es el repositorio de referencia para hallar paquetes desarrollados por la comunidad.
Si ya conoces el nombre del módulo que quieres instalar, puedes obtenerlo de **PyPi** directamente desde la consola:

```bash
pip install <modulo>
```

También podrás actualizar los módulos que ya tengas instalados añadiendo –upgrade después del nombre del paquete:

```bash
pip install <modulo> --upgrade
```

Te animo a que busques todas las librerías que puedas para ver si encuentras alguna que te guste, y que así puedas implementarla en tu código y en tus proyectos, pues dispones de muchísimas de ellas.

Voy a dejarte una lista de librerías, con su funcionalidad y su forma de instalar:
* NumPy: Para la manipulación eficiente de matrices y operaciones matemáticas. Se usa, especialmente, para cálculos numéricos, álgebra lineal y manipulación de datos.
* Pandas: Perfecta para la manipulación y análisis de datos estructurados. Se usa para trabajar con conjuntos de datos tabulares (CSV, Excel), para limpieza y para transformación de datos.
* Matplotlib: Crea gráficos y visualizaciones. Perfecta para generación 2D y 3D y visualización de datos.
* Scikit-learn: Para el aprendizaje automático y minería de datos. Es ideal para la construcción, el entrenamiento y evaluación de modelos de machine learning.
* TensorFlow: Biblioteca de aprendizaje profundo y machine learning. Se usa para el desarrollo de modelos de redes neuronales y aprendizaje profundo.
* PyTorch: Especialmente para machine learning y desarrollo de modelos de aprendizaje profundo, como TensorFlow. También es muy buena para el desarrollo de modelos de redes neuronales y entrenamiento de estos.
* Django: Para el desarrollo rápido y limpio de aplicaciones web. Se usa especialmente para la construcción de aplicaciones web escalables y mantenibles.
* Flask: Marco ligero y flexible. Para el desarrollo rápido de aplicaciones web más simples y pequeñas.
* Requests: Trabaja con solicitudes HTTP. Perfecta para realizar peticiones a APIs web e interactuar con servicios web.
* Beautiful soup: Se usa para el web scraping y la extracción de datos. Está en el campo del análisis de datos web.

>Si a estas alturas te estás preguntando la diferencia entre librerías, yo te la doy: están las librerías internas, que están incorporadas en la biblioteca estándar de Python, a las cuales se accede con el “import” y el nombre de dicha librería; y están estas que acabamos de ver, que son librerías externas, por tanto, se tienen que instalar, y yo te dejo el código de ejemplo de todas estas, para que veas cómo se hace:

```bash
pip install numpy

pip install pandas

pip install matplotlib

pip install scrikit-learn

pip install tensorflow

pip install torch

pip install django

pip install flask

pip install requests

pip install beautifulsoup4
```

No tienes que aprenderlas de memoria, pues puedes buscar su instalación en Google. Eso sí, tienes que tener instalado pip, para poder instalar las librerías. Por lo general, desde Python 3.4, pip se incluye en la instalación de Python. Para comprobar si tienes pip, ve a la consola y escribe:

```bash
pip --version
```

Aún así, solo tienes que acudir a Google para instalarlo o actualizarlo

***
### Módulos y paquetes
Los módulos no son más que archivos .py, que almacenan funciones, variables y clases, y pueden ser importados por otros. Los paquetes agrupan estos módulos en carpetas, de los cuales uno debe ser:
```python
__init__.py
```

```python
import modulo1

# Para importar un módulo
```

Si solo queremos importar una función del módulo:
```python
from modulo1 import funcion
```

Y podemos ejecutarlo desde la consola con:
```python
...> ruta python modulo1.py
```

Si el módulo lo tenemos en un subpaquete:
```python
from paquete.subpaquete import modulo3
```

![modulos python](https://github.com/JuanCarlosFR26/imagen-modulos-python/blob/main/Imagen1.png?raw=true)

Todos los paquetes, para ser considerados como tales, deben contar con un archivo __init__.py (constructor).

Creamos el contenido del módulo 1:

```python
# contenido del modulo1.py
def funcion_modulo1():
    print("Función en el módulo 1")
```

Ahora creamos el contenido del módulo 2:

```python
# contenido del modulo1.py
def funcion_modulo2():
    print("Función en el módulo 2")
```

Por último, nos vamos al fichero principal y los incluimos de la siguiente forma:

```python
# En tu script principal.py
from mi_paquete import modulo1, modulo2

modulo1.funcion_modulo1()
modulo2.funcion_modulo2()
```

***
### Manejo de errores
Existen estrategias para capturar y gestionar los errores que pueden presentarse al ejecutar un programa, con la intención de evitar un fallo mayor y controlar la información que se muestra al usuario:

```python
try:
    # Código que se ejecuta hasta finalizar o hasta que haya un error.
except:
    # Manejador de errores
else:
    # Se ejecuta únicamente cuando ninguna excepción haya sido detectada (sin errores)
finally:
    # Se ejecuta simepre
```

Dentro de **try** se encuentra el código que se ejecuta hasta finalizar, o hasta que se presenta un error (excepción).
El **except** contiene el manejador de errores, es decir, la respuesta del programa ante un error. Atrapa las excepciones que se presentan durante la ejecución del try.
El **else** engloba el código que se ejecutará únicamente cuando ninguna excepción haya sido detectada en la ejecución de try, es decir, cuando no hay errores. 
Por último, el **finally** se ejecutará siempre, se produzcan o no errores en el código. Hay que destacar, que tanto el else como el finally son completamente opcionales.
Es buena práctica capturar y manejar las excepciones posibles individualmente, para brindar información acerca del error y su posible solución:

```python
except ValueError:

except TypeError:

except FileNotFoundError:
```

Podemos verlo a través del siguiente ejemplo práctico:
```python
def dividir_numeros(dividendo, divisor):
    try:
        resultado = dividendo / divisor
    except ZeroDivisionError:
        print("Error: No puedes dividir por cero.")
    except TypeError:
        print("Error: Asegúrate de que ambos operandos son números.")
    else:
        print(f"La división de {dividendo} entre {divisor} es: {resultado}")
    finally:
        print("Este bloque se ejecuta siempre. Patata.")

# Ejemplo de uso
dividir_numeros(10, 2)
dividir_numeros(5, 0)

dividir_numeros("abc", 2)
```

Como ves en el ejemplo, estamos manejando las posibles excepciones que pueden darse al hacer una división, como intentar dividir por cero que nos lanzaría un error al tratarse de una indeterminación, o al intentar dividir un string y un número.
Si nos aseguramos de manejar estas posibles excepciones el código será más legible y estará a prueba de errores.

***
Ya que hemos empezado el tema mencionando las distintas librerías y cómo instalarlas con pip, aquí te traigo un verificador de código, de errores y de calidad para Python, siguiendo el estilo recomendado por PEP 8, la guía de estilo de Python. Es muy útil para el trabajo en equipo.
Se instala de la siguiente forma:

```bash
pip install pylint
```

Y se puede ejecutar desde la consola con:

```bash
pylint python.py -r y
```

Esto nos traerá un análisis de nuestro código, con las características que fueron evaluadas, errores y puntuaciones parciales.
Te traerá también una puntuación del código. A mayor puntuación, mayor será la calidad de tu código. Un umbral aceptable sería >= 7.00/10

`Your Code has been rated at 6.67/10`

***

### Unittest
Unit Testing es un método o herramienta utilizado en programación para determinar si un módulo o un conjunto de módulos de código funciona correctamente. Esta evaluación se realiza en un archivo independiente. En Python, se implementa desde el módulo incorporado Unittest.
Es una biblioteca integrada, por tanto, no tenemos que instalar nada. Imagina que quieres probar tu fichero “mi_archivo.py”. Creamos por otro lado un módulo nuevo para hacer las pruebas, y podemos llamarlo “modulo_nuevo.py”, donde importaremos Unittest e importaremos también el módulo que queremos probar. Creamos una clase Prueba que hereda el método TestCase para hacer las pruebas que necesitemos:

```python
import unittest
import mimodulo

class NombrePrueba(unittest.TestCase):
    def tetst_prueba(self):
        primer_valor = {algo}
        segundo_valor = {salida de mmodulo.funcion}
        self.assertEqual(primer_valor, segundo_valor, mensaje)

if __name__ == '__main__':
    unittset.main()
```

Puede parecer un poco complicado, así como lo ves, sobre todo la parte del condicional:
```python
if __name__ == '__main__':
    unittset.main()
```

No voy a darte una explicación muy detallada, pues no es necesaria, pero te voy a explicar por qué es así: La mayoría de los lenguajes de programación tienen una clase llamada Main (principal) para que el sistema sepa que tiene que comenzar por esa clase, pero Python no funciona así y esta es una manera de hacerle saber al sistema qué función tiene que ejecutar y cuál no.
En el ejemplo, los dos primeros argumentos de assertEqual son dos valores que se comparan para establecer si hay igualdad entre ellos. Por eso, uno debe obtenerse a partir de una función del módulo que es evaluado, y otro debe ser la salida esperada para una misma entrada de información que en el primer caso. El tercer parámetro (mensaje), contendrá un string con información que se mostrará al usuario en caso de que el test falle.
Vamos a verlo con un ejemplo práctico para que veas que no es tan complejo como suena.
Vamos a crear un directorio que sea así:
![directorio](https://github.com/JuanCarlosFR26/imagen-modulos-python/blob/main/Imagen2.png?raw=true)

En nuestro fichero “suma.py” crearemos una función que queremos probar:
```python
def sumar(a, b):
    return a + b
```

Y en el fichero “prueba.py” añadiremos el código del ejemplo:

```python
import unittest

# Importamos la función que queremos probar
from suma import sumar

# Clase de prueba que hereda de unittest.Testcase
class TestSuma(unittest.TestCase):
    # Método de prueba para verificar si la función sumar funciona correctamente
    def test_sumar(self):
        # Comprueba si sumar 2 + 3 devuelve 5
        self.assertEqual(sumar(2, 3), 5)
        # comprobar si sumar -1 + 5 devuelve 4
        self.assertEqual(sumar(-1, 5), 4)

# Si ejecutas este script directamente, ejecutará las pruebas
if __name__ == '__main__':
    unittest.main()
```

Puedes hacer las pruebas que necesites hasta cogerle el truco, ya verás que no es nada difícil.

Al ejecutarlo, nos mostrará en pantalla lo siguiente:
```bash
----------------------------------------------------
Ran 1 test int 0.00s

Ok
```

Nos dice el tiempo que ha tardado en probarlo y el resultado es “ok”.

***
### Decoradores
Los decoradores son patrones de diseño en Python, utilizados para dar nueva funcionalidad a objetos (funciones), modificando su comportamiento sin alterar su estructura: son funciones que modifican funciones.
Las funciones en Python soportan operaciones tales como ser asignadas a una variable, pasadas como argumento, y ser devueltas por otra función como resultado. También, es posible definir funciones dentro de funciones, sin que estén disponibles fuera de la función en la que fueron definidas.
Los decoradores permiten que una función se modifique ante determinados escenarios, sin duplicar código:

```python
# Definimos un decorador llamado "decorador_ejempo

def decorador_ejemplo(funcion):
    def wrapper():
        prnt("Antes de llamar a la función...")
        funcion() # Llamamlos a la función original
        print("Después de llamar a la función...")
    return wrapper

# Definimos una función que será decorada
def funcion_a_decorar():
    print("Esta es la función que será decorada")

# Decoramos la función utilizando el decorador "decorador_ejemplo"
funcion_a_decorar_decorada = decorador_ejemplo(funcion_a_decorar)

# Llamamos a la función decorada
funcion_a_decorar_decorada()
```

Como siempre, vamos a verlo con ejemplos para que quede más claro.

```python
import time

# Definimos un decorador llamado "calcular_tiempo"
def calcular_tiempo(func):
    def wrapper(*args, **kwargs):
        inicio = time.time() # Tiempo inicial
        resultado = func(*args, **kwargs) # Llamamos a la función original
        fin = time.time() # tiempo final
        print(f"Tiempo de ejecución de '{func.__name__}': {fin - inicio} segundos")
        return resultado
    return wrapper

# Decoramos una función utilizando el decorador @calcular_tiempo
@calcular_tiempo
def suma(a, b):
    time.sleep(1) # Simulamos una operación que toma 1 segundo
    return a + b

# Llamamos a la función decorada
print(suma(5, 3))
```

En este ejemplo, el decorador “calcular_tiempo” coge una función como argumento (func), y devuelve otra función (wrapper). Esta función “wrapper” calcula el tiempo antes y después de llamar a la función original “func”, y luego imprime el tiempo de ejecución. Finalmente, llamamos a la función decorada “suma(5, 3)”, la cuál imprimirá el tiempo de ejecución de la suma de los números 5 y 3.
Los decoradores pueden usarse para hacer un registro y un seguimiento de la ejecución de funciones; sirven para autenticación y autorización de usuarios antes de ejecutar una función; para validación de entradas o manejo de errores, etc.

***
### Generadores
Los generadores son tipos especiales de funciones que devuelven un iterador que no almacena su contenido completo en memoria, sino que “retrasa” la ejecución de una expresión hasta que su valor se solicita.

Imagina que queremos usar una función que nos devuelva el número 28. Con una función normal tendríamos que hacer:

```python
def mi_funcion():
    return 28
```
Pero con un generaddor sería:

```python
def mi_generador():
    yield 28
```

Como ves, utiliza “yield” en lugar de “return”. La diferencia es que return produce el 28 y nos lo devuelve, sin embargo, el generador se prepara para que cuando le pidamos el número lo produzca en el momento.
Si llamamos a ambas, los resultados serían:

```python
def mi_funcion():
    return 28

def mi_generador():
    yield 28

print(mi_funcion())
print(mi_generador())

>> 28
>> <generator object mi_generador at 0x0000023B9FB58CA0>
```

Primero el número 28 al imprimir la función, pero al imprimir el generador no nos lo da como tal, sino que nos devuelve un código que indica que hay un objeto de la clase generador y que existe, pero no ha producido el 28 aún.
Vamos a guardar el generador en una variable y vamos a acceder a él para que nos dé el número:

```python
def mi_funcion():
    return 28

def mi_generador():
    yield 28

print(mi_funcion())
print(mi_generador())

generaddor = mi_generador()

print(next(generador))

>> 28
>> <generator object mi_generador at 0x0000023B9FB58CA0>
>> 28
```

Como ves, se ha usado “next” para acceder al generador para indicarle que produzca el número que tiene que producir. En este caso no se le puede pedir nuevamente porque no tiene más para mostrar.
Vamos a verlo con un ejemplo más funcional:

```python
def obtener_pares_funcion(n):
    pares = []
    for i in range(n):
        pares.append(i * 2)
    return pares

# Uso de la función
resultado_funcion = obtener_pares_funcion(5)
print(resultado_funcion)

def obtener_pares_generador(n):
    for i in range(n):
        yield i * 2

# Uso del generador
generador_pares = obtener_pares_generador(5)

print(next(generador_pares))
print(next(generador_pares))
print(next(generador_pares))

>> [0, 2, 4, 6, 8]
>> 0
>> 2
>> 4
```

Como ves en el ejemplo, ambas hacen lo mismo, solo que el generador espera a que le pidamos con “next” que nos muestre el valor que corresponde en cada momento

***