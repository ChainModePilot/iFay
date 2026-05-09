# 11. Cognition Layer — Thinking

The Cognition Layer's Thinking subsystem is iFay's "memory and understanding center" — it manages iFay's memory, acquires external knowledge, and maintains a deep understanding of you, providing the cognitive foundation for all behavior.

---

## 11.1 Personal Data Heap

### One-Line Definition

The Personal Data Heap is iFay's **memory** — your photos, chat logs, work documents, health data… scattered across phones, computers, and cloud drives. The Personal Data Heap unifies their management, allowing iFay to "recall" any moment from the past at any time.

### Why It's Needed

Think about how your own memory works. Your brain doesn't store "visual memories" in one place, "auditory memories" in another, and "emotional memories" in a third — when you recall a trip, images, sounds, and feelings all come flooding back together. Your brain **manages all this information in a unified way**, letting you naturally "remember" any experience.

But your digital life is nothing like this. Your photos are in your phone's gallery, work documents on your computer's hard drive, chat logs in messaging apps, health data in your smartwatch's app, and cloud drives hold a bunch more files… This data is scattered across a dozen different places, in different formats, with no connection between them.

If iFay is to become your digital avatar, it must be able to "remember" everything about you — but it can't require you to move all your data to one place. The Personal Data Heap's solution is: **data stays where it is, but iFay reads and writes it all through a unified interface**. Just like your brain doesn't care which neurons store a particular memory — it just needs to be able to "recall" it.

The Personal Data Heap is iFay's memory system. It gives iFay a complete, searchable, ever-growing "life memory."

### How It Works

The Personal Data Heap's operation can be summarized in four keywords: **Unified, Classified, Persistent, Enriched**.

**1. Unified — One interface for all data**

Your photos might be on iCloud, documents on Google Drive, chat logs on your local phone, and health data in your smartwatch's cloud. The Personal Data Heap doesn't move all this data to one place — instead, it provides a **unified read/write interface**. Other iFay modules just need to say "I want to find photos taken in Hangzhou three years ago," and the Personal Data Heap automatically goes to the corresponding storage location to find them.

**2. Classified — Four data types**

The Personal Data Heap manages four types of data:
- **Content**: Things you create — photos, videos, articles, notes, code
- **Data**: Structured information — health data, financial records, location history, sensor data
- **Knowledge Base**: Organized knowledge — your professional notes, study materials, work experience summaries
- **Info Feed**: Continuously updated information — news subscriptions, social media feeds, email notifications

**3. Persistent — Secure data custody**

Through **DTP (Data Tunnel Protocol)**, the Personal Data Heap handles persistent storage and custody of data. "Custody" means more than just storage — it also means protection: ensuring data isn't lost, isn't accessed without authorization, and can be fully recovered when needed.

**4. Enriched — Making raw data more valuable**

The Personal Data Heap doesn't just passively store data — it can also perform **enrichment and personalization** on data. For example:
- Your health data is a bunch of numbers (heart rate 72, blood pressure 120/80, steps 8000). The Personal Data Heap can correlate them to generate insights like "your overall health today is good, and you exercised 20% more than yesterday"
- Your photos aren't just image files. The Personal Data Heap can add semantic tags — "family photo at West Lake, Hangzhou, summer 2022"

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Sensor** | Environmental data collected by sensors is stored in the Personal Data Heap | Sensory signals → memory storage |
| **External Knowledge** | Information acquired by External Knowledge is integrated into the Personal Data Heap | Knowledge learned from the library → becomes your own memory |
| **Aligned Consciousness** | Aligned Consciousness mines data from the Personal Data Heap to build the Human Prime profile | Summarizing "what kind of person I am" from memories |
| **Self-driven Behavior** | Self-driven Behavior retrieves information from the Personal Data Heap to decide whether proactive action is needed | Deciding "what should I do now" based on memory |
| **DTP Protocol** | Data is transmitted bidirectionally between terminals and the Personal Data Heap via DTP | Input and output channels for memory |

### Scenario Stories

#### Scenario 1: Finding a Restaurant You Visited Three Years Ago

On the weekend, you want to take a friend to a restaurant. You remember going once three years ago — the food was great — but you've forgotten the name and address. All you remember is "it was probably in Hangzhou, we had Hangzhou cuisine, and I think I went with colleagues."

You tell iFay: "Help me find that Hangzhou cuisine restaurant I went to three years ago."

