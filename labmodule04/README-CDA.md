# Constrained Device Application (Connected Devices)

## Lab Module 04

Be sure to implement all the PIOT-CDA-* issues (requirements).

### Description

NOTE: Include two full paragraphs describing your implementation approach by answering the questions listed below.

What does your implementation do? 

How does your implementation work?

PIOT-CFG-04-001 → Instalamos ciertas librerías como Pisense y Sense-Emun para que facilite el desarrollo y haga pruebas de aplicaciones de IoT sin necesidad de hardware físico.

PIOT-CDA-04-000 → Crear una rama “LAB04” en python-components para hacer las modificaciones de solo este lab.

PIOT-CDA-04-001 → Esta implementación crea módulos en Python para emular sensores de humedad (HumidityEmulatorTask), presión (PressureEmulatorTask) y temperatura (TemperatureEmulatorTask) utilizando la biblioteca Pisense y Sense-Emu. Cada módulo hereda de BaseSensorSimTask y permite operar en modo de emulación o con hardware real según la configuración. Las clases recopilan datos del entorno (humedad, presión o temperatura) y los almacenan en objetos SensorData. Luego, estos datos pueden ser utilizados por otros componentes del sistema.

PIOT-CDA-04-002 → Esta implementación crea módulos para emular actuadores como un humidificador (HumidifierEmulatorTask), un HVAC (HvacEmulatorTask) y una pantalla LED (LedDisplayEmulatorTask) usando la biblioteca Pisense y Sense-Emu. Cada módulo hereda de BaseActuatorSimTask y permite operar en modo de emulación o con hardware real según la configuración. Los actuadores muestran mensajes en la pantalla LED del Sense HAT para indicar su estado (encendido o apagado). La pantalla LED emula la visualización de datos, mostrando información cuando está activa y limpiando la pantalla al desactivarse. 

PIOT-CDA-04-003 → El módulo SensorAdapterManager se actualiza para integrar el emulador SenseHAT, cargando dinámicamente sensores de temperatura, presión y humedad si self.useEmulator es True. Si está deshabilitado, usa datos simulados de SensorDataGenerator. La configuración permite definir límites personalizados para cada sensor. Esto mejora la modularidad y permite cambiar entre emulación y hardware real sin modificar la lógica central.

PIOT-CDA-04-004 → El módulo ActuatorAdapterManager se actualiza para integrar el emulador SenseHAT, cargando dinámicamente actuadores HVAC, humidificador y pantalla LED si self.useEmulator es True. Si está deshabilitado, usa simulaciones estándar. Se usa import_module() para cargar tareas según la configuración, permitiendo flexibilidad en pruebas sin hardware real. Esto optimiza la modularidad y facilita la alternancia entre emulación y hardware físico.

PIOT-CDA-04-100 → Hacemos commit de todos los cambios llamado “PIOT-CDA-04-00x” siendo x el número del apartado que corresponde y hacemos un merge para default.

### Code Repository and Branch

NOTE: Be sure to include the branch.

URL: https://github.com/luciaavivero/python-components/tree/LAB04


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

- SenseHatEmulatorQuickTest
- HumidityEmulatorTaskTest
- PressureEmulatorTaskTest
- TemperatureEmulatorTaskTest
- HumidifierEmulatorTaskTest
- HvacEmulatorTaskTest
- LedDisplayEmulatorTaskTest
- SensorEmulatorManagerTest
- ActuatorEmulatorManagerTest

EOF.
