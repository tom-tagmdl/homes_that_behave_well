# Context Before Intent: A Concierge Architectural Framework

## Purpose

This document defines the Context Before Intent architectural pattern within the Concierge framework.

It establishes that Concierge is fundamentally a **room-context engine**, not a voice assistant. Voice is one consumer of contextual intelligence. The same context serves UI, automation, scene execution, and future interaction modalities.

This pattern aligns with Homes That Behave Well philosophy:

- Calm
- Predictable
- Context Aware
- Human-Centered
- Low Cognitive Load
- Confidence Through Context
- Natural Language Interaction

---

## Core Architectural Insight

**A Home That Behaves Well establishes context before intent.**

By understanding occupants, rooms, spaces, devices, and conversation state *before* a request is made, the home can respond naturally, reduce ambiguity, improve responsiveness, and allow people to interact with technology as they would with another person.

This is not a voice feature optimization.

This is a core platform strategy for deterministic, predictable, context-aware interaction.

---

## Architectural Principle: Context Before Intent

### Definition

Context Before Intent means the system resolves all relevant environmental and behavioral context *before* attempting to interpret user intent.

Instead of this flow:

```
User Request
→ Interpret Intent
→ Determine Room Context
→ Resolve Devices
→ Execute
```

The system uses this flow:

```
Room Context Already Established
Device Scope Already Known
Conversation State Already Active
→ Interpret Intent (narrowed)
→ Execute (immediate)
```

### Benefits

- **Faster execution**: No post-request context discovery
- **Lower ambiguity**: Intent interpreted within known scope
- **More natural interactions**: Users speak as they would to another person
- **Reduced cognitive load**: No need to specify redundant context
- **Improved responsiveness**: Contributes to a calm user experience

---

## Component Responsibilities

### Foundation (System of Record)

Foundation owns facts and state about the physical home.

**Foundation is responsible for:**

- Rooms (area_id)
- Merged Spaces (logical groupings of rooms)
- Presence (who is home)
- Occupancy (who is where)
- Adjacency (which rooms connect)
- Device Membership (which devices belong to which rooms)
- Space Membership (which rooms compose which spaces)

Voice Identity contributes identity attribution context as an optional peer service.

**Foundation room-source rule:**

- Home Assistant Areas are the source of truth for rooms.
- Concierge room cards are derived from Home Assistant Area records.
- If an Area is added or removed in Home Assistant, Concierge must reflect that change automatically.
- Concierge data for rooms is extension data attached to `area_id` (context and policy), not a separate room registry.

**Examples:**

```
Rooms:
  - Primary Bedroom
  - Primary Bathroom
  - Laundry

Merged Spaces:
  - Primary Suite
    - Primary Bedroom
    - Primary Bathroom
    - Closet

  - Great Room
    - Kitchen
    - Dining
    - Living Room
```

**Foundation answers:** "What is true?"

**Foundation does NOT decide:**

- Which assistant responds
- Which room owns a conversation
- Which devices are selected for execution

Those belong to Concierge Coordinator.

---

### Concierge Coordinator (Decision and Orchestration)

Concierge Coordinator is the decision-making engine at runtime.

It consumes Foundation state and derives interaction context in real time.

It may consume Voice Identity attribution outputs when available.

**Coordinator answers:** "What should happen?"

**Coordinator responsibilities include:**

- **Context Resolution** — Determines which room or space a user is likely interacting with
- **Interaction Space Determination** — Establishes the active conversation area
- **Conversation Ownership** — Assigns one room/assistant to lead interaction
- **Response Routing** — Routes responses to appropriate speakers or interfaces
- **Notification Routing** — Determines which room receives alerts and notifications
- **Persona Application** — Applies room-specific behavior and preferences
- **Identity Context Fusion** — Fuses person, presence, and optional Voice Identity confidence
- **Media Ducking** — Manages audio priority across rooms
- **Learning and Adaptation** — Stores correction signals and improves future context resolution

