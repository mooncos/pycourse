# Tema 9
***
### Módulo Collections
El módulo **Collections** amplía los tipos de contenedores disponibles en Python. Un contenedor almacena diferentes objetos y proporciona una nueva forma de acceder e iterar sobre los mismos.
Podemos empezar con Counter(contadores), que es una subclase del diccionario, usado para contar las repeticiones de cada elemento en un iterable, en forma de diccionario:

```python
from collections import Counter

# Lista de elementos
lista = ['a', 'b', 'c', 'a', 'b', 'a', 'd', 'e', 'a', 'b']

#contar la frecuencia de elementos en la lista
contador =  Counter(lista)

# Imprimir el resultado
print(contador)
```

Después tenemos **DefaultDict**, que es otra subclase del diccionario, usado para proporcionar valores por defecto para las claves que no existan, sin generar un mensaje de error. El valor por defecto puede ser un tipo de dato (int, list, etc.) o una función lambda que proporcione dicho valor directamente (lambda: “mi valor”):
Lambda es una función anónima o sin nombre. Sirve para definir funciones pequeñas y simples de una sola línea.

```python
from collections import defaultdict

# Creamos un defaultdict con un valor predeterminado de lista vacío
diccionario = defaultdict(list)

# Añadimos algunos elementos al diccionario
diccionario['frutas'].append('manzana')
diccionario['frutas'].append('mango')
diccionario['hortalizas'].append('zanahoria')

# Accedemos a una clave que no existe
print(diccionario['carnes']) # No genera un KeyError, devuelve una lista vacía por defecto

# Imprimimos el diccionario
print(diccionario)
```

Esto es muy útil para el recuento o agrupación de datos; para cacheo de resultados o para hacer grafos ponderados, donde las claves son los nodos y los valores son los nodos vecinos.
Por último, veremos **NamedTuple**, que devuelve una tupla donde las posiciones de sus elementos tienen un nombre, además de un número de índice como las tuplas tradicionales:

```python
from collections import namedtuple

# Definimos una namedtuple llamada 'Producto' con campos 'nombre', 'precio', y 'cantidad'

Producto = namedtuple('Producto', ['nombre', 'precio', 'cantidad'])

# Creamos una instancia de la namedtuple 'Producto' para un producto específico
producto1 = Producto(nombre="Camisa", precio=29.99, cantidad=50)

# Accedemos a los campos de la namedtuple
print("Nombre del producto:", producto1.nombre)
print("Precio del producto:", producto1.precio)
print("Cantiad dl producto:", producto1.cantidad)
```

NamedTuple es muy útil para la representación de datos estructurados, para hacer el código más legible y mantenible y, además, para crear una simplicidad en la manipulación de datos.

***
### Módulo Shutil & Os
El módulo Shutil ofrece funcionalidades de alto nivel sobre archivos, tales como copiar, crear, eliminar y mover entre directorios. También se verán métodos del módulo Os que cumplen con objetivos similares.

```python
import shutil
```

Con shutil, podemos mover ficheros de la siguiente forma:

```python
import shutil

shutil.move("prueba.txt", "C:\\Users\\Juanqui\\Desktop")
```

Recuerda que en Windows usamos ( \\ ). Primero ponemos el nombre del archivo que queremos mover, y luego la ruta. Se entiende que se mueve desde el directorio actual.

También podemos **eliminar** una carpeta indicada en el directorio, incluyendo todas las ramificaciones (subcarpetas y archivos), de manera definitiva y sin pasar por la papelera de reciclaje:

```python
import shutil

shutil.rmtree("C:\\Users\\Juanqui\\Desktop\\pruebas\\ficheros")
```
En este ejemplo, eliminaríamos la carpeta prueba que se encuentra en el escritorio.
También podemos copiar texto de un archivo a otro:

```python
import shutil
# Archivo origen
src_file = 'prueba.txt'

# Archivo destino
dst_file = 'copia.txt'

# Copiar el archivo desde la ruta de origen a la ruta de destino
shutil.copy(src_file, dst_file)

print(f"El Archivo '{src_file}' copiado exitosamente a '{dst_file}'")
```

Otras funciones que tenemos en Os que no hemos visto antes, son las siguientes que te voy a poner con sus ejemplos:

```python
import os

# Archivo para eliminar
archivo_a_eliinar = 'prueba.txt'

# Verificar si el archivo existe antes de intentar eliminarlo
if os.path.exists(archivo_a_eliminar):
    # Eliminar el archivo
    os.unlink(archivo_a_eliminar)
    print(f"Archivo '{archivo_a_eliminar} eliminado exitosamente'")
else:
    print(f"El archivo '{archivo_a_eliminar} no existe'")
```

