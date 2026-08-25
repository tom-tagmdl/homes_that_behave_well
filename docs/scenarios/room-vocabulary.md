# Scenario: Room Vocabulary

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Index: [README.md](README.md).

---

## The household

```
Living Space = Merged Room (Kitchen + Dining + Living)

Shades:        Kitchen 1 + Dining 3 + Living 3 = 7
Speakers:      Sonos music speakers
TV:            LG television
Media Player:  Apple TV
Sonos Beam:    participates as TV audio, EXCLUDED from "Speakers"
Lights:        overhead ceiling fixtures
Lamps:         table and floor lamps
```

Two voice assistants are assigned to the Living Space.

---

## Scenario 1 — One term, seven devices, two assistants

### What the household experiences

Tom stands in the Kitchen and says, "Close the shades." Seven shades close.

David stands in the Living area and says the same thing to the other assistant. The same seven shades
respond, identically.

Neither of them knows there are seven. Neither of them knows which assistant heard them.

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Concierge | Receives the utterance from a voice assistant device |
| 2 | Room Configuration | Resolves the device → its assigned Room → **Living Space** |
| 3 | Contextual Vocabulary | Resolves "shades" in Living Space → the 7 configured shades |
| 4 | Truth | Reports the current state and availability of the resolved targets |
| 5 | Operational Trust | Confirms shade control is permitted here, now, at Autonomous level |
| 6 | Concierge | Closes them, and records the trace |

**The Kitchen and the Living area are constituent Physical Rooms of one Merged Room.** They resolve to
the same Room Context, so both assistants resolve identically. This is not two behaviors that happen to
agree; it is one configuration.

### What the home can say afterwards

> "I closed the shades in the Living Space."

Not: *"I closed `cover.kitchen_1`, `cover.dining_1` …"*

---

## Scenario 2 — A vocabulary term that is a knowledge asset

### What the household experiences

In the Music Room, Tom says, "Tell me about the piano." The home describes a 1918 A.B. Chase 6' grand
piano — its history, its service record, and its humidity requirements.

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves Room Context → **Music Room** |
| 2 | Contextual Vocabulary | Resolves "piano" → the asset *1918 A.B. Chase 6' Grand Piano* |
| 3 | Foundation asset model | Supplies identity, documentation, and declared environmental limits |
| 4 | Stewardship | Supplies obligation state and service history |
| 5 | Truth | Supplies the current Music Room humidity |
| 6 | Operational Trust | Confirms Tom may see appraisal and value content |
| 7 | Concierge | Composes and speaks the answer |

**The vocabulary term did not rename the asset.** "Piano" is an interaction alias in this Room. The
authoritative name is unchanged.

---

## Scenario 3 — Lights are not Lamps

### What the household experiences

"Turn on the lights" turns on the overhead fixtures. "Turn on the lamps" turns on the table and floor
lamps. The household never has to say "turn on the light entities in the light domain".

### Why this matters architecturally

Home Assistant classifies both as `light`. **The platform domain must not dictate household
vocabulary.** The distinction is a household concept, held in Room Configuration, and it survives
regardless of how the platform classifies the devices.

| Term | Resolves to |
|---|---|
| Lights | explicitly selected overhead ceiling fixtures |
| Lamps | explicitly selected table and floor lamps |

---

## Scenario 4 — Speakers are not TV audio

### What the household experiences

Tom says, "Play music on the speakers." The Sonos music speakers play. **The Sonos Beam does not.**

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves Room Context → Living Space |
| 2 | Contextual Vocabulary | Resolves "speakers" → the Sonos music speakers only |
| 3 | Room Configuration | Confirms the Beam **participates** as TV audio and is **excluded** from "Speakers" |
| 4 | Concierge | Plays on the resolved targets only |

The Beam **exists**. It **participates**. It is **not exposed** under this term. Those are three
different states, and the exclusion is configuration, not an error.

### If Tom asks why

> "The Beam is deliberately not part of *Speakers* in this room — it's set up for TV audio. Would you
> like me to use it anyway?"

Home Assistant classifies the Sonos speakers, the Beam, the LG television, and the Apple TV all as
`media_player`. HTBW distinguishes **Speakers**, **TV**, and **Media Player**. **This household
distinction is preserved.**

