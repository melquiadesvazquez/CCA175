# Introducción

Sqoop coge una base de datos relacional y vuelca su contenido a hdfs (y viceversa)

# Comandos

Listar las tablas

```
sqoop list-tables \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training 
```

Importar tabla a HDFS

```
sqoop import \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--table accounts \
--target-dir /loudacre/accounts \
--null-non-string '\\N'
```

Importar table a HDFS en formato parquet

```
sqoop import \
--connect jdbc:mysql://localhost/loudacre \
--username training --password training \
--table accounts \
--target-dir /loudacre/accounts_parquet \
--as-parquetfile
```

Para visualizar el formato parquet

```
parquet-tools schema \
hdfs://localhost/[HDFS PATH]/myfile.parquet

parquet-tools head \
hdfs://localhost/[HDFS PATH]/myfile.parquet
```
