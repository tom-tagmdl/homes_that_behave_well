# Communication

> **Document status: Active — Canonical model.**
> Owning responsibility: **Foundation** (definitional).
> Governed by **P31** and **P32**. Established by
> [../architecture/adr-resident-communication-and-delivery-separation.md](../architecture/adr-resident-communication-and-delivery-separation.md).
> Terminology: [glossary.md](glossary.md).

---

## Purpose

This model defines what a **Communication** is, how it differs from the act of delivering it, and how
its history is recorded.

Foundation defines this model. **Foundation does not own any Communication.** Any responsibility may
originate one; **Concierge** decides and records delivery.

**This model creates no new responsibility.** There is no Communication responsibility, no Messaging
responsibility, no Inbox responsibility, no central delivery owner, no central inbox owner, and no
second escalation ladder.

**This model creates no new temporal record kind.** Communication history is recorded using the
Change Records, Governed References, and Version Identity already defined in
[temporal-record.md](temporal-record.md).

---

## Question answered

> *What does the home need to convey, to whom, about what — and what happened when it tried?*

---

## The central separation

> **A Communication is a household interaction. A Delivery is an act of conveying it.**

| Concept | Meaning |
|---|---|
| **Communication** | The governed object. What must be conveyed, to whom, about what |
| **Delivery** | The act of conveying a Communication through a surface |
| **Delivery Attempt** | One bounded act of delivery to one surface, with its own outcome |
| **Delivery Surface** | A governed abstraction of a place through which delivery may occur |
| **Announcement** | A Delivery made **audibly to a shared surface**. An outcome, never an object |

A Communication may have zero, one, or many Delivery Attempts. It is not defined by any of them.

**A Communication is never a notification, a push message, an announcement, an indicator, an email,
or a spoken phrase.** Those are delivery outcomes. See **P31**.

---

## The Communication object

A Communication is a **small governed record with a mutable Current Projection and a history of
Change Records**. It is never a growing document.

### Required

| Field | Purpose |
|---|---|
| **Communication ID** | Without identity it cannot be referenced, superseded, held, or tombstoned |
| **Version Identity** | Required of every governed record by **P29** and **P30** |
| **Effective Time** | When the Communication became relevant |
| **Recorded Time** | When the home recorded it |
| **Provenance** | Which responsibility, through which evidence, at what confidence |
| **Originator reference** | A **Governed Reference** to the responsibility and to the exact version of the record that caused it |
| **Subject reference** | A **Governed Reference** to what it is about — an Asset, Room, Person, Obligation, or Fact version |
| **Intended Audience** | An audience **specification** — never a device or surface list |
| **Category** | What it is about. Proposed by the originator |
| **Urgency** | What it is entitled to interrupt. Determined by **Operational Trust** |
| **Significance reference** | A reference to Stewardship's significance, never a copied value |
| **Originating Context Reference** | A **Governed Reference** to the Fact versions that were true at origination |
| **Visibility Classification reference** | A reference to the Operational Trust classification, re-evaluated at each attempt |
| **Retention Classification** | Carries the retention **floor and ceiling** onto the record |
| **Lifecycle State** | The Current Projection — what state it is in now |
| **Supersedes / Superseded-by** | Governed References. Supersession is never inferred from ordering |
| **Expiry specification reference** | A reference to the governing policy, never a copied duration |
| **Minimal rendering projection** | The immutable human-readable form. Permitted by **P30**; must not become a wholesale copy |
| **Explanation references** | Governed References to the Decision Traces that created or suppressed it |

### Prohibited

> **These three fields must never exist on a Communication.**

| Prohibited | Reason |
|---|---|
| A stored **context** value | Context is resolved by Truth and Room Context **at delivery time**. A stored context is a frozen snapshot that will silently become wrong. Use the Originating Context Reference |
| A stored resolved **visibility** value | Visibility is Operational Trust's and is re-evaluated at **each** Delivery Attempt. A stored value would survive a policy revocation — the **P30** failure mode |
| An embedded **delivery history** array | The embedded-audit-array defect recorded in [../architecture/adr-temporal-record-model.md](../architecture/adr-temporal-record-model.md). Delivery history is Change Records referencing the Communication by Version Identity |

---

## Category and Urgency

**These are orthogonal axes and must never be merged.**

### Category — what it is about

Proposed by the originator. Representative categories:

| Category | Representative subject |
|---|---|
| Informational | A package was delivered; a weather change |
| Obligation | Medication due; collection day; filter replacement |
| Stewardship | Humidity is outside the safe range for a sensitive asset; service is due |
| Condition | A door is unlocked; the garage is open |
| Safety | Water, smoke, or carbon monoxide detected |
| Interaction | The home needs an answer before it can proceed |
| Governance | An action was refused; consent is required; a limitation is being reported |

The exact enumeration is open decision **OD-53**.

### Urgency — what it may interrupt

**Urgency is an entitlement granted by Operational Trust, never a property the originator asserts.**
The originator may propose an urgency; Operational Trust determines it.

> **A category must never function as a bypass.** If a category could grant interruption rights by
> virtue of its name, an originator could authorise itself, and **P32** would be decorative.

Urgency classification is open decision **OD-46**. Its relationship to action-risk classification is
**OD-51**.

### Why the axes are separate

*Package delivered* and *weather update* are about different things and interrupt identically.
*Alert* and *critical alert* are about the same kind of thing and differ only in interruption
entitlement. Merging the axes makes the taxonomy the permission model.

### Advisory

**Advisory is a Stewardship judgement**, not a Communication category. An Advisory suggests what
could be improved; an Alert indicates that something is wrong. See
[../patterns/advisory-patterns.md](../patterns/advisory-patterns.md). The Communication conveying an
advisory carries the **stewardship** category.

---

## Intended Audience

An audience is expressed as a **specification**, resolved to surfaces only at delivery.

| Audience kind | Meaning |
|---|---|
| Specific Person | One identified person |
| Role | Caretaker, adult, child — resolved by Operational Trust |
| Authority Class | Anyone holding a stated authority |
| Anyone Present With Authority | The first suitably authorised person contextually present |
| Household | All residents |

> **"Household" never means "everyone in earshot."** Audience is a specification of who the
> Communication is *for*. Who can *perceive* a surface is a separate question, answered by Truth and
> governed by **P32**.

**Guests are never an audience by default**, and guest presence constrains delivery to every
audience. See [../architecture/privacy.md](../architecture/privacy.md).

The audience specification model is open decision **OD-52**.

---

## Audience composition

**Intended Audience says who a Communication is *for*. Audience composition says who may be able to
*perceive* it.** They are different questions, and conflating them is precisely what **P32** forbids.

Audience composition answers: *who may be able to perceive this content through the proposed delivery
surface?* It is a governed **input to disclosure**, evaluated by Operational Trust. It applies to a
solicited answer just as it applies to an unprompted announcement.

| Term | The question it answers |
|---|---|
| **Requestor** | Whose request is this? An Interaction Initiator assertion, for a Person or an Unknown Person |
| **Speaker** | Who uttered it? A Speaker Attribution assertion, for a Person or an Unknown Person |
| **Present Person** | Who is likely physically here? A Room Presence assertion |
| **Potential Listener** | Who may perceive the proposed delivery? |
| **Authorized Recipient** | Whom does Operational Trust permit to receive this content? |
| **Delivery Target** | Which surface, device, application, Room, or endpoint was selected? |

**These must never be collapsed into a single audience field.** A requestor may be authorised while
another potential listener is not. A speaker may not be the authenticated application user. A present
Person may not be a listener when delivery is private. A Delivery Target may be a phone rather than
the Room the request arrived in.

### Composition states

| State | Meaning |
|---|---|
| Known Person present | A known Person, with a purpose-specific confidence |
| Known non-resident Person present | A specifically configured non-resident |
| Unknown Person likely present | Someone is supported; nobody is identified |
| Multiple known Persons | More than one identified potential listener |
| Unresolved plurality | One or more unidentified people; the count is not established |
| No additional listener supported | No evidence of anyone else — **not proof of solitude** |
| Audience unknown | Composition could not be established |
| Audience detection unavailable | The evidence needed to evaluate composition could not be obtained |

> **Audience composition must retain its uncertainty.** It is not required — and not permitted — to
> identify every listener in order to be useful.

Four inferences are prohibited:

- **Room occupancy count is not audience identity.** Occupancy says how many, never who.
- **A detected phone is not proof that its owner can hear the response.** A device is not an ear.
- **Absence of detected evidence is not proof that nobody else is present.** *No additional listener
  supported* and *nobody else is here* are different statements, and the second is not available.
