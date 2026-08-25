# Decision Ledger

> **Document status: Canonical governance.**
> Authority: [authority-order.md](authority-order.md).

---

## Purpose

The record of what the refoundation decided, and what it deliberately left open.

**A deliberately open decision is not a gap.** Recording it honestly is better than inventing an
answer the household has not chosen.

---

## Part 1 — Accepted decisions

| ID | Decision | Supersedes | ADR |
|---|---|---|---|
| **DL-01** | HTBW Core is defined by **seven responsibilities**: Foundation, Stewardship, Identity, Truth, Continuity, Operational Trust, Concierge | The four-service platform model | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-02** | **Human Trust is an outcome, not a layer.** It cannot be implemented directly | Any treatment of trust as a component | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-03** | **Behavioral Governance is cross-cutting**, not a layer | Any treatment of governance as a service | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-04** | **Truth is a first-class authoritative fact engine.** Foundation defines what a Fact is; Truth decides what is factual now | "Foundation owns truth" | [adr-truth-as-fact-engine.md](../architecture/adr-truth-as-fact-engine.md) |
| **DL-05** | **Voice Identity is superseded as a platform-service boundary.** The responsibility is **Identity**; voice is one evidence source | `adr-voice-identity-platform-service.md` | [adr-identity-replaces-voice-identity-boundary.md](../architecture/adr-identity-replaces-voice-identity-boundary.md) |
| **DL-06** | Identity Evidence, Identity Assertion, and Contextual Person-Presence Fact are **three distinct objects** with two distinct owners | Conflation of identity with presence | [adr-identity-replaces-voice-identity-boundary.md](../architecture/adr-identity-replaces-voice-identity-boundary.md) |
| **DL-07** | **Stewardship** is a first-class responsibility for significance, care, obligations, and lifecycle accountability | Stewardship as inventory; Asset Intelligence as the "what matters" layer | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-08** | The **HTBW asset model is Foundation-owned descriptive knowledge**. The standalone Asset Intelligence product remains separate, with no compatibility requirement | Asset Intelligence as an HTBW Core layer | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-09** | **Room Configuration is owned by Foundation**, and is an interaction-definition model | Room Configuration implicitly inside Concierge | [adr-room-configuration-ownership.md](../architecture/adr-room-configuration-ownership.md) |
| **DL-10** | **Contextual Vocabulary is part of Room Configuration.** Concierge consumes the resolved target | Vocabulary owned by Concierge | [adr-room-configuration-ownership.md](../architecture/adr-room-configuration-ownership.md) |
| **DL-11** | **Existence, Participation, Exposure, and Authority are four distinct states** | Conflation of existence with availability | [adr-room-configuration-ownership.md](../architecture/adr-room-configuration-ownership.md) |
| **DL-12** | **"Merged Room" is the single canonical term.** "Composite Room", "Operational Space", "Interaction Space", "Listening Area", and bare "Space" are superseded | The terminology fork across 15+ documents | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-13** | A Room and a Merged Room **behave identically**. Movement between constituent Physical Rooms of one Merged Room is not a transfer | Special-case orchestration for composites | [adr-room-configuration-ownership.md](../architecture/adr-room-configuration-ownership.md) |
| **DL-14** | **Operational Trust** owns authority; it is distinct from Human Trust | Absence of an authority owner | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-15** | The **Decision Trace** is a required output of every decision, action, non-action, and suppression | Explainability as an optional feature | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-16** | **Home Assistant First** — HA capability is used before HTBW builds its own (P21) | Parallel HTBW primitives by default | [adr-home-assistant-first-and-connected-storage.md](../architecture/adr-home-assistant-first-and-connected-storage.md) |
| **DL-17** | **Connected Storage** — durable household knowledge lives in attached storage with explicit traceability (P22) | Implicit or hidden storage | [adr-home-assistant-first-and-connected-storage.md](../architecture/adr-home-assistant-first-and-connected-storage.md) |
| **DL-18** | **Native Experience** — HTBW presents as a native part of Home Assistant; no invented UI standards (P23) | Custom UI conventions | [adr-home-assistant-first-and-connected-storage.md](../architecture/adr-home-assistant-first-and-connected-storage.md) |
| **DL-19** | **HTBW Core is greenfield.** No compatibility requirement with Asset Intelligence, Voice Identity, or Concierge | Implicit migration obligations | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-20** | **The framework is vendor-agnostic.** Home Assistant is the first implementation environment, not a constraint | Platform-shaped architecture | [adr-home-assistant-first-and-connected-storage.md](../architecture/adr-home-assistant-first-and-connected-storage.md) |
| **DL-21** | **A learned suggestion is not an autonomous policy** (P26) | Silent promotion of learned patterns | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-22** | The **assessment-to-platform traceability model** is canonical | Untraced recommendations | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-23** | The **authority order** in [authority-order.md](authority-order.md) governs all conflicts | Ad-hoc precedence | [adr-htbw-core-refoundation.md](../architecture/adr-htbw-core-refoundation.md) |
| **DL-24** | **Historical Explainability is a constitutional requirement** (P27). The home must retain enough governed information to reconstruct what it observed, believed, knew, and decided, and why. Retention is a **floor as well as a ceiling**. Historical Explainability is cross-cutting and owns no store | Explainability treated as single-decision only; retention treated only as a limit | [adr-historical-explainability-and-historical-truth.md](../architecture/adr-historical-explainability-and-historical-truth.md) |
| **DL-25** | **Truth is the system of record for both present and historical Facts** (P28). Operational expiration removes a Fact from *what is true now*; it does not delete *what was true then*. Truth owns Fact history and the eight lifecycle transitions. No consumer may maintain a competing or re-derived Fact history | Fact history unowned; `event-model.md` "event history remains authoritative" | [adr-historical-explainability-and-historical-truth.md](../architecture/adr-historical-explainability-and-historical-truth.md) |
| **DL-26** | **History is recorded as governed change, not as repeated full copies** (P29). A Current Projection answers what is true now; history consists of immutable Change Records and Domain Events, accelerated by Snapshots. HTBW must not require comparison of complete stored payloads to discover what changed | Full-payload versioning as the default history pattern; pure event sourcing | [adr-temporal-record-model.md](../architecture/adr-temporal-record-model.md) |
| **DL-27** | **Governed records reference exact versions and do not copy complete payloads** (P30). An explanation must remain accurate after configuration or policy changes. A dangling reference is reported, never silently rendered as though the source record never existed | Decision Traces embedding copies of their inputs | [adr-temporal-record-model.md](../architecture/adr-temporal-record-model.md) |
| **DL-28** | **Communication is separate from delivery** (P31). A Communication is a household interaction that exists independently of transport. Origination establishes that something must be conveyed, to whom, and with what significance; delivery establishes surface, moment, form, and whether at all. A Communication is never defined as a notification, push message, announcement, or indicator | Communication modelled as a transport artifact; delivery-channel enumerations embedded in domain models; *Notification* and *Message* as HTBW domain terms | [adr-resident-communication-and-delivery-separation.md](../architecture/adr-resident-communication-and-delivery-separation.md) |
| **DL-29** | **Permission to act does not imply permission to announce** (P32). Outbound communication is governed by the Existence → Participation → Exposure → Authority chain, evaluated against who can perceive the delivery surface. Where context is insufficient to deliver safely, the **delivery** degrades, not the governance | Exposure rules treated as applying only to requested disclosure | [adr-resident-communication-and-delivery-separation.md](../architecture/adr-resident-communication-and-delivery-separation.md) |
| **DL-30** | **Home Assistant First carries an ordered burden of proof** (P21). Native capability, then an existing maintained integration or ecosystem capability, then an HTBW extension that governs an existing capability, then — only then — a new HTBW capability. Each step must record the capability evaluated, the source documentation, the constitutional requirement, the remaining gap, and why the lower layer cannot practically satisfy it. **An undocumented evaluation does not discharge the burden, and unverifiable documentation leaves the decision open** | "Home Assistant First" asserted as a preference discharged by assertion | [principles.md](../architecture/principles.md), [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-31** | **HTBW references native Home Assistant objects and extends them; it does not copy them** (P21, P30). Home Assistant remains authoritative for its registry objects and every property those objects natively own. HTBW references them by stable identifier and retains only the additional information required by a constitutional requirement. Where an HTBW concept benefits from native visibility, state, targeting, or automation, a **native representation** is created or used in preference to a parallel hierarchy — and that representation is a projection, never a second authority. **No resident may be required to maintain the same information twice** | Native metadata mirrored into HTBW storage; parallel registries; a projection treated as the authoritative record; residents maintaining the same value in two places | [home-assistant-boundary.md](../architecture/home-assistant-boundary.md), [../models/asset.md](../models/asset.md), [../models/room-configuration.md](../models/room-configuration.md), [../models/person-and-identity.md](../models/person-and-identity.md) |
| **DL-32** | **Identity evidence reliability belongs to the Person-to-evidence-source association, not to the evidence type** (P26, P30, DL-06, DL-31). Every Identity Assertion states the **purpose** it answers, and no general-purpose identity score exists. A source contributes only to the claims it can actually establish, only where consent permits, weighted by the reliability configured for **that Person and that source**, adjusted for freshness, grouped into evidence families so correlated observations are not counted twice, and offset by claim-specific contradiction. **Configured reliability is a contribution weight, never measured accuracy. A provider match value is retained as reported and is never rewritten as fused confidence. Missing evidence is not contradicting evidence.** Identity performs fusion; Truth decides what becomes a Fact; Operational Trust decides permission separately. Reliability may be proposed by learning but **never silently changed**, and a change never rewrites an earlier assertion | Universal per-device-type weights; adding provider values to configured weights; counting one device's observations as independent confirmations; a kiosk account treated as a person; occupancy treated as identity; authentication treated as physical presence; confidence treated as permission | [../models/person-and-identity.md](../models/person-and-identity.md), [../contracts/identity-contract.md](../contracts/identity-contract.md), [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-33** | **Unknown Person is a valid Identity Assertion outcome, and never a native Person** (P15, DL-06, DL-31, DL-32). Identity may establish with high confidence that a human participant exists while being unable to associate that participant with any known Person. This is the existing `unknown` state, carrying whether a **human participant** is supported so that *"someone is here and I do not know who"* is distinguishable from *"I have no evidence anyone is here"*. A provider that evaluated successfully and returned no eligible match yields `unknown`, **never `unavailable`**. An Unknown Person expires with the assertion, references no Person, **creates no Home Assistant Person**, owns no preferences or history, inherits nothing from any resident, generates **no person-scoped learning**, and grants nothing. What an Unknown Person may request, control, or receive is the **unidentified-person policy**, owned by Operational Trust as a policy subject rather than a profile | A synthetic *Guest*, *Visitor*, or *Unknown* Person created to carry a policy; `unknown` reported as `unavailable`, an error, or an absence; a durable unknown-person profile that accumulates across visits; an unknown evidence source treated as a person, a role, or a recurring individual; occupancy treated as identity; resident permissions or preferences inherited by an unidentified person | [../models/person-and-identity.md](../models/person-and-identity.md), [../models/operational-trust.md](../models/operational-trust.md), [../contracts/identity-contract.md](../contracts/identity-contract.md), [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-34** | **Disclosure is evaluated against audience composition, not against requestor identity** (P32, DL-28, DL-29). Establishing who asked does not establish that everyone able to perceive the answer is an authorized recipient. **DL-29 stated this for unprompted communication; it applies identically to a solicited answer.** Access and disclosure are two separate Operational Trust decisions, and *access allowed, disclosure not appropriate* and *access allowed, private delivery available* must remain representable. **Audience composition** — who may perceive content through a proposed surface — is a governed input that **consumes** accepted identity assertions and presence Facts, **identifies nobody**, is never a second identity fusion, and must retain its uncertainty. Requestor, Speaker, Present Person, Potential Listener, Authorized Recipient, and Delivery Target answer different questions and are never collapsed | A single audience field; requestor authorization treated as room-wide authorization; occupancy count treated as audience identity; a detected device treated as proof its owner can hear; absence of evidence treated as proof of solitude; audience inference producing a person identity; a surface treated as private because it is a phone; a reasoning provider used as the sensitivity classifier | [../models/operational-trust.md](../models/operational-trust.md), [../models/communication.md](../models/communication.md), [principles.md](../architecture/principles.md) |
| **DL-35** | **A historically correlated actor is a bounded reference within one reconstruction, never an identity** (P15, P21, P22, P30, DL-30, DL-31). An **Unknown Actor Reference** groups observations sufficiently supported as belonging to one actor within a defined reconstruction scope. It is part of the projection, not a store, and it asserts no Person, role, occupation, intent, or criminality. **Temporal proximity alone never establishes correlation**; adjacency, travel plausibility, evidence continuity, entry and exit, contradictions, and competing-actor evidence are all evaluated, alternatives are preserved, and original evidence is never rewritten. One actor, several actors, and **unresolved plurality** are all representable. Observations, derived intervals, inferred transitions, estimated dwell times, and unknown gaps are **labelled distinctly**. Externally owned video is **referenced, never copied**, and is never asserted to depict the actor. Later identification is **additive**, preserving the original uncertainty and granting no retroactive permission | An actor or surveillance store independent of governed records; a cross-scope or reusable unknown-actor identity; joining an unknown proximity source and an unmatched voice because they co-occurred; presenting an estimate as a direct observation; implying continuous surveillance from intermittent evidence; describing an unknown actor as a cleaner, contractor, guest, intruder, burglar, or robber without governed evidence; treating an Evidence Package as legal proof | [../models/temporal-record.md](../models/temporal-record.md), [privacy.md](../architecture/privacy.md), [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-36** | **Identity supplies confidence; the consumer determines sufficiency, and sufficiency is never universal** (P15, DL-06, DL-32). One purpose-specific Identity Assertion is consumed by **four materially distinct evaluations** — the **Identity Presentation Threshold**, the **Capability Access Threshold**, **disclosure evaluation**, and **confirmation** — and satisfying one never satisfies another. **Operational Trust owns all four**, including the presentation threshold, because speaking a name is itself a disclosure. Identity never judges its own sufficiency; Concierge applies presentation and orchestrates confirmation but sets no threshold; Communication, Continuity, and reasoning providers set none. The requirement belongs to **what is being protected** — the capability, the protected resource, the protected operation, or the action-risk class — and attaches to the existing **Authority** state of Existence → Participation → Exposure → Authority. **Read, write, delete, and governance operations are never collapsed into one threshold.** *No identity required* is a legitimate requirement and is **never** an absence of governance. **Presentation is not personalization**: being addressed by name authorises no preference, session, resource, attribution, or learning | One universal confidence threshold, or a general-purpose identity score used as a gate; a threshold owned by Identity, Concierge, Communication, or a provider; presentation treated as access; access treated as personalization; access treated as disclosure; one threshold covering both read and delete; *no identity required* treated as *no policy applies*; a Person preference treated as a permission; a reasoning provider deciding sensitivity | [../models/operational-trust.md](../models/operational-trust.md), [../models/person-and-identity.md](../models/person-and-identity.md), [../contracts/operational-trust-contract.md](../contracts/operational-trust-contract.md), [../contracts/identity-contract.md](../contracts/identity-contract.md) |
| **DL-37** | **A confirmation is a bounded interaction outcome, and never retroactive certainty** (P15, P27, DL-32, DL-34, DL-36). Confirmation is the existing `permitted_with_confirmation` outcome and the existing bounded identity evidence source; **no second confirmation model exists**. **Confirmation Opportunity** — offered instead of refusal when confidence falls short — and **Confirmation Requirement** — demanded regardless of confidence — are different, and both are held by the protected capability or operation. A successful confirmation produces a **separate governed record**; it **never rewrites the provider match, the fused confidence, the evidence, the original assertion, or earlier uncertainty**, and **`Confirmed` is a scoped interaction state, not the top of the confidence scale**. **The capability declares the confirmation strength it requires**, and a spoken *yes* is not adequate for permission changes, enrollment, security configuration, financially consequential action, highly sensitive disclosure, Preservation Hold release, evidence deletion, or administrator changes. Every confirmation is bounded by purpose, capability and operation, interaction, channel, Room, Person, and time — **and never by audience**. `Denied`, `Unclear`, `Cancelled`, `Unavailable`, and `Expired` are first-class outcomes; a denial preserves the original assertion, records the contradiction, and **never silently promotes the next candidate or establishes the stated alternative**. **A confirmation challenge is itself a Communication** and is audience-evaluated before it is spoken | Confirmation rendered as 100 percent, as certainty, or as authentication; an original assertion rewritten or re-scored after confirmation; an unbounded or session-like confirmation; a confirmation for one capability silently covering another; identity or access confirmation treated as disclosure authorisation; a spoken *yes* accepted for every operation; a confirmation mechanism declaring its own sufficiency; `Unclear` or `Expired` treated as `Confirmed`; a denial creating a durable association, training a voice profile, or altering evidence weights; a candidate name announced aloud without audience evaluation | [../models/operational-trust.md](../models/operational-trust.md), [../models/person-and-identity.md](../models/person-and-identity.md), [../models/communication.md](../models/communication.md), [../models/decision-trace.md](../models/decision-trace.md) |
| **DL-38** | **The Identity Fusion Function is deterministic, ordinal, purpose-scoped, and stepped** (P15, P21, P26, P27, P30, DL-06, DL-31, DL-32, DL-33, DL-36, DL-37). Fusion begins with the **assertion purpose** and a **bounded candidate set**; ineligible evidence is **excluded before weighting, never down-weighted**. Nine rules govern the aggregation: **(F1)** each evidence family carries the highest support level it can reach **for that purpose**, and the assertion never exceeds the highest such ceiling; **(F2)** each correlation family yields **exactly one** contribution, and further observations in it may improve observation quality but never become a second confirmation; **(F3)** within a family, each qualification stage — provider match, observation quality, freshness, configured association reliability — may only **lower or hold**, and the four are **never multiplied into one product**; **(F4)** one **anchor family** sets the result and each **additional independent** family raises it by one **bounded step**, never by summation; **(F5)** a source requiring corroboration anchors only to a reduced ceiling; **(F6)** contradiction applies **bounded reduction** against the specific candidate and claim, and is never averaged away; **(F7)** absence is neutral — fewer sources yield a **lower ceiling, never a penalty and never a denominator effect**; **(F8)** `known` requires the leading candidate to reach the purpose minimum **and** satisfy a governed **separation** requirement, otherwise `ambiguous`; **(F9)** the function is **deterministic and monotonic** under a stated **Fusion Policy version**. Outcome selection is **ordered** so `not required`, `unavailable`, `unknown`, `ambiguous`, and `known` cannot blur, and **a weak candidate is never forced**. Freshness requires source- and purpose-specific windows, graduated reduction, and a hard cutoff together; **no duration is prescribed**. The output is an **ordinal support level mapped to a confidence band** through a versioned band map — **the band is authoritative**, a normalised numeric is a deterministic ordering value and **never a probability, likelihood, or measured accuracy**, and **one enumeration serves every purpose**. Every assertion references its **Fusion Policy version**; changes follow the existing promotion ladder and **never recalculate an earlier assertion**. The function is **uncalibrated by construction**, testable through deterministic fixtures requiring no biometric or proximity hardware. **Identity fuses; nobody else does**, and **confirmation is never an input** | Adding, averaging, or multiplying percentages; a weighted average that penalises a household for owning fewer sources; a Bayesian or belief-combination model claiming calibrated probability the home cannot support; treating separate entities or integrations as proof of independence; a native Person counted separately from the trackers producing it; the numerically highest candidate silently selected; a weak known candidate returned instead of Unknown Person; `unavailable` rendered as `unknown`; a consumer re-weighting or recomputing identity evidence; a confirmation fused as certainty; a reasoning provider nominating a candidate; a universal device-type weight; a Fusion Policy changed silently by learning; earlier assertions recalculated under a new policy | [../models/person-and-identity.md](../models/person-and-identity.md), [../contracts/identity-contract.md](../contracts/identity-contract.md), [../models/decision-trace.md](../models/decision-trace.md), [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-39** | **Identity has exactly four confidence bands; `None` belongs to Operational Trust** (P15, P27, P30, P32, DL-06, DL-32, DL-33, DL-34, DL-36, DL-37, DL-38). A `known` Identity Assertion carries one of **Low < Moderate < High < Very High** — ordered, purpose-specific, produced by **DL-38**, privacy-safe, and describing **only the strength of identity support**. The bands are **ordered**, and the ordering is authoritative; the labels are words because bands are never added, averaged, or treated as a distance, and an ordinal numeral invites exactly that misreading. A band carries **no access, presentation, personalization, disclosure, audience, confirmation, authentication, consequence-class, or sensitivity meaning**, and **Very High is not certainty, confirmation, or authentication**. **`None` is not an Identity band**: it is one of five **Required Identity Band** values — `None`, Low, Moderate, High, Very High — owned by **Operational Trust** and meaning *no known-Person identity is required for this operation*. An operation permitted under `None` is explained as *identity was not required*, **never** as a band exceeding `None`. **State and band are different dimensions**: bands apply only to `known`; `ambiguous`, `unknown`, `unavailable`, and `not required` carry **no band**, and an Unknown Person is assigned neither a band nor `None`. **Operational Trust owns every threshold**, including **Address by Name** — enabled state, minimum current band, neutral fallback, audience evaluation — wherever it is surfaced in configuration; Identity, Concierge, Communication, and Continuity own none. **Access and presentation are evaluated independently from the same assertion and may differ**, and a presentation threshold that is not met produces neutral wording and **never denies the action**. **Every interaction is evaluated from current eligible evidence for the applicable assertion purpose.** HTBW creates **no long-lived Identity session**: continuous Room occupancy is not continuous authentication, and a prior assertion, band, access grant, naming eligibility, or confirmation is **never revived because presence remained active**. **Assertion validity (OD-15) is not current-interaction applicability** — a valid assertion may remain a correct historical record while being inapplicable to a new interaction. **A confirmation is consumed by the protected operation that required it**: no occupancy grace period, no authenticated session, no automatic carry-forward, and **no change to the Identity band**; a bounded multi-step task must state its bound explicitly. Sensor debouncing belongs to evidence freshness under **DL-38** and never becomes an authorisation, presentation, or confirmation lifetime. Decision Trace records **identity result, requirement, access decision, presentation decision, and confirmation** as five separate outcomes | A fifth band called `None`; `None` treated as an Identity output; a band used as a permission, or described as authorising access; a band assigned to `unknown`, `ambiguous`, `unavailable`, or `not required`; `ambiguous` rendered as `Low`; an Unknown Person assigned a band; a threshold owned by Identity, Concierge, or Communication because of where it is configured; an action denied because a presentation threshold was not met; a name spoken from a prior interaction's eligibility; identity preserved by continuous occupancy; a presence-based or grace-period confirmation lifetime; a confirmation treated as an authenticated session or as raising the band; a valid assertion treated as the current-speaker assertion; access and presentation recorded as one outcome | [../models/person-and-identity.md](../models/person-and-identity.md), [../models/operational-trust.md](../models/operational-trust.md), [../contracts/identity-contract.md](../contracts/identity-contract.md), [../contracts/operational-trust-contract.md](../contracts/operational-trust-contract.md), [../models/communication.md](../models/communication.md), [../models/decision-trace.md](../models/decision-trace.md) |
| **DL-40** | **Required Confirmation Strength is an ordered class set; a class is not a mechanism** (P15, P27, P30, DL-32, DL-36, DL-37, DL-39). Operational Trust configures, for each protected operation, a **Required Confirmation Strength** on the ordered set **`None` < Verbal < Authenticated < Strong**, alongside and independent of the **Required Identity Band**. **What separates the classes is independence** — from the evidence that produced the assertion and from the channel that carried the request — **not friction, effort, or ceremony**. **Verbal** is an in-interaction acknowledgement on the channel already in use, and is therefore corroborated by evidence that was already insufficient; **Authenticated** requires a surface carrying a governed authenticated user context; **Strong** requires a factor deliberately independent of both the evidence and the channel. **A strength class is a governance statement, not a platform claim.** A class is satisfied only by a mechanism the deployment has **verified** as meeting it; **no mechanism is prescribed, assumed, or required to exist**, and no mechanism is credited with a class because it feels secure. Where a required class has no verified available mechanism, the confirmation outcome is the existing **`Unavailable`** and the operation is refused or degraded under normal policy — **a required strength is never silently downgraded to a weaker class**. Which class each capability, protected operation, and action-risk class requires is **configuration** resolved with **OD-51**, not architecture. **DL-37 is unchanged and unreopened**: this decision fills the enumeration slot DL-37 explicitly deferred, and every DL-37 rule stands — a confirmation is consumed by the operation that required it, is bounded, **never changes the Identity band**, and a spoken *yes* remains inadequate on its own for permission changes, identity enrollment, security configuration, financially consequential action, highly sensitive disclosure, Preservation Hold release, evidence deletion, and administrator changes | Confirmation strength is a **classification**, not an implementation; naming a required strength is not prescribing a mechanism; an unavailable strength never degrades to a weaker one; a strength class never becomes a second permission system, a second confirmation system, or an authenticated session | [../models/operational-trust.md](../models/operational-trust.md), [../contracts/operational-trust-contract.md](../contracts/operational-trust-contract.md), [../models/glossary.md](../models/glossary.md) |
| **DL-41** | **Capabilities declare dependencies, and a missing dependency disables the capability** (P21, P24, DL-30, DL-36, DL-39, DL-40). Every capability declares the preconditions without which it cannot exist in this home: a **native Home Assistant capability**, an **integration**, a **provider**, **Connected Storage**, **consent**, or **configuration**. Where a declared dependency is missing the capability is **unavailable**, the missing dependency is **named**, and the household is told in a sentence it can act on. **A native Home Assistant capability satisfies a dependency where it fully represents the requirement** (P21, DL-30); an **integration or provider** satisfies a non-native dependency where it is configured, valid, and available, presence in configuration not being sufficient; **Connected Storage** satisfies an artifact or extended-retention dependency; **consent** is an **eligibility** dependency and never a platform dependency; **configuration** satisfies a dependency on a declared setting. **A capability may declare several dependencies**: all **mandatory** dependencies must be satisfied for it to be available, while an unmet **optional** dependency improves quality without ever causing unavailability, and an undeclared load-bearing dependency is a defect. Availability turns on a dependency being **usable, not merely named** — not configured, configured but invalid, configured but currently unavailable, healthy, degraded but usable, and removed are distinguishable states, and a degraded-but-usable dependency is recorded rather than hidden. **HTBW does not emulate a missing dependency** — it does not substitute an approximation, build a local stand-in, or silently reduce the capability to something weaker that shares its name. **Capability unavailable is a dependency outcome, never a trust failure, an identity failure, or a permission failure**; expressing one as the other is a defect in both directions, because a household told it lacks permission when it lacks an integration cannot fix its home, and a genuine refusal dismissed as a setup problem is a safety failure. **Three questions are independent and evaluated in order** — *can this happen at all?* (declared dependencies), *who is this?* (Identity, DL-38 and DL-39), *may this happen?* (Operational Trust, DL-36, DL-39, DL-40). **Dependency is evaluated first**: where a capability is unavailable, identity is not consulted and no requirement is evaluated, and identity is likewise not evaluated where the protected operation requires none. An unavailable capability never lowers a threshold, and a satisfied threshold never conjures a missing dependency. **Five outcomes stay distinct and are never collapsed** — dependency unavailable, identity insufficient, Operational Trust denied, disclosure not appropriate, and runtime failure — each with a different cause, remedy, and explanation; exact wording is not prescribed, but the distinction is required. A Decision Trace records capability availability, the missing dependency, and that identity and requirement were not evaluated. **Truth may establish Facts about dependency health and Repairs may surface a defect, without either becoming the owner of the capability or its dependency declaration**, and **no runtime health protocol is defined**. **This creates no Capability responsibility, no capability registry service, and no dependency broker**; declaring a precondition is a property of a capability, owned by the responsibility that owns it, and the seven responsibilities are unchanged | A dependency failure rendered as a denial or an identity failure; the five outcomes collapsed into one generic failure; a threshold treated as a substitute for a dependency; an emulated, approximated, or silently reduced capability; an undeclared load-bearing dependency; an optional dependency causing unavailability; a dependency treated as present because it is named in configuration; identity evaluated for an unavailable capability, or where the operation requires none; a Capability responsibility, registry, or broker; a dependency evaluated after identity | [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md), [../models/operational-trust.md](../models/operational-trust.md), [../contracts/operational-trust-contract.md](../contracts/operational-trust-contract.md), [../models/decision-trace.md](../models/decision-trace.md) |
| **DL-42** | **Home Assistant owns Home Assistant data; Connected Storage is a capability dependency** (P21, P22, P27, P30, DL-30, DL-31, DL-41). **HTBW follows Home Assistant storage, retention, and artifact models by default** and creates no parallel store and no second retention model for information Home Assistant already governs and retains — Recorder history and long-term statistics, entity state and attributes, device state and registry data, Person state and `user_id` linkage, Area membership, floors, labels, aliases, Recorder retention and purge, and native metadata. These are **consumed through the accepted boundary**, not duplicated, and **HTBW builds no second Recorder**. **Duplication requires a documented governed gap, never a preference**: convenience, query shape, performance speculation, and *"it is easier to own it"* are not justifications, **wanting longer retention is not a gap**, and the ordered burden of proof (**DL-30**) applies unchanged. **The presence of Connected Storage transfers no ownership of native data**, and external history is an HTBW **extension** that uses native history as its source while available, never a replacement for it. **Duplication requires a documented governed gap, never a preference**: convenience, query shape, performance speculation, and *"it is easier to own it"* are not justifications, and the ordered burden of proof (**DL-30**) applies unchanged. **Connected Storage is required** wherever HTBW must persist an artifact that does not practically fit a native storage or retention model — asset documents, manuals, invoices, warranty records, voiceprints, materialised evidence packages, preservation and historical-reconstruction artifacts, and future HTBW-generated artifacts. **Without it the dependent capability is unavailable** under **DL-41** — capabilities needing no external artifact remain available — and three failures are prohibited: **no unmanaged local repository**, **no silent scope reduction**, and **no forcing of an artifact into attributes, entity state, or a helper to make it fit**. **Where storage is lost after artifacts exist**, creation and retention extension are **suspended**, persistence is **never claimed**, artifacts are **never recreated elsewhere**, and governed metadata and references are **not deleted merely because storage is temporarily absent** — they resolve to *"unavailable"* rather than *"never existed"*, and the condition is surfaced through the accepted degradation and Repairs surfaces; temporary unavailability and permanent replacement are distinct, and reconciliation mechanics remain an open implementation matter. **Conceptual storage classes are architecture; physical layout is not** — no root, folder, path, or format is accepted here, and technology, encryption, synchronisation, credentials, mount, backup, replication, migration, quota, and recovery tooling remain **OD-02** and **OD-03**, **both since closed by DL-44 and DL-45**. **External History Retention** is a single configured value that is **both the retention window and the purge window** — Disabled by default, in which case HTBW follows Home Assistant retention; where configured, anything older is removed by a **governed recurring purge** and **no separate archive tier is introduced**, with no *"archive after X, purge after Y"* model unless a future decision explicitly governs one. **Purge frequency is not architecture**: the window must be enforced regularly and explainably, but job timing and cadence are implementation choices. The configured period is an **ordinary ceiling, never an authority**: it overrides no retention floor required by **P27**, **a Preservation Hold suspends ordinary purge** for the records it covers, and retention per record class is declared inside the lifecycle under **DL-47**, with four structural floors that survive any configured window. **Changing the configured duration is a governed, historically explainable change**, an earlier decision remains explainable under the setting that applied when it was made, and **reducing the duration never silently deletes held or protected records**. Purge is not silence — a removed record stays distinguishable from one that never existed | A parallel store for natively governed data; a second Recorder; a second purge over native history; duplication justified by convenience or by a wish for longer retention; an unmanaged local fallback when Connected Storage is absent or lost; artifacts silently recreated elsewhere; persistence claimed when a write did not occur; governed metadata deleted because storage is temporarily unavailable; a hardcoded storage path treated as accepted architecture; a purge cadence treated as architecture; an archive tier created because data is old; a configured window treated as authority over a retention floor or a Preservation Hold; a reduced window applied as a bulk erasure; storage unavailability rendered as a refusal | [../architecture/connected-storage.md](../architecture/connected-storage.md), [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md), [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md) |
| **DL-43** | **No externally stored artifact exists without a documented lifecycle** (P21, P22, P27, DL-30, DL-41, DL-42). Every artifact class stored outside Home Assistant declares, **before it is introduced**, its **Artifact Type; owning responsibility; creating capability; required dependency; storage class** (a governed class, **not a physical path**); **anchor** to a native object or governed record; **retention strategy; deletion trigger; consent effect; Preservation Hold effect; behaviour when Connected Storage is unavailable; behaviour when storage is lost after creation; historical and explainability requirements (P27); access restrictions**; and, where applicable, **integrity or version requirements** and **recovery or reconciliation behaviour**. A retention strategy need not be a duration — *"retained while the anchor asset exists"* is a complete answer — but **"undecided" is not**, and an artifact whose retention or deletion strategy is unstated **must not be created**. **Artifact classes do not share one retention strategy**, and none is imposed on them. The accepted strategies are: **asset documents**, owned by **Foundation** which owns the Asset and its documentation anchor — **Stewardship owns significance and care, not the document artifact** — retained while the anchor Asset exists, deleted when the Asset is removed or the resident explicitly removes the document, with **no ordinary age-based purge** and unreachable documentation reported as **unavailable** rather than absent; **voice enrollment samples**, owned by **Identity**, temporary with zero default retention, removed on success and on cancellation, failure cleanup, consent withdrawal, or policy expiry, and **never becoming historical identity evidence merely because they existed**; **voiceprints and derived identity profiles**, owned by **Identity**, retained while the governed profile remains enabled **and consent remains valid**, deleted on profile removal or **consent withdrawal** — revocation removing the derived profile and its associations rather than merely their use — with biometric internals including **storage paths** never exposed, and **deletion of a voiceprint never rewriting an earlier Identity Assertion**; **extended historical records** governed by External History Retention under **DL-42**; **Preservation Hold** a marker or state on governed records and **not an artifact class of its own**, so duplicating payloads to satisfy a hold remains prohibited, **releasing a hold does not itself delete anything** but restores ordinary retention, and release remains **OD-39**; **Historical Reconstruction** a projection that is never retained, creating **no persistent reconstruction store by implication**; **Evidence Package** a projection assembled on demand and **not retained by default**, so only a deliberately materialised copy becomes an artifact and must then declare its own lifecycle, access, and preservation behaviour in its own right — **retention never making it legal proof** — with assembly, transport, integrity, and audience remaining **OD-40**. Consent and Preservation Hold both act on deletion and are evaluated before it — consent withdrawal **causes** deletion, a hold **defers** it — and their reconciliation with retention floors remains **OD-36**. Every future artifact proposal answers the artifact review checklist, and an unanswered question is an unmet burden of proof. **This creates no artifact registry and no artifact service**; the declaration lives with the architecture of the artifact class, owned by the responsibility that owns the artifact, and **physical storage owns nothing** | An artifact introduced without its declarations; an undeclared lifecycle treated as a permissive default; one retention strategy imposed across artifact classes; an ordinary age-based purge of asset documents; voice samples retained after enrollment completes, or treated as historical identity evidence; consent withdrawal treated as a visibility change; voiceprint deletion rewriting an earlier Identity Assertion; a Preservation Hold artifact class; a persisted Evidence Package or Historical Reconstruction store; an artifact registry or artifact service | [../architecture/connected-storage.md](../architecture/connected-storage.md), [../patterns/temporary-artifact-lifecycle-pattern.md](../patterns/temporary-artifact-lifecycle-pattern.md), [../architecture/privacy.md](../architecture/privacy.md), [../models/glossary.md](../models/glossary.md) |
| **DL-44** | **Home Assistant is the storage provider; Connected Storage is persistence, not an access surface** (P21, P22, P23, DL-30, DL-41, DL-42, DL-43). HTBW uses the connected storage Home Assistant already provides and **owns nothing beneath it**: not protocol selection between NFS and CIFS, not share mounting, not network credentials, not server discovery, not host mount configuration, and not general network-storage administration. Those belong to **Home Assistant or the deployment**; HTBW's ownership begins only once a valid storage dependency has been made available, and covers what HTBW puts there and how it governs it. **Connected Storage provides persistence; HTBW provides every governed interaction with the artifact.** Residents never require filesystem navigation to use an HTBW feature: they interact with the **Asset** and its document list, with the **enrollment session** and **voice profile**, and with **a question** about what happened — never with a storage hierarchy. The namespace is **not a resident file browser, not a second Home Assistant UI, not a generic document-management system, not an alternative media library, and not a direct authorisation surface**. **Media-browser exposure is a visibility boundary, never the sole security or authorisation control**: Home Assistant documentation establishes that media directories are protected by **authentication**, not by per-person authorisation, and establishes nothing about a file type being unreachable by every path, so sensitive internal artifacts — voiceprints, temporary samples, governed history — are **not exposed as resident media** absent a separately accepted requirement, and **HTBW, Operational Trust, privacy, and consent remain the security boundary**. HTBW requires **one governed namespace** with **separation by artifact-owning function or artifact class, collision-resistant governing-object references, no resident-supplied path as the authoritative identifier, no display name as the only storage key, traceability to the governing object, no cross-capability artifact mixing, removable empty structures, and migration through governed references rather than hardcoded user-facing paths**. Exact root and folder names, path depth, separators, and file naming are **implementation mapping** unless a stated interoperability requirement makes one architectural, and **a new branch is introduced only when an accepted capability declares an artifact class under DL-43**. Artifacts are located through a **governed reference**, never through a typed path or a chosen name; native registry properties are **not copied into the reference** merely to populate it; and **physical storage paths are not exposed** through ordinary UI, diagnostics, Repairs, or service responses where a governed identifier suffices. **File formats remain capability-specific and no universal payload schema is imposed.** Every artifact class declares one **interaction model** — **Managed Content**, **Internal Runtime Artifact**, or **Queryable Historical Record** — which classifies governed operations and resident visibility without replacing the DL-43 lifecycle declaration. **This creates no Storage, Artifact, Repository, Capability, or Dependency responsibility**; Connected Storage remains an architectural boundary and a capability dependency, and the seven responsibilities are unchanged | HTBW selecting or managing a storage protocol, mount, or credential; a generic resident file browser; storage treated as an authorisation surface; My Media visibility treated as a security control; an internal runtime artifact exposed as resident media for convenience; a resident-supplied path or display name used as the authoritative identifier; a physical path exposed as a public identifier; native registry properties copied into an artifact reference; a universal payload schema imposed across capabilities; folders reserved for capabilities that do not exist; a Storage, Artifact, or Repository responsibility | [../architecture/connected-storage.md](../architecture/connected-storage.md), [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md), [../architecture/privacy.md](../architecture/privacy.md), [../models/asset.md](../models/asset.md) |
| **DL-45** | **Every artifact declares a governing parent, and parent removal cleans up** (P21, P27, DL-41, DL-42, DL-43, DL-44). Every externally stored artifact declares a **governing parent object** and a **Parent Removal Behavior**. **The ordinary default is cleanup when the parent disappears; continued existence requires an explicit accepted reason.** On removal HTBW identifies dependent artifacts and references, evaluates Preservation Holds, retention floors, consent rules, and other lifecycle constraints, deletes artifacts no longer governed by a valid requirement, removes dependent references, removes empty capability-owned structures, preserves required Tombstones, Change Records, Decision Traces, and lifecycle evidence, reports failures through Repairs or accepted degradation, **never claims cleanup succeeded while storage was unavailable**, and reconciles incomplete cleanup once the dependency returns. **Cleanup never silently overrides** a Preservation Hold, a retention floor, an Evidence Package lifecycle, or historical explainability. **Retention and parent cleanup are distinct mechanisms**: time-window purge does not substitute for parent-object cleanup, parent-object cleanup does not substitute for time-window purge, and an object-scoped record class may be subject to both. **Native Home Assistant objects follow their own lifecycle** and are never deleted because an HTBW artifact structure was cleaned. Per class: deleting an **Asset** enumerates its artifact references, deletes every document without an overriding retention or preservation rule, removes empty Asset structures, surfaces cleanup failure, and **is not reported complete while mandatory cleanup remains unresolved** unless the accepted lifecycle supports a pending-cleanup state, with historical governance records permitted to remain but **never retaining the document payload without authority**; deleting a **single Asset document** removes the artifact, removes or tombstones its reference, may remove empty structures, and **leaves the Asset**; **voice enrollment success** removes temporary recordings and working artifacts and **does not claim a voiceprint successfully complete while mandatory sample cleanup is outstanding** unless the accepted model distinguishes generated from cleanup-complete; **cancellation or failure** leaves **no unmanaged recording and claims no voiceprint**; **voice profile deletion** removes voiceprint and derived artifacts and **leaves earlier Identity Assertions historically unchanged**; **Person deletion** evaluates every Person-governed voice profile and artifact so that **no orphan profile remains**, with consent and historical governance records following their own lifecycle. **No Room artifact class is created here**; if a future accepted capability introduces Room-scoped artifacts, its declaration states Room Parent Removal Behavior, artifacts shared with another valid governing object are **not** deleted because one Room disappeared, and merged-Room ownership is resolved before deletion. **Where storage is unavailable during cleanup the obligation is preserved, not discarded**: deletion is not claimed, a governed pending-cleanup state is retained under the existing reconciliation model, the reference is not silently discarded, the artifact is not recreated elsewhere, and the condition is surfaced; **retry and reconciliation timing are implementation mapping**, and reconciliation against floors and holds is owned by **OD-36** without a new decision | An artifact without a declared governing parent or Parent Removal Behavior; an orphan artifact surviving its parent by default; a voice profile surviving its Person; cleanup that silently overrides a hold or a retention floor; cleanup reported successful while storage was unavailable; a discarded reference converting a pending obligation into an orphan; a native object deleted because an artifact folder was cleaned; time-window purge substituted for parent cleanup, or the reverse; a Room artifact class invented to satisfy a future rule | [../architecture/connected-storage.md](../architecture/connected-storage.md), [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md), [../models/asset.md](../models/asset.md), [../models/person-and-identity.md](../models/person-and-identity.md) |
| **DL-46** | **Home Assistant retains native activity; HTBW retains the governed meaning Home Assistant does not represent** (P8, P21, P27, P28, P30, DL-04, DL-31, DL-42). Home Assistant remains authoritative for entity and device states, state changes, native events, occupancy and motion state, media-player state, Person and Device Tracker state, natively provided automation and script activity, and Recorder history. **HTBW consumes these by governed reference and persists no second copy merely to explain a decision later.** What HTBW persists is what the platform does not naturally represent: **purpose-specific Identity Assertions, safe identity-evidence summaries, Decision Traces, Operational Trust evaluations, policy outcomes, attribution, explicit Change Records, capability-dependency outcomes, audience and disclosure outcomes, governed non-actions, reason codes, historical policy and Fusion Policy versions, cleanup obligations, Tombstones, and broken-reference state**. **The Decision Trace is the canonical explainability spine**, linking trigger or request, relevant Facts, Identity Assertion, capability availability, Operational Trust evaluation, conflicts and alternatives, decision, action or non-action, observed outcome, and resident-safe explanation. It **references rather than copies** (P30), and **no second explainability model, reasoning record, or parallel decision history is created beside it**. **A longer HTBW retention requirement is never authority to copy native history**: HTBW does not retain every state transition, Recorder row, automation trace, sensor payload, voice interaction, or provider response, and any native payload copied into HTBW storage requires a separately documented governed gap and its own lifecycle. **Durable explanation after native expiry is already provided and requires no new construct**: the accepted Fact that Truth recorded — its Subject, Statement, confidence at the time, Provenance, evidence references or classes, Coverage, and Freshness — is the bounded summary, and it is **material to the decision, never a copied Recorder row**; a purged native reference resolves to *"no longer retained"*, never *"never existed"*. **Significance is already settled and creates no new owner**: a Decision Trace records an **HTBW decision evaluation**, not an occurrence, so a native state change with no HTBW decision produces no trace, an occurrence is evidence for an explanation rather than a trace of its own, and **HTBW never produces a Decision Trace for a decision HTBW did not make**. **Explainability is a governed record, never a reasoning log**: HTBW must not persist private chain-of-thought, hidden prompts, unrestricted model reasoning, raw provider deliberation, provider secrets, biometric internals, voiceprint vectors or embeddings, raw voice recordings, unnecessary conversation transcript, or unnecessary raw sensor payloads, and **the explanation must remain truthful after every sensitive detail is redacted**. Where identity was **not required**, the trace states that plainly and **never implies that identity authorised the operation**, while remaining free to record that identity supported attribution or named presentation. **This creates no History, Explainability, Persistence, Audit, or Activity responsibility, no generic event warehouse, and no second Recorder** | Copying native state history so HTBW can retain it longer; a second Recorder, event warehouse, or parallel decision history; a new Reasoning Record beside the Decision Trace; persisted chain-of-thought, embeddings, or raw samples; a Decision Trace for an occurrence HTBW did not decide; a trace claiming identity authorised an operation that required none; a purged reference rendered as though nothing happened; a bounded Fact summary widened into a Recorder replica; a History, Explainability, or Persistence responsibility | [../architecture/explainability.md](../architecture/explainability.md), [../models/decision-trace.md](../models/decision-trace.md), [../models/temporal-record.md](../models/temporal-record.md), [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) |
| **DL-47** | **Every governed record class declares its retention, exactly as every artifact class does** (P1, P27, P28, DL-42, DL-43, DL-45, DL-46). DL-43 required a declared lifecycle before an **artifact** could exist; the same rule now binds every **governed record class**, whether it is held in Home Assistant or in Connected Storage. **A record class whose retention is unstated must not be accepted**, *"undecided"* is not a retention strategy, and **one retention rule is not imposed across classes**. The accepted rules are: a **Current Projection** lives while its object lives and is replaced rather than retained; a **Change Record** is retained under the lifecycle of the governed object it describes, and under External History Retention where it is externally held, carrying its own **Retention Classification**; a **Domain Event** follows External History Retention; a **Snapshot** is an accelerator and **is retained no longer than the records it summarises**, never outliving the change history it accelerates; a **Decision Trace** is governed explainability history and follows **External History Retention** unless an accepted floor or a Preservation Hold applies, and **holding a trace preserves the governed source versions required to keep it explainable** rather than duplicating their payloads; a **Historical Fact** is Truth-owned governed history following External History Retention, with per-Fact-class differentiation an **Operational Trust policy matter, not architecture**; a persisted **Identity Assertion** is retained **with the Decision Trace or governed history it supports**, never under a separate universal duration and never as a licence to retain biometric internals; **Communication** records follow the same rule with content and metadata classified separately (**OD-49**); **Preservation Hold** metadata follows hold governance and **is not removed by ordinary purge, because a purge that erases the proof of the hold defeats the hold**; a **Tombstone** outlives the record it marks, for the same reason; **saved Evidence Packages and saved Historical Reconstructions** take their own artifact lifecycle under DL-43, while unsaved ones are projections that retain nothing. **Four structural floors survive any configured window**: Tombstones, consent-lifecycle records, records under Preservation Hold, and the governed versions required to keep a held Decision Trace explainable. **External History Retention is the ceiling and the purge boundary; it overrides no floor and no hold.** Everything remaining is a **household configuration value, not architecture** — the numeric floor and ceiling per class, the trace floor (**OD-05**), the experience-history question (**OD-26**), and the communication content-versus-metadata classification (**OD-49**) — and **no universal retention matrix is required, because retention is declared inside every lifecycle**. **This creates no retention registry, no retention service, and no central purge owner**; each responsibility enforces retention over its own records | A governed record class accepted without a declared retention; an undeclared retention treated as a permissive default; one retention rule imposed across every class; a Snapshot outliving the Change Records it summarises; an Identity Assertion retained on its own universal clock; Preservation Hold metadata or a Tombstone removed by ordinary purge; a configured window overriding a floor or a hold; a retention registry, retention service, or central purge owner; a universal retention matrix rebuilt outside the lifecycle declarations | [../models/temporal-record.md](../models/temporal-record.md), [../models/operational-trust.md](../models/operational-trust.md), [../architecture/privacy.md](../architecture/privacy.md), [../models/truth.md](../models/truth.md) |

| **DL-48** | **Obligation condition and obligation lifecycle are orthogonal, and closure requires evidence** (P21, P26, P27, P28, DL-15, DL-26, DL-27, DL-46, DL-47). An obligation carries **two independent fields**. Its **condition state** answers *what is true of the world relative to the care expectation* and remains exactly the accepted six — `met`, `due`, `unmet`, `overdue`, `waived`, `unknown`. Its **lifecycle state** answers *what has happened to the obligation record itself* and is `raised`, `active`, `deferred`, `closed`, `reopened`. **Deferral and closure are removed from the condition set and may never be added to it**, which resolves the defect this was raised on: the Stewardship history description named two lifecycle outcomes as though they were states. **Every lifecycle transition is a Change Record written at the moment of transition** (**DL-26**), never derived later by comparing stored payloads, carrying actor, recorded time, effective time where it differs, reason where supplied, and **version-pinned references** to the care expectation evaluated against (**P30**, **DL-27**). **One new record class is accepted — the Care Evidence Record** — which is what closes an obligation and which declares its own **Retention Classification** under **DL-47**. It carries exactly one evidence kind: `observed`, where Truth established that the condition resolved; `attested`, where a person with accountability recorded that care occurred and Truth cannot observe it; `performed`, where an executor reported completion **and** Truth or an attestation confirms the outcome; or `waived`, a household decision that closes the obligation **without asserting that care occurred**. **An executor reporting success is not closure**, and neither is a dismissed reminder, a ticked projection, or a requested action. **`unknown` is never `met`** and **absence of evidence is never compliance**. A **reopened** obligation retains its identity so a repeatedly unmet obligation stays reportable as a pattern. **Grouping of simultaneous obligations is a projection concern and is not part of the obligation model** (**OD-23**). **A satisfied-without-action obligation is now distinguishable from a performed one** by its evidence kind | Deferral and closure as condition states; closure by dismissal, tick, request, or executor report; snapshot comparison to discover lifecycle change | [../models/stewardship.md](../models/stewardship.md), [../contracts/stewardship-contract.md](../contracts/stewardship-contract.md), [../models/temporal-record.md](../models/temporal-record.md) |
| **DL-49** | **Custody is a time-bounded accountability record owned by Stewardship, and is neither ownership, nor caretaking, nor location** (P21, DL-07, DL-08, DL-26, DL-27, DL-45, DL-46, DL-47, DL-48). A **Custody Period** records **who is accountable for a subject, for a bounded time**, carrying the custodian designation, the declared custody location context, an agreement reference where one exists, the party bearing insurance responsibility for the period, the begin time, the expected end time where agreed, the actual end time on closure, purpose, and notes. **Foundation defines the object type and continues to own the Asset, the `owner-of` and `caretaker-of` relationship types, and the `located-in` declared location; Stewardship owns the Custody Period record, its lifecycle, and its history**, because a custody period must consume Truth and must produce obligations, and dependency-view rule 6 forbids Foundation from consuming anything. **No new Foundation relationship type is created**: `owner-of` and `caretaker-of` are **durable**, custody is **episodic**, and episodic accountability belongs on a time-bounded record rather than in a standing relationship set — whether a role-bearing construct later supersedes this remains **OD-77**, which this decision neither expands nor resolves. **The custodian designation may be a governed reference to an existing Foundation object or free text**, and free text is preserved verbatim in history with the actor who recorded it. **A Custody Period opens on a recorded Check-Out and closes only on a recorded Check-In**; physical return is a Truth Location Fact and is **evidence toward** closure, never closure itself, because Truth can establish where something is and cannot establish that an accountability period has been accounted for. **A custody transfer changes the accountable party, the declared custody location context, and insurance responsibility for the period. It does not change ownership, the asset's declared `located-in` home, its observed current location, or its significance.** **HTBW does not adopt a fixed custody-status enumeration as canonical**, and a Custody Period instead carries a governed lifecycle of `opened`, `updated`, `closed`, `corrected`, and `adversely_resolved`, each transition written as a Change Record. The current custodian is the open Custody Period, or the household by default — **and the absence of an open period is a statement about accountability only, never about location: on-site status requires a Truth Location Fact or Foundation's declared `located-in`, and is never inferred from ownership or from the absence of a custody record.** **In transit and in storage are Custody Periods whose custodian is the carrier or the storage provider**, not separate states, which lets a household record every leg or none — and **no unrecorded leg is ever inferred**. **Overdue is not a custody state**: an expected end time that passes leaves custody unchanged and the period open, and changes only the obligation that expectation created. **Lost and stolen are not custody states and are never custodians**; they are coordinated outcomes in which Truth reports location `unknown`, the Custody Period ends `adversely_resolved` with a recorded disposition **while preserving the last known custodian**, Stewardship raises the resulting obligations, Operational Trust may authorise a **Preservation Hold**, and a declaration of theft is recorded with provenance rather than inferred — and an adverse resolution **never satisfies** the return obligation, which closes only by a Care Evidence Record of kind `waived`. **Condition evidence, photographs, appraisals, conservator and repair reports, contracts, and insurance material are Asset documents under the Asset as governing parent** (**DL-45**), referenced from the custody record by **version-pinned governed reference and never copied into it** (**DL-27**, **P30**) | Custody as ownership, as current location, or as an enumerated state machine; overdue, lost, or stolen as custody states; a first-class Counterparty object; document payloads duplicated into custody records; inferred chain-of-custody legs | [../models/stewardship.md](../models/stewardship.md), [../contracts/stewardship-contract.md](../contracts/stewardship-contract.md), [../models/asset.md](../models/asset.md), [../contracts/foundation-contract.md](../contracts/foundation-contract.md), [../models/glossary.md](../models/glossary.md) |
| **DL-50** | **A capability may declare an execution host, and a voice provider reports candidates that Identity alone resolves** (P21, P25, DL-05, DL-06, DL-30, DL-32, DL-33, DL-36, DL-38, DL-39, DL-41, DL-43, DL-44, DL-47). **An HTBW capability that cannot execute inside the Home Assistant integration process may declare an execution host**, named in the capability's dependency declaration and in the Decision Trace exactly as any other dependency is. **The rule is a per-capability declared host; a Home Assistant app is the reference deployment and not the architecture** — because **P25** keeps Home Assistant the first implementation environment and not a constraint, and apps exist only on some installation types, so **no answer may bind HTBW to one deployment topology**. Refusing a host outright was rejected as a large capability loss taken by omission; a household-provided external service remains **permitted** as a declared host and engages **OD-07** and consent rather than being foreclosed; native-only was rejected because it would have removed voice evidence entirely on the verified host. **One conformance rule is recorded verbatim: a hard manifest `requirements` entry is an all-or-nothing gate for the entire integration, so a dependency that is optional to a capability must not be declared there, or a degraded capability becomes a total setup failure.** **DL-41 applies unchanged**: a host that is missing, unreachable, or incompatible makes the capability **unavailable and names why**, with **no approximation, no substitution, no local stand-in, and no silent reduction to something weaker sharing its name**, and **capability unavailable is never expressed as a trust failure, an identity failure, or a permission failure**. **An execution host is not a third-party engine that decides and acts** — it decides nothing, every decision remains with the responsibility that owns it, and delegation therefore remains **OD-66** and is not resolved here; **data residency remains OD-07** and is not resolved here; and **HTBW acquires no host operating-system administration**, consistent with the storage boundary. **The Wyoming protocol is the preferred voice-pipeline interoperability boundary** wherever HTBW requires runtime audio, discharging the **DL-30** burden at step 2 as an existing maintained ecosystem capability; **Wyoming is a protocol and never an HTBW component**, and **no third-party voice project becomes a mandatory HTBW dependency**. **Providers produce evidence and HTBW produces decisions**: a voice provider emits an **unbound Voice Evidence Record** carrying an **ordered candidate list with a provider-reported score for each candidate**, separation data, ambiguity indicators, quality and channel metadata, and **encoder family, encoder version, and audio-contract version**, and it resolves **no person**, emits **no confidence band**, produces **no fused confidence**, reaches **no threshold verdict**, and authorises **nothing** — **a provider match value is retained as reported and is never rewritten as fused confidence**, and a provider value is **meaningful only within its own provider**, never compared across providers and never rendered to the household. **Compatibility is enforced before comparison and never warned about afterwards**, an incompatible gallery is an explicit **DL-41** outcome, and a model upgrade requires a governed migration path rather than a documented instruction to re-enroll. **Speaker evidence is enrichment and never a gate**: a non-match, an unknown speaker, an unavailable host, or an incompatible gallery **never suppresses the transcript**, `unknown` is never reported as `unavailable`, and **identity never travels inside transcript content** in any form, because an assertion placed in a content field is logged, retained, and passed onward with no audience evaluation. **Region-level matching is a provider capability and never an Identity decision**; **speaker-conditioned audio extraction is validation-required and is not accepted behaviour**; **passive conversation-state evidence is a North Star and no implementation is authorised**; and **raw rejected-audio retention is not enabled by default and requires a declared purpose, duration, access controls, deletion behaviour, consent and privacy review, and a DL-43 artifact declaration before it exists**. **No new responsibility, record class, artifact class, retention rule, threshold, or confidence representation is created by this decision, and no add-on, container, runtime, model, or vendor is selected by it** | Every **DL-30** rung implicitly assuming execution inside the integration process; apps addressed **only** as third-party engines that decide and act; a single-winner provider match treated as an identity answer; a provider-emitted confidence band; a universal provider confidence threshold | [adr-wyoming-compatible-voice-evidence-runtime.md](../architecture/adr-wyoming-compatible-voice-evidence-runtime.md) |

---

## Part 2 — Open decisions

Each is deliberately unresolved. None blocks the constitutional foundation.

> **GitHub issues are the authoritative source for the current status, remaining questions,
> dependencies, and closure evidence of every open decision below.** This ledger remains authoritative
> for **what the decision is** and for every accepted decision in Part 1. The identifier-to-issue
> mapping, with dependency summaries, is
> [open-decision-issue-index.md](open-decision-issue-index.md); the governance backlog Epic is issue
> **#147**.

| ID | Question | Responsibilities affected | Recommended ADR topic |
|---|---|---|---|
| **OD-01** | Home Assistant representation strategy — **partially resolved**. The reference-and-extension rule, the three representation categories, and the object-by-object mapping are accepted as **DL-31** and recorded in [home-assistant-boundary.md](../architecture/home-assistant-boundary.md). **The residual is the persistence shape of Change Records, Snapshots, and Current Projections** — config entry, subentry, or private storage — which **OD-01 now owns alone**. It was previously duplicated in **OD-34**; OD-34 has closed on the persistence *model*, and this mechanism question was not carried with it. **Narrowed by verified platform documentation**: config entries and subentries are **user-created, user-removable configuration data**, which makes them structurally unsuitable for immutable historical records. It **remains open** because the Storage helper documentation could not be verified. Classification mechanics are **OD-68**, Entity projection is **OD-69**, Merged Room projection is **OD-70** | Foundation, Room Configuration | Governed-record persistence shape |
| **OD-02** | **Resolved as DL-43, DL-44, and DL-45.** The question was the connected-storage **format** for vocabulary, participation, and documentation. Its architectural content was how HTBW **locates and governs** an externally stored record, and that is answered by the **governed artifact reference contract** — stable identifier, class, owning responsibility, creating capability, governing parent, native anchor, storage class, relative locator, lifecycle policy, retention, deletion trigger, consent and preservation effects, availability, broken-reference, and reconciliation state — together with the artifact declaration and interaction model required of every class. **No universal payload schema is required, and file formats remain capability-specific.** Remaining encoding choices are per-capability implementation | Foundation, Room Configuration | **Closed — DL-43, DL-44, DL-45** |
| **OD-03** | **Resolved as DL-42, DL-44, and DL-45.** The question was storage technology, encryption, and synchronisation. **Home Assistant is the storage provider**: it owns protocol selection, mounting, credentials, and network-storage administration, and HTBW selects none of them. What HTBW must own is settled by DL-44: **one governed namespace, separation by artifact-owning function or class, collision-resistant references, no resident-supplied path or display name as an identifier, traceability to the governing object, no cross-capability mixing, removable empty structures, and migration through governed references**. Exact root and folder names, path depth, and file naming are **implementation mapping**. Encryption, backup, replication, and quota belong to Home Assistant or the deployment, and **HTBW records no unmet requirement against them** | All | **Closed — DL-42, DL-44, DL-45** |
| **OD-04** | Exact global priority order across policy scopes, **including the ordering applied to competing Communications**. **Unchanged by DL-36.** Threshold and confirmation requirements are ordinary policy statements resolved by the existing precedence order and the existing most-restrictive rule; **they introduce no new precedence mechanism, no threshold-specific ordering, and no override path**. A household default, a Room policy, a capability requirement, and a per-operation requirement compete exactly as any other policies do, and **a Person preference is never a permission** | Operational Trust, Concierge | Policy precedence order |
| **OD-05** | Decision Trace retention **floor and ceiling** — how long a trace must be kept to satisfy P27, and how long it may be kept under privacy minimisation. **Narrowed by DL-47: the rule is settled — a trace is governed explainability history following External History Retention unless an accepted floor or a Preservation Hold applies, and holding a trace preserves the versions that keep it explainable. Only the values remain** | Concierge, Operational Trust | Trace retention floor and ceiling |
| **OD-06** | Consent user experience | Identity, Operational Trust | Consent capture and revocation UX |
| **OD-07** | Local versus cloud voice implementation | Identity | Voice processing locality |
| **OD-08** | **Resolved as DL-39 and DL-40.** **Resolved:** Identity produces **exactly four confidence bands** — **Low < Moderate < High < Very High** — carried only by a `known` assertion, describing identity support only, and carrying no access, presentation, personalization, disclosure, audience, confirmation, or authentication meaning. **`None` is not an Identity band**; it is one of five **Required Identity Band** values owned by Operational Trust, meaning *no known-Person identity is required for this operation*. **State and band are separate dimensions**, and an Unknown Person is assigned neither. **Operational Trust owns every threshold**, including **Address by Name**, regardless of configuration surface. **Access and presentation are evaluated independently** and may differ. **Every interaction is evaluated from current eligible evidence**; there is **no long-lived Identity session**, continuous occupancy is not continuous authentication, and **assertion validity is not current-interaction applicability**. **Confirmation is consumed by its protected operation**, has no occupancy grace period, and never changes the band. Per-class and per-capability defaults, the Address by Name default, and the Presentation Threshold default are **configuration**, resolved with **OD-51**'s risk-class enumeration, and are not held open here. Household-facing band **labels** are adopted as **Low, Moderate, High, Very High**; the ordering is authoritative and the labels carry no operational meaning. **Residual discharged as DL-40.** The residual was framed as *which mechanisms* constitute a stronger-than-verbal confirmation, and that framing conflated two separable things. **A required strength is a classification; an implemented mechanism is a platform capability.** Architecture needs only the ordered class set **`None` < Verbal < Authenticated < Strong**, the rule that a capability declares the class it requires, and the rule that a class is satisfied only by a mechanism the deployment has verified as meeting it. **No Home Assistant mechanism is prescribed or assumed** — companion-application, push, PIN, and secondary-factor confirmation remain unverified against official documentation and remain barred from prescription — and where no verified mechanism meets a required class the outcome is `Unavailable`, never a downgrade. Mechanism mapping is deployment configuration and platform capability discovery, not an open architectural question. **DL-37** stands unchanged: the capability declares the strength it requires, and a spoken *yes* remains inadequate for permission changes, enrollment, security configuration, financially consequential action, highly sensitive disclosure, Preservation Hold release, evidence deletion, and administrator changes | Identity, Operational Trust | Closed — DL-39, DL-40 |
| **OD-09** | Export and deletion mechanics, **evaluated against the native History export and history endpoint, and against Backup**. Native export is entity-scoped and ungoverned, and connected storage is outside Backup scope unless the deployment deliberately places it within it | All | Data portability and erasure |
| **OD-10** | Whether Floors are a first-class scope. **The Floor registry developer documentation could not be verified; this must not be closed on assumed Floor-registry behaviour** | Foundation, Operational Trust | Scope hierarchy |
| **OD-11** | Whether a Physical Room may participate in more than one Room | Foundation, Room Configuration | Room composition rules |
| **OD-12** | Whether exclusion reasons are structured or free text | Room Configuration | Exclusion metadata |
| **OD-13** | Whether vocabulary terms may be inherited from Home scope and overridden per Room | Contextual Vocabulary | Vocabulary inheritance |
| **OD-14** | **Resolved.** Home Assistant naming information is an **input** to HTBW vocabulary and never an authority. A native name or Assist alias may **seed** a contextual term; the seed is attributed to Home Assistant, is not synchronised afterwards, and is **never written back**. A household-defined term is never overwritten by a native change. Recorded in [../models/contextual-vocabulary.md](../models/contextual-vocabulary.md) and [home-assistant-boundary.md](../architecture/home-assistant-boundary.md) under **DL-31**. **OD-13** is unaffected | Contextual Vocabulary | Resolved — no ADR required |
| **OD-15** | Identity assertion validity windows by confidence band. **Scope clarified by DL-37: this decision is assertion lifetime only, and is not the confirmation decision.** How long an Identity Assertion remains valid belongs to Identity here; how long a governed **confirmation** covers a request belongs to Operational Trust, and is settled by **DL-39** as **consumption by the protected operation**. The two must never be conflated, and **a confirmation never extends the life of the assertion it was raised against**. **Scope further clarified by DL-38: observation freshness is not assertion lifetime.** How long each *source observation* may contribute is Fusion Policy, decided inside fusion; how long the *resulting assertion* stays valid is this decision. **DL-38 does not close it**, and no duration is prescribed by either. **Scope further clarified by DL-39: validity is not current-interaction applicability.** An assertion inside its window remains a correct historical record for the purpose and moment it was produced; it does **not** thereby become the current-speaker assertion for a new interaction, and **a validity window creates no permission, no confirmation persistence, and no authorisation grace period**. Presence continuity never extends speaker-attribution validity. **DL-39 does not close it either** | Identity | Assertion lifetime |
| **OD-16** | **Resolved.** Identity evidence weighting is complete. The evidence architecture was accepted as **DL-32**, and the **Identity Fusion Function** is now accepted as **DL-38** and recorded in [../models/person-and-identity.md](../models/person-and-identity.md): assertion-purpose-first evaluation, bounded candidate generation, eligibility gating before weighting, the nine fusion rules **F1–F9**, ordered outcome selection, freshness treatment, confidence-output semantics, Fusion Policy versioning, the calibration boundary, and deterministic fixtures. **No mathematics was invented**: the function is ordinal and stepped rather than arithmetic, and it makes no probabilistic claim. **Remaining values are implementation mapping, not architecture** — freshness durations, the number and size of corroboration and reduction steps, the separation margin, per-purpose minimums, and reason-code strings are all **Fusion Policy configuration**, versioned and governed, and none of them is an unresolved architectural question. Band **naming and operational meaning** are now accepted as **DL-39**. Room-granularity ceilings remain bounded by unverified native Room-level detection, which limits one source's ceiling and not the function | Identity | Resolved — accepted as DL-38 |
| **OD-17** | Composite-fact aggregation algorithm and coverage thresholds, **including how a natively assigned Area temperature or humidity entity participates as an input** — see **OD-61** | Truth, Room Configuration | Composite fact computation |
| **OD-18** | Fact validity and expiration defaults per fact class — this governs **operational** Fact validity, **not** Historical Fact retention, which is settled by **DL-47** | Truth | Fact freshness policy |
| **OD-19** | Governed conflict-resolution rules for disagreeing evidence, **including disagreement between a natively assigned Area environmental entity and the HTBW-configured input set** | Truth | Evidence conflict resolution |
| **OD-20** | Whether HTBW Core consumes the standalone Asset Intelligence product as an optional evidence source. **Framed by DL-41: if it does, it is a declared capability dependency, and its absence makes the dependent capability unavailable rather than degraded** | Foundation, Stewardship | Optional product integration |
| **OD-21** | How significance is expressed — ordinal band, score, or household vocabulary | Stewardship | Significance representation |
| **OD-22** | Escalation ladder semantics and defaults. **This is the single escalation ladder, and it serves Communications as well as obligations.** Repeating delivery to the same audience is retry, not escalation | Stewardship, Operational Trust | Escalation model |
| **OD-23** | Whether obligations project into HA calendars, `todo` entities, or a connected store. **A `todo` projection does not own the obligation, and item completion is a list state, not proof that care occurred** | Stewardship | Obligation projection |
| **OD-24** | Session-merging algorithm when two people's sessions meet in one Room | Continuity, Concierge | Session merge policy |
| **OD-25** | Resume eligibility window defaults per experience class | Continuity | Resume eligibility |
| **OD-26** | Whether experience history is retained per person, per room, or both, and for how long. **Narrowed by DL-47: experience history is a governed record class following External History Retention with its own Retention Classification; the scoping and duration questions remain** | Continuity | History retention |
| **OD-27** | Whether concurrent same-class sessions in one Room are permitted by default | Continuity | Concurrency policy |
| **OD-28** | The learned-preference lifecycle — how a suggestion is proposed, accepted, rejected, corrected, paused, forgotten, versioned, and revoked, and how acceptance is recorded so that a past adaptive action stays reconstructable after the preference changes (**P26**, **DL-21**). Evidence eligibility is **OD-65** | Operational Trust, Continuity | Learned-policy promotion |
| **OD-29** | Where Decision Traces are persisted — HA Activity, connected storage, or both, **including purge exemption and Governed Reference resolvability**. **Activity records what changed and never why, so an Activity entry is a projection of a trace and never the trace itself** | Concierge | Trace persistence |
| **OD-30** | Which surfaces expose Decision Traces, and to whom | Concierge, Operational Trust | Trace visibility |
| **OD-31** | Whether assessment records are stored in connected storage as first-class documents. **If they are, DL-43 applies and the five artifact declarations must be stated as part of the answer** | Assessment, Foundation | Assessment record storage |
| **OD-32** | Reassessment cadence, per-item or per-home | Assessment, Stewardship | Maturity review cadence |
| **OD-33** | **Resolved as DL-43, DL-46, and DL-47.** The question was the retention floor and ceiling per record class and Fact class, and it presumed a **universal retention matrix**. No matrix is required: **retention is declared inside every lifecycle**, and DL-47 extends that obligation from artifact classes to every governed record class. Every current class now has a rule — Current Projection, Change Record, Domain Event, Snapshot, Decision Trace, Historical Fact, Identity Assertion, Communication, Preservation Hold metadata, Tombstone, and saved projections — with **External History Retention as the ceiling and purge boundary** and **four structural floors that survive any configured window**: Tombstones, consent-lifecycle records, held records, and the versions required to keep a held trace explainable. Per-Fact-class differentiation is an Operational Trust **policy** matter. The remaining numeric values are household configuration and are held by **OD-05**, **OD-26**, and **OD-49** | All | **Closed — DL-43, DL-46, DL-47** |
| **OD-34** | **Resolved as DL-42, DL-44, DL-46, and DL-47.** The question was the persistence strategy for Change Records, Snapshots, Historical Facts, and Decision Traces. The **temporal-persistence model** is complete: what is persisted, referenced, projected, temporary, or saved only on request is settled by the Temporal Record model; ownership is settled by the history-ownership table; immutability, bitemporality, and Version Identity are constitutional; **Home Assistant remains authoritative for native history and HTBW builds no second Recorder** (DL-42); the **Decision Trace is the explainability spine** and durable explanation after native expiry is carried by the accepted Fact rather than by a copied row (DL-46); retention is declared per record class (DL-47); and externally held records follow the governed namespace and reference contract (DL-44). **The residual that remained was never OD-34's**: *config entry, subentry, or private storage* is the **Home Assistant representation mechanism**, stated verbatim in **OD-01**, and it is retained there rather than duplicated here. Serialization, indexing, batching, compression, scheduling, and database technology are **implementation mapping** | All | **Closed — DL-42, DL-44, DL-46, DL-47** |
| **OD-35** | Historical query surface and access, **including access to actor reconstructions and movement histories**, which Operational Trust governs and which must not be reachable through generic Room Help or a general-question capability (**DL-35**) | All | Historical retrieval and access |
| **OD-36** | Reconciliation of deletion and export obligations with retention floors and Preservation Holds, **noting that Recorder offers no per-record purge exemption and that Backup coverage of connected storage must be verified for the deployment rather than assumed**. **Narrowed by DL-45, which adds parent-object cleanup as a deletion trigger and assigns the pending-cleanup and post-recovery reconciliation obligation here rather than to a new decision. The unresolved question is unchanged: how a deletion obligation and a preservation obligation are reconciled when they conflict** | Operational Trust, All | Deletion versus preservation |
| **OD-37** | Snapshot triggers, cadence, and scope per responsibility | All | Snapshot policy |
| **OD-38** | Version identity, correlation, and causation identifier strategy, **including evaluation of Home Assistant Context IDs**. Context may support correlation, may support an initiating-to-resulting relationship where Home Assistant supplies a parent context, and may support resident attribution only where the platform supplies an attributable user. **Context does not establish semantic reasoning, does not replace Version Identity, does not replace a Decision Trace, and does not prove causation beyond the documented relationship** | Foundation, All | Identifier and correlation strategy |
| **OD-39** | Preservation Hold authority, duration, review, release, and conflict with deletion. **Bounded by DL-43: a hold is a marker on records and is not an artifact class of its own**, so no hold payload store may be introduced while this remains open. **Bounded further by DL-45: a hold survives parent-object removal and cleanup never silently overrides it. Hold release remains separate from parent deletion and remains unresolved** | Operational Trust | Preservation Hold governance |
| **OD-40** | Evidence Package assembly, transport, integrity representation, and audience. **Bounded by DL-43: a package is a projection assembled on demand and is not retained by default**, so no package store may be introduced while this remains open; a deliberately materialised copy is an artifact and must declare its own lifecycle. **Further narrowed by DL-44 and DL-45: a saved package is Managed Content, reached through the owning capability rather than through storage, and its governing parent and Parent Removal Behavior are part of that declaration. Assembly, transport, integrity representation, and audience remain unresolved** | Concierge, Operational Trust | Evidence Package governance |
| **OD-41** | **Incident and Case object model** — whether an Incident remains an ad hoc retrieval scope only, or may become a persisted Incident or Case object. **An Unknown Actor Reference is a reconstruction-scoped projection (DL-35) and does not settle this decision in either direction** | Foundation, Operational Trust, Concierge | Incident and Case object model |
| **OD-42** | Communication object persistence and Home Assistant representation — subordinate to **OD-01**, which now owns the persistence-mechanism residual alone | Foundation, All | Communication persistence |
| **OD-43** | Delivery Surface capability model — what a surface can convey, **to whom it is perceptible**, and whether it can attest presentation | Foundation, Concierge | Delivery Surface capability model |
| **OD-44** | Delivery outcome semantics across the **two levels** — Communication lifecycle state and Delivery Attempt outcome | Concierge, Foundation | Delivery outcome semantics |
| **OD-45** | Acknowledgement semantics — receipt, acknowledger identification, and whether unacknowledged delivery constitutes failure. **Ignoring a Home Assistant Repairs issue is not a person-attributed acknowledgement and must not be adopted as one** | Concierge, Operational Trust | Acknowledgement semantics |
| **OD-46** | Urgency classification **as an Operational Trust entitlement**, its relation to action-risk classification, and its mapping to non-portable platform ladders. **`IssueSeverity` is a developer-facing platform ladder and is not resident-facing Urgency** | Operational Trust | Urgency entitlement model |
| **OD-47** | Household Inbox — **resolved as a projection**. Residual question is projection scope and refresh semantics | Concierge | Inbox projection semantics |
| **OD-48** | Re-presentation preference for outstanding Communications, and its relation to the Follow-Me preference family | Continuity, Concierge | Re-presentation preference |
| **OD-49** | Communication retention floor and ceiling, with **content and metadata classified separately** — formerly subordinate to **OD-33**, which has closed. **DL-47 settles the rule: Communication records follow the governed-record retention model with content and metadata classified separately. What remains is that separate classification itself, and the values** | Operational Trust, All | Communication retention |
| **OD-50** | **Resolved**: there is one escalation architecture. The residual question is the ladder itself, which is **OD-22** | Stewardship, Operational Trust | Resolved into OD-22 |
| **OD-51** | Interruption governance — **resolved** as an Operational Trust action-risk class. Residual question is risk-class enumeration and defaults. **Widened by DL-36 and DL-37: each risk class now carries both a required identity confidence and a required confirmation strength**, so the enumeration settled here is a direct input to the **Required Identity Band** accepted as **DL-39** and the **Required Confirmation Strength** accepted as **DL-40** | Operational Trust | Interruption risk classes |
| **OD-52** | Audience specification model, and how *anyone present with authority* resolves. **`HassBroadcast` and `assist_satellite.announce` target surfaces, never audiences, and neither is an audience model**. This is the **specification** of who a Communication is *for*; **audience composition** — who may *perceive* a delivery — is accepted as **DL-34**, and the policy applied when composition is uncertain is **OD-71** | Operational Trust, Concierge | Audience specification |
| **OD-53** | Communication category enumeration, and confirmation of the Category × Urgency separation | Foundation, Operational Trust | Communication taxonomy |
| **OD-54** | Delivery retry policy — attempts, intervals, surface progression, and give-up semantics. **Explicitly not escalation** | Concierge | Delivery retry policy |
| **OD-55** | Presentation attestation — which surface classes can attest `Presented`, how `unknown` is represented, and how it is prevented from decaying into *not presented* | Foundation, Concierge | Presentation attestation |
| **OD-56** | Safety-category scope — whether HTBW may originate safety-category Communications at all, given the life-safety non-claim | Operational Trust, Stewardship | Safety-category scope |
| **OD-57** | Indication versus content separation — when content-free indication becomes mandatory degradation. Content-free indication is the accepted degradation path when audience composition is uncertain (**DL-34**, **OD-71**) | Operational Trust, Concierge | Indication and content separation |
| **OD-58** | Terminology supersession scope — whether *Notification* and *Message* are formally superseded in the **DL-12** sense | Foundation | Terminology supersession |
| **OD-59** | Relationship between HTBW **Exposure** and Home Assistant **Assist entity exposure** — how HTBW narrows native exposure, how a divergence is surfaced as a configuration condition, and how the two are presented without conflation | Foundation, Room Configuration, Operational Trust | Exposure precedence |
| **OD-60** | **Repairs adoption scope** — which HTBW configuration defects and administrator-correctable conditions become Repairs issues, which are fixable through a repair flow, how `severity` is chosen, and how the ignore lifecycle is reconciled with HTBW defect state. **Repairs must not become an obligation store, a Communication surface, or an acknowledgement mechanism** | Foundation, Concierge | Repairs adoption scope |
| **OD-61** | **Area environmental entity consumption** — whether a natively assigned Area `temperature_entity_id` or `humidity_entity_id` is an automatic composite-fact input, a default proposal, or evidence requiring explicit participation. Related: **OD-17**, **OD-19** | Truth, Room Configuration | Area environmental entity consumption |
| **OD-62** | **Governed retrieval through Conversation** — which explainability and historical questions are answerable through Assist, how custom sentences and custom intents are defined, how authority and privacy filtering is applied before an answer is produced, and how an unanswerable question is reported honestly. **Conversation owns nothing.** This is the *retrieval surface*; provider choice is **OD-67** and is not required to close it | Concierge, Operational Trust | Governed conversational retrieval |
| **OD-63** | **Behaviour attribution** — the *semantic* model: the enumeration of behaviour sources, the evidence required to assert each, the confidence representation, and how *unattributed* is represented so that it never decays into a guess. **Person attribution remains bounded by Identity and creates no identification of its own.** **DL-38 sharpens the boundary: a behaviour source is not an identity evidence source.** Attribution consumes a completed Identity Assertion by reference and **never enters the Identity Fusion Function, never nominates a candidate, and never re-weights identity evidence**. Which platform evidence is captured is **OD-64**; declaration of an external decision-maker is **OD-66** | Foundation, Concierge, Truth | Behaviour attribution |
| **OD-64** | **Native automation, script, scene, and blueprint awareness** — the *evidence* question: which platform-supplied execution evidence HTBW references, how it is anchored, and its retention. **HTBW must not require the household to rewrite existing automations.** **Native execution evidence is not identity evidence (DL-38)**: an automation, script, scene, or blueprint execution record is evidence about *what changed a device*, and it is never admitted to the Identity Fusion Function nor used to nominate a candidate Person. How that evidence is interpreted as a behaviour source is **OD-63** | Foundation, Concierge | Native behaviour observation |
| **OD-65** | **Learning evidence eligibility** — which observations may contribute to a learned suggestion and which are excluded; how a resident's manual adjustment is distinguished from an automation-generated value; how competing residents' observations are handled; and how room-scoped and person-scoped learning are separated. Attribution itself is **OD-63**; lifecycle and revocation are **OD-28**. **An Unknown Person's interactions are never eligible evidence for person-scoped learning (DL-33)**. **Presentation is not personalization (DL-36): naming a candidate, or meeting the Identity Presentation Threshold, creates no learning eligibility of any kind**, and a denied or unclear confirmation never trains a profile or alters an evidence weight (**DL-37**). **A learned proposal may target a Fusion Policy value — reliability, correlation, freshness, contradiction, candidate comparison, normalisation, or band mapping — but never applies silently, and never recalculates an earlier assertion (DL-38)** | Continuity, Identity, Operational Trust | Learning evidence eligibility |
| **OD-66** | **Delegated external adaptive behaviour** — how an autonomous third-party policy engine is declared, bounded, observed, and disclosed, and how the reduced explainability of delegated behaviour is stated honestly to residents. **Execution by an integration does not by itself constitute delegation** | Operational Trust, Concierge | Delegation boundary |
| **OD-67** | **Reasoning Provider Strategy** — which classes of provider HTBW may use, for which purposes, under which governance. **No provider is selected here, and no provider abstraction is designed or presumed here.** Closure of **OD-62** does not depend on it. **Unknown Person access defaults to household-neutral context (DL-33)**, and household-private context is not authorised merely because a request originated inside the home. **Under DL-41 a reasoning provider is a declared capability dependency: where none is configured, valid, and available, the dependent capability is unavailable and says so, and no local approximation stands in for it. Which classes of provider are permissible remains open** | Concierge, Operational Trust, All | Reasoning provider strategy |
| **OD-68** | **Managed classification projection** — the reserved label taxonomy for Asset Type and any comparable classification: naming, stable identification, idempotent seeding, detection of existing labels, collision handling, taxonomy versioning, additions on upgrade, retirement, preservation of resident-created labels, and reconciliation reporting. **The architectural requirement is settled by DL-31; only the mechanism is open**, because no integration-facing label-management documentation could be verified. Closure must preserve: Asset Type stays authoritative in HTBW, labels stay derived, resident labels are never removed or overwritten, and a projection failure never changes a classification | Foundation, Stewardship | Managed label projection mechanism |
| **OD-69** | **Asset-derived Entity projection** — which Asset-related values are published as Entities, on which entity platform, with which state vocabulary, and how each refers back to its Asset. **HTBW defines no "asset health" state model**, and none may be invented to close this; the candidate vocabularies are the Stewardship obligation states and Truth's evaluation of current conditions. Closure must preserve: the determining responsibility keeps the determination, the Entity remains a projection and never a second authority, and the value stays explainable to its inputs. Does not depend on **OD-01**'s residual | Foundation, Stewardship, Truth | Asset state projection |
| **OD-70** | **Merged Room native projection** — whether a Merged Room warrants any native Home Assistant representation, or remains a purely HTBW semantic construct referencing its constituent Areas. **No native construct is invented to force an answer.** Closure must preserve: the Merged Room stays HTBW-owned, constituent Area definitions are never copied, and any projection remains a projection | Foundation, Room Configuration | Merged Room representation |
| **OD-71** | **Audience-uncertainty disclosure policy** — what Operational Trust does when audience composition is unknown, when audience detection is unavailable, or when plurality is unresolved: whether to confirm with the requestor, degrade to a content-free indication, redirect to an authorized private surface, or refuse; how the choice varies by content classification, Room, and mode; and how a household configures it. **Audience composition itself is accepted as DL-34 and is not reopened here.** **DL-37 adds one case: a confirmation challenge is itself a Communication**, so a challenge that names a candidate aloud is an audience-evaluated disclosure, and the neutral-challenge and private-redirect options are governed by this decision. The audience *specification* model remains **OD-52**; surface perceptibility remains **OD-43**; the indication-versus-content boundary remains **OD-57** | Operational Trust, Concierge | Audience-uncertainty disclosure policy |
| **OD-72** | **Unknown Actor correlation confidence** — how the evaluated correlation factors combine into a hypothesis confidence or quality band, and how that band is named and calibrated. **The correlation requirements are accepted as DL-35, and no mathematics is invented to close this.** Distinct from **OD-16**, which concerned identifying a *known* Person from identity evidence; this concerns grouping observations without identifying anyone. **OD-16's resolution as DL-38 does not close this decision and must not be borrowed to close it.** The Identity Fusion Function answers a purpose-specific *current* identity question against a bounded candidate set of known Persons; unknown-actor correlation groups *historical* observations into hypotheses while **identifying nobody**, and it has no candidate set, no Person-to-source associations, and no known-candidate separation. Shared primitives — freshness, observation quality, evidence families, contradiction — **may be referenced, but the function is not reused**. Access to the resulting reconstructions is **OD-35**; whether an Incident becomes a persisted object is **OD-41** | Concierge, Truth, Operational Trust | Actor correlation confidence |
| **OD-73** | **Interaction-Surface Room Context Resolution** — how **Room Context** is resolved when an interaction originates from a surface that is **not bound to a Room**: a phone, a wearable, a Companion App action, a browser session, or any other portable or mobile surface. **The constitutional concern is ownership and direction, not convenience.** Room Context is owned by **Foundation / Room Configuration**, whose accepted resolution order begins at *voice assistant identity* and whose failure behaviour states *"Never infer from device naming"*; yet [../models/glossary.md](../models/glossary.md) already asserts that Room Context may be established *"by a UI surface"*, and [../models/room-configuration.md](../models/room-configuration.md) already claims to provide *"Resolved Room Context for a given voice assistant **or surface**"* — **neither of which is defined**. The obvious input is illegal for the owner: deriving Room Context from a device's current location would require **Foundation to consume a Truth Fact at runtime**, contradicting [../architecture/dependency-view.md](../architecture/dependency-view.md) rule 6 — *"Foundation feeds everything and consumes nothing"* — and a naïve remedy risks the cycle **Room Context → Truth facts for that Room → Identity Room Presence → Room Context**, which the graph prohibits. **The native evidence is documented as insufficient**: device tracker granularity is verified as the **zone, never a Room or Area**, a connection tracker's zone is a documented **assumption**, and no native Room-level or Area-level BLE proximity capability has been verified, so under **DL-30** the burden of proof is **not discharged**. **This is also an explainability defect**: a Decision Trace must record Room Context and how it was resolved, and `room_context.resolved_from` currently has **no legal value** for this path, making the trace incomplete by its own definition. **Alternatives to evaluate, none preferred here: (A)** refuse — a non-room-bound surface never establishes Room Context, and the request is stated at Home scope or the resident is asked; **(B)** explicit household-configured surface-to-Room binding, exactly as for a voice assistant; **(C)** Room Configuration supplies the candidate Room set and its rules while **Concierge** consumes the Truth device-location Fact and selects, recording the selection in the trace; **(D)** Truth publishes an Engagement Fact carrying Room scope which Room Configuration consumes — **which violates dependency rule 6 unless that rule is amended by an accepted ADR**; **(E)** Room Context becomes multi-valued — *resolved*, *provisional*, *unresolved* — with provisional Room Context permitted only for capability classes Operational Trust marks tolerant; **(F)** interaction-surface Room Context is a Foundation-declared function over a Truth Fact **reference**, evaluated on request rather than by Foundation itself. **Closure must preserve**: a single named owner; a demonstrably **acyclic** dependency graph with the reasoning recorded; dependency rule 6 either preserved or amended by ADR and **never silently contradicted**; an enumerated `resolved_from` vocabulary sufficient for every trace to state honestly how Room Context was resolved; governed behaviour for unresolved context, unknown device Room, a device outside the Home, an unconfigured Room, a **constituent Room of a Merged Room** (**DL-13**: no transfer, no context change), and two equally supported candidate Rooms; the rule that Room Context resolution **never produces, alters, or substitutes for an Identity Assertion**; and **DL-30** discharged or the Room-granularity claim explicitly reduced. **Creates no responsibility, no second Room registry, and no second device tracker.** Related: **OD-11**, **OD-15**, **OD-51**, **OD-61**, **OD-63**, **OD-74**. **Must not be closed on assumed Home Assistant behaviour, on an unverified Companion App capability, or on implementation convenience in a reference integration** | Foundation, Room Configuration, Truth, Concierge | Interaction-surface Room Context resolution |
| **OD-74** | **Truth Fact Confidence Representation** — how **Truth Fact confidence** is represented, as a band, a numeric, or both, across every Fact class and every Fact Subject: Home, Room, Merged Room, Person, Pet, Asset, and Device. **Every Fact is required to carry Confidence** — [../models/truth.md](../models/truth.md) and [../contracts/truth-contract.md](../contracts/truth-contract.md) both state that *"a statement whose confidence, provenance, or freshness cannot be given is not published as a fact"* — **and no enumeration has ever been accepted.** `confidence: high` is used informally in the Truth model and in the Decision Trace machine form without definition or ordering, and the **superseded** [../models/occupancy-presence-model.md](../models/occupancy-presence-model.md) used a numeric `0.92`, which is exactly the numeric-as-canonical-confidence pattern **DL-39** now prohibits for Identity with no equivalent rule yet stated for Truth. **The DL-39 bands cannot be borrowed**: they are defined as describing *"only the strength of support for a **known-Person Identity Assertion**"*, so a Pet-location, Asset-location, Device-location, or environmental Fact cannot carry one. **No existing decision covers this**: **OD-17** is the composite-fact *aggregation algorithm*, **OD-18** is *validity*, **OD-19** is *conflict resolution*. **Alternatives to evaluate, none preferred here: (A)** reuse the household labels *Low / Moderate / High / Very High* as a **separate, independently owned Truth enumeration**, accepting a high conflation risk that must be neutralised by an explicit separation statement; **(B)** a distinct Truth vocabulary carrying no Identity resonance; **(C)** band plus optional normalised numeric, mirroring the **DL-38** handoff — band authoritative, numeric a deterministic ordering value only, **never a probability and never presented as accuracy**; **(D)** per-Fact-class enumerations; **(E)** coverage-derived confidence for Composite Facts with bands elsewhere, which couples this decision to **OD-17**. **Closure must preserve**: the band as the canonical public and policy-facing form, with percentages **not** exposed as canonical public confidence unless accepted architecture explicitly requires them; **`None` is never a Truth confidence value** — it is an Operational Trust **Required Identity Band** value (**DL-39**); Truth confidence is **never an Identity band and never an authorisation**, since sufficiency remains Operational Trust's (**DL-36**); `unknown`, `unresolved`, `stale`, and `withdrawn` remain **first-class states, not low bands**, mirroring **DL-39**'s *state and band are different dimensions*; authoritative ordering that resists being added, averaged, or treated as a distance; and demonstrated applicability to a Contextual Person-Presence Fact, a Pet Location Fact, a Device Location Fact, and an environmental Composite Fact. **No mathematics is invented to close this**, and **the Identity Fusion Function is not reused** — the same prohibition **OD-72** already applies to unknown-actor correlation applies here. Related: **OD-17**, **OD-18**, **OD-19**, **OD-61**, **OD-73** | Truth | Truth Fact confidence representation |
| **OD-75** | **Resolved as DL-48 and DL-49.** Obligation **condition** and obligation **lifecycle** are now orthogonal; deferral and closure are lifecycle transitions carried by **Change Records**; the **Care Evidence Record** defines what closes an obligation and distinguishes *satisfied without action* from *performed*; and custody is resolved as a Stewardship-owned **Custody Period**. **Formal acceptance review completed 2026-08-20 with a result of PASS, and issue #105 is closed as the completed governance record for OD-75.** The original question is retained for the record: **Obligation lifecycle completeness** — how a care obligation is **deferred**, **closed**, **reopened**, **grouped**, and what constitutes **accepted evidence that care occurred**. **This is a defect, not merely a gap.** [../models/stewardship.md](../models/stewardship.md) enumerates the obligation states as `met`, `due`, `unmet`, `overdue`, `waived`, and `unknown`, and in the same document describes obligation history as *raised, met, unmet, escalated, deferred, closed* — naming two lifecycle outcomes that **are not states**. The same document already establishes that **completion is not proof of fulfilment**, that marking a projected `todo` item complete is a list state rather than evidence of care, and that **absence of evidence is never compliance** — which together make *what does count as evidence* a question the architecture asks and does not answer. **Bounded by what is already accepted and not reopened here**: an obligation is never closed by a dismissed reminder, a ticked projection, a requested action, or an executor reporting success, because the projection does not own the obligation and an action is not an outcome; `unknown` is never `met`; a repeatedly unmet obligation makes the **pattern itself reportable**; and Stewardship observes closure from **Truth**, not from having asked for something. **Alternatives to evaluate, none preferred here: (A)** extend the state set with `deferred` and `closed` and define the transitions; **(B)** keep the six states and model deferral and closure as **Change Records** over an unchanged state, so history carries the lifecycle and the state stays a condition; **(C)** separate *condition state* from *lifecycle state* as two orthogonal fields; **(D)** define an Evidence-of-Care record class with its own retention under **DL-47**. Grouping of simultaneous obligations, and whether a *satisfied without action* obligation is distinguishable from a *performed* one, are part of this decision. **No new responsibility, store, or history owner may be created to close it**, and significance representation remains **OD-21**, escalation semantics remain **OD-22**, and projection surface remains **OD-23** | Stewardship, Concierge, Operational Trust | **Closed — DL-48, DL-49** |
| **OD-76** | **Person Stewardship authority** — whether a **care obligation may be declared for one Person by another**, and how consent, delegated authority, disclosure, retention, and withdrawal are represented when it is. **The gap is specific and verified**: the accepted `caretaker-of` relationship type carries accountability for an **obligation or an Asset**, and this repository defines **no caregiver relationship, no delegated care authority, and no mechanism by which one Person's declaration creates a care obligation whose subject is another Person**. **Every Stewardship use case involving a supported adult depends on it**, and the architecture currently supports only the case where the subject declares her own care. **Bounded by what is already accepted and not reopened here**: **people are not Assets** and a care profile never makes a Person property; **participation is optional and consent-gated**, and withdrawn consent makes evidence **ineligible before weighting** rather than down-weighted; a dependent capability whose consent is absent is **unavailable and names the missing dependency**; **disclosure is evaluated against audience composition**, so care content is audience-evaluated before it is conveyed; **no medical diagnosis, clinical advice, wellness score, or health inference is produced**; **HTBW is not a life-safety system**; and consent-lifecycle records are a **structural retention floor**. **Alternatives to evaluate, none preferred here: (A)** refuse — only the subject may declare care for herself, and third-party care management is out of scope; **(B)** a consent-scoped delegation in which the subject grants a named Person a bounded authority to declare, view, or receive specific care classes, revocable by the subject at any time; **(C)** a household-role approach in which an existing Role carries the authority, accepting that a Role is not consent; **(D)** a per-obligation-class grant separating *declare*, *view*, *receive*, and *close*. **The capacity question — a subject who cannot consent — must be addressed explicitly or explicitly excluded**, and must not be resolved by silence. **No new responsibility may be created to hold this**: Identity keeps consent lifecycle, Foundation keeps the relationship type, Operational Trust keeps disclosure and every threshold, and Stewardship keeps the obligation. Consent user experience remains **OD-06** and safety-category scope remains **OD-56** | Stewardship, Identity, Operational Trust, Foundation | Person Stewardship and delegated care authority |

| **OD-77** | **Person-to-external-resource association ownership** — which responsibility owns the governed association between a **Person** and an **external service, account, calendar, mailbox, media profile, audiobook account, or reasoning-provider profile**, and how that association is created, referenced, disclosed, reassigned, revoked, detected as stale, and deleted. **The gap is specific and verified.** [../models/person-and-identity.md](../models/person-and-identity.md) lists *Mailbox, calendar, and other external-service references* in the Person-extension table and assigns them to *the responsibility that governs their use* — **naming no responsibility** — while [../contracts/foundation-contract.md](../contracts/foundation-contract.md) declares the relationship types as **caretaker-of, owner-of, serves-room, and located-in**, **none of which expresses that an account belongs to a Person**. Continuity's ownership list does not contain it. **Every personal-resource outcome depends on it**: whose calendar is read for *what is on my calendar*, whose mailbox is summarised, whose audiobook progress is resumed, and whose media profile shapes a suggestion. **Bounded by what is already accepted and not reopened here**: the underlying provider configuration is **never copied** and HTBW owns **no calendar contents, mailbox contents, provider credentials, or tokens** (**P21**, **P22**, **DL-46**); connected storage **never becomes a shadow system of record** for something Home Assistant already owns authoritatively; an **Unknown Person references no Person, inherits nothing, and grants nothing** (**DL-33**); *who may access calendars, messages, email, or history* remains **Operational Trust's**; a dangling reference is **reported, never silently rendered as though the source record never existed** (**P30**); and a missing or invalid association makes the dependent capability **unavailable and names the missing dependency** (**DL-41**). **Alternatives to evaluate, none preferred here: (A)** a Foundation relationship type, consistent with `caretaker-of` and `owner-of`, since Foundation already owns relationships and consumes nothing; **(B)** an Identity-owned association, on the argument that it resembles the Person-to-evidence-source association of **DL-32**, accepting the risk of conflating *who is this* with *what is theirs*; **(C)** a Continuity-held reference, accepting that Continuity would then hold something it currently does not, and that **DL-46** still forbids copying its content; **(D)** an Operational-Trust-held entitlement with no separate association object, accepting that a permission is not an identity of a resource; **(E)** a Concierge-held consumption binding, **which would move governance into Concierge and is recorded here only so that it can be rejected explicitly**. Whether the household authors the association, or it is derived from a provider integration's own account binding, is part of this decision. **No new responsibility is created by this decision**, and revocation, participant removal, reassignment, stale-association detection, and deletion must be answered together with erasure mechanics (**OD-09**) and the consent experience (**OD-06**) | Foundation, Identity, Continuity, Operational Trust, Concierge | Person-to-external-resource association |
| **OD-78** | **Remembered-value classes and restoration semantics** — which class of remembered value a restoration draws from, and whether restoration **reproduces a prior value** or **computes a currently appropriate one**. **This is a defect, not merely a gap.** [../models/continuity.md](../models/continuity.md) claims *last lamp levels, last speaker volume* and *last song played in the room* as Continuity-held, and [../architecture/framework.md](../architecture/framework.md) repeats the room-scoped list, **yet the only restoration mechanics stated anywhere are in the subordinate** [../patterns/execution-patterns.md](../patterns/execution-patterns.md), which requires restoration to *use stored state*, forbids *guessing previous values* and *reconstructing state from history*, and sources restored state from a *runtime state snapshot or cache* — **a mechanism no canonical model, contract, or ADR names**. The classes a household actually distinguishes — **last observed value, last successful value, last person-selected value, configured default, person preference, room preference, experience preference, and restored state** — are **nowhere enumerated**, so *last lamp level* is ambiguous between at least four of them. **There is also an unresolved tension with DL-46**, which makes Home Assistant authoritative for entity and device states and requires HTBW to persist **no second copy merely to explain later**: a Continuity-held *last lamp level* is either governed meaning Home Assistant does not represent, or a second copy of native state, and **the repository does not say which**. **Bounded by what is already accepted and not reopened here**: a remembered value is **never a Fact** and is never presented as one; an unaccepted pattern **never becomes a preference** (**P26**, **DL-21**); a missing preference is **stated, never replaced by a silent platform default**; the household's own scenes, scripts, and automations are **not rewritten, wrapped, or migrated**; and current Truth, Room mode, Identity confidence, Operational Trust, audience composition, and safety remain **preconditions to applying any remembered value, never overridden by it**. **Alternatives to evaluate, none preferred here: (A)** reproduce the stored value only, treating restoration as replay and refusing where the stored value is invalid under current conditions; **(B)** compute a currently appropriate value from the remembered value plus current Truth, accepting that the result is a derivation and must be explainable as one; **(C)** name the value classes explicitly and let the household configure which class each capability restores from; **(D)** confine restoration to Session resume and remove environmental-state restoration from Continuity entirely, leaving it to native Home Assistant scenes; **(E)** treat the runtime restoration cache as a Home Assistant concern under **P21** and hold only the approved preference in Continuity. **Whether a prior or preferred room temperature is a Continuity-held value at all is part of this decision**, since no canonical document currently states that it is. **No new responsibility, store, or history owner is created by this decision** | Continuity, Truth, Operational Trust, Concierge | Remembered-value classes and restoration semantics |

| **OD-79** | **Presentation preference scope and precedence** — at which scopes a **presentation preference** may exist, which responsibility owns each scope, and **what takes precedence when two scopes disagree**. **This is a defect, not merely a gap.** [../models/continuity.md](../models/continuity.md) and [../contracts/continuity-contract.md](../contracts/continuity-contract.md) enumerate exactly two scopes, and **neither tier contains voice, language, persona, verbosity, explanation depth, or delivery modality** — yet **TTS volume is room-scoped**, placing the adjacent concern inside Continuity's room tier while leaving the voice that speaks at that volume ungoverned. **Person scope is settled**: [../scenarios/stewardship-use-cases.md](../scenarios/stewardship-use-cases.md) and [../models/communication.md](../models/communication.md) both attribute preferred delivery and preferred presentation to **Continuity**. **Room scope has no owner**, and two candidates exist that the repository chooses between nowhere — **Continuity**, as a room-scoped experience setting consistent with TTS volume, or **Foundation / Room Configuration**, as part of the Room's interaction definition, which already owns which voice assistants participate in a Room. The only document naming the concept, [../contracts/concierge-scope-contract.md](../contracts/concierge-scope-contract.md) — *room persona and voice overrides* — is **Historical and superseded**. **There is also no precedence rule, and the conflict is concrete**: a Room may carry a persona, a voice, and a language while a Person carries an interaction style, and nothing states what happens when a concise-preferring resident asks a question in a Room configured with an expansive persona. **OD-04 does not cover it**, because that decision governs *policy* precedence and the glossary is explicit that a Preference *is not a fact and not a policy*. The dimensions themselves are enumerated only in [../models/person-profile-model.md](../models/person-profile-model.md) and [../contracts/service-contracts.md](../contracts/service-contracts.md), **both Historical and neither authority**. **Bounded by what is already accepted and not reopened here**: a preference influences presentation only and **never alters a Fact, a threshold, an authority outcome, or a conclusion**; applying a Person's preference is a **person-scoped capability access** evaluated by Operational Trust against the current Identity Assertion (**DL-36**); **presentation is not personalization**, and being addressed by name grants no preference application and no learning eligibility (**DL-36**, **OD-65**); an **Unknown Person owns no preferences and inherits nothing** (**DL-33**); guests must not receive residents' preferences; **audience governs disclosure regardless of presentation** (**DL-34**, **P32**), so a persona never widens what may be said; a reasoning provider **owns nothing** and its absence makes the dependent capability unavailable rather than approximated (**DL-41**); and the **person-scoped versus room-scoped split is preserved**. **Alternatives to evaluate, none preferred here: (A)** person scope only, with no Room persona, accepting the loss of a wanted capability; **(B)** Continuity holds both tiers with person overriding room where Identity suffices, requiring a stated fallback below threshold; **(C)** split ownership, with the Room's voice and language as Room Configuration and style, depth, and modality as Continuity at person scope, accepting a seam the household may feel; **(D)** three declared tiers of household, room, and person, accepting a scope tier the Continuity model deliberately does not have; **(E)** separate **character** from **accommodation**, treating persona and voice as decorative and room-scoped while verbosity, modality, language, and accessibility are person-borne and always win. **Whichever option is chosen, the decision must answer whether an accessibility or language need is a preference subject to precedence at all, or an entitlement that no Room setting may override.** **No new responsibility, model, store, or history owner is created by this decision**, and no third scope tier is introduced unless the decision explicitly accepts one | Continuity, Foundation, Operational Trust, Concierge | Presentation preference scope and precedence |

| **OD-80** | **Resolved as DL-50.** **Capability execution host** — the question was **where an HTBW capability may execute** when the Home Assistant integration process cannot host it, and how that host is declared, governed, and made explainable. **This is a defect, not merely a gap.** **DL-30**'s ordered burden runs native capability, then existing maintained integration, then HTBW extension governing existing capability, then new HTBW capability — and **every rung assumes execution inside the integration process**. [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) addresses add-ons **only** as third-party engines that decide and act, governed as a delegation boundary under **OD-66**; **an add-on as a host for HTBW's own capability is nowhere addressed**. **The failure is verified rather than hypothetical**: a speaker-embedding encoder declared as a manifest requirement had **no installable wheel on the target host** — no build for the interpreter version below one release line and no build for the platform libc above it, so **no released version satisfied the host at all** — and because Home Assistant's manifest `requirements` install is a **hard precondition for `async_setup_component`**, the resolution failure failed the **entire integration** before any of its own code ran, **regardless of how carefully that code had been written to degrade without the dependency**. The response was to move the encoder into an application running on the host device, **a topology this repository neither describes, permits, nor forbids**. **This is not OD-07**, which asks *where processing happens* in trust and residency terms; this asks **what process hosts it**, and a capability may be entirely local yet still unhostable in the integration process. **It is also not simply DL-41**, which governs a dependency that is absent — here the dependency is specified, correct, and **structurally uninstallable**, which may still resolve to permanent unavailability but should be decided deliberately rather than by omission. **Bounded by what is already accepted and not reopened here**: **P21** and the **DL-30** ordered burden stand and must be extended rather than bypassed; **DL-41** stands, so a capability whose host is unavailable is **unavailable and names why**, with **no approximation, substitution, or silent reduction**; **P25** keeps Home Assistant the first implementation environment and **not a constraint on the architecture**, so no answer may bind HTBW to one deployment topology; data residency remains **OD-07**; third-party engines that decide and act remain **OD-66**; and HTBW acquires **no host operating-system administration**, consistent with the existing storage boundary. **Alternatives to evaluate, none preferred here: (A)** refuse, leaving such a capability permanently unavailable and explained as such, accepting a large capability loss taken by omission; **(B)** a Home Assistant add-on as a governed execution host declared as a **DL-41** dependency, accepting that add-ons exist only on some installation types so availability becomes deployment-dependent; **(C)** a household-provided external service or device referenced like any other provider, accepting a widened trust surface that engages **OD-07** and consent; **(D)** a per-capability declared host named in the dependency declaration and in the Decision Trace, the most explainable and the most to specify; **(E)** native-only, bounding capability ambition to what the Home Assistant environment can already install. **One conformance rule should be recorded whichever option is chosen**: a hard manifest `requirements` entry is an **all-or-nothing gate for the entire integration**, so a dependency that is optional to a capability **must not be declared there**, or a degraded capability becomes a total setup failure. **No new responsibility is created by this decision**, and no add-on, container, runtime, model, or vendor is selected by it. **Resolved 2026-08-25 as DL-50** on the evidence that four independent open-source speaker-recognition projects for Home Assistant all execute their encoder outside the Home Assistant Core process, which is evidence at step 2 of the **DL-30** ordered burden. **Alternative (D) is the accepted rule and (B) is the reference deployment only**; **(C)** is not foreclosed and remains available as a declared host engaging **OD-07**; **(A)** and **(E)** are rejected. **The conformance rule is recorded verbatim in DL-50.** **What this closure does not do**: it resolves neither **OD-07** nor **OD-66**, it selects no add-on, container, runtime, model, or vendor, and it authorises no implementation. **Two residuals were separated rather than absorbed**: the product-portfolio question is **OD-82**, and voiceprint gallery structure under channel diversity is **OD-83** | All, Identity, Concierge, Operational Trust | **Closed — DL-50** |
| **OD-81** | **HTBW capability exposure and self-consumption** — **whether HTBW publishes its own capabilities as first-class Home Assistant services, events, entities, and addressable household objects that a resident may call from their own automations, scripts, blueprints, and dashboards**, and **whether HTBW's own components must consume those same public interfaces rather than private internal paths**. **The gap is directional and verified.** **DL-16**, **DL-30**, **DL-42**, **DL-44**, and **DL-46** all govern HTBW **consuming** Home Assistant; **nothing governs HTBW publishing to Home Assistant for household consumption**. [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) enumerates what Home Assistant may provide and what HTBW owns, and contains **no statement about a service HTBW registers, an event HTBW fires, an entity HTBW creates as a public surface, or a household automation consuming HTBW**. **DL-11 does not answer it**: Exposure there is the constitutional state of being perceptible to a resident and is explicitly **not Home Assistant Assist entity exposure**, so it governs narrowing, never publishing. **The direction is already anticipated but never generalised**: **DL-31**'s representation strategy states that where an HTBW concept benefits from native visibility, state, targeting, **or automation**, a native representation is created or used in preference to a parallel hierarchy **and that representation is a projection, never a second authority** — yet that is a rule about *representations of concepts*, and the three cases that instantiate it remain individually open as **OD-23**, **OD-69**, and **OD-70**, with no parent question asking whether a general public capability surface should exist at all. **The self-consumption half is a separate unresolved choice**: [../contracts/concierge-contract.md](../contracts/concierge-contract.md) already requires that all state changes occur **through the owning responsibility's governed interface**, but **no canonical document defines what a governed interface is**, and whether it must be the same surface a resident may call is undecided. **The evidence is implementation-verified**: three shipped products independently exposed roughly twenty-four services and twenty bus events, thirty-five services, and a services-only integration respectively, and households already automate against them, so the question is whether that becomes governed platform behaviour or remains accidental. **Closure must preserve**: a projection is never a second authority; **Operational Trust evaluates appropriateness before any effect regardless of who invoked it**, so a public surface is never an authority bypass; a **Decision Trace** is produced for every invocation including a resident-initiated one, which makes caller attribution a live concern under **OD-63** and **OD-64**; **DL-42**'s prohibition on a second Recorder cuts both ways, because Home Assistant's Recorder retains whatever HTBW publishes, making retention a **consequence** of publishing rather than a separate choice and engaging **DL-47** and **OD-05**; and disclosure governance binds, because an entity state is readable by every Home Assistant user with **no audience evaluation**, so publishing a Person, an identity state, or a confidence band as an entity is a disclosure surface under **DL-34** and **DL-39** and a numeric confidence value is disclosed only where policy governs it and the audience permits. **Two vocabularies are prohibited in advance**: **room health is not an HTBW term** and **HTBW defines no asset health state model**, so neither may be introduced as a published entity to close this. **This decision selects no service name, no entity platform, no event schema, and no catalog format**, and **preempts nothing** — **OD-23**, **OD-59**, **OD-62**, **OD-63**, **OD-64**, **OD-68**, **OD-69**, **OD-70**, and **OD-73** each retain their own question and may be decided before or after it | All, Foundation, Concierge, Operational Trust | HTBW capability exposure and self-consumption |
| **OD-82** | **HTBW product consolidation and retirement** — **whether the standalone Asset Intelligence, Voice Identity, and Concierge products are harvested into a unified HTBW product and retired, or continue as separate released products**, and what becomes of their released artifacts, namespaces, entity identifiers, storage, and installed households if they are. **This is a verified contradiction, not a gap.** [authority-order.md](authority-order.md) records as a **non-negotiable constraint binding regardless of rank** that *"Asset Intelligence, Voice Identity, and Concierge remain **separate released products** with their own lifecycles"*; **DL-08** states the same for Asset Intelligence and **DL-19** states the greenfield form of it for all three. **An execution premise dated 2026-08-25 asserts the opposite** — that the three are being harvested into and retired in favour of a unified HTBW project — and that assertion cannot be adopted by implementation, by an ADR, or by prose, because a non-negotiable constraint is changed only by a decision that names it. **What is already settled and is not reopened by raising this**: **DL-05** stands, so Identity is the responsibility and voice is one evidence source regardless of the outcome; **DL-19** stands, so no compatibility requirement flows upward from any of the three into HTBW Core whether they are retired or retained; **DL-07** stands, so Stewardship owns significance and care; and the ledger's existing consolidation language for Asset Intelligence is a **responsibility** statement and was never a **product** statement, which is precisely the distinction this decision must hold. **The two are genuinely separable and must not be collapsed**: a responsibility may be first-class inside HTBW while its released product continues, and a product may be retired while its responsibility is unchanged — **OD-20** already depends on that separation, because it asks whether HTBW Core consumes the standalone Asset Intelligence product as an optional evidence source, and that question is only meaningful while a separate product exists. **What must be answered whichever way it goes**: whether installed households are migrated, left in place, or told the product is unsupported; whether released entity identifiers, unique identifiers, and storage keys survive; whether **DL-31**'s prohibition on requiring a resident to maintain the same information twice is satisfied during any overlap period; whether **DL-41** capability dependencies naming a standalone product remain resolvable; and whether **DL-45** parent-removal cleanup is triggered by a product retirement, which it must not be, because retiring a product is not removing a household's governing parent objects. **Alternatives to evaluate, none preferred here: (A)** retain all three as separate released products, leaving the constraint unchanged and the premise rejected; **(B)** consolidate into one HTBW product and amend the constraint by an accepted decision that states the migration obligations explicitly; **(C)** consolidate the **responsibilities** while retaining the released products as thin compatibility surfaces for existing households; **(D)** retire selectively, product by product, each with its own migration record. **No implementation artifact, namespace, domain, or entity identifier is renamed by raising this**, consistent with the existing rule that implementation artifacts are not renamed to match architectural words | All | HTBW product consolidation and retirement |
| **OD-83** | **Voiceprint gallery structure under channel diversity** — **whether a Person holds one voiceprint gallery entry derived from samples across every capture channel, a derived profile per channel, or a hybrid**, and how a runtime comparison selects among them. **Separated from DL-50 deliberately, and it must not be settled by implementation choice.** **DL-50** accepts channel-aware enrollment, so a voiceprint **records where enrollment occurred** — microphone source, satellite source, room, capture distance, and audio characteristics. **Recording where enrollment occurred is not the same as deciding how the gallery is structured**, and conflating the two would decide this question silently the first time an implementation chose a storage shape. **The question is real rather than theoretical**: a voiceprint derived on a handset is not equally representative of audio captured by a distant room satellite, which is the failure mode channel-aware enrollment was adopted to address, and a single averaged profile and a set of per-channel profiles behave differently against the same runtime audio. **Bounded by what is already accepted and not reopened here**: **DL-38** stands, so whichever structure is chosen it yields **one contribution per correlation family** and never several confirmations from one person's several profiles — **F2** forbids that directly; **DL-32** stands, so reliability remains configured per Person-to-source association and a per-channel profile is never a second source; **DL-43** stands, so voiceprints are Identity-owned and retained while the profile is enabled and consent remains valid, and any per-channel multiplication inherits that rule rather than creating a new one; **OD-16** stands, so sample counts, quality thresholds, and separation margins remain Fusion Policy configuration and are **not** part of this question. **Alternatives to evaluate, none preferred here: (A)** one person-global gallery entry built from channel-diverse samples, simplest and weakest where channels differ sharply; **(B)** a derived profile per channel, strongest per-channel accuracy and the most lifecycle surface, requiring an explicit rule that they never count as independent confirmations; **(C)** a hybrid, a person-global entry with per-channel refinements consulted when the capture channel is known; **(D)** channel recorded as evidence quality only, with no structural effect, letting **DL-38**'s observation-quality stage carry it. **This decision creates no new record class and no new artifact class**, and whichever alternative is chosen, an incompatible or absent profile remains a **DL-41** capability outcome rather than an identity failure | Identity | Voiceprint gallery structure |
| **OD-84** | **Multi-speaker evidence and speaker plurality** — **whether a voice evidence record may report that more than one person spoke within one capture**, and how a consumer distinguishes that from uncertainty about a single speaker. **This is a defect, not merely a gap.** **DL-38 F8** yields `ambiguous` when the leading candidate fails the governed separation requirement, and **`ambiguous` means one speaker whose identity could not be separated between candidates** — yet **two people speaking produces the same observable shape**, several candidates scoring closely, **from the opposite cause**. Uncertainty and plurality are therefore **currently indistinguishable at the point where the distinction matters most**, and an implementation that reports plurality as `ambiguous` would be conforming to the letter of an accepted rule while asserting something false. **HTBW already represents plurality twice, and in neither place is it a speaker**: **DL-35** makes *one actor, several actors, and unresolved plurality* representable for an **Unknown Actor Reference** within a historical reconstruction, and [../models/communication.md](../models/communication.md) carries *Multiple known Persons* and *Unresolved plurality* as **audience composition** states — but **DL-34** states that audience composition *identifies nobody* and *is never a second identity fusion*, so it may not be borrowed, and **audience answers who could hear while this question asks who spoke**, which **DL-34** itself separates by naming Requestor, Speaker, Present Person, Potential Listener, Authorized Recipient, and Delivery Target as six distinct roles that are never collapsed. **Bounded by what is already accepted and not reopened here**: **DL-38** stands entire and no fusion rule is amended, so whatever is decided must not turn a second speaker into a second confirmation of the first — **F2** forbids that directly; **DL-33** stands, so an unidentified second speaker is `unknown` with a supported human participant and never a synthetic Person; **DL-36** stands, so nothing here decides sufficiency for any purpose; **DL-34** stands, so a resolved second speaker is **not** thereby an audience determination and grants no disclosure; and **OD-16** stands, so no margin, count, or threshold is at issue. **Alternatives to evaluate, none preferred here: (A)** one capture yields exactly one speaker evidence record and additional voices remain **quality metadata**, the current position by default, simplest and silently lossy where a household genuinely has two people talking; **(B)** one capture may yield **several** evidence records, one per detected speaker region, each independently qualified, which is the most faithful and the most work for every consumer; **(C)** one evidence record carrying an explicit **plurality indicator** alongside its candidate list, distinguishing *uncertain* from *several* without multiplying records; **(D)** plurality treated as a **Truth** concern about the Room rather than an Identity concern about the capture, consistent with speech activity being a Room Fact. **Whichever is chosen, `ambiguous` must retain its accepted meaning**, and **no new responsibility, record class, or confidence representation may be created to carry plurality** | Identity, Truth, Operational Trust | Multi-speaker evidence and speaker plurality |

---

### Notes on the capability-exposure open decision

**OD-81 creates no capability, no surface, and no catalog.** It asks one previously unasked question:
whether HTBW **publishes** to Home Assistant, having only ever governed how it **consumes** from it.
Every accepted decision on the boundary — **DL-16**, **DL-30**, **DL-42**, **DL-44**, **DL-46** —
runs in the consuming direction, and the boundary document names what Home Assistant may provide and
what HTBW owns without once naming a service HTBW registers, an event HTBW fires, or an entity HTBW
creates for a resident to automate against. **DL-11's Exposure is not this question**: it is the
constitutional state of being perceptible to a resident, and it explicitly is not Home Assistant
Assist entity exposure, so it governs narrowing and never publishing.

**The question is raised as a parent, not as a replacement.** **DL-31** already anticipates the
direction for representations — where an HTBW concept benefits from native visibility, state,
targeting, or automation, a native representation is preferred to a parallel hierarchy and remains a
projection rather than a second authority — and three decisions already instantiate it for one case
each: obligations under **OD-23**, Asset-derived values under **OD-69**, and Merged Rooms under
**OD-70**. **None of those asks whether a general public capability surface should exist**, and none
addresses services, events, or self-consumption at all. OD-81 therefore sits above them and
**preempts none of them**; each may be decided before or after it, and a decision there does not
decide the general question here.

**Two invariants are already settled and are not reopened by raising this.** A projection is never a
second authority, and **Operational Trust evaluates appropriateness before any effect regardless of
who invoked it** — a public surface is a way in, never an authority bypass, and a resident-initiated
invocation is subject to exactly the evaluation an interaction-initiated one is. What follows from
that is a live concern rather than a settled one: every invocation still produces a **Decision
Trace**, so **who invoked it** becomes attribution work already owned by **OD-63** and **OD-64**.

**Publishing has a retention consequence that is not a separate choice.** **DL-42** forbids a second
Recorder, and Home Assistant's Recorder retains whatever HTBW publishes as entity state. **A decision
to publish is therefore also a decision about what is retained**, engaging **DL-47** and **OD-05**,
and that consequence must be reasoned about rather than inherited.

**Disclosure binds hardest on the most attractive proposals.** An entity state is readable by every
Home Assistant user and carries **no audience evaluation**, so publishing a Person, an identity
state, or a confidence band as an entity is a disclosure surface under **DL-34** and **DL-39**, and
privacy governance already restricts a numeric confidence value to where policy governs it and the
audience permits. Convenient automation context and governed disclosure pull in opposite directions
here, and that tension is the substance of the decision rather than an obstacle to it.

**Two vocabularies are prohibited in advance so they cannot enter through a published entity.**
**Room health is not an HTBW term**, and **HTBW defines no asset health state model** — the latter
already stated in **OD-69**. Neither may be introduced as a sensor, an event, or a catalog heading.

**This note introduces no construct.** It defines **no service**, **no event schema**, **no entity
platform**, **no household object type**, **no catalog format**, and **no self-consumption rule**. It
**amends no accepted decision** and **reopens none**. The ledger moves to eighty-one identifiers,
nine closed, seventy-two open.

---

### Notes on the voice-evidence runtime review

**Recorded 2026-08-25. Updated the same day on acceptance.** The review produced
[../architecture/adr-wyoming-compatible-voice-evidence-runtime.md](../architecture/adr-wyoming-compatible-voice-evidence-runtime.md),
**accepted as DL-50**, which closes **OD-80** and raises **OD-82** and **OD-83**.

**Acceptance settles three things and authorises no fourth.** It settles **where a capability may
execute**, **what a voice provider returns**, and **what may never happen to a transcript**. It
authorises **no implementation** — the roadmap phases are separately tracked, speaker-conditioned
extraction remains validation-gated, and passive conversation-state evidence remains a North Star that
the ADR explicitly does not approve.

**The review was a comparative examination of four third-party speaker-recognition projects for Home
Assistant, the official Wyoming protocol, and the current reference implementation.** Its principal
finding is that **OD-80's verified failure has a verified ecosystem answer**: every one of the four
projects executes its neural encoder **outside the Home Assistant Core process**, and not one attempts
in-process execution. That is evidence at step 2 of the **DL-30** ordered burden, and it is why the
decision is a rule rather than a described workaround.

**Two protocol facts were verified and are recorded because their absence is load-bearing.** The
Wyoming protocol advertises the service types `asr`, `tts`, `wake`, `handle`, `intent`, `satellite`,
`mic`, and `snd`, and **defines no speaker, identification, verification, or biometric service type
and no speaker-evidence event**. It does define `user-event`, a user-defined event carrying `name`,
`data`, and `context`, and servers are documented to drop unrecognised events. **The gap is therefore
real and the sanctioned extension path already exists**, which is why the decision records the gap and
declines to invent a protocol extension.

**One correlation finding narrows nothing and closes nothing, but it must not be lost.** Wyoming does
**not** close the correlation gap. `info.satellite.area` carries an area **name**, and **DL-31**
requires reference by stable identifier, so a satellite area name never resolves a Room by itself. The
existing position stands unchanged: evidence is produced **unbound**, the consumer supplies
correlation context explicitly, and **temporal proximity alone never establishes correlation**, which
**DL-35** already states.

**Three boundary drifts were found in the reference implementation and are recorded as evidence, not
as decisions.** A provider-emitted confidence enumeration collapses **state** and **band** into one
value, which **DL-39** separates; a provider-side attribution record resolves a person, which **DL-06**
and **DL-32** assign to Identity; and a single default confidence constant contradicts **DL-36**'s
*sufficiency is never universal*. **None of these is a new open decision.** Each is a conformance
finding against an already-accepted decision, and each belongs to implementation remediation rather
than to architecture. The same implementation is **ahead of every project reviewed** on encoder
version pinning and on the correlation boundary, and that is recorded with equal weight.

**No decision about thresholds was taken, and none was needed.** **OD-16** already resolved that
separation margins, per-purpose minimums, freshness durations, and confidence thresholds are **Fusion
Policy configuration, versioned and governed, and none of them is an unresolved architectural
question**. The review observed that the same cosine metric produces an operating point near 0.30 in
one project and near 0.82 in another, which is a demonstration of that decision rather than a
challenge to it: **a provider match value is not portable across providers**, and **DL-32**'s rule that
it is *retained as reported and never rewritten as fused confidence* is what makes the four bands the
only cross-provider currency.

**Eight harvested patterns are accepted as implementation patterns, and one of them is a
classification rather than a capability.** Out-of-process runtime, Wyoming-compatible participation,
top-N candidate evidence, channel-aware enrollment, speech-region segmentation, rejection telemetry,
and provider abstraction are adopted where appropriate. **Passive conversation-state remains North
Star only.** **Each pattern is reimplemented as an HTBW-owned contract**; every source project is
MIT-licensed; **no third-party source code is taken**; and **no single-maintainer project becomes a
mandatory dependency**, which matters because every project reviewed has exactly one contributor.

**Two residuals were separated rather than absorbed, and both separations are load-bearing.**
**OD-82** is the product-portfolio question, kept out of the ADR because a non-negotiable constraint in
[authority-order.md](authority-order.md) is changed only by a decision that names it, and the ADR
holds whichever way it is decided. **OD-83** is voiceprint gallery structure, kept out because
**recording where enrollment occurred is not the same as deciding how the gallery is structured** —
and had they been merged, the second question would have been answered silently by the first
implementation that chose a storage shape.

**One terminology question was resolved without a decision, because naming is not architecture.**
**DL-05** supersedes *Voice Identity* as a platform-service boundary, and the responsibility is
**Identity**. The out-of-process runtime keeps its released artifact name; its **architectural role
name is Voice Evidence Provider Runtime**; it is a capability component and never a responsibility.
The existing rule that implementation artifacts are not renamed to match architectural words is
applied here exactly as it was applied to Asset Intelligence.

**One contradiction was found that the review had no authority to resolve, and it was raised rather
than absorbed.** The execution premise asserted that the three standalone products are being retired
into a unified HTBW product, and [authority-order.md](authority-order.md) records their separateness
as a **non-negotiable constraint binding regardless of rank**. That is **OD-82**, and **DL-50** holds
whichever way it is decided, because it governs the responsibility architecture and not the product
portfolio.

**This note introduces no construct.** It creates **no responsibility**, **no record class**, **no
artifact class**, **no retention rule**, **no threshold**, and **no confidence representation**. It
**amends no accepted decision other than by adding DL-50**, and **reopens none**. At acceptance the
ledger stood at eighty-three identifiers, ten closed, seventy-three open; the post-acceptance harvest
recorded below moves it to eighty-four, ten closed, seventy-four open.

---

### Notes on the Episode 8 Concierge narrative validation

**Recorded 2026-08-25. This review produced no decision, and the ledger is unchanged.** Twenty
Concierge human-outcome use cases were documented in
[../scenarios/concierge-use-cases.md](../scenarios/concierge-use-cases.md) and traced against accepted
architecture. **No open decision was created, no accepted decision was reopened, and no new
construct — responsibility, record class, artifact class, retention rule, threshold, or confidence
representation — was introduced.**

**The narrative is a stress test, never authority**, and the strongest evidence that the architecture
withstood it is arithmetic. **Fourteen of twenty-four Concierge facets are already accepted, no facet
is missing, and none requires a new construct. Eleven of twenty cross-cutting questions are answered
by accepted architecture, and every one of the nine that are open is an existing open decision.**

**No use case is classified as implemented, because HTBW Core contains no code.** That is stated
plainly in the catalogue rather than softened. Where a standalone released product implements
something resembling a use case, it is recorded as **product evidence** and never as HTBW
implementation, consistent with **DL-19**.

**Three responsibilities named in the Episode 8 material do not exist, and the catalogue corrects
them rather than accommodating them.** There is no **Experience Delivery** responsibility — delivery is
Concierge's and a Delivery Surface is a platform concern. There is no **Communication or Messaging**
responsibility — [authority-order.md](authority-order.md) forbids it as a non-negotiable constraint.
There is no **Intelligence** responsibility — whether a reasoning provider may be consulted at all is
**OD-67**, and a provider's output never silently becomes a Fact. **A compelling story is not
authority to add a responsibility.**

**Ten candidate principles were tested and none was elevated.** Seven are already accepted in
substance, and elevating a restatement would create two authorities for one rule — the defect the
authority order exists to prevent. Three are recorded inside the catalogue as **Concierge guidance,
explicitly subordinate to canon**: *information may come from many places, judgment belongs at home*;
*connectivity does not relocate responsibility*; and *Concierge recognises when assistance becomes
useful*. The first two were deliberately **not** elevated because doing so would preempt **OD-07** and
**OD-67**, and the second rests on platform facts this repository has not verified. **DL-50**'s
*providers produce evidence, HTBW produces decisions* was deliberately **not generalised** beyond
voice for the same reason.

**One apparent gap was tested and found already answered, which is worth recording because it looked
like a decision.** Unprompted assistance — the shopping list becoming useful at the shop, the vehicle
recommendation the evening before a long day — appeared to need an owner for *who decides that an
opportunity exists*. [../models/communication.md](../models/communication.md) already states that
**any responsibility may originate a Communication**, so the originator is whichever responsibility
owns the underlying matter, and the residual question is only **who owns the association between a
person and an external list or calendar**, which is **OD-77**. **No new decision was justified.**

**The review's most useful output is a sequencing signal rather than a finding.** Twelve of the
twenty use cases are blocked, and the blockers concentrate almost entirely in five existing decisions
— **OD-06**, **OD-77**, **OD-43**, **OD-84**, and **OD-52**. **Deciding those five would unblock ten
of the twelve.**

**This note introduces no construct**, amends no accepted decision, and reopens none. The ledger
remains at eighty-four identifiers, ten closed, seventy-four open.

---

### Notes on the post-acceptance voice-evidence architecture harvest

**Recorded 2026-08-25, after DL-50 was accepted.** Twenty patterns raised during the voice-evidence
research were tested against the accepted architecture to determine whether any remained trapped
outside the architecture-of-record. **Fifteen were already incorporated, four were partial and are
already tracked, and one was missing.** **The harvest amends no accepted decision, reopens none, and
creates no document.**

**The one missing pattern is OD-84, and it is a defect rather than an absence.** **DL-38 F8** yields
`ambiguous` when the leading candidate fails the governed separation requirement, and `ambiguous`
means **one speaker whose identity could not be separated between candidates**. **Two people speaking
produces the same observable shape from the opposite cause** — several candidates scoring closely —
so uncertainty and plurality are **currently indistinguishable at the point where the distinction
matters most**, and an implementation reporting plurality as `ambiguous` would conform to the letter
of an accepted rule while asserting something false. **HTBW already represents plurality twice and in
neither place is it a speaker**: **DL-35** for an Unknown Actor Reference in a historical
reconstruction, and [../models/communication.md](../models/communication.md) for **audience
composition**, which **DL-34** states *identifies nobody* and *is never a second identity fusion*.
**Audience answers who could hear; this question asks who spoke**, and **DL-34** itself keeps the six
roles distinct. The urgency is concrete rather than theoretical: **speech-region segmentation is the
mechanism that would surface a second speaker, and it is scheduled to ship into a model that has
nowhere to put the finding**.

**Two proposals were tested against the repository and deliberately answered no.** A separate
`voice-evidence-provider-contract.md` is **not** created, because
[../contracts/README.md](../contracts/README.md) defines a contract as *the explicit boundary of a
responsibility*, describing *obligations between responsibilities, not transport, schema, or platform
mechanics* — and **a provider is a component, not a responsibility**, so such a file would be a
category error and would fragment the boundary that
[../contracts/identity-contract.md](../contracts/identity-contract.md) already carries. A **provider
plug-in or registry framework** is likewise **not** created: **DL-41** already enumerates *a provider*
among its dependency classes, and building a registration framework would be a **new HTBW capability**
requiring the **DL-30** ordered burden to be discharged first, which nothing in the research
discharges.

**Four partial patterns were found, and none of them justified a new decision.** Channel-diversity
gallery strategy is **OD-83**, already open. **Provider optional-feature discovery** and
**provider-substitution migration** are **contract work**, folded into Phase 1 rather than raised as
questions — the first because Patterns 5, 6, and 8 are optional capabilities a provider may or may not
offer, and the second because section 16's model-upgrade rule already answers the substitution case
once it is stated as applying to a change of provider and not only of model. **Microphone governance**
is **already sufficient for the active path** — Room participation under **DL-11**, per-source consent
under **DL-32**, and purpose authority under **DL-36** together answer whether a microphone may
contribute evidence to a resident-initiated interaction — and is **insufficient only for the passive
path**, which is a North Star with microphone-governance policy already named among its prerequisites.
**A prerequisite that is already recorded is not a gap.**

**Two apparent gaps were tested and found to be settled positions rather than omissions.** **Enrollment
quality scoring** is deliberately not canonical: the enrollment-sufficiency note below already refuses
*no canonical threshold, sample count, duration, margin, or quality score*, and quality is expressed as
**gates**, not as a published score. **Audio-quality scoring** is likewise already held: **DL-38 F3**
names **observation quality** as a qualification stage that may only lower or hold, and
[../models/person-and-identity.md](../models/person-and-identity.md) already lists *quality summary*
among the safe metadata Identity may emit. Neither needed anything added.

**Conversation-active remains where DL-50 put it, and that placement is itself the finding.** The
distinction between **conversation active** and **conversation content** exists **only in the accepted
ADR** and appears in no canonical model. **That is correct and must not be repaired**: writing it into
[../models/truth.md](../models/truth.md) would grant canonical standing to a capability that is
explicitly a **North Star with no implementation authorised**, which is the failure mode the North Star
classification exists to prevent. The prohibitions that protect it — no transcript requirement, no
semantic requirement, no ambient recording, no conversation storage — are already carried by **DL-42**,
**DL-46**, and [../architecture/privacy.md](../architecture/privacy.md) independently of the ADR.

**No contradiction was found**, no responsibility boundary was moved, and the provider boundary remains
extensible: a future encoder, an alternate provider, an experimental provider, or a future
Wyoming-compatible provider is adopted under **DL-41** as a declared dependency and under **DL-50** as
a candidate-reporting provider, **without redesigning Identity**.

**This note introduces no construct.** It creates **no responsibility**, **no record class**, **no
artifact class**, **no retention rule**, **no threshold**, and **no confidence representation**. It
**amends no accepted decision** and **reopens none**. The ledger moves to eighty-four identifiers, ten
closed, seventy-four open.

---

### Notes on the custody and obligation-lifecycle decision

**Recorded 2026-08-20. DL-48 and DL-49 were accepted, and OD-75 is closed by them. Formal acceptance
review completed the same day with a result of PASS, and issue #105 is closed as the completed
governance record for OD-75.**

**The acceptance review confirmed the accepted outcomes rather than restating them**, and the ones it
named are held in canon: obligation condition and lifecycle are orthogonal; **`met` means satisfied to
date, not completed**; a Care Evidence Record provides governed closure by observation, attestation,
performance, or waiver; a **Custody Period** is Stewardship-owned and carries the lifecycle `opened`,
`updated`, `closed`, `corrected`, `adversely_resolved`; custody is separate from ownership,
caretaking, declared location, observed location, significance, and risk; a lost or stolen period ends
`adversely_resolved` with the **last known custodian preserved**; and recovery opens a **new** period
rather than rewriting the adverse one. The review also confirmed what was **not** done: no Asset
Intelligence schema was adopted, no ownership moved into Continuity or Concierge, **OD-77 was neither
expanded nor silently resolved**, no current physical location is inferred from custody, and **no
issue was closed solely because documentation changed**.

**Implementation remains separate** and is gated by the applicable persistence, retention,
preservation, relationship, document, and Home Assistant First decisions. **Issue #155 remains open**
as the Asset Intelligence legacy capability harvest register.

**The household outcome this had to serve**: preserve a complete, explainable custody chain for a
significant asset; know who is accountable and where it is expected to be; protect return commitments;
preserve condition and contractual evidence; and support insurance, provenance, conservation, and
eventual retirement — **without confusing custody with ownership, caretaking, declared location,
current location, risk, or environmental truth**.

**Three household requirements were challenged and corrected rather than adopted:**

| Proposed | Verdict | Accepted form |
|---|---|---|
| Custody states *Owned On Site*, *On Loan Out*, *In Transit*, *In Storage*, *Lost*, *Stolen* | **Rejected as a fixed enumeration** | **HTBW adopts no fixed custody-status enumeration as canonical**, though a Custody Period does carry a governed lifecycle. *In transit* and *in storage* are Custody Periods whose custodian is the carrier or storage provider; *owned on site* is **not a custody statement at all** and requires a Truth Location Fact or a declared `located-in`; *overdue*, *lost*, and *stolen* are not custody states |
| A *Counterparty* object | **Rejected** | The custodian designation is a **governed reference to an existing Foundation object, or free text preserved verbatim** with the actor who recorded it. No new object was demonstrated as necessary |
| A *custodian* Foundation relationship type | **Rejected** | `owner-of` and `caretaker-of` are **durable**; custody is **episodic**. Episodic accountability belongs on a time-bounded record. **OD-77 was neither expanded nor resolved** |

**One tension required care rather than a ruling either way.** The household requires that an open loan
stay open until Check-In is explicitly recorded, while the accepted rule is that *Stewardship observes
closure from Truth, not from having asked for something*. Both are honoured because they concern
different subjects: **Truth can establish where something is; it cannot establish that an
accountability period has been accounted for.** Physical return is therefore **evidence toward
closure**, and the Check-In is a **Care Evidence Record** of kind `attested`. **This is not a ticked
projection** — it is a household attestation of a real-world event, carrying the return date, the
condition, and its evidence.

**The custody findings decided the obligation half.** Asset Intelligence had independently built a
plain custody **state** alongside a loan **lifecycle** — which is alternative **(C)**, already working
in a neighbouring domain. Its `expected_return_date` versus `actual_return_date` pair is **completion
evidence by construction**, which is alternative **(D)**. **DL-48 therefore accepts (C) as the shape,
(B) as the mechanism, and (D) as what closes — and rejects (A)**, because putting *deferred* and
*closed* into the condition set is the precise category error this decision was raised on.

**Four boundaries were deliberately preserved:**

- **Continuity owns none of this.** Custody, care history, environmental history, insurance
  responsibility, and asset provenance are **not Continuity's** merely because they persist. Use Case 1
  of [../scenarios/stewardship-use-cases.md](../scenarios/stewardship-use-cases.md) records
  *Continuity interaction — None*, and it stands.
- **Concierge owns no obligation and no reminder policy.** Stewardship originates the Communication;
  Operational Trust governs entitlement, interruption, and audience; Concierge decides whether, when,
  and how. **Reminder lead time and cadence are household policy, not canonical constants.**
- **No dashboard colour became a Fact.** *Blue* and *purple* for within-period and beyond-expected-return
  are presentation candidates over an obligation condition state, and the projection surface remains
  **OD-23**.
- **No second risk authority was created.** When an asset is off site and household environmental
  evidence is unavailable, **Truth publishes no Fact it cannot support** and the dependent evaluation is
  **unavailable and says so** (**DL-41**) — never green, never red. Significance persists, custody
  persists, the return obligation persists, and the environmental conclusion does not.

**Corrections recorded at formal acceptance review, 2026-08-20.** The accepted direction was not
reopened; four statements were imprecise and are corrected here and in the canonical documents.

| Imprecise as first written | Corrected |
|---|---|
| *"The home knows the sculpture is at the DMA."* | **A custody record never establishes current physical location.** The architecture-faithful sentence is *"the custody record says the sculpture is in the museum's custody."* Current physical location requires a **Truth** Location Fact |
| *"Owned on site is the absence of an open Custody Period plus an `owner-of` relationship."* | **Withdrawn.** The absence of an open Custody Period means only that **no non-default custodian is currently recorded**. On-site status requires a Truth Location Fact or Foundation's declared `located-in`, and is **never inferred from ownership** |
| *"There is no custody state machine."* | **Imprecise.** A Custody Period **does** have a governed lifecycle — `opened`, `updated`, `closed`, `corrected`, `adversely_resolved`. What HTBW declines to adopt is the **legacy fixed custody-status enumeration** as canonical |
| *`met` used without definition* | **`met` means satisfied to date, not completed.** This is the meaning the model already carried — implicit in the filter, tuning, and preservation obligations — and it is now stated. **No new condition value was introduced**, and `met` is never asserted from absence |

**One field was decomposed** without creating an object: *insurance responsibility* is genuinely
several things — the **insurer** and **insured party**, which live on the policy artifact; the party
**responsible for maintaining coverage** and the party **accountable for a claim**, which are
period-scoped and live on the Custody Period; and the **governing agreement**, which is an Asset
document referenced without copying. Ownership and custody remain independent of all of them.

**No Asset Intelligence schema was adopted.** No object model, storage schema, event schema, state
enumeration, or field name was copied, and the legacy snapshot-comparison pattern is explicitly
excluded: **custody and obligation changes are semantic Change Records written at the moment of
change** (**DL-26**).

**These decisions preempt nothing else.** They decide no significance representation (**OD-21**), no
escalation ladder (**OD-22**), no obligation projection surface (**OD-23**), no acknowledgement
semantics (**OD-45**), no interruption risk classes (**OD-51**), no retry policy (**OD-54**), no
audience specification (**OD-52**), no delegated care authority (**OD-76**), no person-to-resource
association (**OD-77**), and no governed-record persistence shape (**OD-01**).

---

### Notes on the Episode 4 and Episode 5 narrative-validation clarifications

**Recorded 2026-08-17. No decision was created, closed, reopened, or amended by this work.**

Narrative development of **Season 1 Episode 4 (Identity)** and **Season 1 Episode 5 (Operational
Trust)** surfaced eleven points at which accepted architecture was **correct but under-stated** — true
by implication from **DL-32**, **DL-33**, **DL-34**, **DL-36**, **DL-37**, **DL-38**, **DL-39**,
**P15**, **P16**, **P26**, and **P32**, yet not written plainly enough to be implementable or
teachable. They were memorialized as **clarifications inside the existing Identity, Operational
Trust, privacy, and explainability documents**, not as ledger entries.

| Clarification | Already implied by | Where memorialized |
|---|---|---|
| Identity establishes confidence; Operational Trust evaluates **sufficiency for a specific request**, never generalized trustworthiness | **DL-36** | Operational Trust model and contract |
| Operational Trust **applies** household values; it does not **author** them | **DL-36**, **P26** | Operational Trust model and contract |
| **Participation is optional and requires consent**; voice identity evidence is available only for a consenting, enrolled participant | **DL-38** eligibility gate; privacy consent requirements | Identity model and contract, Operational Trust model and contract, privacy |
| **Consent → Available Evidence → Identity → Operational Trust** | **DL-32**, **DL-38** | Identity model and contract, Operational Trust model and contract, privacy |
| **Audience awareness is a first-class input**; identity confidence may be unchanged while the outcome varies | **DL-34**, **P32** | Operational Trust model and contract |
| **Disclosure is separate from knowledge** — *can the home know?* versus *should the home share?* | **DL-34**, **P32** | Operational Trust model and contract, privacy |
| Operational Trust **prefers explicit metadata and classifications** over content interpretation or sensitivity inference | **DL-34** (a reasoning provider is never the sensitivity classifier), **P15**, **P16** | Operational Trust model and contract, explainability |
| **Confidence requirements are configured per capability**; there is no universal threshold | **DL-36**, **DL-39**, **OD-51** | Operational Trust model and contract |
| **"Not now" is a valid outcome** — Allow, Require Confirmation, Defer, Redirect, Abstain, Deny | Existing authority and disclosure outcomes; **P16**, **DL-15** | Operational Trust model and contract |
| Operational Trust evaluates **eight inputs** before producing an outcome | Distributed across the above | Operational Trust model and contract |
| **Unknown is a valid identity outcome**; the home must not be more confident than the evidence supports | **DL-33**, **DL-38** rules **F1–F8** | Identity model and contract |

**Three boundaries were deliberately preserved rather than adjusted:**

- **The six outcome shapes are a household-facing reading, not a new enumeration.** The authoritative
  authority outcomes remain `permitted`, `prohibited`, `permitted_with_confirmation`,
  `permitted_with_escalation`, and `undecidable`; the disclosure outcomes remain as accepted under
  **DL-34**. **Operational Trust owns the constraint — *not at this moment*, *not on this surface* —
  and Concierge owns the expression of it.** *Defer* and *Redirect* remain Concierge outcomes and were
  **not** relocated.
- **No native privacy-marking capability is claimed.** The preference for explicit classification is
  stated at the architectural level; **which native fields carry such a marking remains subject to the
  ordered burden of proof in DL-30**, and no such field is asserted anywhere in this repository.
- **No new responsibility, model, threshold, or store was created**, and no ownership moved. Identity
  still fuses; Truth still owns Facts; Operational Trust still owns every threshold; Concierge still
  owns decisions and the Decision Trace; the household still owns its values.

**These clarifications preempt nothing.** They decide no risk-class enumeration (**OD-51**), no
assertion validity window (**OD-15**), no consent user experience (**OD-06**), no audience-uncertainty
policy (**OD-71**), no reasoning-provider strategy (**OD-67**), and no learning eligibility
(**OD-65**).

### Notes on the Episode 6 narrative-validation clarifications

**Recorded 2026-08-18. No decision was created, closed, reopened, or amended by this work, other than
the opening of OD-75 and OD-76 above.**

Narrative development of **Season 1 Episode 6 (Stewardship — *How Does a Home Know What Matters?*)**
was used as an **architecture stress test**, in the same manner as Episodes 4 and 5. The narrative is
**not** authoritative architecture and was not incorporated as such. It was used to find questions the
accepted architecture must answer.

**The proposed episode doctrine was validated and accepted as a human-facing summary**, with the
precise architectural wording recorded behind it:

| Proposed narrative statement | Verdict | Precise architectural wording |
|---|---|---|
| *The household determines what matters* | **Accepted** | The household **declares** what matters and defines the relevant care expectations, through registration, configuration, caretaker assignment, consent, policy, relationship records, care profiles, schedules, declared environmental requirements, or a default it **explicitly chose** |
| *Stewardship helps care for it* | **Accepted as the human-facing summary** | Stewardship **represents those care expectations, evaluates authoritative observations against them, and creates governed care obligations when attention is required** |
| *Stewardship often appears as automation* | **Accepted, with a boundary** | The **automation is the executor**. Stewardship states that an obligation is unmet; Operational Trust governs; Concierge decides; an executor acts |
| *Stewardship exists to support care* | **Accepted** | Consistent with **DL-07** |
| *Sometimes automation is used to take corrective action before anyone needs to be notified* | **Contradicted as written** | The corrective action is real and permitted; **attributing it to Stewardship is not**. Remediated narration is recorded below |
| *Operational Trust enforces what is appropriate* | **Rejected** | **Enforcement is execution.** The canonical wording is *Operational Trust determines what is appropriate for this request, in this context*, and it appears in this repository nowhere else |
| *Care results in action when attention is required* | **Superseded** | **Care creates an obligation when attention is required.** Whether an action follows is Operational Trust's, Concierge's, and the executor's |

**Seven points were found where accepted architecture was correct but under-stated** — true by
implication from **DL-07**, **DL-08**, **DL-19**, **DL-21**, **DL-25**, **DL-26**, **DL-31**,
**DL-36**, **DL-41**, **DL-42**, **DL-46**, **DL-47**, **P21**, **P26**, **P28**, and **P32**, yet not
written plainly enough to be implementable or teachable. They were memorialized as **clarifications
inside existing documents**, not as ledger entries.

| Clarification | Already implied by | Where memorialized |
|---|---|---|
| **The household declares what matters; Stewardship represents that declaration.** Stewardship never decides on the household's behalf that something matters | **DL-07**, **DL-21**, **P26**; the provenance requirement on significance; the Operational Trust *applies, does not author* rule | Stewardship model and contract, framework |
| **There is no universal HTBW hierarchy of importance.** Price, appraisal, sensor count, Identity participation, residency, and registration confer no significance | **DL-21**, **P26**; the absence of any ranking construct anywhere in the repository | Stewardship model and contract, glossary |
| **People are not Assets. Pets are not Assets.** Both may carry care obligations without being modelled as property | The asset model's object-distinction table; the glossary Person and Pet entries; *the Pet is not a Person* in the obligations scenario | Asset model, glossary, Stewardship model and contract |
| **Stewardship does not begin with an alert.** It begins with a declaration and a care definition; a reminder, advisory, corrective action, or escalation is a later consequence | The obligation structure, which requires a subject, statement, significance, schedule or condition, and provenance **before** any state can be evaluated | Stewardship model and contract, use-case document |
| **Stewardship never calls a Home Assistant service**, and an automation resolving a condition quietly is the **executor** acting, not Stewardship | *Stewardship never closes the door*; dependency-view rule 4 *Stewardship does not act*; **P32** *acting is not announcing* | Stewardship model and contract, framework, use-case document |
| **The canonical Operational Trust verb is *determines … for this request, in this context*.** *Enforces* is rejected; the unqualified *determines* is rejected | **DL-36**; *Operational Trust applies household values; it does not author them* | Operational Trust model and contract |
| **Continuity is not a child of Stewardship.** Stewardship history is Stewardship's; general preferences, Follow-Me, resume, transfer, and experience restoration never move into Stewardship | *Each responsibility owns the history of its own records*; the Continuity ownership list | Continuity model and contract |

**Four boundaries were deliberately preserved rather than adjusted:**

- **The obligation boundary is authoritative and was not relaxed.** *Stewardship owns the obligation;
  Stewardship does not own the resulting Communication or physical action* stands unchanged. The
  Episode 6 corrective-action narration is remediated **toward** the architecture, not the reverse.
- **The Asset Intelligence consolidation was already accepted and was not re-decided.** **DL-07**
  removed *what matters* from Asset Intelligence; **DL-08** placed the descriptive asset record with
  Foundation and kept the standalone product separate; **DL-19** removed every compatibility
  requirement; `asset-intelligence-contract.md` is Historical and superseded. **No implementation
  artifact, integration, namespace, storage schema, event name, or user interface was renamed or
  removed to make words match**, and none may be. Whether HTBW Core consumes the product as an
  optional evidence source remains **OD-20**.
- **No new responsibility, model, threshold, store, or history owner was created**, and no ownership
  moved. Truth still owns current and historical Facts; Foundation still owns the descriptive asset
  record and the relationship types; Operational Trust still owns every threshold and all disclosure;
  Concierge still owns decisions, delivery, and the Decision Trace; Continuity still owns preferences
  and sessions; the household still owns its values.
- **"Room health" and "asset health" remain undefined, deliberately.** HTBW defines no such state
  model and none may be invented (**OD-69**). A household-facing room summary is a **projection** over
  Truth Facts and Stewardship obligation states with the fields kept separate and separately
  explainable.

**Two genuine defects were found and are now open decisions**, rather than being closed by invention:

- **OD-75** — the obligation state set does not contain the *deferred* and *closed* outcomes the same
  document's history description names, and *what counts as evidence that care occurred* is asked and
  unanswered.
- **OD-76** — no caregiver relationship or delegated care authority exists, so a care obligation
  declared for one Person by another is **unsupported**. The aging-parent use case is documented with
  that gap stated plainly rather than papered over.

**These clarifications preempt nothing.** They decide no significance representation (**OD-21**), no
escalation ladder (**OD-22**), no obligation projection surface (**OD-23**), no Asset-derived Entity
vocabulary (**OD-69**), no consent user experience (**OD-06**), no safety-category scope (**OD-56**),
no urgency entitlement model (**OD-46**), no audience specification (**OD-52**), no executor-evidence
model (**OD-63**, **OD-64**), and no optional Asset Intelligence integration (**OD-20**).

**The eight validated use cases were added to
[../scenarios/stewardship-use-cases.md](../scenarios/stewardship-use-cases.md)** as canonical
Stewardship use cases and future acceptance scenarios: Artwork Preservation, Pet Stewardship,
Aging-Parent Support, Washing-Machine Leak Protection, Window-Shade Battery Maintenance, HVAC Filter
Maintenance, Irrigation Stewardship, and Antique Piano Stewardship. **No production capability is
asserted by that document**; HTBW Core remains greenfield under **DL-19**.

---

### Notes on the Episode 7 narrative-validation clarifications

**Recorded 2026-08-20. No decision was created, closed, reopened, or amended by this work, other than
the opening of OD-77 and OD-78 above.**

Narrative development of **Season 1 Episode 7 (Continuity — *How Does a Home Remember What
Matters?*)** was used as an **architecture stress test**, in the same manner as Episodes 4, 5, and 6.
The narrative is **not** authoritative architecture and was not incorporated as such. It was used to
find questions the accepted architecture must answer.

**The proposed episode doctrine was validated**, with the precise architectural wording recorded
behind it:

| Proposed narrative statement | Verdict | Precise architectural wording |
|---|---|---|
| *What Should Be Remembered?* as the internal framework question | **Accepted** | It is the abbreviated form already used in the [../architecture/north-star.md](../architecture/north-star.md) framework diagram. The full canonical question is *what should be remembered, restored, resumed, or transferred?* and the episode must not narrow Continuity to memory alone |
| *A Home That Behaves Well remembers what matters so comfort, experiences, relationships, commitments, and care can continue* | **Accepted as the human-facing summary** | Continuity holds **preferences, sessions, resume and transfer state, and experience history**. Relationships, commitments, and care are held by **Foundation**, the **source system**, and **Stewardship** respectively; Continuity holds how the household wants them delivered |
| *Continuity is not unlimited memory or a generic data store* | **Accepted** | The constraint is already binding through **DL-46** (no second copy), **DL-47** (every record class declares its retention), and **P22** (no shadow system of record) |
| *Continuity preserves governed observations and patterns* | **Contradicted as written** | An **observation is a Domain Event owned by the responsibility that observed it**, and an unaccepted pattern is **nothing behavioural**. Continuity holds the **approved preference** — never the observation that produced it |
| *Continuity preserves watering history, moisture history, rainfall, and prior outcomes* | **Contradicted** | [../scenarios/stewardship-use-cases.md](../scenarios/stewardship-use-cases.md) Use Case 7 records **Continuity interaction — None**. Weather Facts are **Truth's Historical Facts**; watering obligations and outcomes are **Stewardship's** |
| *Continuity preserves relevant history, associations, and commitments for care* | **Contradicted** | **Stewardship history is Stewardship's.** Continuity's contribution to a care Communication is the **preferred delivery, preferred presentation, and re-presentation preference**, and nothing else |
| *Stewardship marked the commitment as requiring care* (dental appointment) | **Contradicted** | **A calendar appointment is not a care obligation.** Stewardship represents a care expectation **the household declared**; it never decides on the household's behalf that something matters |
| *"I need to make dinner"* authorising a room-to-room media transfer | **Not yet governed** | The canonical trigger is an **explicit instruction** or an **already-enabled Follow-Me preference**. No accepted document maps an indirect utterance to a media transfer, and **DL-30** is not discharged by assertion |
| *The home learned the routine* | **Accepted only with qualification** | *The home noticed the pattern, asked whether you wanted it, and does it because you said yes.* Silent promotion is prohibited (**P26**, **DL-21**) |
| *Continuity reconnects the person to the governed personal context* | **Not yet governed** | The Person-to-external-resource association has **no named owner** — **OD-77** |

**Seven points were found where accepted architecture was correct but under-stated** — true by
implication from **DL-21**, **DL-26**, **DL-27**, **DL-30**, **DL-33**, **DL-41**, **DL-46**,
**DL-47**, **P21**, **P22**, **P26**, **P28**, **P30**, and **P32**, yet not written plainly enough to
be implementable or teachable. They were memorialized as **clarifications inside existing documents**,
not as ledger entries.

| Clarification | Already implied by | Where memorialized |
|---|---|---|
| **Continuity holds preferred delivery and preferred presentation**, and the preference *dimensions* are enumerated only in Historical documents that are not authority | The Stewardship use-case ownership map; the Communication model's Continuity row; *preferred interaction patterns* in the Continuity model | Continuity model and contract, use-case document |
| **Continuity holds the approved preference, never the observation.** An observation is a Domain Event owned by its observer | **P26**; the Continuity model's own learning paragraph | Continuity model and contract, use-case document |
| **Continuity holds no external-service reference.** Calendar, mailbox, account, and media-profile associations are not in its ownership list | The Continuity ownership list; the Person-extension table's unassigned row | Continuity model and contract, use-case document, **OD-77** |
| **A record does not become Continuity's because it is personal.** Care history is Stewardship's; environmental history is Truth's; source content is the provider's | *Each responsibility owns the history of its own records*; **DL-46** | Continuity model and contract, use-case document |
| **A remembered value is not a Fact**, and current Truth, Room mode, Identity, Operational Trust, audience, and safety are preconditions to applying one, never overridden by it | The Continuity blocking-state model; dependency-view rule 5 | Continuity model and contract, use-case document, **OD-78** |
| **There is no Journey, checkpoint, or progress-marker object.** Provider-owned playback position stays with the provider; Continuity holds resume eligibility and a Governed Reference | The glossary's Experience and Session entries; **DL-46**; **P30** | Continuity model and contract, use-case document |
| **Continuity neither formulates nor presents a recommendation** | Dependency-view rule 5; the Reasoning Provider glossary entry | Continuity model and contract, use-case document |

**Five boundaries were deliberately preserved rather than adjusted:**

- **The person-scoped versus room-scoped split is authoritative and was not extended.** Preferred
  artist, genre, album, and playlist are person-scoped; last song, last genre, music volume, duck
  volume, and TTS volume are room-scoped. **The proposed household-, asset-, experience-, journey-,
  capability-, and relationship-scoped memory list was not adopted**, because those are the scopes of
  *other responsibilities' records*, not of Continuity preferences.
- **The superseded memory documents were not revived.** `household-memory-model.md`,
  `household-memory-contract.md`, `person-continuity-model.md`,
  `person-continuity-affinity-contract.md`, `person-room-affinity-model.md`,
  `experience-restoration-context-model.md`, `experience-restoration-contract.md`,
  `adr-household-memory-governance.md`, and `adr-personalization-governance.md` are all **Historical
  and superseded**, their canonical replacement is the Continuity model and contract, and
  [../architecture/adr-historical-explainability-and-historical-truth.md](../architecture/adr-historical-explainability-and-historical-truth.md)
  states that their **former ownership boundaries are not reactivated**. **There is no Household
  Memory responsibility, no Historical Intelligence responsibility, and no Affinity responsibility**,
  and none may be created to carry Episode 7 material.
- **No new responsibility, model, object, store, threshold, or history owner was created**, and no
  ownership moved. Truth still owns Facts and Fact history; Foundation still owns object definitions
  and relationship types; Stewardship still owns obligations and care history; Operational Trust still
  owns every threshold, all disclosure, and all retention policy; Concierge still owns decisions,
  delivery, and the Decision Trace; Continuity still owns preferences, sessions, and experience
  history; the household still owns its values.
- **Household traditions, plant-care knowledge, and travel-time computation remain undefined,
  deliberately.** A repository-wide search returns no canonical match for *tradition*, *ritual*, or
  *travel time*, and **none was invented here**. A recurring household moment is an **Experience** or
  a household-authored Home Assistant automation; deciding that a recurrence *matters* is a
  **household declaration**.
- **A recommendation is not an authorisation, and a reasoning provider is not an authority.** *A
  reasoning provider owns nothing… its output never silently becomes a Fact, and its recommendation
  never silently becomes an authorised action.* Provider strategy remains **OD-67**, and **DL-41**
  makes a provider a declared capability dependency for which **no local approximation stands in**.

**Two genuine defects were found and are now open decisions**, rather than being closed by invention:

- **OD-77** — the Person-to-external-resource association is named in the Person-extension table with
  **no owning responsibility**, and no accepted relationship type expresses it. Every personal-resource
  outcome in Episode 7 depends on it.
- **OD-78** — the remembered-value classes are nowhere enumerated, restoration mechanics exist only in
  a subordinate patterns document, and a Continuity-held *last lamp level* sits in unresolved tension
  with **DL-46**.

**A third defect was found while reviewing the retiring Concierge configuration surfaces**, and is
recorded as **OD-79**: **presentation preference scope and precedence**. Person scope is settled as
Continuity's, room scope has **no owner**, the Continuity scope tables contain **neither**, and no rule
states what happens when a Room persona and a person's interaction preference disagree. The dimension
enumeration gap noted in the clarification table above is part of the same decision.

**One documentation-governance defect was found that is not an open decision.**
[../architecture/north-star.md](../architecture/north-star.md) declares itself *subordinate only to
the North-Star framework as represented in the HTBW video-series artifacts*, **yet no video-series
visual artifact exists in this repository**, and a repository-wide search for `CORE-08` and for any
visual register returns nothing. The highest-ranked authority in the governance chain is therefore
**unversioned, unregistered, and unreviewable**. It is tracked as documentation remediation alongside
**#145**, and **no visual asset was created, altered, or asserted by this review**. The review
validated the repository's canonical equivalent instead — the framework diagram node in
[../architecture/north-star.md](../architecture/north-star.md), and
[../architecture/framework.md](../architecture/framework.md) section 5.

**These clarifications preempt nothing.** They decide no learned-policy lifecycle (**OD-28**), no
learning evidence eligibility (**OD-65**), no behaviour attribution (**OD-63**), no native behaviour
observation (**OD-64**), no session merge (**OD-24**), no resume window (**OD-25**), no experience
history retention (**OD-26**), no session concurrency (**OD-27**), no re-presentation preference
(**OD-48**), no reasoning-provider strategy (**OD-67**), no delegation boundary (**OD-66**), no
audience specification (**OD-52**), no interruption risk classes (**OD-51**), no erasure mechanics
(**OD-09**), and no deletion-versus-preservation reconciliation (**OD-36**).

**The fifteen validated use cases were added to
[../scenarios/continuity-use-cases.md](../scenarios/continuity-use-cases.md)** as canonical Continuity
use cases and future acceptance scenarios: Comfort Restoration, the Dental Appointment Reminder,
Follow-Me Music, Audiobook Resume, Interaction Styles, Person-to-Calendar and Person-to-Mailbox
Associations, the Morning Calendar Rhythm, Maisey's Care Continuity, Artwork Caretaker Notification,
Irrigation and Weather, Content Recommendation Candidates, Household Traditions, Correction and
Deletion, Guests and Multi-Person Conflict, and Explaining What Was Remembered. **No production
capability is asserted by that document**; HTBW Core remains greenfield under **DL-19**.

---

### Notes on the Asset Intelligence legacy capability harvest

**Recorded 2026-08-20. No decision was created, closed, reopened, or amended by this work.**

The released **Asset Intelligence** HACS product was reviewed end to end — services, coordinator,
evaluation, storage, config and options flows, diagnostics, entities, events, frontend surfaces,
tests, and its own open issues — to harvest household outcomes and operational lessons **before** the
product is retired into HTBW. The register is **#155**.

**Asset Intelligence implementation is rank-four evidence** under
[authority-order.md](authority-order.md). It demonstrated outcomes, revealed refinements, exposed
gaps, and supplied reference patterns. **It created no architecture authority and resolved no open
decision.**

**No new open decision was required.** Every gap found is owned by an existing accepted decision or an
already-open one. The harvest tested roughly twenty-four services, twenty domain event types, twelve
accumulating record classes, nine environment signal categories, and five interaction surfaces against
the canon, and the canon already answered the ownership questions.

**Two findings are contradictions with accepted architecture rather than gaps**, and in both cases the
governing sentence was already written:

- **Shipped care defaults are applied as though declared.** The product ships a `baseline_adult`
  human-comfort profile and per-asset-type debounce profiles, and evaluates against them whether or
  not the household ever saw them. [../models/stewardship.md](../models/stewardship.md) already
  states that a default must be one the household **explicitly chose**, and that **a default the
  household never saw is not a declaration**. The household outcome — low-friction setup — is worth
  preserving; the mechanism is not. A default is a **proposal** until accepted. The residual question,
  what provenance an accepted default carries, is recorded on **OD-21**.
- **Home Assistant labels are read back as behavioural authority.** A `label_profiles` map keyed
  `asset_type:painting` and `sensitivity:high` selects the debounce policy that decides how long a
  risk condition must persist before a household is told. **OD-68** preserves the opposite direction —
  *Asset Type stays authoritative in HTBW, labels stay derived* — and labels are recorded in
  [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) as **flat,
  global, and ungoverned**. A projection is not an input. Recorded on **OD-68**, with the
  significance-shaped key routed to **OD-21**.

**One negative result is worth recording.** The most mature implementation in the portfolio reached
release without any **significance** field at all, expressing what matters implicitly through
registration and declared limits — and, where it needed a significance-shaped concept, inventing it as
an ungoverned label. It also holds purchase price and estimated value and **uses neither in any
evaluation**, independently honouring the accepted rule that **price confers no significance**.

**Fifteen reference patterns were identified for preservation**, recorded in full on **#155**. The
most architecturally significant are: the **Change Record shape** — changed-field list, explicit
before and after, and actor — which satisfies **DL-26** as written; **bounded audit payload
constants**, a refinement this repository names nowhere; **domain events published on the native Home
Assistant event bus**, which is **DL-46** done correctly and which exists in the same codebase as the
pattern that violates it; **reason strings that carry the observation, the threshold, and the
mechanism**; and **honest unknowns**, where missing data produces a stated warning and never a
violation.

**Refinements with no canonical home** were recorded against the decisions that own them rather than
being adopted: temporal **debounce** and value **hysteresis** as stability-before-commitment rules
(**OD-18**) — independently invented by two separate products, which is the strongest argument that
the architecture should name the primitive; **per-signal aggregation across multiple contributors**
(**OD-17**); a four-value confidence enumeration in which **staleness competes with coverage for a
single field** (**OD-18**, **OD-74**); **soft and hard threshold pairs** (**OD-21**); **loan terms**
including counterparty, expected return, and insurance responsibility (**OD-75**); and a **transient
export artifact** with an unconditional sixty-second lifetime (**OD-09**).

**Nothing was migrated, and no schema was adopted.** No object model, storage schema, event schema,
ring-buffer bound, `.storage` layout, media path, panel design, hardcoded category, audience class,
confidence percentage, or profile naming was copied into this repository, and none may be on the
strength of this review alone. **No implementation was modified in any repository**, no HTBW
governance was placed in the Asset Intelligence repository, and **no issue was closed**.

---

### Notes on the enrollment sufficiency and re-enrollment governance challenge

**A proposed open decision was raised, tested, and rejected. No identifier was issued, and the ledger
is unchanged at eighty identifiers.** The Concierge and Voice Identity legacy capability harvest
proposed a decision on *enrollment sufficiency and re-enrollment obligation*, on the grounds that two
implementations ship different enrollment constants and that one of them emits a re-enrollment
instruction with no governed owner. A narrow challenge established that **accepted architecture
already governs both questions**, and that issuing the decision would have **reopened resolved
work**. This note records the result so the question is not raised a third time.

**Enrollment sufficiency is four layers, not one, and each already has an owner.** *Enrollment-data
adequacy* — whether there is enough usable evidence to construct a derived profile — belongs to
**Identity**, which owns enrollment, revocation, and identity diagnostics, and whose enrollment
**state and quality** are already required to be **inspectable by the enrolled person** and
expressible as a **quality summary** under the safe-metadata rule. *Where that quality enters an
assertion* is settled by **DL-32**, which places reliability on the **Person-to-evidence-source
association** rather than on the evidence type, and by **DL-38 (F3)**, which already names
**configured association reliability** as a qualification stage that **may only lower or hold**. A
better-enrolled voice profile lawfully raises the ceiling that the voice family can reach for a
person, and a marginal one lawfully lowers it; **the slot exists and is occupied**. *Assertion
producibility* is **DL-38 (F1)** and **(F8)**, where `known` requires the purpose minimum **and** a
governed separation requirement and is otherwise `ambiguous`. *Capability sufficiency* is **DL-36**
and the **Required Identity Band**, owned by **Operational Trust**, where **sufficiency is never
universal**. **These four are never collapsed into one question, and the harvest's central error was
to collapse them.**

**The literal values were already settled as non-architecture, by a resolved decision.** **OD-16**
states that the remaining values are **implementation mapping, not architecture** — naming
**freshness durations**, the **separation margin**, **per-purpose minimums**, and **reason-code
strings** as **Fusion Policy configuration**, versioned and governed, and **none of them an
unresolved architectural question** — and **DL-38** adds that **no duration is prescribed**. Sample
counts, minimum durations, quality thresholds, prompt-category diversity, and capture-distance
diversity are of exactly that class. **Two implementations holding different constants is calibration
divergence, not an architecture gap**, and **making a shipped constant canonical would contradict
DL-36 and reopen OD-16**.

**Re-enrollment is a dependency outcome, and creates no obligation by default.** An incompatible,
superseded, or revoked derived profile is an **Identity lifecycle result**; **DL-43** already ties a
voiceprint's existence to the profile remaining enabled **and consent remaining valid**. The
household-facing consequence is **DL-41**, which already enumerates **configured but invalid** among
the distinguishable dependency states, requires that the capability be **unavailable**, that the
missing dependency be **named**, and that the household be told **in a sentence it can act on**,
forbids **emulating** the missing dependency, and insists that **capability unavailable is never a
trust failure, an identity failure, or a permission failure**. **Stewardship raises nothing**,
because the household **declares** what matters and **a default the household never saw is not a
declaration**; an implementation emitting a re-enrollment instruction is a **remediation hint**, not
a declaration. **DL-48 is referenced here as not applicable by default, not applied.** Where a
household does explicitly declare that maintaining voice recognition matters, the existing DL-48
machinery already carries it, and **no new construct is required for that path**. Telling the
household is ordinary **Communication**: any responsibility may originate one, and **Concierge**
decides and records delivery.

**The governed sequence is therefore already complete**: Identity reports that no compatible profile
is available; **DL-41** reports voice attribution unavailable and names the incompatible dependency;
**Operational Trust** evaluates whether another evidence path satisfies the Required Identity Band
for the request; **Concierge** offers re-enrollment as **optional corrective action**; **Stewardship
creates no obligation**.

**This note creates nothing.** It introduces **no Enrollment Sufficiency construct**, **no enrollment
quality model**, **no re-enrollment obligation class**, and **no canonical threshold, sample count,
duration, margin, or quality score**. It **amends no accepted decision**, **reopens none**, and
**preempts nothing** — **OD-15** still owns assertion lifetime, **OD-06** still owns the consent
experience including revocation and the currently absent authorisation to enrol another person,
**OD-07** still owns voice processing locality, and the execution host — without which none of these
values can be validated at all — was **OD-80**, since **accepted as DL-50**.

**A separate finding is recorded rather than resolved.** Real-time voice comparison is **not a
validated capability**. Its plumbing is live-proven — evidence production executes on a real host and
correctly returns a no-match outcome — but **no `known` attribution has ever been produced from a
live utterance**, because at the time of this note the encoder had no accepted execution host. **That
blocker is removed by DL-50, and the finding is not thereby discharged**: an accepted host is a
precondition for validation, never a substitute for it. **No calibration value in
either implementation has been validated**, and none may be described as calibrated, canonical, or
household-ready on the strength of this review.

---

### Notes on the legacy documentation knowledge harvest

**This harvest produced no decision, and the ledger is unchanged.** A documentation-only review of
the Concierge, Voice Identity, and Asset Intelligence repositories was completed after their code
harvests, covering two hundred and thirty documents in one repository, seventy in another, and nine
in the third. **Three legacy-product reviews have now produced zero new open decisions.** That is the
third consecutive confirmation that the accepted architecture is materially complete, and it is
recorded here so the pattern is not mistaken for insufficient scrutiny.

**A legacy filename is not an authority claim.** The legacy sets contain documents named as ADRs,
contracts, and architecture that were authored against the pre-refoundation architecture, and others
that remain marked *proposed* while dependent documents treat them as settled. **Every legacy
document is rank-four historical evidence**, and none acquires standing from its filename, its
heading, or the confidence of its wording.

**Four accepted decisions were independently rediscovered by products that did not share them.**
Dependency naming distinct from permission failure (**DL-41**) appears in one product as a refusal
category set and in another as a per-reason retry vocabulary; a recommendation is never a decision
(**DL-21**) appears as an advisory boundary, a repairs boundary, and a consumption boundary in three
separate codebases; reference rather than copy with an exact version (**DL-27**) appears as a
contract-version rule that forces migration and forbids silent fallback; and **DL-33**'s requirement
that `unknown` remain expressible appears as a five-state fail-closed matrix. **Independent
rediscovery is the strongest available evidence that a decision describes something real**, and these
four are accordingly recorded as candidates for formal acceptance review rather than as new work.

**Stability before commitment has now been invented four times.** Two products and one household
automation pattern each arrived at a dwell, debounce, or hysteresis rule without shared design, and
the third product added a deliberate severity exemption so that critical signals escalate
immediately. **OD-18** owns the primitive; the intervals do not belong to this ledger.

**The largest finding is not architectural.** The legacy documentation sets hold a substantial body
of **operational refinement** — precedence ladders, fallback ladders, dwell intervals, cleanup
taxonomies, outcome classifications, and household-facing wording — which is not architecture, has
almost no canonical home, and would be lost when those repositories go quiet. Two extensions were
made to subordinate documents to preserve the parts that clarify an accepted requirement:
[../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md) records the
validation-is-not-discovery boundary, refusal categorisation, per-reason retry eligibility, the
separation of a machine-safe reason code from a household sentence, and the rule that **silence must
never be used to hide a refusal**; and
[../patterns/temporary-artifact-lifecycle-pattern.md](../patterns/temporary-artifact-lifecycle-pattern.md)
records the distinction between an idempotent and a completed cleanup, the reconciliation taxonomy,
the prohibition on reporting cleanup successful while storage was unavailable, sanitised failure
detail, self-expiring artifacts, and payload bounds rather than count bounds alone. **Both additions
are explicitly non-normative, add no requirement, and canonise no value.** The remainder is held
outside this ledger as a standing implementation-planning input.

**This note creates nothing.** It introduces **no outcome-classification model**, **no refusal
taxonomy**, **no retry policy**, **no reconciliation model**, and **no household wording standard**.
It **amends no accepted decision**, **reopens none**, and **preempts nothing** — **OD-04** still owns
policy precedence, **OD-18** still owns stability before commitment, **OD-29** and **OD-30** still
own trace persistence and visibility, and **OD-78** still owns remembered-value classes. **No legacy
schema, threshold, calibration value, vocabulary, or product ownership was imported**, and the
superseded vocabulary those documents use — *composite room*, *household memory*, *affinity*,
*experience model* — is not reactivated by being quoted.

---

### Notes on the location and engagement-context open decisions

**OD-73 and OD-74 create no responsibility, no model, and no new object.** Foundation continues to own
object definitions, the `located-in` relationship, and Room Configuration; Identity continues to own
assertions and fusion; Truth continues to own Facts and Fact history; Operational Trust continues to own
permission, disclosure, and every threshold; Concierge continues to own decisions and the Decision Trace.
**There is no Location, Engagement, Presence, or Engager responsibility, and none may be created to hold
this material.**

**No new model was created, deliberately.** The **Truth Fact** already carries a first-class, subject-typed
`Subject` field, so extending its enumeration to *Home, Room, Merged Room, Person, Pet, Asset, Device*
achieves everything five parallel location-assertion types would have achieved — with one owner, one
lifecycle, one provenance model, one conflict model, and one retention rule (**DL-47**). **A
`PersonLocationAssertion`, `PetLocationAssertion`, `AssetLocationAssertion`, `DeviceLocationAssertion`,
`CurrentEngagerAssertion`, or `EngagementContext` model must not be created.** *Location Fact* and
*Engagement Fact* are **Fact classes of the existing model**, not new models.

**One structural asymmetry is deliberate and must not be smoothed away.** A **Person**-subject location
Fact requires an Identity Assertion first (**DL-06**, **P9**), because establishing *which human* is a
fusion question over a bounded candidate set of known Persons. A **Pet**, **Asset**, or **Device** subject
requires **no Identity Assertion and must not be routed through Identity**, because there is no *which
human* question — Identity's candidate set contains known Persons only, and **DL-39** bands describe
identity support only. *"Where is Maisey?"* and *"Where is my phone?"* are **Truth-only** questions;
*"Where is Tom?"* is a two-stage question.

**"Current Engager" is rejected as an HTBW term.** It does not appear in this repository, and the concept
it names is already decomposed — more precisely — into the six **Assertion Purposes** accepted under
**DL-32**: Speaker Attribution, Room Presence, Household Presence, Interaction Initiator, Authenticated
Session Identity, and Endpoint Context. **A single fused engager result would recreate the general-purpose
identity score that DL-32 and DL-38 prohibit**, would break the **F1** purpose ceilings, would break
**DL-36**'s four independent consumers, would break **DL-34**'s separation of Requestor, Speaker, Present
Person, Potential Listener, Authorized Recipient, and Delivery Target, and would make the kiosk safeguard
unimplementable — because that safeguard *is* the purpose separation. The rejection is recorded in
[../models/glossary.md](../models/glossary.md).

**The Truth and Identity direction was already settled and is not reopened.** **DL-06**, **P9**, and
[../architecture/dependency-view.md](../architecture/dependency-view.md) rule 2 are unchanged: Identity
feeds Truth; Truth does not feed Identity authority. **The apparent circularity is a documentation defect,
not an architectural one**, and it is remediated by explanatory notes in
[../models/truth.md](../models/truth.md), [../architecture/dependency-view.md](../architecture/dependency-view.md),
and [../architecture/runtime-sequence.md](../architecture/runtime-sequence.md). **Truth's Room-occupancy
Fact precedes fusion; Truth's Contextual Person-Presence Fact follows it. They are different Fact Subjects,
and the sequence is not a cycle.**

**Only two open decisions were created, from a larger candidate set.** Extending the Fact Subject
enumeration, defining *Location Fact* and *Engagement Fact*, separating declared from current location,
stating non-Person evidence ceilings, declaring Pet and Device governing parents and retention, and
enumerating disclosure rules for device- and pet-derived location were **not** created as open decisions,
because **ownership for each is already determinate** — only the statement was missing, and it has now been
made. Creating decisions for them would have manufactured uncertainty the architecture does not have.

**Two documentary bounds apply and are recorded in the Platform Capability Review.** Device tracker
granularity is documented as the **zone**, and a connection tracker's zone as an **assumption**; **no
native Room-level or Area-level BLE proximity capability, no native pet-location capability, and no native
kiosk concept could be verified.** Under **DL-30** those burdens are **not discharged**, and no Room-level
claim may be asserted from them.

**OD-73 and OD-74 preempt nothing else.** They decide no composite-fact aggregation (**OD-17**), no Fact
validity defaults (**OD-18**), no conflict-resolution rules (**OD-19**), no assertion validity window
(**OD-15**), no risk-class enumeration (**OD-51**), no audience-uncertainty policy (**OD-71**), no
behaviour attribution (**OD-63**), and no unknown-actor correlation confidence (**OD-72**).

### Notes on the temporal open decisions

**The unverified Storage helper guard now attaches to OD-01, not to OD-34.** The official Home
Assistant Storage helper documentation could not be verified during the temporal-record review, and
no link to it is recorded anywhere in this repository. It must be located and reviewed first.
**OD-01's residual — config entry, subentry, or private storage — must not be closed on assumed
Storage helper behaviour.** OD-34 closed without relying on any such assumption, because the
temporal-persistence *model* never depended on the mechanism; it is recorded as closed on that basis
and on no other.

**Two facts about config entries are verified and constrain the residual.** Home Assistant documents
config entries as **configuration data created by a user via the UI** and **removable by the user**,
and documents subentries as configuration **added by the user via the UI**. A store that a resident
creates and deletes as configuration is therefore **structurally unsuitable for immutable historical
records**, and OD-01 is narrowed accordingly. See
[config entries](https://developers.home-assistant.io/docs/config_entries_index/).

**OD-41 does not create a responsibility.** Should a persisted Incident or Case object be adopted,
Foundation would define the model, Operational Trust would govern authority, and Concierge could
coordinate creation, assembly, narration, and export. For now, an **Incident is at least a retrieval
scope** over governed records; nothing here states that it can never become a durable object.

### Notes on the communication open decisions

**OD-42 through OD-58 create no responsibility.** Foundation defines the communication model,
Operational Trust governs entitlement and visibility, originators originate, and Concierge decides
and records delivery. **There is no Communication, Messaging, Inbox, Delivery, or Escalation
responsibility, no central delivery owner, no central inbox owner, and no second escalation ladder.**

**OD-47, OD-50, and OD-51 are recorded as partially resolved.** The Household Inbox is a projection;
there is one escalation architecture; interruption is an Operational Trust action-risk class. Only
their residual questions remain open, and reopening the resolved parts requires a new ADR.

**OD-43, OD-55, and OD-57 must not be closed on assumed Home Assistant behaviour.** Dashboard
visibility semantics, `media_player` delivery semantics, and voice-satellite indicator behaviour were
**not verified** during the communication review, and no links to them are recorded anywhere in this
repository. They must be located and reviewed first.

**OD-56 is bounded by the life-safety non-claim.** HTBW is not a life-safety system, and no closure
of OD-56 may assert smoke detection, carbon-monoxide detection, medical alerting, security
monitoring, or emergency-notification sufficiency.

### Notes on the platform-alignment open decisions

**OD-59 through OD-67 create no responsibility.** There is no Activity, Learning, Adaptation,
Attribution, Conversation, or Reasoning responsibility. Truth continues to own Facts and Fact
history; Continuity continues to own preferences and sessions; Operational Trust continues to own
permission; Stewardship continues to own obligations and the single escalation ladder; Concierge
continues to own decisions, delivery, and the Decision Trace. **What occurred in the household
remains a Domain Event, owned by the responsibility that observed it** — see
[../models/temporal-record.md](../models/temporal-record.md).

> **Do not close an open decision solely because a native Home Assistant capability exists.** The
> existence of a capability is evidence at step 1 of the **DL-30** burden of proof. Closure additionally
> requires that the constitutional requirement be satisfied, or that the remaining gap be recorded.

**OD-10 must not be closed on assumed Floor-registry behaviour, and OD-61 must not be closed on
assumed Area-registry behaviour beyond the documented attributes.** The Floor registry and Label
registry developer pages did not resolve during the platform alignment review, and no links to them
are recorded anywhere in this repository.

**OD-67 must classify each candidate accurately before evaluating it.** These are different things
and must not be merged: a conversation mechanism; a speech-to-text provider; a text-to-speech
provider; a conversation agent; a general reasoning provider; a local model; a cloud model; a
retrieval mechanism; and an action-execution mechanism. **Home Assistant Cloud must not be
characterised as a reasoning provider unless official Home Assistant or Nabu Casa documentation
supports that characterisation.** Record the precise documented capability instead.

Invariants that any closure of **OD-67** must preserve:

- Truth owns Facts. **A provider's output never silently becomes a Fact.**
- The Decision Trace owns governed reasoning. A provider does not author the reasoning of record.
- Operational Trust owns permission. **A recommendation never silently becomes an authorised action.**
- Concierge orchestrates. A provider is a consulted component, never a decision owner.
- **A model is replaceable.** No architecture may depend on one provider's behaviour.
- Explanations must remain grounded in governed records.
- Sensitive context is supplied only under the consent, privacy, and authority rules.

### Notes on the representation open decisions

**DL-31 creates no responsibility, no registry, and no new object.** It states how existing HTBW
concepts relate to existing Home Assistant objects. Foundation continues to own descriptive
knowledge, including **Asset Type**; Stewardship continues to own significance, care, and
obligations; Truth continues to own the evaluation of current conditions.

> **A native representation is a projection.** It makes an HTBW concept visible, targetable, and
> automatable in Home Assistant. It never becomes the authoritative record, and its absence,
> deletion, or failure never changes what HTBW holds to be true.

**OD-68, OD-69, and OD-70 are each independently closable.** None depends on the residual of
**OD-01**, and closing any of them does not close the others.

**OD-01's residual must not be closed on assumed storage behaviour.** It **now owns that residual
alone** — OD-34 previously duplicated it and has since closed on the persistence *model* without
relying on any such assumption. The Home Assistant storage-helper documentation could not be verified
during this review. Under **DL-30**, unverifiable documentation leaves the decision open.

**DL-31 preempts nothing.** It decides nothing about identity confidence thresholds (**OD-08**),
identity evidence weighting (**OD-16**), the governed-record representation mechanism (**OD-01**
residual), or reasoning provider strategy (**OD-67**).

**No custom device class exists.** Device `entry_type` accepts only `None` and the `service` member,
and device classes are entity classifications drawn from per-domain enumerations. **HTBW must not
claim a custom device class, and must not repurpose native registry fields to carry HTBW meaning.**

**Household language follows the same rule, and this resolves OD-14.** Home Assistant owns native
names, native Assist aliases, and native Assist exposure. HTBW reads them, may use them to **seed** a
contextual term, and stores only the Room-scoped meaning Home Assistant does not natively represent.
**Nothing is synchronised in either direction**, because a contextual term may name a group, a
capability, or a Room-dependent target that no alias can carry — and because Home Assistant documents
that configured aliases may also be used by assistants beyond Assist. **No new open decision was
required**, and **OD-13**, **OD-59**, and **OD-70** are untouched.

> **Do not assert that Home Assistant treats aliases as globally conflicting.** The documentation
> describes the same alias applied to entities in different Areas, matched in conjunction with the
> Area name. The write-back prohibition rests on scope and reach, not on a claimed native conflict.

### Notes on the identity-evidence open decisions

**DL-32 introduces no responsibility and no model.** The Person-to-evidence-source association was
already listed among the things Identity owns; **DL-32 names and governs it rather than creating it.**
No second Person record, no parallel person-to-tracker registry, no identity history store, and no
generic event store exists as a result.

**Ownership is unchanged.** Identity performs fusion and owns the reliability configuration, because
that configuration determines how identity evidence is *interpreted*. **Continuity does not own it**
merely because personal habits inform it. Truth is not an identity fusion engine, Concierge is not,
and Operational Trust does not calculate identity — it evaluates permission **after** an assertion
exists.

**OD-16 could not close cleanly at the time, and was not forced.** The governing architecture was
complete, but the **aggregation function** — how weighted, fresh, correlated, and contradicted evidence
becomes one confidence result — was genuinely unresolved. **Inventing arithmetic to close a decision
would have been the defect, not the closure.** *It was subsequently resolved as **DL-38**, without
inventing arithmetic — see the notes on the fusion decision below.*

**A second bound is documentary.** Device tracker granularity is documented as the **zone**, and a
connection tracker's zone is documented as an **assumption** while connected. **No native Room-level
BLE capability and no native kiosk concept could be verified**, so none is claimed, and Room Presence
is asserted only from evidence whose Room granularity is actually grounded.

**DL-32 preempts nothing else.** It decides no confidence bands (**OD-08**), no validity windows
(**OD-15**), no voice processing locality (**OD-07**), no consent user experience (**OD-06**), no
learning lifecycle (**OD-28**), no learning evidence eligibility (**OD-65**), no behaviour attribution
model (**OD-63**), no native execution evidence capture (**OD-64**), and no retention floor
(**OD-05**, **OD-26**, **OD-49**).

**Derived recognition forms are the same projection rule again, and required no decision.** A
resident configures one term; HTBW may derive additional forms of **that term** for matching, and a
derived form is subordinate, generated, explainable, and never a vocabulary entry. **No plural field,
no second authoritative value, and no new state exist.** A configured term always outranks a derived
form, so **plurality never creates a group** — group vocabulary remains explicitly configured. The
authoritative term is whatever form the household chose; **HTBW must not require singular terms**,
since the canonical vocabulary examples are themselves plural.

### Notes on the unknown-person, audience, and actor decisions

**DL-33, DL-34, and DL-35 introduce no responsibility and no owner.** Identity keeps assertions and
fusion; Truth keeps Facts; Operational Trust keeps permission, disclosure, and the unidentified-person
policy; Concierge keeps orchestration, delivery selection after permission, and the reconstruction
projection; Communication remains the governed object. There is no Actor, Audience, Security,
Privacy, or Surveillance owner, and none may be created to hold this material.

**No new model was created.** Unknown Person is the existing `unknown` assertion state carrying
whether a human participant is supported — the one element the model genuinely lacked, and the
smallest compatible extension. The unidentified-person policy is the phrase already used by
[../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md) and
[../architecture/runtime-sequence.md](../architecture/runtime-sequence.md), stated as a governed
policy rather than only as a fallback. The Unknown Actor Reference lives inside the existing
Historical Reconstruction projection and creates no store.

**Only two open decisions were created, from three candidates.** Audience-uncertainty policy
(**OD-71**) and actor-correlation confidence (**OD-72**) are each materially distinct, independently
closable, and owned. A third candidate — the unidentified-person capability defaults — was **not**
created: the architecture is accepted here, and the defaults are already the subject matter of
**OD-51** and **OD-08**. Creating it would have duplicated both.

**OD-08 and OD-16 were both open at this point.** Neither residual was resolved by this work. **OD-16 concerns
identifying a known Person from identity evidence; OD-72 concerns grouping observations without
identifying anyone.** They are different questions with different outputs, and neither aggregation
function is invented here.

**DL-35 preempts nothing else.** **DL-47** and **OD-39** own retention and hold governance,
**OD-40** still owns Evidence Package assembly and audience, **OD-41** still owns whether an Incident
becomes a persisted object, **OD-38** still owns correlation identifiers, and **OD-63** and **OD-64**
still own behaviour attribution and native execution evidence — an Unknown Actor answers *who was
moving*, never *what changed a device*.

**One documentary bound applies.** Externally owned video is referenced on whatever identifiers and
integrity metadata the owning system supplies. **No claim is made here about what any specific camera
integration exposes**, because no such documentation was verified; where the owning system supplies
nothing stable, the reconstruction records that limitation rather than substituting one.

### Notes on the confidence-consumption decisions

**DL-36 and DL-37 introduce no responsibility, no model, and no file.** Both are recorded inside the
existing Operational Trust and Identity material. Every structure they rely on already existed: the
`permitted_with_confirmation` authority outcome, the four-row action-risk table, the *Explicit
confirmation* evidence row and its explicit exclusion of *permanent certainty*, the **Authority**
state of Existence → Participation → Exposure → Authority, and
[../architecture/framework.md](../architecture/framework.md)'s assignment of *identity-confidence
thresholds* and *confirmation requirements* to Operational Trust. **Nothing is duplicated and nothing
superseded is revived.**

**They are separate because they answer different questions.** DL-36 answers *who decides whether
confidence is enough*. DL-37 answers *what a confirmation is worth once it is given*. A household
could accept the first and still get the second catastrophically wrong — by treating a confirmed
interaction as an authenticated session, or as a retroactive correction of the assertion behind it.

**No new open decision is created, deliberately.** Confirmation strength, scope, and lifetime are not
a new unresolved choice: **OD-08 already claims *confirmation scope and lifetime* as its own
residual**, so a separate decision would duplicate it. **OD-15 is not the confirmation decision** — it
is identity *assertion* validity, owned by Identity — and conflating the two would place a confirmation
policy under the wrong responsibility. Seven existing decisions were amended instead.

**OD-08 did not close then, and the residual stood at four parts** — band enumeration and meaning,
per-class and per-operation requirements, confirmation method strength and lifetime, and the
presentation-threshold default. Part (a) was blocked at the time: **OD-16's aggregation function had
to be settled first**, because a band cannot be named or calibrated before the value that produces it
is defined. **OD-16 was therefore the minimum next decision, and it was not closed here** — *it closed
subsequently as **DL-38**, and part (a) is now unblocked.*

**These decisions preempt nothing else.** **OD-43** still owns
surface perceptibility, **OD-52** still owns audience specification, **OD-57** still owns the
indication-versus-content boundary, **OD-67** still owns reasoning-provider strategy, **OD-71** still
owns audience-uncertainty policy, **OD-72** still owns unknown-actor correlation confidence, **OD-06**
still owns consent experience, and **OD-01** with **DL-31** still owns person-scoped connected
resources — a Person-anchored external account is referenced through its anchor, and **ownership is
never inferred from a connection's name**.

**One documentary bound applies.** **No confirmation mechanism is prescribed.** No companion
application, push confirmation, PIN, or secondary-factor capability has been verified against official
Home Assistant documentation, so stronger-than-verbal confirmation is described only as *available
where the platform genuinely supports it*. **OD-08(c) was not closed on an assumed mechanism.** *It was subsequently settled as **DL-40**, which classifies required strength without prescribing any mechanism.*

### Notes on the fusion decision

**DL-38 closes OD-16 without inventing mathematics.** The chosen function is **ordinal and stepped**,
not arithmetic. Additive scoring, weighted averaging, Bayesian fusion, and belief-combination models
were each evaluated and rejected on repository grounds: averaging **penalises a household for owning
fewer sources**, contradicting *missing evidence is not contradicting evidence*; probabilistic fusion
requires priors and an independence assumption the correlation rules explicitly deny, and would state
a **calibrated probability the home cannot support**; belief combination is not explainable in
household language. The stepped form is the **minimum** architecture satisfying every accepted
constraint at once.

**No responsibility, model, store, or file was created.** DL-38 is recorded inside the existing
Identity material. Every structure it uses already existed — the assertion purpose enumeration, the
five assertion states, the Identity Evidence Association, evidence families, the freshness,
correlation, contradiction, and absence sections, the fifteen-step fusion process, and the promotion
ladder. **DL-38 supplies the aggregation rules those sections were waiting for.**

**Zero new open decisions.** Everything left is **Fusion Policy configuration**: freshness durations,
step sizes, separation margins, per-purpose minimums, and reason-code strings. These are versioned,
governed, and household-configurable, and none is a materially distinct architectural question, so
none warrants an open decision of its own. Per the acceptance rule, **OD-16 is not held open for
operational tuning.**

**The OD-08 handoff is one-directional and now discharged.** DL-38 defines the *output semantics* — an
ordinal support level mapped to a confidence band through a versioned map, with **one enumeration
serving every assertion purpose**. **OD-08** names the bands and assigns operational meaning.
**OD-08(a) was unblocked and OD-08 became the minimum next decision.** Neither reopens the other, and
the former circular dependency is dissolved. *The bands were subsequently enumerated as **DL-39**.*

**Boundaries preserved rather than absorbed.** **OD-15** keeps assertion lifetime, which is not
observation freshness. **OD-72** keeps unknown-actor correlation, which has no candidate set, no
Person-to-source associations, and identifies nobody — **the fusion function must not be borrowed to
close it**. **OD-63** and **OD-64** keep behaviour attribution and native execution evidence, neither
of which is identity evidence. **OD-65** keeps learning eligibility, and a learned Fusion Policy
proposal never applies silently. **DL-36** and **DL-37** are untouched: fusion produces belief,
Operational Trust produces permission, and **confirmation is never an input**.

**One documentary bound applies.** **Native Room-level proximity detection and native managed-endpoint
human identity remain unverified.** This bounds a single evidence family's Room-Presence *ceiling* in
a given deployment; it does not bound the function, and fusion is deliberately designed against no
particular proximity implementation or voice provider.

### Notes on the confidence-band decision

**DL-39 completes the separation OD-08 was raised to settle.** Identity produces four bands and
nothing else. Operational Trust chooses among five requirement values, one of which is `None`. The
asymmetry is deliberate and is the whole decision: **four outputs, five requirements**, because *"no
identity is required here"* is a statement about a protected operation, never about a person.

**The rejected shape was a five-value band scale beginning at `None`.** It reads naturally and is
wrong in three ways. It puts a permission concept inside an evidence result. It makes *"identity was
not required"* indistinguishable from *"identity was evaluated and found absent"*. And it invites the
sentence *"High exceeded `None`, therefore the action was authorised"* — which manufactures an
identity dependency the policy does not have, and would make a correctly permitted action appear to
fail whenever identity happened to be weak.

**No band was given operational meaning.** A band says how strongly identity is supported for its
purpose. What that is *enough for* is a requirement, and every requirement is Operational Trust's.
This is DL-36 applied to the enumeration rather than restated beside it.

**The names were not allowed to hold the decision open.** The ordering, the semantics, the contract,
and the requirement values were fixed before the labels were chosen, and choosing them changed none
of it. **Low, Moderate, High, Very High** were adopted because they are already how this repository
and the household describe identity strength, because they read correctly in an explanation a
resident hears, and because **words resist arithmetic** where an ordinal numeral invites it. **A band
name applies only to a `known` Identity Assertion.** Truth facts, human-participant support, and
Unknown Actor correlation also speak of confidence; none of them carries an Identity band, and the
shared adjective never implies a shared scale.

**Three lifetime confusions are closed together.** Continuous occupancy is not continuous
authentication; a valid assertion is not the current-speaker assertion; and a confirmation is spent by
the operation that required it. Each of these, left implicit, produces the same failure — the home
keeps talking to someone who left. **No grace period, session, or presence-linked lifetime exists
anywhere in the model**, and sensor debouncing stays inside evidence freshness under DL-38 where it
belongs.

**Nothing was created.** No responsibility, no second confidence model, no second permission model, no
second confirmation model, no Identity session, no Identity Controller, no new precedence order, no
new file. **DL-36, DL-37, and DL-38 are intact and unamended**, and the Identity Fusion Function is
untouched. **DL-40 fills the enumeration slot DL-37 itself deferred**, which is completion, not
reopening.

**The last residual was a framing error, not a missing fact.** OD-08 held the **confirmation
method-strength enumeration** open as *documentarily bounded*, because no companion-application,
push, PIN, or secondary-factor mechanism has been verified against official Home Assistant
documentation. That bound is real and remains in force — **no mechanism may be prescribed until it is
verified** — but it never bound the architecture. **A required strength is a classification; an
implemented mechanism is a platform capability**, and only the second needs documentation. **DL-40**
settles the first: an ordered class set, a rule that the capability declares the class it requires, a
rule that only a verified mechanism satisfies a class, and `Unavailable` where none does. Mechanism
mapping is deployment configuration, not an open decision. **Per-class defaults were not treated as a
residual**; they are configuration resolved with OD-51. **OD-08 therefore closes.**

**OD-15 is amended for boundary only, and is not closed.** Validity is a window; applicability is a
question about *this* interaction. A window creates no permission and no confirmation persistence.

---

### Notes on capability dependency, storage, and artifact lifecycle

**DL-41, DL-42, and DL-43 answer three questions that the repository had never asked.** HTBW had a
rich model of *may this happen* and no model at all of *can this happen here*. It had a Connected
Storage principle and no statement of what Home Assistant already owns. It had per-artifact rules and
no requirement that an artifact declare a lifecycle before it exists. The three decisions close those
gaps in that order, and each depends on the one before it.

**They introduce no responsibility.** There is no Capability responsibility, no Storage
responsibility, no Artifact responsibility, no capability registry, no dependency registry, no
artifact registry, and no dependency broker. A declared dependency is a **property of a capability**,
owned by the responsibility that owns the capability, in the same way that a required Confirmation
Strength is a property of a protected operation under **DL-40**. Adding an owner would have been the
easy mistake and the wrong one.

**The dependency question is deliberately upstream of both identity and permission.** *Can this
happen at all* is answered before *who is this*, which is answered before *may this happen*. This
ordering is not a convenience; it is what prevents the two failure modes that motivated **DL-41**.
Rendering an absent integration as a refusal teaches a household that the home is withholding
something it could do. Rendering a policy denial as a missing feature teaches the opposite, and
invites someone to go looking for a configuration change that will never help. The five distinct
outcomes exist for the same reason: **a wrong explanation is a governance failure, not a wording
problem**.

**DL-42 states for storage what DL-31 stated for models.** It is the storage face of Home Assistant
First, not a new principle. Its sharpest clause is the one about justification: duplication requires
a **documented governed gap**, and a wish for longer retention is not a gap. That is precisely the
argument that would otherwise be used to build a second Recorder, and it is refused here in advance.
Where Connected Storage is absent, HTBW does not shrink into a local imitation of it — the dependent
capability is simply unavailable, and says so.

**External History Retention is one value on purpose.** A retention window and a purge window that
can drift apart become two policies, then a tier, then an archive, then a second retention model
inside the thing that was meant to extend the first. Collapsing them into a single configured period
makes that drift impossible to introduce accidentally. The period is a **ceiling**: it never
overrides a **P27** floor, and a Preservation Hold suspends it. **Purge cadence was deliberately left
unstated** — the repository has never accepted a runtime schedule as architecture, and this decision
does not become the first to do so.

**DL-43 is a burden-of-proof decision rather than a schema.** The declarations it requires are
questions, not fields, and their purpose is to make an undeclared lifecycle impossible to defend.
Two of them do the real work. *What happens when storage is lost after the artifact exists* is the
question that separates a governed artifact from an orphan, and it was the gap most likely to be
discovered in production rather than in review. *Does consent delete it* is the question that keeps
withdrawal from decaying into a visibility toggle.

**Projections were held apart from artifacts throughout.** An Evidence Package and a Historical
Reconstruction are assembled from governed records on demand, and neither becomes a store because it
was useful once. Only a deliberately saved copy is an artifact, and it then carries a full lifecycle
declaration of its own. A Preservation Hold is likewise a **marker on records**, never a duplicated
payload — the temporal-record rules already prohibited copying, and DL-43 does not quietly reopen it.

**Nothing here settles a mechanism.** Storage technology, layout, encryption, synchronisation,
recovery tooling, dependency health detection, purge scheduling, and reconciliation after storage
replacement all remain open, and are recorded as such against **OD-02**, **OD-03**, **OD-33**,
**OD-34**, **OD-36**, **OD-39**, **OD-40**, and **OD-67**. Each of those was amended for boundary
only. **None was closed**, because in every case the technical or policy question that kept it open
is still unanswered.

**Subsequently — OD-02 and OD-03 were closed by DL-44 and DL-45**, once the storage-provider
boundary was established and the residual questions were shown to be implementation mapping rather
than architecture. **OD-33 and OD-34 were later closed by DL-46 and DL-47**, on the retention and
persistence *model* rather than on any storage mechanism. The remainder of the list is unaffected,
and purge scheduling, recovery tooling, and reconciliation after storage replacement remain open.

---

### Notes on the storage-provider and cleanup decisions

**DL-44 removes a question HTBW should never have been asking.** Storage technology had been carried
as an open decision since the foundation, as though HTBW would one day choose between SMB and NFS.
Home Assistant already makes that choice, already mounts the share, already holds the credentials,
and already surfaces the result. **P21** had the answer the whole time; the decision only had to be
read. HTBW's ownership begins where Home Assistant's ends, and not one step earlier.

**The harder half of DL-44 is the sentence about access.** Persistence and user experience had
quietly blurred together, and the blur was about to produce a file browser. It is worth being
explicit about why that would have been wrong: a resident who must find a folder to reach a manual is
a resident the architecture has failed. **The Asset lists its documents. The profile owns its
voiceprint. A question retrieves history.** Storage is the floor, not the room.

**The My Media finding was deliberately written down at its true strength and no higher.** Home
Assistant documentation establishes that media directories are protected by **authentication** —
which is a real and useful property — and establishes nothing whatever about per-person
authorisation, nor about an unlisted file type being unreachable by every path. The same directories
are reachable through file-access apps. So the finding is recorded as a **visibility boundary**, and
**Operational Trust remains the security boundary**. It would have been easy, and wrong, to let a
convenient platform behaviour stand in for governance.

**OD-02 closed because its architectural content turned out not to be a schema.** The question was
*"what format?"*, but what HTBW actually needed was the ability to **find, govern, retain, and delete**
an artifact — and that is a reference contract, not a file format. A manual is a PDF because the
manufacturer made it one. A voiceprint is whatever its encoder produces. **Imposing one payload
schema across those would have been an architecture serving itself.** What remains is per-capability
encoding, which is implementation.

**OD-03 closed on the provider boundary plus nine namespace rules.** The rules that matter are the
negative ones: **no resident-supplied path as an identifier**, and **no display name as the only
storage key**. Both are how artifact stores become unrecoverable — someone renames a Room, and the
artifacts beneath it are orphaned by an operation nobody thought was destructive. Folder names stayed
implementation on purpose; **an architecture that names folders has started building a product**.

**DL-45 exists because absence of a rule is itself a rule.** With nothing stated, every artifact
would have survived its parent, and the store would have filled with material belonging to Assets
that no longer exist and People who have been removed. **The default is now cleanup, and continued
existence has to be argued for.** Two guards keep that from becoming its own hazard: a hold or a
retention floor always outranks it, and **cleanup is never reported successful when storage was
unavailable** — a claim of deletion is a claim about the world, and HTBW does not make one it cannot
support.

**Retention and parent cleanup were kept as two mechanisms on purpose.** A time window and a
governing object answer different questions, and collapsing them would mean either that deleting an
Asset silently waits for a purge cycle, or that a purge cycle silently deletes something still
owned. An object-scoped record class is simply subject to both.

**No new decision was created for pending cleanup.** The obligation to reconcile a deletion that
could not complete is the same obligation **OD-36** already carries, and inventing a second decision
for it would have split one question across two records. **OD-33, OD-34, OD-36, OD-39, and OD-40 were
narrowed and none was closed**, because storage placement was never what kept any of them open.
**OD-33 and OD-34 closed later, under DL-46 and DL-47, for entirely different reasons.**

---

### Notes on explainability persistence and retention

**DL-46 records a separation that was already true and had never been said in one place.** Home
Assistant retains what happened to the house; HTBW retains what the house made of it. Occupancy
became active, a voice interaction occurred, playback began — those are the platform's. That Tom was
supported as the current speaker at High confidence, that wearable and voice evidence contributed,
that music required no known identity, that identity nevertheless supported naming him in the reply —
**none of that exists anywhere in Home Assistant, and none of it can be recovered from a state
table.** That is the boundary, and it settles the retention argument as well: a longer retention
requirement never becomes a licence to copy the platform's history into HTBW's.

**The "bounded summary" turned out to be something the repository already had.** The review began
expecting to invent a way for a Decision Trace to stay meaningful after a native event ages out, and
found the answer already accepted: **the Fact is the summary.** Truth records the Subject, Statement,
confidence at the time, Provenance, evidence references, Coverage, and Freshness — *"the Den was
accepted as occupied"* — and it was never a copy of the sensor row. **No new construct was created,
because creating one would have quietly rebuilt the Recorder under a gentler name.**

**Significance needed no owner either.** The rule was already in the record boundary: *an occurrence
is evidence for an explanation; it is not automatically a Decision Trace*, and **HTBW never produces
a trace for a decision HTBW did not make**. A trace tracks a decision, not an event. Every proposal
for a significance threshold, a capture policy, or an event filter would have been a way of solving a
problem the boundary had already dissolved.

**The most important line in DL-46 is a prohibition on flattery.** A trace that says *"Tom was
recognised, therefore the music played"* is more satisfying than the truth, which is that the music
required no identity at all and would have played for anyone. **The home is not permitted the
flattering version.** Identity may be recorded as supporting attribution and named presentation; it
may not be dressed up as authorisation it never provided.

**DL-47 closed OD-33 by removing the thing OD-33 was asking for.** The decision wanted a retention
matrix — every record class down one axis, floors and ceilings across the other. Such a table would
have been obsolete the moment a capability declared a new record class, and it would have lived apart
from the classes it governed, which is how retention tables drift out of truth. **DL-43 had already
proved the better shape**: retention is declared inside the lifecycle, by whoever owns the class, and
a class with no declared retention is not accepted. DL-47 does nothing cleverer than apply that rule
to records as well as artifacts.

**Four floors survive any configured window, and they share one reason.** A Tombstone, a
consent-lifecycle record, a held record, and the versions that keep a held trace explainable are all
things whose removal would erase the evidence of the removal. **A purge that deletes the proof of the
purge has not enforced retention; it has covered its tracks.**

**OD-34 closed on a duplication, not on a discovery.** Its residual — *config entry, subentry, or
private storage* — was stated word for word in **OD-01**, which owns Home Assistant representation
and is where a representation question belongs. Two decisions holding one residual is not caution; it
is an ownership defect, and it kept OD-34 open long after the temporal-persistence model was
finished. **The repository's standing guard was honoured rather than removed**: the Storage helper
documentation is still unverified, so the guard was **re-pointed at OD-01**, where the unverified
dependency actually lives. OD-34 closed without relying on any assumption about it.

**One verified fact narrowed OD-01 on the way past.** Home Assistant documents config entries as
configuration data **created and removed by the user through the UI**, and subentries likewise.
**A store the resident can delete as configuration cannot hold immutable history** — so one of the
three candidates is now excluded on evidence rather than preference. The remaining choice still waits
on documentation that has not been found.

**OD-05, OD-26, and OD-49 were narrowed and left open.** Each now has its rule and lacks only its
value, which is a household configuration question. **No decision was created in this review**, and
the fourteen scenarios were added to an existing file rather than a new one.

---

## Part 3 — Recorded supersessions

| Superseded | Replaced by |
|---|---|
| The four-service platform model | [../architecture/north-star.md](../architecture/north-star.md), [../architecture/framework.md](../architecture/framework.md) |
| `canonical-architecture.md` | [../architecture/north-star.md](../architecture/north-star.md), [../architecture/framework.md](../architecture/framework.md), [../architecture/dependency-view.md](../architecture/dependency-view.md) |
| `adr-voice-identity-platform-service.md` | [../architecture/adr-identity-replaces-voice-identity-boundary.md](../architecture/adr-identity-replaces-voice-identity-boundary.md) |
| "Foundation owns truth" statements | [../contracts/truth-contract.md](../contracts/truth-contract.md) |
| `composite-room-contract.md` | [../contracts/room-configuration-contract.md](../contracts/room-configuration-contract.md) |
| `room-vocabulary-registry-contract.md` | [../contracts/contextual-vocabulary-contract.md](../contracts/contextual-vocabulary-contract.md) |
| `person-identity-contract.md`, `voice-recognition-contract.md` | [../contracts/identity-contract.md](../contracts/identity-contract.md) |
| *Notification* as an HTBW domain term | **Communication** (the object) or **Delivery** / **Delivery Attempt** (the act). See [../models/communication.md](../models/communication.md). Retained only as Home Assistant platform vocabulary. Formal supersession scope is **OD-58** |
| "Alias-first" as the **source of truth for household phrases**, in the subordinate pattern and philosophy documents | [../models/contextual-vocabulary.md](../models/contextual-vocabulary.md). Native aliases remain a **seed and a native execution target**; they are not the authority for household vocabulary. Resolved under **OD-14** |
| *Message* as an HTBW domain term | **Communication**. Retained only for external provider content where the provider is the system of record. Formal supersession scope is **OD-58** |
| The Concierge "Communication Model" delivery levels — Info, Attention, Urgent | The orthogonal **Category** and **Urgency** axes in [../models/communication.md](../models/communication.md) |
| "Operational Trust **enforces** what is appropriate", and the unqualified "Operational Trust determines what is appropriate" | **Operational Trust determines what is appropriate for this request, in this context**, paired with *the household defines what appropriate means*. Enforcement is execution and belongs to an executor. See [../models/operational-trust.md](../models/operational-trust.md) |
| "Care results in action when attention is required" | **Care creates an obligation when attention is required.** Whether an action follows is Operational Trust's, Concierge's, and the executor's. See [../models/stewardship.md](../models/stewardship.md) |
| "Stewardship determines what matters" | **The household declares what matters; Stewardship represents that declaration** as care expectations and evaluates observations against them. See [../models/stewardship.md](../models/stewardship.md) |
| "Room health" and "asset health" as state models | **Neither exists and neither may be invented** (**OD-69**). The constituent statements are a **Truth** Fact and a **Stewardship** obligation state, kept separate. *Room health* survives only in pre-refoundation and historical illustration documents |

The complete per-file disposition is in [document-register.md](document-register.md).

---

## Related documents

- [authority-order.md](authority-order.md)
- [open-decision-issue-index.md](open-decision-issue-index.md) — the canonical issue link for every open decision
- [document-lifecycle.md](document-lifecycle.md)
- [document-register.md](document-register.md)
- [../architecture/principles.md](../architecture/principles.md)
- [../models/temporal-record.md](../models/temporal-record.md)
- [../models/communication.md](../models/communication.md)
- [../architecture/adr-resident-communication-and-delivery-separation.md](../architecture/adr-resident-communication-and-delivery-separation.md)