---

## Scenario 5 — Room Help

### What the household experiences

Tom says, "What can I do here?" The home answers with what is actually available in the Living Space,
in household language:

> "Here you can control the lights, the lamps, the shades, the speakers, the TV, and the media player.
> You can also ask about the artwork."

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves Room Context → Living Space |
| 2 | Room Configuration | Returns the **configured exposed capability set** and the exposed-term list |
| 3 | Operational Trust | Filters by who is asking — a child or guest may see less |
| 4 | Concierge | Speaks the answer in household language |

> **Room Help must be derived from the configured exposed capability set and vocabulary, never generated
> from raw device inventory.**

The Beam is not offered. The individual seven shades are not enumerated. The Room Help answer, the panel,
and the voice surface all present **the same exposed set** — one configuration, many surfaces.

---

## Scenario 6 — A Composite Fact for room environment

### What the household experiences

Tom asks, "How warm is it in here?" The home says 72 degrees. It does not read out three sensors.

### What each responsibility does

| Step | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Declares which sensors are **eligible contributors** to Living Space temperature |
| 2 | Truth | Calculates the composite fact, with confidence, provenance, freshness, and coverage |
| 3 | Concierge | Reports the authoritative fact |

```
Truth: Living Space temperature = 72 degrees
       confidence: high
       coverage:   2 of 2 eligible contributors reporting
       provenance: Sensor A (71.6), Sensor C (72.4)
```

**Room Configuration does not calculate Truth. Truth does not own the sensor inventory. Concierge does
not choose sensors at runtime.**

### If a sensor fails

> "It's about 72 degrees, though one of the sensors in the Living Space isn't reporting right now."

Coverage drops, confidence drops, and the resident hears about it. Uncertainty survives the pipeline.

---

## Scenario 7 — A term that is not configured here

### What the household experiences

In the Den, Tom says, "Close the shades." The Den has no configured shades.

### What the home does

> "There aren't any shades configured in the Den. In here you can control the lights, the speakers, and
> the TV."

**The home does not search the house for anything called a shade.** It does not guess. It does not close
the Living Space shades. It states what is configured, and offers what is available.

---

## Scenario 8 — Native names and aliases seed the configuration

The household has already named things in Home Assistant. **They are not asked to do it again.**

| # | Situation | What happens |
|---|---|---|
| 8a | An Entity becomes eligible, has a native name, and has no HTBW term | The native value is offered as the **seed**. Home Assistant stays authoritative for its own name. **HTBW creates no independently maintained duplicate merely to reproduce the same value**, and nothing is written back |
| 8b | The Entity also has an applicable native Assist alias | The alias may be presented as a selectable seed, attributed to Home Assistant. **Accepting or editing the term does not modify the native alias.** Where several aliases apply, none is chosen silently |
| 8c | Tom customizes *Desk Lamp* to **"Lamp"** in the Office | "Lamp" becomes Office contextual vocabulary. The native name and aliases are **unchanged**. Office Room Context resolves the target |
| 8d | The native Entity is later renamed | The new native name is read from Home Assistant. **The customized term stays "Lamp".** HTBW may say the native source changed and offer re-import. **Nothing is overwritten in either direction** |

---

## Scenario 9 — The same term in several Rooms

"Lamp" is configured in the Office, the Guest Room, and the Living Space.

| Room | "Lamp" resolves to |
|---|---|
| Office | the configured Office lamp target |
| Guest Room | the configured Guest Room lamp target |
| Living Space | a **configured group** of participating lamps |

Each Room resolves the term through its own configuration. **Reuse across Rooms is not an error** —
it is the point. **No native alias is written to any target**, and the Living Space group is
**not** projected as an alias onto each member. Explicit exclusions stay excluded.

This is exactly what a native alias cannot carry: one of these three targets is a group, and all
three depend on Room context that Home Assistant does not model.

---

## Scenario 10 — A Device with several Entities

The LG television is one native Device with many Entities — power, source, volume, and diagnostics.

**A Device-level term is not assumed to apply to every Entity.** The configuration identifies the
actual target or capability participating, native Device and Entity relationships remain
authoritative, and the mapping stays deterministic. **"TV" does not silently mean "everything this
Device offers".**

---