iFay begins searching the Personal Data Heap:
1. First checks **location history** (Data type): your activity trail in Hangzhou three years ago, filtering for locations where you lingered in dining areas
2. Then checks **photos** (Content type): photos you took during that period, finding several food photos from a restaurant
3. Then checks **chat logs** (Content type): discovers you sent a message in your colleagues' group chat saying "the Hangzhou cuisine today was amazing," with the restaurant's location attached
4. Finally cross-validates: location data, photos, and chat logs all point to the same restaurant — "Hangzhou Flavor · West Lake Branch"

iFay tells you: "Found it — it's 'Hangzhou Flavor · West Lake Branch,' at XX Road, West Lake District. You went with colleagues on June 15 three years ago. You took three food photos and recommended it in the group chat. Want me to make a reservation?"

#### Scenario 2: Enriched Insights from Health Data

You wear a smartwatch every day that continuously records your heart rate, sleep, steps, blood oxygen, and more. This raw data is stored in the Personal Data Heap (Data type).

One day, after performing enrichment processing on this data, iFay gives you an insight:

"Over the past two weeks, your average sleep time has dropped from 7.5 hours to 6.2 hours, and your deep sleep ratio has fallen from 22% to 15%. Meanwhile, your resting heart rate has risen from 68 to 74. I notice that during this period your calendar has many evening meetings (work schedule data from the Knowledge Base), and you've frequently been putting down your phone after 1 AM (usage habit data)."

"Suggestion: you might need to adjust your routine. Would you like me to reschedule all meetings after 10 PM to the next day?"

### For Developers

The Personal Data Heap belongs to **Phase 2 (Direct Client Takeover)** as a core module.

- **Requirement ID**: Requirement 11 (Personal Data Heap)
- **Interface Specification**: `PersonalDataHeap` interface with four core methods: `read()` (unified read), `write()` (unified write), `enrich()` (data enrichment), and `persist()` (persistent storage)
- **Four Data Types**: Content, Data, Knowledge Base, Info Feed
- **Supported Storage Locations**: Runtime memory (`runtime_memory`), cloud storage (`cloud`), vector database (`vector_db`), local storage (`local`)
- **Related Protocols**: DTP (Data Tunnel Protocol) for bidirectional data transmission and data custody between terminals and the Data Heap
- **Related Modules**: Sensor (`SensorModule`) provides environmental data; External Knowledge (`ExternalKnowledge`) provides external information; Aligned Consciousness (`AlignedConsciousness`) mines the Human Prime profile from the Data Heap
- **Conformance Testing**: iFACTS L1 validates read/write capabilities for all four data types; L2 validates data interfaces with Sensor and External Knowledge modules; L3 validates the complete "data collection → storage → enrichment → retrieval" chain
- **Design Points**: Unified read/write interface abstracts away underlying storage differences; supports semantic queries (`semanticQuery`); data enrichment and personalization processing

---

## 11.2 External Knowledge

### One-Line Definition

External Knowledge is iFay's **library and expert consultant** — the Personal Data Heap is iFay's own memory, while External Knowledge is the library iFay can consult and the experts it can ask. It gives iFay knowledge beyond the Human Prime's own capabilities.

### Why It's Needed

No matter how good your memory is, you can't remember everything. When you encounter a problem you don't understand, what do you do? You go to the library to look things up, or consult a professional.

For example, you receive a health checkup report that says "triglycerides 2.8 mmol/L." Do you know what that means? Most people don't. What you need at that point isn't "recall" (Personal Data Heap), but "lookup" — checking a medical knowledge base, or asking a doctor.

iFay works the same way. The Personal Data Heap stores your own data and memories, but your knowledge is limited. The External Knowledge module lets iFay **step beyond its own memory** to consult external knowledge bases and query external intelligent models — just like a person walking into a library or calling an expert.

This means iFay's capabilities are no longer limited to "what you know," but extend to "what knowledge in the world can help you."

### How It Works

External Knowledge's operation can be summarized in three keywords: **Connect, Query, Integrate**.

**1. Connect — Linking to external knowledge sources**

External knowledge sources come in many varieties:
- **Knowledge Bases**: Medical knowledge bases, legal knowledge bases, encyclopedias
- **Large Language Models**: GPT, Claude, and other general AI models
- **Expert Systems**: Specialized reasoning systems for specific domains
- **Search Engines**: Public information on the internet