- **Audience composition identifies nobody.** It consumes accepted identity assertions and presence
  Facts. **It is not a second identity-fusion process**, and it produces no assertion of its own.

Composition carries forward, unaltered, the assertion purpose, the known or unknown state, the
confidence band, freshness, Room context, the supporting evidence references, the residual
uncertainty, and whether detection was available at all.

### Private delivery

Where content should not be conveyed aloud, Concierge may offer an authorised alternative: a resident
application surface on an associated device, an Inbox projection restricted to the authorised
audience, a private dashboard, a content-free indication, or a confirmation asking whether audible
delivery is still wanted.

> **A surface is not private because it is a phone.**

Operational Trust evaluates target association, authenticated user, governed device binding, delivery
capability, audience restriction, content classification, and applicable policy before any surface is
treated as private. Surface capability and perceptibility are **OD-43**; the audience specification
model is **OD-52**; the policy applied when composition is uncertain is **OD-71**.

Communication remains the object. Delivery remains separate. **Concierge orchestrates the outcome and
owns none of the authority.** See [operational-trust.md](operational-trust.md).

### A confirmation challenge is a Communication

When the home asks *"I think I am speaking with Tom. Can you confirm?"*, it is not merely running a
process — it is **conveying to everyone within earshot that it believes Tom is present**.

> **The question is a disclosure. It is audience-evaluated before it is asked.**

A confirmation challenge therefore carries an Intended Audience, an audience composition, a Delivery
Surface, and a disclosure decision like any other Communication (**DL-34**, **P32**). Naming a
candidate aloud, choosing a neutral challenge that names nobody, and redirecting the challenge to an
authorised private surface are **three different disclosure outcomes**, and the choice is Operational
Trust's.

**No wording is prescribed here.** The requirement is that the challenge is governed, not that it is
phrased in a particular way. Confirmation requirements, strength, scope, and outcomes belong to
[operational-trust.md](operational-trust.md); the policy applied when audience composition is
uncertain is **OD-71**.

### Named and neutral presentation

Speaking a Person's name is a disclosure, so **whether a response is named or neutral is an
Operational Trust outcome that Communication carries and Concierge renders**. The **Address by Name**
setting and its required current Identity band are Operational Trust's; Communication never sets
them, and never names a candidate on its own initiative.

| Condition | Presentation |
|---|---|
| The **current** assertion meets the required band **and** the audience permits the name | Named |
| The current assertion is below the required band | **Neutral** |
| Address by Name is disabled | **Neutral**, regardless of band |
| The assertion is `ambiguous`, `unknown`, `unavailable`, or `not required` | **Neutral**. No candidate is named |
| The name would disclose identity to an audience not authorised to receive it | **Neutral**, or a private surface is offered (**DL-34**) |

> **A neutral response is a correct response, not a degraded one.** It is never an apology, and it is
> never a refusal of the action.

The naming decision is made from the assertion current **at the time the response is generated**. A
name used in an earlier response confers no eligibility on the next one, and continuing Room occupancy
supplies none. See [person-and-identity.md](person-and-identity.md).

---

## Delivery

### Delivery Surface

A Delivery Surface is a **capability abstraction**, not a device and not a product.

A surface declares what it can convey, **to whom it is perceptible**, and whether it can attest that
something was presented. Perceptibility is the property **P32** depends on; format is not.

> **This model contains no surface catalogue.** Enumerating surfaces would re-couple the domain to
> transport, which is what **P31** forbids. Surface capability modelling is open decision **OD-43**.

### Indication and content are separate deliveries

A **content-free indication** asserts only that something is outstanding. It discloses nothing, and
is therefore permissible where content is not.

| Delivery | Discloses | Governed by |
|---|---|---|
| Indication | That something is outstanding | Permitted broadly; still subject to interruption authority |
| Content | What it says | Full **P32** evaluation against surface perceptibility |
| Retrieval | What it says, on request | Resident-initiated; returns to the ordinary exposure chain with identity asserted at retrieval |

> **Modelling indication and content as one act removes the safe degradation path and forces a
> choice between silence and disclosure.**

On a shared surface the indication is **aggregate and content-free**. A shared surface must never
enumerate whose Communications are waiting. Separation policy is open decision **OD-57**.

### Re-presentation

