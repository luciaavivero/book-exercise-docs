# Constrained Device Application (Connected Devices)

## Lab Module 10

Be sure to implement all the PIOT-CDA-* issues (requirements) listed.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-10-001 → Mi implementación habilita el soporte de TLS en una instancia local del broker MQTT Mosquitto para permitir conexiones seguras cifradas entre el broker y los clientes (GDA y CDA). Esto se logra generando certificados de prueba con OpenSSL, configurando Mosquitto para usarlos, y actualizando tanto su archivo de configuración como los de los clientes. El proceso incluye ubicar correctamente los certificados, adaptar rutas según el entorno (Ubuntu o WSL) y asegurar permisos adecuados. Esta configuración permite establecer una comunicación MQTT segura y cifrada mediante TLS.

PIOT-CDA-10-000 → Crear una rama “LAB10” en python-components para hacer las modificaciones de solo este lab.

PIOT-INT-10-001 →  Para probar el rendimiento de publicación MQTT en CDA, se crea una clase de prueba MqttClientPerformanceTest.py en src/test/python/.../connection. Se desactivan los logs en los métodos publishMessage y onPublish, y se usa wait_for_publish() para asegurar que cada mensaje se publique antes de continuar. Se realizan 10,000 publicaciones con QoS 0, 1 y 2, primero sin TLS y luego con TLS activado, midiendo el tiempo total. Esta prueba debe ejecutarse localmente y no contra un servidor público. El objetivo es evaluar el rendimiento de publicación sin interferencias externas.

PIOT-INT-10-002 → Para probar el rendimiento de CoAP en CDA, se crea la clase CoapClientPerformanceTest.py en src/test/python/.../connection, basada en CoapClientConnectorTest. Se desactivan temporalmente los logs en métodos relacionados con POST y PUT, tanto en CoapClientConnector como en GenericCoapResourceHandler. Se ejecutan 10,000 solicitudes POST usando modos CON (confirmado) y NON (no confirmado), midiendo el tiempo total de ejecución. Cada solicitud utiliza datos serializados desde un objeto SensorData. Estas pruebas deben ejecutarse localmente para asegurar consistencia. 

PIOT-CDA-10-001 → Para habilitar conexiones TLS en el MqttClientConnector de CDA, se agregan configuraciones que permiten activar o desactivar el cifrado y definir el archivo del certificado (PEM). En el método connectClient(), se verifica si TLS está habilitado, y en tal caso, se configura el puerto seguro y se establece el contexto SSL con tls_set(), usando ssl.PROTOCOL_TLS_CLIENT. Esta implementación permite conexiones cifradas hacia el broker MQTT, incrementando la seguridad de la comunicación. Se mantiene compatibilidad con conexiones sin cifrado, en caso de fallos o configuraciones sin TLS.

PIOT-CDA-10-002 → Para permitir que el CDA procese mensajes de comando de actuadores enviados por el GDA, se actualiza la interfaz IDataMessageListener con el método handleActuatorCommandMessage(), que recibe un objeto ActuatorData. Luego, en la clase DeviceDataManager, se implementa este método, verificando que los datos sean válidos antes de delegar el comando al actuatorAdapterMgr. Esto habilita al CDA para ejecutar acciones físicas o simuladas basadas en instrucciones del GDA, completando así el flujo bidireccional de comunicación IoT.

PIOT-CDA-10-003 → Para que el CDA pueda recibir comandos de actuación del GDA mediante MQTT, se actualiza la clase MqttClientConnector para suscribirse al tópico correspondiente y redirigir los mensajes a IDataMessageListener. Se agrega una referencia a este listener, se define una función onActuatorCommandMessage() para decodificar los datos usando DataUtil, y se enlaza dicha función en onConnect() con message_callback_add(). Además, se recomienda deshabilitar msgInfo.wait_for_publish() en publishMessage() para evitar bloqueos. Esta implementación permite que el CDA actúe en tiempo real ante comandos del GDA.

PIOT-CDA-10-004 → Se actualiza DeviceDataManager para implementar el método _handleUpstreamTransmission, que se encarga de enviar datos de sensores o de rendimiento del sistema al GDA. Puedes elegir entre MQTT o CoAP para la transmisión (por simplicidad y menor latencia, se suele preferir MQTT). Luego, dentro de handleSensorMessage() y handleSystemPerformanceMessage(), se convierte la instancia de datos a JSON usando DataUtil() y se envía llamando a _handleUpstreamTransmission. Además, se verifica si la temperatura excede los umbrales definidos en PiotConfig.props, en cuyo caso se debe activar un evento de actuación (esto ya debe estar implementado en _handleSensorDataAnalysis). Esto asegura una comunicación fluida y en tiempo real entre el CDA y el GDA.

PIOT-CDA-10-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-10-00x” siendo x el número del apartado que corresponde y  hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB10


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

- MqttClientPerformanceTest
- 
- 

EOF.