These knowledge sources connect to iFay through **SSP (Skill Sharing Protocol)**. SSP is a standardized protocol that opens services and interfaces — originally available only to specific clients — to the entire network.

**2. Query — Asking questions like consulting an expert**

When iFay needs external knowledge, it sends a query request to the corresponding knowledge source. Each query result comes with a **confidence score** — telling iFay how reliable the answer is. iFay can synthesize answers from multiple knowledge sources and select the most reliable information.

**3. Integrate — Learned knowledge becomes your own**

Information acquired from external knowledge sources isn't just "use and discard." Important knowledge gets integrated into the Personal Data Heap, becoming part of iFay's own memory. Next time a similar question arises, iFay can find the answer directly from its own memory without querying external knowledge sources again.

**What if a knowledge source is unavailable?**

The network might disconnect, or a knowledge source might go offline. In that case, the External Knowledge module **falls back to cached knowledge in the Personal Data Heap**. Meanwhile, iFay notifies the Cognition Layer that "currently using cached knowledge, which may not be the latest."

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Personal Data Heap** | Information acquired by External Knowledge is integrated into the Personal Data Heap | Knowledge learned from the library → written in your notebook |
| **Registered Skill** | External knowledge sources are registered and managed as a skill type | A library card is also a type of "skill credential" |
| **Aligned Consciousness** | Aligned Consciousness helps filter external knowledge relevant to the Human Prime | Your interests determine what books you borrow from the library |
| **Internal Skill** | Internal Skill checks whether external knowledge conflicts with the Human Prime's intent | Using your own judgment to evaluate the credibility of external information |
| **SSP Protocol** | External knowledge sources connect through the standardized SSP protocol | The library's unified borrowing rules |

### Scenario Stories

#### Scenario 1: Helping You Understand a Health Checkup Report

You receive your annual health checkup report, full of incomprehensible indicators: triglycerides 2.8 mmol/L, LDL cholesterol 3.9 mmol/L, uric acid 480 μmol/L…

You tell iFay: "Help me look at this checkup report — is there anything I should be concerned about?"

iFay gets to work:
1. First retrieves your past three years of checkup data from the Personal Data Heap (its own memory)
2. Then queries an external **medical knowledge base** (the library): what's the normal range for each indicator? What does exceeding it mean?
3. After comprehensive analysis, tells you:

"Your triglycerides are elevated (normal should be below 1.7, yours is 2.8), and your LDL cholesterol is also high (normal should be below 3.4, yours is 3.9). Both indicators have risen compared to last year. Combined with your dining records from the past three months (data from the Personal Data Heap), your takeout ordering frequency has noticeably increased, with a preference for high-oil, high-salt foods."

"I suggest you pay attention to your blood lipid health and consider adjusting your diet. Would you like me to book a cardiology appointment for you?"

#### Scenario 2: Helping You Draft Contract Clauses

You're a small business owner who needs to sign a procurement contract with a supplier. You're not very familiar with contract law, but you don't want to pay for a lawyer every time.

You tell iFay: "Help me draft a breach clause for a procurement contract — if the supplier delays delivery by more than 15 days, we have the right to terminate the contract."

iFay gets to work:
1. Queries an external **legal knowledge base**: legal provisions and common formulations for procurement contract breach clauses
2. References contract templates you've previously signed from the Personal Data Heap (its own memory)
3. Synthesizes a draft breach clause including legal terminology and protective provisions

iFay presents the draft: "Here's a breach clause drafted based on relevant contract law provisions. I referenced standard templates from the legal knowledge base and incorporated the style from your previous contract with XX Company. Would you like to make any adjustments?"

At the same time, iFay reminds you: "This is a draft generated from the legal knowledge base. I recommend having a professional lawyer review it before formal signing."

### For Developers

External Knowledge belongs to **Phase 3 (iFay as Virtual World Interface)** as a core module.

