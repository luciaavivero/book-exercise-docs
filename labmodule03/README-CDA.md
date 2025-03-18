# Constrained Device Application (Connected Devices)

## Lab Module 03

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CDA-03-000 → Crear una rama “LAB03” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-03-001 → La implementación tiene como objetivo crear una estructura de datos para gestionar información proveniente de sensores (SensorData), actuadores (ActuatorData) y el rendimiento del sistema (SystemPerformanceData). A través de una clase base común (BaseIotData), otras clases especializadas permiten manejar y almacenar datos como valores de sensores, comandos de actuadores y estadísticas de uso de recursos del sistema (como CPU y memoria). Esta estructura facilita la gestión y el acceso a estos datos de manera organizada y coherente.


PIOT-CDA-03-002 → La implementación tiene como objetivo crear un módulo que simula la generación de datos de sensores (BaseSensorSimTask). Este módulo puede usar un conjunto de datos predefinido o generar valores aleatorios dentro de un rango especificado. Permite simular la recolección de datos de sensores de manera flexible y controlada, dependiendo de la configuración utilizada (aleatoria o de conjunto de datos).


PIOT-CDA-03-003 → La implementación crea tres módulos de simulación de sensores derivados de la clase base BaseSensorSimTask. Cada uno de estos módulos representa un tipo de sensor específico: Humedad (HumiditySensorSimTask), Presión (PressureSensorSimTask) y Temperatura (TemperatureSensorSimTask). Los módulos simulan el comportamiento de cada sensor y pueden trabajar con conjuntos de datos predefinidos o generar datos aleatorios dentro de un rango especificado.

PIOT-CDA-03-004 → La implementación crea una clase base llamada BaseActuatorSimTask, que simula el comportamiento de un actuador. El objetivo principal de esta clase es recibir comandos de encendido y apagado (y posiblemente otros comandos en el futuro), activar o desactivar el actuador según el comando, y devolver un objeto ActuatorData con el estado actualizado del actuador. Esta clase maneja la lógica básica de actuadores y sirve como base para implementaciones más específicas de actuadores en el futuro.


PIOT-CDA-03-005 → La implementación crea dos módulos para simular actuadores específicos: un humidificador (HumidifierActuatorSimTask) y un HVAC (calefacción, ventilación y aire acondicionado) (HvacActuatorSimTask). Ambos módulos heredan de la clase base BaseActuatorSimTask, que proporciona la funcionalidad básica para activar y desactivar los actuadores. Los nuevos módulos se centran en configurar los parámetros necesarios para cada tipo de actuador, como el nombre, el tipo de identificador y un nombre simple para facilitar la gestión de logs. Aunque la activación y desactivación de los actuadores se gestionan de manera genérica en la clase base, los módulos derivados permiten especificar características particulares de cada tipo de actuador.

PIOT-CDA-03-006 → La implementación del SensorAdapterManager tiene como objetivo gestionar simuladores para obtener datos de sensores como temperatura, presión y humedad. La clase se encarga de crear y configurar instancias de simuladores para cada tipo de sensor, de acuerdo con los valores de piso y techo definidos en el archivo de configuración. Además, la clase maneja un cronograma que ejecuta de forma periódica la generación de datos de sensores a través de la biblioteca APScheduler, con un intervalo determinado por la tasa de sondeo configurada. Dependiendo de la configuración, la implementación utiliza simuladores para generar datos de sensores en lugar de emuladores. La clase también se encarga de pasar estos datos generados a un oyente de mensajes que procesará la información.

PIOT-CDA-03-007 → La implementación de la clase ActuatorAdapterManager se encarga de gestionar los actuadores de un dispositivo, especialmente en lo que respecta a las simulaciones de actuadores ambientales como humidificadores y sistemas de calefacción, ventilación y aire acondicionado (HVAC). Su principal tarea es recibir y procesar comandos de actuación enviados al dispositivo, actuando sobre los componentes simulados según las configuraciones establecidas. Dependiendo de los parámetros configurados, la clase puede trabajar con simuladores o emuladores, lo que afecta cómo se simulan o gestionan las respuestas de los actuadores. Además, permite la integración con otros componentes del sistema mediante un listener, que se encarga de procesar los datos relacionados con los actuadores.

PIOT-CDA-03-008 → La implementación de este módulo se centra en la creación de una clase llamada DeviceDataManager que maneja todos los procesos relacionados con la recopilación y procesamiento de datos provenientes de sensores y actuadores. En primer lugar, la clase se encarga de la configuración de los elementos necesarios para el funcionamiento de los sistemas de seguimiento de desempeño del sistema, sensores y actuadores. Dependiendo de los valores de configuración, que son obtenidos a través de un archivo de configuración (PiotConfig.props), se habilitan los módulos correspondientes. La clase DeviceDataManager también proporciona los métodos necesarios para gestionar y procesar los mensajes provenientes de los sensores y actuadores, así como para comunicar estos datos a otros sistemas.

PIOT-CDA-03-009 → La implementación consiste en modificar la clase ConstrainedDeviceApp para integrar y gestionar la instancia de DeviceDataManager. Se han realizado cambios en los métodos de inicio y detención de la aplicación para incluir el control del ciclo de vida del DeviceDataManager, llamando a sus métodos de inicio y detención respectivamente. Además, se eliminan referencias a componentes como SystemPerformanceManager, que eran gestionados anteriormente dentro de la aplicación. El objetivo de esta implementación es mejorar la gestión de datos de los dispositivos, centralizando la lógica en el DeviceDataManager, el cual se encarga de coordinar las interacciones entre los diferentes módulos del sistema, como los sensores y actuadores.

PIOT-CDA-03-100 → Hacemos commit de todos los cambios llamado “cambios LAB03” y hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB03

### Unit Tests Executed

NOTE: The instructor will execute your unit tests. You only need to list each test case below
(e.g. ConfigUtilTest, DataUtilTest, etc). Be sure to include all previous tests, too,
since you need to ensure you haven't introduced regressions.

- ActuatorDataTest
- SensorDataTest
- SystemPerformanceDataTest
- HumiditySensorSimTaskTest
- PressureSensorSimTaskTest
- TemperatureSensorSimTaskTest
- HumidifierActuatorSimTaskTest
- HvacActuatorSimTaskTest

### Integration Tests Executed

NOTE: The instructor will execute most of your integration tests using their own environment, with
some exceptions (such as your cloud connectivity tests). In such cases, they'll review
your code to ensure it's correct. As for the tests you execute, you only need to list each
test case below (e.g. SensorSimAdapterManagerTest, DeviceDataManagerTest, etc.)

- SensorAdapterManagerTest
- ActuatorAdapterManagerTest
- DeviceDataManagerNoCommsTest
- ConstrainedDeviceAppTest

EOF.