En este ejemplo, vemos como con os.unlink, podemos eliminar un archivo si existe.

Con el siguiente ejemplo, te muestro cómo eliminar una carpeta vacía con Os:
```python
import os

os.rmdir("C:\\Users\\Juanqui\\Desktop\\carpeta")
```


Por último, con os.walk podremos recorrer un directorio, para devolver las carpetas, subcarpetas y archivos dentro de ellas en forma de tupla, a través de un generador.

```python
import os

# Directorio base a recorrer
directorio_base = "C:\\Users\\Juanqui\\Desktop\\carpeta"

# Recorremos el directorio base y sus subdirectorios utilizando os.walk
for directorio_actual, subdirectorios archivos in os.walk(directorio_base):
    print(f"Directorio actual: {directorio_actual}")
    print(f"Subdirectorios: {subdirectorios}")
    print(f"Archivos: {archivos}")
```

En el ejemplo, recorremos el directorio con un bucle y traemos directorio, subdirectorios y archivos.
***
### Módulo Datetime
Este módulo (incorporado en Python) puede importarse en proyectos para trabajar con fechas y horas, así como con intervalos y duraciones:

##### Fecha
Dentro de la fecha, tenemos el año, el mes y el día, que son integers comprendidos en los rangos de fechas “reales”, es decir, 12 meses y 31 días como máximo. Podemos extraer el año, el mes y el día individualmente, también:
```python
import datetime

# Fecha
mi_fecha = datetime.date(año, mes, dia)

# Año
year = mi_fecha.year
# Mes
mes = mi_fecha.month
# Díaa
dia = mi_fecha.day
```


##### Hora
Para la hora, todos los argumentos son opcionales (se asume que es 0 si no se indican), y deben estar comprendidos entre 0 y 24 para las horas, 0 y 60 para los minutos y segundos, y 0 y 1000000 para los microsegundos

```python
import datetime

mi_hora = datetime.time(hora, minuto, segundo, microsegundo)
```

Para completar, podemos unir fecha y hora:

```python
import datetime

fecha_hora = datetime.datetime(año, mes, dia, hora, minuto, segundo, microseg)
```

Podemos obtener el “ahora”, es decir, la fecha y la hora actual, además de poder obtener las horas, los minutos y los segundos:

```python
import datetime

# Fecha y hora actual
ahora = datetime.datetime.now()

# Hora
hora = ahora.hour
# Minuto
minuto = ahora.minuto

# Segundo
segundo = ahora.second
```

*** 

### Módulo para medir el tiempo

Podemos estudiar el tiempo transcurrido durante la ejecución de un código, para poder conocerlo mejor y tomar decisiones acerca de la vía más eficiente para resolver un problema. Tenemos dos módulos que nos ayudarán: time y timeit:
```python
import time

inicio = time.time()
# Código
final = time.time()
duracion = final - inicio

print(duracion)
```

Y para ver time con un ejemplo, tienes lo siguiente: 
```python
from datetime import datetime, time

# Crear un objeto datetime con fecha y hora
fecha_hora = datetime(2024, 2, 17, 12, 30, 0)

# obtener la parte de tiepo utilizando el método .time()
hora_actual = fecha_hora.time()

# Imprimir la parte de tiempo
print("Hora actual:", hora_actual)

# Acceder a componentes específicos de la hora
print("Hora:", hora_actual.hour)
print("Minuto:", hora_actual.minute)
print("Segundo:", hora_actual.second)
```

Para ver timeit, te lo dejo con un ejemplo directamente:

```python
import timeit

# Función simple que queremos medir
def ejemplo():
    suma = 0
    for i in range(100000):
        suma += i
    return suma

# Utilizar timeit para medir el tiempo de ejecución
tiempo_ejecucion = timeit.timeit(ejemplo, number= 100)

# Imprimir
print(f"El tiempo de ejecución: {tiempo_ejecucion} segundos")
```

En este ejemplo, “number” es la cantidad de veces que se evaluará el código para obtener su tiempo de ejecución mínimo.

***
### Math
Este módulo contiene un conjunto de métodos y constantes que se pueden utilizar para resolver tareas matemáticas de mayor complejidad. Es el equivalente a la calculadora científica dentro de Python.
Puede ayudarnos a resolver:
* Relaciones trigonométricas (seno, coseno, tangente, etc.).
* Funciones logarítmicas.
* Potencias y raíces.
* Combinatoria y permutaciones.
* Redondeos.
* Factoriales.