- **Requirement ID**: Requirement 12 (External Knowledge Integration)
- **Interface Specification**: `ExternalKnowledge` interface with three core methods: `query()` (query external knowledge), `registerSource()` (register knowledge source), and `fallbackToCache()` (fall back to cache)
- **Knowledge Source Types**: `knowledge_base`, `llm` (Large Language Model), `expert_system`, `search_engine`
- **Related Protocols**: SSP (Skill Sharing Protocol) for standardized integration of external knowledge sources
- **Related Modules**: Personal Data Heap (`PersonalDataHeap`) integrates external knowledge; Registered Skill (`RegisteredSkillManager`) manages knowledge source registration; Internal Skill (`InternalSkill`) checks for knowledge conflicts
- **Fallback Strategy**: When external knowledge sources are unavailable, automatically falls back to cached knowledge in the Personal Data Heap and notifies the Cognition Layer
- **Conformance Testing**: iFACTS L1 validates knowledge query and cache fallback capabilities; L2 validates knowledge integration interface with Personal Data Heap; L3 validates the complete "knowledge query → integration → cache → fallback" chain

---

## 11.3 Aligned Consciousness

### One-Line Definition

Aligned Consciousness is iFay's **complete understanding of you** — if the Ego Model is iFay's "personality," Aligned Consciousness is iFay's deep cognition of you as a person — your values, preferences, habits, and boundaries. It is the baseline for all of iFay's behavior.

### Why It's Needed

Imagine you have an assistant who's been with you for ten years. The reason this assistant works so well isn't because of superior technical skills, but because they **know you so well**:

- They know you don't like meetings before 10 AM
- They know you're allergic to peanuts and automatically avoid them when ordering food
- They know you prefer data-driven decisions, so reports always include charts
- They know you're currently on a diet, so they won't proactively recommend desserts

This kind of "understanding" isn't written in a manual — it's accumulated through long-term interaction. It includes your values, preferences, habits, capability boundaries, and even behavioral patterns you're not aware of yourself.

Aligned Consciousness is iFay's version of this "complete understanding" of you. It maintains a **comprehensive profile** about you — not simple tags ("male, 30, programmer"), but a multi-dimensional, continuously updated, deeply ingrained understanding.

Why does this matter? Because every action iFay takes needs a "baseline" to judge: should this be done? How should it be done? To what extent? This baseline is the Human Prime profile provided by Aligned Consciousness. Without it, iFay is like a stranger who doesn't know you — no matter how technically capable, the results might still leave you unsatisfied.

### How It Works

The Human Prime profile maintained by Aligned Consciousness contains multiple dimensions: **value orientation, interest preferences, habit patterns, cognitive boundaries, skill boundaries, permission boundaries, and working style**. Together, these dimensions form a complete picture of "you."

This profile is established and updated through **three methods**:

**1. Data Mining — Understanding you from your data**

Aligned Consciousness mines behavioral patterns from the Personal Data Heap. For example:
- Analyzing your past year of food orders, discovering you haven't ordered meat dishes in the last three months → inferring you may have become vegetarian
- Analyzing your calendar data, discovering you never schedule work meetings on weekends → inferring you value work-life balance
- Analyzing your reading history, discovering you've been reading extensively about investing recently → inferring you've developed an interest in investing

This method is **passive and continuous** — iFay doesn't need to ask you; it gradually understands you by observing your data.

**2. Real-time Adjustment — Reading you from your reactions**

The Self-awareness module observes your reactions in real-time and passes observations to Aligned Consciousness. For example:
- iFay recommended a song, and you immediately skipped it → Aligned Consciousness updates: you don't like this style of music
- iFay wrote an email for you, and you heavily revised the wording → Aligned Consciousness updates: your email style is more formal than iFay expected
- iFay reminded you of a work task at 11 PM, and you showed irritation → Aligned Consciousness updates: you don't want to be disturbed by work late at night

This method is **active and immediate** — iFay learns from every one of your reactions, continuously fine-tuning its understanding of you.

**3. Manual Definition — You tell iFay directly**

Some preferences and boundaries you can tell iFay directly:
- "I don't want you to schedule any meetings before 10 AM"
- "I'm allergic to peanuts — keep that in mind when ordering food for me"
- "Use formal tone for work emails, casual is fine for personal messages"

This method is **explicit and immediate** — whatever you say, iFay records it, no inference needed.

