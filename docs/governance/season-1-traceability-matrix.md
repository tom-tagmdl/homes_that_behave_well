# Season 1 Narrative-to-Architecture Traceability Matrix

> **Document status: Operational.**
> A **traceability artifact**. It maps published Season 1 narrative to accepted architecture so that
> coverage and gaps are visible.
> **This document creates no authority, decides nothing, and classifies nothing the repository has not
> already classified.** Where it disagrees with [decision-ledger.md](decision-ledger.md),
> [authority-order.md](authority-order.md), or any canonical model or contract, **those prevail and
> this document is wrong**.
> Compiled 2026-09-08. **It is a snapshot and it will go stale.**
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Evidence limits, stated first

**The episodes themselves were not accessible to this review.** `youtube.com` returned **HTTP 401** for
both the channel video list and a specific episode URL.

Everything in the *Episode* columns below is taken from the **Homes That Behave Well website**
(`/education` and `/framework`), which is authoritative for **its own summaries of its own episodes**
but is **not the episode**. **No transcript, narration, or production document was reviewed.**

Consequently:

- **Scene-level and use-case-level traceability cannot be established from published evidence.**
  Where this matrix records use cases, they come from the **repository's own canonical scenario
  documents**, not from the episodes.
- **The chain is therefore bounded**: `Season → Episode → Responsibility → Repository artefact → Issue`
  is supported. `Episode → Scene → Use case` is **not**, except where a repository episode-validation
  record already made that link.
- **This is a coverage limit, not a finding of absence.** The episodes may well contain material this
  matrix cannot see.

---

## Season 1 structure, as published

Eleven episodes. Titles and responsibility labels verbatim from `/education`.

| # | Published title | Published label | Repository artefact | Validation issue | Episode evidence |
|---|---|---|---|---|---|
| 1 | *Why Do Intelligent Homes Still Feel Dumb?* | `HUMAN TRUST` | **None** | — | **Not accessible** |
| 2 | *What Is a Home Operating System?* | `OPERATING MODEL` | **None** — and *Home Operating System* has **zero** repository occurrences | — | **Not accessible** |
| 3 | *How Does a Home Know What Is True?* | `TRUTH` | **None** | — | **Not accessible** |
| 4 | *How Does a Home Know It Is Me?* | `IDENTITY` | `decision-ledger.md` — *Notes on the Episode 4 and Episode 5 narrative-validation clarifications* | — | **Not accessible** |
| 5 | *How Does a Home Know What Is Allowed?* | `OPERATIONAL TRUST` | same Notes subsection | — | **Not accessible** |
| 6 | *How Does a Home Know What Matters?* | `STEWARDSHIP` | `decision-ledger.md` — *Notes on the Episode 6 narrative-validation clarifications*; `scenarios/stewardship-use-cases.md` (S1–S8) | **#75** | **Not accessible** |
| 7 | *Why Does the Home Remember?* | `CONTINUITY` | `scenarios/continuity-use-cases.md` (CU1–CU15) | **#151** | **Not accessible** |
| 8 | *What Should Happen Next?* | `CONCIERGE` | `scenarios/concierge-use-cases.md` (C1–C20); ledger *Notes on the Episode 8 Concierge narrative validation* | **#170** | **Not accessible** |
| 9 | *Why Did That Happen?* | `EXPLAINABILITY` | **No scenario artefact.** `architecture/explainability.md`, `models/decision-trace.md`, `scenarios/why-did-this-happen.md` exist but were not produced by Episode 9 | **#173** | **Not accessible** |
| 10 | *Why Do Intelligent Homes Need Governance?* | `GOVERNANCE` | `decision-ledger.md` — *Notes on the Episode 10 governance narrative validation*; **OD-86**, **OD-87** | **#173** | **Not accessible** |
| 11 | *Can a Home Accumulate Technical Debt?* | `TECHNICAL DEBT` | **None. Zero repository occurrences of Episode 11, and no debt construct exists** | **None** | **Not accessible** |

**Coverage: 5 of 11 episodes have a repository artefact. 6 of 11 have none.**

---

## Traceability chain — what is supported and what is not

| Chain link | Supported? | Where it lives |
|---|---|---|
| Season → Episode | **Yes** | This matrix, from `/education` |
| Episode → Responsibility | **Yes** | Published episode labels, which match **DL-01** responsibility names for Episodes 3–8 |
| Episode → Scene or scenario | **No** | **Episodes not accessible.** No production documentation is in the repository |
| Scenario → Use case | **Partial** | Only for Episodes 6, 7, 8, which produced `docs/scenarios/*-use-cases.md` |
| Use case → Household outcome | **Yes**, where a use case exists | The use-case documents carry outcomes |
| Use case → Responsibility | **Yes** | Use-case documents name owning responsibilities |
| Use case → Cross-cutting concern | **Yes** | Use-case documents name them |
| Use case → Principle | **Partial** | Named where material; not exhaustively mapped |
| Use case → ADR or accepted decision | **Yes** | Use-case documents cite DL identifiers |
| Use case → Contract or model | **Yes** | Cited in the use-case documents |
| Use case → Home Assistant native capability | **Partial** | `home-assistant-boundary.md` holds the capability reviews; per-use-case mapping is incomplete and is **#146**'s work |
| Use case → HTBW differentiated requirement | **Yes** | Recorded per use case |
| Use case → Implementation component | **Not applicable** | **HTBW Core contains no code files.** No use case may be classified `Implemented` |
| Use case → Test | **Not applicable** | Same reason |
| Use case → GitHub issue | **Yes** | Use-case documents and `open-decision-issue-index.md` |
| Use case → Acceptance evidence | **No** | **No acceptance review has been completed for any Season 1 use case** |

