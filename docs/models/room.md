# Room and Merged Room Model

> **Document status: Canonical model.**
> Terminology: [glossary.md](glossary.md). Owning responsibility: **Foundation**.
> Interaction definition lives in [room-configuration.md](room-configuration.md).

---

## Purpose

The Room is the household's interaction context. It is what residents talk to, talk about, and
navigate in the UI.

## Question answered

*Which context is this request about, and which physical places does that context cover?*

---

## The three place concepts

| Concept | What it is | Who uses it |
|---|---|---|
| **Physical Room** | An actual physical space, normally an HA Area | Asset location, maintenance, environmental evidence, sensor provenance, diagnostics, precise facts |
| **Room** | The HTBW interaction context | Residents, voice assistants, Room Help, vocabulary, experiences |
| **Merged Room** | A Room composed of more than one Physical Room | Identical to a Room in behavior |

---

## The behavioral identity rule

**A Room and a Merged Room function the same way from the resident and runtime behavior
perspective.**

> Do not create separate orchestration logic simply because a Room is merged.

There is one Room contract. A Merged Room is a Room whose constituent set has more than one member.
Every rule about vocabulary, participation, exposure, Room Help, modes, experiences, transfer,
suppression, and explanation applies identically.

> **Merged Room composition is owned by Room Configuration.** Foundation defines what a Room and a
> Merged Room *are*; [room-configuration.md](room-configuration.md) declares which Physical Rooms
> constitute a given Room. Both sit inside Foundation, but composition has a single owner.

---

## Merged Room example

**Living Space** may combine:

- Kitchen
- Dining Room
- Living Room

The HTBW UI and runtime treat **Living Space** as a Room context.

The underlying Physical Rooms remain available for:

- Asset location
- Maintenance
- Environmental evidence
- Sensor provenance
- Diagnostics
- More precise facts where required

**Constituent membership is retained. It is never discarded by merging.**

---

## Participation is explicit

A Merged Room may contain multiple participating voice assistants, speakers, lights, lamps, shades,
media devices, sensors, assets, and experiences.

> **Do not assume every asset in every constituent Room automatically participates in the merged Room
> interaction model.**

Participation is declared in [room-configuration.md](room-configuration.md).

If several music speakers are configured to participate as the speaker set for a Room, they are the
configured music destination for that Room. **Do not automatically include every Home Assistant
`media_player`.**

Worked example:

| Device | Disposition |
|---|---|
| Sonos room speakers | Selected as **"Speakers"** — the music destination |
| Sonos Beam (television sound) | Known to the asset model, **intentionally excluded** from the "Play Jazz" destination; still available for television audio |
| LG television | Exposed as **"TV"** |
| Apple TV | Exposed as **"Media Player"** |

---

## Movement inside a Merged Room is not a transfer

**A movement between constituent Physical Rooms inside the same Merged Room must not automatically be
treated as an experience transfer between two different HTBW Rooms.**

Walking from the Kitchen to the Living Room within *Living Space* changes no Room Context. Follow-Me
does not fire. No transfer is evaluated. No suppression is recorded.

Truth may still record the finer-grained Physical Room presence fact, because that fact has value for
diagnostics, environmental attribution, and precision — but the Room Context is unchanged.

---

## Room-scoped state

| Owner | Room-scoped content |
|---|---|
| Room Configuration (Foundation) | Constituent rooms, participation, exclusions, exposure, contextual vocabulary, Room Help definitions, composite-fact input selection, experience endpoints, relevant modes |
| Truth | Occupancy, presence, current activity, active room mode, composite environmental facts, device facts |
| Continuity | Last song played in the room, last genre played in the room, music volume, duck volume, TTS volume, current room experience, room-specific resume state |
| Operational Trust | Room-mode restrictions, privacy modes, quiet-hour restrictions, per-Room authority |
| Stewardship | Obligations attached to the room or to assets serving it, environmental limits to be protected |

---

## Relationship to Home Assistant

A Room normally maps to one or more Areas. Home Assistant has no native equivalent of a Room as an
interaction context, and no native equivalent of a Merged Room.

Per the Home Assistant First principle, HTBW uses Areas as the constituent primitive and adds only
the Room construct that Home Assistant cannot practically represent. See
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md).

An Area may carry a natively assigned temperature or humidity entity. HTBW **consumes** those
assignments rather than building a competing room-sensor mechanism; how they participate in composite
facts is **OD-61**.

> **HTBW Exposure and Home Assistant Assist exposure are different concepts, and Assist exposure
> takes precedence as a platform boundary.** HTBW may narrow it and must never bypass it. The
> canonical explanation is in
> [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md).

---

## Explicit non-responsibilities

The Room model does **not**:

- Establish what is happening in the Room — that is Truth
- Decide what is allowed in the Room — that is Operational Trust
- Store preferences or sessions — that is Continuity
- Decide what should happen — that is Concierge
- Calculate composite facts — Room Configuration selects eligible inputs; **Truth** calculates

---

## Failure behavior

| Condition | Behavior |
|---|---|
| A Room has no constituent Physical Rooms | Invalid configuration; report as a configuration problem |
| A constituent Area is deleted in Home Assistant | Report a broken constituent reference; do not silently shrink the Room |
| A Room has no participating voice assistant | Valid; the Room simply has no default voice context |
| Two Rooms claim the same Physical Room | Permitted only if the household configured it; ambiguity must be surfaced and resolved by explicit configuration, never by runtime preference |

## Privacy considerations

Room membership and occupancy history are sensitive. See
[../architecture/privacy.md](../architecture/privacy.md).

## Explainability requirements

Every Decision Trace records the resolved Room Context and, where relevant, which constituent
Physical Room supplied a fact.

---

## Representative scenarios

- [../scenarios/room-vocabulary.md](../scenarios/room-vocabulary.md)
- [../scenarios/follow-me-media.md](../scenarios/follow-me-media.md)
- [../scenarios/nighttime-suppression.md](../scenarios/nighttime-suppression.md)

## Open decisions

| ID | Question |
|---|---|
| OD-01 | Home Assistant representation strategy for a Room |
| OD-10 | Whether Floors are a first-class HTBW scope |
| OD-11 | Whether a Physical Room may belong to more than one Room, and how ambiguity is configured |

## Related documents

- [room-configuration.md](room-configuration.md)
- [contextual-vocabulary.md](contextual-vocabulary.md)
- [../contracts/room-configuration-contract.md](../contracts/room-configuration-contract.md)
- [truth.md](truth.md)
