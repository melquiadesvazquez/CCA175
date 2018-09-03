# Introducción

Apache Kafka es un proyecto de intermediación de mensajes, puede verse como una cola de mensajes, bajo el patrón publicación-suscripción. 

Consta de:

* *Topic* (tema): Categorías en las que clasificar los mensajes enviados a Kafka.

* *Producer* (productor): Clientes conectados responsables de publicar los mensajes. Estos mensajes son publicados sobre uno o varios topics.

* *Consumer* (consumidor): Clientes conectados suscritos a uno o varios topics encargados de consumir los mensajes.

* *Broker* (nodos): Nodos que forman el cluster  de Kafka.

* *Zookeeper*: es parecido a un servidor LDAP, se utiliza para saber los brokers que hay en el cluster y para detectar la adición y borrado de consumidores

Alguna de sus ventajas son: asincrono, desacoplado, persistente, escalable, replicado y tolerante a fallos

Tiene dos tipos de procesos: *point to point* (de muchos a 1) y *public and subsbribe* (de 1 a muchos)

## Comandos


