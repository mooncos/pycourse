# Tema 6
***

##### Abrir y leer archivos
> La manipulación de archivos desde Python se engloba bajo las funciones E/S (entrada/salida).

En este tema exploraremos las funciones utilizadas para abrir, leer y cerrar archivos. Para practicar, puedes crear en el directorio donde estás programando un fichero llamado “prueba.txt”, para practicar con él. Escribe lo que quieras dentro.

Empezaremos con **open(archivo, modo)**, que abre archivos, y devuelve un objeto de tipo archivo sobre el que pueden aplicarse métodos:

```python
mi_archivo = open("prueba.txt")

print(mi_archivo)
```

Podrás ver archivos con esta forma, pero no es lo idóneo, pues no verás el texto que contiene en el fichero. Al hacer esto con open recibirás algo así:

```python
<_io.TextIOWrapper name='pruba.txt' mode='r' encoding='cp1252'>
```

Ya ves que no es nada legible. Porr tanto, es necesario tratarlo de la siguiente forma:

```python
mi_archivo = open("prueba.txt")

print(mi_archivo,read())
>> Texto para mostrar
Segunda parte del texto
Ultima parte del texto
```

Ya aquí nos está mostrando lo que contiene el fichero llamado “prueba.txt”. Pero, recuerda que es necesario cerrarlo, porque cuando trabajemos con archivos mucho más grandes y necesitemos añadir más código nos ocupará mucha memoria si dejamos abierto el fichero de texto. Por tanto, quedaría mejor si hacemos esto:

```python
mi_archivo = open("prueba.txt")

print(mi_archivo,read())

# Resto del código

mi_archivo.close()
>> Texto para mostrar
Segunda parte del texto
Ultima parte del texto
```

Podemos trabajarlo de varias formas. Esta es una de ellas, mostrando el texto completo y cerrando el fichero.

También puede darse el caso de que solo quieras una línea, o mostrarlo de línea en línea, dependiendo de lo que requiera el proyecto en el que estás trabajando.
Por tanto, vamos a hacer otro ejemplo mostrándolo por líneas:

```python
mi_archivo = open("prueba.txt")

una_linea = mi_archivo.readline()
print(una_linea)

una_linea = mi_archivo.readline()
print(una_linea)

una_linea = mi_archivo.readline()
print(una_linea)


mi_archivo.close()

>> Texto para mostrar

Segunda parte del texto

Ultima parte del texto
```

Cuando ya tenemos el fichero abierto, podemos aplicarle métodos. Podemos ver varios en los siguientes ejemplos:
Podemos aplicar rstrip() para eliminar los espacios de la derecha:

```python
mi_archivo = open("prueba.txt")

una_linea = mi_archivo.readline()
print(una_linea.rstrip())

mi_archivo.close()

>> Texto para mostrar
```

Con upper() (que ya lo hemos visto antes también), podemos poner todo el texto en mayúsculas:

```python
mi_archivo = open("prueba.txt")

una_linea = mi_archivo.readline()
print(una_linea.upper())

mi_archivo.close()

>> TEXTO PARA MOSTRAR
```

Podemos crear un bucle para recorrerlo también:

```python
mi_archivo = open("prueba.txt")

for linea in mi_archivo:
    print("Esta línea dice: " + linea)

mi_archivo.close()

>> Esta línea dice: Texto para mostrar

Esta línea dice: Segunda parte del texto

Esta línea dice: Última parte del texto
```

Con readlines() (en plural), podremos mostrar una lista con los elementos del texto:

```python
mi_archivo = open("prueba.txt")

print(mi_archivo.readlines())

mi_archivo.close()

>> ['Texto para mostrar\n', 'Segunda parte ddel texto\n', 'Última parte del texto']
```

Y se le pueden aplicar muchos más métodos. Te animo a que los buses por tu cuenta en la documentación oficial. Tienes que acostumbrarte a buscar documentación

También tienes, como método alternativo, la siguiente forma de abrir archivos, que, aunque no sea necesario escribir el código así, siempre es bueno tener un código limpio y con buenas prácticas:

