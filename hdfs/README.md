# Introducción


# Comandos
Para listar un directorio

```
hdfs dfs -ls /user/training/test
```

Para borrar/crear directorio lo anterior con rm o mkdir

```
hdfs dfs -mkdir /user/training/test
hdfs dfs -rm /user/training/test
```

Para subir a hdfs

```
hdfs dfs -put deviceBQ.csv /user/training/test
```

Para bajar de hdfs

```
hdfs dfs -get /user/training/test/deviceBQ.csv deviceBQ.csv
```

Para ver la parte final del contenido de un archivo

```
hdfs dfs -tail /user/training/test/deviceBQ.csv
```