# Constrained Device Application (Connected Devices)

## Lab Module 06

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-06-001 → Instalé y configuré el broker Mosquitto MQTT en un entorno Ubuntu 20.04 LTS. Esta instalación permite crear un servidor MQTT que facilita la comunicación entre dispositivos mediante el protocolo MQTT. El proceso incluye la instalación del software, configuración básica, y pruebas usando los clientes mosquitto_pub y mosquitto_sub. 

PIOT-CDA-06-000 → Crear una rama “LAB06” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-06-001 → Mi implementación crea un módulo en Python llamado MqttClientConnector, que actúa como cliente MQTT y sigue la interfaz IPubSubClient. El módulo se conecta a un broker MQTT usando la biblioteca Paho, con configuración leída desde archivos externos. Se implementan métodos para conectar y desconectar el cliente, así como preparar los métodos para publicar, suscribirse y manejar mensajes. También se permite asignar un listener para procesar datos entrantes. Esta estructura facilita la comunicación IoT de forma modular y escalable.

PIOT-CDA-06-002 → Mi implementación añade los métodos de callback al módulo MqttClientConnector para manejar eventos del cliente MQTT. Se implementan funciones que se ejecutan al conectar, desconectar, recibir mensajes, publicar y suscribirse a temas, registrando mensajes en el log para confirmar cada evento. Estos callbacks permiten gestionar la comunicación del cliente con el broker y preparar la lógica para el procesamiento de datos. Las funciones se asignan dentro del método connectClient() antes de establecer la conexión. Esto completa la integración básica del cliente MQTT con eventos clave.

PIOT-CDA-06-003 → Mi implementación añade al módulo MqttClientConnector la funcionalidad completa de publicación y suscripción usando MQTT. Se implementan los métodos publishMessage(), subscribeToTopic() y unsubscribeFromTopic(), validando siempre el tema y el nivel de QoS. Si los valores son incorrectos, se registran advertencias y se usan valores por defecto cuando sea necesario. El método publishMessage() espera a que el mensaje se publique antes de continuar, y tanto la suscripción como la desuscripción registran información útil en el log. Esto permite gestionar eficazmente la comunicación IoT con temas específicos.

PIOT-CDA-06-004 → En esta implementación, se integra la clase MqttClientConnector dentro del DeviceDataManager para gestionar la conexión con el broker MQTT. Se revisa el archivo de configuración usando ConfigUtil para verificar si se debe habilitar MQTT (por medio de la clave ENABLE_MQTT_CLIENT_KEY). Si es así, se instancia el cliente MQTT y se configura el listener.
En el método startManager(), se conecta el cliente al broker y se suscribe al tópico CDA_ACTUATOR_CMD_RESOURCE con un QoS configurable. En stopManager(), se cancela la suscripción a ese mismo tópico y se desconecta del broker, asegurando así una gestión limpia del ciclo de vida del cliente MQTT dentro de la aplicación.

PIOT-CDA-06-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-06-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB06


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

- MqttClientConnectorTest
  - testConnectAndDisconnect
  - testConnectAndCDAManagementStatusPubSub


EOF.
