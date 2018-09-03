# Introducción

Cloudera Impala es un motor de consulta que corre en Apache Hadoop, es parecido a un cliente SQL, version moderna de Hive.

No puede leer archivos sin esquema implicito como .txt, pero .json, .csv y .avro si por ejemplo.

# Comandos

Ejecutar Impala

```
impala-shell
```

Para mostrar todas las tablas

```
SHOW TABLES;
```

Para seleccionar elementos de una table

```
SELECT * FROM device WHERE name LIKE 'Me%' LIMIT 5;
```

Para crear un backup de una tabla

```
CREATE TABLE deviceBQ AS (SELECT * FROM device);
```

Exportar tabla a CSV

```
impala-shell -B -q 'SELECT * FROM device' --print_header -o deviceBQ.csv '--output_delimiter=,';
```

Crear table desde CSV (Sin nombre de columnas)

```
CREATE EXTERNAL TABLE deviceBQ (devnum smallint, released timestamp, name string,type string) ROW FORMAT DELIMITED FIELDS TERMINATED BY ',' LOCATION '/user/training/test';
```
