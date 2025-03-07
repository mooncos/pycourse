# Tema adicional: Pandas

***

### Introducción a Pandas

<aside>
🐍 Pandas es una biblioteca de Python especializada para el análisis y manipulación de datos. Es una herramienta fundamental en ciencia de datos, análisis estadístico y aprendizaje automático.
</aside>

Pandas proporciona estructuras de datos flexibles y eficientes diseñadas para trabajar con datos estructurados (tabulares, multidimensionales, potencialmente heterogéneos) y series temporales. Las dos estructuras de datos principales son:

* **Series**: Estructura unidimensional similar a un array, pero con etiquetas (índices).
* **DataFrame**: Estructura bidimensional (tabular) con filas y columnas etiquetadas.

```python
# Importar la biblioteca pandas
import pandas as pd
```

Pandas se construye sobre NumPy, por lo que es importante tener instalada también esta biblioteca:

```bash
pip install pandas
pip install numpy
```

***

### Series

<aside>
🐍 Las Series son como arrays unidimensionales etiquetados, capaces de almacenar datos de cualquier tipo (enteros, cadenas, flotantes, objetos, etc.).
</aside>

#### Creación de Series

```python
# Crear una Serie desde una lista
lista = [10, 20, 30, 40, 50]
serie = pd.Series(lista)
print(serie)

>> 0    10
   1    20
   2    30
   3    40
   4    50
   dtype: int64
```

Podemos especificar índices personalizados:

```python
# Crear una serie con índices personalizados
serie = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])
print(serie)

>> a    10
   b    20
   c    30
   d    40
   e    50
   dtype: int64
```

También podemos crear Series desde diccionarios:

```python
# Crear una serie desde un diccionario
diccionario = {'a': 10, 'b': 20, 'c': 30, 'd': 40, 'e': 50}
serie = pd.Series(diccionario)
print(serie)

>> a    10
   b    20
   c    30
   d    40
   e    50
   dtype: int64
```

#### Acceso a elementos de una Serie

Podemos acceder a los elementos de una Serie utilizando el índice:

```python
serie = pd.Series([10, 20, 30, 40, 50], index=['a', 'b', 'c', 'd', 'e'])

# Acceder a un elemento por su índice
print(serie['c'])
>> 30

# Acceder a múltiples elementos
print(serie[['a', 'c', 'e']])
>> a    10
   c    30
   e    50
   dtype: int64

# Acceder a un rango de elementos
print(serie['b':'d'])
>> b    20
   c    30
   d    40
   dtype: int64
```

***

### DataFrames

<aside>
🐍 Los DataFrames son estructuras de datos bidimensionales (como una tabla o una hoja de cálculo) con filas y columnas etiquetadas.
</aside>

#### Creación de DataFrames

```python
# Desde un diccionario de listas
datos = {
    'Nombre': ['Ana', 'Juan', 'Pedro', 'María'],
    'Edad': [25, 30, 35, 28],
    'Ciudad': ['Madrid', 'Barcelona', 'Sevilla', 'Valencia']
}

df = pd.DataFrame(datos)
print(df)

>>   Nombre  Edad     Ciudad
  0    Ana    25     Madrid
  1   Juan    30  Barcelona
  2  Pedro    35    Sevilla
  3  María    28   Valencia
```

También podemos crear DataFrames a partir de listas de diccionarios:

```python
# Desde una lista de diccionarios
datos = [
    {'Nombre': 'Ana', 'Edad': 25, 'Ciudad': 'Madrid'},
    {'Nombre': 'Juan', 'Edad': 30, 'Ciudad': 'Barcelona'},
    {'Nombre': 'Pedro', 'Edad': 35, 'Ciudad': 'Sevilla'},
    {'Nombre': 'María', 'Edad': 28, 'Ciudad': 'Valencia'}
]

df = pd.DataFrame(datos)
print(df)

>>   Nombre  Edad     Ciudad
  0    Ana    25     Madrid
  1   Juan    30  Barcelona
  2  Pedro    35    Sevilla
  3  María    28   Valencia
```