**A Communication has no location.** It cannot move, follow, or remain location-bound.
Location-boundness is a property of a Delivery Attempt.

Where a person moves and a Communication remains outstanding, Concierge may make a **new Delivery
Attempt** on a newly appropriate surface, re-evaluating **P32** against the **new** audience. Each
attempt is separately recorded.

**The Communication is never duplicated.** One object, many attempts.

Whether a resident wants this is a **Continuity** preference within the existing Follow-Me family.
Whether it is permitted is **Operational Trust**. Whether and where to attempt it is **Concierge**.
See **OD-48**.

### Retry is not escalation

| Concept | Definition | Owner |
|---|---|---|
| **Delivery retry** | Repeating delivery **to the same audience**, on the same or another surface | **Concierge** |
| **Escalation** | Changing **the audience** to a more authoritative or accountable person | **Stewardship** ladder (**OD-22**), **Operational Trust** authority |

> **There is one escalation architecture, and it already exists.** Retry is a delivery concern and is
> never called escalation. Retry policy is open decision **OD-54**.

---

## Delivery outcome model

**Two levels. They must never be flattened.**

### Communication lifecycle states

| State | Meaning |
|---|---|
| **Created** | The Communication exists and is outstanding |
| **Suppressed** | Withheld by decision. **Produces a Decision Trace** — suppression is an Intentional Non-Action |
| **Acknowledged** | An **identified person** acknowledged it. Anonymous dismissal is not acknowledgement |
| **Expired** | Its relevance window closed without a terminal outcome |
| **Superseded** | Replaced by a later Communication, by explicit Governed Reference |
| **Resolved by origin** | The originator withdrew it because the underlying condition cleared. The resident may never have seen it |
| **Undeliverable** | No permitted surface could convey it. **Must be reported, never silent** |

### Delivery Attempt outcomes

| Outcome | Meaning |
|---|---|
| **Attempted** | An attempt was made to a specific surface |
| **Delivered** | The surface accepted it |
| **Presented** | The surface rendered it perceptibly |
| **Failed** | The attempt did not succeed |

### The honesty rule for Presented

> **Most surfaces cannot attest presentation.** Where a surface cannot attest it, `Presented` is
> recorded as **unknown**. It is **never** inferred from `Delivered`.

A home that reports something as seen when it only knows it was sent has converted uncertainty into
false certainty. See **P15** and
[../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md).
Attestation per surface class is open decision **OD-55**.

### Why two levels

A Communication has exactly one current lifecycle state and may have many Delivery Attempts.
Flattening the levels makes multi-surface delivery unrepresentable — the most likely modelling error
in this area.

### Rejected state

**Completed** is not a state. It conflates *the Communication was dealt with* with *the underlying
condition was resolved*. The latter belongs to the originator and outlives every Communication about
it. `Resolved by origin` covers the legitimate case.

---

## Communication history

Communication history uses the shared temporal model **unchanged**.

| Historical record | Record kind | Owner |
|---|---|---|
| Communication created | **Change Record** with no prior version | Concierge |
| Communication suppressed | **Change Record** and a **Decision Trace** | Concierge |
| Delivery attempted, delivered, presented | **Change Record** per attempt | Concierge |
| Delivery failed | **Change Record**, plus a diagnosable failure report | Concierge |
| Communication acknowledged | **Domain Event** *and* **Change Record** | Concierge |
| Communication expired | **Change Record** | Concierge |
| Communication superseded | **Change Record** carrying a Governed Reference | Concierge |
| Communication redacted, purged, or truncated | **Tombstone** | Concierge |

### Acknowledgement is both kinds of record

A resident acknowledging a Communication is **something that happened in the household** — a Domain
Event — *and* **something that happened to a governed record** — a Change Record. Both are recorded.

**Do not collapse them.** See the distinction in [temporal-record.md](temporal-record.md).

### Ownership

**Concierge owns communication delivery history**, because delivery is a decision and Concierge
already owns decision history. **No new row is added to the History-ownership matrix** in
[../architecture/framework.md](../architecture/framework.md).

The **originator** continues to own the history of the underlying matter. An Obligation's history is
Stewardship's; it is not delivery history and is not duplicated here.

> **No consumer may maintain a competing or re-derived communication history.**

### Retention

Settled by **DL-47** as a governed record class; the separate classification of content and metadata
remains **OD-49**. A floor is never stated without its ceiling.