**Core principle:** Coordinator is stateful and decision-focused, not data-focused.

Boundary rule:

- Coordinator consumes identity outputs and must not own fingerprint generation or attribution model internals.

---

## New Architectural Concepts

### Interaction Space

#### Definition

An Interaction Space is the area in which a conversation is actively occurring.

It may correspond to:

- A single room
- A merged space
- A suite
- A logical area

#### Examples

```
Primary Suite
  - Bedroom
  - Bathroom
  - Closet

Great Room
  - Kitchen
  - Dining
  - Living Room

Master Bedroom (single room)
```

#### Derivation

Interaction Space is derived using:

- Wake word detections (microphone locations)
- Occupancy patterns (presence distribution)
- Presence signals (person identity and location)
- Voice Identity attribution confidence when available
- Historical behavior (user patterns in specific rooms)

#### Behavior

Once established, Interaction Space:

- Narrows command scope before intent resolution
- Remains active during multi-turn conversations
- Provides context for device resolution
- Informs messaging and notification routing
- Influences speaker selection for audio output

---

### Conversation Ownership

#### Definition

Conversation Ownership establishes which room leads a multi-turn interaction.

Once a conversation begins in an Interaction Space, all subsequent requests remain in that context until the conversation naturally ends or times out.

#### Rules

- One room owns the interaction
- One assistant responds (if multiple assistants present)
- Other assistants become passive listeners
- Follow-up commands remain in the same context without re-resolution

#### Example

```
User (in living room): "Turn on the lamps"
  → Coordinator resolves Interaction Space: Living Room
  → Coordinator establishes Conversation Ownership: Living Room

User: "Dim them"
  → Still in Living Room context
  → No need to re-resolve room

User: "Make them warmer"
  → Still in Living Room context
  → Request executes against living room devices

[30 seconds pass, no new requests]

User (in bedroom): "Turn on the lamps"
  → Interaction Space timeout triggered
  → Coordinator resolves new context: Bedroom
  → New Conversation Ownership established: Bedroom
```

#### Benefits

