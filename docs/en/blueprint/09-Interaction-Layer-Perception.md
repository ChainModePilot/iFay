# 9. Interaction Layer — Perception

The Interaction Layer's Perception subsystem is iFay's "senses" — it lets iFay see the screen, perceive the environment, and read your intent, providing information input for subsequent actions and cognition.

---

## 9.1 First-person Tracer

### One-Line Definition

The First-person Tracer is iFay's **eyes and ears** — it lets iFay see the images you see and hear the sounds you hear, giving it the exact same first-person perspective as you.

### Why It's Needed

Imagine you've hired an assistant to help you fill out a web form. If this assistant were blind — unable to see the input fields, buttons, and error messages on screen — how could they help?

That's what iFay would be without the First-person Tracer.

When humans operate computers and phones, they rely on eyes to see the screen and ears to hear notification sounds. iFay needs the same capabilities. The First-person Tracer is the module that gives iFay this ability — it lets iFay **see the screen like you do**, rather than reading code like a programmer.

There's a key distinction here: iFay sees what you **see with your naked eyes**, not the hidden code behind web pages (like HTML tags, SEO keywords — things you can't see at all). Just as when you read a book, you see text and images, not the printing plant's typesetting files. iFay works the same way — it prioritizes "visual" understanding of interfaces rather than parsing structured documents.

### Its Position in the Architecture

```
iFay Four-Layer Architecture
├── Social Layer
├── Interaction Layer          ← First-person Tracer is here
│   ├── Perception (Sense)
│   │   ├── 👉 First-person Tracer   ← Looks outward, sees the screen
│   │   ├── Sensor                   ← Perceives the environment
│   │   └── Self-awareness           ← Looks inward, reads you
│   └── Action
│       ├── Simulated Operation
│       ├── Invoke Skill
│       └── Self-driven Behavior
├── Cognition Layer
└── Ego Layer
```

The First-person Tracer sits in the **Interaction Layer's Perception subsystem**. If iFay were a person, the Interaction Layer would be the "body" through which iFay interacts with the external world, and the First-person Tracer would be the **eyes and ears** on that body.

### How It Works

The First-person Tracer works intuitively — just like you looking at a screen:

**1. Seeing the Display**
iFay captures what's currently displayed on your screen — text, images, buttons, input fields, pop-ups… everything you can see, iFay can see too.

**2. Hearing Sounds**
If the interface has notification sounds, voice announcements, or video audio, iFay can capture those as well.

**3. Real-time Change Tracking**
This is the most important part. When iFay performs an operation on screen (like clicking a button), it needs to **immediately see the result** — did the page navigate? Did an error message appear? Is the loading animation still spinning?

Just as after you click a "Submit" button with your mouse, your eyes automatically watch the screen for the result. iFay's First-person Tracer does the same thing:
- Tracks visual changes after cursor movement
- Tracks newly exposed areas after window switching
- Tracks dynamic page updates (like real-time refreshing data)

**4. Hand-Eye Coordination**
The First-person Tracer and the Simulated Operation module are tightly paired "partners" — like a person's eyes and hands. Eyes see where the button is, hands can click accurately; after clicking, eyes check the result. This "see → do → see again" loop is iFay's hand-eye coordination capability.

**5. Reporting "Can't See"**
If for some reason (screen locked, app crashed, insufficient permissions) the First-person Tracer can't capture the display, it won't pretend nothing happened — it honestly reports to iFay's Cognition Layer: "I can't see." The Cognition Layer then decides what to do next (wait, retry, or notify you).

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Simulated Operation** | Tightly coupled, hand-eye coordination | Eyes ↔ Hands |
| **Cognition Layer** | Reports perception status (normal/degraded/failed) | Eyes → Brain ("I can see" or "I can't see clearly") |
| **Sensor** | Both in the Perception subsystem, but different roles: Tracer sees the screen, Sensor perceives the environment | Eyes vs. nerves on the skin |
| **Self-awareness** | Both in the Perception subsystem, but different directions: Tracer looks outward, Self-awareness looks inward | Eyes vs. emotional intelligence |

### Scenario Stories

#### Scenario 1: Filling Out a Government Website Form

You need to fill out an application form on an outdated government website. This site has no AI adaptation — no API, no structured interface, just a plain web form.

iFay's First-person Tracer "sees" the form: name input field, ID number input field, a dropdown menu, a CAPTCHA image, a blue "Submit" button. It passes this visual information to the Simulated Operation module, which fills in fields one by one, selects options, enters the CAPTCHA, and clicks submit — just like your hands would.

After submission, the First-person Tracer immediately "looks" at the result — if a red error message "ID number format incorrect" appears, it captures this change, and iFay knows it needs to correct and resubmit.

Throughout the process, iFay sees exactly what you see — it doesn't need to know what the website's HTML code looks like.

