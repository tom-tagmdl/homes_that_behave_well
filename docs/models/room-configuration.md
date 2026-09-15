# Room Configuration Model

> **Document status: Canonical model.**
> Terminology: [glossary.md](glossary.md). Owning responsibility: **Foundation**.
> Contract: [../contracts/room-configuration-contract.md](../contracts/room-configuration-contract.md)

---

## Purpose

**Room Configuration is an interaction-definition model. It is not an inventory screen and not merely
a location model.**

This is one of the most important architectural discoveries carried forward from the exploratory
Concierge work. The original Room Setup achieved a valid and essential household outcome. The
outcome is preserved; the ownership is corrected.

## Question answered

*In this Room, what participates, what is exposed, what do residents call it, what can they do here,
and which sensors feed the room's composite facts?*

---

## The canonical distinction

| Statement | Owner |
|---|---|
| The asset model defines **what exists** | Foundation (asset model) |
| Room Configuration defines **what participates** | Foundation (Room Configuration) |
| Room Configuration defines **what is exposed** | Foundation (Room Configuration) |
| Room Configuration defines **how residents refer to the participating resources** | Foundation (Room Configuration) |
| Truth defines **what is happening** | Truth |
| Operational Trust defines **what is allowed** | Operational Trust |
| Concierge determines **what should happen** | Concierge |

> Do not place canonical Room Configuration ownership inside Concierge merely because the exploratory
> Concierge integration contained the setup UI.
>
> **Concierge consumes Room Configuration.**
>
> The eventual unified HTBW UI may expose Room Configuration through a room-oriented experience, but
> **UI placement does not change architectural ownership.**

---

## The four states

These must never be conflated.

| # | State | Definition |
|---|---|---|
| 1 | **Existence** | The asset, device, entity, sensor, person, pet, service, or relationship is known. |
| 2 | **Participation** | The item has been explicitly selected to contribute to a Room capability, experience, composite fact, or interaction. |
| 3 | **Exposure** | The item or grouped capability is intentionally made available to residents through vocabulary, Room Help, UI, conversation, or another interaction surface. |
| 4 | **Authority** | A person or automated process is permitted to use, change, query, or act on the exposed capability. |

Principles P5–P7:

- Asset existence does not imply room participation.
- Room participation does not imply resident exposure.
- Resident exposure does not imply permission to act.

> **Exposure here is the HTBW constitutional state. It is not Home Assistant Assist entity
> exposure.** Assist exposure decides whether an assistant may target an entity; HTBW Exposure
> decides whether something may be perceptible to a resident. **Assist exposure is a platform
> boundary that HTBW may narrow and must never bypass.** The canonical explanation and the precedence
> rule are in
> [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md);
> the residual question is **OD-59**.

Worked examples:

| Example | States |
|---|---|
| A Sonos Beam exists but does not participate as a music speaker | Exists, not participating (as a music speaker) |
| A temperature sensor exists, is not exposed conversationally, but participates as evidence for a Composite Fact about Room temperature | Exists, participates, not exposed |
| A piano exists, participates as a knowledge asset, and is exposed under the vocabulary term "Piano" | Exists, participates, exposed |
| Seven shades exist and are exposed collectively as "Shades" | Exist, participate, exposed as a group |
| A guest may see that lights are available but may not change security settings | Exposed, no authority |

---

## What Room Configuration owns or establishes

- Room identity
- Constituent Physical Rooms or Areas
- Participating voice assistants
- Participating controllable assets
- Participating knowledge assets
- Participating music speakers
- Participating television or video assets
- Participating environmental sensors
- Participating occupancy or presence evidence sources
- **Explicitly excluded assets**
- Contextual vocabulary
- Vocabulary-to-target mappings
- Capability exposure
- Room Help definitions
- Composite-fact input selection
- Experience endpoints
- Relevant Room modes
- Human-friendly room configuration

Explicit exclusion is first-class. Participation is one of three distinct states, and the deliberate
exclusion must survive later re-configuration and be explainable.

