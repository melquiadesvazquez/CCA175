# Introducción
Cuando cargamos un conjunto de datos (por ejemplo proveniente de una fuente externa como los archivos de un directorio de un HDFS, o de una estructura de datos que haya sido previamente generada en nuestro programa) para ser procesado en Spark, la estructura que usaremos internamente para volcar dichos datos es un RDD

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
