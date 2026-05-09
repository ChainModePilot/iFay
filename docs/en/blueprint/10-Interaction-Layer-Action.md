# 10. Interaction Layer — Action

The Interaction Layer's Action subsystem is iFay's "effectors" — it lets iFay operate interfaces like a human, invoke services, and act proactively, transforming perception and cognition into actual behavior.

---

## 10.1 Simulated Operation

### One-Line Definition

Simulated Operation is iFay's **hands** — it can click, drag, scroll, and type like a human, operating any existing software interface without the software needing any AI-specific modifications.

### Why It's Needed

Imagine you've hired a new assistant and want them to handle various tasks on your computer and phone. But the problem is: the software you use — bank websites, insurance systems, government service platforms — are all designed for humans, and none provide an "AI-only entrance."

What to do? The most direct approach: **have the assistant operate these software applications just like you would**. See a button, click it. See a form, fill it in. See a page, scroll it.

That's the significance of Simulated Operation. It lets iFay help you get things done **right now**, without waiting for every piece of software in the world to be redesigned for AI.

But Simulated Operation is fundamentally different from traditional "automation scripts" (like RPA). RPA is like an actor who can only recite memorized lines — it follows a pre-written script step by step, and gets stuck if the interface changes slightly. iFay's Simulated Operation is **perception-driven**: it "sees" the screen through the First-person Tracer, understands the current interface state, then decides what to do next. Just like a real human user — even if a website gets redesigned, you can intuitively find the new button location.

### Its Position in the Architecture

```
iFay Four-Layer Architecture
├── Social Layer
├── Interaction Layer          ← Simulated Operation is here
│   ├── Perception (Sense)
│   │   ├── First-person Tracer   ← Eyes: sees what's on screen
│   │   ├── Sensor                ← Nervous system: perceives environment
│   │   └── Self-awareness        ← Heart: reads your intent
│   └── Action
│       ├── 👉 Simulated Operation ← Hands: click, drag, type
│       ├── Invoke Skill           ← Mouth: directly "calls" services
│       └── Self-driven Behavior   ← Will: decides when to act
├── Cognition Layer
└── Ego Layer
```

Simulated Operation sits in the **Interaction Layer's Action subsystem**, one of three ways iFay interacts with the external world. Its relationship with the First-person Tracer is the closest — the Tracer is the "eyes," Simulated Operation is the "hands," and together they achieve **hand-eye coordination**.

This is like when you use a mouse — your eyes are always watching the screen for changes, and your hand adjusts based on what your eyes see. iFay works the same way: after every operation, the Tracer observes interface changes, then Simulated Operation decides the next step based on those observations.

### How It Works

The core workflow can be summarized in three keywords: **Perceive, Operate, Feedback**.

**1. Perceive — Look First, Then Act**

Before performing any operation, iFay first "sees" the current interface through the First-person Tracer. It doesn't parse the webpage's HTML code — it **sees what's displayed on screen** like a human: where the buttons are, where the input fields are, where the dropdown menus are.

**2. Operate — Interact Like a Human**

iFay supports all operations humans can perform on interfaces:
- **Click**: Left-click buttons, right-click to open menus
- **Drag**: Drag files, resize windows
- **Scroll**: Scroll pages up and down to view more content
- **Type**: Enter text in input fields
- **Edge Gestures**: Swipe from screen edges to invoke sidebars
- **Multi-finger Gestures**: Two-finger zoom, three-finger app switching

**3. Feedback — Check Results After Each Action**

After every operation, iFay re-"looks" at the interface through the First-person Tracer to confirm whether the operation succeeded. If a button was clicked but the page didn't change, iFay realizes "this button might not have responded" and tries another approach.

This "operate → observe → adjust" loop is the fundamental difference between Simulated Operation and RPA scripts. RPA is a blind person feeling an elephant — executing scripts regardless of results. iFay works with eyes open — seeing, thinking, and adjusting at every step.

**What About Unfamiliar Interfaces?**

