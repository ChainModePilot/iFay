# 2. Definition and Concept

## Product-Specific Terms

### iFay
Individual Fay. A digital avatar attached to a natural person (called the **Human Prime**, or **Prime** for short), committed to aligning with the natural person (Human Prime) it is attached to in terms of values, personality, and habits. iFay is an Instantiation of the Human Prime's personality, fusing the Prime's personality traits with digital capabilities, aiming to take over the Prime's mechanical, repetitive, dangerous labor and tedious auxiliary work, enhance the Prime's safety, health, and quality of life, and amplify the Prime's social value.

### coFay
Common Fay, a digital avatar that assumes public roles, roughly equivalent to the current concept of an Agent. It possesses general knowledge and skills in a specific domain and can serve multiple people through conversation. coFay is an independent project; the iFay specification only references it when necessary.

### Fay
A collective term for iFay and coFay, a general term for personified AI agents. It may become an important node in new types of social relationships.

### FayID
A globally unique persistent identifier assigned to each Fay, human-readable and machine-readable. FayID uses a unified identifier generation and management mechanism for both iFay and coFay, supporting identifier capacity exceeding the global population scale.

### FayGer
A container that provides a virtual runtime environment for Fay (iFay and coFay), similar to Docker. This ensures that Fay can Inhabit different hardware and software cross-platform, imbuing them with the Human Prime's personal will. FayGer provides cross-language build tools and cross-platform runtime containers, allowing any Fay (regardless of development language) to be packaged and executed.

### Ego Model
iFay's personalized micro-model, aligned with a specific individual's profile. Ego is a pluggable, switchable edge small model that can be loaded onto any terminal device to give that device the Human Prime's personality. Ego constrains iFay to align with the Prime across dimensions such as value orientation, interest preferences, habits, cognitive boundaries, skill boundaries, permission boundaries, and working style. It operates independently of external large models, ensuring personality stability. It supports multi-version management and personality switching to accommodate the Prime's multi-faceted personality needs across different scenarios.

> ⚠️ **Ethics Constraint**: Ego version switching must follow the principle of transparency. All Ego versions must share the same set of core values; differences are limited to expression style and interaction preferences. When switching, the currently active Ego version identifier must be annotated in the interaction metadata to ensure auditability.

### iFay Profile
iFay's unified data model, a semantically interpretable attribute table. Used for humans and systems to identify iFay, as well as for Fays to identify each other — it is iFay's complete "identity card." It contains six dimensions: iFay Identity (FayID + metadata), Ego Model (current active Ego version reference), Faying Thinking, Faying Skills, Faying Hardware, Faying Permissions. The Human Prime profile (Aligned Consciousness) is a subset and input source of the Profile.

### FayManifest
iFay's declarative assembly configuration file, similar to package.json. It declares the components, protocols, control modes (command control / Ego control / autonomous control), and configurations required for an iFay implementation. Developers only need to declare "what is needed" rather than "how to implement it." It supports minimal declarations — declaring just a subset of components is enough to go live, and the system automatically supplements required infrastructure dependencies.

### GMChain
**Global Merit Chain (GMC)**, the iFay ecosystem's social contribution ledger — a blockchain infrastructure that establishes reputation and voice by recording and measuring identifiable social contributions. GMChain spans all levels of the CPE+M framework, providing unified contribution tracking and incentive mechanisms for humans, iFay, coFay, and service providers. Unlike most blockchain projects, GMChain relies entirely on the recognition of social value to accumulate points, rather than consuming computing power to complete computational tasks. GMChain does not accept monetary injection, and MeriToken is not exchangeable with fiat currency. It belongs to the long-term vision component of Roadmap Phase 5, but interface definitions need to be reserved in early phases.

### MeriToken
**MeriToken**, the unit of social contribution measurement on GMChain. MeriToken is not currency — it is a quantified credential for reputation, voice, and collaboration incentives. Acquisition is based on creating social value (such as completing collaborative tasks, providing API services, contributing computing power, etc.), rather than consuming computing power to complete blockchain technical work. The MeriToken Ledger records each participant's cumulative contributions, reputation score, and voice weight.

### μ (MU)
Merit Unit, the unit of measurement for MeriToken.

