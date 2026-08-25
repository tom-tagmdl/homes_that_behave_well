# Scenario — "Home, I don't have my phone. Where is it?"

> **Document status: Canonical scenario.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Demonstrates: a **Truth-only** device-location path, the zone-versus-Room granularity boundary,
> **Home Assistant First** applied to a location question, and why a device-location answer is a
> **person-location disclosure**.

---

## Why this scenario exists

Three things collide in this one question, and each is easy to get wrong:

1. **It is a device-location question, not an engager-identification question.** Tom is asking about a
   *thing*. Establishing who asked is a separate matter, answered by a separate assertion purpose.
2. **The native evidence is documented as zone-granular, not Room-granular.** Answering *"in the Den"*
   from `device_tracker` alone would be a claim the home cannot support.
3. **Answering where Tom's phone is usually answers where Tom is** — to everyone who can hear.

---

## 1. What the household experiences

Tom asks the Den assistant: *"Home, I don't have my phone. Where is it?"*

The home answers: *"Your phone is in the Den."* — **or**, where the deployment supplies only zone-level
evidence: *"Your phone is home, but I cannot tell which room."*

Both answers are correct. **Which one is honest depends on the evidence, not on what would be more
useful.**

---

## 2. What each responsibility does

| # | Responsibility | Action |
|---|---|---|
| 1 | Room Configuration | Resolves **Room Context = Den** from the participating voice assistant |
| 2 | Identity | Asserts **Speaker Attribution** for **Tom**, the requestor. **No assertion is made about the phone** |
| 3 | Foundation | Supplies the **Device** reference and the Person-to-device relationship, **by stable identifier — never copied** (**DL-31**) |
| 4 | Truth | Consumes native `device_tracker` and any Room-grounded proximity evidence, and establishes a **Location Fact**, Subject = **Device** |
| 5 | Operational Trust | Evaluates **access** and, separately, **disclosure against audience composition** |
| 6 | Concierge | Composes the answer and the Decision Trace |

```
Truth establishes  : Tom's phone is in the Den
                     Subject     : Device(Tom's phone)
                     Confidence  : Truth Fact confidence — OD-74
                     Provenance  : native device_tracker state, and Room-grounded proximity where present
                     Freshness   : as observed
                     Validity    : per OD-18
```

> **Identity performs no fusion about the phone.** A Device is not a Person, and there is no *which
> human* question. This is a **Truth-only** path, exactly as in
> [where-is-maisey.md](where-is-maisey.md).

---

## 3. Home Assistant First — what may honestly be claimed

This is the clearest worked case of the **DL-30** burden of proof applied to a location answer.

| Evidence | Documentation status | What may be claimed |
|---|---|---|
| Native `device_tracker` | **Verified.** *"the granularity is the zone, never a Room or Area"* | *Home*, *Not home*, or a named **zone** |
| Connection-type tracker | **Verified.** The zone is a documented **assumption** while connected | The same, marked as an assumption |
| Room-level BLE or proximity | **Not verified** (Platform Capability Review **L4**, **L5**) | **Nothing at Room granularity by default** |
| Companion App room attribution | **Not verified** (**L6**) | **Nothing** |
| Deployment-specific Room-grounded evidence | Deployment-dependent | A **Room-level** Fact, where that specific source genuinely grounds it |

> **`Home` is not `Den`.** Where only zone-level evidence exists, the honest Location Fact is
> zone-granular, and the honest answer is *"your phone is home, but I cannot tell which room."*
> **Publishing a Room-level Fact from zone-level evidence is a defect, not a convenience.**

### What HTBW adds, and what it must not add

| HTBW adds | HTBW must not add |
|---|---|
| Subject typing, confidence, provenance, freshness, validity, coverage | The position itself |
| Preserved conflict and first-class `unknown` | A second device tracker |
| Fact lifecycle and governed history | A parallel location history or a second Recorder |
| An explainable answer | A longer-retained copy of native rows — *"wanting longer retention is not a gap"* |

Native state is **consumed as evidence**; the Fact is the governed conclusion. *"A state is evidence. A
Fact is governed, provenance-bearing, and confidence-bearing."*

---

## 4. The variants that matter

### The phone is in the Den, but Tom is not

**Both statements can be true at once**, and the architecture must keep them apart:

```
Device Location Fact  : Tom's phone is in the Den        ✅ supported
Person Location Fact  : Tom is present in the Den        ❌ NOT established by this
```

**A device-location Fact never establishes that the bound Person is with the device.** The observation
contributes to a *Room Presence* assertion for Tom only through **Identity**, at that family's ceiling —
and it is exactly the *device left behind* case the conflict table governs.

### The phone is out of battery, off, or unreported

Truth publishes `unknown`. **The last known location is never retained as current**, and the home says
*"I do not know where your phone is — I last saw it in the Den about an hour ago"*, with the historical
statement clearly marked as historical. **A Historical Fact is never presented as current and never
silently becomes current again.**

### The tracker says `Home` and a Room-grounded beacon says `Office`

These are **different granularities, not two answers to one question**. Both are published at the
granularity each grounds. Where they genuinely contradict, Truth preserves the disagreement — reduced
confidence, `unresolved`, or `unknown` — under **OD-19**.

