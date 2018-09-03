Para lanzar un YARN job

```
spark-submit --master yarn-client wordcount.py /loudacre/kb/*
```

Para listar todos los YARN jobs

```
yarn application -list -appStates ALL
```

Los Hadoop YARN jobs están en http://localhost:8088/