## Scenario 11 — Native Assist exposure is turned off

Home Assistant exposure is removed from a participating Entity.

| State | Result |
|---|---|
| Native Assist exposure | Withdrawn. **The platform boundary moves** |
| HTBW participation | Unchanged |
| HTBW contextual exposure | Unchanged as configuration |
| Authority | Unchanged |

**The contextual term does not bypass the native restriction.** Room Help does not advertise a native
Assist capability the platform will not honour, or one the asking resident is not authorised to know
about. Four distinct states — **never one checkbox.**

---

## Scenario 12 — Merging, and a deleted target

| # | Situation | What happens |
|---|---|---|
| 12a | The Kitchen and Living Rooms are combined | Native names and aliases are **unchanged**. Merged vocabulary is **declared**, not inherited automatically. Where constituents used one term for different targets and the merged configuration is silent, the result is `ambiguous` and is surfaced. **No alias synchronisation occurs.** **OD-70 remains open** |
| 12b | The Merged Room is later unmerged | Constituent membership was retained, so constituent Room behaviour is restored. Native objects were never touched |
| 12c | A native target is deleted outside HTBW | The reference becomes **unresolved** and follows the Repairs and broken-reference boundary. **The customized term is never automatically reassigned to another object**, and historical references are not rewritten |

---

## Scenario 13 — One configured term, several recognised forms

Tom configures **Lamp** in the Office. He configures nothing else.

| # | Situation | What happens |
|---|---|---|
| 13a | "Turn on the lamp" | The configured term matches directly |
| 13b | "Turn on the **lamps**" | Recognised as a form of *Lamp*, resolving to **the same configured target** — not to more targets |
| 13c | Tom opens the Office configuration | He sees *Lamp*, and alongside it that *Lamps* will be understood. **Only *Lamp* is editable.** There is no plural field to fill in, and none to keep in step |
| 13d | The same configuration for **Shade** | *Shade* and *Shades* are both understood. **No separate plural entry exists** |

**The resident maintains one value. The home derives the rest.**

---

## Scenario 14 — The plural that is a group

In the Living Space the household configured **Lamps** deliberately, as the Corner Lamp, the Sofa
Lamp, and the Bookcase Lamp. The Office still has **Lamp**, meaning one desk lamp.

| Room | "Turn on the lamps" resolves to |
|---|---|
| Living Space | The **configured group** — three lamps. A configured term always outranks a derived form |
| Office | The **single configured target**, matched through a derived form. **Saying the plural did not add lamps to the Room** |

**These are different concepts and the repository keeps them apart.** *Lamps* as a grammatical form of
*Lamp* means the same thing said differently. *Lamps* as a group term means a larger, explicitly
configured target set. **Plurality alone never creates the group** — someone configured it.

If a word matched derived forms of two configured terms and no configured term, the result is
`ambiguous` and the home asks. It does not pick one.

---

## Scenario 15 — Explaining what was heard

Tom says *"Turn on the lamps"* in the Office.

| Recorded | Value |
|---|---|
| Recognition form heard | Lamps |
| Authoritative vocabulary | Lamp |
| Resolved target | The configured Office lamp target |
| Room Context | Office |

And the home simply says: *"I turned on the lamp in the Office."* **The explanation is available
without the resident needing to know anything about grammar, derivation, or entity IDs.** Where a
separate group configuration governs the word, that configuration is what is recorded and explained
instead.

---

## Responsibilities exercised

| Responsibility | Exercised by |
|---|---|
| Foundation | Asset identity, Room and Merged Room object definitions |
| Room Configuration | Merged Room composition, participation, exclusion, exposure, eligible contributors, Room Help |
| Contextual Vocabulary | Term → target resolution in every scenario |
| Truth | Composite temperature, availability, current state |
| Stewardship | Piano service history and obligations |
| Operational Trust | Room Help filtering, permission to act |
| Concierge | Interpretation, execution, explanation |

## Related documents

- [../models/room-configuration.md](../models/room-configuration.md)
- [../models/contextual-vocabulary.md](../models/contextual-vocabulary.md)
- [../contracts/room-configuration-contract.md](../contracts/room-configuration-contract.md)
- [../architecture/adr-room-configuration-ownership.md](../architecture/adr-room-configuration-ownership.md)
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
