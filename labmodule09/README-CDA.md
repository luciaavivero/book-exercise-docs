# Constrained Device Application (Connected Devices)

## Lab Module 09

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CDA-09-000 → Crear una rama “LAB09” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-09-001 → Mi implementación crea un conector cliente CoAP en Python utilizando la biblioteca aiocoap, para interactuar con un servidor CoAP. El cliente se configura para conectarse a un servidor especificado en un archivo de configuración, obteniendo la dirección IP y el puerto. Se define un constructor que inicializa el cliente, y varios métodos de la interfaz IRequestResponse son implementados, aunque por ahora solo registran su invocación. El conector permite manejar solicitudes como GET, POST, DELETE, y PUT, además de integrar la gestión de datos mediante un listener. Se conecta finalmente al sistema IoT a través de la clase DeviceDataManager si se habilita en la configuración.

PIOT-CDA-09-002 → Mi implementación actualiza la clase CoapClientConnector para permitir el envío de solicitudes GET usando la biblioteca aiocoap. El método sendGetRequest construye la ruta del recurso y realiza la petición de forma asíncrona, utilizando un bucle de eventos de asyncio. Internamente, se crea un mensaje CoAP con tipo confirmado (CON) o no confirmado (NON), según se indique. La respuesta se recibe y se maneja mediante el método _onGetResponse. Esta funcionalidad permite recuperar datos de dispositivos o servicios expuestos vía CoAP.

PIOT-CDA-09-003 → Mi implementación amplía la clase CoapClientConnector para admitir solicitudes PUT mediante la biblioteca aiocoap, permitiendo enviar datos a un recurso CoAP. El método sendPutRequest construye la ruta del recurso y lanza una operación asíncrona que incluye el payload codificado en UTF-8. Internamente, _handlePutRequest crea un mensaje con tipo CON o NON según se especifique, lo envía al servidor y maneja la respuesta con _onPutResponse. Esta funcionalidad permite actualizar datos de sensores o dispositivos en el sistema IoT. 

PIOT-CDA-09-004 → Mi implementación extiende la clase CoapClientConnector para admitir solicitudes POST usando la biblioteca aiocoap, permitiendo crear o enviar datos a un recurso CoAP. El método principal, sendPostRequest, genera una ruta de recurso basada en los parámetros dados, codifica el payload como bytes UTF-8, y lanza una operación asíncrona. Internamente, _handlePostRequest construye el mensaje con tipo CON o NON, envía la solicitud al servidor CoAP y maneja la respuesta usando _onPostResponse. 

PIOT-CDA-09-005 → Mi implementación añade soporte para solicitudes DELETE usando la biblioteca aiocoap dentro de la clase CoapClientConnector. El método sendDeleteRequest construye la ruta del recurso, selecciona el tipo de mensaje CoAP (CON o NON), y ejecuta una operación asíncrona para eliminar el recurso remoto. Internamente, _handleDeleteRequest crea el mensaje con Code.DELETE, lo envía al servidor CoAP, y maneja la respuesta con _onDeleteResponse.

PIOT-CDA-09-006 → Mi implementación añade soporte para operaciones de observación CoAP (OBSERVE) en el módulo CoapClientConnector, utilizando aiocoap. Se introducen los métodos startObserver y stopObserver para iniciar y detener observaciones sobre recursos remotos. Internamente, _handleStartObserveRequest envía una solicitud GET con el flag observe=0, almacena la solicitud en observeRequests, y escucha actualizaciones usando un bucle asíncrono. _handleStopObserveRequest cancela activamente las observaciones registradas. 

PIOT-CDA-09-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-09-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB09



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

- CoapClientConnectorTest
  - testGetActuatorCommandCon()
	- testGetActuatorCommandNon()
	- testPutSensorMessageCon ()
	- testPutSensorMessageNon ()
	- testPostSensorMessageCon ()
	- testPostSensorMessageNon ()
	- testDeleteSensorMessageCon ()
  - testDeleteSensorMessageNon ()
	- testActuatorCommandObserve()


EOF.