```python
with open('prueba.txt', 'r') as archivo:
    # Lee el contenido del archivo
    contenido = archivo.read()

# Imprimir o realizar otras operaciones con el contenido leído
print(contenido)
```

Pruébalo, te dará el mismo resultado. 

Te dejo a continuación, una lista con las funciones que más vas a usar, pero bien descritas para que las tengas a mano:
* open(archivo, modo): Abre un archivo, y devuelve un objeto de tipo archivo sobre el que pueden aplicarse métodos
* read(bytes): Devuelve un número especificado de bytes del archivo. De manera predeterminada (sin indicar un valor en el argumento bytes), devolverá el archivo completo (equivalente a escribir -1). Por lo general, un byte equivale a un carácter.
* readline(bytes): Devuelve una línea del archivo, limitada por el número indicado en el parámetro tamaño (en bytes). Por lo general, un byte equivale a un carácter.
* readlines(bytes): Devuelve una lista que contiene cada una de las líneas del archivo como ítem de dicha lista. Si el tamaño excede lo indicado en el parámetro bytes, no se devolverán líneas adicionales. Por lo general, un byte equivale a un carácter.
* close(): Cierra el archivo abierto. Es una buena práctica usar este método si ya no será necesario realizar acciones sobre un archivo.

***

##### Crear y escribir archivos

Ya hemos visto como abrir archivos y aplicarles métodos distintos. Pero, también podemos crear y escribir nuestros propios archivos desde Python. Sí, Python sirve para todo.

Para escribir un archivo desde Python, deberemos elegir con cuidado el parámetro “modo de apertura”.


```python
open(archivo, modo)
```

Tenemos los siguientes parámetros de modo de apertura:
* “r” – Read (Lectura) – Predeterminado. Permite leer, pero no escribir, y lanza un error si el archivo no existe.
* “a” – Append (Añadir) – Abre el archivo para añadir líneas al final del mismo. Si el archivo no existe, se creará uno nuevo. 
* “w” – Write (Escritura) – Abre o crea un archivo (si no existe previamente) en modo de escritura. Cualquier contenido previo en el archivo será sobrescrito. Si el archivo no existe, se crea uno nuevo. Este método escribe un texto especificado en el argumento sobre el archivo.
* “x” – Create (Creación) – Crea un archivo, pero lanza un error si el archivo ya existe en el directorio.
* “writelines” – (lista) – Recibe un texto a ser escrito en forma de lista, escribiendo cada elemento de la lista como una línea en el archivo.

Ya vimos formas de usar open en el apartado de abrir archivos, así que veremos directamente las formas de escribir código, pero con buenas prácticas. Tendrás varios ejemplos sobre cada método, para que puedas practicar después con los ejercicios del tema.

Con “read”, ya vimos varios ejemplos en su apartado, pero aquí tienes un ejemplo distinto con uno de los métodos:

```python
mi_archivo = open("prueba.txt", "r")

print(mi_archivo.read(10))

>> Texto para

# Solo lee los 10 primeros caracteres
```

Con el método “append” tienes los siguientes ejemplos:

```python
# Ejemplo 1: Añadir una línea al final del archivo
with open('prueba.txt', 'a') as archivo:
    archivo.write('\nEsta es una nueva línea añadida al final.\n')

# Ejemplo 2: Añadir múltiples líneas al final del archivo
lineas_nuevas = ['Línea 1\n', 'Línea 2\n', 'Línea 3\n']
with open('prueba.txt', 'a') as archivo:
    archivo.writelines(lineas_nuevas)

# Ejemplo 3: Añadir contenido de otro archivo al final del archivo
with open('otroarchivo.txt', 'r') as archivo_anexo:
    contenido_anexo = archivo_anexo.read()
    with open('prueba.txt', 'a') as archivo:
        archivo.write(contenido_anexo)
```

Con el método “write” tienes los siguientes ejemplos:

```python
# Ejemplo 1: Escribir en un archivo
with open('prueba.txt', 'w') as archivo:
    archivo.write('Este es el contenido que se escribirá en el archivo.\n')

# Ejemplo 2: Sobrescribir el contenido de un archivo
with open('prueba.txt', 'w') as archivo:
    archivo.write('Nuevo contenido que sobrescribirá el anterior.\n')
```