| Participation state | Meaning |
|---|---|
| **Participating** | The asset or capability takes part in this Room's interaction model |
| **Not Selected** | The asset is known to the Home but was never considered for this Room |
| **Deliberately Excluded** | The asset was considered and intentionally kept out of this Room, or out of a specific vocabulary term |

**Not Selected** and **Deliberately Excluded** must never be collapsed. Only the latter is
explainable as an intention.

### Room Configuration extends an Area; it does not copy it

Governed by **DL-31** and
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md).

Home Assistant remains authoritative for the Area's **name, picture, `floor_id`, `aliases`, `labels`,
and its assigned temperature and humidity entities**. Room Configuration **references the Area by its
area ID** and stores only the interaction extensions listed above.

**None of those native values is copied into Room Configuration.** An Area rename, picture change, or
Floor move therefore requires **no synchronisation**, because there is nothing to keep in step. A
resident who has named and organised an Area in Home Assistant must **never be asked to do so again**
in HTBW.

A **Merged Room** likewise **references** its constituent Areas or Rooms. Constituent definitions are
never copied into the Merged Room; only the merged interaction semantics are HTBW-owned. Whether a
Merged Room additionally warrants a native projection is **OD-70**.

### Selecting participating objects

The configuration experience distinguishes **available** native objects from **participating** ones.

*Available* objects are the Devices and Entities associated with, or otherwise eligible for, the
native Area the Room represents. Eligibility uses supported Home Assistant relationships and remains
subject to participation and exposure governance; it is never an unrestricted inventory.

Moving an object into participation **does not** rename it, change its native aliases, expose it to
Assist, grant authority to use it, make every one of its capabilities resident-visible, or include
every Entity belonging to a Device. **A Device-level term is never assumed to apply to all of that
Device's Entities**; the participating target or capability is identified explicitly.

#### Explicit participation already selects the execution provider (DL-55)

Where one physical endpoint is represented by more than one technical provider (for example a Sonos
speaker visible through the native Sonos integration, Music Assistant, and the Home Assistant device
registry simultaneously), **participation's existing rule that the target is identified explicitly
already resolves which provider executes** — the household's (or configuration flow's) explicit
native reference names one concrete entity, not an abstract capability class, so there is no runtime
choice left to make. **No separate provider-precedence mechanism is required for execution.** A
provider whose entity was not selected may still contribute identity, capability, or connectivity
**evidence** through Truth, but it never becomes a competing execution or attestation authority for
that participating target (**DL-41**, **DL-54**). Endpoint identity across multiple provider records
for one physical thing is the existing **Asset** model's concern where the household has declared an
Asset (`docs/models/asset.md`: one Asset may be represented by several Devices); where no Asset is
declared, the participating target's own native reference is a sufficient identity anchor for this
Room's purposes, and no name/room/IP/vendor matching is required or permitted. Residual runtime
questions this does not answer — room-level outcome aggregation across several participating
endpoints, and configuration evolution as capabilities change — are addressed in
[../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md) and this
model's existing failure-behavior table, respectively. See **OD-88**, resolved as **DL-55**.

For each participating target the configuration may present the native reference, the native display
name, applicable native Assist aliases, native Assist exposure status, the HTBW contextual term,
whether that term is seeded or household-defined, target scope, participation status, explicit
exclusions, ambiguity indicators, and Merged Room implications. **This is an architecture
description. It prescribes no frontend technology, layout, or component.**

Native naming information may **seed** a contextual term when a target first participates. The seed is
attributed to Home Assistant, never synchronised afterwards, and **never written back**. A
household-defined term survives a later native rename. The full rule is
[contextual-vocabulary.md](contextual-vocabulary.md).

### Four states that must not be collapsed

| State | Owner | Question it answers |
|---|---|---|
| **Native Assist exposure** | Home Assistant | May an assistant target this entity at all? |
| **HTBW participation** | Room Configuration | Does this object take part in this Room's interaction model? |
| **HTBW contextual exposure** | Room Configuration | Is it reachable by a term, and offered in Room Help? |
| **Authority** | Operational Trust | Is this resident permitted to act on it, or to know it exists? |

