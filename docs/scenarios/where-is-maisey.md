# Scenario — "Where is Maisey?"

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Demonstrates: a **Truth-only** location path, why a Pet must **not** be routed through Identity, the
> tag-versus-wearer conflict, an undischarged **DL-30** burden stated honestly, and consent and
> disclosure for pet-derived evidence.

---

## Why this scenario exists

This is the counterpart to [where-is-tom.md](where-is-tom.md). It exists to make one asymmetry
unmistakable:

> ***"Where is Tom?"* is a two-stage question. *"Where is Maisey?"* is a Truth-only question.**

**A Pet is a Foundation object and is not a Person.** There is no *which human* question to answer, so
there is **no Identity Assertion, no candidate set, and no DL-39 band**. Routing a pet tag through
Identity would be a category error: Identity's candidate set contains **known Persons only**, and the
four bands describe *"only the strength of support for a known-Person Identity Assertion."*

---

## 1. What the household experiences

Tom asks the Living Space assistant: *"Where is Maisey?"*

The home answers: *"Maisey's tag is showing in the Living Room."*

> **Read the wording carefully.** It is deliberately about the **tag** unless the deployment supplies
> evidence that genuinely grounds the Pet's own location. Section 3 explains why.

---

## 2. What each responsibility does

| # | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves **Room Context = Living Space** from the participating assistant's Room assignment |
| 2 | Foundation | Supplies the **Pet** object *Maisey* and the tag's evidence-source reference. **Foundation does not confirm current state** |
| 3 | Identity | **Not invoked for the Pet.** It may separately assert *Speaker Attribution* for **Tom**, the requestor — that is a different question about a different subject |
| 4 | Truth | Consumes the tag observation and establishes a **Location Fact**, Subject = **Pet(Maisey)** or **the tag**, at the granularity the evidence grounds |
| 5 | Operational Trust | Evaluates **disclosure** — is naming this Room to this audience appropriate? — and **consent** for the evidence source |
| 6 | Concierge | Composes the answer and the Decision Trace |

```
Truth establishes  : Maisey is in the Living Room
                     Subject     : Pet(Maisey)
                     Confidence  : Truth Fact confidence — OD-74
                     Provenance  : the tag observation, by reference
                     Freshness   : as observed
                     Validity    : per OD-18
                     Coverage    : where more than one eligible contributor reports
```

> **No Identity Assertion appears anywhere in this path.** That absence is the correctness property, not
> an omission.

---

## 3. The honest granularity problem

Under **P21** and the ordered burden of proof in **DL-30**, a Room-granularity claim requires evidence
whose Room granularity is **actually grounded**. The Platform Capability Review records this domain as
**not discharged**:

| Row | Capability | Status |
|---|---|---|
| **L1** | Any native primitive representing a Pet or its location | **No native primitive exists** |
| **L2** | Deriving a Pet's Room from a worn tag, collar, or beacon | **Not verified** |
| **L4 / L5** | Room-level device or BLE proximity | **Not verified** |

Two consequences follow, and they are architectural rather than stylistic:

- **A tag-location claim may be published for the tag.** A **Room-granularity Pet-location** claim may
  **not** be asserted from an unverified capability.
- **Where the deployment genuinely grounds Room-level detection, the Pet-subject Fact is publishable at
  that granularity.** Where it does not, the honest Fact is about the tag, or the Room claim is reduced
  or `unknown`.

> **This is the architecture working, not failing.** *"Do not close an open decision solely because a
> native Home Assistant capability exists"*, and equally: **do not assert a capability because the
> household would like one.**

---

## 4. The variants that matter

### The tag has been removed, or the pet has slipped its collar

**A tag is not the Pet.** The tag-location Fact stands for the **tag**; the Pet-location Fact is reduced,
**unresolved**, or `unknown`. The conflict is **preserved and explainable**, never resolved by preferring
the convenient reading, and the governed resolution rules are **OD-19**.

### A person is carrying the tag

Identical treatment. **The Subject of a Fact is what the evidence actually observes.** The tag-location
Fact is true; the Pet-location Fact is not supported.

> **Under no circumstances does a tag carried by a person become identity evidence.** A tag scan
> *"identifies a tagged object and an interaction with it"* and **never a person** — anyone may carry a
> tag. Consistent with **DL-06**: a detection is not an identification.

### All contributing sources become unavailable

Truth publishes `unknown`. **The last known location is never retained as current**, and the home says
*"I do not know where Maisey is."*

### Maisey is in a Merged Room

*Living Space* is a Merged Room of Kitchen, Dining, and Living. **A Room and a Merged Room behave
identically** (**DL-13**). Truth may additionally record the finer-grained **Constituent Room** Fact,
because that has value for diagnostics and precision — and **movement between constituent Rooms is not a
transfer and changes no Room Context**.

