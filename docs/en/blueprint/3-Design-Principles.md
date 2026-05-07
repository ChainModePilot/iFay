<img width="100%" alt="iFay Title Banner" src="./illustration/ifay-title-banner.png"/>

# 3. Design Principles

iFay (Individual Fay) is an AI digital avatar deeply bound to a natural person. It is not a tool, but an extension of your personality — fusing your character, memories, preferences, and digital capabilities, taking over your mechanical, repetitive, and dangerous labor, and amplifying your social value. iFay adopts the CPE+M framework (Context, Protocol, Environment, Merit), consisting of a four-layer architecture — Social Layer, Interaction Layer, Cognition Layer, and Ego Layer — covering five evolutionary phases from simulating human operations to reshaping labor structure and value distribution.

---

## Design Principles

iFay's design follows five core principles that permeate the entire system's architecture and implementation:

| # | Principle | One-Line Summary |
|---|-----------|-----------------|
| 1 | **Ecosystem-Friendly Progressive Adoption** | Ecosystem partners don't need to implement a complete iFay to ship a product — an iFay that only controls drones just needs to satisfy the required component subset to go live. |
| 2 | **Declarative Minimal Assembly** | Define required components, protocols, and configurations through a single FayManifest declaration file, assembling iFay like writing a package.json. |
| 3 | **Flexible Composition** | Components are loosely coupled and mixable; implementations from different vendors can be freely combined as long as they conform to interface contracts. |
| 4 | **Personified, Not Toolified** | iFay is not an Agent — each iFay has a unique personality, memory, and preferences, an instantiation of the Human Prime, capable of continuing the Prime's personality even after they pass away. |
| 5 | **Scenario-Driven Intuition** | Every functional module can be explained with a concrete life scenario, letting readers intuitively imagine life with iFay. |

---

## Table of Contents

1. [Definition and Concept](./2-Definition-and-Concept)

    Provides the definition and structural overview of iFay, analyzes the fundamental differences between iFay and the current Agent concept, and the principles behind its operational characteristics.

---

2. [iFay Application Scenarios](./5-Application-Scenarios)

    The complete process of actually using iFay from scratch: how to inject your personality, add skills to iFay, interact with iFay, how iFay socializes, and a panoramic view of security and the industry ecosystem.

    - [Injecting Prime Traits into iFay](./5-Application-Scenarios#injecting-prime-traits-into-ifay)
    - [Supplementing iFay with External Capabilities](./5-Application-Scenarios#supplementing-ifay-with-external-capabilities)
    - [Human-iFay Interaction Methods](./5-Application-Scenarios#human-ifay-interaction-methods)
        - [How to Activate iFay](./5-Application-Scenarios#how-to-activate-ifay)
        - [iFay's Autonomous Awareness](./5-Application-Scenarios#ifays-autonomous-awareness)
        - [How to Shut Down iFay](./5-Application-Scenarios#how-to-shut-down-ifay)
    - [iFay's Social Features](./5-Application-Scenarios#ifays-social-features)
    - [Security](./5-Application-Scenarios#security)
    - [Shaping the AI Industry Ecosystem](./5-Application-Scenarios#shaping-the-ai-industry-ecosystem)

---

3. [iFay Is a Replication of Human Personality](./6-iFay-Personality-Replication)

    iFay is attached to a specific natural person, so the Human Prime's traits need to be injected into iFay from three dimensions: personality shapes the Ego model, data populates the Personal Data Heap, and permissions establish credential delegation.

    - [Prime Personality](./6-iFay-Personality-Replication#prime-personality)
    - [Prime Data](./6-iFay-Personality-Replication#prime-data)
    - [Prime Permissions](./6-iFay-Personality-Replication#prime-permissions)

---

4. [iFay Profile](./7-iFay-Profile)

    iFay Profile is iFay's complete "identity card" — a semantically interpretable six-dimensional attribute table used for humans to identify iFay, systems to identify iFay, and Fays to identify each other.

    - [iFay Identity](./7-iFay-Profile#ifay-identity)
    - [Ego Model](./7-iFay-Profile#ego-model)
    - [Faying Thinking](./7-iFay-Profile#faying-thinking)
        1. [Content](./7-iFay-Profile#content)
        2. [Data](./7-iFay-Profile#data)
        3. [Knowledge Base](./7-iFay-Profile#knowledge-base)
        4. [Info Feed](./7-iFay-Profile#info-feed)
    - [Faying Skills](./7-iFay-Profile#faying-skills)
        1. [API](./7-iFay-Profile#api)
        2. [Workflow](./7-iFay-Profile#workflow)
        3. [Bot](./7-iFay-Profile#bot)
        4. [Agent](./7-iFay-Profile#agent)
        5. [APP](./7-iFay-Profile#app)
        6. [Microservice](./7-iFay-Profile#microservice)
    - [Faying Hardware](./7-iFay-Profile#faying-hardware)
        1. [Device](./7-iFay-Profile#device)
        2. [Storage](./7-iFay-Profile#storage)
        3. [Computing](./7-iFay-Profile#computing)
    - [Faying Permissions](./7-iFay-Profile#faying-permissions)
        1. [SSO](./7-iFay-Profile#sso)
        2. [OAuth](./7-iFay-Profile#oauth)
        3. [Fingerprint](./7-iFay-Profile#fingerprint)

---

5. [FayManifest Declarative Assembly](./13-FayManifest)

    FayManifest is iFay's "package.json" — developers only need to list the required components, protocols, control modes, and driver configurations in a single JSON declaration file, and the FayGer runtime automatically resolves dependencies and assembles the iFay instance. You can build a dedicated iFay from scratch in a weekend.

---

6. [iFACTS Conformance Verification](./14-iFACTS)

    iFACTS (iFay Architecture Conformance Test Suite) is a standardized conformance test suite covering key specification points including protocol interactions, module interfaces, and security behaviors. Vendor implementations must pass iFACTS tests to claim "iFay Ready," with tests divided into four levels: L1 Single Component Conformance, L2 Interface Conformance, L3 Integration Conformance, L4 Behavioral Conformance.

---

7. [Guardianship and Personality Continuity](./15-Guardianship)

    iFay is the digital vessel of personality. When the Human Prime can no longer manage iFay, a guardian can take over management rights through mnemonic phrases or pre-specified identity authentication; after the Human Prime passes away, iFay can continue to exist as an independent identity in a Digital Cemetery sandbox — personality endures.

---

8. Case Studies

    We will provide a series of case studies demonstrating how iFay is created and how systems interface with iFay.
