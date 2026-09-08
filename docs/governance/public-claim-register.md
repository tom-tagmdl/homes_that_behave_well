# Public-Claim Register

> **Document status: Operational.**
> A **traceability register** linking material public claims to repository authority.
> **This document creates no authority and decides nothing.** It does not accept a public claim as
> architecture, and it does not amend a public claim. Where it disagrees with
> [decision-ledger.md](decision-ledger.md), [authority-order.md](authority-order.md), or any canonical
> model or contract, **those prevail and this document is wrong**.
> Compiled 2026-09-08. **It is a snapshot and it will go stale.**
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Why this register exists

Public material sits at **rank 8** in [authority-order.md](authority-order.md) — it is evidence, use
cases, terminology, and public expectation. **It does not override accepted repository architecture.**
But a public statement a reasonable reader could read as a present capability, an implementation
commitment, or a governance guarantee **is a claim the repository should be able to trace**.

This register records the trace. **Where the trace fails, that is a finding, not a decision.**

---

## Alignment statuses used

`Aligned` · `Aligned but aspirational` · `Partially governed` · `Missing repository traceability` ·
`Public wording requires clarification` · `Repository documentation requires clarification` ·
`Architectural contradiction` · `Requires further evidence`

---

## 1. Material findings, in severity order

### F1 — The public framework states **six** responsibilities; the repository accepts **seven**

| Field | Value |
|---|---|
| **Source** | `https://www.homesthatbehavewell.com/framework` |
| **Exact claim** | *"Six connected responsibilities. One earned outcome."* The page then lists **Truth, Identity, Operational Trust, Stewardship, Continuity, Concierge**, with **Human Trust** as `OUTCOME`. |
| **Tense** | Present, definitional |
| **Architectural owner** | Constitutional — the framework itself |
| **Governing artifact** | **DL-01**: *"HTBW Core is defined by **seven responsibilities**: Foundation, Stewardship, Identity, Truth, Continuity, Operational Trust, Concierge."* Also `adr-htbw-core-refoundation.md` L35, `north-star.md` L32, `authority-order.md` L34, `README.md` L20 |
| **Implementation status** | Not applicable — this is a definitional claim |
| **Related issue** | New public-contract issue |
| **Alignment status** | **Architectural contradiction** |
| **Required remediation** | **Public.** `Foundation` is absent from the public framework entirely — it has no page, no episode, and no listing. Foundation owns the descriptive substrate: Rooms, Room Configuration, Contextual Vocabulary, the Person reference, and the shared temporal, version, change-record, snapshot, correlation, and provenance models. **A public reader cannot discover it.** |

**Note:** measured 2026-09-08 across all repository markdown, the phrase `six responsibilit` appears in **no**
canonical, constitutional, or architecture document — its only occurrences are in this register and in
[season-1-traceability-matrix.md](season-1-traceability-matrix.md), both of which quote it as a public
finding. `seven
responsibilit` appears **13** times across constitutional documents. **The repository is internally
consistent. The public material is not consistent with it.**

### F2 — The public site contradicts itself on the same point

| Field | Value |
|---|---|
| **Source** | `https://www.homesthatbehavewell.com/ideas/blog/building-htbw-when-a-framework-meets-reality` (2026-09-08) |
| **Exact claim** | *"Those observations eventually became the seven responsibilities of **Foundation, Stewardship, Identity, Truth, Continuity, Operational Trust, and Concierge**."* |
| **Alignment status** | **Aligned** — this is **DL-01** verbatim, in the correct order |
| **Required remediation** | **None for this post.** It is the `/framework` page that diverges. Recorded here because it **proves the seven-responsibility model is the intended public position** and that F1 is a page-level defect rather than a change of doctrine. |

### F3 — **Technical Debt** is a public first-class framework capability with **no repository construct**

| Field | Value |
|---|---|
| **Source** | `/framework` cross-cutting list; `/framework/technical-debt`; Episode 11 *"Can a Home Accumulate Technical Debt?"*; `/ideas/blog/the-hidden-inventory` |
| **Exact claim** | *"TECHNICAL DEBT — What does this choice cost later?"*, presented alongside Explainability and Governance as a cross-cutting capability of the framework |
| **Tense** | Present, definitional |
| **Governing artifact** | **There is none.** `decision-ledger.md` states the opposite: *"**No debt construct is created.** Experience debt, vocabulary debt, identity debt, and migration debt are admitted as **narrative and review lenses only**. The word appears normatively in this repository exactly once — **P24, greenfield without compatibility debt**."* |
| **Implementation status** | No model, no contract, no ADR, no owner |
| **Alignment status** | **Architectural contradiction** |
| **Required remediation** | **Governed disposition required.** Either the repository accepts a Technical Debt construct — which reverses an explicit ledger statement and needs formal governance — or the public material presents it as a **review lens and household-facing teaching concept** rather than a framework capability. **This review recommends neither and decides neither.** |