#### Acceso a datos en un DataFrame

```python
# Acceder a una columna
print(df['Nombre'])
>> 0      Ana
   1     Juan
   2    Pedro
   3    María
   Name: Nombre, dtype: object

# Acceder a múltiples columnas
print(df[['Nombre', 'Ciudad']])
>>   Nombre     Ciudad
  0    Ana     Madrid
  1   Juan  Barcelona
  2  Pedro    Sevilla
  3  María   Valencia

# Acceder a una fila usando .loc (por etiqueta)
print(df.loc[2])
>> Nombre    Pedro
   Edad         35
   Ciudad   Sevilla
   Name: 2, dtype: object

# Acceder a una fila usando .iloc (por posición)
print(df.iloc[2])
>> Nombre    Pedro
   Edad         35
   Ciudad   Sevilla
   Name: 2, dtype: object
```

***

### Lectura y escritura de datos

<aside>
🐍 Pandas puede leer y escribir datos en diversos formatos como CSV, Excel, SQL, JSON, etc.
</aside>

#### Lectura de archivos CSV

```python
# Leer un archivo CSV
df = pd.read_csv('datos.csv')
print(df.head())  # Muestra las primeras 5 filas
```

#### Escritura a archivos CSV

```python
# Guardar DataFrame en un CSV
df.to_csv('datos_nuevos.csv', index=False)
```

#### Lectura de archivos Excel

```python
# Leer un archivo Excel
df = pd.read_excel('datos.xlsx', sheet_name='Hoja1')
print(df.head())
```

#### Escritura a archivos Excel

```python
# Guardar DataFrame en un archivo Excel
df.to_excel('datos_nuevos.xlsx', sheet_name='Resultados', index=False)
```

***

### Análisis básico de datos

<aside>
🐍 Pandas proporciona herramientas para realizar análisis estadísticos básicos sobre los datos.
</aside>

#### Información del DataFrame

```python
# Obtener información del DataFrame
print(df.info())
```

#### Estadísticas descriptivas

```python
# Obtener estadísticas descriptivas
print(df.describe())
```

#### Valores nulos

```python
# Verificar valores nulos
print(df.isnull().sum())

# Eliminar filas con valores nulos
df_limpio = df.dropna()

# Rellenar valores nulos
df_relleno = df.fillna(0)  # Rellenar con 0
df_relleno = df.fillna(method='ffill')  # Rellenar usando el valor anterior
```

***

### Manipulación de datos

#### Filtrado de datos

```python
# Filtrar filas basadas en una condición
mayores_30 = df[df['Edad'] > 30]
print(mayores_30)

# Filtrar con múltiples condiciones
filtro = df[(df['Edad'] > 25) & (df['Ciudad'] == 'Madrid')]
print(filtro)
```

#### Ordenación

```python
# Ordenar por una columna
df_ordenado = df.sort_values('Edad')
print(df_ordenado)

# Ordenar por múltiples columnas
df_ordenado = df.sort_values(['Ciudad', 'Edad'], ascending=[True, False])
print(df_ordenado)
```

#### Agrupación

```python
# Agrupar datos y aplicar función
agrupado = df.groupby('Ciudad')['Edad'].mean()
print(agrupado)

# Agrupar por múltiples columnas
agrupado = df.groupby(['Ciudad', 'Otra_Columna']).agg({
    'Edad': 'mean',
    'Otra_Columna2': 'sum'
})
print(agrupado)
```

***

### Operaciones con columnas

#### Crear nuevas columnas

```python
# Añadir una nueva columna
df['Año_Nacimiento'] = 2024 - df['Edad']
print(df)

# Columna basada en otras columnas
df['Información'] = df['Nombre'] + ' - ' + df['Ciudad']
print(df)
```

#### Aplicar funciones a columnas