**These are four distinct states, never one checkbox and never one semantic concept.** Where the
configuration displays exposure, it must say which of the four it is showing. HTBW may narrow native
Assist exposure and must never bypass it; the canonical explanation is in
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md).

### When the native object changes

| Native change | Required behaviour |
|---|---|
| Device or Entity renamed | The new name is read from Home Assistant. **A household-defined term is unchanged.** An unaccepted seed may be refreshed |
| Aliases added, removed, or changed | Same treatment. HTBW may report that the native source changed and offer re-import. **Nothing is imported automatically over a household-defined term** |
| Native Assist exposure changes | The platform boundary moves. Participation and vocabulary are unchanged; what may be voice-targeted follows the native setting |
| Object moves to another Area | Participation is **not** silently redefined. The condition is surfaced and resolved through this lifecycle |
| Object disabled or unavailable | Vocabulary is retained. Resolution reports the condition. **Unavailability never deletes a term** |
| Object deleted | The reference becomes unresolved and follows the Repairs and broken-reference boundary. **A term is never automatically reassigned to another object, and historical references are never rewritten** |
| The Room is inside a Merged Room | The same rules apply. The Merged Room is a Room |

Removing an object from participation **never renames or alters the native object.**

---

## The questions Room Configuration must keep answering

These were successful outcomes of the original Concierge Room Setup and must not be simplified away
into a generic room-grouping model:

- **What do you call this?**
- **What can I do here?**
- **Which devices participate?**
- **Which devices are intentionally excluded?**
- **Which sensors contribute to composite room truth?**
- **Which vocabulary terms are available in this Room?**

> These questions are preserved verbatim. In canonical terminology, "composite room truth" means a
> **Composite Fact** scoped to the Room — a fact Truth derives from more than one eligible contributing
> sensor. It is unrelated to the superseded term "Composite Room". See [glossary.md](glossary.md).

---

## Voice assistant context

Participating voice assistants are explicitly assigned to a Room configuration.

When a participating voice assistant receives a request, **its Room assignment provides the default
Room Context.** The resident should not need to state the Room name.

Resolution order for a spoken request:

1. Voice assistant identity
2. Assigned HTBW Room Context
3. Persisted Room vocabulary mapping
4. Explicit target set
5. Applicable Identity, Truth, Continuity, Stewardship, and Operational Trust context
6. Concierge evaluation and orchestration

Two voice assistants participating in the same Room produce the **same** target resolution.

Prohibited:

- Runtime discovery of nearby devices
- A query across every device in the Room
- Requiring the resident to name the Room
- Requiring the resident to know individual target names
- Automatic inclusion of every matching device in every constituent Room

Separation to preserve:

- **Identity** may determine who spoke.
- **The voice assistant assignment** determines the default Room Context.
- **Truth** may confirm or refine current person presence where required.

Do not collapse these separate responsibilities.

### Interaction surfaces that are not bound to a Room

The resolution order above is defined for a **room-bound** surface — a participating voice assistant, a
participating kiosk, or another endpoint the household has assigned to a Room.

**It is not defined for a surface that is not bound to a Room**: a phone, a wearable, a Companion App
action, or a browser session. Such a surface may carry very strong **person** binding while carrying no
**room** binding at all, and the two must not be confused.

| Rule | Statement |
|---|---|
| The governed outcome today is `unresolved` | Ask which Room, or refuse, per policy. **This is correct behaviour, not a failure** |
| **Never infer from device naming** | Unchanged from the failure table below, and it applies to surfaces exactly as it applies to targets |
| Never substitute a plausible Room | A wrongly resolved Room resolves the wrong vocabulary, targets the wrong assets, consults the wrong Room's facts and modes, and produces a trace that is internally consistent and externally wrong |
| A person binding is not a room binding | An authenticated surface may establish **Authenticated Session Identity** or **Interaction Initiator** — and establishes **no Room Context** |
| The trace must say so | Every Decision Trace records Room Context **and how it was resolved**; where it was not resolved, it records `unresolved` and the reason. See [decision-trace.md](decision-trace.md) |