---

## 5. Consent and disclosure

> **A pet-worn tag reports, continuously, where the tag is — in rooms people occupy.**

| Concern | Governed treatment |
|---|---|
| **Consent** | Consent to track a **Pet** is **not** consent to derive household movement or occupancy patterns from it. Where pet-location evidence is used or retained beyond the Pet's own location, the applicable consent must be present. Evidence lacking valid consent is **excluded before weighting**, never down-weighted |
| **Disclosure** | *"Maisey is in the Primary Bedroom"* is evaluated as a **room-occupancy disclosure**, against **audience composition** (**DL-34**, **P32**) |
| **Sensitive Rooms** | A bedroom, bathroom, or guest room is **not** exempted because the question named a Pet |
| **No person inference** | Pet-location evidence never nominates a candidate Person, never enters the Identity Fusion Function, and **never creates person-scoped learning** |

Where audience composition is uncertain, **the delivery degrades — not the governance** (**OD-71**).

---

## 6. Lifecycle

| Concern | Rule |
|---|---|
| **Governing parent** | The **Pet** (**DL-45**) |
| **Retention** | Truth-owned governed history following External History Retention, with its own Retention Classification (**DL-47**) |
| **Parent removal** | Pet removal cleans up Pet-subject Facts and their history, subject to Preservation Holds, retention floors, and the versions required to keep a held Decision Trace explainable |
| **Tag removal** | The tag is **evidence, not the parent**. Removing it **withdraws current Facts and deletes no history** |
| **Consent withdrawal** | The source becomes **ineligible**; current Facts are withdrawn or reduced. **Earlier Facts remain historically true and remain explainable** |
| **No second store** | Native evidence is referenced. **HTBW builds no second Recorder and no parallel location history** (**DL-42**, **DL-46**) |

---

## 7. Decision Trace

```yaml
decision_id: 2026-08-16T19:11:52Z/living_space/knowledge.pet_location
requested: "Where is Maisey?"
room_context:
  room: Living Space
  resolved_from: voice_assistant_room_assignment
requester:
  assertion_purpose: speaker_attribution
  candidate_person: Tom
  assertion_state: known
  confidence_band: High
subject_identity_result: not_applicable        # a Pet is not a Person
capability_availability: available
facts_consulted:
  - statement: pet(maisey).located_in = Living Room
    subject: Pet(Maisey)
    granularity: room
    granularity_basis: deployment_grounded_room_detection
    provenance: [tag_observation_ref]
    freshness_s: 40
    fact_ref: <governed reference>
conflicts_detected: none
access_decision:
  required_identity_band: <policy>
  decision: permitted
disclosure_decision:
  audience_composition: [Tom, no unidentified participant supported]
  room_sensitivity: not_sensitive
  decision: disclosure_permitted_on_shared_surface
action_taken: respond("Maisey is in the Living Room")
alternative_considered: none_required
```

### Human form

> "Maisey is in the Living Room. Her tag was seen there about forty seconds ago. If the tag comes off,
> I will tell you I know where the tag is and not where she is."

### The conflicted form

```yaml
facts_consulted:
  - statement: tag(maisey_collar).located_in = Living Room
    subject: Asset(Maisey's collar tag)
    fact_ref: <governed reference>
  - statement: pet(maisey).located_in = unresolved
    subject: Pet(Maisey)
    candidates: [Living Room, unknown]
    conflict: tag_may_not_be_worn
    fact_ref: <governed reference>
action_taken: respond("Maisey's tag is in the Living Room, but I cannot confirm she is wearing it")
```

---

## 8. What this scenario proves

| Requirement | Demonstrated by |
|---|---|
| A Pet location path is **Truth-only** | Step 3 — Identity is **not invoked for the Pet** |
| A Pet is not a Person | No candidate set, no fusion, **no DL-39 band** |
| Non-person trackers are not identity evidence | The carried-tag variant |
| Granularity is not inflated | Section 3 — **L1, L2, L4, L5 are undischarged burdens** |
| Conflict is preserved | The removed-tag variant publishes **unresolved** |
| `unknown` is first-class | And the last known location is never retained as current |
| Consent and disclosure are evaluated | Section 5 |
| Lifecycle is declared | Section 6 — **DL-43, DL-45, DL-47** |
| No new model | One **Truth Fact**, Subject = Pet. **No `PetLocationAssertion` exists** |

---

## Related documents

- [../models/truth.md](../models/truth.md)
- [../models/person-and-identity.md](../models/person-and-identity.md)
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
- [../architecture/privacy.md](../architecture/privacy.md)
- [where-is-tom.md](where-is-tom.md)
- [where-is-my-phone.md](where-is-my-phone.md)
