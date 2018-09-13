# Introducción

# Documentación disponible durante el examen Python / Scala

http://spark.apache.org/docs/1.6.0/api/python/index.html

http://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.package

# Comandos

Para pasarle parámetros a una aplicación en Python / Scala

```
spark-submit CountJPGs.py /myDB/weblogs/*

spark-submit --class stubs.CountJPGs target/countjpgs-1.0.jar /myDB/weblogs/*
```

Si quieres hacerlo en el cluster en Python / Scala

```
spark-submit --master yarn-client CountJPGs.py /myDB/weblogs/*

spark-submit --class stubs.CountJPGs \
--master yarn-client 
target/countjpgs-1.0.jar /myDB/weblogs/*
```

Para que no devuelva tantos errores en ambos:

```
sc.setLogLevel("WARN")
```

Para cerrar el SparkContext en ambos

```
sc.stop()
```

Para contar el numero de peticiones jpg en Python / Scala

```
jpgs = sc.textFile(sys.argv[1]) \
.map(lambda line: line.split(" ")[6]) \
.filter(lambda file: '.jpg' in file).count()

val jpgs = sc.textFile(args(0)).
map(_.split(" ")(6)).filter(_.contains(".jpg")).count()
```

En scala necesitamos un proyecto maven
countjpgs_project/src/main/scala/stubs/CountJPGs.scala

```
package stubs

import org.apache.spark.SparkContext

object CountJPGs {
    def main(args: Array[String]) {
        if (args.length < 1) {
            System.err.println("Usage: stubs.CountJPGs <logfile>")
            System.exit(1)
        }

        //TODO: complete exercise
        println("stub is not implemented")
        System.exit(1)
   }
}
```

Posteriormente compilamos el proyecto Maven y finalmente ejecutamos la aplicación scala compilada y le pasamos parametros (indicado al principio)

```
mvn package
```

Para añadir el nombre de la aplicación en ambos

```
--name 'Count JPGs'
```

Tambien podemos crear un archivo de configuración .conf

```
spark.app.name          My Spark App
spark.master            yarn-client
spark.executor.memory   400M
```

Y luego añadimos esto

```
--properties-file myspark.conf
```