#### Scenario 2: Real-time Stock Monitoring

You ask iFay to watch a stock's real-time chart. The First-person Tracer continuously "watches" the K-line chart and number changes on screen — price jumps from 152.30 to 153.10, volume bars suddenly spike, MACD indicator shows a golden cross…

The First-person Tracer continuously tracks all these real-time changes. When the price hits your target price, iFay immediately notifies you. Just like watching the market yourself, except iFay won't get distracted, won't get tired, and can "watch" 24/7 without interruption.

### For Developers

The First-person Tracer belongs to **Phase 1 (Simulating Human Operations)** as a core module — one of the first components iFay needs to implement.

- **Requirement ID**: Requirement 4 (First-person Tracer)
- **Interface Specification**: `FirstPersonTracer` interface with four core methods: `captureVisual()`, `captureAudio()`, `trackChanges()`, and `getPerceptionStatus()`
- **Related Protocols**: Phase 1 doesn't depend on CAP/DTP protocols, implementing directly through OS-level screen capture; from Phase 2 onward, deeper interface information can be obtained via CAP protocol
- **Conformance Testing**: iFACTS L1 (Single Component Conformance) verifies visual capture capability; L2 (Interface Conformance) verifies hand-eye coordination interface with Simulated Operation module
- **Design Points**: Prioritize visual perception over structured document parsing; perception failures must be reported to the Cognition Layer; form a closed feedback loop with the Simulated Operation module

---

## 9.2 Sensor

### One-Line Definition

The Sensor is iFay's **nervous system** — it lets iFay perceive all changes in the surrounding environment, from temperature and location to heart rate and light, just like the nerve endings distributed throughout your body.

### Why It's Needed

If the First-person Tracer is iFay's eyes and ears, then the Sensor is iFay's **entire neural network**.

Think about your body: you don't just perceive the world through eyes and ears. Your skin senses temperature and touch, your inner ear senses balance and acceleration, your body tells you when you're hungry, tired, or cold. These sensations don't come from eyes or ears — they come from the nervous system distributed throughout your body.

Now think about your phone and smartwatch: GPS knows where you are, the accelerometer knows if you're walking or running, the light sensor knows if you're indoors or outdoors, the heart rate sensor knows how fast your heart is beating. These are all "sensors" — the device's nerve endings.

iFay's Sensor module **unifies access** to all these sensors across devices, giving iFay a complete nervous system. And this nervous system is continuously expandable — any new sensor type that emerges in the future can be integrated.

### How It Works

The Sensor's workflow can be summarized in three keywords: **Bridge, Regulate, Extend**.

**1. Bridge — Connecting Device Sensors**

Your phone has GPS, gyroscope, accelerometer, light sensor, barometer… Your smartwatch has heart rate sensor, blood oxygen sensor, skin temperature sensor… Your smart home has temperature sensors, humidity sensors, door/window sensors…

The Sensor module acts as a "translator," uniformly translating data from all these different devices and sensor types into a format iFay can understand. It uses **CAP (Control Authority Protocol)** and **DTP (Data Tunnel Protocol)** to achieve this bridging.

**2. Regulate — Dynamic Sensitivity**

Your nervous system has a clever feature: when you're focused on work, you barely feel the chair's touch; but when someone taps your shoulder, you feel it immediately. That's dynamic sensitivity regulation.

iFay's Sensor works the same way. It doesn't need to collect data from all sensors at maximum precision all the time — that would waste too many resources. For example:
- When you're quietly working in the office, GPS doesn't need to update your position every second
- But when you're driving with navigation, GPS needs high-frequency updates
- When you're sleeping, the heart rate sensor can lower its sampling frequency
- But when abnormal heart rate is detected, sampling frequency immediately increases

The Sensor module **automatically adjusts each sensor's sensitivity** based on the current scenario and needs.

**3. Extend — Future Sensors Can Also Be Integrated**

Today's sensors are GPS and heart rate monitors; tomorrow's might be brainwave sensors, air quality sensors, or even emotion recognition sensors. The Sensor module's design is open — when new sensor types appear, you just need to register a new driver through the Device Driver Hub, and the Sensor module can manage its sensitivity while the Personal Data Heap stores its data.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Device Driver Hub** | Sensor's actual hardware interfaces are managed by the Device Driver Hub | Nerve endings → nerve conduction pathways |
| **Personal Data Heap** | Data collected by sensors is ultimately stored in the Personal Data Heap | Sensory signals → memory storage |
| **First-person Tracer** | Both in the Perception subsystem, but different roles: Tracer sees the screen, Sensor perceives the physical environment | Eyes vs. whole-body nerves |
| **Self-awareness** | Sensor provides environmental data; Self-awareness uses this data to infer Human Prime's state | Nervous system provides sensations → brain interprets emotions |
| **CAP / DTP Protocols** | Sensor implements data bridging based on these two protocols | Transmission protocol for nerve signals |

