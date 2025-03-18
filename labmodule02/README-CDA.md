# Constrained Device Application (Connected Devices)

## Lab Module 02

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CDA-02-000 → Crear una rama “LAB02” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-02-001 → La implementación del SystemPerformanceManager permite la gestión y ejecución de un dispositivo en un entorno IoT. Su objetivo es facilitar el control del sistema, asegurando que pueda iniciarse, ejecutarse y detenerse de manera estructurada. Además, proporciona una base para futuras ampliaciones y mejoras en el funcionamiento del dispositivo.

PIOT-CDA-02-002 → La creación del módulo SystemPerformanceManager gestiona el rendimiento del sistema dentro de un entorno IoT. Su función principal es monitorear ciertos parámetros del sistema y asegurarse de que los procesos relacionados con el dispositivo se ejecuten de manera eficiente. Además, actúa como un intermediario entre la configuración del dispositivo y otros módulos que necesitan acceder a estos datos.

PIOT-CDA-02-003 → La conexión del SystemPerformanceManager mejora la gestión del rendimiento del sistema dentro de la aplicación del dispositivo IoT. Se integra un administrador de rendimiento que permite supervisar y controlar el estado del sistema durante su ejecución, asegurando un funcionamiento más eficiente y estructurado.

PIOT-CDA-02-004 →  La creación del BaseSystemUtilTask define una estructura base para la gestión de tareas relacionadas con la monitorización del sistema en un entorno IoT. Su propósito es proporcionar una plantilla sobre la cual se pueden construir clases específicas que recopilen y procesen datos del sistema, como el uso de CPU, memoria o almacenamiento.

PIOT-CDA-02-005 → La creación del SystemCpuUtilTask permite medir el uso de la CPU en un sistema IoT. Proporciona un mecanismo para obtener datos en tiempo real sobre la carga del procesador, lo que puede ser útil para la monitorización del rendimiento y la optimización de recursos en dispositivos con capacidades limitadas.

PIOT-CDA-02-006 →  La creación del SystemMemUtilTask permite medir el uso de la memoria en un sistema IoT. Proporciona información en tiempo real sobre el porcentaje de memoria utilizada, lo que resulta útil para la gestión eficiente de los recursos en dispositivos con capacidad limitada.

PIOT-CDA-02-007 → Esta implementación amplía la funcionalidad del SystemPerformanceManager al conectarlas con SystemCpuUtilTask y SystemMemUtilTask. Utiliza la biblioteca apscheduler para ejecutar estas mediciones de manera automática, permitiendo una supervisión continua del rendimiento del sistema.

PIOT-CDA-02-100 → Hacemos commit de todos los cambios llamado “cambios LAB02” y hacemos un merge para default.


### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB02

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

- ConstrainedDeviceAppTest
- SystemPerformanceManagerTest

EOF.
