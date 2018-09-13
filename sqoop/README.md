# Introducción

Sqoop coge una base de datos relacional y vuelca su contenido a hdfs (y viceversa)

# Comandos

Despues de sqoop import, connectamos a la base de datos

```
--connect jdbc:mysql//localhost/myDb
--username myUser --password myPass
```

Posteriormente, selecionamos los datos

```
--table myTable
--columns myColumn1, myColumn2, myColumn3
--where 'myColumn1 = "A%"'
```

Luego indicamos los directorios de salida

```
--target-dir myHDFSDir
--delete-target-dir
--outdir myTempDir
```

Tambien formatemos los campos extraidos

```
--fields-terminated-by ','
--null-string '\\N'
--null-non-string '\\N'
```

Por último configuramos el numero de ficheros de salida

```
--num-mappers 1
```


Listar las tablas

```
sqoop list-tables \
--connect jdbc:mysql://localhost/myDB \
--username myUser --password myPass 
```

Importar tabla a HDFS

```
sqoop import \
--connect jdbc:mysql://localhost/myDB \
--username myUser --password myPass \
--table accounts \
--target-dir /myDB/accounts \
--null-non-string '\\N'
```

Importar table a HDFS en formato parquet

```
sqoop import \
--connect jdbc:mysql://localhost/myDB \
--username myUser --password myPass \
--table accounts \
--target-dir /myDB/accounts_parquet \
--as-parquetfile
```

Para visualizar el formato parquet

```
parquet-tools schema \
hdfs://localhost/[HDFS PATH]/myfile.parquet

parquet-tools head \
hdfs://localhost/[HDFS PATH]/myfile.parquet
```
