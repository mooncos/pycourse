# Tema 2

---

# Variables

<aside>
🐍 Las variables son espacios de memoria que almacenan valores o datos de distintos tipos, y pueden variar. Se crean en el momento que se les asigna un valor, por lo cual en Python no requerimos declararlas previamente.

</aside>

### Ejemplos de uso

```python
pais = "México"

nombre = input("Escribe tu nombre: ")
print("Tu nombre es " + nombre)

num1 = 1000
num2 = 35
print(num1 + num2)
>> 100
```

---

# Nombres de variables

<aside>
🐍 Existen convenciones y buenas prácticas asociadas al nombre de las variables creadas en Python. Tienen la intención de facilitar la interpretabilidad y mantenimiento del código creado.

</aside>

## Reglas

1. **Legible:** El nombre de la variable es relevante según su contenido. Por ejemplo, si estamos trabajando con números la variable sería numero, o num, o numero1 si hay varios números.
2. **Unidad:** No existen espacios entre palabras. Puedes incorporar guiones bajos. numero_entero.
3. **Letras especiales:** Omitir signos específicos del español, como tildes o la letra ñ
4. **Números:** No deben empezar por números, pero pueden contenerlos al final.
5. **Signos/símbolos:** No se deben incluir: “ ’, < > / ? | \ ( ) ! @ # $ % ^ & * ~ - +
6. **Palabras clave:** No utilizamos palabras reservadas por python

---

# Tipos de datos

<aside>
🐍 Tenemos varios tipos, que son fundamentales en programación, ya que almacenan información, y nos permiten manipularla.

</aside>

```python
# texto (str)
"Python"
"750"

# números
int 250
float 12.50

# booleanos
True
False
```

| Estructuras | mutable | ordenado | duplicados |
| --- | --- | --- | --- |
| listas [ ] | ✅ | ✅ | ✅ |
| tuplas ( ) | ❌ | ✅ | ✅ |
| sets { } | ✅ | ❌ | ❌ |
| diccionarios { } | ✅ | ❌ | ❌ : ✅ * |

<aside>
🐍 * → key es única; **value** puede repetirse

</aside>

---

# Integers y floats

<aside>
🐍 Los integers y floats en Python son tipos numéricos: int y float. Su tipo queda definido al asignarle un valor a una variable. La función **type()** nos permite obtener el tipo de valor almacenado en una variable.

</aside>

## int

Int, o integer, es un número entero, positivo o negativo, sin decimales.

```python
num1 = 7
print(type(num1))
>> <class 'int'>
```

## float

“Número flotante”. Número que puede ser positivo o negativo, y a su vez contiene uno o más decimales.

```python
num2 = 7.525587
print(type(num2))
>> <class 'float'>
```

---

# Operadores matemáticos

Los operadores básicos en Python son:

| Suma: | + |
| --- | --- |
| Resta | - |
| Multiplicación | * |
| División | / |
| Cociente | // |
| Resto (módulo) | % (se usa para detectar valores pares) |
| Potencia | ** |
| Raíz cuadrada | **0.5  (caso especial de potencia) |

---

# Conversiones

<aside>
🐍 Python realiza conversiones implícitas de tipos de datos automáticamente para operar con valores numéricos. En otros casos, se necesitará realizar una conversión de manera explícita.

</aside>

```python
int(var)
>> <class 'int'> # Convierte el dato en integer

float(var)
>> <class 'float'> # Convierte el dato en float
```

---

# Redondeo

<aside>
🐍 Facilita la interpretación de los valores calculados al limitar la cantidad de decimales que se muestran en pantalla. También, nos permite aproximar valores decimales al entero más próximo.

</aside>

```python
round(number, ndigits)
number # Valor a redondear
ndigits # cantidad de decimales (si se omite, es entero)
```

### Ejemplos

```python
print(round(100/3))
>> 33
print(round(12/7, 2))
>> 1.71
```

---

# Formatear cadenas

<aside>
🐍 Para facilitar la concatenación que vimos en el tema 1, en Python contamos con dos herramientas que nos evitan manipular las variables, para incorporarlas directamente al texto.

</aside>

- **Función format:** se encierran las posiciones de las variables entre corchetes { }, y a continuación del string llamamos a las variables con la función format:

```python
print("Mi coche es { } y de matrícula { }".format(color_coche, matricula))
```

- **Cadenas literales (f-string):** A partir de Python 3.8, podemos anticipar la concatenación de variables anteponiendo **f** al string

```python
print(f"Mi coche es {color_coche} y de matrícula {matricula}")
```