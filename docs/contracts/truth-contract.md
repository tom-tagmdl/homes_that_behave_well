# Truth Contract

> **Document status: Canonical contract.**
> Responsibility: **Truth**. Model: [../models/truth.md](../models/truth.md).

---

## Owning responsibility

**Truth — what is actually true now?**

**Truth is a first-class authoritative fact engine.** It is not a section of Foundation. Foundation
defines what a Fact *is*; Truth decides what is factual now. Any document stating that Foundation owns
truth is superseded by this contract.

---

## What Truth guarantees

Every published fact carries:

| Element | Guarantee |
|---|---|
| Subject | What the fact is about |
| Statement | What is asserted |
| Confidence | Degree of belief |
| Provenance | Contributing evidence and its sources |
| Freshness | When the underlying evidence was observed |
| Validity | When the fact expires or must be re-established |
| Coverage | For composite facts, how many eligible contributors reported |

**A statement whose confidence, provenance, or freshness cannot be given is not published as a fact.**

### Fact Subjects

A Fact is **subject-typed**, and the Subject is a Foundation object referenced by its stable identifier
(**DL-31**).

**Home · Room · Merged Room · Person · Pet · Asset · Device**

> **This is one extensible model, not seven.** Truth guarantees that no parallel assertion type exists for
> any Subject. There is no `PersonLocationAssertion`, `PetLocationAssertion`, `AssetLocationAssertion`,
> `DeviceLocationAssertion`, `CurrentEngagerAssertion`, or `EngagementContext` model, and consumers must
> not construct one.

**Confidence representation is DL-58 (resolved OD-74).** The four Identity confidence bands are
**DL-39**, describe *only* the strength of support for a `known` **Identity Assertion**, and **are not
Truth Fact confidence.**

### Truth Confidence Band guarantee (DL-58)

| Guarantee | Statement |
|---|---|
| Definition | Truth Confidence describes the strength of qualified evidentiary support for a Fact under the applicable Truth evaluation policy — never probability, measured accuracy, certainty, or an authorization |
| Representation | One uniform ordinal band — **Low < Moderate < High < Very High** — applied identically across every Fact Subject and Fact class. Per-class derivation may differ; the vocabulary does not |
| Structural separation | A **Truth Confidence Band** and a **DL-39 Identity Confidence Band** are separately owned, separately typed (`truth_confidence_band` vs `identity_confidence_band`), and never converted, averaged, or compared as though they measured the same thing |
| Non-Person Subjects | A Pet, Asset, or Device Fact is **structurally unable to carry an Identity Confidence Band** |
| Independence | Confidence is independent of freshness (**OD-18**), provenance, and contributor coverage (**OD-17**) — four separate mandatory Fact dimensions |
| Comparability | Ordinal and semantic across Fact classes; **never arithmetic** — bands are never added, averaged, multiplied, or subtracted |
| Optional numeric | May accompany the band as a non-authoritative deterministic ordering value only; never resident-facing probability, likelihood, calibration, or accuracy; none is mandated |
| Historical Facts | Every Historical Fact retains its Truth Confidence Band and the policy version that produced it; a later policy change never rewrites a prior Fact |

---

## Fact classes

Presence, occupancy, **location**, environmental, **engagement**, device, contextual, room-state,
active-room-mode, current-activity, Composite Facts, and fact transitions such as occupied → unoccupied.

### Location Facts

| Guarantee | Statement |
|---|---|
| Declared and current are separate | **Foundation** owns the declared `located-in` relationship. **Truth** owns the current Location Fact. A declared location is evidence at most, never the Fact |
| Person location is two-stage | A Person-subject Location Fact is the **Contextual Person-Presence Fact** and requires an Identity Assertion first (**DL-06**, **P9**) |
| Pet, Asset, and Device location are Truth-only | They require **no** Identity Assertion and **must not be routed through Identity**. Identity's candidate set contains known Persons only |
| Granularity is not inflated | A Room-level Location Fact is published only from evidence whose Room granularity is **actually grounded** (**P21**, **DL-30**). Zone-level evidence yields a zone-level Fact |
| A device is not its owner | A device-location Fact **never** establishes the location of the Person bound to it |
| A tag is not its wearer | A tag-location Fact **never** establishes that a Pet is wearing the tag, and **never** establishes any human identity |
| Unknown is first-class | Where nothing can be asserted, Truth publishes `unknown`. **It never defaults to a Room and never retains the last known location as current** |

### Engagement Facts

