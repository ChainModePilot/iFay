# 13. Ensamblaje declarativo FayManifest

FayManifest es el "package.json" de iFay. Los desarrolladores simplemente listan los componentes, protocolos, modos de control y configuraciones de controladores requeridos en un único archivo de declaración JSON, y el entorno de ejecución FayGer resuelve automáticamente las dependencias y ensambla la instancia de iFay. No necesitas entender toda la complejidad del sistema iFay — declara lo que necesitas, y el sistema completa el resto.

---

## Por qué se necesita FayManifest

Uno de los principios de diseño de iFay es **ensamblaje mínimo declarativo + adopción progresiva**.

**Problema**: Construir un iFay completo desde cero es complejo — 12 módulos centrales, 6 protocolos, sistemas de permisos, cumplimiento de seguridad, sincronización multi-terminal… Si cada desarrollador tuviera que entender e implementar todo esto, el ecosistema iFay nunca despegaría.

**Solución**: Los desarrolladores solo necesitan declarar el subconjunto de componentes que su negocio requiere, y el sistema complementa automáticamente las dependencias de infraestructura necesarias.

---

## Estructura del archivo FayManifest

FayManifest usa formato JSON y contiene los siguientes campos:

| Campo | Tipo | Requerido | Descripción |
|-------|------|-----------|-------------|
| `name` | string | ✅ | Nombre de la implementación iFay |
| `version` | string | ✅ | Número de versión |
| `description` | string | ✅ | Descripción funcional |
| `vendor` | string | ✅ | Nombre del desarrollador/proveedor |
| `modules` | array | ✅ | Lista de módulos requeridos; cada módulo puede especificar restricciones de versión (`version`), implementación del proveedor (`provider`) y configuración (`config`) |
| `protocols` | array | ✅ | Lista de protocolos requeridos; cada protocolo puede especificar versión y configuración |
| `controlMode` | string | ✅ | Modo de control: `command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | Configuraciones de controladores especificando nombre, tipo, identificador de paquete y configuración |
| `ego` | object | ❌ | Configuración del Modelo Ego especificando fuente del modelo, etiquetas de escenario aplicables y parámetros de restricción |
| `permissions` | object | ❌ | Configuración de permisos declarando permisos inherentes, persistentes y métodos de autenticación soportados |

---

## Modos de control

El campo `controlMode` en FayManifest determina el enfoque de impulso de comportamiento de iFay — elige uno de tres:

| Modo | Nombre | Descripción |
|------|--------|-------------|
| `command` | **Control por comando** | El Human Prime impulsa explícitamente cada acción. iFay no actuará autónomamente; cada operación requiere el comando explícito del Human Prime. Adecuado para escenarios de alto riesgo o fases iniciales de construcción de confianza. |
| `ego` | **Control Ego** | El Modelo Ego toma decisiones autónomas dentro de límites restringidos. iFay puede juzgar y actuar autónomamente basándose en la personalidad y preferencias del Human Prime, pero los límites conductuales están restringidos por el Modelo Ego. Adecuado para escenarios de asistente diario. |
| `autonomous` | **Control autónomo** | Comportamiento completamente autónomo. iFay opera autónomamente basándose en Autoconciencia, Comportamiento autónomo y Habilidades internas, formando un bucle continuo "acción → retroalimentación → re-acción". Adecuado para escenarios de colaboración a largo plazo con alta confianza. |

---

## Complementación automática de dependencias

El diseño central de FayManifest: los desarrolladores declaran componentes de negocio, el sistema complementa automáticamente la infraestructura.

La siguiente infraestructura es requerida en todas las implementaciones de iFay — ya sea que los desarrolladores las declaren explícitamente o no, el sistema las añade automáticamente:

- **FayID** (Identidad)
- **Entorno de ejecución FayGer** (Contenedor de ejecución)
- **Perfil iFay** (Modelo de datos unificado)
- **Sistema de permisos** (Gestión de permisos)
- **Cumplimiento de seguridad y ética** (Restricciones conductuales)
- **Sincronización multi-terminal** (Sincronización de estado)
- **Protocolo Faying** (Emparejamiento seguro, requerido para todo iFay)

---

## Ejemplo completo: iFay de control de drones

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "Implementación iFay para control de drones",
  "vendor": "DroneAI Corp",

  "modules": [
    { "id": "device_driver_hub", "version": "^1.0.0" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera", "lidar"] } },
    { "id": "invoke_skill", "version": "^1.0.0" },
    { "id": "registered_skill", "config": { "preload": ["flight_control", "obstacle_avoidance"] } }
  ],

  "protocols": [
    { "id": "cap_protocol", "config": { "targets": ["flight_controller", "gimbal", "camera"] } },
    { "id": "dtp_protocol", "config": { "bandwidth": "high", "realtime": true } }
  ],

  "controlMode": "ego",

  "drivers": [
    {
      "name": "DJI Flight Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/dji-fc",
      "config": { "model": "A3", "firmwareVersion": "^3.0.0" }
    },
    {
      "name": "Gimbal Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/gimbal-generic"
    }
  ],

  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection", "mapping"],
    "constraints": {
      "skillBoundaries": {
        "allowed": ["flight", "camera", "navigation"],
        "restricted": ["financial", "social"]
      }
    }
  },

  "permissions": {
    "inherent": ["device_control", "sensor_read"],
    "persistent": ["flight_plan_execute"],
    "authMethods": ["device_fingerprint"]
  }
}
```

---

## Integración con iFACTS

iFACTS determina qué pruebas de conformidad debe pasar una implementación basándose en el contenido declarado del FayManifest.

Después de la resolución de dependencias, el sistema determina la fase de iFay (Resolved Stage) correspondiente al Manifest. El ejemplo de control de drones anterior declara Hub de controladores, Sensor, protocolos CAP y DTP, correspondiendo a la Fase 2 (Toma de control directo del cliente), y por lo tanto debe pasar todas las pruebas de conformidad para las Fases 1 y 2.

---

## Configuración mínima de componentes por fase

| Fase | Nuevos módulos | Nuevos protocolos |
|------|----------------|-------------------|
| **Fase 1**: Simulación de operaciones humanas | FayID, Gestión de Credenciales, Rastreador en primera persona, Operación simulada, Modelo Ego | Protocolo Faying, Protocolo de Conversación Interactiva |
| **Fase 2**: Toma de control directo del cliente | Sensor, Hub de controladores, Habilidades registradas, Invocación de habilidades, Montón de datos personales | Protocolo CAP, Protocolo DTP |
| **Fase 3**: Interfaz al mundo virtual | Conocimiento externo | Protocolo SSP |
| **Fase 4**: Personificación completa | Autoconciencia, Comportamiento autónomo, Habilidades internas, Conciencia alineada | Protocolo de Telepatía |
| **Fase 5**: Distribución de valor | GMChain, MeriToken | — |

> **Infraestructura transversal** (requerida para todas las fases): Entorno de ejecución FayGer, Perfil iFay, Sistema de permisos, Cumplimiento de seguridad y ética, Sincronización multi-terminal. Estos componentes no pertenecen a ninguna fase específica pero son requeridos en cada fase.

---

### Documentos relacionados

- [iFACTS](./14-iFACTS) — Pruebas de conformidad
- [Hoja de ruta](./4-Hoja-de-ruta) — Configuración por fases
- [Hub de controladores](./12.1-Hub-de-controladores) — Configuración de controladores