### iFACTS
iFay Architecture Conformance Test Suite, a standardized conformance test suite. It covers key specification points including protocol interactions, module interfaces, and security behaviors, comprising four test levels: L1 Single Component Conformance, L2 Interface Conformance, L3 Integration Conformance, L4 Behavioral Conformance. Vendor implementations must pass iFACTS tests to claim their product is "iFay Ready."

### iFay Ready
The certification standard that application products must meet to be operated by iFay, divided into three tiers:
- **Bronze**: Supports iFay operating the application through simulated operations (First-person Tracer + Simulated Operation)
- **Silver**: Supports iFay directly controlling the application via CAP protocol, supports DTP protocol data exchange
- **Gold**: Supports iFay sharing skills via SSP protocol, supports full C/F/S architecture integration

### Guardian
A natural person designated to take over iFay management rights when the Human Prime passes away or is unable to manage iFay. Note: the term "heir" is deliberately not used. The guardian completes identity verification through mnemonic phrase activation or identity authentication methods pre-specified by the Prime.

### Guardianship
The process and state of the Human Prime transferring iFay management rights to a guardian. After guardianship transfer is complete, iFay binds to the new guardian and updates the Faying protocol pairing relationship.

### Digital Cemetery
A dedicated sandbox environment where iFay continues to operate as an independent identity after the Human Prime passes away. The Digital Cemetery restricts iFay's behavioral scope, preventing iFay from continuing to execute tasks preset by the Prime that could cause confusion and loss, ensuring safety and isolation.

***

## General Concept Clarifications

### Context
The external environment in which Fay operates, including communication targets, interaction modes, conveyed messages, the meaning expressed by messages, controllable hardware and software, callable resources and skills, etc.

### Protocol
Includes annotation definitions for data storage, message bodies, parameters, and interface structures, as well as interaction flow conventions for specific purposes.

### Credentials
A broad concept referring to any digital identifier used to uniquely identify people, things, or objects, which cannot be tampered with or denied. Includes FayID, account passwords, certificates, authorizations, access tokens, smart contracts, and digital tokens (MeriToken).

### Human Prime
The natural person whose personality is replicated by iFay. iFay is deeply bound to the Human Prime, Instantiating the Prime's personality traits and fusing them with digital capabilities.

### Instantiate
The process of generating an iFay aligned with the Human Prime. Instantiation is not a simple data copy, but rather the process of structurally injecting the Human Prime's personality, data, and permissions into iFay.

### Inhabit
The process of injecting iFay into a terminal hardware device or software application so that iFay can control that terminal. After Inhabiting, the terminal becomes iFay's "limb," and iFay can directly control the terminal's hardware and software functions via the CAP protocol.

### Host
The terminal hardware or software application that is Inhabited and controlled by iFay. Note: Host refers to the terminal device or application, not the Human Prime.

### Faying
The process and state of iFay establishing a connection with the Human Prime or a terminal, similar to Bluetooth pairing. When iFay is in a Faying state with the Prime, iFay remains activated. Faying must follow the secure pairing conditions specified by the Faying Protocol, ensuring iFay is only authorized to run under the Prime's explicit intent.

### Separating
The process of iFay disconnecting from the Human Prime and entering hibernation. When iFay is in a Separating state with the Prime, iFay switches to hibernation mode, saves a current state snapshot, and completes the separation.

***

## Module Names

iFay adopts a four-layer architecture comprising 12 core modules:

### Social Layer

| Module | Description |
|--------|-------------|
| **Credentials Management** | Manages seven credential types (FayID, account passwords, certificates, authorizations, access tokens, smart contracts, digital tokens), supporting secure delegation and copy mechanisms for Human Prime credentials |

### Interaction Layer — Perception

| Module | Description |
|--------|-------------|
| **First-person Tracer** | Simulates the Human Prime's first-person perspective, capturing visual and auditory information on the screen or interface, prioritizing visual perception over parsing structured documents |
| **Sensor** | iFay's generalized nervous system, bridging terminal device sensors based on CAP and DTP protocols, supporting dynamic sensitivity adjustment |
| **Self-awareness** | A module that monitors the Human Prime's reactions inward to infer intent, similar to a skilled assistant's ability to read the boss's facial expressions |

### Interaction Layer — Action

