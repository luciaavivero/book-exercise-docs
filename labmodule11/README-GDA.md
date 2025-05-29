# Gateway Device Application (Connected Devices)

## Lab Module 11

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-11-001 → Configurar un servicio en la nube que soporte MQTT con TLS y autorización habilitada, como Ubidots STEM. Se debe crear una cuenta, generar un token de API y descargar los certificados raíz. Luego, se actualiza el archivo de configuración PiotConfig.props con la información de los archivos de credenciales y certificados, asegurándose de no subirlos al repositorio por razones de seguridad.

PIOT-GDA-11-000 → Crear una rama “LAB11” en java-components para hacer las modificaciones de solo este lab.

PIOT-GDA-11-001 → Actualizar la clase MqttClientConnector para permitir la carga de parámetros de configuración desde una sección personalizada del archivo PiotConfig.props y habilitar que clases o subclases puedan invocar directamente las funciones publish, subscribe y unsubscribe. Se agregan constructores y métodos como setConnectionListener para gestionar conexiones. También se implementan métodos protegidos para publicar, suscribir y desuscribir de temas, permitiendo el uso de convenciones de nombres de temas del proveedor de servicios en la nube. Además, se actualiza el método connectComplete() para gestionar suscripciones específicas a temas locales o de la nube.

PIOT-GDA-11-002 → Crear la interfaz Java ICloudClient, que define un contrato para clientes de publicación/suscripción (pub/sub). La interfaz incluye métodos para conectar y desconectar al servidor, enviar datos desde el borde a la nube (para instancias de SensorData y SystemPerformanceData), suscribirse y desuscribirse de eventos de la nube, y establecer un oyente de mensajes de datos. La implementación de esta interfaz permitirá a los clientes gestionar la comunicación con el servicio en la nube de manera flexible y eficiente.

PIOT-GDA-11-003 → Crear una clase Java llamada CloudClientConnector que implementa la interfaz ICloudClient. Esta clase se encarga de la conexión, desconexión, suscripción y publicación de datos hacia la nube, y delega muchas de sus funciones a una instancia de MqttClientConnector. 

PIOT-GDA-11-004 → Conectar el CDA al GDA y al servicio en la nube, enviando datos de sensores y rendimiento. En la nube, se deben almacenar variables como CPU, memoria y temperatura, y generar un evento de activación de LED basado en umbrales. Este evento se enviará al GDA, que lo procesará y reenviará al CDA para ejecutar la acción, como encender un LED o generar un log. Se deben verificar todos los pasos del flujo de datos. El GDA debe suscribirse al tópico de eventos de activación de LED en la nube para gestionarlos correctamente.

PIOT-GDA-11-100 → Hacemos commit de todos los cambios llamado “PIOT-GDA-11-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB11


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

- CloudClientConnectorTest
- 
- 

EOF.