The three methods complement each other: data mining provides long-term trends, real-time adjustment captures immediate changes, and manual definition sets explicit boundaries. Together, they make the profile maintained by Aligned Consciousness increasingly accurate and complete.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Personal Data Heap** | Aligned Consciousness mines data from the Personal Data Heap to build the Human Prime profile | Summarizing "what kind of person I am" from memories |
| **Self-awareness** | Self-awareness observes the Human Prime's reactions in real-time and passes them to Aligned Consciousness for profile updates | Reading facial expressions → updating understanding of you |
| **Ego Model** | Aligned Consciousness provides the Human Prime profile to the Ego Model as input for personality constraints | Understanding of you → shapes iFay's personality |
| **Internal Skill** | Aligned Consciousness provides behavioral constraint baselines for Internal Skill | Understanding of you → determines what can and can't be done |
| **Self-driven Behavior** | Aligned Consciousness helps Self-driven Behavior judge "should I proactively do this" | Knowing your boundaries → determines scope of action |

### Scenario Stories

#### Scenario 1: Discovering You've Become Vegetarian from Food Order Data

Over the past three months, iFay's Aligned Consciousness data mining function has analyzed your food order records in the Personal Data Heap:

- Three months ago: 70% of your takeout orders included meat dishes
- Two months ago: meat dish ratio dropped to 30%, with vegetarian options appearing frequently
- Last month: you haven't ordered any meat dishes at all, and you've followed several vegetarian bloggers on social media

Aligned Consciousness synthesizes this data and updates your profile: **dietary preference has shifted from omnivore to vegetarian**.

This update immediately affects iFay's behavior:
- When you say "order me some takeout," iFay recommends only vegetarian restaurants
- When iFay plans a trip for you, it specifically marks vegetarian-friendly restaurants near the destination
- When a friend invites you to dinner, iFay reminds you "this restaurant has limited vegetarian options — would you like to suggest somewhere else?"

You never explicitly told iFay "I'm vegetarian now," but iFay discovered this change through data mining on its own and automatically adjusted all related behaviors.

#### Scenario 2: You Directly Tell iFay a Rule

One morning, you're woken up by an 8 AM meeting. Somewhat annoyed, you tell iFay: "From now on, don't schedule any meetings for me before 10 AM."

iFay responds immediately: "Got it. All meetings will be scheduled after 10 AM from now on."

This is a **manual definition** — you directly tell iFay an explicit rule. Aligned Consciousness immediately updates your profile, adding this constraint to the "habit patterns" dimension.

The impact of this update is immediate:
- When someone tries to book you for a 9 AM meeting tomorrow through iFay, iFay responds: "XX isn't available before 10 AM. Would after 10 work?"
- When iFay's Self-driven Behavior wants to remind you of a work task at 8 AM, it checks Aligned Consciousness, finds the "no disturbance before 10" rule, and postpones the reminder to 10 AM
- Even scheduled tasks, if their execution time is before 10 AM, iFay will automatically delay them

A simple verbal instruction, transmitted through Aligned Consciousness, affects all of iFay's related behaviors. This is the role of Aligned Consciousness as a "behavioral baseline" — it doesn't directly execute any action, but it constrains all actions.

### For Developers

Aligned Consciousness belongs to **Phase 4 (iFay + coFay Full Personification)** as a core module.

- **Requirement ID**: Requirement 16 (Aligned Consciousness)
- **Interface Specification**: `AlignedConsciousness` interface with four core methods: `getProfile()` (get Human Prime profile), `mineFromDataHeap()` (data mining update), `adjustFromAwareness()` (real-time adjustment from Self-awareness), and `manualUpdate()` (Human Prime manually defines)
- **Human Prime Profile Dimensions**: Value orientation (`values`), preferences (`preferences`), habits (`habits`), cognitive boundaries (`cognitiveBoundaries`), skill boundaries (`skillBoundaries`), permission boundaries (`permissionBoundaries`), working style (`workingStyle`)
- **Three Update Methods**: Mining from Personal Data Heap (passive, continuous); real-time adjustment via Self-awareness (active, immediate); Human Prime manually defines (explicit, immediate)
- **Related Modules**: Personal Data Heap (`PersonalDataHeap`) provides data source; Self-awareness (`SelfAwareness`) provides real-time feedback; Ego Model (`EgoModel`) and Internal Skill (`InternalSkill`) consume profile data
- **Relationship with iFay Profile**: The Human Prime profile (`HostProfile`) is a subset and input source of iFay Profile. Profile is iFay's complete "identity card"; Aligned Consciousness is the "understanding of the Human Prime" portion within it
- **Conformance Testing**: iFACTS L1 validates three profile update methods; L2 validates profile delivery interfaces with Ego Model and Internal Skill; L4 validates the actual impact of profile updates on behavioral constraints