### F4 — **Home Operating System** is a public first-class concept with **no repository representation**

| Field | Value |
|---|---|
| **Source** | Homepage section *"The Home Operating System"*; Episode 2 *"What Is a Home Operating System?"* (`OPERATING MODEL`); the category label on two published posts |
| **Exact claim** | *"A Home Operating System is not a product you buy. It is the residential technology architecture and smart home governance discipline used to coordinate how technology understands, decides, acts, explains, and changes over time."* |
| **Tense** | Present, definitional |
| **Governing artifact** | **None.** The string `Home Operating System` appears **zero** times in the repository. The only near match is *"Home Assistant Operating System"* in `connected-storage.md`, which is HAOS and unrelated |
| **Alignment status** | **Missing repository traceability** |
| **Required remediation** | Determine whether *Home Operating System* is (a) a public synonym for the Behaves Well Framework, (b) a distinct governed concept requiring a glossary entry, or (c) educational framing that should carry no architectural weight. **Not decided here.** The name-collision risk with **HAOS** is a second, independent reason to settle it. |

### F5 — **Observability** is a public architectural concept naming HTBW's **Explainability**

| Field | Value |
|---|---|
| **Source** | `/ideas/blog/what-is-observability-in-a-home` (2026-09-04) |
| **Exact claim** | *"Observability is the discipline of closing that gap so the Home can explain its behavior and earn trust over time"*; *"Monitoring tells us what happened. Observability helps us understand why."* |
| **Governing artifact** | `architecture/explainability.md` (Canonical) is the accepted owner of *why did that happen*. `Observability` appears in the repository only in **subordinate and operational** documents — `platinum-target-checklist.md` §4, `voice-enrollment-modernization-roadmap.md`, `temporary-artifact-lifecycle-pattern.md`, and *"satellite state observability"* — **never as an HTBW architectural concept** |
| **Alignment status** | **Public wording requires clarification** |
| **Required remediation** | **Two public terms name one governed concept.** The site itself uses `Explainability` on `/framework`. Either treat `Observability` as an explicitly-labelled synonym for teaching purposes, or retire it publicly. **Do not add it to the glossary as a second concept.** |

### F6 — A public statement reorders the framework and again omits Foundation

| Field | Value |
|---|---|
| **Source** | `/ideas/blog/what-is-observability-in-a-home` |
| **Exact claim** | *"This is one of the reasons **Truth became the first responsibility** in the Behaves Well Framework™."* |
| **Governing artifact** | **DL-01** framework order begins with **Foundation**; `README.md` L20 *"seven responsibilities, in framework order"*; `foundation-contract.md` L14 *"Foundation is the descriptive substrate of the framework"* |
| **Alignment status** | **Architectural contradiction** — same root cause as **F1** |
| **Required remediation** | Public correction, or an explicit public statement that Truth is the first responsibility **that answers a household question**, with Foundation named as the substrate beneath it. |

### F7 — The store advertises a **Voice Identity** playbook for a product **DL-51 sunsets**

| Field | Value |
|---|---|
| **Source** | `/store` |
| **Exact claim** | *"**Voice Identity Implementation & Integration Playbook** — $49 — **Coming soon** — A practical guide for creating voice experiences that use identity evidence, confidence, context, consent, and household boundaries appropriately."* Listed alongside *"Asset Intelligence Implementation & Integration Playbook — $49 — Coming soon"* |
| **Tense** | **Future, with a price and a product name** — a commercial commitment |
| **Governing artifact** | **DL-51**: *"Product disposition is stated per product, never for the portfolio."* **Asset Intelligence remains a released standalone integration; Voice Identity and Concierge standalone integrations sunset.** Recorded in `adr-product-disposition-and-legacy-adoption.md` (Accepted) |
| **Implementation status** | Asset Intelligence: released, v1.0.12. Voice Identity: one release, v0.1.0, **sunsetting** |
| **Related issue** | **#171**, **#160**, **#172** |
| **Alignment status** | **Architectural contradiction** |
| **Required remediation** | The **Asset Intelligence** playbook is consistent with DL-51. The **Voice Identity** playbook advertises an implementation and integration guide for a product the repository has decided to sunset, and **Identity is a responsibility, not a product** (`adr-identity-replaces-voice-identity-boundary.md`). **This is the most commercially consequential misalignment in the register.** |

### F8 — The governing development law does not appear in the public framework

