# Human Trust and Explainability

> **Document status: Canonical.**
> Explainability is cross-cutting architecture. It is not a North-Star framework layer.

---

## Human Trust is the outcome

| | Question | Nature |
|---|---|---|
| Operational Trust | What is allowed? | A governed responsibility |
| Human Trust | Can people rely on the environment? | An **outcome** |

Human Trust is produced by behavior that is understandable, consistent, respectful, and reliable.
It is never implemented directly, never configured, and never claimed.

A home that acts correctly but cannot explain itself does not earn Human Trust.

---

## The explainability requirement

**Every material Concierge decision must be explainable.** This includes:

- Actions taken
- Actions intentionally not taken
- Questions asked
- Communications originated, delivered, and **suppressed**
- Delivery attempts and their outcomes, including outcomes that are honestly **unknown**
- Transfers suppressed
- Automation refused
- Conflicts resolved
- Obligations escalated

**Explainability is not optional logging added later. It is an architectural requirement from the
beginning.**

### Explainability constrains how decisions are made, not only how they are recorded

A decision reached by a route that cannot be stated plainly is **not** rescued by a well-formed trace.
Two consequences follow, and both are already binding elsewhere:

| Requirement | Consequence |
|---|---|
| **Prefer an explicit classification over an inferred one** | *"You marked it private"* is verifiable by the resident; *"it looked sensitive"* is not. Operational Trust prefers explicit privacy markings, household-configured classifications, and declared source classifications over content interpretation or sensitivity inference. See [../models/operational-trust.md](../models/operational-trust.md) |
| **Prefer a stated requirement over a derived one** | A configured Required Identity Band can be quoted, versioned, and reviewed. An improvised threshold cannot |

**Predictability and auditability are explainability properties**, not implementation conveniences: the
same item, classified the same way, on every surface, every time — with a source, a version, and a
change record behind it.

---

## Decision Trace requirement

Every decision evaluation must be capable of producing a Decision Trace containing:

- Trigger
- Explicit request, if any
- Room or contextual origin
- Evidence considered
- Identity assertions considered
- Authoritative Truth facts used
- Continuity state used
- Stewardship obligations used
- Operational Trust policies evaluated
- Room modes evaluated
- Existing experiences evaluated
- Conflicts found
- Policy or priority that prevailed
- Decision
- Action or intentional non-action
- Human-readable explanation
- Confidence and uncertainty
- Relevant timestamps or validity periods
- Result
- Failure or fallback, if any

The structure is defined in [../models/decision-trace.md](../models/decision-trace.md).

---

## Questions the platform must be able to answer

- Why did this happen?
- Why did this not happen?
- Which policy took priority?
- What fact caused the decision?
- What would need to change for a different outcome?
- Was this explicitly requested, suggested, or autonomous?
- **What caused this?** — and, where the evidence supports it, *which automation or script did this?*
- **Why didn't you tell me?**

The last question matters as much as the others. A resident must always be able to tell whether the
home acted because it was told to, because it suggested and was approved, or because it was permitted
to act on its own.

### The record boundary

Four questions, four owners. **They are not interchangeable.**

| Question | Answered from | Owner |
|---|---|---|
| What facts were established, and when? | Facts and Fact history | Truth |
| What occurred in the environment? | **Domain Events**, referencing native Home Assistant records where they exist and are retained | The responsibility that observed the occurrence |
| Why did HTBW make, allow, suppress, defer, or refuse a governed decision? | The **Decision Trace** | Concierge |
| What version of a governed record existed at a given time? | **Temporal Records** | The responsibility owning the record |

> **An occurrence is evidence for an explanation. It is not automatically a Decision Trace.**
>
> **Do not convert temporal proximity into asserted causation.** That two things happened in
> sequence is an observation. That one caused the other is a claim, and a claim requires evidence.

**HTBW never produces a Decision Trace for a decision HTBW did not make.** Where a native automation,
an external integration, or a resident caused a change, the honest answer names what is known and
states what is not held.

### Conversation as the interaction path

Home Assistant Conversation and Assist — with custom sentences and custom intents — may be the
**native interaction and presentation path** for explainability requests: *"Why did you do that?"*,
*"Why did you not do that?"*, *"Why did you tell me?"*, *"Why did you not tell me?"*, *"What
happened?"*, *"What changed?"*, *"What caused this?"*, *"Which automation or script did this?"*

> **Conversation owns nothing.** Not facts, not occurrences, not history, not Decision Traces, and
> not authority. It is a way of asking and a way of answering.