```python
# Aplicar una función a una columna
df['Edad_Meses'] = df['Edad'].apply(lambda x: x * 12)
print(df)

# Aplicar función a múltiples columnas
df[['Edad', 'Otra_Columna']] = df[['Edad', 'Otra_Columna']].apply(lambda x: x * 2)
```

***

### Combinación de DataFrames

<aside>
🐍 Pandas permite combinar diferentes DataFrames de varias formas.
</aside>

#### Concatenación

```python
# Concatenar DataFrames (apilamiento vertical)
df1 = pd.DataFrame({'A': ['A0', 'A1'], 'B': ['B0', 'B1']})
df2 = pd.DataFrame({'A': ['A2', 'A3'], 'B': ['B2', 'B3']})
resultado = pd.concat([df1, df2])
print(resultado)

# Concatenación horizontal
resultado = pd.concat([df1, df2], axis=1)
print(resultado)
```

#### Unión (Merge)

```python
# Combinar mediante una columna común (como JOIN en SQL)
clientes = pd.DataFrame({
    'id_cliente': [1, 2, 3, 4],
    'nombre': ['Ana', 'Juan', 'Pedro', 'María']
})

compras = pd.DataFrame({
    'id_cliente': [1, 2, 3, 5],
    'producto': ['Laptop', 'Móvil', 'Tablet', 'Smartwatch']
})

# Inner join
inner_join = pd.merge(clientes, compras, on='id_cliente')
print(inner_join)

# Left join
left_join = pd.merge(clientes, compras, on='id_cliente', how='left')
print(left_join)

# Right join
right_join = pd.merge(clientes, compras, on='id_cliente', how='right')
print(right_join)

# Outer join
outer_join = pd.merge(clientes, compras, on='id_cliente', how='outer')
print(outer_join)
```

***

### Series temporales

<aside>
🐍 Pandas tiene un soporte excelente para el análisis de series temporales.
</aside>

```python
# Crear una serie temporal
fechas = pd.date_range(start='2023-01-01', periods=5, freq='D')
serie_temporal = pd.Series([10, 20, 15, 30, 25], index=fechas)
print(serie_temporal)

>> 2023-01-01    10
   2023-01-02    20
   2023-01-03    15
   2023-01-04    30
   2023-01-05    25
   dtype: int64

# Resamplear datos (cambiar la frecuencia)
diario_a_mensual = serie_temporal.resample('M').mean()
print(diario_a_mensual)

# Desplazar datos en el tiempo
desplazado = serie_temporal.shift(periods=2)
print(desplazado)
```

***

### Visualización de datos con Pandas

<aside>
🐍 Pandas se integra muy bien con Matplotlib para la visualización de datos.
</aside>

```python
import matplotlib.pyplot as plt

# Asegurarse de que los gráficos se muestren en el notebook
%matplotlib inline

# Gráfico de líneas
df['Edad'].plot(kind='line')
plt.title('Edades')
plt.show()

# Gráfico de barras
df['Ciudad'].value_counts().plot(kind='bar')
plt.title('Distribución por Ciudad')
plt.show()

# Histograma
df['Edad'].plot(kind='hist', bins=10)
plt.title('Distribución de Edades')
plt.show()

# Gráfico de dispersión
df.plot(kind='scatter', x='Edad', y='Otra_Columna')
plt.title('Edad vs Otra Columna')
plt.show()
```

***

### Ejemplo práctico

Vamos a ver un ejemplo completo que utiliza muchas de las funcionalidades de Pandas:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Crear un DataFrame con datos de ventas
datos = {
    'Fecha': pd.date_range(start='2023-01-01', periods=12, freq='M'),
    'Producto': ['A', 'B', 'A', 'C', 'B', 'A', 'C', 'B', 'A', 'B', 'C', 'A'],
    'Región': ['Norte', 'Norte', 'Sur', 'Sur', 'Este', 'Este', 'Norte', 'Sur', 'Este', 'Norte', 'Sur', 'Este'],
    'Ventas': [100, 150, 200, 120, 180, 210, 130, 160, 220, 140, 190, 230],
    'Costos': [50, 70, 80, 55, 85, 90, 60, 75, 95, 65, 80, 100]
}

