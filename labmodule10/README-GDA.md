# Gateway Device Application (Connected Devices)

## Lab Module 10

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-GDA-10-000 → Crear una rama “LAB10” en java-components para hacer las modificaciones de solo este lab.

PIOT-INT-10-001 → Para GDA, se crea la clase MqttClientPerformanceTest.java en src/test/java/.../connection, usando la clase síncrona MqttClient de Paho, no MqttAsyncClient. Se eliminan los logs en publishMessage y deliveryComplete, y se hacen 10,000 publicaciones por nivel de QoS (0, 1 y 2). Cada ejecución mide el tiempo desde el envío hasta el cierre de conexión. También se prueba la conexión y desconexión por separado. Las pruebas deben correr localmente para evitar variabilidad de red.

PIOT-INT-10-002 → En GDA, se crea la clase CoapClientPerformanceTest.java en src/test/java/.../connection, siguiendo el modelo de CoapClientConnectorTest. Se deshabilitan logs en métodos POST y PUT, y se asegura que cada solicitud configure correctamente la URI del endpoint. Se envían 10,000 solicitudes POST con y sin confirmación (CON y NON), utilizando datos simulados en formato JSON. El rendimiento se mide registrando el tiempo desde la primera hasta la última solicitud. Todo debe ejecutarse en entorno local para resultados fiables.

PIOT-GDA-10-001 → Mi implementación actualiza la clase MqttClientConnector para soportar conexiones seguras MQTT con TLS y autenticación de usuario y contraseña. Configura estos parámetros cargándolos desde el archivo PiotConfig.props, incluyendo certificados y credenciales si están presentes. Si se habilita la encriptación, se carga un archivo PEM y se configura el SSLSocketFactory. Además, las credenciales de usuario y contraseña se cargan desde un archivo de configuración. Todo esto se gestiona a través del método initClientParameters, llamado por el constructor de la clase.

PIOT-GDA-10-002 → Mi implementación actualiza la clase MqttClientConnector para suscribirse a los temas relacionados con los mensajes de SensorData, SystemPerformanceData y las respuestas de ActuatorData del CDA. Utiliza un cliente MQTT asíncrono (MqttAsyncClient) para evitar condiciones de bloqueo, y dentro del método connectComplete(), se suscribe a estos temas mediante dos opciones: usando un único callback o implementando clases separadas para cada tipo de mensaje mediante la interfaz IMqttMessageListener. Además, he actualizado el DeviceDataManager para eliminar las suscripciones redundantes y moverlas a la clase MqttClientConnector, lo que asegura que los temas se suscriban después de una conexión exitosa al broker.

PIOT-GDA-10-003 → El objetivo es mejorar el DeviceDataManager para manejar mensajes CDA como SensorData, SystemPerformanceData y ActuatorData. En particular, se enfoca en analizar datos de humedad para verificar si superan los umbrales definidos en la configuración. Si se cruza un umbral, se debe activar o desactivar el humidificador, y este evento se debe enviar al CDA. Además, se debe registrar y verificar el tiempo transcurrido desde el último cruce del umbral, asegurando que las acciones solo se tomen después de un tiempo de espera adecuado. Este proceso requiere implementar la lógica de análisis de datos, comunicación con el CDA y gestión de la persistencia de eventos.


PIOT-GDA-10-100 → Hacemos commit de todos los cambios llamado “PIOT-GDA-10-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB10



### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- MqttConnectorTest
- 
- 

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- 
- 
- 

EOF.
