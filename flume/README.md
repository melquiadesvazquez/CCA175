# Introducción

Apache Flume es un servicio distribuido y fiable para la recogida, agregación, y traslado de grandes conjuntos de datos de manera eficiente.

Se compone de:

* *Client* (cliente): Implementación que opera en el punto de origen de los eventos y los entrega a un agente Flume. Por ejemplo, Log4J appender de Flume es un cliente.

* *Agent* (agente?: Un proceso independiente que aloja los componentes Fume como las fuentes (Source), canales (Channel) y sumideros (Sink), tiene la capacidad de recibir, almacenar y reenviar eventos a su próximo destino.

* *Source* (fuente): Implementación que puede consumir eventos entregados a él a través de un mecanismo (por ejemplo, una fuente de Avro se puede utilizar para recibir los eventos Avro de clientes u otros agentes en el flujo). Cuando una fuente recibe un evento, se lo entrega a uno o más canales.
* *Channel* (canal): Buffer de almacenamiento temporal para eventos, donde éstos se entregan al canal a través de fuentes que operan con del agente.
* *Sink* (sumidero): Implementación que puede eliminar eventos de un canal y transmitirlos al siguiente agente en el flujo, o hasta el destino final del evento, normalmente hdfs.

Lee ficheros de un lugar y los guarda automáticamente en hdfs u otro lugar (streaming data). 

Complementa a Kafka en subir los archivos a hdfs (Flafka), cada uno tiene ventajas e inconvenientes y Kafka puede hacer de source, channel o sink.

## Comandos