When iFay encounters an interface it's never seen before, it **explores** like a human: tries clicking a button to see what happens, hovers the mouse over an icon to check for tooltip text, scrolls the page to see what's below. Through this exploration, iFay gradually understands the interface's structure and functionality.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **First-person Tracer** | Simulated Operation's "eyes" — perceives interface state before and after each operation | Hands ↔ Eyes (hand-eye coordination) |
| **Invoke Skill** | Both in the Action subsystem, but different approaches: Simulated Operation works through interfaces, Invoke Skill calls APIs directly | Operating by hand vs. making a phone call |
| **Self-driven Behavior** | Self-driven Behavior decides "when to act," Simulated Operation handles "how to act" | Will decides action → hands execute |
| **Ego Model** | Ego constrains Simulated Operation's behavioral style (e.g., operation speed, caution level) | Personality influences how things are done |
| **Credentials Management** | Simulated Operation needs credentials from Credentials Management when logging in | Hands take keys to open doors |

### Scenario Stories

#### Scenario 1: Filling Out a Complex Insurance Claim Form

You had a minor car accident and need to fill out a claim on the insurance company's outdated website. The site was probably designed a decade ago — the form has 30+ fields spread across 5 pages, with various dropdown menus and date pickers.

You tell iFay: "Help me fill out the car insurance claim — the one last Wednesday afternoon at the intersection of Zhongshan Road and Jianshe Road."

iFay gets to work:
1. "Sees" the insurance company website's login page through the First-person Tracer, logs in with your delegated credentials
2. Finds the "Claim Application" entry and clicks in
3. Sees the first page form: accident date, location, type… iFay extracts information from your description and Personal Data Heap, filling in each field
4. Encounters a "Upload Accident Photos" button — iFay clicks it, finds your scene photos in the file picker, and uploads them
5. On the third page, discovers a dropdown menu with options different from expected (the site may have been updated) — iFay doesn't get stuck; instead, it carefully reads each option's text and selects the best match
6. On the final confirmation page, iFay reviews each filled item, confirms everything is correct, and clicks "Submit"

Throughout the process, iFay isn't executing a pre-written script — it's working like a skilled assistant, **watching the screen, understanding content, making judgments**. Even if this website gets redesigned tomorrow, iFay can still complete the task — because it operates by "seeing," not by "memorizing."

#### Scenario 2: Ordering Takeout on a Phone, Adapting to App Updates

You say: "Order me the same thing from last time on Meituan — the braised chicken rice, deliver to the office."

iFay opens the Meituan app but finds the interface looks different — the app just updated, the homepage layout changed, and the search bar moved.

If this were an RPA script, it would error out and stop. But iFay doesn't:
1. Scans the new homepage layout through the First-person Tracer, finds the search icon moved to the upper right
2. Clicks the search icon, types "braised chicken rice"
3. In the search results, visually identifies the restaurant you ordered from last time (matching store name and logo)
4. Enters the store page, finds the menu has been rearranged — iFay scrolls through the menu and finds "Braised Chicken Rice"
5. Clicks to add to cart, confirms the delivery address is your office
6. Completes the order

iFay demonstrated **adaptive exploration** throughout: it doesn't depend on fixed interface layouts but understands the current interface through visual perception and flexibly adjusts its operation strategy. This is the essential difference between "perception-driven" and "script-driven."

### For Developers

Simulated Operation belongs to **Phase 1 (Simulating Human Operations)** as a core module.

- **Requirement ID**: Requirement 5 (Simulated Operation)
- **Interface Specification**: `SimulatedOperation` interface with three core methods: `execute()`, `explore()`, and `getPostActionState()`
- **Supported Operation Types**: `click`, `drag`, `scroll`, `gesture` (edge and multi-finger gestures), `type`
- **Related Modules**: First-person Tracer (`FirstPersonTracer`) provides visual feedback; Credentials Management (`CredentialManager`) provides login credentials
- **Core Design**: Perception-driven, not script-driven; after each operation, perceives state changes through the Tracer, forming an "operate → perceive → adjust" closed loop; supports adaptive exploration of unknown interfaces
- **Conformance Testing**: iFACTS L1 verifies execution capability for each operation type; L2 verifies hand-eye coordination interface with First-person Tracer
- **iFay Ready Relevance**: Bronze certification requires applications to support iFay operation through Simulated Operation

---

## 10.2 Invoke Skill

### One-Line Definition

Invoke Skill is iFay's **mouth and telephone** — if Simulated Operation is iFay using its hands to operate interfaces, Invoke Skill is iFay directly "calling" a service — no interface needed, directly calling APIs or triggering tasks.

### Why It's Needed

Imagine you need to translate a document. You have two options:

**Option 1**: Open a browser, go to a translation website, paste the text, wait for translation, copy the result. This is the "Simulated Operation" approach — operating through the interface step by step.

