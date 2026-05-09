# 13. FayManifest 声明式组装

FayManifest 是 iFay 的"package.json"。开发者只需在一个 JSON 声明文件中列出所需的部件、协议、控制模式和驱动配置，FayGer 运行时自动解析依赖并组装 iFay 实例。你不需要理解整个 iFay 系统的复杂性——声明你需要什么，系统帮你补齐剩下的。

---

## 为什么需要 FayManifest

iFay 的设计原则之一是**声明式极简组装 + 渐进式采纳**。

**问题**：从零构建一个完整的 iFay 是复杂的——12 个核心模块、6 个协议、权限体系、安全合规、多终端同步……如果每个开发者都必须理解并实现所有这些，iFay 生态将永远无法起步。

**解决方案**：开发者只需声明业务所需的部件子集，系统自动补充必需的基础设施依赖。一个只用于控制无人机的 iFay，不需要实现完整的社交层和认知层——声明设备驱动中枢、传感器和 CAP 协议即可，其余由系统处理。

---

## FayManifest 文件结构

FayManifest 采用 JSON 格式，包含以下字段：

| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `name` | string | ✅ | iFay 实现的名称 |
| `version` | string | ✅ | 版本号 |
| `description` | string | ✅ | 功能描述 |
| `vendor` | string | ✅ | 开发商/厂商名称 |
| `modules` | array | ✅ | 所需模块列表，每个模块可指定版本约束（`version`）、厂商实现（`provider`）和配置（`config`） |
| `protocols` | array | ✅ | 所需协议列表，每个协议可指定版本和配置 |
| `controlMode` | string | ✅ | 控制模式：`command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | 驱动程序配置，指定驱动名称、类型、驱动包标识和配置 |
| `ego` | object | ❌ | Ego 模型配置，指定模型来源、适用场景标签和约束参数 |
| `permissions` | object | ❌ | 权限配置，声明与生俱来的权限、持久权限和支持的鉴权方式 |

---

## 控制模式

FayManifest 中的 `controlMode` 字段决定了 iFay 的行为驱动方式，三选一：

| 模式 | 名称 | 说明 |
|------|------|------|
| `command` | **指令控制** | 人类原型明确驱动每一个动作。iFay 不会自主行动，每次操作都需要人类原型的明确指令。适用于高风险场景或初始信任建立阶段。 |
| `ego` | **Ego 控制** | Ego 模型在约束范围内自主决策。iFay 可以根据人类原型的个性和偏好自主判断和行动，但行为边界由 Ego 模型约束。适用于日常助手场景。 |
| `autonomous` | **自主控制** | 完全自驱行为。iFay 基于自我感知、自驱行为和内部技能自主运行，形成持续的"动作→反馈→再动作"循环。适用于高度信任的长期协作场景。 |

---

## 自动依赖补充

FayManifest 的核心设计：开发者声明业务部件，系统自动补充基础设施。

以下基础设施在所有 iFay 实现中都是必需的，无论开发者是否显式声明，系统都会自动添加：

- **FayID**（身份标识）
- **FayGer 运行时**（运行时容器）
- **iFay Profile**（统一数据模型）
- **权限体系**（权限管理）
- **安全与伦理合规**（行为约束）
- **多终端同步**（状态同步）
- **Faying 协议**（安全配对，所有 iFay 必需）

此外，如果 Manifest 中声明了 `ego` 配置，系统会自动添加 `ego_model` 模块。

---

## 完整示例：无人机控制 iFay

以下是一个用于无人机控制的 iFay 的 FayManifest 声明：

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "用于无人机控制的 iFay 实现",
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


### 逐段解读

**元信息**（`name`、`version`、`description`、`vendor`）：标识这个 iFay 实现的基本信息。`vendor` 为 "DroneAI Corp"，表明这是一个第三方厂商的实现。

**模块**（`modules`）：声明了四个业务模块——设备驱动中枢用于管理无人机硬件驱动，传感器模块配置了 GPS、IMU、摄像头和激光雷达四种传感器类型，技能调用和注册技能模块预加载了飞行控制和避障两个核心技能。

**协议**（`protocols`）：声明了 CAP 协议（控制飞行控制器、云台和摄像头）和 DTP 协议（高带宽实时数据传输，用于传感器数据流）。

**控制模式**（`controlMode`）：选择 `ego` 模式，意味着 Ego 模型在飞行、拍摄和导航范围内自主决策，但不会涉及金融或社交行为。

**驱动程序**（`drivers`）：配置了 DJI A3 飞行控制器驱动和通用云台控制器驱动，指定了具体的驱动包和固件版本要求。

**Ego 配置**（`ego`）：使用无人机飞行员 Ego 模型 v1，适用于航拍、巡检和测绘场景，技能边界明确限制在飞行、摄像和导航领域。

**权限**（`permissions`）：设备控制和传感器读取是与生俱来的权限，飞行计划执行是持久权限，使用设备指纹作为鉴权方式。

### 系统自动补充

上述 Manifest 只声明了 4 个模块和 2 个协议，但系统会自动补充以下基础设施：

| 自动补充的部件 | 原因 |
|----------------|------|
| FayID | 所有 iFay 必需的身份标识 |
| FayGer 运行时 | 所有 iFay 必需的运行时容器 |
| iFay Profile | 所有 iFay 必需的统一数据模型 |
| 权限体系 | 所有 iFay 必需的权限管理 |
| 安全与伦理合规 | 所有 iFay 必需的行为约束 |
| 多终端同步 | 所有 iFay 必需的状态同步 |
| Ego 模型 | 因声明了 `ego` 配置而自动添加 |
| Faying 协议 | 所有 iFay 必需的安全配对协议 |

最终，这个无人机控制 iFay 实际包含 12 个部件和 3 个协议——但开发者只需要关心其中与无人机业务相关的部分。

---

## 与 iFACTS 的集成

iFACTS（iFay Architecture Conformance Test Suite）根据 FayManifest 的声明内容确定该实现应通过哪些合规性测试。

依赖解析完成后，系统会确定该 Manifest 对应的 iFay 阶段（Resolved Stage）。上述无人机控制示例声明了设备驱动中枢、传感器、CAP 和 DTP 协议，对应阶段 2（直接接管客户端），因此需要通过阶段 1 和阶段 2 的所有合规性测试。

测试范围包括：
- **L1 单部件合规**：验证每个声明的模块和协议是否符合独立规范
- **L2 接口合规**：验证模块间的接口对接是否正确
- **L3 集成合规**：验证端到端流程的完整性
- **L4 行为合规**：验证系统级行为约束（如 Ego 个性稳定性）

---

## 阶段性最小部件配置

每个阶段有其最小部件配置（Minimum Component Set）。开发者声称支持某个阶段时，必须包含该阶段及所有前置阶段的部件：

| 阶段 | 新增模块 | 新增协议 |
|------|----------|----------|
| **阶段 1**：模拟人类操作 | FayID、凭证管理、第一人称追踪器、模拟操作、Ego 模型 | Faying 协议、交互对话协议 |
| **阶段 2**：直接接管客户端 | 传感器、设备驱动中枢、注册技能、技能调用、个人数据堆 | CAP 协议、DTP 协议 |
| **阶段 3**：虚拟世界接口 | 外部知识 | SSP 协议 |
| **阶段 4**：全面拟人化 | 自我感知、自驱行为、内部技能、对齐意识 | 心灵感应协议 |
| **阶段 5**：价值分配 | GMChain、MeriToken | — |

> **跨阶段基础设施**（所有阶段必需）：FayGer 运行时、iFay Profile、权限体系、安全与伦理合规、多终端同步。这些部件不属于任何特定阶段，但在每个阶段都是必需的。

---

### 相关文档

- [iFACTS](./14-iFACTS合规性验证) — 合规性验证
- [路线图](./4-路线图) — 阶段配置
- [设备驱动中枢](./12-认知层-技能#121-设备驱动中枢) — 驱动配置
