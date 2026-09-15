# Scenario — "Where is Tom?"

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Demonstrates: the **two-stage** person-location path, evidence ceilings, conflict preservation,
> `unknown` as a valid outcome, disclosure evaluated against audience, and Decision Trace integration.

---

## Why this scenario exists

Person location is the case where **Identity and Truth must both act, in that order, without either
absorbing the other**. It is the canonical demonstration of **DL-06** and **P9**:

> *"We believe this is Tom" is not the same fact as "Tom is present in the Den."*

Compare with [where-is-maisey.md](where-is-maisey.md) and [where-is-my-phone.md](where-is-my-phone.md),
which are **Truth-only** and must not be routed through Identity.

---

## 1. What the household experiences

David asks the Den voice assistant: *"Where is Tom?"*

The home answers: *"Tom is in the Den."*

---

## 2. What each responsibility does

| # | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves **Room Context = Den** from the participating voice assistant's Room assignment. Records `resolved_from: voice_assistant_room_assignment` |
| 2 | Identity | Produces an assertion for **David** — purpose *Speaker Attribution* — for the requestor |
| 3 | Truth | Holds the **Room-subject** occupancy Fact: *the Den is occupied* |
| 4 | Identity | Produces a **separate** assertion for **Tom** — purpose **Room Presence**, Den — from current eligible evidence |
| 5 | Truth | Consumes that assertion **as one input** and establishes the **Person-subject** Fact: *Tom is present in the Den* |
| 6 | Operational Trust | Evaluates **access** — may David ask where Tom is? — and **disclosure** — may the answer be spoken here, to this audience? |
| 7 | Concierge | Composes the answer and the Decision Trace |

### Step 4 in detail — the fusion

Identity evaluates **Room Presence for Tom in the Den** from current eligible evidence:

| Evidence family | Observation | Ceiling for **Room Presence** |
|---|---|---|
| Wearable proximity | Tom's watch observed in the Den, fresh | Person-associated proximity; Room Presence **only where Room-level detection is genuinely grounded** |
| Phone-derived | Tom's phone observed in the Den, fresh | Person-associated proximity. **Never establishes that Tom is holding it** |
| Room occupancy | The Den is occupied | *That the Room is occupied; corroboration of context.* **Never "which Person"** |

Three rules bind the result:

- **F2 — one contribution per family.** Where the phone-derived observations arrive through several
  entities that originate from one device, they are **one** contribution, not several.
- **F1 — ceilings.** Room occupancy corroborates. **It cannot anchor the claim**, because it cannot
  establish *which* Person.
- **F4/F5 — anchor and corroboration.** The wearable anchors; each additional **independent** family
  raises the result by one bounded step, never by summation.

The output is a **purpose-specific Identity Assertion** carrying a **DL-39 band** — Low, Moderate,
High, or Very High — and its Fusion Policy version.

### Step 5 in detail — the Fact

```
Identity asserts   : candidate Tom, purpose Room Presence (Den), band High,
                     families [wearable_proximity, phone_derived, room_occupancy]
Room Configuration : the Den's occupancy evidence sources are X and Y
Truth establishes  : Tom is present in the Den
                     Subject     : Person(Tom)
                     Confidence  : Truth Fact confidence — OD-74
                     Provenance  : the Identity Assertion, by exact version, plus the Den occupancy Fact
                     Freshness   : as observed
                     Validity    : per DL-59
```

> **Truth does not re-run the fusion.** It consumes the assertion, and only the assertion. **Truth
> receives no biometric internals** and reaches past nothing.
>
> **The Identity band and the Truth Fact confidence are two different values.** The band describes
> identity support (**DL-39**); the Fact confidence describes belief in the world-statement, and its
> representation is **OD-74**. **Neither may be presented as the other.**

---

## 3. The variants that matter

### Tom's phone is in the Den but Tom is not

The phone-derived family contributes at its ceiling and **never establishes that Tom is holding it**.
Where the wearable is absent or contradicts, the result is a **lower band**, `ambiguous`, or `unknown`.
The home says *"I think Tom's phone is in the Den, but I am not confident Tom is."* **The device-location
Fact and the person-location Fact are not the same Fact.**

### Tom's watch is in the Kitchen and his phone is in the Den

**Contradiction is claim-specific and is retained, never averaged.** Under **F6** the reduction applies
against *Tom is present in the Den*. Truth's permitted outcomes apply:

| Outcome | When |
|---|---|
| Single Fact with reduced confidence | A governed resolution rule applies and is recorded (**OD-19**) |
| **Unresolved** Fact | No rule applies; **both candidate statements are reported** |
| `unknown` | Nothing can be asserted |

