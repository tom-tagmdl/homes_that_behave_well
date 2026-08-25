# Truth Model

> **Document status: Canonical model.**
> Terminology: [glossary.md](glossary.md). Owning responsibility: **Truth**.
> Contract: [../contracts/truth-contract.md](../contracts/truth-contract.md)

---

## Purpose

**Truth is a first-class authoritative fact engine.**

Truth is not a section of Foundation. Foundation defines what a *Fact* is. **Truth decides what is
factual now.** Any document stating that Foundation owns truth is superseded.

## Question answered

*What is actually true now?*

---

## Consumes

Evidence and assertions from:

- Devices and sensors
- Assets
- Identity (identity assertions only — never biometric internals)
- Voice events
- BLE events
- Media systems
- Calendars, where authorized
- Environmental sources
- Room Configuration (which evidence is eligible for which composite fact)
- Other governed sources

---

## Owns

Authoritative facts, including:

- Presence facts
- Occupancy facts
- **Location facts**
- Environmental facts
- **Engagement facts**
- Device facts
- Contextual facts
- Room-state facts
- Active-room-mode facts
- Current-activity facts
- Composite facts derived from more than one contributing sensor
- Evidence freshness
- Fact confidence or certainty
- Provenance
- Fact validity and expiration

Examples:

- Tom is present in the Den.
- The Living Space is occupied.
- Maisey is in the Living Room.
- Tom's phone is in the Den.
- A conversation is active.
- An interaction is in progress through the Kitchen voice assistant.
- Music is already playing.
- The television is in use.
- The Primary Bedroom is in Nighttime mode.
- The room temperature is 72 degrees.
- The garage door is open.
- The room moved from occupied to unoccupied.

---

## Fact structure

Every fact carries at minimum:

| Element | Purpose |
|---|---|
| Subject | What the fact is about. See **Fact Subjects** below |
| Statement | What is asserted |
| Confidence | Degree of belief |
| Provenance | Contributing evidence and its sources |
| Freshness | When the underlying evidence was observed |
| Validity | When the fact expires or must be re-established |
| Coverage | For Composite Facts, how many eligible contributors reported |

A fact whose confidence, provenance, or freshness cannot be stated is not a fact.

### Fact Subjects

A Fact is **subject-typed**. The Subject is the Foundation object the Fact is about, referenced by its
stable identifier under **DL-31**.

| Subject | Notes |
|---|---|
| **Home** | The outermost governed scope |
| **Room** | The interaction context |
| **Merged Room** | A Room whose constituent set has more than one member. **A Room and a Merged Room behave identically** (**DL-13**); the finer-grained **Constituent Room** remains available where a more precise Fact is warranted |
| **Person** | See the two-stage rule below |
| **Pet** | A Foundation object with its own obligations. **A Pet is not a Person** |
| **Asset** | Device-backed or not |
| **Device** | A referenced Home Assistant Device or Entity. **Referenced, never duplicated** |

> **This enumeration extends the existing Fact. It creates no parallel assertion types.** There is no
> `PersonLocationAssertion`, `PetLocationAssertion`, `AssetLocationAssertion`, `DeviceLocationAssertion`,
> `CurrentEngagerAssertion`, or `EngagementContext` model, and none may be introduced. **Truth remains the
> single extensible model**, with one owner, one lifecycle, one provenance model, one conflict model, and
> one retention rule (**DL-47**).

**Confidence representation across every Subject and Fact class is open decision OD-74.** The four
Identity confidence bands are **DL-39** and describe *only* the strength of support for a `known`
known-Person **Identity Assertion**. **They are not Truth Fact confidence and must not be borrowed for
one.**

---

## Location facts

A **Location Fact** is a Fact whose Statement places its Subject somewhere in the Home **now**.

> **Declared location and current location are different things with different owners, and collapsing
> them is a defect.**

| | Declared Location | Current Location |
|---|---|---|
| What it is | A configured, durable statement of where something belongs or is kept | An evidence-derived, confidence-bearing statement of where something **is now** |
| Owner | **Foundation** — the `located-in` relationship | **Truth** — a Location Fact |
| Authority | [../contracts/foundation-contract.md](../contracts/foundation-contract.md) | This model |
| Changes when | The household reconfigures it | Evidence changes |
| Carries confidence | No. It is a definition | **Yes**, with provenance, freshness, validity |
| When unrecorded | Foundation reports `unknown` — *"an asset with no known location"* | Truth publishes `unknown`. **Never default to a Room** |