### Scenario Stories

#### Scenario 1: Smart Health Reminder

At 3 PM, you've been sitting at your computer for three hours. iFay discovers through your smartwatch's sensor data:

- **Accelerometer**: Almost no significant movement in the past 3 hours (indicating you've been sitting the whole time)
- **Heart Rate Sensor**: Heart rate increased from a normal 72 bpm to 85 bpm (possibly mild discomfort from prolonged sitting)
- **Skin Temperature Sensor**: Wrist temperature slightly elevated

The Sensor module aggregates this data and passes it to iFay's Cognition Layer. After comprehensive analysis, iFay gently reminds you: "You've been sitting for 3 hours and your heart rate is a bit high. How about standing up and stretching? The time it takes me to brew you a cup of tea is just enough for a quick walk."

In this process, the Sensor module didn't "understand" what the data meant — it just faithfully collected and transmitted. Understanding and judgment are the Cognition Layer's job. But without the raw data provided by the Sensor, the Cognition Layer would have nothing to work with.

#### Scenario 2: Autonomous Drone Flight

iFay is deployed on a drone for an aerial photography mission. The drone has multiple sensors:

- **GPS**: Provides position and altitude information
- **IMU (Inertial Measurement Unit)**: Provides acceleration and angular velocity for attitude control
- **Camera**: Provides visual information (handled by the First-person Tracer)
- **Ultrasonic/LiDAR**: Provides obstacle distance information
- **Barometer**: Provides precise altitude data
- **Wind Speed Sensor**: Provides current wind force information

The Sensor module unifies all these data streams. During stable flight, IMU sensitivity can be appropriately lowered; but when sudden wind speed changes are detected, the Sensor module immediately increases IMU and barometer sensitivity, allowing iFay to more precisely control the drone's attitude and avoid loss of control.

### For Developers

The Sensor module belongs to **Phase 2 (Direct Client Takeover)** as a core module, depending on CAP and DTP protocols.

- **Requirement ID**: Requirement 7 (Sensor Module)
- **Interface Specification**: `SensorModule` interface with four core methods: `registerSource()`, `adjustSensitivity()`, `getDataStream()`, and `getActiveStatus()`
- **Related Protocols**: CAP (Control Authority Protocol) for taking over sensor hardware; DTP (Data Tunnel Protocol) for bidirectional data transmission
- **Related Modules**: Device Driver Hub (`DeviceDriverHub`) manages actual hardware interfaces; Personal Data Heap (`PersonalDataHeap`) stores sensor data
- **Conformance Testing**: iFACTS L1 verifies sensitivity adjustment capability; L2 verifies interface integration with Device Driver Hub and Personal Data Heap
- **Design Points**: Sensor module serves only as a sensitivity regulator, not directly managing hardware interfaces; supports dynamic sensitivity adjustment; new sensor types are integrated through the Device Driver Hub

---

## 9.3 Self-awareness

### One-Line Definition

Self-awareness is iFay's **emotional intelligence** — it doesn't look at the screen or perceive the environment. Instead, it **looks inward at you**, inferring your feelings and intentions through your reactions, like an old friend who's great at reading people.

### Why It's Needed

iFay's Perception subsystem has three modules, each looking in a different direction:
- **First-person Tracer** looks outward — sees what's on the screen
- **Sensor** perceives the environment — senses temperature, location, motion
- **Self-awareness** looks inward — observes **you**

Why look inward?

Imagine two types of assistants. The first does whatever you say, like a vending machine — you press a button, it dispenses a drink. The second notices that you're speaking faster than usual today, your brow is slightly furrowed, and you only ate half your lunch, so they proactively postpone your afternoon meeting by half an hour, pour you a cup of hot water, and put on your favorite light music.

The first is iFay without self-awareness — a command-following robot.
The second is iFay with self-awareness — a partner who **understands you**.

Self-awareness upgrades iFay from "you say, I do" to "you don't say, I still understand." It observes your micro-expressions, changes in your operating habits, and emotional fluctuations, then infers what you might need — even before you realize it yourself.

That's the difference between a vending machine and a thoughtful friend.

### How It Works

Self-awareness works like an old friend who's known you for years reading you:

**1. Observing Your Reactions**

Self-awareness continuously monitors various signals during your interactions with iFay:
- Changes in your operation speed (suddenly faster might mean urgency, slower might mean hesitation)
- Your browsing behavior (lingering on a passage might mean interest, quickly scrolling past might mean disinterest)
- Your expressions and tone (if the device has a camera and microphone)
- Your acceptance or rejection patterns of iFay's suggestions
- Whether your daily habits show anomalies

**2. Inferring Your Intent**

Based on observed signals, Self-awareness infers your current state and possible intentions. This isn't simple "if A then B" rules, but intelligent inference combining multiple signals.

For example: you're reading an article about machine learning, scrolling speed noticeably slows at a certain section, and you scroll back twice — Self-awareness infers you're particularly interested in this paragraph and might want to dive deeper.

**3. Passing Inference Results**

When Self-awareness infers a new intent, it does two things:

- **Tells the Self-driven Behavior module**: "The Human Prime might be interested in this topic — should we proactively find related materials?" The Self-driven Behavior module might then automatically search for related articles.
- **Tells the Aligned Consciousness module**: "The Human Prime shows interest in the machine learning field — update the Human Prime profile." The Aligned Consciousness module then adds "interested in machine learning" to your personal profile, making iFay's future behavior more aligned with you.

**4. Real-time Adjustment**

Self-awareness isn't a one-time judgment — it runs continuously. It constantly revises its inferences based on your latest reactions. If it infers incorrectly (e.g., you reject a suggestion it provided based on an inference), it learns and adjusts.

### Relationships with Other Modules

| Related Module | Relationship | Human Body Analogy |
|---------------|-------------|-------------------|
| **Self-driven Behavior** | Self-awareness inferences trigger proactive actions | EQ → proactive care ("You look tired, let me…") |
| **Aligned Consciousness** | Self-awareness adjusts the Human Prime profile in Aligned Consciousness in real-time | Understanding of you deepens with time together |
| **Cognition Layer** | Inference results are passed to the Cognition Layer for deeper understanding and decision-making | Intuition → rational thinking |
| **First-person Tracer** | Tracer looks outward, Self-awareness looks inward — complementary | Eyes see the world vs. heart reads people |
| **Sensor** | Sensor's environmental data can assist Self-awareness inferences | Body sensations assist emotional judgment (e.g., accelerated heartbeat → possibly nervous) |

### Scenario Stories

#### Scenario 1: You're Reading an Article, iFay Proactively Finds Materials

On a weekend afternoon, you're browsing a long article about "sustainable building design" on your tablet. Self-awareness notices:

- You quickly scroll through the first half (not very interested)
- But at the "passive house energy-saving technology" section, your scrolling speed noticeably slows
- You scroll back once to re-read a chart
- You linger on this section for nearly two minutes

Self-awareness infers: you're particularly interested in the topic of "passive house energy-saving technology."

It passes this inference to the Self-driven Behavior module. The Self-driven Behavior module proactively searches for several in-depth articles and a YouTube video tutorial, quietly placing them in your reading list. When you finish the article, iFay gently suggests: "I found some in-depth materials on passive houses. Want to take a look?"

You never said "find me materials," but iFay already had them ready.

#### Scenario 2: A Thoughtful Assistant During a Video Meeting

You're in a video meeting. Self-awareness captures your facial micro-expression changes through the camera:

- First 20 minutes: relaxed expression, occasional nodding
- When a colleague starts discussing project budget cuts, your brow slightly furrows and corners of your mouth turn down slightly
- Your body posture shifts from relaxed to leaning forward, fingers unconsciously tapping the desk

Self-awareness infers: you're uncomfortable with the current discussion topic — possibly disagreeing with the budget cut proposal, or the topic is causing you stress.

It passes this inference to the Self-driven Behavior module. The Self-driven Behavior module quietly prepares two things:
1. A project budget analysis report you previously created (in case you need data to counter-argue)
2. A polite excuse message draft ("Sorry, I have an urgent call to take"), in case you want to temporarily leave

These are all quietly prepared without disturbing you. Only when you need them will iFay present them to you.

### For Developers

The Self-awareness module belongs to **Phase 4 (iFay + coFay Full Personification)** as a core module — the key to iFay evolving from "tool" to "partner."

- **Requirement ID**: Requirement 13 (Self-awareness)
- **Interface Specification**: `SelfAwareness` interface with three core methods: `inferIntent()` (infer intent), `monitorHostReaction()` (monitor Human Prime's reactions), and `adjustAlignment()` (adjust Aligned Consciousness)
- **Related Modules**: Self-driven Behavior (`SelfDrivenBehavior`) receives inference results and triggers proactive actions; Aligned Consciousness (`AlignedConsciousness`) receives inference results and updates Human Prime profile
- **Related Protocols**: No direct protocol dependency, but can leverage the Sensor module (via CAP/DTP) for auxiliary data (e.g., heart rate, facial expressions)
- **Conformance Testing**: iFACTS L1 verifies intent inference capability; L2 verifies interfaces with Self-driven Behavior and Aligned Consciousness; L4 verifies inference accuracy and privacy protection
- **Design Points**: Inference results must be passed to both the Self-driven Behavior module and the Cognition Layer simultaneously; supports real-time Aligned Consciousness adjustment; should learn and correct from Human Prime's feedback when inferences are wrong