| Module | Description |
|--------|-------------|
| **Simulated Operation** | Simulates human UI interaction operations (clicking, dragging, scrolling, gestures, etc.), adaptively exploring interfaces through First-person Tracer feedback |
| **Invoke Skill** | An action module that directly triggers registered skills or executes specific tasks, similar to function calls or API calls |
| **Self-driven Behavior** | An autonomously triggered behavior module supporting three trigger sources: scheduled tasks, self-awareness inference, and persistent skills, forming an "action → feedback → re-action" loop |

### Cognition Layer — Thinking

| Module | Description |
|--------|-------------|
| **Personal Data Heap** | Unified management of all iFay private data, supporting multiple storage formats and locations, providing a unified read/write interface to internal modules |
| **External Knowledge** | An access module for external knowledge bases and models, integrating external intelligence as a skill type, accessing open services via the SSP protocol |
| **Aligned Consciousness** | A complete description of the Human Prime's personal profile, supporting establishment and updates through three methods: data mining, real-time adjustment via self-awareness, and manual definition by the Prime |

### Cognition Layer — Skills

| Module | Description |
|--------|-------------|
| **Device Driver Hub** | The hub layer for device drivers, integrating new drivers through standardized interfaces, ensuring internal architecture stability when new drivers are integrated |
| **Registered Skill** | Skills that iFay has mastered or gained the ability to use, supporting six skill types (API, Workflow, Bot, Agent, APP, Microservice) |
| **Internal Skill** | An inherent capability module aligned with the Human Prime's personality, providing introspection mechanisms to ensure external knowledge does not conflict with the Prime's intent |

### Ego Layer

| Module | Description |
|--------|-------------|
| **Ego Model** | iFay's personalized micro-model, a pluggable, switchable edge small model that operates independently of external large models, ensuring personality stability |

***

## Protocol Names

The iFay protocol system includes six core protocols:

| Protocol | Description |
|----------|-------------|
| **Faying Protocol** | A protocol specifying the conditions for secure pairing and activation between a natural person and iFay, ensuring iFay is only authorized to run under the Human Prime's explicit intent |
| **Interactive Conversation Protocol** | A modular multimodal semantic protocol for human UIs, modularizing and multimodalizing semantic content so that clients can reconstruct readable, user-friendly message displays |
| **Telepathy Protocol** | A semantic communication protocol between Fays that removes the UI translation layer (i.e., UI-free semantic vector direct communication, also known as Semantic Direct Protocol), allowing meaning and intent to be transmitted directly between Fays, using agreed-upon vector-encoded tokens instead of structured text |
| **Control Authority Protocol (CAP)** | Used for iFay to take over terminal hardware and specific software, directly calling drivers, local interfaces, and commands |
| **Data Tunnel Protocol (DTP)** | A bidirectional transmission protocol between terminals and iFay. Terminal→iFay direction supports persistent user data storage and data guardianship; iFay→Terminal direction supports data enrichment and personalized processing |
| **Skill Sharing Protocol (SSP)** | Opens services and interfaces that were previously only available to clients to the entire network through a standardized remote protocol |

***

## iFay Profile Dimensions

iFay Profile contains six dimensions, of which four Faying dimensions describe iFay's capabilities and resources:

### iFay Identity
FayID + metadata, iFay's foundational identity marker.

### Ego Model
Reference to the currently active Ego version; only one version is active at any given moment.

### Faying Thinking
iFay's cognitive resource dimension, containing four sub-types:
- **Content** — Structured and unstructured content assets
- **Data** — The Human Prime's personal data
- **Knowledge Base** — Organized knowledge systems
- **Info Feed** — Real-time information subscriptions and push notifications

### Faying Skills
iFay's capability dimension, containing six skill types:
- **API** — Standardized interface calls
- **Workflow** — Workflow orchestration
- **Bot** — Conversational bots
- **Agent** — Intelligent agents
- **APP** — Applications
- **Microservice** — Microservices

### Faying Hardware
iFay's hardware dimension — iFay's "limbs." When iFay migrates, the terminal scans and attempts to connect to available hardware. Contains three sub-types:
- **Device** — Terminal hardware devices
- **Storage** — Data storage resources
- **Computing** — Computing resources

### Faying Permissions
iFay's permission dimension — iFay's "relationships." Supports extensible authentication methods such as SSO, OAuth, Fingerprint (a collective term for any identity-recognizable identifier), etc. Permission lifecycles are divided into three types: inherent, persistent, and ephemeral.