**Foundation does not confirm current state** ([../contracts/foundation-contract.md](../contracts/foundation-contract.md)),
and **Truth does not own the object definition**. A declared location is *evidence* toward a Location
Fact where a household governs it that way; it is never itself the Fact.

### The Person asymmetry

| Subject | Requires an Identity Assertion first? | Why |
|---|---|---|
| **Person** | **Yes, always** | *Which human* is a fusion question over a bounded candidate set of known Persons. **DL-06**, **P9**. The result is the **Contextual Person-Presence Fact** |
| **Pet, Asset, Device** | **No — and must not** | There is no *which human* question. Identity's candidate set contains **known Persons only**, and **DL-39** bands describe identity support only. **Routing a pet tag or a device tracker through Identity is a category error** |

> *"Where is Maisey?"* and *"Where is my phone?"* are **Truth-only** questions.
> *"Where is Tom?"* is a **two-stage** question.

### What each source may establish about a non-Person Subject

**Reliability is not a property of an evidence type**, and what a source can *establish* is bounded by
what it actually observes. Under **P21** and **DL-30**, a Room-granularity claim requires evidence whose
Room granularity is **actually grounded**; where it is not, no Room-level Location Fact is asserted.

| Evidence source | May support | Never establishes on its own |
|---|---|---|
| Native `device_tracker` | Presence of the **device** at **zone** granularity — `Home`, `Not home`, a zone name | A Room or Area; **that the bound Person is with the device** |
| Connection-type tracker | The device is associated with a network, with its zone treated as a documented **assumption** | Physical location; a Room |
| Room-scoped proximity or beacon evidence | Device or tag proximity to a Room, **only where Room-level detection is genuinely grounded** | Which Person is holding it; which Person is in the Room |
| Pet-worn tag or collar | That a **tagged object** is where the tag is observed | That the Pet is wearing it; **any human identity**; Room Presence for a Person |
| Tag scan | That an object was scanned, by which device, at what time | Who scanned it; where the object is between scans |
| Declared `located-in` | Where the household **keeps** the thing | Where it is now |
| Room occupancy or presence sensor | That the Room is occupied; corroboration of context | **Which** Person, Pet, or Asset |

**The device-left-behind case is the governing example.** A phone observed in the Den supports *the phone
is in the Den*. It supports *Tom is in the Den* only through **Identity**, at that family's ceiling, and
it **never** establishes that Tom is holding it. **A tag removed from a pet, and a pet that has moved a
tag, are contradiction cases** handled under *Conflicting evidence* below and governed by **OD-19**.

### Disclosure warning

> **A device-location Fact is frequently a person-location disclosure, and a pet-location Fact is
> frequently a human-movement disclosure.** Truth publishes the Fact; **Operational Trust decides whether
> it may be conveyed, to whom, on which surface** (**DL-34**, **P32**). See
> [operational-trust.md](operational-trust.md) and [../architecture/privacy.md](../architecture/privacy.md).

---

## Engagement facts

An **Engagement Fact** is a Fact stating that **an interaction is occurring** — nothing more.

It may carry:

- The **interaction channel** — voice, kiosk, Companion App, browser session, physical control
- The **interaction surface** — the participating device or endpoint, referenced by its native identifier
- The **Room Context**, where one has been resolved, and **`unresolved` where it has not**
- **Freshness** — when the interaction was observed
- **Provenance** — which native event or governed source reported it
- **Whether a human participant is supported**, where an Identity Assertion has independently reported it

> **An Engagement Fact must never identify the engaging Person.**

| An Engagement Fact is | An Engagement Fact is not |
|---|---|
| A Truth Fact about the world | An Identity Assertion |
| A statement that an interaction is in progress | A statement of **who** is interacting |
| Channel, surface, Room, freshness, provenance | A candidate Person, a confidence band, or a fusion result |
| Consumable as **corroborating context** by Identity, at that family's ceiling | A source that may **nominate a candidate** |

