# 13. FayManifest Declarative Assembly

FayManifest is iFay's "package.json." Developers simply list the required components, protocols, control modes, and driver configurations in a single JSON declaration file, and the FayGer runtime automatically resolves dependencies and assembles the iFay instance. You don't need to understand the full complexity of the iFay system — declare what you need, and the system fills in the rest.

---

## Why FayManifest Is Needed

One of iFay's design principles is **declarative minimal assembly + progressive adoption**.

**Problem**: Building a complete iFay from scratch is complex — 12 core modules, 6 protocols, permission systems, security compliance, multi-terminal synchronization… If every developer had to understand and implement all of these, the iFay ecosystem would never get off the ground.

**Solution**: Developers only need to declare the subset of components their business requires, and the system automatically supplements the necessary infrastructure dependencies. An iFay used solely for drone control doesn't need to implement the full Social Layer and Cognitive Layer — just declare the Device Driver Hub, Sensor, and CAP Protocol, and the system handles the rest.

---

## FayManifest File Structure

FayManifest uses JSON format and contains the following fields:

| Field | Type | Required | Description |
|------|------|------|------|
| `name` | string | ✅ | Name of the iFay implementation |
| `version` | string | ✅ | Version number |
| `description` | string | ✅ | Functional description |
| `vendor` | string | ✅ | Developer/vendor name |
| `modules` | array | ✅ | List of required modules; each module can specify version constraints (`version`), vendor implementation (`provider`), and configuration (`config`) |
| `protocols` | array | ✅ | List of required protocols; each protocol can specify version and configuration |
| `controlMode` | string | ✅ | Control mode: `command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | Driver configurations specifying driver name, type, driver package identifier, and configuration |
| `ego` | object | ❌ | Ego model configuration specifying model source, applicable scenario tags, and constraint parameters |
| `permissions` | object | ❌ | Permission configuration declaring inherent permissions, persistent permissions, and supported authentication methods |

---

## Control Modes

The `controlMode` field in FayManifest determines iFay's behavior-driving approach — choose one of three:

| Mode | Name | Description |
|------|------|------|
| `command` | **Command Control** | Human Prime explicitly drives every action. iFay won't act autonomously; every operation requires the Human Prime's explicit command. Suitable for high-risk scenarios or initial trust-building phases. |
| `ego` | **Ego Control** | The Ego Model makes autonomous decisions within constrained boundaries. iFay can judge and act autonomously based on the Human Prime's personality and preferences, but behavioral boundaries are constrained by the Ego Model. Suitable for daily assistant scenarios. |
| `autonomous` | **Autonomous Control** | Fully self-driven behavior. iFay operates autonomously based on Self-awareness, Self-driven Behavior, and Internal Skill, forming a continuous "action → feedback → re-action" loop. Suitable for high-trust long-term collaboration scenarios. |

---

## Automatic Dependency Supplementation

FayManifest's core design: developers declare business components, the system automatically supplements infrastructure.

The following infrastructure is required in all iFay implementations — whether or not developers explicitly declare them, the system automatically adds:

- **FayID** (Identity)
- **FayGer Runtime** (Runtime container)
- **iFay Profile** (Unified data model)
- **Permission System** (Permission management)
- **Security & Ethics Compliance** (Behavioral constraints)
- **Multi-terminal Synchronization** (State synchronization)
- **Faying Protocol** (Secure pairing, required for all iFay)

Additionally, if the Manifest declares an `ego` configuration, the system automatically adds the `ego_model` module.

---

## Complete Example: Drone Control iFay

Here is a FayManifest declaration for a drone control iFay:

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "iFay implementation for drone control",
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

### Section-by-Section Explanation

**Metadata** (`name`, `version`, `description`, `vendor`): Identifies the basic information of this iFay implementation. `vendor` is "DroneAI Corp," indicating this is a third-party vendor implementation.

**Modules** (`modules`): Declares four business modules — Device Driver Hub for managing drone hardware drivers, Sensor module configured with GPS, IMU, camera, and LiDAR sensor types, Invoke Skill and Registered Skill modules with flight control and obstacle avoidance as preloaded core skills.

**Protocols** (`protocols`): Declares CAP Protocol (controlling flight controller, gimbal, and camera) and DTP Protocol (high-bandwidth real-time data transmission for sensor data streams).

**Control Mode** (`controlMode`): Selects `ego` mode, meaning the Ego Model makes autonomous decisions within flight, photography, and navigation scope, but won't engage in financial or social behaviors.

**Drivers** (`drivers`): Configures DJI A3 flight controller driver and generic gimbal controller driver, specifying concrete driver packages and firmware version requirements.

**Ego Configuration** (`ego`): Uses drone pilot Ego Model v1, applicable to aerial photography, inspection, and mapping scenarios, with skill boundaries explicitly limited to flight, camera, and navigation domains.

**Permissions** (`permissions`): Device control and sensor read are inherent permissions, flight plan execution is a persistent permission, and device fingerprint is used as the authentication method.

### System Auto-Supplementation

The above Manifest only declares 4 modules and 2 protocols, but the system automatically supplements the following infrastructure:

| Auto-supplemented Component | Reason |
|----------------|------|
| FayID | Required identity for all iFay |
| FayGer Runtime | Required runtime container for all iFay |
| iFay Profile | Required unified data model for all iFay |
| Permission System | Required permission management for all iFay |
| Security & Ethics Compliance | Required behavioral constraints for all iFay |
| Multi-terminal Synchronization | Required state synchronization for all iFay |
| Ego Model | Automatically added because `ego` configuration was declared |
| Faying Protocol | Required secure pairing protocol for all iFay |

Ultimately, this drone control iFay actually contains 12 components and 3 protocols — but the developer only needs to care about the parts related to drone business.

---

## Integration with iFACTS

iFACTS (iFay Architecture Conformance Test Suite) determines which conformance tests an implementation should pass based on the FayManifest's declared content.

After dependency resolution, the system determines the iFay phase (Resolved Stage) corresponding to the Manifest. The drone control example above declares Device Driver Hub, Sensor, CAP and DTP protocols, corresponding to Phase 2 (Direct Client Takeover), and therefore must pass all conformance tests for Phase 1 and Phase 2.

Test scope includes:
- **L1 Single Component Conformance**: Validates whether each declared module and protocol conforms to its independent specification
- **L2 Interface Conformance**: Validates whether inter-module interface integration is correct
- **L3 Integration Conformance**: Validates end-to-end process completeness
- **L4 Behavioral Conformance**: Validates system-level behavioral constraints (e.g., Ego personality stability)

---

## Phase-wise Minimum Component Configuration

Each phase has its Minimum Component Set. When developers claim support for a phase, they must include components from that phase and all preceding phases:

| Phase | New Modules | New Protocols |
|------|----------|----------|
| **Phase 1**: Simulated Human Operation | FayID, Credential Management, First-person Tracer, Simulated Operation, Ego Model | Faying Protocol, Interactive Dialogue Protocol |
| **Phase 2**: Direct Client Takeover | Sensor, Device Driver Hub, Registered Skill, Invoke Skill, Personal Data Heap | CAP Protocol, DTP Protocol |
| **Phase 3**: Virtual World Interface | External Knowledge | SSP Protocol |
| **Phase 4**: Full Anthropomorphization | Self-awareness, Self-driven Behavior, Internal Skill, Aligned Consciousness | Telepathy Protocol |
| **Phase 5**: Value Distribution | GMChain, MeriToken | — |

> **Cross-phase Infrastructure** (required for all phases): FayGer Runtime, iFay Profile, Permission System, Security & Ethics Compliance, Multi-terminal Synchronization. These components don't belong to any specific phase but are required in every phase.

---

### Related Documents

- [iFACTS](./14-iFACTS) — Conformance testing
- [Roadmap](./04-Roadmap) — Phase configuration
- [Device Driver Hub](./12.1-Device-Driver-Hub) — Driver configuration
