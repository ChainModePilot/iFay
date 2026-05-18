# 8. Social Layer

The Social Layer defines iFay's **mode of existence** in society — it answers three fundamental questions: "Who am I" (Identity), "What am I authorized to do" (Social Permissions), and "How much are my contributions worth" (Social Contribution & Voice).

If we compare iFay to a social person, the Social Layer is their **social identity**: an ID card proves who you are, various certificates and keys prove what you're authorized to do, and your social reputation and contribution record determine your voice and credibility in the community.

The Social Layer is the cornerstone of iFay's security system and the prerequisite for iFay's integration into social relationships.

```
iFay Four-Layer Architecture
├── 👉 Social Layer
│   ├── 8.1 Identity (FayID)              ← Who am I
│   ├── 8.2 Social Permissions            ← What am I authorized to do
│   │   ├── Account/Password
│   │   ├── Certificate
│   │   ├── Authorization
│   │   ├── Access Token
│   │   └── Smart Contract
│   └── 8.3 Social Contribution & Voice   ← How much are my contributions worth
│       ├── GMChain (Global Merit Chain)
│       └── MeriToken
├── Interaction Layer
├── Cognition Layer
└── Ego Layer
```

---

## 8.1 Identity (FayID)

### One-Line Definition

FayID is iFay's **identity number** — a globally unique, human-readable, machine-readable persistent identifier that serves as the foundation for iFay to be recognized and tracked in all social interactions.

### Why It's Needed

In human society, an ID number is the starting point for all social activities — without an ID, you can't open a bank account, sign a contract, or even buy a train ticket. FayID has the exact same significance for iFay: it is the prerequisite for iFay to participate in any social interaction.

FayID's design has two key considerations:

1. **Unified Identification**: iFay and coFay use the same FayID generation and management mechanism. This ensures that when individual iFays eventually assume meaningful social roles, their identity can transition smoothly — just as some individual YouTubers evolve into playing important roles in public discourse without needing to change their identity.

