# 4. Roadmap: 5 Phases

We are still in the "Human Operation Era" — hardware and software rely on humans interacting through interfaces to drive devices and execute functions.

![](./illustration/human-operation-era.png)

Currently, the relationship between humans, devices, and service providers is as shown in the diagram above.

<br>

---

## 1️⃣ Phase 1: Simulating Human Operations
On top of the existing hardware and software architecture, we let iFay simulate human UI operations.

![Phase 1 Concept](./illustration/phase1-concept.png)

To achieve this, we need to accomplish at least 2 things:
1. Credential Delegation: Human users must be able to securely authorize iFay to use their [credentials](./2-Definition-and-Concept#general-concept-clarifications) (accounts, passwords, certificates, access permissions, contracts, etc.) through a controllable and auditable delegation mechanism.
2. Interacting with iFay: Primarily through a conversational interface. However, careful design is needed — when tasks involve higher interaction complexity or precision, structured interfaces may be more efficient than pure chat.

<br>

Based on the above thinking, when we release iFay v1.0, it will include the following 5 modules (the orange sections in the diagram below):

![Phase 1: Simulating Human Operations](./illustration/phase1-architecture.png)

### 1. FayID
This is iFay's unique identifier. In fact, both iFay and [coFay](https://github.com/ChainModePilot/coFay/wiki) are assigned unified unique IDs.

The purpose is to ensure that when personal iFays eventually assume meaningful social roles, identity can transition smoothly — just as some individual YouTubers evolve into playing important roles in public discourse and civic education.

Here we address two core problems:
- _**FayID Generation and Management**_: Fays will grow exponentially, eventually exceeding the number of human users. This requires a scalable, user-friendly, easily recognizable ID generation and management mechanism.
- _**Activation State**_: To ensure iFay never operates without the Human Prime's knowledge or intent, we define strict activation rules. No iFay should act autonomously without explicit intent. This is governed by the open-source [Faying Protocol](https://github.com/ChainModePilot/Faying-Protocol/wiki), which specifies how natural persons and iFay securely pair, and under what conditions iFay is authorized to operate in an activated state.

### 2. Credentials Management
"Credentials" here is a broad concept. For natural person users, most of the time, users must hold one or more tickets to have the right to use hardware and software. The following 7 types are collectively called credentials (more types may be added with iteration):
- Identity Identifier (FayID)
- Account / Password
- Certificate
- Authorization
- Access Token
- Smart Contract
- Digital Token ([MeriTokens](https://github.com/ChainModePilot/Global-Merit-Chain/wiki))

Note: Initially, all these tickets come from the Human Prime user. For higher security and more convenient management, all of the Human Prime's credentials will be exchanged for copies corresponding to the original credentials. iFay uses these copies for login and authentication.

Of course, we don't assume iFay cannot own its own credentials that the Human Prime cannot use. Therefore, each credential type indicates whether its original owner is the Human Prime or iFay itself.

For example: When we need to verify the authenticity of personal information provided by someone, we might authorize iFay to directly log into a database to query. To prevent private data leakage, iFay only needs to feed back whether it's true or false.

### 3. First-person Tracer
To enable iFay to work directly with existing software — rather than waiting for every application to be redesigned for AI — iFay must have at least visual and auditory capabilities.

We emphasize visual perception over parsing structured documents (like HTML), because many document elements are imperceptible to humans. Hidden elements, such as SEO keyword stuffing, typically don't add real value to the user experience.

By aligning its sensory perception with the Human Prime, iFay can make judgments and decisions that closely match human intent.

The key challenge is achieving hand-eye coordination for iFay. Visual and auditory perception must go beyond passively processing software feedback — iFay also needs to track changes caused by its own operations.

For example, it must track cursor movement, detect newly exposed areas after window movement, and adapt to dynamic interface changes. This requires tight coupling between first-person perspective tracking and simulated interaction, ensuring iFay perceives and responds to the environment like a human operator.

### 4. Simulated Operation
Here we specifically refer to simulating human interaction with UIs. iFay doesn't just click — it may drag, scroll, perform edge gestures, or multi-finger gestures, depending on the interface components.

The core challenge is that customizing operation sequences for each interface is infeasible. Instead, iFay's simulated interaction must also simulate human exploration of interfaces, using feedback from first-person perspective tracking to determine which operations are feasible or effective. This approach fundamentally differs from traditional RPA implementations, which rely on predefined scripts rather than adaptive, perception-driven exploration.

### 5. Ego Model
We call it **[Ego](https://github.com/ChainModePilot/Ego/wiki)**, emphasizing that it is not a large AGI model. Ego aligns with the profile of a specific individual or role.

Many super-large models pursuing AGI face a key limitation: no matter how extensive their knowledge and skills, they cannot fully satisfy every person's or scenario's unique preferences and context.

Ego provides a baseline paradigm that constrains (but is not limited to) the following dimensions:
- Value orientation
- Interest preferences
- Habits
- Cognitive boundaries
- Skill boundaries
- Permission boundaries
- Working style

It's important to note that embedding the Ego model does not prevent iFay from leveraging external skills or other large models. The decision to include an internal micro-model is based on two considerations:
1. _**Offline Device Control**_: In scenarios where terminal devices are not connected to the internet, the embedded micro-model supports local near-field device control.
2. _**Personality Stability**_: Prevents sudden personality changes in iFay due to large model updates or deliberate tampering, ensuring Ego remains consistent.

<br>

---

## 2️⃣ Phase 2: Direct Client Takeover
While AI simulating UI operations improves efficiency, visual interfaces still have limitations:

- _**Information Loss**_: Limited views and static elements hinder effective communication.
- _**High Learning Cost**_: Inconsistent interfaces across providers force users to learn multiple interaction patterns.
- _**Interface Rigidity**_: Once hardware/software designs a UI, it's fixed for the current version. Users must relearn interfaces when using different devices or applications.
- _**Low Information Transfer Efficiency**_: Intent must first be translated into a visual interface, then fed back to the machine through user operations.
- _**High Development Cost**_: Building functional UIs requires cross-disciplinary coordination (e.g., product managers, UI/UE designers, front-end developers).

![Phase 2 Concept](./illustration/phase2-concept.png)

In contrast, if terminal devices support client protocols (as shown above), iFay can directly control hardware and software. This approach addresses all five issues:
- _**Unlimited Output**_: Information is no longer constrained by UI display limitations.
- _**Intent-Based Interaction**_: Users express intent, iFay translates it into API calls or commands.
- _**Rich Data, Concise Delivery**_: Terminals can output rich structured data, iFay filters and summarizes it into clear essentials.
- _**Direct Transmission**_: No visual rendering needed, enabling more efficient data flow.
- _**No Frontend Needed**_: UI design and development can be minimized or eliminated.

I've defined two protocols applicable to terminals:
- [Control Authority Protocol (CAP)](https://github.com/ChainModePilot/Control-Authority-Protocol/wiki): For inhabiting terminal hardware and specific software, directly calling drivers, local interfaces, and commands, enabling iFay to control terminals.
- [Data Tunnel Protocol (DTP)](https://github.com/ChainModePilot/Data-Tunnel-Protocol/wiki): A bidirectional transmission protocol:
  - _**Terminal → iFay**_: Persistent user data storage and data guardianship.
  - _**iFay → Terminal**_: Data enrichment and personalized processing.

In the diagram below, the blue sections correspond to these two protocols, targeting device functionality and data respectively.

![Phase 2: Direct Client Takeover](./illustration/phase2-architecture.png)

Compared to [Phase 1](./4-Roadmap#1️⃣-phase-1-simulating-human-operations), iFay adds five new internal modules, starting with:

<br>

### Perception → Sensor
The Sensor must be implemented on top of the Control Authority Protocol and Data Tunnel Protocol. It serves as a bridge to terminal device sensors, receiving data streams from the external environment — this is why we call it iFay's nervous system.

Crucially, iFay doesn't need to process all incoming data at all times. The Sensor can dynamically adjust its sensitivity to better match the surrounding context.

Think of the Sensor as a sensitivity regulator. The actual interfaces with the external world are managed by the Device Driver Hub and Personal Data Heap.

<br>

### Skills → Device Driver Hub
To clarify, this is not a single device driver, nor a collection of drivers.

It operates as a driver hub layer, ensuring that as new device drivers are continuously integrated, iFay's internal architecture remains stable without needing modification with each update.

<br>

### Skills → Registered Skill
Registration is a prerequisite for any iFay action.

When a skill is registered to iFay, it means iFay can invoke it at any time. Registration is not just simple record-keeping — it typically serves as a pre-authorization step, ensuring no additional authentication is needed during execution, thereby reducing latency.

Another key benefit is offline resilience: when iFay is offline, it can cache pending actions and execute them asynchronously when connectivity is restored.

<br>

### Thinking → Personal Data Heap
This component is responsible for managing all of iFay's private data in a unified manner. It supports multiple storage formats and locations — for example, some data may reside in iFay's runtime memory, some in Google Drive, and some in a dedicated vector database.

From iFay's internal perspective, it only needs to read from and write to the data heap, without worrying about where or how data is physically stored.

<br>

### Action → Invoke Skill
This is iFay's primary action — essentially, you can think of it as an invocation behavior.

<br>

---

## 3️⃣ Phase 3: iFay as the Interface to the Virtual World

As iFay inhabits the client, the client-server (C/S) architecture evolves into a client-Fay-server (C/F/S) model.
Users no longer need to manually operate clients to access backend services — instead, iFay can directly capture and leverage open services on the internet.

![Phase 3 Concept](./illustration/phase3-concept.png)

To achieve this, services and interfaces that were previously only open to clients should be made available network-wide through a standardized remote protocol.

This remote protocol is the [Skill Sharing Protocol](https://github.com/ChainModePilot/Skill-Sharing-Protocol/wiki) shown in the diagram below.

![Phase 3: iFay as the Interface to the Virtual World](./illustration/phase3-architecture.png)

As shown, iFay controls both the client side (edge devices) and the server side (or cloud services).

The Human Prime only needs to communicate with their own iFay, and iFay then invokes the required services based on the Prime's intent.

Since the interface through which the Human Prime views information is composed and rendered by iFay, it effectively plays the role of a browser.

Since the core motivation for introducing iFay is to make it an intelligent extension beyond the Human Prime, its enhanced capabilities are achieved through registered skills.
In the thinking domain, we introduce the following module:

<br>

### Thinking → External Knowledge

From an implementation perspective, we treat external knowledge bases and models as a skill type, enabling iFay to access external intelligence like consulting a knowledge hub or expert advisor.
Knowledge and information acquired through this skill are managed alongside iFay's personal data, ultimately achieving intelligence that surpasses the Human Prime's own capabilities.

<br>

---

## 4️⃣ Phase 4: iFay + coFay — Full Personification of Software

At this stage, the embodiment of Fay is essentially complete.
However, they still lack the ability to act autonomously like true members of society.
For iFay to operate independently and effectively, 2 key conditions must be met:
- Internal: iFay must develop self-driven motivation — a continuous "action → feedback → re-action" loop.
- External: iFay and coFay must be widely adopted and able to communicate using a common language.
With this foundation, iFay can collaborate with humans, other iFays, or its dedicated coFays to autonomously execute predefined tasks.

![Phase 4 Concept](./illustration/phase4-concept.png)

To achieve this, we need to embed self-driven capabilities in four core modules — perception, action, skills, and thinking.

<br>

### Perception → Self-awareness
A truly living entity doesn't just perceive — it also feels.
Unlike machines, iFay itself cannot have genuine emotions. But by observing its Human Prime and surrounding context, it can infer feelings from perception.
This is the core strategy for building iFay's self-awareness.

<br>

### Action → Self-driven Behavior
Since iFay needs to handle tasks autonomously, it must have its own behavior trigger mechanisms.
These triggers can come from:
- Scheduled tasks
- Self-awareness inference
- Persistent skills, including registered skills and internal skills.

<br>

### Skills → Internal Skill
We introduce the Internal Skill module for three main purposes:
- Establish habits aligned with the Human Prime's personality, including potential restrictions or governance over external skills.
- Provide an introspection mechanism to ensure external knowledge never conflicts with the Human Prime's intent.
- Embed fixed Prime-specific capabilities, such as professional skills and expertise.

<br>

### Thinking → Aligned Consciousness
Essentially, this represents a complete description of the Human Prime's personal profile.
It can be established through three main methods (possibly more):
- Mining data from the Personal Data Heap.
- Real-time adjustment through self-awareness.
- Manual definition by the Human Prime.

<br>

![Phase 4: iFay + coFay — Full Personification of Software](./illustration/phase4-architecture.png)

However, this alone is not enough for iFay to integrate into social relationships.
For this, we need to equip iFay with communication capabilities, involving two core protocols:
- [Telepathy Protocol](https://github.com/ChainModePilot/Telepathy-Protocol/wiki) — A Fay-friendly semantic communication protocol that removes the UI translation layer, allowing meaning and intent to be transmitted directly between iFay and coFay. It uses agreed-upon vector-encoded tokens instead of structured text.
- [Interactive Conversation Protocol](https://github.com/ChainModePilot/Interactive-Conversation-Protocol/wiki) — A human UI-friendly protocol that modularizes and multimodalizes semantic content, enabling client interfaces to reconstruct readable, user-friendly message displays.

<br>

---

## 5️⃣ Phase 5: Fay Reshapes Labor Structure and Value Distribution

Ultimately, our goal is to build an ecosystem with strong social attributes, rather than treating AI as a more advanced tool.
This new social form will inevitably differ from human society as we know it today.
We can foresee at least 5 fundamental shifts:
1. _**Human Labor Exit**_ — Programmatic work will be entirely taken over by AI and robots, driving human resource costs toward zero.
2. _**Knowledge Flattening**_ — Professional knowledge and expertise will be equalized by AI, making supply chains extremely flat.
3. _**Universal Survival Guarantee**_ — Everyone will have access to basic living resources, eliminating the need to work for survival.
4. _**New Value Creation**_ — Human participation will focus on meaning creation, human-centered craftsmanship, and the AI + robot production ecosystem.
5. _**New Social Stratification**_ — Ownership of autonomous production resources will become the new driver of wealth and class differentiation.

This will fundamentally reshape the economic ecosystem built on ownership of material resources (i.e., means of production).
From an economic perspective, 2 major shifts will occur:
- _**Minimized Human Participation in the Real Economy**_ — Very few people will directly participate in traditional production activities.
- _**Dramatic Increase in Unit Value of Human Labor**_ — Unless human work is highly valued, humans will completely withdraw from physical labor.

When most people are immersed in virtual work, traditional value metrics — such as working hours, monetary income, or physical quantities of goods — become inadequate.
Therefore, measuring social value requires a consensus mechanism, similar to how auctions determine the value of art or stocks. Auctions are just one way to establish consensus.

To maintain this consensus, a dedicated platform is needed. Currently, blockchain is a suitable choice, with years of accumulated experience.

We quantify social contributions in a unified unit (μ, Merit Unit) and issue corresponding digital tokens (MeriToken) on the blockchain, forming what we call the [Global Merit Chain](https://github.com/ChainModePilot/Global-Merit-Chain).

In the future, acquiring MeriTokens will not depend on consuming computing power to complete blockchain technical work, but on creating social value.

![Phase 5 Concept](./illustration/phase5-concept.png)
