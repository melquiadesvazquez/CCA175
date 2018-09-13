# Introducción
Cuando cargamos un conjunto de datos (por ejemplo proveniente de una fuente externa como los archivos de un directorio de un HDFS, o de una estructura de datos que haya sido previamente generada en nuestro programa) para ser procesado en Spark, la estructura que usaremos internamente para volcar dichos datos es un RDD


# Documentación disponible durante el examen Python / Scala

http://spark.apache.org/docs/1.6.0/api/python/index.html

http://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.package

# Comandos

Para lanzar la Shell de Python usar

```
pyspark
```

Para lanzar la Shell de Scala usar

```
spark-shell
```

Para controlar el nivel de log en ambos

```
sc.setLogLevel("WARN")
```

Para ejecutar un archivo Python con argumentos

```
spark-submit myFile.py myArgument1 myArgument2
```

Para ejecutar un archivo Scala con argumentos

```
mvn package

spark-submit --class ClassName target/jarName.jar  myArgument1 myArgument2
```

Siempre detener el SparkContext

```
sc.stop()
```

El salto de linea en Python se hace con el punto abajo y en Scala con el punto arriba

Para guardar un archivo en HDFS y generar solo un archivo:

```
result.repartition(1).saveAsTextFile("/myFolderInHDFS")
```

Para hacer un bucle en un RDD en Python y Scala

```
for item in result.collect():
    print item

result.foreach(println)
```

Para hacer un casting de tipos en Python y Scala

```
long(value)

value.toLong
```

Para persistir un RDD

```
.persist()
```

Para extraer los parametros en Scala

```
.map{case (k, v) => (k._1, k._2, v)}
```

Para leer o escriber un fichero de texto en ambos

```
sc.textFile("file:/[HDFS PATH].txt") 
ipsRDD.saveAsTextFile("/[HDFS PATH]")
```

Contar, leer todas o algunas de las lineas en ambos

```
myRDD.count()
myRDD.collect()
myRDD.take(10)
```

Filtrar líneas por texto en Python / Scala

```
myRDD.filter(lambda line: ".jpg" in line)

myRDD.filter(_.contains(".jpg")) 
```

Crear un mapa con la longitud de cada linea en Python / Scala

```
myRDD.map(lambda line: len(line)).take(5)

myRDD.map(_.length).take(5)
```

Crear un mapa con la primera palabra de cada linea en Python / Scala

```
myRDD.map(lambda l: l.split(' ')[0]).take(5)

myRDD.map(_.split(' ')(0)).take(5)
```

Crear un bucle que imprima lineas en Python / Scala

```
for ip in myRDD.take(10): print ip

myRDD.take(10).foreach(println)
```

Imprimir la ip y el usuario en Python / Scala

```
ipsRDD = logsRDD.map(lambda line: \
(line.split(' ')[0], line.split(' ')[2])) \
for t in ipsRDD.take(10): \
print t[0] + "/" + t[1]

val ipsRDD = logsRDD.map(_.split(' ')).
map(record => (record(0), record(2)))
ipsRDD.take(10).
foreach(t => println(t._1 + "/" + t._2))
```