Y con “create” tienes el siguiente:

```python
# Ejemplo 1: Crear un archivo nuevo y escribir en él
with open('prueba.txt', 'x') as archivo:
    archivo.write('Este es un archivo recién creado.\n')
```

Cuando veas el apartado de manejo de errores, puedes volver aquí para ver estos dos ejemplos siguientes:

```python
# Ejemplo 2: Manejando el error al intentar crear un archivo que ya existe.
try:
    with open('nuevo_archivo.txt', 'x') as archivo:
        archivo.write('Este es un archivo recién creado.\n')
except FileExistsError:
    print("El archivo 'nuevo_archivo.txt' ya existe.")
else:
    print("El archivo 'nuevo_archivo.txt' se ha creado exitosamente")

# Ejemplo 3: Crear un archivo solo si no existe
try:
    with open('nuevo_archivo.txt', 'x') as archivo:
        archivo.write('Este es un archivo recién creado.\n')
except FileExistsError:
    print("El archivo 'nuevo_archivo.txt' ya existe.")
```

En estos dos ejemplos, manejamos errores por si ya existen los ficheros que intentamos crear.

***

##### Directorios
Para trabajar sobre archivos que se encuentran en otros directorios diferentes al de nuestro código, se necesitará usar el módulo “OS”, que contiene una serie de funciones para interactuar con el sistema operativo. Podremos importarlo con:

```python
import os
```

Para obtener y devolver el directorio del trabajo actual usamos **“os.getcwd”**, que será el mismo en el que corre el programa si no se ha modificado:

```python
import os

# Ejemplo: Obtener el directorio de trabajo actual
directorio_actual = os.getcwd()
print("Directorio arcual:", directorio_actual)
```

Con **“os.chdir(ruta)”** cambiamos el directorio de trabajo a la ruta especificada

```python
import os

# Ejemplo: Cambiar el directorio de trabajo a un directorio existente en Windows
os.chdir('C:/Users/Juanqui/Documents') #Cambia el directorio de trabajo
print("Directorio de trabajo cambiado a:", os.getcwd())
```

Con **“os.makedirs(ruta)”** creamos una carpeta, así como todas las carpetas intermedias necesarias de acuerdo a la ruta especificada:

```python
import os

# Ejemplo 1: Crear una carpeta con subcarpetas
os.makedirs('C:/Users/Juanqui/Desktop/Aprende Python/CarpetaCreada')
print("Carpeta y subcarpetas creadas")

# Ejemplo 2: Crear una carpeta con múltiples niveles de subcarpetas
os.makedirs('C:/Users/Juanqui/Desktop/Aprende Python/CarpetaCreada/Subcarpeta1')
print("Carpeta y subcarpetas creadas")
```

Dada una ruta, podemos obtener el nombre del archivo (nombre base) con **“os.path.basename(ruta)”**:

```python
import os

# Ejemplo: Obtener el nombre del archivo de una ruta
nombre_archivo = os.path.basename('C:/Users/Juanqui/Desktop/Aprende Python/directorios.py')
print("Nombre del archivo:", nombre_archivo)
```

Para obtener el directorio (carpeta que almacena un archivo) de una ruta usamos **“os.path.dirname(ruta)”**:
```python
import os

# Ejemplo: Obtener el directorio de una ruta
directorio = os.path.dirname('C:/Users/Juanqui/Desktop/Aprende Python/directorios.py')
print("Directorio:", directorio)
```

Para obtener una tupla con el directorio y el nombre de base del archivo usaremos **“os.path.split(ruta)”**:

```python
import os

# Ejemplo: Dividir una ruta en directorio y nombre de archivo
tupla_directorio = os.path.split('C:/Users/Juanqui/Desktop/Aprende Python/directorios.py')
print(tupla_directorio)
```
Por último, podremos eliminar el directorio indicado en la ruta con **“os.rmdir(ruta)”**:

```python
import os

# Ejemplo: Eliminar un directorio
os.rmdir('C:/Users/Juanqui/Desktop/Aprende Python/CarpetaCreada')
print("Directorio eliminado")
```