### Tom asks about **David's** phone

The Subject is a Device bound to **David**. The disclosure evaluation is governed by **David's** policy,
not Tom's, and *"access allowed, disclosure not appropriate"* remains representable.

### The request arrives from Tom's phone itself

Then the interaction surface is **not bound to a Room**, Room Context is **`unresolved`**, and the
degraded path applies. See **OD-73** and
[../models/decision-trace.md](../models/decision-trace.md).

---

## 5. Disclosure — the part that is easy to skip

> **Answering where Tom's phone is usually answers where Tom is.**

```
Asked   : "Where is my phone?"
Answered: "Your phone is in the Den."
Heard as: "Tom is in the Den."
```

| Requirement | Statement |
|---|---|
| **Audience evaluation is mandatory** | A device-location answer is evaluated as a **person-location disclosure** whenever the device is bound to a Person |
| Correct classification is not an exemption | Calling this *asset or device location rather than engager identification* is right about **ownership**. **It is not a licence to skip disclosure evaluation** |
| The requestor is not the audience | Tom asking does not authorise stating Tom's whereabouts in front of an unidentified listener |
| Degradation is available | Content-free indication, a private surface, confirmation, or refusal (**OD-71**) — **the delivery degrades, the governance does not** |

---

## 6. Lifecycle

| Concern | Rule |
|---|---|
| **Governing parent** | The **Person, Asset, or Room** the Device is governed through (**DL-45**) |
| **Retention** | Truth-owned governed history following External History Retention, with its own Retention Classification (**DL-47**) |
| **Native Device removed outside HTBW** | Produces a **broken reference**, which is **reported**; current Facts are withdrawn; **history is never rewritten**. **HTBW never deletes a referenced native Device** (**DL-31**) |
| **Person deleted** | Dependent Facts and history are cleaned up, subject to Preservation Holds, retention floors, and versions required to keep a held trace explainable |
| **Consent withdrawn for the source** | The source becomes **ineligible**; current Facts are withdrawn or reduced. **Earlier Facts remain historically true and explainable** |

---

## 7. Decision Trace

```yaml
decision_id: 2026-08-16T19:20:33Z/den/knowledge.device_location
requested: "Where is my phone?"
room_context:
  room: Den
  resolved_from: voice_assistant_room_assignment
requester:
  assertion_purpose: speaker_attribution
  candidate_person: Tom
  assertion_state: known
  confidence_band: High
  fusion_policy_version: 4
subject_identity_result: not_applicable        # a Device is not a Person
capability_availability: available
native_references:
  - device_tracker_state: <native reference>
facts_consulted:
  - statement: device(tom_phone).located_in = Den
    subject: Device(Tom's phone)
    granularity: room
    granularity_basis: deployment_grounded_room_detection
    provenance: [device_tracker_ref, den_proximity_ref]
    freshness_s: 12
    fact_ref: <governed reference>
conflicts_detected: none
access_decision:
  required_identity_band: <policy>
  decision: permitted
disclosure_decision:
  evaluated_as: person_location_disclosure
  reason: device_bound_to_person(Tom)
  audience_composition: [Tom, no unidentified participant supported]
  decision: disclosure_permitted_on_shared_surface
presentation_decision:
  address_by_name_required_band: High
  current_band_qualified: true
  response: named
action_taken: respond("Tom, your phone is in the Den")
alternative_considered: private_surface_delivery (available, not required here)
```

### The zone-only form

```yaml
facts_consulted:
  - statement: device(tom_phone).located_in = zone(Home)
    subject: Device(Tom's phone)
    granularity: zone
    granularity_basis: native_device_tracker_zone_only
    provenance: [device_tracker_ref]
    fact_ref: <governed reference>
action_taken: respond("Your phone is home, but I cannot tell which room")
alternative_considered: room_level_claim (not supported by available evidence)
```

### Human form

> "Your phone is in the Den — I can see it there now. I said it out loud because there was nobody here I
> could not identify. If all I had was that it was somewhere in the house, I would have told you that
> instead, rather than guess a room."

---

## 8. What this scenario proves

| Requirement | Demonstrated by |
|---|---|
| A Device location path is **Truth-only** | Step 2 — Identity asserts about **Tom**, never about the phone |
| A device is not its owner | Section 4 — both Facts stated, only one supported |
| Granularity is not inflated | Section 3 and the zone-only trace form |
| **Home Assistant First** holds | Native state consumed as evidence; **no second device tracker, no second Recorder** |
| Device location is a person disclosure | Section 5, and `evaluated_as: person_location_disclosure` in the trace |
| Historical is not current | The battery-dead variant |
| Conflict is preserved | The zone-versus-Room variant |
| Lifecycle is declared | Section 6 — **DL-45**, **DL-47**, broken-reference behaviour |
| No new model | One **Truth Fact**, Subject = Device. **No `DeviceLocationAssertion` exists** |

---

## Related documents

- [../models/truth.md](../models/truth.md)
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
- [../models/operational-trust.md](../models/operational-trust.md)
- [../architecture/privacy.md](../architecture/privacy.md)
- [where-is-tom.md](where-is-tom.md)
- [where-is-maisey.md](where-is-maisey.md)
