# Gateway Device Application (Connected Devices)

## Lab Module 08

Be sure to implement all the PIOT-GDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-08-001 → Instale y configure las herramientas Californium CoAP para realizar pruebas iniciales con un servidor CoAP. El proceso incluye clonar el repositorio, compilar con Maven y ejecutar el cliente desde línea de comandos. La herramienta permite enviar solicitudes CoAP al servidor para verificar su funcionamiento.
PIOT-CFG-08-002 → Instalé y configuré la biblioteca aiocoap para desarrollar aplicaciones IoT basadas en el protocolo CoAP.

PIOT-GDA-08-000 → Crear una rama “LAB08” en java-components para hacer las modificaciones de solo este lab.

PIOT-GDA-08-001 → Mi implementación crea e inicializa la clase CoapServerGateway, que actúa como servidor CoAP usando la biblioteca Californium. Este servidor permite gestionar recursos locales y responder a solicitudes CoAP como GET, PUT, POST y DELETE. Se integra con DeviceDataManager mediante un listener para procesar mensajes entrantes. El servidor puede iniciarse o detenerse según una configuración booleana (enableCoapServer). La implementación configura, registra los recursos y asegura la comunicación IoT dentro del sistema.

PIOT-GDA-08-002 → Mi implementación crea dos manejadores de recursos CoAP personalizados: UpdateSystemPerformanceResourceHandler y UpdateTelemetryResourceHandler. Ambos extienden CoapResource y permiten que el CDA envíe datos al GDA mediante solicitudes PUT. Procesan los datos en formato JSON, los convierten a objetos Java (SystemPerformanceData o SensorData) y los pasan al DeviceDataManager. También implementan métodos básicos para GET, POST y DELETE que aceptan las solicitudes y responden con el código correspondiente. Así, habilitan la comunicación y actualización de datos en un entorno IoT distribuido.

PIOT-GDA-08-003 → Se implementó la clase GetActuatorCommandResourceHandler, que extiende CoapResource e implementa la interfaz IActuatorDataListener para manejar comandos de actuadores mediante el protocolo CoAP con soporte para la funcionalidad OBSERVE. Esta clase permite al GDA enviar actualizaciones automáticas al CDA tras una solicitud GET inicial. Se configuró el recurso como observable, se implementó el método onActuatorDataUpdate() para actualizar datos y notificar a los clientes conectados, y se sobreescribió handleGET() para aceptar la solicitud y responder con datos en formato JSON. Esta estructura facilita la comunicación bidireccional en tiempo real entre dispositivos IoT.

PIOT-GDA-08-004 → se actualizó DeviceDataManager para incluir una variable IActuatorDataListener y se implementó el método setActuatorDataListener(), permitiendo la recepción de actualizaciones de actuadores. Además, se integró el listener en el método handleIncomingDataAnalysis() para reenviar las actualizaciones al recurso CoAP correspondiente. En CoapServerGateway, se implementó el método initServer() para inicializar el servidor y crear los recursos predeterminados, mientras que initDefaultResources() se encargó de registrar los manejadores de recursos como GetActuatorCommandResourceHandler. Finalmente, se desarrollaron los métodos addResource() y createAndAddResourceChain() para facilitar la adición de recursos externos de manera dinámica en el servidor.

PIOT-GDA-08-100 → Hacemos commit de todos los cambios llamado “PIOT-GDA-08-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB08


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

- CoapClientToServerConnectorTest
  - testSystemPerformancePutMessage()


EOF.