The home says *"I have evidence in two rooms and cannot resolve it."* **Silently picking the fresher or
higher-scoring observation is prohibited.**

### Nothing can be established

Identity returns `unknown`; Truth publishes `unknown`. The home says *"I do not know where Tom is."*

> **`unknown` is a valid, complete answer — not an error, not a degraded mode, and not something to
> retry away.** *"Absence of evidence is not evidence of absence"*, and the home must never report
> *"Tom is not home"* from a failure to observe him.

### Identity cannot be evaluated at all

A required input failed. The result is **`unavailable`**, not `unknown`, and Concierge **fails closed**.

### Continuous occupancy since Tom was last seen

**Irrelevant.** *Presence does not preserve identity.* A Room may remain continuously occupied while its
occupants change entirely, and **a prior assertion is never revived because presence persisted**
(**DL-39**). Each interaction is evaluated from **current** eligible evidence.

---

## 4. Disclosure — access and disclosure are two decisions

David asking is not authority to answer aloud.

| Evaluation | Question | Outcome |
|---|---|---|
| **Access** | May David ask where Tom is? | Per Tom's disclosure policy, evaluated by Operational Trust |
| **Disclosure** | May the answer be conveyed on this surface, to this audience? | Evaluated against **audience composition** (**DL-34**, **P32**) — *not* against David |

If an unidentified person is present in the Den, *"access allowed, disclosure not appropriate"* remains
representable, and the honest degradations are a content-free indication, a private surface, a
confirmation, or a refusal (**OD-71**). **The delivery degrades; the governance does not.**

---

## 5. Decision Trace

```yaml
decision_id: 2026-08-16T19:04:11Z/den/knowledge.person_location
requested: "Where is Tom?"
room_context:
  room: Den
  resolved_from: voice_assistant_room_assignment
requester:
  assertion_purpose: speaker_attribution
  candidate_person: David
  assertion_state: known
  confidence_band: High
  fusion_policy_version: 4
subject_identity_result:
  assertion_purpose: room_presence
  candidate_person: Tom
  assertion_state: known
  confidence_band: High
  supporting_evidence_families: [wearable_proximity, phone_derived, room_occupancy]
  correlation_treatment: "phone-derived observations grouped as one family"
  contradicting_evidence: none
  fusion_policy_version: 4
  identity_assertion_ref: <governed reference>
capability_availability: available
facts_consulted:
  - statement: den.occupied = true
    subject: Room(Den)
    provenance: [motion_a, presence_b]
    fact_ref: <governed reference>
  - statement: person(tom).present_in = Den
    subject: Person(Tom)
    provenance: [identity_assertion_ref, den_occupancy_fact_ref]
    fact_ref: <governed reference>
access_decision:
  required_identity_band: <policy>
  decision: permitted
presentation_decision:
  address_by_name_required_band: High
  current_band_qualified: true
  response: named
disclosure_decision:
  audience_composition: [David, no unidentified participant supported]
  residual_uncertainty: low
  decision: disclosure_permitted_on_shared_surface
action_taken: respond("Tom is in the Den")
alternative_considered: private_surface_delivery (not required here)
```

### Human form

> "Tom is in the Den. I believe that because his watch and his phone are both showing in the Den, the
> Den is occupied, and nothing places him anywhere else. I told you out loud because nobody I could not
> identify was there to hear it."

---

## 6. What this scenario proves

| Requirement | Demonstrated by |
|---|---|
| Person location is **two-stage** | Steps 4 and 5 — Identity asserts, **Truth** establishes |
| Identity and Truth are not circular | Room occupancy precedes fusion (**Room** subject); person presence follows it (**Person** subject) |
| Truth never re-runs fusion | Step 5 consumes the assertion **only** |
| Evidence ceilings hold | Occupancy corroborates and never anchors |
| Correlated evidence counts once | **F2** grouping in the trace |
| Conflict is preserved | The two-room variant publishes **unresolved**, never a preferred fact |
| `unknown` is first-class | And is distinguished from `unavailable` |
| Access ≠ presentation ≠ disclosure | Three separately recorded outcomes |
| No new model | One **Truth Fact**, Subject = Person. **No `PersonLocationAssertion` exists** |

---

## Related documents

- [../models/truth.md](../models/truth.md)
- [../models/person-and-identity.md](../models/person-and-identity.md)
- [../models/operational-trust.md](../models/operational-trust.md)
- [../models/decision-trace.md](../models/decision-trace.md)
- [where-is-maisey.md](where-is-maisey.md)
- [where-is-my-phone.md](where-is-my-phone.md)
