# Gateway Device Application (Connected Devices)

## Lab Module 01

Be sure to implement all the PIOT-GDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

Para llevar a cabo este proyecto, utilicé WSL con una distribución de Ubuntu. Instalé la versión 3.12.3 de Python, junto con pip 24.0, y para Java, configuré OpenJDK 21.0.6. Además, instalé Git para la gestión del código fuente.

Posteriormente, creé una carpeta denominada programmingtheiot, en la cual cloné los repositorios proporcionados para este proyecto: python-components, java-components y book-exercise-docs. finalmente, configuré un entorno virtual .venv para trabajar en el proyecto de manera aislada y organizada.

Actualice la variable DEFAULT_CONFIG_FILE_NAME del archivo ConfigConst.java por el path del archivo PiotConfig.props que tiene en mi proyecto. Además, instale una extensión, maven for java, para poder ejecutar los test de java.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/java-components/tree/LAB01


### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ConfigUtilTest


### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- GatewayDeviceAppTest

EOF.