**Two rejections are explicit and constitutional:**

- **Engagement Fact is not Identity.** Who is engaging is answered by a purpose-specific **Identity
  Assertion** — Speaker Attribution, Interaction Initiator, Authenticated Session Identity, or Endpoint
  Context — produced by **Identity alone** (**DL-32**, **DL-38**).
- **Engagement Fact is not "Current Engager".** *Current Engager* is **not an HTBW architectural term** and
  must not be introduced. A single fused engager result would recreate the general-purpose identity score
  that **DL-32** and **DL-38** prohibit. See [glossary.md](glossary.md).

**Endpoint Context remains Identity's**, and it identifies a **thing, not a person**
([person-and-identity.md](person-and-identity.md)). An Engagement Fact and an Endpoint Context assertion
may describe the same interaction from two sides; **they are not interchangeable and neither replaces the
other.**

Where the interaction arrived through a surface that is **not bound to a Room**, the Engagement Fact
records the Room Context as **`unresolved`**. **How such a Room Context may be resolved at all is open
decision OD-73**, and nothing in this section resolves it.

---

## Composite facts

Truth may use multiple eligible contributing sensors to establish a single **Composite Fact**.

> "Composite Fact" concerns the combination of **evidence**. It is unrelated to the superseded term
> "Composite Room" (now **Merged Room**), which concerns the combination of Physical Rooms. A Composite
> Fact may be scoped to a Room or to a Merged Room. See [glossary.md](glossary.md).

```
Room Configuration:  eligible contributors for Living Space temperature = Sensor A, Sensor C
Truth:               Living Space temperature = 72 degrees
                     confidence: high
                     coverage:   2 of 2 eligible contributors reporting
                     provenance: Sensor A (71.6), Sensor C (72.4)
```

Residents ordinarily receive the authoritative composite fact rather than a list of raw sensor
readings. Raw evidence remains available for diagnostics, provenance, calibration, and explainability
where authorized.

Boundaries:

- **Room Configuration does not calculate Truth.**
- **Truth does not own the sensor inventory.**
- **Concierge does not choose sensors at runtime.**

The specific aggregation algorithm — mean, median, weighted, primary-with-fallback — is **not decided
here**. Open decision **OD-17**.

---

## Identity assertions become presence facts

```
Identity asserts:        candidate Tom, confidence 0.94, evidence voice + BLE + phone
Room Configuration says: the Den's occupancy evidence sources are X and Y
Truth establishes:       Tom is present in the Den (confidence, provenance, validity)
```

The identity assertion is evidence. The presence fact is Truth. They are different objects with
different owners.

**Truth receives the assertion only.** Biometric internals never cross this boundary, so Truth has
nothing to store or expose. See [person-and-identity.md](person-and-identity.md).

**Truth never fuses identity evidence.** It does not re-weight, re-combine, or recompute an assertion,
and it does not reach past the assertion to the evidence behind it in order to reach a different
conclusion about who someone is. Truth consumes the assertion as **one input** among the Room's
configured occupancy evidence, and produces a Fact about the world (**DL-06**, **DL-38**).

### The direction is one-way, and it is not a cycle

This boundary is frequently misread as circular. It is not, and the misreading is worth stating plainly
because it inverts two accepted decisions.

| Statement | Correct? |
|---|---|
| **Identity produces Identity Assertions** | ✅ Identity alone. *"Identity performs fusion. No other responsibility does."* |
| **Truth consumes Identity Assertions** | ✅ As **one input**, among the Room's configured occupancy evidence |
| **Truth produces Contextual Person-Presence Facts** | ✅ *Tom is present in the Den* is a **Truth** Fact |
| **Truth determines identity** | ❌ **Never.** *Which human* is Identity's question |
| **Truth re-runs identity fusion** | ❌ **Never.** Truth does not re-weight, re-combine, or recompute an assertion |
| **Identity consumes a Truth person-presence Fact to decide who is engaging** | ❌ **Never.** This inverts **DL-06** and **P9** |

> **Truth establishes *occupancy* — a Room-subject Fact — before fusion. Truth establishes *person
> presence* — a Person-subject Fact — only *after* fusion, from the assertion.** These are two different
> Fact Subjects at two different points, and reading them as one object is what creates the illusion of a
> loop.