**Content and metadata are classified separately.** The fact that the home tried to convey something
and failed may require a longer floor than the content of what it tried to convey.

---

## Household Inbox

> **The Household Inbox is a projection over outstanding Communications. It is not a persisted
> object.**

| Property | Statement |
|---|---|
| Assembled | On demand, from governed records |
| Filtered | By the viewer's authority, **evaluated at read time** |
| Owned | By no responsibility. Concierge produces it; Operational Trust filters it |
| Never | A store, a source of truth, or a shared household-wide list |

**Why it must not be persisted.** If authority to see a Communication is withdrawn, a stored inbox
still contains it until something remembers to rewrite it. A projection is correct by construction.
This is the **P30** failure mode applied to visibility.

**There is no single household inbox.** There are as many projections as there are viewers.

This is the same treatment given to **Historical Reconstruction** and **Evidence Package** in
[temporal-record.md](temporal-record.md). Projection scope and refresh semantics are open decision
**OD-47**.

---

## Explaining communication

The home must be able to answer *"why didn't you tell me?"*:

| Question | Records |
|---|---|
| Did you know? | Truth Fact history (**P28**) |
| Did you decide to tell me? | The creation Change Record |
| Did you decide **not** to? | The suppression Change Record **and its Decision Trace** |
| Did you try? | Delivery Attempt Change Records |
| Did it arrive? | Delivered and Presented, or an honest `unknown` |
| Did I acknowledge it? | The acknowledgement Domain Event, with identity attribution |
| Is it still outstanding? | The Current Projection |
| Do you still hold the record? | The record, or its **Tombstone** |

**Communication** is a Historical Explainability retrieval scope. See
[../architecture/explainability.md](../architecture/explainability.md).

---

## Multi-person communication

| Step | Responsibility | Output |
|---|---|---|
| 1 | **Originator** | This must be conveyed, to this audience, about this subject |
| 2 | **Operational Trust** | Who may receive it; urgency entitlement; interruption entitlement; visibility classification |
| 3 | **Identity** | Candidate person assertions with confidence — never presence |
| 4 | **Truth** | Contextual person-presence and occupancy — **who else can perceive the surface** |
| 5 | **Continuity** | Re-presentation preference and personal surface defaults |
| 6 | **Concierge** | Resolve audience to surfaces, apply **P32**, decide, deliver or suppress, record, explain |

The ordering is already constitutional: *context before intent, identity before authorization, truth
before decision, trace always.* See
[../architecture/runtime-sequence.md](../architecture/runtime-sequence.md).

---

## Privacy considerations

- **Outbound communication inverts the initiative.** The audience is whoever can perceive the
  surface, not whoever asked. This is why **P32** exists.
- Guest presence constrains delivery to every audience.
- Health, medication, and pet-care Communications must be **deliverable without disclosing content
  to an unintended audience**. Content-free indication is the mechanism.
- Where identity or occupancy is uncertain, **the delivery degrades — the governance does not.**
- Visibility is never stored resolved; it is re-evaluated per attempt.
- Content and metadata are classified separately for retention.
- A suppressed Communication is recorded and explainable. **Silence is never unrecorded.**
- Redaction, purge, or truncation of a Communication leaves a **Tombstone**.

---

## Life-safety non-claim

**HTBW is not a life-safety system.**

A safety-category Communication does not constitute smoke detection, carbon-monoxide detection,
water-leak protection, medical alerting, security monitoring, or emergency notification, and must
never be represented as a substitute for certified alarms, monitored services, or emergency services.

Delivery is **best-effort** and may fail at the platform boundary. Whether HTBW may originate
safety-category Communications at all is open decision **OD-56**.

---

## Explicit non-responsibilities

This model does **not**:

- Create a Communication, Messaging, Inbox, Delivery, or Escalation responsibility
- Create a central delivery owner, a central inbox owner, or a preservation authority
- Create a second escalation ladder
- Create a new temporal record kind or a parallel history mechanism
- Own any Communication, audience, policy, obligation, or Fact
- Select a delivery technology, surface catalogue, indicator scheme, urgency scale, retry interval,
  retention duration, or identifier implementation
- Revive the superseded "message authority" boundaries of the Historical provenance and household
  memory ADRs

---

## Failure behavior

