# Constrained Device Application (Connected Devices)

## Lab Module 05

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CDA-05-000 → Crear una rama “LAB05” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-05-001 → El módulo SystemPerformanceManager se actualiza para almacenar datos de rendimiento del sistema en SystemPerformanceData dentro de handleTelemetry(), registrando el uso de CPU y memoria. Si dataMsgListener está configurado, se invoca su callback con los datos recopilados. Además, se actualiza setDataMessageListener() para permitir futuros callbacks. Opcionalmente, se puede agregar monitoreo de uso de disco siguiendo el patrón de SystemCpuUtilTask y SystemMemUtilTask.

PIOT-CDA-05-002 → El módulo DataUtil se actualiza para convertir ActuatorData, SensorData y SystemPerformanceData a JSON y viceversa. Se usa JsonDataEncoder para serializar objetos y json.loads() para deserializarlos. Se implementan métodos de conversión con _generateJsonData() y _formatDataAndLoadDictionary(), asegurando compatibilidad con BaseIotData. 

PIOT-CDA-05-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-05-00x” siendo x el número del apartado que corresponde y hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB05


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

- SystemPerformanceManagerTest
- DataUtilTest
- DataIntegrationTest

EOF.
