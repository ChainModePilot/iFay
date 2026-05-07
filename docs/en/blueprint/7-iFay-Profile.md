# 7. iFay Profile

iFay Profile is iFay's complete "identity card" — a semantically interpretable six-dimensional attribute table. It not only lets humans identify an iFay, but also lets systems parse it, and more importantly, lets Fays recognize each other.

The Human Prime profile (Aligned Consciousness) is a subset and input source of the iFay Profile. The Human Prime profile describes "what kind of person the Human Prime is," while the iFay Profile describes "what kind of entity this iFay is" — it includes the Prime's personality traits, but also iFay's own independent attributes such as skills, hardware, and permissions.

The Human Prime profile is maintained by the [Aligned Consciousness](./11.3-Aligned-Consciousness) module. The skills dimension is managed by [Registered Skill](./12.2-Registered-Skill), the hardware dimension by [Device Driver Hub](./12.1-Device-Driver-Hub), and the permissions dimension by [Credentials Management](./8.1-Credentials-Management).

---

## iFay Identity

iFay Identity consists of FayID and metadata. FayID is a globally unique, human-readable, machine-readable persistent identifier — the foundation for iFay to be identified and tracked across all interaction scenarios.

iFay Identity supports smooth identity migration — when iFay evolves from a personal assistant to an autonomous social role, the FayID doesn't need to change; identity naturally continues.

---

## Ego Model

The Ego dimension in the Profile records the reference to the currently active Ego version.

The Ego model is a pluggable, switchable edge small model that can be loaded onto any terminal device to give that device the Prime's personality. iFay supports having multiple Ego versions to accommodate the Human Prime's multifaceted personality — but only one version is active at any given moment, preventing "split personality."

There are two switching methods: manually triggered by the Human Prime, or automatically determined by iFay based on context. After switching, the active Ego version reference in the Profile is updated synchronously.

### Scenario

> Zhang Lei is a product manager who configured two Ego versions for his iFay: "Professional Mode" and "Casual Mode."
>
> On weekday mornings, iFay automatically switches to "Professional Mode" — email replies are rigorously worded, meetings are scheduled with efficiency as the priority, and requirement documents are handled with emphasis on logical completeness.
>
> On weekend evenings, iFay detects that Zhang Lei is browsing food recommendations and automatically switches to "Casual Mode" — restaurant recommendations focus more on ambiance and taste preferences, and the tone becomes relaxed and casual.
>
> Two versions, same Zhang Lei.

---

## Faying Thinking

Faying Thinking is iFay's cognitive assets, containing four sub-types:

| Sub-type | Description | Examples |
|----------|-------------|----------|
| **Content** | Structured or unstructured content assets | Human Prime's photo collection, written articles, composed music, recorded videos |
| **Data** | Personal data | Health monitoring data, spending records, app usage habits, location history |
| **Knowledge Base** | Organized knowledge systems | Professional domain notes, study material libraries, work experience summaries, industry research reports |
| **Info Feed** | Real-time information subscriptions | Followed news sources, industry update feeds, social media updates, stock quotes |

The data in the Thinking dimension comes from the initialization and continuous accumulation of the Personal Data Heap, forming the foundation for iFay to understand the world and make judgments.

---

## Faying Skills

Faying Skills are iFay's action capabilities, containing six skill types:

| Type | Description |
|------|-------------|
| **API** | Directly callable programming interfaces, such as weather query API, translation API |
| **Workflow** | Multi-step automated processes, such as "generate weekly report every Monday and send to team" |
| **Bot** | Conversational bots for specific scenarios, such as customer service Bot, appointment Bot |
| **Agent** | Intelligent agents with autonomous decision-making, such as investment analysis Agent |
| **APP** | Complete applications, such as calendar management APP, health tracking APP |
| **Microservice** | Independently deployed service units, such as image recognition service, speech-to-text service |

Skill registration is a prerequisite for iFay to perform any action. Registered skills complete pre-authorization, ensuring no additional authentication is needed during execution.

---

## Faying Hardware

Hardware is iFay's "limbs." iFay is a personality and cognitive entity; hardware is its vehicle for interacting with the physical world.

### Three Hardware Sub-types

| Sub-type | Description | Examples |
|----------|-------------|----------|
| **Device** | Terminal hardware devices | Phone, computer, smartwatch, drone, smart home devices |
| **Storage** | Data storage resources | Cloud storage, local hard drive, NAS, vector database |
| **Computing** | Computing resources | GPU, cloud computing nodes, edge computing devices |

### Hardware Discovery Mechanism

When iFay migrates to a new environment, the terminal device is responsible for scanning Faying-capable hardware in the current environment — similar to how Bluetooth or WiFi scans for nearby devices. iFay itself doesn't directly perform hardware scanning; instead, it performs capability matching based on scan results.

There's a key distinction here:

- **Which hardware iFay can operate** depends on its cognitive capabilities (registered skills, internal skills)
- **Which hardware iFay can connect to** depends on the devices actually available in the current environment

### Scenario

> Imagine a person who can play badminton walking into a sports hall.
>
> "Knowing how to play badminton" is their **skill** — it's their own capability that they carry wherever they go. But whether they can actually play depends on whether the hall has **rackets** — that's the hardware provided by the environment.
>
> iFay works the same way. It might have the skill to control a drone (registered a flight control API), but if there's no connectable drone in the current environment, that skill can't be exercised. Conversely, even if there's a 3D printer in the environment, if iFay hasn't registered the relevant operating skill, it can only "see" the device but can't use it.

---

## Faying Permissions

Permissions are iFay's "relationships" — they define the trust boundaries between iFay and the external world.

### Three Permission Lifecycles

| Lifecycle | Description | Examples |
|-----------|-------------|----------|
| **Inherent** | Permissions possessed from creation | Access to Human Prime's calendar, reading Prime's preference settings |
| **Persistent** | Long-term valid permissions | Read/write access to Prime's email, corporate intranet access |
| **Ephemeral** | Applied for when needed, released after use | One-time access to medical records, temporary API call rights |

### Extensible Authentication Methods

iFay's authentication methods are extensible, supporting SSO, OAuth, Fingerprint, and other methods. "Fingerprint" here is a collective term covering any identity-recognizable identifier — facial recognition, voiceprint, device fingerprint, etc. Different fingerprint types have different confidence levels: facial recognition may have higher confidence than device fingerprint, while multi-factor combinations have higher confidence than single factors.

### Scenario

> Wang Fang's iFay has three permissions with different lifecycles:
>
> **Inherent**: When iFay was created, it automatically gained access to Wang Fang's calendar — this is a basic capability of every iFay, requiring no additional application.
>
> **Persistent**: Wang Fang authorized iFay to manage her work email long-term. iFay can read emails, draft replies, and manage labels — this permission remains valid until Wang Fang actively revokes it.
>
> **Ephemeral**: Wang Fang needs to view last year's physical exam report. She asks iFay to retrieve records from the hospital system. iFay temporarily applies for one-time medical data access permission, and after obtaining the report, the permission is automatically released — next time it's needed, a new application is required.

---

## Profile Visibility

Profile visibility is an application-layer concern, determined by specific application scenarios and interaction methods.

The same iFay Profile displays different dimensions in different scenarios: during inter-Fay collaboration, the other party may only need to see the skills and permissions dimensions; in the Human Prime management interface, all six dimensions are fully visible; in public social scenarios, only identity and partial skill information may be shown.

The Profile itself doesn't define "who can see what" — that decision is left to the application using the Profile.
