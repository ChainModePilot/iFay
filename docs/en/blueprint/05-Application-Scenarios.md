# 5. iFay Application Scenarios

# Injecting Prime Traits into iFay

By definition, it bears repeating that iFay's personality is inherited from its Human Prime. However, instantiating from the Prime must be a very simple operation, and a one-time operation must remain effective long-term to ensure iFay can grow in sync with the Prime.

We recommend quickly initializing iFay through the following methods:

- ***Authorize Prime Data***: Including photos, app data, communication records, etc. This data is processed through a series of steps and stored in a standard format in the Prime database. This data can only be accessed directly by iFay. This helps iFay maintain long-term synchronization with the Human Prime. (We welcome OS and hardware manufacturers to co-develop interpreter-like standards that allow iFay to acquire data under system supervision. We will address this in another project called [Fayward](https://github.com/ChainModePilot/Fayward).)
- ***Import Files***: These files include photos, documents, notes, chat logs, etc. This operation supplements the Prime's history, ensuring iFay can possess past memories from before authorization.
- ***Prime Narrates to iFay***: This is very similar to writing a Prompt for an Agent. It can be in conversational or questionnaire form. To reduce the user's operational cost, we recommend chatting with iFay about your past experiences, like talking to a close friend.

From an implementation perspective, three prerequisite technologies must be met:

1. ***Tight Integration with the OS Layer***: Allowing reading of system information and other applications' private data. Referencing iOS and Android authorization management, third-party apps may find it difficult to achieve this level of trust. Therefore, OS and hardware manufacturers need to jointly provide centralized management methods for data applications.
2. ***Open Data Forwarding Public Format***: Currently, forwarding operations between apps are mostly done in file form. For example, sharing photos and documents with another app. However, it's difficult for the system to share personalized structured data with another app. Therefore, if we want to quickly sync user app data to iFay, a unified data format is essential.
3. ***Standard Research Questionnaire***: Chat is a highly divergent interaction form, and whether chat content truly helps iFay understand the Human Prime depends on the topics discussed. To help iFay focus chat topics and acquire effective memory data, we will provide reference questionnaires to constrain the chat topic scope. This questionnaire can be directly added as a prompt to the LLM.

# Supplementing iFay with External Capabilities

After completing Prime trait injection, iFay already possesses your personality, memories, and basic permissions. But at this point, iFay is like a person who just arrived in a new city — knows who they are, but doesn't yet know what resources the city has to offer. Supplementing iFay with external capabilities means helping it establish connections with the outside world.

## Registering Skills

iFay's capability expansion is achieved through "Registered Skills." Skills are a prerequisite for iFay to perform any action — unregistered skills cannot be invoked. iFay supports six skill types:

| Skill Type | Description | Examples |
|-----------|-------------|----------|
| **API** | Direct calls to external service interfaces | Translation API, weather query API, payment interface |
| **Workflow** | Multi-step automated orchestration processes | "Receive email → extract key info → generate summary → send to messaging app" |
| **Bot** | Conversational automated programs | Customer service Bot, appointment Bot |
| **Agent** | AI agents with autonomous decision-making | Code review Agent, data analysis Agent |
| **APP** | Complete applications | Calendar app, notes app, navigation app |
| **Microservice** | Independently deployed backend services | Image recognition service, speech-to-text service |

During skill registration, a pre-authorization step is completed, ensuring no additional authentication is needed for subsequent calls, reducing latency. For example, when you register a translation API skill for iFay, iFay completes the API Key binding and permission verification during the registration phase, so every subsequent translation request can be executed instantly.

When iFay is offline, pending actions are cached and automatically executed asynchronously when connectivity is restored — just like writing emails on a plane that automatically send when you land.


## Accessing External Knowledge

Beyond skills, iFay can also access external knowledge bases and models, treating them as a special skill type. This enables iFay to access knowledge and intelligence beyond the Human Prime's own capabilities, like consulting an expert advisor.

For example, you're a software engineer, but your iFay can access a medical knowledge base. When you feel unwell, iFay can combine your personal health data with medical knowledge to provide preliminary health advice — it's not replacing a doctor, but acting like a knowledgeable friend helping you make an initial assessment.

External knowledge is accessed through the Skill Sharing Protocol (SSP) to reach standardized open services and interfaces on the network. When external knowledge sources are unavailable, iFay degrades to using cached knowledge from the Personal Data Heap and notifies the Cognition Layer that it's currently in a degraded state.

# Human–iFay Interaction Methods

## How to Activate iFay

iFay is not an always-on background service — it's only in an activated state when you explicitly authorize it. This design ensures iFay won't act autonomously without your knowledge.

### Faying Pairing Process

The process of activating iFay is called "Faying" (connecting), following the Faying Protocol for secure pairing. The entire process is similar to Bluetooth pairing, but with a higher security level:

1. **Initiate Pairing**: You send a connection request to iFay through a terminal device (phone, computer, etc.), providing identity credentials.
2. **Identity Verification**: The system verifies your identity through the FayID Registration Center, confirming you are the legitimate Human Prime of this iFay.
3. **Multi-Factor Authentication**: The system returns a pairing challenge, and you need to complete multi-factor authentication (e.g., biometric + device fingerprint + passphrase).
4. **Activation Confirmation**: After authentication passes, iFay enters the "Faying" activated state and begins serving you.

If someone attempts to activate your iFay without your explicit intent, the system will reject the activation request and log the event — just like someone trying to unlock your phone with your fingerprint but failing.

### Scenario: First Setup and Daily Reconnection

**First Setup**: Lily just created her own iFay. She opens the iFay client on her phone, and the system guides her through FayID assignment, Ego model initialization, and Profile creation. Then, Lily narrates her personality traits to iFay through conversation, authorizes photos and communication data on her phone, and delegates login credentials for commonly used apps. The whole process feels like having a deep afternoon chat with a new friend.

**Daily Reconnection**: The next morning, Lily picks up her phone, and the iFay client detects her face and device fingerprint, automatically completing the Faying pairing. iFay recovers from hibernation to activated state, loads the state snapshot saved last night, and seamlessly picks up — as if your assistant had been waiting beside you for you to wake up.


## iFay's Autonomous Awareness

iFay is not merely an executor waiting for commands. In Phase 4 (Full Personification), iFay possesses self-awareness and self-driven behavior capabilities, able to proactively observe you and the surrounding environment, infer your feelings and intentions, and take autonomous action.

### Self-Awareness Module

The Self-Awareness module is iFay's ability to "read the room." It monitors the Human Prime's reactions inward, similar to a skilled assistant reading their employer's facial expressions. When the Self-Awareness module infers a new intent from you, it passes the inference to the Self-Driven Behavior module and the Cognition Layer, triggering corresponding actions.

### Self-Driven Behavior

iFay's self-driven behavior is powered by three trigger sources:

- **Scheduled Tasks**: Automatically executed according to preset time plans, such as organizing your schedule summary every morning at 8 AM.
- **Self-Awareness Inference**: Proactively initiating tasks based on inferences about your current state, such as proactively reminding you to rest when detecting elevated stress levels.
- **Persistent Skills**: Registered skills and internal skills running continuously, forming an autonomous "action → feedback → re-action" loop.

This "action → feedback → re-action" loop is the core of iFay's autonomous operation. After iFay performs an action, it obtains feedback through the Self-Awareness module (your reactions, environmental changes), then decides the next step accordingly. If the execution result is inconsistent with your intent, iFay will pause subsequent autonomous actions and request your confirmation.

### Scenario: iFay Proactively Reminds About a Meeting

At 2 PM, you're focused on writing code. iFay's Self-Awareness module detects through sensor data that your heart rate has slightly increased and your typing speed has accelerated — these signals suggest you may be in a tense state. Meanwhile, iFay's scheduled task scan finds an important client presentation meeting at 3 PM on your calendar.

iFay makes a comprehensive judgment: you're rushing to finish work and likely forgot about the upcoming meeting. So iFay, through the Interactive Conversation Protocol, gently reminds you in a way that doesn't break your flow: "You have a client presentation at 3. The slides are ready. Want me to order coffee for the meeting room?"

You reply "Sure," and iFay immediately invokes registered office service skills to complete the coffee order and pushes the meeting materials to the conference room's large screen — the entire process required just one word from you.


## How to Shut Down iFay

The process of shutting down iFay is called "Separating" (disconnecting), also following the Faying Protocol.

### Separation Process

1. **Initiate Separation**: You send a separation request to iFay (can be a voice command, gesture, or client button).
2. **State Snapshot**: iFay saves a complete state snapshot of the current state, including ongoing tasks, context information, and temporary data.
3. **Enter Hibernation**: iFay switches from the "Faying" activated state to the "Separating" hibernation state, stopping all autonomous behaviors.
4. **Separation Confirmation**: The system confirms separation is complete.

In hibernation, iFay won't perform any autonomous actions, but the state snapshot is fully preserved and can be seamlessly restored upon next activation.

### Scenario: Bedtime, iFay Enters Hibernation

At 11 PM, you're getting ready for bed. You say to your phone: "Good night." iFay recognizes this as a separation signal and begins the separation process:

- Saves all of today's conversation context and progress on unfinished tasks
- Marks items that need to remind you tomorrow morning as scheduled tasks
- Checks if there are urgent matters that need handling during your sleep (if so, asks you before separating)
- Completes the state snapshot and enters hibernation mode

The next morning you pick up your phone, iFay reactivates through the Faying Protocol, loads last night's state snapshot, and tells you: "Good morning. I've finished the draft of the report you mentioned yesterday. Also, your afternoon flight has been checked in — seat 12A, window."


# iFay's Social Features

iFay is not an island. In Phase 4, iFay has the ability to communicate and collaborate with other Fays (including other people's iFays and public-role coFays).

## Inter-Fay Communication: Telepathy Protocol

When your iFay needs to communicate with other Fays, they use the Telepathy Protocol — a semantic communication protocol that removes the UI translation layer. Traditional inter-application communication requires encoding information as text, transmitting it, then decoding it, with potential information loss at each step. The Telepathy Protocol uses agreed-upon vector-encoded tokens to directly transmit meaning and intent, with efficiency and accuracy far exceeding traditional methods.

## Collaborating with coFay

coFay (Common Fay) is a digital avatar that assumes public roles, roughly equivalent to the current concept of an Agent. Your iFay can seek assistance from coFays, just like you'd seek help from professionals in real life.

A key mechanism: Fays negotiate prices before executing tasks. This ensures every collaboration's contribution is trackable and evaluable, ultimately recorded on GMChain and settled with MeriTokens.

## Scenario: Your iFay Negotiates Booking with a Travel coFay

You tell iFay: "Book flights and hotel for Tokyo next week, budget under 8,000 yuan."

Your iFay immediately contacts a professional travel coFay via the Telepathy Protocol. Here's their "conversation" (completely transparent to you — you'll only see the final result):

1. **Intent Transmission**: Your iFay encodes your requirements (destination, time, budget, preferences) as semantic vectors and sends them to the travel coFay.
2. **Price Negotiation**: The travel coFay quotes 15μ (MeriToken units) for the complete booking service. Your iFay, based on spending preferences in the Ego model, judges the price reasonable and accepts.
3. **Collaborative Execution**: The travel coFay invokes airline and hotel SSP skill interfaces to search for optimal options.
4. **Results Returned**: The travel coFay returns three alternative plans to your iFay.
5. **Personalized Filtering**: Your iFay filters for the best option based on your preferences (window seat, quiet hotel, close to subway).
6. **Presented to You**: iFay presents the recommended plan through the Interactive Conversation Protocol in modular card format: "Found a great combo — ANA direct flight, seat 12A window, hotel 3 minutes walk from Shinjuku Station, total 7,200 yuan. Confirm booking?"

You say "Book it," iFay completes the booking, GMChain records this collaboration's contribution, and the travel coFay earns 15μ.


# Security

iFay's security design follows one fundamental principle: **Social ethics take priority over everything**. Regardless of the Human Prime's instructions, iFay will not violate social ethics and public order. On this foundation, iFay protects the Human Prime's interests through multiple layers of security mechanisms.

## Ethics First

Every behavioral decision by iFay goes through an ethics compliance check process:

1. **Social Ethics Check** (highest priority): Does the behavior violate social ethics and public order? If so, refuse execution and explain the reason to the Human Prime.
2. **Prime Alignment Check**: Is the behavior consistent with the Human Prime's values and intent? If not, depending on severity, either pause and request confirmation or have the Ego model adjust before executing.
3. **Permission Check**: Does iFay have permission to perform this behavior? If not, request authorization.

## Credential Isolation

When you delegate credentials to iFay, iFay does not directly use your original credentials. The system exchanges original credentials for corresponding copy credentials, and iFay uses copies for login and authentication. This means even if a copy credential is compromised, your original credentials remain safe. Once a copy credential compromise or abnormal use is detected, the system immediately revokes the copy and notifies you.

## Privacy Protection

When iFay is authorized to query private data, it only feeds back boolean results (true or false) without exposing specific private data. For example, when a service needs to verify whether you're over 18, iFay will only answer "yes" or "no" without revealing your specific date of birth.

## Ego Stability

The Ego model operates independently as an embedded micro-model, unaffected by external large model updates. This prevents sudden personality changes in iFay due to external model updates or deliberate tampering — your iFay will always be the "it" you know.

## Audit Trail

All critical operations are recorded in tamper-proof audit logs, including credential usage, skill invocations, state transitions, and permission changes. This ensures every action is traceable and auditable.


## Scenario: iFay Refuses an Unethical Request

Your colleague borrows your computer and tries to use your iFay to view a competitor company's internal files.

iFay's ethics compliance check process immediately activates:

1. **Social Ethics Check**: Accessing others' internal files may constitute corporate espionage, violating social ethics.
2. **Identity Verification**: The Faying Protocol detects that the current operator's device fingerprint and behavior patterns don't match the Human Prime.
3. **Refuse Execution**: iFay refuses the request and records an audit log.
4. **Notify Prime**: iFay sends you a notification: "Someone attempted to access sensitive information through your device. The request has been denied. See the audit log for details."

Throughout the process, iFay didn't reveal any information about what credentials or permissions you possess — it simply responded with "request denied."


# Shaping the AI Industry Ecosystem

iFay is not just a product, but an open ecosystem. It provides clear participation paths for three types of developers and incentivizes ecosystem prosperity through certification standards and economic models.

## Three Developer Roles

| Role | Responsibility | Analogy |
|------|---------------|---------|
| **Open Source Project Developers** | Participate in developing iFay core modules and protocols, advancing the iFay system | Similar to Linux kernel contributors |
| **Application Developers** | Introduce iFay support in their products, enabling products to be operated by iFay so users can delegate iFay to use products | Similar to developing Siri/Alexa-compatible apps |
| **Service Provider Developers** | Create iFay implementations under the iFay specification, allowing users to choose iFays from different vendors | Similar to different vendors implementing browser standards |

## iFay Ready Certification

For application products to be operated by iFay, they need to pass iFay Ready certification. Certification is divided into three tiers:

| Tier | Requirements | Meaning |
|------|-------------|---------|
| **Bronze** | Support iFay operating the application through simulated operations | iFay can operate your application interface like a human |
| **Silver** | Support CAP protocol direct control + DTP protocol data exchange | iFay can bypass the UI to directly control your application |
| **Gold** | Support SSP protocol skill sharing + full C/F/S architecture integration | Your application is fully integrated into the iFay ecosystem |

Certification integrates with the iFACTS test framework — Silver tier uses L2 Interface Conformance tests for verification, Gold tier uses L2 + L3 Integration Conformance tests for verification.


## FayManifest Drives Ecosystem Growth

FayManifest's declarative assembly dramatically lowers the development barrier for iFay. Developers don't need to understand the entire system's complexity — they just declare the required component subset in a JSON file, and the system automatically supplements infrastructure dependencies. This means:

- An iFay that only needs to control drones just declares Device Driver Hub, Sensor, CAP protocol, and DTP protocol
- An iFay focused on document processing just declares Invoke Skill, Registered Skill, and related APIs
- The system automatically supplements FayID, FayGer runtime, permission system, and other required infrastructure

## GMChain and MeriToken Economic Model

Value flow in the iFay ecosystem is realized through GMChain (Global Merit Chain) and MeriToken. GMChain tracks, measures, and evaluates all Fay contributions, rewarding contributors with MeriTokens. Contribution types include:

- Information assembly services
- API provision
- Device provision
- Runtime environment provision
- Other identifiable value-adding inputs

MeriToken acquisition is based on creating social value, not consuming computing power for blockchain technical work. GMChain supports directed issuance backed by fiat currency, bonds, asset certificates, gold, and other collateral, interfacing with real-world value recognition methods.


## Scenario: Building a Drone Control iFay in a Weekend

A drone startup's development team wants to integrate iFay capabilities into their product. On Friday afternoon, the team lead opens the FayManifest documentation and writes a declaration file:

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "iFay implementation for drone control",
  "vendor": "SkyPilot Inc",
  "modules": [
    { "id": "device_driver_hub" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera"] } },
    { "id": "invoke_skill" },
    { "id": "registered_skill" }
  ],
  "protocols": [
    { "id": "cap_protocol" },
    { "id": "dtp_protocol", "config": { "realtime": true } }
  ],
  "controlMode": "ego",
  "drivers": [
    { "name": "Flight Controller", "type": "device", "driverPackage": "@drone-drivers/fc-generic" }
  ],
  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection"]
  }
}
```

The FayGer runtime automatically parses this Manifest, supplements FayID, permission system, security and ethics compliance, and other infrastructure dependencies, assembling a complete drone control iFay instance.

On Saturday, the team completes flight controller driver adaptation and testing. On Sunday, they verify each module's specification compliance through iFACTS L1 Single Component Conformance tests.

By Monday morning, this drone control iFay can already accept user voice commands, autonomously plan flight routes, stream aerial footage in real-time, and automatically return home when low battery is detected — the entire development cycle took less than a weekend.