| Field | Value |
|---|---|
| **Source** | Site-wide |
| **Finding** | *"HTBW extends Home Assistant. It does not compete with Home Assistant."* appears **once**, in the Building HTBW blog post — **verbatim and correctly framed**. It appears **nowhere** on `/`, `/framework`, `/about`, `/education`, `/store`, or `/advisory` |
| **Counter-positioning** | The homepage states *"**Vendor-Neutral and Platform-Independent** — We do not sell devices and do not maintain preferred-vendor relationships"* and *"A well-designed Home should outlast any single vendor, platform, protocol, subscription, or technology generation."* The advisory intake form lists **Home Assistant as one option among Control4, Crestron, Savant** |
| **Governing artifact** | **P21** Home Assistant First; **DL-16**; **DL-30**; **P25**, which forbids binding the architecture to one topology |
| **Alignment status** | **Repository documentation requires clarification** |
| **Required remediation** | **These are not necessarily in conflict, and the repository has never recorded which scope each statement has.** The defensible reading is that the **Behaves Well Framework is platform-neutral** while **HTBW Core, the software, extends Home Assistant** — but **no repository document states that distinction**, and no public page states it either. **This is a repository gap first and a public gap second.** |

---

## 2. Claims assessed as aligned

| Source | Claim | Governing artifact | Status |
|---|---|---|---|
| `/framework` | **Human Trust** presented as `OUTCOME`, not as a responsibility | **P19** — human trust is an earned outcome, not a responsibility | **Aligned** |
| `/framework` | Explainability and Governance shown as **cross-cutting**, not as responsibilities | Accepted cross-cutting treatment; **DL-15** | **Aligned** for Explainability; see **F3** for the third item |
| Building HTBW | *"If Home Assistant already solves a problem well, HTBW should get out of the way… If Home Assistant provides a capability, HTBW should reuse it."* | **P21**, **DL-30** ordered burden of proof | **Aligned** — this is DL-30 stated in plain language |
| Building HTBW | *"Features we once thought we might need to build ourselves are increasingly appearing as native platform capabilities. Every time that happens, we consider it a success."* | **#146 item 11 step F** — *HTBW builds nothing* is a passing outcome | **Aligned**, and unusually well aligned |
| Building HTBW | *"How does a home determine who it is interacting with when no one has explicitly logged in?"* | **DL-06**, **DL-32**, **DL-38**, **DL-39**; **OD-63** (#128) | **Aligned but aspirational** — correctly posed as an open question |
| `/about` | *"Explainability Is Not Optional"* | **P27**, **P28**, `explainability.md` | **Aligned** |
| `/advisory` | Consent checkbox: *"the Home Architecture Assessment is a consulting and advisory engagement and **does not include implementation services**"* | Not an architecture claim | **Aligned** — an explicit scope limit, correctly stated |
| `/education` | *"Courses… are in development"*; store items marked **Coming soon** / **Planned** | Not architecture claims | **Aligned but aspirational** — **correctly labelled**, and this is the pattern **F7** should follow |
| `/ideas/blog/the-hidden-inventory` | *"A trustworthy Home understands who can act, what authority has been granted, why that authority exists, and when it should come to an end"* | **OD-15** Identity Assertion Lifetime (#96); `operational-trust.md` | **Aligned but aspirational** — substance is right; it is not implemented |

---

## 3. Claims requiring further evidence

| Source | Claim | Why unresolved |
|---|---|---|
| `/ideas/blog/what-is-observability-in-a-home` | *"The music followed someone into the room because the Home understood who was there."* | Present tense, illustrative. Corresponds to `scenarios/follow-me-media.md`, which is **Canonical** but **not implemented** — HTBW Core contains no code. **Requires further evidence** that a reader understands this as illustration rather than product behaviour |
| `/store` | **Home Architecture Assessment Workbook v1.1**, $79, *"Available now"* | The workbook is **paywalled and was not accessible to this review**. `north-star.md` L52 references it; it is **absent from the repository** (**#176**). Its doctrine, responsibility definitions, and terminology are therefore **NOT VERIFIED** |
| Season 1, Episodes 1–11 | All episode content | **YouTube returned HTTP 401 to this review.** Episode titles, responsibilities, and descriptions were taken from the **HTBW website**, which is authoritative for its own summaries but is **not the episode itself** |
| `/framework/technical-debt`, `/framework/human-trust`, and the six responsibility pages | Full page content | **Not individually fetched.** Only `/framework` and `/framework/governance` were retrieved. Claims on the per-responsibility pages are **NOT VERIFIED** |

---

## 4. What this register deliberately does not do

- It **does not amend any public material.** Published articles are not rewritten by a repository review.
- It **does not accept any public claim as architecture.**
- It **does not create, rename, or retire a responsibility, a construct, or a term.**
- It **allocates no open-decision identifier.** Two findings — **F3** and **F4** — may warrant one, and
  allocation requires a ledger row first under the ledger's own maintenance rules.

---

## Related documents

- [authority-order.md](authority-order.md) — public material is rank 8
- [decision-ledger.md](decision-ledger.md) — **DL-01**, **DL-51**, **P24** debt statement
- [season-1-traceability-matrix.md](season-1-traceability-matrix.md)
- [season-1-architectural-baseline.md](season-1-architectural-baseline.md)
- [../architecture/principles.md](../architecture/principles.md) — **P19**, **P21**, **P24**, **P25**
