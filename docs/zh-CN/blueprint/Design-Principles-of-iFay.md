
<img width="100%" alt="iFay 标题横幅" src="./illustration/ifay-title-banner.png"/>

iFay（Individual Fay）是与自然人深度绑定的 AI 数字化身。它不是工具，而是你的人格延伸——融合你的性格、记忆、偏好与数字能力，代替你执行机械性、重复性和危险性劳动，放大你的社会价值。iFay 采用 CPE+M 框架（Context 上下文、Protocol 协议、Environment 环境、Merit 贡献度量），由社交层、交互层、认知层和自我层四层架构组成，覆盖从模拟人类操作到重塑劳动结构与价值分配的五个演进阶段。

---

## 设计原则

iFay 的设计遵循五项核心原则，它们贯穿整个系统的架构与实现：

| # | 原则 | 一句话说明 |
|---|------|-----------|
| 1 | **生态友好的渐进式采纳** | 生态伙伴无需实现完整 iFay 即可发布产品——一个只控制无人机的 iFay，只需满足所需部件子集即可上线。 |
| 2 | **声明式极简组装** | 通过一个 FayManifest 声明文件定义所需部件、协议和配置，像写 package.json 一样组装 iFay。 |
| 3 | **灵活的部件组合** | 部件松耦合、可混搭，不同厂商的实现只要符合接口契约即可自由组合。 |
| 4 | **人格化而非工具化** | iFay 不是 Agent——每个 iFay 都有独特的个性、记忆和偏好，是宿主的增强版，甚至可在宿主过世后延续人格。 |
| 5 | **场景驱动的直觉设计** | 每个功能模块都能用一个具体的生活场景来解释，让读者直观想象有了 iFay 后的生活。 |

---

## 目录

1. [定义与概念](./Definition-and-Concept)

    提供 iFay 的定义和结构概述，分析 iFay 与当前 Agent 概念的根本区别，以及其运行特征背后的原理。

---

2. [iFay 应用场景](./iFay-Application-Scenarios)

    从零开始实际使用 iFay 的完整过程：如何注入你的个性、为 iFay 添加技能、与 iFay 交互、iFay 如何社交，以及安全性和产业生态的全景描绘。

    - [将本体特征注入 iFay](./iFay-Application-Scenarios#将本体特征注入-ifay)
    - [为 iFay 补充外部能力](./iFay-Application-Scenarios#为-ifay-补充外部能力)
    - [人与 iFay 的交互方式](./iFay-Application-Scenarios#人与-ifay-的交互方式)
        - [如何激活 iFay](./iFay-Application-Scenarios#如何激活-ifay)
        - [iFay 的自主意识](./iFay-Application-Scenarios#ifay-的自主意识)
        - [如何关闭 iFay](./iFay-Application-Scenarios#如何关闭-ifay)
    - [iFay 的社交功能](./iFay-Application-Scenarios#ifay-的社交功能)
    - [安全性](./iFay-Application-Scenarios#安全性)
    - [塑造 AI 产业生态](./iFay-Application-Scenarios#塑造-ai-产业生态)

---

3. [从人类到 iFay](./Human-to-iFay)

    iFay 附属于特定自然人，因此需要将宿主的特征从三个维度注入 iFay：性格塑造 Ego 模型、数据填充个人数据堆、权限建立凭证委托。

    - [宿主性格](./Human-to-iFay#宿主性格)
    - [宿主数据](./Human-to-iFay#宿主数据)
    - [宿主权限](./Human-to-iFay#宿主权限)

---

4. [iFay 画像](./iFay-Profile)

    iFay Profile 是 iFay 的完整"身份证"——一个语义可解释的六维属性表，用于人类识别 iFay、系统识别 iFay、以及 Fay 之间相互识别。

    - [iFay 身份](./iFay-Profile#ifay-身份)
    - [Ego 模型](./iFay-Profile#ego-模型)
    - [Faying 思维](./iFay-Profile#faying-思维)
        1. [内容（Content）](./iFay-Profile#内容)
        2. [数据（Data）](./iFay-Profile#数据)
        3. [知识库（Knowledge Base）](./iFay-Profile#知识库)
        4. [信息流（Info Feed）](./iFay-Profile#信息流)
    - [Faying 技能](./iFay-Profile#faying-技能)
        1. [API](./iFay-Profile#api)
        2. [工作流（Workflow）](./iFay-Profile#工作流)
        3. [Bot](./iFay-Profile#bot)
        4. [Agent](./iFay-Profile#agent)
        5. [APP](./iFay-Profile#app)
        6. [微服务（Microservice）](./iFay-Profile#微服务)
    - [Faying 硬件](./iFay-Profile#faying-硬件)
        1. [设备（Device）](./iFay-Profile#设备)
        2. [存储（Storage）](./iFay-Profile#存储)
        3. [算力（Computing）](./iFay-Profile#算力)
    - [Faying 权限](./iFay-Profile#faying-权限)
        1. [SSO](./iFay-Profile#sso)
        2. [OAuth](./iFay-Profile#oauth)
        3. [指纹（Fingerprint）](./iFay-Profile#指纹)

---

5. [FayManifest 声明式组装](./FayManifest)

    FayManifest 是 iFay 的"package.json"——开发者只需在一个 JSON 声明文件中列出所需的部件、协议、控制模式和驱动配置，FayGer 运行时自动解析依赖并组装 iFay 实例。一个周末就能从零搭建一个专用 iFay。

---

6. [iFACTS 合规性验证](./iFACTS)

    iFACTS（iFay Architecture Conformance Test Suite）是标准化合规性测试套件，覆盖协议交互、模块接口、安全行为等关键规范点。厂商实现必须通过 iFACTS 测试才能声称"iFay 可用"，测试分为 L1 单部件合规、L2 接口合规、L3 集成合规、L4 行为合规四个层级。

---

7. [监护与人格延续](./Guardianship)

    iFay 是人格的数字载体。当宿主无法管理 iFay 时，监护人可通过助记词或预指定身份认证接管管理权；当宿主过世后，iFay 可在数字墓园沙箱中以独立身份继续存在，人格不灭。

---

8. 案例

    我们将提供一系列案例来演示 iFay 如何被创建以及系统如何与 iFay 对接。
