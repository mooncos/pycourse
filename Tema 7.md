# Tema 7
***
La programación orientada a objetos es un modelo de programación en el que el diseño de software se organiza alrededor de datos u objetos, en vez de usar funciones y lógica. Se enfoca en los objetos que los programadores necesitan manipular, en lugar de centrarse en la lógica necesaria para esa manipulación.

Se basa en los conceptos de clases y objetos. Este tipo de programación se usa para estructurar un programa de software en piezas simples y reutilizables de planos de código (clases) para crear instancias individuales de objetos.

##### Clases

> Python es un lenguaje de Programación Orientado a Objetos. Como tal, utiliza y manipula objetos, a través de sus métodos y propiedades. Las clases son las herramientas que nos permiten crear objetos, que "empaquetan" datos y funcionalidad juntos.

Podemos pensar en las clases como la “receta” a partir de la cual podemos crear objetos individuales, con propiedades y métodos asociados:

```python
class Objeto: # Crear una clase
    #Código

nuevo_objeto = Objeto() # Creamos un objeto a partir de la clase
# Este objeto es una instancia de la clase
```

Como ejemplo, podemos crear la clase coche:

```python
class Coche:
    pass

mi_coche = Coche()
```

Puedes pensar, que ya puedes usar tu objeto coche, pero la realidad es que aún no tiene nada de código. De hecho, si usar print con el objeto obtendrás lo siguiente:

```python
class Coche:
    pass

mi_coche = Coche()

print(mi_coche)
>> <__main__,Coche object at 0x0000025055353350>
```

Sin embargo, si imprimimos el tipo del objeto nos dará:

```python
class Coche:
    pass

mi_coche = Coche()

print(type(mi_coche))
>> <class `__main__.Coche'>
```
Puedes crear todos los objetos que quieras a partir de su clase:

```python
class Coche:
    pass

mi_coche = Coche()
mi_coche2 = Coche()
coche_audi = Coche()
```

***

##### Atributos

> Los atributos son variables que pertenecen a la clase. Existen atributos de clase (compartidos por todas las instancias de la clase), y de instancia (que son distintos en cada instancia de la clase).

Cada objeto creado a partir de la clase puede compartir determinadas características, y estos son los atributos de clase (por ejemplo, cantidad de caras de un cubo).
Por otro lado, cada objeto creado a partir de a clase puede contener características específicas, que son los atributos de instancia (color, altura, ancho, etc.).

```python
class Cubo:
    caras = 6 # Atributo de clase
    def __init__(self, color):

        self.color = color # Atributo de instancia

# Los atributos de la función __init__ se entregan a los atributos de instancia
```

Todas las clases tienen una función que se ejecuta al instanciarla, llamada __init__(), y que se utilizar para asignar valores a las propiedades del objeto que está siendo creado. La palabra “self” representa a la instancia del objeto que se va a crear.
Para verlo mejor, te doy el siguiente ejemplo:

```python
class Cubo:
    def __init__(self, color, caras):
        self.color = color
        self.caras = caras

mi_cubo = Cubo("Verde", 4)

print(mi_cubo.color)
>> Verde
```

Y esto puedes usarlo en formateo de cadenas, por ejemplo, al guardarlo en una variable:
```python
class Cubo:
    def __init__(self, color, caras):
        self.color = color
        self.caras = caras

mi_cubo = Cubo("Verde", 4)

print(f"Mi cubo tiene {mi_cubo.caras} caras y es de color {mi_cubo.color}")
>> Mi cubo tiene 4 caras y es de color verde
```

***
##### Métodos
Los objetos creados a partir de clases también tienen métodos. Dicho de otra manera, los métodos son funciones que pertenecen al objeto.

```python
class Persona:
    especie = "humano"
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        print(f"Hola, mi nombre es {self.nombre}")
    def sumar_edad(self, humor):
        print(f"Cumplo, {self.edad + 1} años. Esto me pone {humor}")

javier = Persona("Javier", 39)