**Option 2**: Directly call the translation company's phone, say "translate this passage for me," and they tell you the result directly. No website to open, no interface to operate. This is the "Invoke Skill" approach — **directly calling the service**.

Why is the second option needed? Because in many cases, operating an interface is an unnecessary intermediary. What you really want isn't "open a translation website" but "translate this passage into English." Invoke Skill lets iFay skip the interface and directly accomplish your goal.

This is like division of labor in human society: you don't need to personally go to the bakery and knead dough (operate the interface) — you just make a phone call saying "deliver a loaf of bread" (invoke a skill). Invoke Skill enables iFay to efficiently leverage all registered services — APIs, workflows, Bots, Agents, Apps, microservices — like an assistant who's great at getting things done over the phone.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Registered Skill** | Invoke Skill can only call registered skills; registration is the prerequisite for invocation | Must have a license before practicing |
| **Simulated Operation** | Both in the Action subsystem, but different approaches: Invoke Skill calls directly, Simulated Operation operates through interfaces | Making a phone call vs. going in person |
| **Self-driven Behavior** | Self-driven Behavior decides "what to do," Invoke Skill handles "calling to do it" | Will → mouth |

### For Developers

Invoke Skill belongs to **Phase 2 (Direct Client Takeover)** as a core module.

- **Requirement ID**: Requirement 6 (Invoke Skill)
- **Interface Specification**: `InvokeSkillService` interface
- **Conformance Testing**: iFACTS L1 verifies intent matching and skill invocation capability; L2 verifies interface integration with Registered Skill module; L3 verifies the complete "intent expression → skill invocation → contribution recording" chain

---

## 10.3 Self-driven Behavior

### One-Line Definition

Self-driven Behavior is iFay's **autonomous will** — Simulated Operation is the hands, Invoke Skill is the mouth, and Self-driven Behavior is iFay deciding on its own "when to act and when to speak." It transforms iFay from a passive executor into a proactive actor.

### Why It's Needed

Imagine you have an excellent assistant. If this assistant only acts when you give commands, then you still have to think of everything and give every instruction yourself — this doesn't truly lighten your burden, it just changes "doing it yourself" to "telling someone to do it."

What does a truly good assistant look like? They **proactively** do things:
- Automatically prepare your weekly work summary every Monday morning (**scheduled task**)
- Notice you frowning and sighing, and proactively ask if you've run into difficulties (**acting after reading the room**)
- You once said "check the logistics every time I get a delivery notification," and they always remember to do it automatically (**continuously executing habits**)

That's the significance of Self-driven Behavior. It gives iFay "autonomous will" — no longer just waiting for you to speak, but judging on its own when to do what, then proactively doing it.

But there's an important safety mechanism: if something iFay does autonomously turns out wrong, it **pauses and asks you**. Like a good assistant who proactively helps but checks with you when uncertain, rather than going all the way on their own judgment.

### How It Works

Self-driven Behavior has **three trigger types**, like three reasons humans proactively do things:

**1. Scheduled Tasks — Do It When the Time Comes**

The simplest trigger, like an alarm you set. You tell iFay: "Generate last week's work report every Monday morning at 9 AM." iFay will execute this task punctually every Monday morning.

**2. Self-awareness Inference — Sense You Need Something, Proactively Do It**

The most "intelligent" trigger. iFay observes your state and environment through the Self-awareness module, infers what you might need, then proactively acts.

For example: iFay discovers through sensor data that your fridge is running low on ingredients (smart fridge sensor data), combines this with your recent eating habits, and proactively orders groceries for you. You never said "buy groceries," but iFay judged on its own that "it's time to restock."

**3. Persistent Skills — Habits Running Continuously in the Background**

Some skills aren't one-time — they run continuously. For example, you tell iFay "monitor this stock and alert me if it drops below 50." This task runs continuously in the background until the condition triggers.

