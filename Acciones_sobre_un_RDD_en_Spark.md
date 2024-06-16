# Acciones sobre un RDD en Apache Spark

## ¿Qué es un RDD?

Un RDD (Resilient Distributed Dataset) es la principal abstracción de datos en Apache Spark. Es una colección de elementos distribuida a lo largo de un clúster, que puede ser procesada en paralelo. Los RDDs son inmutables y se pueden crear a partir de datos en almacenamiento estable o de otros RDDs.

## Transformaciones y Acciones

En Spark, las operaciones que se pueden realizar en RDDs se dividen en dos categorías principales:

1. **Transformaciones**: Estas son operaciones que crean un nuevo RDD a partir de uno existente. Son perezosas, lo que significa que no se ejecutan inmediatamente. Ejemplos incluyen `map()`, `filter()`, `flatMap()`, etc.

2. **Acciones**: Estas son operaciones que devuelven un valor al controlador o almacenan datos en un sistema de almacenamiento externo. Ejecutan las transformaciones que han sido aplicadas a un RDD. Ejemplos incluyen `collect()`, `count()`, `take()`, `reduce()`, etc.

## Principales Acciones en Spark

### 1. `collect()`

Recoge todos los elementos del RDD y los devuelve al controlador como una lista. Esto es útil para depuración pero no debe usarse con RDDs grandes porque puede saturar la memoria del controlador.

**Ejemplo:**

```python
from pyspark import SparkContext
```
# Inicializar SparkContext
```
sc = SparkContext("local", "Collect Example")
```
# Crear un RDD
```
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)
```
# 1. Acción collect
```
collected_data = rdd.collect()
print(collected_data)
```
# 2. count()
## Cuenta el número de elementos en el RDD.
```
count = rdd.count()
print(f"Number of elements in RDD: {count}")
```
## 3. take(n)
## Devuelve los primeros n elementos del RDD como una lista.
```
# Acción take
first_two_elements = rdd.take(2)
print(first_two_elements)
```
## 4. reduce(func)
## Agrega los elementos del RDD usando una función binaria especificada.
```
# Acción reduce
sum_elements = rdd.reduce(lambda x, y: x + y)
print(f"Sum of elements: {sum_elements}")
```
## 5. saveAsTextFile(path)
## Guarda los elementos del RDD como un archivo de texto en el sistema de archivos especificado.
```
# Acción saveAsTextFile
rdd.saveAsTextFile("/path/to/save/rdd_output")
```
# spark_rdd_actions.py
```python
from pyspark import SparkContext

def main():
    # Inicializar SparkContext
  
    sc = SparkContext("local", "RDD Actions Example")

    # Crear un RDD
    data = [1, 2, 3, 4, 5]
    rdd = sc.parallelize(data)

    # Acción collect
    collected_data = rdd.collect()
    print("Collect: ", collected_data)

    # Acción count
    count = rdd.count()
    print(f"Number of elements in RDD: {count}")

    # Acción take
    first_two_elements = rdd.take(2)
    print("First two elements: ", first_two_elements)

    # Acción reduce
    sum_elements = rdd.reduce(lambda x, y: x + y)
    print(f"Sum of elements: {sum_elements}")

    # Acción saveAsTextFile
    rdd.saveAsTextFile("/path/to/save/rdd_output")

if __name__ == "__main__":
    main()