| Concern | Authority |
|---|---|
| Facts and Fact history | Truth |
| What occurred | The observing responsibility, through Domain Events |
| Reconstructable historical versions | Temporal Records |
| Governed reasoning | Decision Traces |
| Whether this listener may receive this answer | Operational Trust |
| Assembling and presenting the answer | Concierge |

A reasoning provider may improve wording, summarisation, or presentation. **It must not fabricate
missing facts, causation, attribution, or authority.** Provider strategy is **OD-67**, and
governed conversational retrieval and command resolution is **DL-69** (resolved **OD-62**).

HTBW does **not** state that every explanation is AI-generated, and HTBW does **not** introduce a new
query language. The retrieval scopes above remain the model; Conversation is one surface onto them.

---

## Historical Explainability

**Explainability has a temporal dimension.** A home that can explain only its most recent decision
cannot account for itself. **P27** in [principles.md](principles.md) makes historical explainability
an architectural requirement.

The home must retain enough governed information to reconstruct what it observed, what it believed,
what it knew, what it decided, why it decided so, and why the alternatives were rejected — across
these retrieval scopes:

| Scope | Example question |
|---|---|
| A single decision | "Why did the music not follow me last night?" |
| A time range | "What happened in this home between Friday and Sunday?" |
| An incident retrieval scope | "Show me everything relating to the water leak." |
| A Room or Merged Room | "What changed about the Living Space configuration this year?" |
| An Asset | "What is the care and custody history of this instrument?" |
| A Person | "What does the home hold about me, and why?" |
| A **Communication** | "Why didn't you tell me the garage was open?" |
| A correlation or causation chain | "What else followed from that request?" |
| A **location conclusion** | "Why do you think Tom is in the Den?" · "Why can't you tell me where my phone is?" |

### The location retrieval scope

A location answer must be explainable to the evidence that produced it, and **its refusals and
uncertainties must be as explainable as its conclusions**.

| Question | Answered from |
|---|---|
| Why do you believe that? | The Location Fact's provenance and, for a **Person** subject, the referenced Identity Assertion with its supporting and contradicting evidence families |
| Why are you not sure? | The conflict record — contradicting evidence is **preserved, never averaged away** |
| Why won't you say? | The **disclosure** decision, recorded separately from the access decision (**DL-34**) |
| Why don't you know which room? | The **granularity basis** — where only zone-level evidence exists, the home says so rather than guessing a Room |
| Where was it before? | Truth's Fact history. **A Historical Fact is never presented as current** |

> **Access to movement histories and reconstructions is governed by Operational Trust and must not be
> reachable through generic Room Help or a general-question capability** (**DL-35**, **OD-35**).

### The communication retrieval scope

*"Why didn't you tell me?"* is answered from governed Communication records:

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

See [../models/communication.md](../models/communication.md).

### Historical Explainability is cross-cutting, not a responsibility

Historical Explainability **assembles** governed historical records held by their canonical owners.
**It owns no historical store, duplicates no responsibility, and creates no new responsibility.**
Truth owns Fact history; Stewardship owns obligation history; Continuity owns preference and session
history; Operational Trust owns policy history; Room Configuration owns configuration history;
Concierge owns decision history, **including communication delivery history**. See
[framework.md](framework.md).

### Explanations must survive change

Under **P30**, a Decision Trace references the **exact versions** of the Facts, assertions, policies,
obligations, preferences, sessions, configuration, and vocabulary it used. An explanation must
therefore remain accurate after the current configuration or policy has changed. An explanation that
silently re-reads today's policy to describe last month's decision is a defect.

### Limitations must remain explainable

Retention is a **floor as well as a ceiling**. Where privacy requires removal or redaction, the
resulting limitation must itself remain explainable. The home says *"I no longer hold that record"*
rather than falling silent or, worse, implying that nothing happened.

A historical reconstruction containing an **unreported gap** is a defect. See
[../models/temporal-record.md](../models/temporal-record.md) and [privacy.md](privacy.md).

---

## Two paired forms

Every explanation exists in two paired forms. Neither is sufficient alone.

| Form | Purpose | Audience |
|---|---|---|
| Machine-readable | Diagnostics, assessment, validation, auditing, regression detection | Tools, maintainers, the assessment workbook |
| Human-readable | Understanding and trust | Residents |

The human-readable form is derived from the machine-readable form. It must never assert something
the trace does not support.

---

## Example

> "Your Jazz session is configured to follow you. It did not move into the Kitchen because music was
> already playing there, and the current policy gives the existing room experience priority."

This single sentence contains:

| Element | Source |
|---|---|
| An active session with Follow-Me intent | Continuity |
| The destination Room | Room Configuration and Truth |
| Music already playing there | Truth |
| Existing-experience priority | Operational Trust policy |
| The intentional non-action | Concierge decision |

---

## Explanation quality rules

1. **Name the fact, not the mechanism.** "Music was already playing" — not "the destination state
   evaluation returned occupied-media".
2. **Name the governing policy in household terms.** Residents must be able to find and change it.
3. **State uncertainty when it existed.** "I was not certain it was you" is a valid explanation.
4. **Explain non-actions with the same care as actions.**
5. **Say what would change the outcome** when the resident asks, and when the trace supports it.
6. **Never fabricate a reason.** If the trace is incomplete, say so.

---

## What is persisted for explanation, and what is never persisted

**Home Assistant retains what happened to the house. HTBW retains what the house made of it.**
Entity and device states, state changes, native events, occupancy and motion, media-player state,
Person and Device Tracker state, natively provided automation activity, and Recorder history are the
platform's, and HTBW **consumes them by governed reference rather than copying them** (**DL-46**).

What HTBW persists is what the platform does not represent at all: **purpose-specific Identity
Assertions and safe evidence summaries, Decision Traces, Operational Trust evaluations, policy
outcomes, attribution, explicit Change Records, capability-dependency outcomes, audience and
disclosure outcomes, governed non-actions, reason codes, historical policy and Fusion Policy
versions, Tombstones, and broken-reference state.**

**A longer retention requirement is never authority to copy native history.** HTBW does not retain
every state transition, Recorder row, automation trace, sensor payload, voice interaction, or
provider response. **Durable explanation after native expiry needs no copy**: the accepted Fact that
Truth recorded — its Statement, confidence at the time, Provenance, and Freshness — carries what was
material to the decision, and a purged native reference resolves to *"no longer retained"*, never
*"never existed."*

### Explainability is a governed record, not a reasoning log

**HTBW must never persist private internal deliberation.** Chain-of-thought, hidden prompts,
unrestricted model reasoning, raw provider deliberation, provider secrets, biometric internals,
voiceprint vectors or embeddings, raw voice recordings, unnecessary conversation transcript, and
unnecessary raw sensor payloads are all outside the record.

**The governed reason for a decision is not the same thing as the private route to it.** A trace
states the request, the Facts consulted, the identity determination as bands and evidence classes,
the policies evaluated, the conflicts and alternatives, and the outcome. **The explanation must
remain truthful after every sensitive detail is redacted** — if it does not, the explanation was
resting on something it should never have retained.

**Where identity was not required, the explanation says so.** It may record that identity supported
attribution or named presentation, and it must **never imply that identity authorised an operation
that required none**. The flattering version of a decision is not permitted to displace the accurate
one.

---

## Privacy constraints on explanation

An explanation must not disclose information the listener is not permitted to receive.

- A guest asking why a light did not turn on must not learn a resident's calendar contents.
- An explanation may state that a policy prevented an action without naming a protected fact.
- Decision Trace visibility and retention are Operational Trust policy decisions.

See [privacy.md](privacy.md).

---

## Where explainability is produced

| Responsibility | Contribution to the trace |
|---|---|
| Foundation / Room Configuration | Resolved Room Context, resolved vocabulary target set, participation and exposure state |
| Identity | Candidate person, confidence, contributing evidence, reason code |
| Truth | Facts used, provenance, confidence, freshness, validity |
| Continuity | Preferences, active sessions, transfer or resume intent |
| Stewardship | Obligations considered and their state |
| Operational Trust | Policies evaluated, thresholds applied, ceiling in force, prevailing priority |
| Concierge | Conflicts found, decision, action or intentional non-action, both explanation forms |
| Concierge | Communications originated, suppressed with reason, attempted, delivered, presented or `unknown`, acknowledged, expired, and superseded |

**Concierge owns the trace. Concierge does not own the contents contributed by other
responsibilities.**

---

## Related documents

- [../models/decision-trace.md](../models/decision-trace.md)
- [../models/temporal-record.md](../models/temporal-record.md)
- [../models/communication.md](../models/communication.md)
- [behavioral-governance.md](behavioral-governance.md)
- [failure-and-degradation.md](failure-and-degradation.md)
- [adr-historical-explainability-and-historical-truth.md](adr-historical-explainability-and-historical-truth.md)
- [adr-resident-communication-and-delivery-separation.md](adr-resident-communication-and-delivery-separation.md)
- [../scenarios/why-did-this-happen.md](../scenarios/why-did-this-happen.md)