- Reduces latency (no re-resolution required)
- Improves user experience (natural conversation flow)
- Prevents context thrashing (devices don't get re-resolved)
- Supports multi-room speech in sequence (after timeout)

---

### Attention Management

#### Definition

Attention Management is the system's awareness of where interaction is most likely occurring.

It is not about "which microphone heard the command best."

It is about "where should the home's attention be focused right now?"

#### Input Signals

- **Occupancy** — Distribution of people across spaces
- **Presence** — Identity and location of specific persons
- **Identity** — Who is speaking (if determinable)
- **Wake word locations** — Which room's microphone(s) detected the wake word
- **Recent interactions** — Which rooms had recent activity
- **Environmental context** — Activity level, noise patterns

#### Computation

Attention Management is a probabilistic or weighted evaluation that considers all inputs.

Examples:

- High occupancy + recent activity in kitchen → Focus kitchen attention
- Person home + movement detected in bedroom → Shift attention to bedroom
- Wake word in two rooms → Weight by signal strength or recent behavior
- No recent activity + normal patterns → Maintain last active context with decay

#### Output

Attention Management produces:

- Primary focus area (highest probability)
- Secondary focus area (backup context)
- Confidence level
- Factors contributing to the decision

#### Architectural Principle

**The home pays attention to people and spaces, not microphones.**

Microphones are sensors of occupancy and activity. They are not decision-making instruments.

The home's attention follows people, not audio capture points.

---

### Context Compression

#### Definition

Context Compression is the optimization achieved when room context is pre-established.

Traditional voice systems require full verbosity:

```
"Turn on the bedroom lamps"
"Adjust the living room temperature"
"Close the kitchen shades"
```

Context-aware systems allow natural compression:

```
"Turn on the lamps"
"Adjust the temperature"
"Close the shades"
```

#### This Is Not Merely Convenience

Context Compression is **not** a feature for brevity.

It is a **performance optimization strategy**.

- The home has already narrowed the scope before intent processing
- Intent resolution operates over a smaller decision space
- Execution targets are already resolved
- Response time improves measurably

#### Benefits

- **Faster execution** — No post-request scoping
- **Lower ambiguity** — Intent clearly maps to room scope
- **More natural interactions** — Users speak naturally
- **Reduced cognitive load** — No need to specify redundant context
- **Improved responsiveness** — Contributes to calm UX

---

### Device Scope Resolution

#### Definition

Concierge maintains an in-scope device inventory for each active room and merged space.

When a voice request arrives, intent resolution happens against the local device scope first.

#### Example: Primary Bedroom Scope

```
Bedroom Lamps (light.bedroom_lamps)
Bedroom Lights (light.bedroom_ceiling)
Bedroom Shades (cover.bedroom_shades)
Bedroom TV (media_player.bedroom_tv)
Bedroom Speakers (media_player.bedroom_speakers)
Bedroom Climate (climate.bedroom_thermostat)
```

#### Example: Great Room Scope

```
Kitchen Lights (light.kitchen_lights)
Dining Lights (light.dining_lights)
Living Room Lamps (light.living_room_lamps)
Living Room TV (media_player.living_room_tv)
Great Room Speakers (media_player.great_room_speakers)
Great Room Climate (climate.great_room_thermostat)
```

#### Resolution Rules

1. **Prefer Contextual Resolution** — Match intent against local room/space scope first
2. **Only Expand When Necessary** — Only look outside local scope if ambiguity remains
3. **Explicit Scoping** — If a user specifies "other room lights," respect that override
4. **Deterministic Ordering** — Resolution order must be predictable and stable

#### Architectural Principle

**Prefer Contextual Resolution over Global Resolution.**

---

### Learning Through Corrections

#### Definition

The system learns and improves through user corrections without requiring explicit training.

#### Correction Signals

```
User says: "No, the bathroom."
  → Coordinator stores: Room resolution error in bathroom context

User says: "Wrong room."
  → Coordinator stores: Interaction Space misidentification

User says: "I meant this room."
  → Coordinator stores: Context override signal
```

#### Adaptation

Over time, Coordinator uses correction signals to:

- Improve room detection accuracy
- Weight certain signals more heavily
- Recognize patterns in user corrections
- Adjust attention management algorithms

#### Rules

- Corrections must be stored deterministically
- Corrections must not break predictability
- The system should remain explainable at all times
- Learning must not introduce randomness

#### Architectural Principle

**The home should continuously improve while remaining predictable.**

---

## Performance Optimization: Room Context as Efficiency Strategy

### Traditional Architecture

```
Voice Request Arrives
  ↓
Attempt to Interpret Intent (broad interpretation)
  ↓
Determine Which Room (discovery / inference)
  ↓
Resolve Which Devices (search entire home)
  ↓
Execute
  ↓
Time to Response: 500ms - 2000ms (depending on discovery complexity)
```

### Context-Before-Intent Architecture

```
Room Context Already Established (pre-computed)
Device Scope Already Known (cached)
Conversation State Already Active (maintained)
  ↓
Voice Request Arrives
  ↓
Interpret Intent Against Local Scope (fast)
  ↓
Resolve Target (already narrowed)
  ↓
Execute
  ↓
Time to Response: 50ms - 300ms (minimal overhead)
```

### Measurable Impact

The context-before-intent pattern:

- Eliminates expensive discovery operations
- Reduces decision space for intent matching
- Removes ambiguity requiring clarification
- Enables immediate execution

**Result:** Faster, more responsive interaction that contributes to a calm user experience.

---

## Runtime Data Structures

### Coordinator Maintained State

Concierge Coordinator maintains these runtime structures:

#### 1. Active Interaction Spaces

```
active_interaction_spaces:
  - space_id: great_room
    type: merged_space
    rooms: [kitchen, dining, living_room]
    established_at: 2026-06-27T10:00:00Z
    last_activity: 2026-06-27T10:00:45Z
    status: active
    confidence: 0.92
    source_signals:
      - wake_word_kitchen: 0.8
      - occupancy_great_room: 0.95
      - recent_activity: 0.85

  - space_id: primary_bedroom
    type: single_room
    rooms: [primary_bedroom]
    established_at: 2026-06-27T09:55:00Z
    last_activity: 2026-06-27T09:56:00Z
    status: passive
    confidence: 0.45
    timeout_seconds: 30
```

#### 2. Conversation Ownership

```
active_conversations:
  - conversation_id: conv_2026062710004501
    interaction_space: great_room
    owner_room: kitchen
    started_at: 2026-06-27T10:00:00Z
    last_exchange: 2026-06-27T10:00:45Z
    timeout_seconds: 30
    device_scope:
      - light.kitchen_lights
      - light.dining_lights
      - light.living_room_lamps
      - media_player.great_room_speakers
    response_speaker: speaker.kitchen
```

#### 3. In-Scope Device Inventory

```
device_scopes:
  great_room:
    device_groups:
      - group_key: lights
        display_name: Lights
        vocabulary: [lights, kitchen lights]
        entity_ids:
          - light.kitchen_lights
          - light.dining_lights
      - group_key: lamps
        display_name: Lamps
        vocabulary: [lamps, living room lamps]
        entity_ids:
          - light.living_room_lamps
      - group_key: media
        display_name: Media
        vocabulary: [media, speakers, tv]
        entity_ids:
          - media_player.great_room_speakers
          - media_player.living_room_tv
      - group_key: climate
        display_name: Climate
        vocabulary: [climate, thermostat]
        entity_ids:
          - climate.great_room_thermostat
      - group_key: other
        display_name: Other
        vocabulary: [other]
        entity_ids:
          - cover.kitchen_shades
          - switch.island_fan

  primary_bedroom:
    device_groups:
      - group_key: lights
        display_name: Lights
        vocabulary: [lights, bedroom lights]
        entity_ids:
          - light.bedroom_ceiling
      - group_key: lamps
        display_name: Lamps
        vocabulary: [lamps, bedroom lamps]
        entity_ids:
          - light.bedroom_lamps
      - group_key: media
        display_name: Media
        vocabulary: [media, bedroom tv, bedroom speakers]
        entity_ids:
          - media_player.bedroom_tv
          - media_player.bedroom_speakers
      - group_key: other
        display_name: Other
        vocabulary: [other]
        entity_ids:
          - cover.bedroom_shades
          - climate.bedroom_thermostat
```

Rule:

- group definitions and vocabulary are setup-authored and persisted
- runtime context resolution must use these precomputed mappings and must not infer new categories

---

## Practical Examples

### Example 1: Natural Voice Interaction in Context

```
Setup:
  - User is in the kitchen (part of Great Room)
  - Coordinator has established Interaction Space: Great Room
  - Device scope is pre-loaded

User: "Turn on the lamps"
  1. Coordinator recognizes context: Great Room
  2. Intent matches: "turn on" → "lamps"
  3. Device resolution against scope: Great Room lamps
     - Kitchen Lights (best match)
     - Dining Lights (secondary match)
  4. Execution: Service call to light.kitchen_lights
  5. Response: "Kitchen lights are on"

User: "And the dining lights"
  1. Still in Great Room conversation context
  2. Intent matches: "turn on" → "dining lights"
  3. Device resolution:
     - Explicit mention "dining lights" → Dining Lights
  4. Execution: Service call to light.dining_lights
  5. Response: "Dining lights are on"

User: "Lower the temperature"
  1. Still in Great Room conversation context
  2. Intent matches: "lower" → "temperature"
  3. Device resolution: Great Room thermostat (only climate in scope)
  4. Execution: Service call to climate.great_room_thermostat
  5. Response: "Great Room temperature lowered"

[60 seconds pass, no new requests]
  → Conversation timeout
  → Conversation Ownership expires
  → Interaction Space may shift if user moves or new activity detected
```

### Example 2: Multi-Room Conversation with Attention Shift

```
Setup:
  - User is in Great Room, conversation established
  - User moves to Primary Bedroom

User (in Great Room): "Turn on the lamps"
  → Interaction Space: Great Room
  → Coordinator: Execute kitchen lamps

[User walks to bedroom, no request for 45 seconds]
  → Attention Management detects movement to bedroom
  → Occupancy shifts: person now in bedroom
  → Interaction Space transitions

User (in Primary Bedroom): "Turn on the lamps"
  1. Attention Management: Primary Bedroom has highest probability
  2. Coordinator establishes new Interaction Space: Primary Bedroom
  3. Device scope: Bedroom lamps
  4. Execution: Service call to light.bedroom_lamps
  5. Response: "Bedroom lights are on"
```

### Example 3: Correction and Learning

```
Setup:
  - Multiple rooms have similar devices
  - User is in living room

User: "Turn on the lamps"
  1. Coordinator resolves: Living Room context
  2. Executes: light.living_room_lamps
  3. Result: Lights turn on, but user is frustrated
  
User: "No, the kitchen lamps"
  1. Correction signal detected
  2. Coordinator stores: "User in living room originally → kitchen intent"
  3. Coordinator executes: light.kitchen_lights
  4. Learning: Adjust context resolution weights

[Later, similar scenario]
  User: "Turn on the lamps"
  → Coordinator: Considers kitchen context based on learned pattern
  → Higher confidence in kitchen scope
  → Result: Correct device activated
```

---

## Concierge Voice Integration

Voice is one consumer of Concierge context.

The same context engine serves:

- **Voice interaction** — Uses Interaction Space and device scope
- **UI interaction** — Room filters based on Interaction Space
- **Scene execution** — Pre-scoped device lists improve performance
- **Automation rules** — Room context determines applicability
- **Notification routing** — Interaction Space routes alerts to active speakers
- **Future interaction modalities** — Any new interface uses the same context

### Voice Interaction Rules

#### Coordinator provides:

- Active Interaction Space
- Device scope for current room/space
- Conversation ownership state
- Response routing (which speaker outputs)

#### Voice processing layer receives:

- Natural language request
- Interaction Space context
- Device scope
- Identity of speaker

#### Intent resolution happens against:

- Local device scope only (no home-wide search)
- Conversation context (multi-turn state)
- User identity and preferences

#### Execution layer:

- Calls services with pre-resolved targets
- Uses response_speaker from conversation state
- Applies learned room preferences

---

## Architectural Principles Summary

### Context Before Intent

Establish context before interpreting intent.

### Prefer Contextual Resolution

Resolve devices against local scope before expanding.

### Conversation Ownership

Maintain conversation state across multiple requests.

### Attention to People

Focus system attention on occupancy patterns, not microphone locations.

### Room Context as Performance Optimization

Context pre-establishment dramatically improves response time.

### Learning Through Corrections

Adapt room resolution without breaking predictability.

### Concierge as Context Engine

Concierge is fundamentally a room-context engine, not a voice system. Voice is a consumer of context.

---

## Homes That Behave Well Principle

**A Home That Behaves Well establishes context before intent.**

By understanding occupants, rooms, spaces, devices, and conversation state before a request is made, the home can:

- Respond naturally
- Reduce ambiguity
- Improve responsiveness
- Allow people to interact with technology as they would with another person

This is the architectural insight that makes the Homes Platform coherent as a unified decision-support system for the home.

Voice, UI, automation, and future integrations all consume the same context engine.

The home is not a collection of voice-activated devices.

It is a context-aware environment that facilitates human interaction through multiple modalities, with room context as the unifying principle.
