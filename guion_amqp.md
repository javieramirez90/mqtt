Guion Completo para Presentación AMQP (Formato Markdown)
Integrante 1 – Introducción + Fundamentos
Integrante 2 – Arquitectura + Casos de Uso + Setup
Integrante 3 – Demo
## 1. ¿Qué es AMQP?

Habla: Integrante 1

“Advanced Message Queuing Protocol o AMQP es un protocolo abierto y orientado a mensajes diseñado para garantizar comunicación confiable entre aplicaciones distribuidas. A diferencia de otros protocolos más ligeros, AMQP no se limita a enviar mensajes: define cómo se enrutan, cómo se almacenan temporalmente y cómo se aseguran.
Su fortaleza está en ser robusto, interoperable y altamente confiable, por lo que es estándar en sistemas financieros, telecomunicaciones y plataformas de misión crítica.
AMQP está compuesto por cuatro actores principales: Producer, Exchange, Queue y Consumer. Todo mensaje pasa por este flujo y el broker es quien administra esta interacción.”

## 2. Tipos de Exchange

Habla: Integrante 1

“El Exchange es el corazón del enrutamiento de mensajes en AMQP. No almacena nada, sólo decide a qué cola enviar cada mensaje según reglas llamadas bindings.”

Tipos:

1. Direct Exchange: enrutamiento por coincidencia exacta de routing key.

2. Fanout Exchange: broadcast; envía a todas las colas asociadas.

3. Topic Exchange: usa patrones (*.error, app.log.*).

4. Headers Exchange: basado en metadatos en vez de claves.

“Para nuestro demo utilizamos los más comunes: direct para una cola de trabajo y fanout para un esquema publicación/suscripción.”

## 3. Arquitectura AMQP

Habla: Integrante 2

“Una arquitectura AMQP clásica tiene este flujo: el producer envía mensajes hacia el exchange, el exchange los enruta a una o varias queues, y finalmente un consumer los procesa.
Esta arquitectura desacopla completamente productores y consumidores. Ninguno necesita conocer la existencia del otro. Sólo interactúan a través del broker.”

Puntos clave:

- El producer no conoce al consumer.

- Las queues absorben diferencias de velocidad.

- Se pueden replicar consumers para balanceo de carga.

- Los ACKs evitan pérdida de mensajes.

## 4. AMQP vs MQTT

Habla: Integrante 2

“AMQP y MQTT son protocolos de mensajería, pero están diseñados para mundos diferentes.
MQTT está pensado para IoT, sensores, dispositivos con recursos limitados y redes inestables. Su prioridad: ser ligero.
AMQP está pensado para sistemas robustos, empresariales y transaccionales donde la confiabilidad, la persistencia y el control del enrutamiento son clave.”

Comparación breve:

AMQP

- Complejo, robusto
- Asegura entrega
- Exchange + queues + bindings
- TCP
-Casos: finanzas, microservicios, telecom

MQTT

- Ultra ligero
- Pub/Sub básico
- Ideal para IoT
- Brokers como Mosquitto
- Casos: sensores, wearables, telemetría

“En resumen: MQTT es mínimo y rápido, AMQP es completo y confiable.”

## 5. Casos de Uso

Habla: Integrante 2

“AMQP se utiliza cuando la empresa necesita mensajería confiable, ordenada y con control total de enrutamiento. Los casos más comunes incluyen:”

- Procesamiento asíncrono de tareas (PDFs, correos, imágenes).
- Microservicios desacoplados.
- Filas de trabajo con varios workers.
- Arquitecturas basadas en eventos.
- Plataformas financieras.
- Sistemas de telecomunicaciones.

## 6. Setup y Configuración

Habla: Integrante 2

“Para la demostración utilizamos RabbitMQ corriendo en un contenedor. También evaluamos CloudAMQP porque facilita el acceso remoto para el trabajo en equipo.
En nuestro caso, lo configuramos así:”

Checklist:

- RabbitMQ vía Docker o CloudAMQP.
- Activación del dashboard de administración.
- Creación del exchange direct y del fanout.
- Configuración de colas y bindings.
- Pruebas manuales desde el panel.

Entorno Python:

pip install pika

scripts Producer/Consumer

“Una vez listo el entorno, ya podemos demostrar el flujo real de envío y consumo de mensajes.”

## TRANSICIÓN AL DEMO

Habla: Integrante 2

“Con el setup completo, ahora pasamos a la demostración para ver cómo interactúan productores, exchanges, colas y consumidores en tiempo real. Le doy la palabra a [Nombre].”

## 7. Demo

Habla completamente: Integrante 3

Contenido sugerido:

RabbitMQ Management UI

Cola con Direct Exchange

Producer enviando

Consumers procesando

Pub/Sub con Fanout

Confirmación de ACKs y conteos

## 8. Conclusiones

Hablan: Integrante 1 y 2

Integrante 1:

“AMQP ofrece una capa de mensajería madura, robusta y confiable. Su arquitectura basada en exchanges y queues permite desacoplar sistemas al máximo y manejar grandes volúmenes de mensajes sin pérdida.”

Integrante 2:

“RabbitMQ facilita todo el ecosistema: métricas, monitoreo y flexibilidad en el enrutamiento. La separación producer–exchange–queue–consumer crea un patrón ideal para microservicios y sistemas distribuidos. Nuestro demo refleja estos conceptos en acción.”