Only one feedback path exists, and it is bounded on four sides:

```text
sensor / voice / BLE / tracker evidence
        ↓
Identity  →  purpose-specific Identity Assertion
        ↓
Truth     →  Contextual Person-Presence Fact          (Person subject)

Truth     →  Room occupancy Fact                      (Room subject)
        ↓
        └── may re-enter a LATER Identity fusion as ONE evidence family only
```

| Guarantee | Why the path cannot close into a cycle |
|---|---|
| **Subject separation** | Only the **Room-subject occupancy** Fact re-enters fusion. A **Person-subject** presence Fact never does, so no fusion consumes its own output |
| **Ceiling (F1)** | Room occupancy may support *"that the Room is occupied; corroboration of context"* and **never** *"which Person; who spoke; who initiated"* |
| **Candidate-set exclusion** | Occupancy is **not** an admissible source of a candidate Person. *"Occupancy is not identity"* |
| **Version referencing (P30, DL-27)** | Every stage references the **exact prior version** it used, so an evaluation cannot consume a result it has not yet produced |

**Continuous occupancy is not continuous identity.** A Room may remain occupied while its occupants
change entirely; a prior assertion, band, or confirmation is never revived because presence persisted
(**DL-39**). See [person-and-identity.md](person-and-identity.md) and
[../architecture/dependency-view.md](../architecture/dependency-view.md).

---

## Fact lifecycle and Historical Facts

**Truth is the system of record for both present and historical Facts** (**P28**).

Operational expiration removes a Fact from *what is true now*. It does **not** automatically delete
*what was true then*. This completes the qualifier already present in this model's failure table:
*"do not retain the last value **as current**"* — which has always presupposed that historical
retention is a different question from operational currency.

### The eight lifecycle transitions

Each must be **separately reconstructable**:

| Transition | Meaning |
|---|---|
| Established | The Fact came into being |
| Confirmed | Further evidence supported it without changing the statement |
| Confidence changed | The degree of belief moved |
| Superseded | A newer Fact replaced it |
| Withdrawn | Evidence was contradicted or invalidated |
| Operationally expired | Validity elapsed; the Fact left *what is true now* |
| Became unknown | Nothing could be asserted |
| Became unresolved | Candidates conflicted with no governed resolution |

A transition is recorded as a **Change Record** under the shared temporal model. See
[temporal-record.md](temporal-record.md).

### What a Historical Fact retains

Where policy permits: Subject, Statement, confidence **at the time**, Provenance, evidence references
or evidence classes, Coverage, Freshness, and lifecycle transitions.

A Historical Fact is **not** a retained raw evidence payload. Evidence is referenced, not copied
(**P30**).

### What a Historical Fact must never be

- Never presented as current
- Never actionable
- Never silently promoted back to current

Re-establishing a Fact requires new evidence and a new lifecycle transition. A Historical Fact does
not revive.

### Ownership

**Truth owns Fact history. No consumer may maintain a competing or re-derived Fact history.** A
consumer that keeps its own record of what Truth used to say has created a second fact engine, which
**P8** and **DL-04** prohibit.

Retention for Historical Facts is settled by **DL-47**: they are governed history following External
History Retention, carrying their own Retention Classification. **Per-Fact-class differentiation is
an Operational Trust policy matter, not architecture.**

### Governing parent, cleanup, and retention by Subject

**DL-43** required a declared lifecycle before an artifact could exist; **DL-47** extended that
obligation to every governed record class; **DL-45** requires every record to declare a **governing
parent** and a **Parent Removal Behavior**, whose ordinary default is **cleanup when the parent
disappears**. Location, Presence, and Engagement Facts are governed record classes and are therefore
bound by all three. **No new responsibility, artifact class, or store is created by this table.**