javier.sumar_edad("triste")
>> Cumpo 40 años. Esto me pone triste.
```

Cada vez que un atributo del objeto sea llamado (por ejemplo, en una función), debe incluirse self, que refiere la instancia en cuestión, indicando la pertenencia de este atributo.
***

##### Tipos de Métodos
Antes de continuar, tienes que saber que existe algo llamado decorador, que nos va a permitir crear diferentes tipos de métodos. 
Por un lado, los métodos de instancia, que son los que hemos realizado en el apartado anterior. También los métodos de clase, que se crean con “@classmethod”. Y, en tercer lugar, los métodos estáticos, con “@stathicmethod”.
Los métodos de instancia pueden:
* Acceder y modificar atributos del objeto
* Acceder a otros métodos
* Modificar el estado de la clase.

Los métodos de clase, se crean usando “@classmethod”, y en sus parámetros en vez de “self”, ponemos “cls”. Estos métodos están asociados a la clase en sí misma, por tanto, pueden ser llamados desde una instancia de nuestra clase y directamente desde la clase. Estos métodos no pueden acceder a los atributos de instancia, pero pueden modificar los atributos de la clase.
Los métodos estáticos, se crean usando “@staticmethod”, y no aceptan como parámetro ni “self” ni “cls”, por eso no pueden modificar el estado ni de la clase ni de la instancia, pero pueden aceptar parámetros de entrada. Pueden resultar útil para indicar que un método no podrá modificar nada ni de la clase ni de la instancia. 

Primero veremos ejemplos los métodos de instancia. Vamos a empezar viendo cómo modifican las características de los objetos:
```python
class Coche:
    def __init__(self, color, puertas, matricula):
        self.color = color
        self.puertas = puertas
        self.matricula = matricula

    def pintar_coche(self, color):
        self.color = color
        print(f"Ahora el coche es de color {color}")

mi_coche = Coche("rojo", 4, "3127FNY")

mi_coche.pintar_coche("Violeta")
print(mi_coche.color)
>> Ahora el coche es de color Violeta
>> Violeta
```

Y modificando el código, veremos cómo acceder a otros métodos:

```python
class Coche:
    def __init__(self, color, puertas, matricula):
        self.color = color
        self.puertas = puertas
        self.matricula = matricula

    def tocar_claxon(self):
        print("piiiiiii")
    
    def arrancar(self):
        print("brrrrrr")
        self.tocar_claxon()

mi_coche = Coche("rojo", 4, "3127FNY")

mi_coche.arrancar()

>> brrrrrr
>> piiiiiiii
```

También están los métodos de clase. Se declaran con un decorador (@):

```python
class Coche:
    def __init__(self, color, puertas, matricula):
        self.color = color
        self.puertas = puertas
        self.matricula = matricula

    def tocar_claxon(self):
        print("piiiiiii")
    
    def arrancar(self):
        print("brrrrrr")
        self.tocar_claxon()

    @classmethod
    def pasar_itv(cls, precio):
        print(f"La itv cuesta", precio, "€.")

Coche.pasar_itv(20)
>> La itv cuesta 20 €.
```

Si observas la diferencia, empieza con el “@classmethod”, y que podemos llamar al método desde la clase “Coche”. Con la clase no podremos llamar a otros métodos que no sean de clase.

Los métodos de clase no pueden acceder a los atributos, ni siquiera podemos llamar a los atributos dentro de un método de clase:

```python
class Coche:
    def __init__(self, color, puertas, matricula):
        self.color = color
        self.puertas = puertas
        self.matricula = matricula

    def tocar_claxon(self):
        print("piiiiiii")
    
    def arrancar(self):
        print("brrrrrr")
        self.tocar_claxon()

    @classmethod
    def pasar_itv(cls, precio):
        print(f"La itv cuesta", precio, "€. El color sigue siendo", self.color)
Coche.arrancar()

>> Nos lanza un error.
```

Por último, tenemos los métodos estáticos:

```python
class MiClase:
    @staticmethod
    def metodo_estatico():
        print("Este es un método estático")

# Uso
MiClase.metodo_estatico()
```

Se definen con el decorador “@staticmethod”, y no toman automáticamente ninguna referencia a la instancia o a la clase. No pueden acceder a los atributos de la instancia o de la clase directamente. Se llaman en la clase, pero no pasan automáticamente la clase como argumento.

En la siguiente tabla te especifico lo que hacen los distintos tipos de métodos:

|  | Métodos de instancia | Métodos de clase | Métodos estáticos |
|--------------|--------------|--------------|-------------------|
| acceso a métodos y atributos<br>atributos de la clase    | Sí    | Sí    | No |
| requiere una instancia    | Sí    | No    | No |
| acceso a métodos y <br> atributos de la instancia   | Sí    | No   | No |

Así como los métodos de instancia requieren del parámetro self para acceder a dicha instancia, los métodos de clase requieren del parámetro cls para acceder a los atributos de clase. Los métodos estáticos, dado que no pueden acceder a la instancia ni a la clase, no indican un parámetro semejante.

***

##### Herencia

> La herencia es el proceso mediante el cual una clase puede tomar métodos y atributos de una clase superior, evitando repetición de código cuando varias clases tienen atributos o métodos en común.

La herencia en Python es un concepto fundamental de la programación orientada a objetos. Permite la creación de nuevas clases basadas en clases existentes. 
Al permitir que una clase herede atributos y métodos de otra clase, facilita la reutilización del código existente. Esto ayuda a evitar la redundancia y a escribir menos líneas de código.
Además, Python no tiene interfaces como en otros lenguajes de programación, pero con la herencia, se puede conseguir utilizar interfaces al definir una clase base con métodos que deben ser implementados por las clases derivadas, actuando como una especie de “interfaz”.
Si se usa de manera adecuada, la herencia puede ser una herramienta crucial para mejorar la eficiencia y la organización del código en Python.

Para ello, utilizaremos el siguiente ejemplo:

```python
class Animal:
    pass