> **How Room Context may be resolved for such a surface is open decision OD-73.** The obvious input — the
> device's current location — is a **Truth** Fact, and [../architecture/dependency-view.md](../architecture/dependency-view.md)
> rule 6 states that **Foundation consumes nothing**. That is an ownership and directional question, not an
> implementation detail, and it is recorded rather than resolved here.

---

## Room Help and capability exposure

When a resident asks **"What can I do here?"**, the answer is generated from the deliberately
configured Room interaction model.

**Room Help must not be generated from:**

- Every Home Assistant entity
- Every device in the Physical Room
- Every asset known to the asset model
- Every sensor
- Every internal diagnostic
- A live runtime inventory search

Room Help describes only intentionally exposed vocabulary and capabilities. Example content:

- Control the lights
- Control the lamps
- Open or close the shades
- Play music
- Control the TV
- Use the media player
- Ask about the piano

**Room Help is a projection of configured participation, vocabulary, capabilities, and exposure. It
is not an inventory report.**

Native Home Assistant names and aliases may **seed** the configuration, but they **never independently
determine Room Help content**. Room Help must not advertise an excluded target, a non-participating
target, a capability not exposed through this configuration, or anything the asking resident is not
authorised to use or to know exists.

**Room Help lists authoritative vocabulary terms only.** Derived recognition forms improve
understanding; they are not separately advertised capabilities, and Room Help does not enumerate them.

### One configuration, many surfaces

The same canonical Room configuration must drive:

- Voice target resolution
- Room Help
- Resident-facing controls
- Capability exposure
- Explainability
- Diagnostics

This is what prevents drift between what the home says is available and what commands actually do.

### Presentation-purpose vocabulary is vocabulary, not a new concept

A household term such as "Speaker" resolving to a Room's music endpoints, or "Display" resolving to
its visual endpoint, is an ordinary application of the existing **vocabulary-to-target mapping** above
— it requires no new capability. Room Configuration continues to own only **which target set a term
resolves to**; it does not own, and must not be asked to resolve, **which currently available
technical provider or evidence path** delivers through that target at a given moment, nor how a
Room-defined outcome spanning several endpoints is aggregated. Those runtime questions are **OD-88**.

---

## Sensors and Composite Facts

Many sensors may exist in a Room without being exposed to residents or used individually by
Concierge.

| Step | Owner |
|---|---|
| Retain all sensors and their authoritative records | Asset model (Foundation) |
| Identify which sensors are **eligible** to participate in configured Composite Facts | Room Configuration |
| Establish the Composite Fact from governed evidence | **Truth** |
| Consume the Composite Fact | Concierge and residents |

Example:

```
Asset model knows:        Temperature Sensor A, B, C
Room Configuration says:  A and C are eligible contributors for Living Space temperature
Truth establishes:        Living Space temperature is 72 degrees (confidence, coverage, provenance)
Resident hears:           "It's 72 degrees in the Living Space."
```

Raw evidence remains available for diagnostics, provenance, calibration, and explainability where
authorized.

Boundaries:

- **Room Configuration does not calculate Truth.**
- **Truth does not own the sensor inventory.**
- **Concierge does not choose sensors at runtime.**

---

## Consumes

- Foundation object identifiers and the asset model
- Home Assistant Area, Device, and Entity references
- Household intent expressed through configuration

## Provides

- Resolved Room Context for a given voice assistant or surface
- Resolved target set for a given vocabulary term in a given Room
- The exposure set used to answer Room Help
- The eligible-evidence set used by Truth for composite facts
- Explicit exclusions, with reasons where supplied

---

## Explicit non-responsibilities

Room Configuration does **not**:

- Calculate composite facts (Truth)
- Determine occupancy or presence (Truth)
- Grant authority (Operational Trust)
- Store preferences or sessions (Continuity)
- Decide what should happen (Concierge)
- Own the authoritative asset record (Foundation asset model)

---

## Failure behavior