Es recomendable leer la documentación de acuerdo a las necesidades que puedas tener.
Las constantes que encontrarás son:
* Pi (3.1415…)
* e o Constante de Euler (2.7182…)
* Tau (6.2831…)
* Infinito (el concepto matemático de infinito positivo)
* Nulo (NaN: not a number)

```python
import math

# Ejemplo de funciones matemáticas

# Raiz cuadrada
numero = 25
raiz_cuadrada = math.sqrt(numero)

# Seno y coseno
angulo_rad = math.radians(45) # Convertir 45 grados a radianes
seno = math.sin(angulo_rad)
coseno = math.cos(angulo_rad)

print(f"Seno de 45 grados: {seno}")
print(f"Coseno de 45 grados: {coseno}")

# Valor absoluto
numero_negativo = -10
absoluto = math.fabs(numero_negativo)
print(f"Valor absoluto de {numero_negativo} = {absoluto}")

# Potencia
base = 2
exponente = 3
potencia = math.pow(base, exponente)
print(f"{base} elevado a la {exponente} es = {potencia}")

# Redondeo
numero_decimal = 3.75
redondeado = math.ceil(numero_decimal) # Redondeo hacia arriba
print(f"Redondeo hacia arriba de {numero_decimal} = {redondeado}")

# Valos máximo común
numeros = [24, 36, 48]
max_comun = math.gcd(*numeros)
print(f"el máximo común divisor de {numeros} es; {max_comun}")
```

Con estos dos ejemplos puedes ver más acerca de este módulo.

***
### Módulo Re

Una expresión regular es una secuencia de caracteres que forman un patrón de búsqueda determinado. Pueden ser utilizadas para verificar strings en búsqueda de un contenido o un patrón específico. Utilizamos el módulo re en Python.

```python
import re
```

Hay muchas funciones disponibles en este módulo, pero no vamos a verlas todas. Veremos 2 de ellas que son fundamentales, las otras puedes buscarlas directamente en su [docuumentación](https://docs.python.org/es/3/library/re.html)

Estas dos funciones que veremos son:
* search(): devuelve un objeto “match”, que contiene información acerca del hallazgo si se encuentra en algún punto del string.
* findall(): devuelve una lista que contiene todos los hallazgos del patrón.

Para formar patrones, utilizamos la siguiente lista de cuantificadores y caracteres especiales:

```python
[] un set de caracteres                           \d dígito numérico
. un caracter cualquier                           \D No numérico
^ inicia con                                      \w caracter alfanumérico
$ finaliza con                                    \W No alfanumérico
* cero o más ocurrencias                          \s espacio en blanco
+ una o más ocurrencias                           \S No espacio en blanco
{ } un número especificado de ocurrencias
? cero o una ocurrencia
| operador lógico "O"
```

Y te dejo un ejemplo para que veas cómo se lleva a la práctica:

```python
import re

patron = r'\b\d{3}-\d{2}-\d{4}\b'
cadena = "El número de seguro social de Juan es 123-45-6789 y el de María es 087-65-4321."

resultado = re.search(patron, cadena)

if resultado:
    print("Número de seguro social encontrado")
else:
    print("Número seguro social no encontrado")
```

***
### Comprimir y descomprimir archivos desde Python
El formato zip permite comprimir archivos sin pérdida de información, ahorrando espacio de almacenamiento y manteniendo documentos relacionados en un mismo archivo .zip.
Podemos usar el módulo zipfile:
```python
import zipfile
```

Podemos comprimir archivos:
```python
import zipfile

mi_zip = zipfile.ZipFile("archivo_comprimido.zip", "w") # Modo escritura
mi_zip.write("mi_archivo.txt") # Comprimimos archivo en mi_zip
mi_zip.close()
```

Y podemos descomprimir:
```python
import zipfile

mi_zip = zipfile.ZipFile("archivo_comprimido.zip", "r") 
mi_zip.extractall() # Extrae todos los archivos del Zip mi_zip
mi_zip.extract("mi_archivo.txt") # Extrae un archivo específico
```

Tiene más funciones, pero como siempre, debes buscarla en la documentación, pues no es necesario explicarlas todas.
Voy a dejarte un ejemplo de zipfile combinado con shutil:

```python
import zipfile
import shutil

# Para comprimir archivos:
shutil.make_archivos(archivo_destino, "zip", carpeta_origen)

# Para descomprimir archivos
shutil.unpack_archive(archivo_zip, nombre_carpeta_extraccion, "zip")
```

***