> Para terminar este apartado, quiero indicar que en Windows es necesario indicar las rutas con dobles barras inversas ( \\ ) para que sean correctamente interpretadas por Python.

***

##### Pathlib
Este módulo está disponible desde Python 3.4, y permite crear objetos Path, generando rutas que pueden ser interpretadas por diferentes sistemas operativos y cuentan con una serie de propiedades útiles. Un objeto Path es una representación de una ruta o ubicación en un sistema de archivos.

```python
from pathlib import Path
```

A partir de una semántica sencilla, devuelve una ruta que el sistema puede comprender:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop")
```

Por ejemplo, en Windows, devolverá: C:\Users\Usuario\Desktop.

###### Navegación
Es posible concatenar objetos Path y strings con el delimitador “/” para construir rutas completas:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop") / "archivo.txt"

print(ruta)
```

###### Métodos y propiedades sobre objetos Path
También tenemos métodos para trabajar con los objetos Path, y como siempre, te dejo algunos descritos con sus ejemplos. El resto puedes buscarlo tú en la documentación oficial:

Con **read_text()**, leemos el contenido del archivo sin necesidad de abrirlo y cerrarlo:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop/Aprende Python/texto.txt")

print(ruta.read_text())
```

Podemos usar **name**, que devuelve el nombre y extensión del archivo:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop/Aprende Python/texto.txt")

print(ruta.name)
```

Otro método interesante es **suffix**, que devuelve la extensión del archivo:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop/Aprende Python/texto.txt")

print(ruta.suffix)
```

Con stem, devolvemos el nombre del archivo sin su extensión:

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop/Aprende Python/texto.txt")

print(ruta.stem)
```

Y por último, con **exists()**, verificamos si el directorio o archivo al que referencia el objeto Path existe, y devuelve un booleano de acuerdo al resultado (True / False):

```python
from pathlib import Path

ruta = Path("C:/Users/Usuario/Desktop/Aprende Python/texto.txt")

print(ruta.exists())
```

***

##### Path
> La clase Path permite representar rutas de archivos en el sistema de archivos de nuesstro sistema operativo. Se destaca por su legibilidad frente a alternativas semejantes.

```python
from pathlib import Path

base = Path.home()

print(base)
```

Se aceptan strings y otros objetos Path:
```python
from pathlib import Path

base = Path.home()

ruta = Path(base, "Desktop", "Aprende Python", "prueba.txt")
```
Con el siguiente código devolvemos un nuevo objeto Path cambiando únicamente el nombre de archivo:
```python
from pathlib import Path

base = Path.home()

ruta = Path(base, "Desktop", "oficina", "Tema 1.md")

ruta2 = ruta.with_name("cambio.md")
```

Podemos conseguir devolver la ruta de jerarquía superior con la propiedad “parent”:

```python
from pathlib import Path

base = Path.home()

ruta = Path(base, "Desktop", "Inkor", "prueba_creacion_path.txt")

continente = ruta.parent.parent

print(continente)

>> C:\Users\...Europa
```

Podemos devolver un conjunto de archivos que coincidan con un patrón:

```python
from pathlib import Path

base = Path.home()

ruta = Path(base, "Desktop", "Inkor", "prueba_creacion_path.txt")

Path(ruta).glob("*.txt")
Path(ruta).glob("**/*.txt")
```

***

##### Limpiar la consola
> Para controlar la información mostrada al usuario en consola podemos limpiarla, eliminando los diferentes mensajes que han aparecido conforme se va ejecutando el programa.

```python
from os import system

# En Mac / Unix / Linux
system("clear")

# En DOS / Windows
system("cls")
```

***
##### Archivos más funciones
> A modo de recordatorio: puedes crear funciones para que ejecuten código cada vez que sean llamadas, evitando repeticiones y facilitando su lectura. Esto se aplica en todo Python, y desde luego también cuando manipulamos archivos.

```python
def manipular_archivo(ruta, nombre_archivo):
    # Código que convierte entradas en salidas
    return # La salida

# Siendo manipular_archivo lo que hace la función
# Siendo nombre_archivo la información que necesita recibir
```

***