| Condition | Behavior |
|---|---|
| Voice assistant not assigned to a Room | Ask which Room, or refuse. Surface as a configuration problem. Never infer from device naming. |
| **The interaction surface is not bound to a Room** | **Room Context is `unresolved`.** Ask which Room, or refuse. **Never infer a Room from the surface, its name, or its owner.** Recorded in the trace with the reason. Resolution is **OD-73** |
| Vocabulary term not configured in this Room | State that the term is not configured here. Do not fall back to runtime search. |
| Vocabulary term maps ambiguously | Ask which target was meant, offering only exposed options. |
| A participating target no longer exists | Report a broken participation reference; do not silently drop it. |
| A composite-fact contributor is unavailable | Truth reduces confidence and records reduced coverage; configuration is unchanged. |
| A historical configuration version cannot be resolved | Report the reference as unavailable with the reason where known; never present today's configuration as though it applied then. |
| A configuration Change Record cannot be written | The failure is itself reportable; a silently unrecorded configuration change is a defect. |
| Room Help requested for an unconfigured Room | Say the Room is not configured yet; do not enumerate inventory. |

## Privacy considerations

Exposure decisions are privacy decisions. A capability that is exposed becomes discoverable by anyone
present. Sensitive capabilities must rely on Operational Trust authority, not on obscurity.
See [../architecture/privacy.md](../architecture/privacy.md).

## Explainability requirements

Every Decision Trace that resolved a target must record: the Room Context, the vocabulary term, the
resolved target set, and the configuration source. Every refusal caused by missing configuration must
say so plainly.

---

## Configuration history

**Room Configuration owns the history of its own records.** Foundation defines the shared temporal
model; Room Configuration records its changes with it. See
[temporal-record.md](temporal-record.md).

History is owned for:

- Room and Merged Room membership
- Participation
- Not-selected state
- Deliberately-excluded state
- Exposure
- Vocabulary terms and mappings
- Voice-assistant assignment
- Composite Fact contributor selection
- Capability definitions

### Current Projection

The **Current Projection** answers what is configured now, and is what runtime resolution reads.
Room Help, vocabulary resolution, and eligible-contributor lookup use the Current Projection.
**Historical records are never the runtime query path.**

### Change Records

Every governed configuration change produces a **Change Record** naming the subject, the change type,
the prior state, the new state, the Effective Time, the Recorded Time, the actor or initiating
process, the reason where supplied, and the prior and new version references.

The three participation states — **participating**, **not selected**, **deliberately excluded** —
must never be collapsed. **This holds in history exactly as it holds in the present.** A Change
Record that reduces *"moved from not selected to deliberately excluded"* to *"changed"* has destroyed
the distinction the model exists to protect.

### Explaining past decisions

A past decision references the **exact configuration version** applied at the time (**P30**). Changing
configuration today must never silently rewrite the explanation of a decision made yesterday.

---

## Representative scenarios

- [../scenarios/room-vocabulary.md](../scenarios/room-vocabulary.md)
- [../scenarios/why-did-this-happen.md](../scenarios/why-did-this-happen.md)

## Open decisions

| ID | Question |
|---|---|
| OD-01 | Home Assistant representation strategy for Room Configuration — the Area reference-and-extension rule is accepted as **DL-31**; the residual is the persistence shape of Change Records, Snapshots, and Current Projections |
| OD-02 | **Closed — DL-43, DL-44, DL-45.** Vocabulary and participation definitions are located through a governed artifact reference; encoding remains capability-specific |
| OD-12 | Whether exclusions carry a structured reason and whether reasons are resident-visible |
| OD-37 | Snapshot triggers, cadence, and scope per responsibility |
| OD-38 | Version identity, correlation, and causation identifier strategy |
| OD-70 | Whether a Merged Room warrants a native Home Assistant projection |
| OD-73 | **Interaction-Surface Room Context Resolution** — how Room Context is resolved for a phone, wearable, Companion App, browser session, or other surface not bound to a Room, without Foundation consuming Truth and without introducing a cycle |

## Related documents

- [room.md](room.md)
- [contextual-vocabulary.md](contextual-vocabulary.md)
- [truth.md](truth.md)
- [temporal-record.md](temporal-record.md)
- [../contracts/room-configuration-contract.md](../contracts/room-configuration-contract.md)
- [../contracts/contextual-vocabulary-contract.md](../contracts/contextual-vocabulary-contract.md)