**Two links are permanently unavailable in their current form** — implementation component and test —
**because HTBW Core has no code.** That is a correct and expected state under **DL-19**, not a defect.

---

## Canonical Season 1 use-case inventory

**The repository already holds the canonical catalog.** This matrix does **not** create a second one.
It records what exists, so the gap is visible.

| Catalog | Identifiers | Count | Source episode | Status |
|---|---|---|---|---|
| `scenarios/concierge-use-cases.md` | **C1–C20** | 20 | Episode 8 | Canonical scenario |
| `scenarios/continuity-use-cases.md` | **CU1–CU15** | 15 | Episode 7 | Canonical scenario |
| `scenarios/stewardship-use-cases.md` | **S1–S8** | 8 | Episode 6 | Canonical scenario |
| `scenarios/follow-me-media.md`, `multi-person-conflict.md`, `nighttime-suppression.md`, `room-vocabulary.md`, `stewardship-obligations.md`, `where-is-tom.md`, `where-is-maisey.md`, `where-is-my-phone.md`, `why-did-this-happen.md` | unnumbered `Scenario N` | 18 scenarios | Pre-episode and cross-episode | Canonical scenarios |

**Total: 43 identified use cases plus 18 named scenarios.**

**Missing catalogs: Truth (Episode 3), Identity (Episode 4), Operational Trust (Episode 5),
Explainability (Episode 9), Governance (Episode 10), Technical Debt (Episode 11), and Foundation —
which has no episode at all.**

### Maturity distribution, from the accepted baseline

`season-1-architectural-baseline.md` §5 classifies the twenty Concierge use cases. **Reproduced, not
re-derived:**

| Class | Count | Use cases |
|---|---|---|
| **A — Implemented** | **0** | — |
| **B — Architecturally supported** | 6 | C3, C4, C9, C12, C19, C20 |
| **C — Planned** | 0 | — |
| **D — North Star** | 1 | C1 |
| **E — Blocked** | 12 | C2, C6, C7, C8, C10, C11, C13, C14, C15, C16, C17, C18 |
| **F — Research required** | 1 | C5 |

**Zero implemented behaviours.** Every Season 1 behaviour is architecture, plan, or open question.
**No public material may present any of them as a current product capability** — see
[public-claim-register.md](public-claim-register.md).

---

## Episodes 10 and 11 — the specific question

**Episode 10 — Governance.** **It did add architecture.** Evidence: `decision-ledger.md` *Notes on the
Episode 10 governance narrative validation* records that **fifteen concepts** were tested, and the
episode produced **two new open decisions**:

- **OD-86** — Vocabulary Change and Term-Withdrawal Consequences (**#174**). A **real defect**: managed
  vocabulary lifecycle existed in three now-Historical documents and **was not carried forward**.
- **OD-87** — Identity Artifact Invalidation as a Governed Household Event (**#175**).

It also produced **#176** (workbook not under governance) and **#177** (assessment-record routing).
**Episode 10 did not merely synthesise. It exposed a carried-forward gap.**

**Episode 11 — Technical Debt.** **Not assessed, because no evidence was accessible and the repository
holds nothing.** What *is* established:

- `Episode 11` has **zero** repository occurrences.
- **No Technical Debt construct exists**, and `decision-ledger.md` states affirmatively that *"**No
  debt construct is created**"*, with the word appearing normatively **exactly once** — **P24**.
- Yet **Technical Debt is published as one of three cross-cutting capabilities** of the framework, with
  its own page and its own episode.

**This is a genuine, currently-unresolved divergence between a published framework capability and
accepted repository governance.** It is **not** resolved by this matrix and **no identifier is
allocated for it here.**

---

## What Season 1 did to the framework

| Question | Evidence-based answer |
|---|---|
| Was a **new responsibility** discovered? | **No.** Measured 2026-09-08: `seven responsibilit` appears throughout the constitutional set — **DL-01**, `adr-htbw-core-refoundation.md`, `north-star.md`, `authority-order.md`, `README.md` — while `six responsibilit` appears in **no** canonical, constitutional, or architecture document, and occurs only where this review quotes the public finding. **DL-01** is unchanged from refoundation through Episode 10 |
| Did a **responsibility boundary** materially change? | **No.** Every episode review resolved to *consume a native capability*, *record a distinction*, or *govern an existing capability more precisely* |
| Was an **accepted constitutional decision invalidated**? | **No.** One was **closed by resolution** — **OD-82** became **DL-51** and **DL-52** |
| Did **late-season stories require new architecture**? | **Episode 10: yes** — two new open decisions, one of them a carried-forward defect. **Episode 11: unknown**, no evidence accessible |
| Is **ownership** clear? | **Yes within the repository.** **No publicly** — Foundation is absent from the public framework |
| Is there **hidden eighth-responsibility risk**? | **Yes, from public material, not from the repository.** `Technical Debt`, `Governance`, and `Home Operating System` are presented publicly as framework-level capabilities. The repository governs `Governance` as a **process**, refuses a `debt` **construct**, and has **no** `Home Operating System` concept |

---

## Related documents

- [public-claim-register.md](public-claim-register.md)
- [season-1-architectural-baseline.md](season-1-architectural-baseline.md)
- [decision-ledger.md](decision-ledger.md)
- [open-decision-issue-index.md](open-decision-issue-index.md)
- [../scenarios/README.md](../scenarios/README.md)
