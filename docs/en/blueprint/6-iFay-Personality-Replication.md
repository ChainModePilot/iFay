# 6. iFay Is a Replication of Human Personality

iFay's personality is not generated from thin air — it is instantiated from the Human Prime (Prime). Every iFay is a personality extension of its Human Prime, and this extension requires a structured injection process.

This page describes how the Human Prime injects their own traits into iFay from three dimensions: **personality** shapes the Ego model, **data** populates the Personal Data Heap, and **permissions** establish credential delegation. All three dimensions are indispensable — personality lets iFay know "who I am," data gives iFay "my past," and permissions enable iFay to "act on my behalf."

---

## Prime Personality (→ Ego Model)

The Prime's personality is the training and configuration input for the Ego model. The Ego model is iFay's embedded micro-model that constrains iFay to align with the Human Prime across dimensions such as value orientation, interest preferences, habits, cognitive boundaries, skill boundaries, permission boundaries, and working style.

### Three Injection Methods

| Method | Description |
|--------|-------------|
| **Conversational Narration** | The Human Prime engages in guided dialogue with iFay. iFay uses a standard research questionnaire to constrain conversation topics, ensuring effective personality data is collected. This isn't casual chat — each round of conversation focuses on a specific personality dimension. |
| **Questionnaire Completion** | The Human Prime directly fills out a structured personality questionnaire, and the system converts answers into training parameters for the Ego model. |
| **Direct Configuration** | Advanced users can directly edit the Ego model's constraint parameters, precisely controlling iFay's behavioral boundaries. |

### Multi-Version Ego

People are multifaceted. You're rigorous and focused at work, relaxed and humorous with friends, gentle and patient with family. The Ego model supports multiple versions, each corresponding to a facet of the Prime's personality. Only one Ego version is active at any given moment, supporting both manual switching and context-based automatic switching.

### Scenario

> Isabel just activated her iFay. The system guides her into a conversation — not casual chat, but guided exchange designed around a standard research questionnaire.
>
> "When you receive a vaguely worded work email, do you tend to reply directly for clarification, or privately reach out to the person first?"
>
> Isabel chose the latter, adding that she prefers resolving potential misunderstandings in informal settings. iFay records this preference, encoding it as a parameter in the "communication style" dimension of the Ego model.
>
> Twenty minutes later, Isabel's iFay has a preliminary understanding of her communication preferences, decision-making style, and risk attitude. These traits will become the behavioral guidelines when iFay handles daily affairs on her behalf.

---

## Prime Data (→ Personal Data Heap)

Data is iFay's "memory." An iFay without data is like a person with amnesia — knows who they are, but can't remember what they've experienced. The Personal Data Heap is the component that uniformly manages all of iFay's private data, and Prime data is its initialization input.

### Four Data Types

| Type | Description | Examples |
|------|-------------|----------|
| **Content** | Structured or unstructured content assets | Photos, videos, articles, creative works |
| **Data** | Personal data | App usage records, health data, spending records |
| **Knowledge Base** | Organized knowledge systems | Professional notes, study materials, work documents |
| **Info Feed** | Real-time information subscriptions | News sources, industry updates, social media follows |

### Three Injection Methods

1. **Authorize Prime Data**: Authorize iFay to access the Human Prime's photos, app data, communication records, etc. The system integrates tightly with the OS layer, supporting reading of system information and other apps' private data under system supervision.
2. **Import Files**: Import documents, notes, chat logs, and other long-term memory files.
3. **Specify Information Sources**: Specify books, information sources, and knowledge bases for iFay to continuously acquire information from.

All data is stored in standard format in the Personal Data Heap, accessible only by iFay directly. This is a one-time initialization operation, but supports long-term growth — iFay continuously accumulates new data as the Human Prime lives their life.

### Scenario

> Chen Ming decided to hand over his past decade of digital life to his iFay.
>
> He first authorized iFay to access his phone's photo album — over 30,000 photos and videos recording every important moment from college graduation to his child's birth. Then he imported chat logs, work email archives, and his notebook.
>
> After iFay processed this data, it not only knew where Chen Ming traveled last year, but understood his social circle, work rhythm, and life habits. When Chen Ming's colleague asked about the name of the restaurant from the last team outing, iFay could find the answer in seconds from photo geotags and chat records — just as if Chen Ming had recalled it himself.

---

## Prime Permissions (→ Credential Delegation)

Permissions determine what iFay can "do on your behalf." An iFay without permissions is like a butler without keys — knows what to do, but can't open any doors.

### Three Permission Sources

iFay's permissions come from three sources, with no containment relationship between them:

| Source | Description | Examples |
|--------|-------------|----------|
| **Direct Prime Authorization** | The Human Prime delegates existing credentials to iFay | Delegating Netflix account, bank query permissions |
| **Prime Permission Exchange** | Derived permissions exchanged from the Prime's permissions | API access rights exchanged from the Prime's enterprise account |
| **iFay Self-Acquired** | Independent permissions iFay obtains through its own actions | API access earned through GMChain contributions, trust credentials built in the Fay social network |

### No Containment Relationship

A key design: there is **no containment relationship** between Prime permissions and iFay permissions. iFay can possess permissions the Human Prime doesn't have (e.g., API access earned through contributions), and the Human Prime can possess permissions not delegated to iFay (e.g., the Prime's private bank account).

### Seven Credential Types

iFay supports managing seven credential types: FayID, account passwords, certificates, authorizations, access tokens, smart contracts, and digital tokens (MeriToken). When the Human Prime delegates credentials, original credentials are exchanged for corresponding copy credentials, and iFay uses copies for login and authentication, ensuring the safety of original credentials.

### Scenario

> Li Wei delegated her Netflix account to iFay — this is **direct Prime authorization**. What iFay received was not Li Wei's original password, but a corresponding copy credential. Now iFay can automatically manage her playlists based on Li Wei's viewing preferences.
>
> Meanwhile, Li Wei's iFay has been providing information assembly services to other Fays through GMChain, accumulating considerable MeriTokens. With these contributions, iFay gained access to a premium weather data API — this is a permission **iFay self-acquired**, which Li Wei herself doesn't have access to.
>
> But Li Wei's private investment account — she chose not to delegate it to iFay. That's perfectly fine — the permission boundaries of Human Prime and iFay are independent.

---

### Related Documents

- [Aligned Consciousness](./11.3-Aligned-Consciousness) — Aligned Consciousness
- [Personal Data Heap](./11.1-Personal-Data-Heap) — Personal Data Heap
- [Credentials Management](./8.1-Credentials-Management) — Credentials Management
- [iFay Profile](./7-iFay-Profile) — iFay Profile