| Guarantee | Statement |
|---|---|
| What it states | That **an interaction is occurring** — and may carry channel, interaction surface, Room Context, freshness, and provenance |
| What it never states | **Who is engaging.** An Engagement Fact must not identify the engaging Person |
| Not an assertion | **Engagement Fact is not Identity**, and it never nominates a candidate Person. It may corroborate context at its family's ceiling and no further |
| Not "Current Engager" | ***Current Engager* is not an HTBW architectural term.** Who is engaging is answered by a purpose-specific Identity Assertion — Speaker Attribution, Interaction Initiator, Authenticated Session Identity, or Endpoint Context |
| Unresolved Room Context is representable | Where the interaction arrived through a surface not bound to a Room, Room Context is recorded as **`unresolved`**. **How it may be resolved is OD-73** |

---

## What Truth will never do

- Trigger actions
- Control devices
- Make resident-facing behavioral decisions
- Own preferences
- Own authority or permission
- Hide uncertainty
- Automatically convert weak evidence into a definitive fact

---

## What consumers may rely upon

| Consumer | May rely upon |
|---|---|
| Stewardship | Environmental, device, and time facts to evaluate obligation state |
| Continuity | Room mode, existing-session, availability, and room-transition facts |
| Operational Trust | Facts required to evaluate conditional policy |
| Concierge | The authoritative current state on which a decision is based |

Consumers receive the authoritative composite fact rather than raw sensor readings. Raw evidence
remains available for diagnostics, provenance, calibration, and explainability where authorized.

---

## What consumers must never assume

- That an identity assertion is a presence fact
- That absence of evidence is evidence of absence
- That a fact remains true past its validity
- That `unknown` may be treated as `false`
- That they may compute their own facts from raw evidence when Truth is unavailable
- That Truth chose which sensors are eligible — Room Configuration did
- That a Historical Fact may be used as a current fact
- That they may keep their own history of what Truth used to say
- **That a device-location Fact establishes the location of the Person bound to that device**
- **That a pet-location Fact is an Identity assertion, or that a tag-location Fact establishes any human identity**
- **That a declared `located-in` relationship is a current Location Fact**
- **That an Engagement Fact identifies who is engaging**
- **That Truth determined identity, or that Truth may re-run identity fusion**
- **That a Truth Fact confidence value is a DL-39 Identity band, or that either is an authorisation**

---

## The direction between Identity and Truth

**Identity produces Identity Assertions. Truth consumes them. The direction is one-way.**

| Guarantee | Statement |
|---|---|
| Truth consumes assertions | As **one input** among the Room's configured occupancy evidence |
| Truth produces the Fact | *Tom is present in the Den* is a **Truth** Contextual Person-Presence Fact |
| **Truth does not determine identity** | *Which human* is Identity's question and Identity's alone |
| **Truth does not re-run identity fusion** | Truth never re-weights, re-combines, or recomputes an assertion, and never reaches past it to the evidence behind it |
| Truth never receives biometric internals | Assertions only — for historical records exactly as for current ones |
| The one feedback path is bounded | Truth's **Room-subject occupancy** Fact may re-enter a **later** Identity fusion as **one evidence family**, at that family's ceiling. Truth's **Person-subject** presence Fact **never** does |

> **Occupancy precedes fusion. Person presence follows it. They are different Fact Subjects, and the
> sequence is not a cycle.** The full guarantee, with its four cycle-prevention properties, is in
> [../models/truth.md](../models/truth.md). See also
> [../architecture/dependency-view.md](../architecture/dependency-view.md) directional rule 2.

---

## Historical Facts

**Truth is the system of record for both present and historical Facts** (**P28**).

### What Truth guarantees historically

| Guarantee | Statement |
|---|---|
| Expiry is not deletion | Operational expiration removes a Fact from *what is true now*; it does not automatically delete *what was true then* |
| Lifecycle is reconstructable | Established, confirmed, confidence changed, superseded, withdrawn, operationally expired, became unknown, and became unresolved are each separately reconstructable |
| The record is sufficient to explain | Where policy permits: Subject, Statement, confidence at the time, Provenance, evidence references or classes, Coverage, Freshness, and lifecycle transitions |
| Versions are referenceable | A Decision Trace may reference the exact Fact version it used, and that reference remains accurate after the Fact changes (**P30**) |
| Limitations are stated | Where retention policy has removed or redacted a Historical Fact, Truth reports the limitation rather than implying the Fact never existed |

### What Truth will never do historically

- Present a Historical Fact as current
- Allow a Historical Fact to be actionable
- Allow a Historical Fact to silently become current again
- Retain a raw evidence payload in place of a governed Historical Fact

### Consumer obligation

**No consumer may maintain a competing or re-derived Fact history.** A consumer needing to know what
Truth previously held requests it from Truth or references the exact version it used. Keeping a
private copy creates a second fact engine, which this contract prohibits.

