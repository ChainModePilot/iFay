# 12. Capa de Cognición — Habilidades

El subsistema de Habilidades de la Capa de Cognición es la "biblioteca de capacidades" de iFay — gestiona controladores de hardware, skills registrados externamente y capacidades inherentes.


---

## 12.1 Hub de controladores

## Definición en una línea

El Hub de controladores son los **nervios motores** de iFay — si el hardware son las "extremidades" de iFay, el Hub de controladores es el sistema nervioso motor que conecta el cerebro con las extremidades. Asegura que iFay pueda controlar correctamente varios dispositivos de hardware, y que nuevos dispositivos puedan conectarse sin necesidad de "reaprender a caminar."

## Por qué es necesario

Imagina tu cuerpo: tu cerebro quiere tomar una taza de la mesa, y no necesita saber cómo se contrae cada fibra de los músculos de tu brazo — los nervios motores traducen la intención "tomar la taza" en comandos musculares precisos. Mejor aún, cuando aprendes a montar bicicleta por primera vez, tu cerebro no necesita reaprender a caminar — las nuevas habilidades motoras se "superponen" a las vías neuronales existentes sin destruir las capacidades existentes.

iFay enfrenta la misma situación con el mundo del hardware. Bombillas inteligentes, aires acondicionados, cortinas, aspiradoras robot, drones… cada dispositivo tiene su propio "lenguaje" y método de control. Si iFay tuviera que reestructurar sus internos cada vez que se conecta un nuevo dispositivo, sería tan absurdo como tener que reaprender a caminar cada vez que aprendes un nuevo movimiento.

El Hub de controladores resuelve exactamente este problema. Es una **capa hub**, no un programa de controlador específico ni una simple colección de controladores. Proporciona una interfaz estandarizada que permite que cualquier nuevo controlador de dispositivo se conecte sin problemas, mientras que los otros módulos de iFay permanecen completamente inconscientes del cambio.

## Cómo funciona

La operación del Hub de controladores se puede resumir en tres palabras clave: **Estandarizado, Transparente, Degradación elegante**.

**1. Estandarizado — Contrato de interfaz unificado**

Ya sea una bombilla inteligente o un brazo robótico industrial, cada controlador de dispositivo debe seguir la misma especificación de interfaz al conectarse. El Hub de controladores define interfaces estándar de registro, invocación y consulta de estado.

**2. Transparente — Completamente transparente para otros módulos**

Cuando se añade un nuevo controlador de dispositivo a iFay, otros módulos de iFay (Sensor, Invocación de habilidades, Comportamiento autónomo, etc.) no necesitan ninguna modificación en absoluto. El Hub de controladores "absorbe" todas las diferencias de hardware, exponiendo solo una interfaz unificada externamente.

**3. Degradación elegante — El fallo de un controlador no crashea iFay**

¿Qué pasa si un controlador de dispositivo falla al cargar o un dispositivo se desconecta? El Hub de controladores no dejará que todo iFay se paralice por ello. Reportará el estado de no disponibilidad del controlador, proporcionará sugerencias de degradación, y el control de otros dispositivos permanece completamente no afectado.

## Historias de escenarios

### Escenario 1: iFay controlando el hogar inteligente

A las 8 PM, le dices a iFay: "Pon mi casa en modo película."

iFay entiende tu intención, luego controla simultáneamente múltiples dispositivos a través del Hub de controladores:

- **Controlador de bombilla inteligente**: Atenúa las luces del salón al 20%, cambia la temperatura de color a amarillo cálido
- **Controlador de aire acondicionado**: Establece temperatura a 24°C, reduce velocidad del ventilador al mínimo (modo silencioso)
- **Controlador de cortina inteligente**: Cierra cortinas para bloquear la luz externa
- **Controlador de proyector**: Enciende el proyector, cambia a fuente de entrada HDMI

Estos cuatro dispositivos son de diferentes marcas, usando diferentes protocolos de comunicación (WiFi, Bluetooth, Zigbee), pero iFay no necesita saber sobre estas diferencias en absoluto. El Hub de controladores protege toda la complejidad.

### Escenario 2: Nueva aspiradora robot — plug and play

Compras una nueva aspiradora robot y la traes a casa. Después de conectarla a tu red doméstica, iFay descubre el nuevo hardware a través del dispositivo terminal.

Lo que pasa después es casi imperceptible para ti:
1. El dispositivo terminal escanea la nueva aspiradora robot y reporta su información a iFay
2. El Hub de controladores carga automáticamente el controlador de la aspiradora robot (registrado a través de la interfaz estandarizada)
3. Una vez que el registro del controlador se completa, iFay inmediatamente gana la capacidad de controlar la aspiradora robot

No necesitas hacer ninguna configuración en iFay. A la mañana siguiente cuando sales a trabajar, el módulo de Comportamiento autónomo de iFay determina "el Human Prime se fue, buen momento para limpiar", y arranca la aspiradora robot a través del Hub de controladores para comenzar a barrer.

## Para desarrolladores

El Hub de controladores pertenece a la **Fase 2 (Toma de control directo del cliente)** como módulo central, dependiendo del Protocolo CAP.

- **ID de requisito**: Requisito 8 (Hub de controladores)
- **Especificación de interfaz**: Interfaz `DeviceDriverHub` con cuatro métodos centrales: `registerDriver()` (registrar controlador), `invokeDevice()` (invocar dispositivo), `getDriverStatus()` (consultar estado) y `unregisterDriver()` (desregistrar controlador)
- **Estados de controlador**: `loaded`, `active`, `error`, `unavailable`
- **Protocolo asociado**: CAP (Protocolo de Autoridad de Control) para llamar directamente a controladores de hardware terminal, interfaces locales y comandos
- **Módulos asociados**: Sensor (`SensorModule`) sus interfaces de hardware son gestionadas por el Hub de controladores, Montón de datos personales (`PersonalDataHeap`) almacena datos de dispositivos
- **Notas de diseño**: El Hub de controladores es una capa hub, no un controlador individual ni una colección de controladores; las interfaces estandarizadas aseguran que la integración de nuevos controladores sea transparente para otros módulos; proporciona sugerencias de degradación en lugar de crash del sistema cuando falla la carga de controladores
- **Pruebas de conformidad**: iFACTS L1 valida capacidades de registro e invocación de controladores, L2 valida la integración de interfaz con Sensor y Montón de datos personales, L4 valida el comportamiento de degradación cuando fallan los controladores
