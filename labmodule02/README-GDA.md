# Gateway Device Application (Connected Devices)

## Lab Module 02

Be sure to implement all the PIOT-GDA-* issues.

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-GDA-02-000 → Crear una rama “LAB02” en java-components para hacer las modificaciones de solo este lab.

PIOT-GDA-02-001 → La implementación del SystemPerformanceManager se encarga de gestionar el ciclo de vida de una aplicación. Esto incluye el inicio y la detención de la aplicación, así como la configuración inicial basada en los parámetros proporcionados. Además, registra eventos clave en el proceso a través de un sistema de logs, lo que facilita el seguimiento de su funcionamiento.

PIOT-GDA-02-002 → La creación del módulo SystemPerformanceManager se encarga de gestionar el rendimiento del sistema, a través de un módulo que permite iniciar y detener un "gestor de rendimiento". Además, lee configuraciones relacionadas con el intervalo de sondeo y ajusta su funcionamiento según esos parámetros. Durante el proceso de inicio y paro, registra información en los logs para mantener un seguimiento claro del estado del sistema.

PIOT-GDA-02-003 → La conexión del SystemPerformanceManager conecta el módulo SystemPerformanceManager con la clase GatewayDeviceApp para que el rendimiento del sistema pueda ser gestionado al iniciar y detener la aplicación. Esto permite que el gestor de rendimiento comience y termine su monitoreo junto con la aplicación principal, proporcionando un control más centralizado de ambos procesos.

PIOT-GDA-02-004 → La creación del BaseSystemUtilTask crea un módulo que obtiene información sobre el uso de la CPU del sistema. Este módulo mide el porcentaje de utilización de la CPU en tiempo real, lo que es útil para monitorear el rendimiento del sistema y detectar posibles problemas o cuellos de botella.

PIOT-GDA-02-005 → La creación del SystemCpuUtilTask crea un módulo que se encarga de obtener la utilización de la CPU del sistema. A través de un método que devuelve el promedio de la carga de la CPU, se obtiene información sobre el uso actual del procesador, lo cual puede ser útil para monitorear el rendimiento del sistema.

PIOT-GDA-02-006 → La creación del SystemMemUtilTask crea un módulo que mide la utilización de la memoria en la Java Virtual Machine (JVM). El objetivo es obtener la cantidad de memoria que está siendo utilizada por el sistema y expresarlo como un porcentaje del total de memoria disponible. Esto ayuda a monitorear el uso de recursos de memoria en aplicaciones que se ejecutan en la JVM.

PIOT-GDA-02-007 → Este ejercicio consiste en integrar las funcionalidades de SystemCpuUtilTask y SystemMemUtilTask en el módulo SystemPerformanceManager. El objetivo es crear una forma automatizada de medir y registrar la utilización de la CPU y la memoria en intervalos regulares. Esto se realiza invocando sus métodos getTelemetryValue() a través de un hilo programado, permitiendo que los datos se recopilen de manera periódica y eficiente.

PIOT-GDA-02-100 → Hacemos commit de todos los cambios llamado “cambios LAB02” y hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB02


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ConfigUtilTest
- SystemCpuUtilTaskTest
- SystemMemUtilTaskTest

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- GatewayDeviceAppTest
- SystemPerformanceManagerTest
- 

EOF.