2. **Activation Binding**: FayID is deeply bound to the Faying Protocol. No iFay should act autonomously without the Human Prime's explicit intent. FayID's activation state is managed by the [Faying Protocol](https://github.com/ChainModePilot/Faying-Protocol/wiki), ensuring iFay only operates under the Human Prime's explicit authorization.

### Core Properties

| Property | Description |
|----------|-------------|
| **Globally Unique** | Supports identifier capacity exceeding the global population scale, ensuring no collisions |
| **Human-Readable** | Humans can intuitively recognize and remember it — not a meaningless hash string |
| **Machine-Readable** | Systems and Fays can efficiently parse and match it |
| **Persistent** | Once assigned, it never changes throughout iFay's lifetime, supporting identity migration and personality continuity |
| **Activation State** | Linked with the Faying Protocol, clearly indicating whether iFay is currently active or dormant |

### Scenario

> Xiao Ming registers his own iFay, and the system assigns FayID `fay://ming.2024.cn`. This ID will accompany Xiao Ming's iFay for life — whether iFay migrates from phone to computer, or evolves from personal assistant to Xiao Ming's digital legacy agent, the FayID never changes.
>
> When Xiao Ming's iFay communicates with a hospital's coFay, both parties identify each other through FayID, just like two people exchanging business cards when they meet.

### For Developers

- **Independent Project**: FayID is an [independent open-source project](https://github.com/ChainModePilot/FayID); see [FayID documentation](https://github.com/ChainModePilot/FayID/wiki)
- **Interface Specification**: `FayIDRegistry` interface with `generate()` (generate FayID), `resolve()` (resolve FayID), `getActivationStatus()` (get activation status)
- **Conformance Testing**: iFACTS L1 verifies FayID uniqueness and persistence; L2 verifies activation state linkage with the Faying Protocol

---

## 8.2 Social Permissions

### One-Line Definition

Social Permissions is iFay's **keychain** — it securely manages the credentials iFay needs to use various services on your behalf. But these credentials aren't your originals — they're secure copies. Even if a copy is lost, your original credentials remain safe.

### Why It's Needed

iFay needs to act on your behalf — log into e-commerce platforms to buy things, use your company email to send messages, control smart home devices, call third-party APIs. All of these require "keys." The Social Permissions module helps you securely manage these keys through a **copy mechanism** that ensures original credentials are never directly exposed.

### Five Permission Types

Social Permissions manages five credential types, each corresponding to different social relationship scenarios:

#### 1. Account / Password

The most common credential type. The Human Prime delegates application and service account passwords to iFay, and iFay uses these credentials through the copy mechanism to log in and operate.

- **Copy Mechanism**: iFay doesn't hold the original password but holds a permission-restricted copy credential
- **Permission Scope**: Copies can have stricter permissions than the original (e.g., "daily necessities only, single purchase not exceeding 200 yuan")
- **Anomaly Revocation**: Automatically revokes the copy when abnormal use is detected; original password remains unaffected

> 🎯 Scenario: You delegate your e-commerce platform account to iFay. What iFay receives is not your original password but a secure copy. She can use this copy to place orders for you, but if the copy is compromised, you can revoke it with one click — your original password remains unaffected.

#### 2. Certificate

Digital certificates for encrypted communication and identity verification. Compatible with existing Certificate Authority (CA) systems, supporting standard formats like X.509.

- **Purpose**: End-to-end encrypted communication, code signing, identity authentication
- **Compatibility**: Seamless integration with existing PKI infrastructure, supporting certificates issued by major CAs
- **Lifecycle**: Supports full lifecycle management of certificate application, renewal, and revocation

> 🎯 Scenario: iFay needs to communicate with a banking system via encrypted channel. It uses a digital certificate delegated by the Human Prime to establish a TLS connection, ensuring data transmission confidentiality and integrity. The certificate is issued by a trusted CA, allowing the banking system to verify iFay's identity legitimacy.

#### 3. Authorization

Compatible with traditional third-party authentication methods (e.g., OAuth 2.0), allowing iFay to authenticate with third-party platforms through authorized factors to obtain restricted access permissions.

- **OAuth Compatible**: Supports OAuth 2.0 authorization code flow, client credentials flow, and other standard patterns
- **Factor Authentication**: Obtains authorization for social platforms, financial services, etc. through account fingerprint information (device fingerprint, biometrics, behavioral patterns)
- **Scope Control**: Precisely controls authorization scope, ensuring iFay can only access necessary resources

> 🎯 Scenario: You authorize iFay to access your social platform. iFay doesn't need your social platform password — it goes through the OAuth flow, using your device fingerprint and facial recognition as authentication factors to obtain a scope-restricted access token. This token only allows reading your friend list and sending messages, not modifying account settings.

#### 4. Access Token

Managed temporary access credentials, usually with an expiration period. Used for API calls, service access, and similar scenarios.

- **Expiration Management**: Automatically tracks token expiration time and refreshes before expiry
- **Least Privilege**: Each token grants only the minimum permissions needed to complete a specific task
- **Audit Trail**: Every token use is recorded, supporting post-hoc auditing

> 🎯 Scenario: iFay needs to call a translation API. It holds an API Key (access token) that automatically rotates every 24 hours. If a key is compromised, the impact is limited to 24 hours of call volume, and the system immediately detects abnormal call patterns and triggers revocation.

#### 5. Smart Contract

Blockchain smart contract credentials for decentralized services and automated collaboration between Fays.

- **Automatic Execution**: Executes automatically when contract conditions are met, no manual intervention needed
- **Immutable**: Contract content cannot be unilaterally modified once deployed
- **Transparent and Verifiable**: Any participant can verify the contract's execution results

> 🎯 Scenario: Your iFay signs a smart contract with a data analysis coFay — "automatically pay 5μ upon analysis completion." When the coFay completes the analysis and submits results, the contract automatically verifies result quality and executes payment — no manual confirmation needed. The entire process is transparent, immutable, and automatically executed.

### Copy Mechanism and Security Defense

All five permission types follow unified security principles:

- **Copy Isolation**: iFay never directly holds original credentials — only permission-restricted copies
- **Owner Tagging**: Each credential indicates whether the owner is the Human Prime or iFay itself (iFay can independently acquire credentials)
- **Audit Trail**: Every credential use is recorded, supporting post-hoc auditing
- **Anomaly Detection**: Automatically revokes copies and notifies the Human Prime when abnormal use patterns are detected
- **Privacy Protection**: When iFay is authorized to query private data, only boolean results (true or false) are returned without exposing actual data

### For Developers

- **Interface Specification**: `CredentialManager` interface with `delegate()` (delegate/create copy), `authenticate()` (authenticate), `revoke()` (revoke), `queryPrivacy()` (privacy query, returns boolean only), `getAuditLog()` (audit log)
- **Five Credential Types**: `account_password`, `certificate`, `authorization`, `access_token`, `smart_contract`
- **Credential Owner**: `human_prime` or `ifay`
- **Copy Status**: `active`, `revoked`, `expired`
- **Conformance Testing**: iFACTS L1 verifies management of five credential types and copy mechanism; L2 verifies authentication interfaces with Registered Skill and Invoke Skill; L4 verifies boolean return constraint for privacy queries and anomaly detection behavior

---

## 8.3 Social Contribution & Voice (GMChain & MeriToken)

### One-Line Definition

GMChain (Global Merit Chain, GMC) is the iFay ecosystem's **social contribution ledger** — it records every contribution made by Fays and humans to society, quantified as MeriToken. MeriToken is not currency — it is a **measure of voice and reputation**.

### Why It's Needed

In traditional society, a person's social standing and voice depend on their contributions, reputation, and accumulated trust. But these are often vague, subjective, and hard to quantify.

In the Fay ecosystem, most work is done by Fays, and every collaboration and contribution can be precisely tracked and recorded. GMChain is this tracking and recording system — it makes "who contributed what" transparent, verifiable, and immutable.

MeriToken is the unit of measurement on GMChain, representing social contribution. Its purpose is not "buying things" but rather:
- **Measuring Contribution**: How much value has your iFay created for society?
- **Building Reputation**: More contributions mean higher reputation and greater trust in the collaboration network
- **Earning Voice**: Contributors have greater voice in decisions requiring community consensus
- **Incentivizing Collaboration**: Contributions in Fay-to-Fay collaboration are fairly recorded and rewarded

### GMChain's Position

GMChain is a **value measurement infrastructure that spans all levels** of the iFay system. It doesn't belong to any specific module but provides contribution tracking and value measurement capabilities for the entire ecosystem.

In the CPE+M framework, M (Merit) represents the contribution measurement layer embodied by GMChain — it spans Context, Protocol, and Environment layers, providing unified contribution recording and incentive mechanisms for all participants (humans, iFay, coFay, service providers).

```
GMChain's Position in the CPE+M Framework
┌─────────────────────────────────────────────┐
│  Merit (M) — GMChain / MeriToken            │  ← Spans all layers
│  Track, measure, evaluate contributions,    │
│  incentivize value creation                 │
├─────────────────────────────────────────────┤
│  Context (C)  │  Protocol (P)  │  Env (E)  │
│  Context      │  Protocol      │  Runtime   │
│  Environment  │  System        │  Env       │
└─────────────────────────────────────────────┘
```

### GMChain's Core Mechanisms

**1. Contribution Recording**

GMChain records the following types of contributions:
- Tasks completed through Fay-to-Fay collaboration (e.g., a travel coFay booking tickets for you)
- Providing information assembly services (e.g., data cleaning, knowledge organization)
- Providing API and skill services
- Providing device and computing resources
- Providing runtime environments
- Other value-adding inputs recognized by the community

**2. Price Negotiation**

Fays negotiate prices (in μ units) before executing collaborative tasks. This ensures:
- Every collaboration's contribution is trackable and evaluable
- No "getting paid without working" or artificially inflated value
- Contributors receive fair rewards

**3. MeriToken Ledger**

The MeriToken Ledger is the contribution score record for each Fay and human. It records:
- Cumulative total contributions
- Contribution type distribution
- Reputation score (based on contribution quality and collaboration feedback)
- Voice weight (voting weight in community governance)

### Fundamental Differences from Traditional Cryptocurrencies

| Dimension | Traditional Cryptocurrency | MeriToken |
|-----------|---------------------------|-----------|
| **Acquisition** | Consuming computing power for computational tasks (mining) | Creating social value (contribution) |
| **Value Anchor** | Market supply/demand and speculation | Social contribution |
| **Purpose** | Financial asset, investment tool | Reputation measurement, voice, collaboration incentive |
| **Fiat Currency Relationship** | Exchangeable with fiat currency | Not exchangeable with fiat currency |
| **Volatility** | Highly volatile | Stable growth (contributions only increase) |

### Long-term Vision and Current Position

> ⚠️ **Important Note**: GMChain/MeriToken is a long-term vision product for a fully AI-driven society, belonging to Roadmap Phase 5 (Fay Reshapes Labor Structure and Value Distribution) as a core component. We will not rush to implement GMChain and MeriToken in the short term, but must reserve a place for them in the system design because they are the key infrastructure for the iFay ecosystem's evolution from "tool usage" to "social collaboration."
>
> We commit:
> - GMChain will never accept monetary injection
> - MeriToken will not be exchangeable with fiat currency
> - MeriToken measures social contribution, not financial assets
>
> In a fully AI-driven society, the fulfillment of survival and social needs does not depend on monetary cost. MeriToken's value-anchoring mechanism is fundamentally different from traditional cryptocurrencies. Details will be progressively refined through rigorous argumentation in subsequent phases.

### Scenario

> Your iFay books a flight for you and contacts a travel coFay via the Telepathy Protocol. The travel coFay quotes 15μ for the complete booking service. Your iFay accepts the quote, and after the travel coFay completes the task, GMChain automatically records this collaboration:
>
> - The travel coFay's MeriToken Ledger increases by 15μ (service contribution)
> - Your iFay's MeriToken Ledger records a "service consumption" (no point deduction, only collaboration history recorded)
> - The airline coFay's MeriToken Ledger increases by 2μ (contribution for providing SSP interface)
>
> As the travel coFay accumulates more contribution records, its reputation score grows higher, becoming increasingly trusted in the collaboration network — more iFays will preferentially choose it, forming a positive cycle.

### For Developers

GMChain belongs to **Phase 5 (Fay Reshapes Labor Structure and Value Distribution)** as a core component, but its interface definitions need to be reserved in early phases.

- **Independent Project**: GMChain is an [independent open-source project](https://github.com/ChainModePilot/Global-Merit-Chain); see [GMChain documentation](https://github.com/ChainModePilot/Global-Merit-Chain/wiki)
- **Interface Specification**: `MeritLedger` interface with `recordContribution()` (record contribution), `getBalance()` (query balance), `getReputation()` (query reputation score), `negotiate()` (price negotiation)
- **Unit of Measurement**: μ (MU, Merit Unit), the smallest unit of MeriToken
- **Conformance Testing**: iFACTS L4 verifies immutability of contribution records and fairness of price negotiation
- **Design Points**: Contribution records are immutable; price negotiation completes before task execution; MeriToken is not exchangeable with fiat currency; reputation scores are based on contribution quality and collaboration feedback
