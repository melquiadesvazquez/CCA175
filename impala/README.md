# Introducción

Cloudera Impala es un motor de consulta que corre en Apache Hadoop, es parecido a un cliente SQL, version moderna de Hive.

No puede leer archivos sin esquema implicito como .txt, pero .json, .csv y .avro si por ejemplo.

# Documentación disponible durante el examen

https://www.cloudera.com/documentation/enterprise/5-10-x/topics/impala_tutorial.html

# Comandos

Ejecutar Impala

```
impala-shell
```

Para evitar la cache

```
INVALIDATE METADATA;
```

Para mostrar todas las tablas

```
SHOW TABLES;
```

Borrar tabla si existe

```
DROP TABLE IF EXISTS myTable;
```

Para seleccionar elementos de una table

```
SELECT * FROM myTable WHERE name LIKE 'Me%' LIMIT 5;
```
Para sumar y agrupar elementos de una tabla

```
SELECT myColumn1, myColum2, sum(myColumn3) as suma FROM myTable
GROUP BY myColumn1, myColumn2
ORDER BY suma DESC;
```

Para crear un backup de una tabla

```
CREATE TABLE myTable2 AS (SELECT * FROM myTable1);
```

Exportar tabla a CSV

```
impala-shell -B -q 'SELECT * FROM myTable' --print_header -o myTable.csv '--output_delimiter=,';
```

Crear table desde CSV (Sin nombre de columnas)

```
CREATE EXTERNAL TABLE myTable (
    myColumn1 INT, 
    myColumn2 TIMESTAMP, 
    myColumn3 STRING
) 
ROW FORMAT DELIMITED FIELDS TERMINATED BY ','
LOCATION '/myHDFSDir';
```
