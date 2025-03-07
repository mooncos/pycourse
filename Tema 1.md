# Tema 1

---

# Print

<aside>
🐍 **Declaración que al ejecutarse imprime por pantalla el argumento que se introduce dentro de los paréntesis.**

</aside>

### Mostrando texto

Ingresamos entre comillas simples o dobles los caracteres de texto que deben mostrarse en pantalla.

```python
print("Hola mundo")
>> Hola mundo
```

### Mostrando números

Podemos entregarle el número que debe mostrar, o una operación matemática a resolver. No empleamos comillas en estos casos.

```python
print(150 + 50)
>> 200
```

---

# Input

<aside>
🐍 Función que permite al usuario introducir información por medio del teclado al ejecutarse, otorgándole una instrucción acerca del ingreso solicitado. El código continuará ejecutándose después de que el usuario realice la acción.

</aside>

```python
input("Dime tu nombre: ")
>> Dime tu nombre: | # Ingreso por teclado

print("Tu nombre es " + input("Dime tu nombre: "))
>> Dime tu nombre: Juan Carlos
>> Tu nombre es Juan Carlos
```

---

# Strings

<aside>
🐍 Los strings en Python son un tipo de dato formado por cadenas de caracteres de cualquier tipo, formando un texto.

</aside>

### Concatenación

Es la unifiación de cadenas de texto:

```python
print("Hola" + " " + "mundo")
>> Hola mundo
```

### Caracteres especiales

Indicamos a la consola que el caracter después del símbolo \ debe ser tratado como un caracter especial.

```python
\" # Imprime comillas
\n # Separa texto en una nueva línea (Salto de línea)
\t # Imprime un tabulador
\\ # Imprime la barra invertida textualmente
```

---