These persistent skills come from two sources: **Registered Skills** (continuous monitoring capabilities from external services) and **Internal Skills** (iFay's own inherent capabilities).

**The Action → Feedback → Re-action Loop**

Regardless of trigger type, Self-driven Behavior follows a core loop:

1. **Action**: iFay executes an autonomously decided task
2. **Feedback**: Observes execution results, judges whether they meet expectations
3. **Re-action**: If results meet expectations, continue to the next step; if not, adjust strategy or pause to ask

This loop ensures iFay's autonomous behavior isn't "charging ahead blindly" but continuously self-correcting.

**Safety Valve: Pause and Confirm**

When iFay finds that autonomous behavior results are inconsistent with your intent, it **pauses all subsequent autonomous actions** and asks you: "I just did XX for you, but the result doesn't seem right. Do you want to continue?" This mechanism ensures iFay's autonomy doesn't go out of control.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Self-awareness** | Self-awareness infers Human Prime's intent, triggering Self-driven Behavior | Inner feelings → drive action |
| **Simulated Operation** | Self-driven Behavior decides "what to do," Simulated Operation handles "doing it by hand" | Will → hands |
| **Invoke Skill** | Self-driven Behavior decides "what to do," Invoke Skill handles "doing it by phone" | Will → mouth |
| **Registered Skill** | Persistent skills are one trigger source for Self-driven Behavior | Long-term habits drive action |
| **Internal Skill** | Internal skills are another trigger source | Instinct drives action |
| **Aligned Consciousness** | Aligned Consciousness provides Human Prime profile, helping Self-driven Behavior judge "should I do this" | Understanding of you determines action boundaries |

### Scenario Stories

#### Scenario 1: Auto-generating Weekly Report Every Monday (Scheduled Task Trigger)

Monday morning 8:55, you're still on the subway. iFay's scheduled task triggers:

1. iFay automatically extracts last week's work data from your Personal Data Heap — emails, calendar, task completion in project management tools, code commit records
2. Through Invoke Skill, calls a document generation API to organize this data into a well-structured weekly report
3. After generation, iFay checks if the content is reasonable (e.g., any important projects missing)
4. At 9:00 sharp, you arrive at the office, open your computer, and find iFay has placed the weekly report on your desktop with a note: "You spent the most time on Project A last week. Project B has two delayed tasks — want me to help adjust this week's plan?"

You never said "write my weekly report" — this was automatically completed by iFay according to the scheduled task you previously set. And it didn't just mechanically aggregate data — it proactively offered suggestions.

#### Scenario 2: Proactively Restocking Groceries (Self-awareness Trigger)

Wednesday evening, iFay discovers through your smart fridge's sensor data: only one carton of milk left, 3 eggs remaining, vegetable compartment nearly empty.

iFay combines the following information to make a judgment:
- Your eating habits (recorded in Aligned Consciousness: you drink milk every morning, use about 12 eggs per week)
- Your recent shopping records (data in Personal Data Heap: last grocery run was 5 days ago)
- Current time (Wednesday evening — if you don't restock, you might run out by the weekend)

iFay proactively acts:
1. Generates a shopping list: 2 cartons of milk, 1 box of eggs, your usual vegetables
2. Through Invoke Skill, calls the fresh delivery app's API to place an order
3. Before ordering, iFay pauses — because the total exceeds your usual single-purchase budget. It asks: "The fridge is running low. I've made a shopping list — 186 yuan total, a bit more than usual because I added the organic vegetables you mentioned wanting to try last week. Should I place the order?"
4. You reply "Sure," iFay completes the order

Notice the "pause and confirm" step — iFay found the amount exceeded your regular budget (result not fully consistent with Human Prime's habits), so it didn't order directly but asked first. This is the Self-driven Behavior safety mechanism at work.

### For Developers

Self-driven Behavior belongs to **Phase 4 (iFay + coFay Full Personification)** as a core module.

- **Requirement ID**: Requirement 14 (Self-driven Behavior)
- **Interface Specification**: `SelfDrivenBehavior` interface with four core methods: `scheduleTask()` (scheduled task), `handleInference()` (handle self-awareness inference), `pauseAndConfirm()` (pause and confirm), and `getLoopStatus()` (loop status)
- **Three Trigger Sources**: `scheduled` (scheduled task), `self_awareness` (self-awareness inference), `registered_skill` / `internal_skill` (persistent skills)
- **Core Mechanism**: Continuous action → feedback → re-action loop; pauses and requests confirmation when execution results are inconsistent with Human Prime's intent
- **Related Modules**: Self-awareness (`SelfAwareness`) provides intent inference; Simulated Operation and Invoke Skill handle actual execution; Aligned Consciousness (`AlignedConsciousness`) provides behavioral constraint baseline
- **Conformance Testing**: iFACTS L1 verifies responsiveness to three trigger sources; L2 verifies interface with Self-awareness module; L4 verifies safety constraints of autonomous behavior (pause-and-confirm mechanism)
