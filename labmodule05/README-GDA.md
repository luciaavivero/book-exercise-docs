# Gateway Device Application (Connected Devices)

## Lab Module 05

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-GDA-05-000 → Crear una rama “LAB05” en java-components para hacer las modificaciones de solo este lab.

PIOT-GDA-05-001 → Esta implementación define varias clases en Java para manejar datos de sensores y actuadores dentro de un sistema IoT. Todas estas clases extienden BaseIotData, que proporciona funcionalidades comunes como nombres, identificadores y marcas de tiempo. ActuatorData almacena información sobre comandos y estados de actuadores, mientras que SensorData maneja valores de sensores. SystemPerformanceData rastrea el uso de CPU, memoria y disco.

PIOT-GDA-05-002 → Esta implementación actualiza la clase SystemPerformanceManager para almacenar los datos de rendimiento del sistema (CPU y memoria) recopilados por handleTelemetry() en una instancia de SystemPerformanceData. Si está configurada una referencia a IDataMessageListener, se invoca un método de retroalimentación cuando se crea un nuevo objeto SystemPerformanceData. Además, se agregan nuevas variables de clase para el ID de ubicación y el listener de mensajes, y se añade un método para establecer dicho listener. También se implementa un seguimiento de la utilización del disco similar a la memoria y la CPU.

PIOT-GDA-05-003 → Esta implementación edita la clase llamada DataUtil que incluye métodos públicos para convertir objetos de tipo ActuatorData, SensorData y SystemPerformanceData a JSON, y viceversa, utilizando la librería gson. El método actuatorDataToJson convierte un objeto ActuatorData en una cadena JSON, mientras que jsonToActuatorData convierte una cadena JSON de nuevo en un objeto ActuatorData. La misma lógica debe aplicarse a las clases SensorData y SystemPerformanceData, y opcionalmente a SystemStateData. El propósito es proporcionar una utilidad sencilla para la conversión de estos objetos a formato JSON y viceversa.

PIOT-GDA-05-004 → Esta implementación crea la clase DeviceDataManager en el paquete programmingtheiot.gda.app, la cual maneja el procesamiento de datos dentro de la aplicación GDA. La clase se encarga de gestionar las conexiones y los administradores de rendimiento del sistema, configurando diversos clientes y servidores a partir de las propiedades definidas en el archivo de configuración mediante ConfigUtil. El constructor configura las conexiones, como MQTT, CoAP, y Cloud Client, mientras que el método initManager() inicializa los diferentes administradores y clientes según las configuraciones habilitadas. Además, implementa los métodos del IDataMessageListener para procesar respuestas de actuadores, mensajes de sensores y de rendimiento del sistema. La clase también gestiona el inicio y detención de los servicios con los métodos startManager() y stopManager().

PIOT-GDA-05-005 → Esta implementación consiste en integrar la clase DeviceDataManager dentro de la aplicación GatewayDeviceApp. Se debe crear una instancia de DeviceDataManager en el constructor de la clase y luego invocar sus métodos startManager() y stopManager() en los métodos correspondientes startApp() y stopApp(). Además, se debe asegurar que DeviceDataManager gestione correctamente el inicio y la detención de SystemPerformanceManager dentro de sus propios métodos startManager() y stopManager(). Esto permite coordinar las operaciones del sistema de manera centralizada.

PIOT-GDA-05-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-05-00x” siendo x el número del apartado que corresponde y hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: 


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ActuatorDataTest
- SensorDataTest
- SystemPerformanceDataTest
- SystemStateDataTest
- DataUtilTest

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- SystemPerformanceManagerTest
- DataIntegrationTest
- DeviceDataManagerNoCommsTest
- GatewayDeviceAppTest

EOF.
