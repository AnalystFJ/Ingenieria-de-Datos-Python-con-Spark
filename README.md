# Ingenieria-de-Datos-Python-con-Spark
## Introducción a Spark Session

## ¿Qué es una Spark Session?

Una **Spark Session** es la entrada principal para trabajar con Apache Spark 2.x y versiones posteriores. Proporciona una forma unificada para leer, transformar y escribir datos, abarcando tanto APIs de DataFrame como de Dataset, y sustituyendo las funciones `SQLContext` y `HiveContext` que se usaban en versiones anteriores de Spark.

## ¿Por Qué es Importante?

- **Facilita el Trabajo con Datos**: Proporciona una interfaz más sencilla y coherente.
- **Optimización**: Incorpora optimizaciones como Catalyst (optimizador de consultas) y Tungsten (optimización de ejecución).

## Creación de una Spark Session


```python
from pyspark.sql import SparkSession

# Crear una Spark Session
spark = SparkSession.builder \
    .appName("MiAplicacionSpark") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate() 
```
## Usos Comunes de Spark Session Creación de una Spark Session
## Leer Datos
```
df = spark.read.json("ruta/al/archivo.json")
```
## Ejecutar Consultas SQL
```
spark.sql("SELECT * FROM tabla")
```
## Escribir Datos
```
df.write.csv("ruta/de/salida.csv")
```

### Ventajas de Usar Spark Session
### Unificación: Simplifica el acceso a las distintas APIs.
### Optimización: Mejor uso de los recursos y optimización automática de consultas.
### Facilidad de Uso: Menor complejidad para el desarrollador.
### Ejemplos Prácticos
### En la carpeta examples/, encontrarás scripts de Python que demuestran cómo crear una Spark Session y realizar operaciones comunes como leer, escribir y ejecutar ### consultas SQL.

### Conclusión
### Spark Session es esencial para trabajar con Apache Spark. Ofrece una interfaz unificada y optimizada que facilita las operaciones de lectura, transformación y 
### escritura de datos.
 