class Perro(Animal):
    pass
```

Creamos la clase Animal, y luego la clase Perro, y entre los paréntesis de esta indicamos que heredamos de Animal. Con el código dentro de la función print podremos ver que Perro es una clase que hereda de Animal.
Es posible crear una clase “hija” con tan solo pasar como parámetro la clase de la que queremos heredar:


```python
class Personaje:
    
    def __init__(self, nombre, arma):
        self.nombre = nombre
        self.arma = arma

class Guerrero(Personaje):
    pass

arturo = Guerrero("Arturo", "Excálibur")
```

En este ejemplo, la clase Guerrero hereda de Personaje. Una clase “hija” puede sobrescribir los métodos o atributos, así como definir nuevos, que sean específicos para esta clase.

Para ver las clases de las que heredan de la clase “Padre” se usa:

```python
class Animal:
    pass

class Perro(Animal):
    pass

print(Animal.__subclases__())
```

*** 
 ##### Herencia Extendida
 > Las clases "hijas" que heredan de las clases superiores, pueden crear nuevos métodos o sobrescribir los de la clase "padre". Asimismo, una clase "hija", puede heredar de una o más clases, y a su vez, transmitir herencia a clases "nietas".

 Ya hemos visto cómo funciona la herencia, pero te traigo un ejemplo más completo para ver este apartado más en profundidad:

 ```python
class Animal:
    def__init__(self, edad, color):
        self.edad = edaad
        self.color = color

    def nacer(self):
        print("Este animal ha nacido")

    def hablar(self):
        print("Este animal emite un sonido")


class Perro(Animal):
    pass

chihuahua = Perro(2, "Beige")
print(chihuahua.color)
```

Perro, al heredar de Animal, puede aplicar los métodos que ha heredado e incluso los atributos. Pero también podemos tener métodos modificados. Para que los veas mejor, vamos a modificar el código anterior, para que veas la aplicación correctamente:

 ```python
class Animal:
    def__init__(self, edad, color):
        self.edad = edaad
        self.color = color

    def nacer(self):
        print("Este animal ha nacido")

    def hablar(self):
        print("Este animal emite un sonido")


class Perro(Animal):
    def hablar(self):
        print("Mini Guau")

    def correr(self, metros):
        print(f"El perro corre {metros} metros.")

chihuahua = Perro(2, "Beige")
print(chihuahua.color)

chihuaha.correr(200)
```

Con esto estás viendo que puede modificar los métodos que ha heredado, los está sobrescribiendo y, además, le hemos añadido uno nuevo que es el método correr().
En este ejemplo, Perro ha heredado edad y color, pero puede tener sus atributos propios además de los heredados.
Voy a explicarte algunas formas para añadirle sus propios atributos. Puedes ir haciendo pruebas con el código que te facilito, o crear tu propio código y tus propios ejemplos imitando los míos, de esta forma, podrás ver distintos ejemplos al mismo tiempo.
Es importante que practiques esta parte, pues al principio puede ser alfo confusa de entender, pero ya verás que la acabarás pillando.

Una de las formas que tenemos para añadirle los atributos es:

 ```python
class Animal:
    def__init__(self, edad, color):
        self.edad = edaad
        self.color = color

    def nacer(self):
        print("Este animal ha nacido")

    def hablar(self):
        print("Este animal emite un sonido")


class Perro(Animal):

    def __init__(self, edad, color, raza):
        self.edad = edad
        self.color = color
        self.raza = raza

    def hablar(self):
        print("Mini Guau")

    def correr(self, metros):
        print(f"El perro corre {metros} metros.")

chihuahua = Perro(2, "Beige")
print(chihuahua.color)

chihuaha.correr(200)
```


Si ahora probaras a usar el método correr desde la clase Animal, o el atributo raza, no podrías, pues son propias de la clase Perro.
Estás viendo que estamos añadiendo los mismos atributos en la clase Perro, y le añadimos el de raza, pero, hay una forma mucho más óptima de hacer esto, y es con la palabra “super”.
Vamos a seguir utilizando el mismo ejemplo. Ahora imagina, que la clase Animal tiene 12 propiedades en vez de 2, pues sería ineficiente tener que escribir uno a uno todos los atributos de la clase Animal en la clase Perro, ya que esto no sería ahorrar código. Pues con la palabra “super” podrás ahorrarte este paso, y lo veremos modificando el ejemplo anterior:

 ```python