| Fact Subject | Governing parent | Retention | Parent Removal Behavior |
|---|---|---|---|
| **Person** | The **Person** (native Person by reference, **DL-31**) | Truth-owned governed history following External History Retention, own Retention Classification (**DL-47**) | Person deletion enumerates and removes dependent Facts and their history, subject to Preservation Holds, retention floors, and the versions required to keep a held Decision Trace explainable |
| **Pet** | The **Pet** (Foundation object) | As above | **Pet removal cleans up Pet-subject Facts and their history** on the same terms as a Person. A tag or collar is **evidence, not the parent** \u2014 removing the tag withdraws current Facts and never deletes history |
| **Asset** | The **Asset** \u2014 already the governing parent of its documentation (**DL-45**) | As above | Asset deletion removes Asset-subject Facts on the same terms already accepted for Asset documents |
| **Device** | The **Person, Asset, or Room** the Device is governed through | As above | **A referenced native Device is never deleted by HTBW** (**DL-31**). Its removal outside HTBW produces a **broken reference**, which is **reported**, withdraws current Facts, and **never rewrites history** |
| **Room, Merged Room, Home** | The Room, Merged Room, or Home | As above | A deleted constituent Area produces a broken constituent reference, **reported, never a silent shrink** |

Four rules bind every row:

- **Retention and parent cleanup are distinct mechanisms** (**DL-45**). Neither substitutes for the other,
  and a Fact class may be subject to both.
- **Cleanup never silently overrides** a Preservation Hold, a retention floor, an Evidence Package
  lifecycle, or historical explainability (**P27**).
- **Cleanup is not claimed while a required dependency is unavailable.** A governed pending-cleanup state
  is retained and reconciled when the dependency returns.
- **Native objects follow their own lifecycle** and are never removed because an HTBW record was cleaned.

**Withdrawing consent for an evidence source is not deletion of history.** Consent withdrawal renders the
source **ineligible** \u2014 excluded before weighting \u2014 and current Facts depending on it are withdrawn or
reduced. **An earlier Fact remains historically true and remains explainable**; later explanations report
that the evidence source no longer exists, and never restate the past as though it did not happen.

**Nothing here authorises a second store.** Location and Engagement Facts reference native state as
evidence; **HTBW builds no second Recorder and no second device tracker** (**DL-42**, **DL-46**).

---

## Truth must not

- Trigger actions
- Control devices
- Make resident-facing behavioral decisions
- Own preferences
- Own authority or permission
- Hide uncertainty
- Automatically convert weak evidence into a definitive fact

---

## Conflicting evidence

**Concierge does not resolve "competing Truths" by inventing a preferred fact.** If evidence or facts
conflict, Truth preserves or resolves the uncertainty according to this contract.

Permitted outcomes when evidence conflicts:

| Outcome | When |
|---|---|
| Resolve to a single fact with reduced confidence | A governed resolution rule applies and is recorded |
| Publish an unresolved fact | No resolution rule applies; both candidate statements are reported |
| Publish `unknown` | Nothing can be asserted |
| Withdraw a fact | Prior evidence is stale or contradicted |

Prohibited: silently selecting the most recent, the highest-confidence, or the most convenient
evidence without recording that a conflict existed.

### Location conflict cases

Location Facts generate a recurring family of conflicts. **All of them are preserved and explainable,
never hidden**, and the governed resolution rules for them are **OD-19**.

| Case | Required treatment |
|---|---|
| **Device left behind** | The device-location Fact stands; it supports **no** Person-location claim. Identity applies the family ceiling. Do not promote *the phone is in the Den* into *Tom is in the Den* |
| **A Person's associated devices are in different Rooms** | Contradiction is **claim-specific** and is retained. Publish reduced confidence or `unresolved`; never average the Rooms |
| **A pet has moved, removed, or shed its tag** | The tag-location Fact stands for the **tag**; the Pet-location Fact is reduced, `unresolved`, or `unknown`. **A tag is not the Pet** |
| **A tag is worn by a different animal or carried by a person** | Same treatment. The Subject of the Fact is what the evidence actually observes |
| **Declared and current location disagree** | **Current location prevails as the Fact.** The declared `located-in` relationship is unchanged and is never rewritten by an observation |
| **Zone-level evidence conflicts with Room-level evidence** | The **zone** claim and the **Room** claim are different granularities, not two answers to one question. Publish at the granularity the evidence actually grounds |
| **Multiple people in one Room** | Occupancy remains true; **no single Person follows from it**. Person-presence requires its own assertion per Person |
| **All contributing sources become unavailable** | Publish `unknown`. **Never retain the last known location as current** |