Retention for Historical Facts is settled by **DL-47**: they follow External History Retention with
their own Retention Classification. **Per-Fact-class differentiation is Operational Trust policy, not
architecture.**

---

## Composite facts

| Step | Owner |
|---|---|
| Declare eligible contributors | **Room Configuration** |
| Calculate the composite fact | **Truth** |
| Select sensors at runtime | **Prohibited** |

```
Room Configuration:  eligible contributors for Living Space temperature = Sensor A, Sensor C
Truth:               Living Space temperature = 72 degrees
                     truth_confidence_band: High
                     coverage:   2 of 2 eligible contributors reporting
                     provenance: Sensor A (71.6), Sensor C (72.4)
```

The aggregation algorithm is not decided by this contract — open decision **OD-17**.

---

## Conflicting evidence

**No consumer may resolve competing Truths by inventing a preferred fact.** Concierge in particular
must not do this.

Permitted Truth outcomes:

| Outcome | When |
|---|---|
| Single fact with reduced confidence | A governed resolution rule applies and is recorded |
| Unresolved fact | No resolution rule applies; candidate statements are reported |
| `unknown` | Nothing can be asserted |
| Withdrawn fact | Prior evidence is stale or contradicted |

Prohibited: silently choosing the most recent, highest-confidence, or most convenient evidence without
recording that a conflict existed.

---

## Uncertainty and unknown representation

`known` with confidence, `unresolved` with candidates, `unknown`, `stale`, `withdrawn`, and
`unavailable` are all first-class. Every consumer must be able to represent all of them.

---

## Failure and degradation behavior

| Condition | Behavior |
|---|---|
| A contributor is unavailable | Recompute from the remainder; reduce confidence; record reduced coverage |
| All contributors unavailable | Publish `unknown`; never retain the last value as current |
| Evidence stale | Mark stale, reduce confidence, or withdraw |
| Sources disagree | Preserve the disagreement |
| A room transition is missed | Do not invent a retroactive transition; treat the newly observed Room as current and record the gap |
| Truth itself is unavailable | Consumers fail closed; they do not substitute their own derivation |

---

## Privacy constraints

Presence and occupancy facts, and their history, are among the most sensitive household data.
Visibility is governed by [operational-trust-contract.md](operational-trust-contract.md).

Historical Facts are bounded by a retention **floor** (**P27**) and a retention **ceiling**
([../architecture/privacy.md](../architecture/privacy.md)). Where the two conflict, privacy governs
and the resulting limitation on explainability is recorded. A redacted Historical Fact remains a
record that the Fact existed.

**Truth consumes identity assertions only.** Truth never receives, stores, or exposes biometric
internals — vectors, embeddings, fingerprint payloads, artifact internals, or storage paths. This
holds for historical records exactly as it holds for current ones. See
[identity-contract.md](identity-contract.md).

---

## Explainability contributions

Every fact used in a decision appears in the Decision Trace with confidence, provenance, and freshness.
A fact that was `unknown`, and therefore blocked an action, must appear as well — a blocking unknown is
an explanation, not a gap.

---

## Open decisions

| ID | Question |
|---|---|
| OD-17 | Composite-fact aggregation algorithm and coverage thresholds |
| OD-18 | Fact validity and expiration defaults per fact class — **operational** validity only, not Historical Fact retention |
| OD-19 | Governed conflict-resolution rules for disagreeing evidence, **including the location conflict cases** |
| OD-73 | **Interaction-Surface Room Context Resolution.** Room Context for a phone, wearable, Companion App, browser session, or other non-room-bound surface |
| OD-74 | **Closed — DL-58.** Truth Fact Confidence is a uniform ordinal band (Low < Moderate < High < Very High), structurally separate from DL-39 Identity Confidence, independent of freshness/provenance/coverage. Consumed without redefinition by OD-17, OD-18, and OD-19 |
| OD-33 | **Closed — DL-43, DL-46, DL-47.** Historical Facts follow External History Retention with their own Retention Classification |
| OD-34 | **Closed — DL-42, DL-44, DL-46, DL-47.** The temporal-persistence model is complete; the representation mechanism is the residual of **OD-01** |

## Related documents

- [../models/truth.md](../models/truth.md)
- [../models/temporal-record.md](../models/temporal-record.md)
- [room-configuration-contract.md](room-configuration-contract.md)
- [identity-contract.md](identity-contract.md)
- [../architecture/adr-truth-as-fact-engine.md](../architecture/adr-truth-as-fact-engine.md)
- [../architecture/adr-historical-explainability-and-historical-truth.md](../architecture/adr-historical-explainability-and-historical-truth.md)