| Condition | Required behavior |
|---|---|
| No permitted surface exists for the audience | Record **Undeliverable** and report it. Never fail silently |
| A Delivery Attempt fails at the platform boundary | Record **Failed** with a diagnosable reason. Never claim success |
| A surface cannot attest presentation | Record `Presented` as **unknown**. Never infer it from Delivered |
| An acknowledgement event never arrives | Remain **unknown**. Never decay into *not acknowledged* |
| Identity is `unknown` or `ambiguous` | Degrade to content-free indication and guest-safe treatment. Never disclose content to resolve ambiguity |
| Occupancy is `unknown` | Do not announce to a shared surface. Choose the benign delivery or defer |
| Operational Trust is unavailable | Fail closed. Do not deliver |
| A Communication Change Record cannot be written | The failure is itself reportable; a silently unrecorded delivery outcome is a defect |
| A Communication is suppressed | Record the suppression **and** its Decision Trace |
| A Governed Reference on a Communication cannot be resolved | Report the reference as unavailable, with the reason where known |
| Communication history was purged | Report the gap and its reason classification. Never interpolate |

> **Silent non-delivery is prohibited.**

---

## Representative scenarios

- Stewardship determines an obligation is unmet; Operational Trust permits interruption but not
  audible announcement because guests are present; Concierge delivers to a personal surface,
  suppresses the shared announcement, and records both.
- A resident hears *"you have one message waiting"*, asks *"what is my message?"*, and identity is
  asserted at retrieval rather than at indication.
- A Communication remains outstanding as a resident moves rooms; a new Delivery Attempt is made and
  separately recorded; the Communication is not duplicated.
- A resident asks *"why didn't you tell me the garage was open?"* and the home reconstructs
  knowledge, decision, suppression, attempts, and outcomes.

See [../scenarios/why-did-this-happen.md](../scenarios/why-did-this-happen.md).

---

## Open decisions

| ID | Question |
|---|---|
| OD-22 | Escalation ladder semantics and defaults — the single ladder, serving communications |
| OD-33 | **Closed — DL-43, DL-46, DL-47.** Communication records follow the governed-record retention model; the content-versus-metadata classification remains **OD-49** |
| OD-34 | **Closed — DL-42, DL-44, DL-46, DL-47.** The temporal-persistence model is complete; Communication object persistence remains **OD-42**, subordinate to **OD-01** |
| OD-38 | Version identity, correlation, and causation identifier strategy |
| OD-42 | Communication object persistence and Home Assistant representation |
| OD-43 | Delivery Surface capability model, including perceptibility and attestation |
| OD-44 | Delivery outcome semantics across the two levels |
| OD-45 | Acknowledgement semantics and acknowledger identification |
| OD-46 | Urgency classification as an Operational Trust entitlement |
| OD-47 | Household Inbox projection scope and refresh semantics |
| OD-48 | Re-presentation preference and its relation to the Follow-Me preference family |
| OD-49 | Communication retention floor and ceiling |
| OD-50 | Escalation ladder semantics for communications, resolved into OD-22 |
| OD-51 | Interruption action-risk class enumeration and defaults |
| OD-52 | Audience specification model |
| OD-53 | Communication category enumeration |
| OD-54 | Delivery retry policy |
| OD-55 | Presentation attestation per surface class |
| OD-56 | Safety-category scope |
| OD-57 | Indication versus content separation |
| OD-58 | Terminology supersession scope for *Notification* and *Message* |

---

## Related documents

- [../architecture/adr-resident-communication-and-delivery-separation.md](../architecture/adr-resident-communication-and-delivery-separation.md)
- [../architecture/principles.md](../architecture/principles.md)
- [../architecture/framework.md](../architecture/framework.md)
- [../architecture/privacy.md](../architecture/privacy.md)
- [../architecture/explainability.md](../architecture/explainability.md)
- [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md)
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
- [../architecture/runtime-sequence.md](../architecture/runtime-sequence.md)
- [temporal-record.md](temporal-record.md)
- [decision-trace.md](decision-trace.md)
- [operational-trust.md](operational-trust.md)
- [stewardship.md](stewardship.md)
- [continuity.md](continuity.md)
- [glossary.md](glossary.md)
- [../contracts/concierge-contract.md](../contracts/concierge-contract.md)
- [../contracts/operational-trust-contract.md](../contracts/operational-trust-contract.md)
- [../governance/decision-ledger.md](../governance/decision-ledger.md)
