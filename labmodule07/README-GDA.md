# Gateway Device Application (Connected Devices)

## Lab Module 07

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-07-001 → Configura y verifica el funcionamiento del broker Mosquitto.
Permite establecer comunicación entre clientes usando el protocolo MQTT.
Utiliza las herramientas mosquitto_pub y mosquitto_sub para probar la conexión.
También puede validarse mediante pruebas de integración del documento PIOT-GDA-07-001.
En resumen, garantiza que el broker esté correctamente instalado y operativo.

PIOT-GDA-07-000 → Crear una rama “LAB07” en java-components para hacer las modificaciones de solo este lab.

PIOT-GDA-07-001 → La implementación consiste en una clase Java llamada MqttClientConnector que permite establecer comunicación con un broker MQTT, utilizando configuración externa para definir parámetros como el host, puerto, cliente ID y tipo de conexión (sincrónica o asincrónica). La clase implementa las interfaces necesarias para manejar la conexión, publicación, suscripción y callbacks, y define los métodos básicos para conectar, desconectar y configurar el cliente. Aunque aún no se han implementado completamente todas las funciones, se ha estructurado la base necesaria para realizar pruebas de integración y extender la funcionalidad en ejercicios posteriores.

PIOT-GDA-07-002 → Esta implementación amplía la clase MqttClientConnector añadiendo los métodos de callback necesarios para manejar eventos clave del cliente MQTT: conexión exitosa, pérdida de conexión, entrega de mensajes y recepción de mensajes. Cada uno de estos métodos registra mensajes en el log para informar sobre el estado del cliente, como cuando se establece una conexión, se pierde, se entrega un mensaje publicado o se recibe un mensaje en un tema suscrito. Además, se asegura que la instancia del cliente MQTT tenga configurado el callback apuntando a la propia clase, permitiendo así que estos eventos sean gestionados directamente desde MqttClientConnector.

PIOT-GDA-07-003 → Esta implementación añade las funcionalidades de publicación y suscripción al módulo MqttClientConnector. Se incorporan los métodos publishMessage(), subscribeToTopic() y unsubscribeFromTopic(), los cuales gestionan la validación de los nombres de los temas y los niveles de QoS antes de realizar las operaciones correspondientes. En caso de errores, se registran mensajes detallados para facilitar la depuración. Además, se proporciona un método isConnected() que verifica el estado de la conexión. Estas funciones permiten una comunicación bidireccional con el broker MQTT, donde las notificaciones de entrega y suscripción se gestionan a través de los callbacks establecidos anteriormente.

PIOT-GDA-07-004 → Esta implementación implica la integración de MqttClientConnector en el DeviceDataManager para habilitar la comunicación con un broker MQTT. Se debe incluir un flag booleano enableMqttClient en el DeviceDataManager para habilitar o deshabilitar la funcionalidad MQTT. En el método initManager(), se crea una instancia de MqttClientConnector si el flag está activado. En el método startManager(), se realiza la conexión al broker MQTT y se suscriben varios temas, aunque la suscripción se moverá a un callback en la siguiente fase. Finalmente, en el método stopManager(), se añaden las llamadas necesarias para desuscribirse de los temas y desconectar al cliente MQTT de manera adecuada.

PIOT-GDA-07-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-07-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB07


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- 
- 
- 

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- MqttClientConnector
  - testConnectAndDisconnect
  - testPublishAndSuscribe


EOF.
