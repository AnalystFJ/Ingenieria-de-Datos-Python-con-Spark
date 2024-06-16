# Introducción a los RDDs en Spark

Este repositorio contiene material para una presentación sobre los RDDs (Resilient Distributed Datasets) en Apache Spark. Incluye una presentación en PowerPoint, ejemplos de código y datos de muestra.

## Contenido del Repositorio

- `Presentacion/Introduccion_RDDs_Spark.pptx`: Presentación en PowerPoint.
- `Codigo/`: Carpeta con ejemplos de código.
  - `Ejemplo1.py`: Código para crear un RDD a partir de una lista y filtrar números pares.
  - `Ejemplo2.py`: Código para leer un archivo de texto y contar líneas.
  - `WordCount.py`: Ejemplo de un conteo de palabras.
- `Data/sample_text.txt`: Archivo de texto de muestra para los ejercicios.

## Cómo usar este repositorio

1. **Presentación**:
   - La presentación `Introduccion_RDDs_Spark.pptx` contiene una introducción teórica a los RDDs en Spark, ejemplos prácticos y ejercicios.

2. **Ejemplos de Código**:
   - Los scripts en la carpeta `Codigo/` son ejemplos de cómo trabajar con RDDs en Spark.
   - Puedes ejecutar estos scripts en un entorno de Spark. Asegúrate de tener Spark instalado y configurado en tu máquina.

## Ejecución de Ejemplos

### Ejemplo 1: Creación de un RDD

```python
from pyspark import SparkContext

sc = SparkContext("local", "Ejemplo 1")
rdd = sc.parallelize([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
even_numbers = rdd.filter(lambda x: x % 2 == 0)
print(even_numbers.collect())
sc.stop()
```
### Ejemplo 2: Operaciones con RDDs
```python
from pyspark import SparkContext

sc = SparkContext("local", "Ejemplo 2")
text_file = sc.textFile("Data/sample_text.txt")
total_lines = text_file.count()
spark_lines = text_file.filter(lambda line: "Spark" in line).count()
print(f"Total lines: {total_lines}")
print(f"Lines with 'Spark': {spark_lines}")
sc.stop()