---

## Provides

- Facts with confidence, provenance, freshness, validity, and coverage
- Fact-change notifications, including transitions such as occupied → unoccupied
- Unresolved and unknown states as first-class outputs
- Diagnostic access to contributing raw evidence, where authorized

---

## Explicit non-responsibilities

Truth does **not** own: identity (Identity), obligations (Stewardship), preferences and sessions
(Continuity), policy and authority (Operational Trust), decisions and actions (Concierge), the sensor
inventory (Foundation asset model), or which sensors are eligible (Room Configuration).

---

## Failure behavior

| Condition | Behavior |
|---|---|
| A contributor is unavailable | Recompute from remaining contributors, reduce confidence, record reduced coverage |
| All contributors unavailable | Publish `unknown`; do not retain the last value as current |
| Evidence stale | Mark stale, reduce confidence, or withdraw |
| Sources disagree | Preserve the disagreement; publish unresolved or reduced-confidence fact |
| A room transition is missed | Do not retroactively invent a transition; treat the newly observed Room as current and record the gap |

## Privacy considerations

Presence and occupancy facts, and their history, are highly sensitive. Visibility is governed by
Operational Trust policy. See [../architecture/privacy.md](../architecture/privacy.md).

Historical Facts are bounded from both directions: **P27** establishes a retention floor, and
[../architecture/privacy.md](../architecture/privacy.md) establishes the ceiling. Where they
conflict, privacy governs, and the resulting limitation is itself recorded rather than left silent.
Historical Facts may be redacted; a redacted Historical Fact **remains a record** that the Fact
existed and made the transitions it made.

## Explainability requirements

Every fact used in a decision appears in the Decision Trace with its confidence, provenance, and
freshness. A fact that was *unknown* and therefore blocked an action must appear as well.

A Decision Trace references the **exact version** of each Fact it used (**P30**), so an explanation
remains accurate after the Fact has since changed, expired, or been withdrawn.

---

## Representative scenarios

- [../scenarios/where-is-tom.md](../scenarios/where-is-tom.md) (person location — the two-stage path)
- [../scenarios/where-is-maisey.md](../scenarios/where-is-maisey.md) (pet location — Truth-only)
- [../scenarios/where-is-my-phone.md](../scenarios/where-is-my-phone.md) (device location — Truth-only)
- [../scenarios/nighttime-suppression.md](../scenarios/nighttime-suppression.md)
- [../scenarios/stewardship-obligations.md](../scenarios/stewardship-obligations.md)
- [../scenarios/why-did-this-happen.md](../scenarios/why-did-this-happen.md)

## Open decisions

| ID | Question |
|---|---|
| OD-17 | Composite-fact aggregation algorithm and coverage thresholds |
| OD-18 | Fact validity and expiration defaults per fact class — this governs **operational** validity, not Historical Fact retention, which is settled by **DL-47** |
| OD-19 | Governed conflict-resolution rules for disagreeing evidence, **including the location conflict cases above** |
| OD-73 | **Interaction-Surface Room Context Resolution.** How Room Context is resolved for a phone, wearable, Companion App, browser session, or other non-room-bound surface. An Engagement Fact records Room Context as `unresolved` until this closes |
| OD-74 | **Truth Fact Confidence Representation.** How Fact confidence is represented across every Fact class and Subject. **The DL-39 Identity bands are not available for this and must not be borrowed** |
| OD-33 | **Closed — DL-43, DL-46, DL-47.** Historical Facts follow External History Retention with their own Retention Classification; per-Fact-class differentiation is Operational Trust policy |
| OD-34 | **Closed — DL-42, DL-44, DL-46, DL-47.** The temporal-persistence model is complete; the representation mechanism is **OD-01** |

## Related documents

- [room-configuration.md](room-configuration.md)
- [person-and-identity.md](person-and-identity.md)
- [temporal-record.md](temporal-record.md)
- [../contracts/truth-contract.md](../contracts/truth-contract.md)
- [../architecture/adr-historical-explainability-and-historical-truth.md](../architecture/adr-historical-explainability-and-historical-truth.md)
- [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md)