df = pd.DataFrame(datos)

# Añadir una columna de beneficio
df['Beneficio'] = df['Ventas'] - df['Costos']

# Información básica del DataFrame
print("Información del DataFrame:")
print(df.info())
print("\nEstadísticas descriptivas:")
print(df.describe())

# Análisis por producto
ventas_por_producto = df.groupby('Producto')['Ventas'].sum()
print("\nVentas totales por producto:")
print(ventas_por_producto)

# Análisis por región
beneficio_por_region = df.groupby('Región')['Beneficio'].sum()
print("\nBeneficio total por región:")
print(beneficio_por_region)

# Análisis temporal
ventas_mensuales = df.set_index('Fecha')['Ventas']
print("\nVentas mensuales:")
print(ventas_mensuales)

# Visualización
plt.figure(figsize=(15, 10))

# Gráfico 1: Ventas por producto
plt.subplot(2, 2, 1)
ventas_por_producto.plot(kind='bar')
plt.title('Ventas totales por producto')

# Gráfico 2: Beneficio por región
plt.subplot(2, 2, 2)
beneficio_por_region.plot(kind='bar')
plt.title('Beneficio total por región')

# Gráfico 3: Ventas mensuales
plt.subplot(2, 2, 3)
ventas_mensuales.plot()
plt.title('Tendencia de ventas mensuales')

# Gráfico 4: Relación Ventas vs Costos
plt.subplot(2, 2, 4)
df.plot(kind='scatter', x='Ventas', y='Costos')
plt.title('Relación entre Ventas y Costos')

plt.tight_layout()
plt.show()

# Guardar el análisis en un Excel
with pd.ExcelWriter('analisis_ventas.xlsx') as writer:
    df.to_excel(writer, sheet_name='Datos', index=False)
    ventas_por_producto.to_excel(writer, sheet_name='Ventas por Producto')
    beneficio_por_region.to_excel(writer, sheet_name='Beneficio por Región')
```

***

### Rendimiento y consejos prácticos

<aside>
🐍 Para trabajar eficientemente con grandes conjuntos de datos en Pandas, considera estas recomendaciones:
</aside>

1. **Usa tipos de datos adecuados**: Convierte las columnas al tipo de dato correcto para optimizar el uso de memoria.
   ```python
   df['columna_entera'] = df['columna_entera'].astype('int32')
   df['columna_categorica'] = df['columna_categorica'].astype('category')
   ```

2. **Evita bucles for cuando sea posible**: Utiliza las operaciones vectorizadas de Pandas.
   ```python
   # En lugar de:
   for i in range(len(df)):
       df.loc[i, 'nueva_columna'] = df.loc[i, 'columna1'] + df.loc[i, 'columna2']
   
   # Utiliza:
   df['nueva_columna'] = df['columna1'] + df['columna2']
   ```

3. **Utiliza consultas eficientes**: Para filtrado, .query() puede ser más rápido con conjuntos de datos grandes.
   ```python
   # En lugar de:
   df[(df['A'] > 0) & (df['B'] < 10)]
   
   # Utiliza:
   df.query('A > 0 and B < 10')
   ```

4. **Considera usar chunks para archivos grandes**: Lee y procesa archivos grandes en porciones.
   ```python
   chunks = []
   for chunk in pd.read_csv('archivo_grande.csv', chunksize=10000):
       # Procesar chunk
       chunks.append(resultado_procesamiento)
   
   # Combinar resultados
   df_final = pd.concat(chunks)
   ```

***

### Recursos adicionales

Para aprender más sobre Pandas, puedes consultar:

1. [Documentación oficial de Pandas](https://pandas.pydata.org/docs/)
2. [Tutoriales de Pandas](https://pandas.pydata.org/docs/getting_started/tutorials.html)
3. [Cheat sheet de Pandas](https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf)

***