class Animal:
    def__init__(self, edad, color):
        self.edad = edaad
        self.color = color

    def nacer(self):
        print("Este animal ha nacido")

    def hablar(self):
        print("Este animal emite un sonido")


class Perro(Animal):

    def __init__(self, edad, color, raza):
        super().__init__(edad, color)
        self.raza = raza

    def hablar(self):
        print("Mini Guau")

    def correr(self, metros):
        print(f"El perro corre {metros} metros.")

chihuahua = Perro(2, "Beige")
print(chihuahua.color)

chihuaha.correr(200)
```


Con esto estás viendo que nos podemos ahorrar líneas de código, y funciona correctamente.
Vamos a centrarnos ahora en la herencia múltiple:

```python
class Padre:
    pass

class Hijo(Padre):
    pass

class Nieto(Hijo):

```

Si te fijas bien, hemos creado la clase Padre, de la que hereda la clase Hijo, y que, a su vez, se ha creado la clase Nieto, que hereda de la clase Hijo.
Vamos a ir agregando más código al ejemplo para verlo más en profundidad.

```python
class Padre:
    def hablar(self):
        print("Hola")

class Madre:
    def reir(self):
        print("Jajajaj")

class Hijo(Padre, Madre):
    pass

class Nieto(Hijo):
    pass

```

Como ves, hemos añadido la clase Madre, y ahora, en la clase Hijo, hemos hecho que herede tanto de la clase Padre como de la clase Madre. Así se realiza la herencia múltiple.
Ahora piensa, ¿qué ocurre si la clase Madre tiene un método igual que el de la clase Padre?:

```python
class Padre:
    def hablar(self):
        print("Hola")

class Madre:
    def reir(self):
        print("Jajajaj")
    def hablar(self):
        print("¿Qué tal?")

class Hijo(Padre, Madre):
    pass

class Nieto(Hijo):
    pass

```

Como puedes ver, ambas clases “padre” tienen un método hablar, pero, si la clase hija usa el método hablar, ¿cuál se ejecutará? La respuesta es simple: se ejecutará el método de la primera clase “padre” que hereda, y en este caso, al usar el método hablar se vería por pantalla “Hola”. 
Si inviertes el orden, y heredas primero de la lase “Madre”, se vería “¿Qué tal?”.

Con el método “__mro__” puedes ver el orden en el que se hereda. Aplicándolo al ejemplo, quedaría así:

```python
class Padre:
    def hablar(self):
        print("Hola")

class Madre:
    def reir(self):
        print("Jajajaj")
    def hablar(self):
        print("¿Qué tal?")

class Hijo(Padre, Madre):
    pass

class Nieto(Hijo):
    pass

print(Nieto.__mro__)
```

***
##### Polimorfismo

Vamos a ver otro de los conceptos fundamentales de la programación orientada a objetos, el Polimorfismo.
Hace referencia a que los objetos pueden coger diferentes formas, como, por ejemplo, como hemos venido viendo, hemos creado distintos objetos que tenían el mismo método, pero cada uno decía una cosa distinta. 
Puede resultar confuso así escrito, pero vamos a verlo con un ejemplo. Vamos a crear de nuevo una clase Animal, y varias clases de animales distintos que hereden de dicha clase.
Después, les añadiremos los mismos métodos, pero, se comportarán de forma diferente.

```python
class Animal:
    def hablar(self):
        pass

class Perro(Animal):
    def hablar():
        return "Woof"

class Gato(Animal):
    def hablar():
        return "Meow"

class Pato(Animal):
    def hablar():
        return "Quack"

perro = Perro()
gato = Gato()
pato = Pato()

resultado_perro = Perro.hablar()
resultado_gato = Gato.hablar()
resultado_pato = Pato.hablar()

print("Perro:", resultado_perro)
print("Gato:", resultado_gato)
print("Pato:", resultado_pato)
```

Si pruebas el ejemplo, verás que estos tres objetos usan el mismo método pero, los resultados son distintos.

***
##### Métodos especiales
Estos métodos pueden ayudarnos a sobrescribir métodos incorporados de Python sobre nuestras clases para controlar el resultado devuelto:

```python
class Libro:

    def __init__(self, autor, titulo, cant_paginas):
        self.autor = autor
        self.titulo = titulo
        self.cant_paginas = cant_paginas

    def __str__(self):

        return f'Titulo: "{self.titulo}", escrito por {self.autor}'

libro = Libro("Stephen King", "It", 1032)

print(str(libro))
print(len(libro))
```