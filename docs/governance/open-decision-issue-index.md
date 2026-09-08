# Open Decision Issue Index

> **Document status: Canonical governance.**
> Authority: [authority-order.md](authority-order.md). Decisions: [decision-ledger.md](decision-ledger.md).
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Purpose

**GitHub issues are the authoritative source for the current status, remaining questions,
dependencies, and closure evidence of open architecture decisions.**

**Repository architecture documents remain authoritative for accepted architecture.**

This index is the bridge between the two. It records, for every open decision, only what a governance
document should carry: identifier, title, status, the canonical issue link, a dependency summary, and
the accepted or superseding authority. **It does not restate the issue.** The issue holds the
architectural context, the remaining questions, the options, the acceptance criteria, and the exit
criteria.

Accepted decisions — **DL-01** through **DL-52** — are closed and binding, are recorded in
[decision-ledger.md](decision-ledger.md) Part 1, and are **not** tracked as issues.

Repository: `tom-tagmdl/homes_that_behave_well`.

---

## Governance backlog Epic

| Item | Issue |
|---|---|
| **HTBW Architecture and Governance Backlog — Authoritative Open Decisions** | **#147** |

The Epic carries the reconstruction record, the dependency map, the recommended work sequence, the
backlog maintenance rules, and the closure criteria.

---

## Open decisions

Status values are those held on the issue. Where a decision is blocked, the blocking issue is named.

| ID | Title | Status | Issue | Depends on | Authority |
|---|---|---|---|---|---|
| **OD-01** | Governed-Record Persistence Shape | Open — Research Required | **#76** | #146 | DL-26, DL-31, DL-42, DL-44, DL-46, DL-47 |
| **OD-04** | Policy Precedence Order | Open — Governance Required | **#97** | #135, #98, #99, #119 | DL-03, DL-14, DL-36 |
| **OD-05** | Decision Trace Retention Floor and Ceiling | Open — Partially Decided | **#77** | #99, #79, #76 | DL-24, DL-46, DL-47 |
| **OD-06** | Consent Capture and Revocation Experience | Open — Governance Required | **#94** | — | DL-38, DL-41, DL-43, DL-47 |
| **OD-07** | Voice Processing Locality | Open — Research Required | **#95** | #94 | DL-05, DL-19, DL-41 |
| **OD-09** | Data Portability and Erasure Mechanics | Open — Research Required | **#78** | #77, #125, #118, #82, #86, #76 | DL-42, DL-43, DL-44, DL-45, DL-47 |
| **OD-10** | Scope Hierarchy and Whether Floors Are First-Class | Open — Research Required | **#135** | #146 | DL-09, DL-12, DL-13, DL-30, DL-31 |
| **OD-11** | Room Composition Rules | Open — Governance Required | **#136** | — | DL-11, DL-12, DL-13 |
| **OD-12** | Exclusion Metadata | Open — Governance Required | **#137** | — | DL-11 |
| **OD-13** | Contextual Vocabulary Inheritance | Open — Governance Required | **#138** | #135, #136 | DL-09, DL-10; OD-14 resolved |
| **OD-15** | Identity Assertion Lifetime | Open — Governance Required | **#96** | — | DL-32, DL-36, DL-37, DL-38, DL-39 |
| **OD-17** | Composite Fact Computation | Open — Governance Required | **#88** | #93, #91, #89 | DL-04, DL-09, DL-11 |
| **OD-18** | Fact Freshness Policy | Open — Governance Required | **#89** | #93 | DL-25, DL-38, DL-47 |
| **OD-19** | Evidence Conflict Resolution | Open — Governance Required | **#90** | #88, #89, #93, #91 | DL-04, DL-25 |
| **OD-20** | Optional Asset Intelligence Product Integration | Open — Narrowed by DL-51 | **#110** | — | DL-07, DL-08, DL-19, DL-41, **DL-51** |
| **OD-21** | Significance Representation | Open — Governance Required | **#107** | — | DL-21, DL-27, DL-39 |
| **OD-22** | Escalation Ladder Semantics and Defaults | Open — Governance Required | **#108** | #107, #115, #100, #105 | OD-50 resolved into this |
| **OD-23** | Obligation Projection Surface | Open — Research Required | **#109** | #105, #107, #140 | DL-16, DL-30, DL-31, DL-42 |
| **OD-24** | Session Merge Policy | Open — Governance Required | **#123** | #126, #97 | DL-13 |
| **OD-25** | Resume Eligibility Window Defaults | Open — Governance Required | **#124** | #125 | — |
| **OD-26** | Experience History Retention | Open — Partially Decided | **#125** | #130, #127 | DL-21, DL-47 |
| **OD-27** | Session Concurrency Policy | Open — Governance Required | **#126** | — | DL-13 |
| **OD-28** | Learned-Policy Promotion Lifecycle | Open — Governance Required | **#127** | #130, #76, #128, #125 | DL-21, DL-26, DL-27, DL-38 |
| **OD-29** | Decision Trace Persistence | Open — Blocked | **#79** | #76, #77 | DL-15, DL-27, DL-46, DL-47 |
| **OD-30** | Decision Trace Visibility | Open — Governance Required | **#80** | #79, #81, #133, #104 | DL-34, DL-36, DL-39, DL-46 |
| **OD-31** | Assessment Record Storage | Open — Governance Required | **#139** | — | DL-22, DL-43, DL-44, DL-45, DL-47 |
| **OD-32** | Maturity Review and Reassessment Cadence | Open — Governance Required | **#111** | #139, #105 | DL-22 |
| **OD-35** | Historical Retrieval and Access | Open — Governance Required | **#81** | #79, #76, #92, #133, #87 | DL-24, DL-25, DL-34, DL-35, DL-46 |
| **OD-36** | Deletion Versus Preservation Reconciliation | Open — Governance Required | **#82** | #85, #77, #125, #118 | DL-24, DL-43, DL-45, DL-47 |
| **OD-37** | Snapshot Triggers, Cadence, and Scope | Open — Blocked | **#83** | #76 | DL-26, DL-47 |
| **OD-38** | Identifier and Correlation Strategy | Open — Research Required | **#84** | #76 | DL-26, DL-27, DL-46 |
| **OD-39** | Preservation Hold Governance | Open — Governance Required | **#85** | #99, #87 | DL-43, DL-45, DL-47 |
| **OD-40** | Evidence Package Governance | Open — Governance Required | **#86** | #81, #82, #85, #87, #92 | DL-35, DL-43, DL-44, DL-45 |
| **OD-41** | Incident and Case Object Model | Open — Governance Required | **#87** | #81, #92 | DL-24, DL-35, DL-43 |
| **OD-42** | Communication Persistence | Open — Blocked | **#112** | #76, #118, #116 | DL-28, DL-31, DL-47 |
| **OD-43** | Delivery Surface Capability Model | Open — Research Required | **#113** | #134 | DL-28, DL-29, DL-34, DL-41 |
| **OD-44** | Delivery Outcome Semantics | Open — Governance Required | **#114** | #113, #121, #102 | DL-28; *Completed* superseded |
| **OD-45** | Acknowledgement Semantics | Open — Governance Required | **#115** | #114, #121, #99 | DL-36, DL-37 |
| **OD-46** | Urgency Entitlement Model | Open — Governance Required | **#98** | #99, #97, #113 | DL-28, DL-29, DL-34 |
| **OD-47** | Household Inbox Projection Semantics | Open — Partially Decided | **#116** | #113, #102, #118, #109 | Resolved as a projection |
| **OD-48** | Communication Re-Presentation Preference | Open — Governance Required | **#117** | #98, #119, #120, #100 | *Follow-Me Communication* superseded |
| **OD-49** | Communication Retention | Open — Partially Decided | **#118** | #119, #77, #82 | DL-46, DL-47; OD-33 closed |
| **OD-51** | Interruption Risk Classes and Defaults | Open — Partially Decided | **#99** | — | DL-36, DL-37, DL-39, DL-40; OD-08 closed |
| **OD-52** | Audience Specification | Open — Governance Required | **#100** | #104, #113, #108 | DL-28, DL-29, DL-33, DL-34 |
| **OD-53** | Communication Taxonomy | Open — Governance Required | **#119** | #101 | Info / Attention / Urgent superseded |
| **OD-54** | Delivery Retry Policy | Open — Governance Required | **#120** | #114, #115, #113, #98 | Retry is never escalation |
| **OD-55** | Presentation Attestation | Open — Research Required | **#121** | #113, #146 | DL-28 |
| **OD-56** | Safety-Category Scope | Open — Governance Required | **#101** | #98, #119 | *HTBW is not a life-safety system* |
| **OD-57** | Indication and Content Separation | Open — Governance Required | **#102** | #104, #98, #119, #113 | DL-28, DL-29, DL-34 |
| **OD-58** | Terminology Supersession Scope | Open — Governance Required | **#122** | — | DL-12, DL-28 |
| **OD-59** | Exposure Precedence | Open — Research Required | **#103** | #140, #146 | DL-11, DL-31; OD-14 precedent |
| **OD-60** | Repairs Adoption Scope | Open — Governance Required | **#140** | #146 | DL-16, DL-30, DL-41, DL-46 |
| **OD-61** | Area Environmental Entity Consumption | Open — Governance Required | **#91** | — | DL-09, DL-11, DL-31 |
| **OD-62** | Governed Conversational Retrieval | Open — Governance Required | **#133** | #103, #79, #80, #81, #104, #146 | DL-33, DL-34, DL-35, DL-36, DL-46 |
| **OD-63** | Behaviour Attribution | Open — Governance Required | **#128** | #129, #84, #93 | DL-38, DL-46 |
| **OD-64** | Native Behaviour Observation | Open — Research Required | **#129** | #84, #76, #146 | DL-30, DL-31, DL-38, DL-42, DL-46 |
| **OD-65** | Learning Evidence Eligibility | Open — Governance Required | **#130** | #128, #129, #96, #125 | DL-21, DL-33, DL-36, DL-37, DL-38 |
| **OD-66** | Delegation Boundary | Open — Governance Required | **#131** | #128, #129, #99, #132 | DL-15, DL-41, DL-46 |
| **OD-67** | Reasoning Provider Strategy | Open — Governance Required | **#132** | #94 | DL-33, DL-34, DL-41 |
| **OD-68** | Managed Label Projection Mechanism | Open — Research Required | **#141** | #146 | DL-31 |
| **OD-69** | Asset-Derived Entity Projection | Open — Governance Required | **#142** | #105, #93, #141 | DL-31, DL-42 |
| **OD-70** | Merged Room Native Representation | Open — Governance Required | **#143** | #136, #141 | DL-12, DL-13, DL-31 |
| **OD-71** | Audience-Uncertainty Disclosure Policy | Open — Governance Required | **#104** | #113, #100, #102, #99 | DL-29, DL-34, DL-37 |
| **OD-72** | Unknown Actor Correlation Confidence | Open — Research Required | **#92** | #81, #87 | DL-35; **DL-38 and DL-39 may not be borrowed** |
| **OD-73** | Interaction-Surface Room Context Resolution | Open — Research Required | **#134** | #146, #93 | DL-09, DL-11, DL-15, DL-30; dependency-view rule 6 |
| **OD-74** | Truth Fact Confidence Representation | Open — Governance Required | **#93** | — | DL-04; **DL-39 bands may not be borrowed** |
| **OD-76** | Person Stewardship and Delegated Care Authority | **Remediation Required** | **#106** | #94 | Episode 6 validation (#75) |
| **OD-77** | Person-to-External-Resource Association Ownership | Open — Governance Required | **#148** | #94, #78, #133, #132, #76 | Episode 7 validation (#151) |
| **OD-78** | Remembered-Value Classes and Restoration Semantics | Open — Blocked | **#149** | #146, #127, #130, #125, #76 | Episode 7 validation (#151) |
| **OD-79** | Presentation Preference Scope and Precedence | Open — Governance Required | **#152** | #97, #113, #117, #132, #96, #104 | Episode 7 validation (#151) |
| **OD-81** | HTBW Capability Exposure and Self-Consumption | Open — Governance Required | **#159** | #146, #109, #142, #143, #103, #133, #128, #129, #77, #80 | DL-11, DL-16, DL-30, DL-31, DL-34, DL-39, DL-42, DL-46, DL-47; harvests #155, #156, #157, #158 |
| **OD-83** | Voiceprint Gallery Structure Under Channel Diversity | Open — Governance Required | **#168** | #163 | DL-32, DL-38, DL-41, DL-43, **DL-50**; OD-16 resolved |
| **OD-84** | Multi-Speaker Evidence and Speaker Plurality | Open — Governance Required | **#169** | #164, #166 | DL-33, DL-34, DL-35, DL-36, DL-38, **DL-50**; OD-16 resolved |
| **OD-85** | Adoption Scope, Artifact Custody, and Coexistence Behaviour | Open — Governance Required | **#172** | #110, #82, #76, #142, #159 | DL-45, DL-48, DL-49, **DL-51**, **DL-52**; OD-82 closed |
| **OD-86** | Vocabulary Change and Term-Withdrawal Consequences | Open — Governance Required | **#174** | #138, #103, #128, #129, #146 | DL-10, DL-14 resolved, DL-27, DL-31, DL-45, P15, P30; superseded vocabulary-lifecycle authority **not** reactivated |
| **OD-87** | Identity Artifact Invalidation as a Governed Household Event | Open — Governance Required | **#175** | #94, #95, #96, #168, #172, #146 | DL-36, DL-38, DL-41, DL-50, DL-52; **OD-16 resolved and not reopened** |

---

## Non-decision governed work

Tracked separately, because a documentation defect is not an open decision and an implementation task
is not an open decision.

| Item | Kind | Status | Issue |
|---|---|---|---|
| Consolidate the Pet model | Documentation Remediation | Remediation Required | **#144** |
| HTBW constitutional documentation set is not under version control | Documentation Remediation | Remediation Required | **#145** |
| Home Assistant native capability verification backlog (**DL-30**) | Implementation Mapping | Open — Research Required | **#146** |
| Monthly Home Assistant release architecture-governance review | Governance Process | Open — **standing obligation, non-terminating**; process defined in `home-assistant-release-review-standard.md` | **#178** |
| Home Assistant 2026.9 architecture-impact review — September 2026 baseline | Governance Review | Open — first review under the monthly standard; **no decision made, no issue closed** | **#179** |
| Season 1 public-contract alignment — website, blog, store, and workbook | Governance Review | Open — **Remediation Required**; register in `public-claim-register.md`. Public framework states **six** responsibilities against **DL-01**'s seven; **DL-51** contradicted by a published store item | **#180** |
| Episode 11 and the ungoverned public framework capabilities | Governance Review | Open — *Technical Debt*, *Home Operating System*, and *Technology Stewardship* are published framework concepts with **zero** repository representation; Episodes 1–3, 9, and 11 have **no artefact** | **#181** |
| External publication remediation package | Governance Remediation | Open — exact replacement copy produced in `external-publication-remediation-package.md`; **nothing applied**, no external system was reachable | **#180**, **#181**, **#176** |
| Episode 6 Stewardship narrative validation | Governance Review | Open — pending OD-75 and OD-76 | **#75** |
| Episode 7 Continuity narrative validation | Governance Review | Open — pending OD-77 and OD-78 | **#151** |
| Episode 8 Concierge narrative validation | Governance Review | Open — pending acceptance; **no new open decision produced** | **#170** |
| Season 1 architectural baseline | Governance Review | Snapshot recorded 2026-08-25 — `season-1-architectural-baseline.md`. **Not authority** | **#147** |
| HTBW visual canon is not under repository governance | Documentation Remediation | Remediation Required | **#150** |
| Canonical documents use numeric Identity confidence, contradicting **DL-39** | Documentation Remediation | Remediation Required | **#154** |
| Asset Intelligence legacy capability harvest | Governance Review | Open — pending OD-75, OD-77, OD-01, OD-37 | **#155** |
| Concierge and Voice Identity legacy capability harvest | Governance Review | Open — pending OD-77, OD-78, OD-79, OD-82, OD-67, OD-19; **OD-80 cleared by DL-50** | **#156** |
| Enrollment sufficiency and re-enrollment ownership | Governance Challenge | Closed — no new decision required; governed by DL-32, DL-36, DL-38, DL-41, DL-43 and resolved OD-16 | **#156** |
| Legacy documentation knowledge harvest — all three repositories | Governance Review | Open — pending refinement triage | **#157** |
| Portfolio operational refinement register | Implementation Planning Input | Open — standing register, not a decision | **#158** |
| Legacy product transition and Asset Intelligence adoption | Governance Review | Open — **OD-82 closed as DL-51 and DL-52**; pending **OD-85** and the onboarding-surface gap | **#171** |
| Episode 9 and Episode 10 narrative validation and scenario artifact remediation | Governance Review | Open — Episodes 9 and 10 have **no scenario artefact**; Episode 10 produced **OD-86** and **OD-87** | **#173** |
| The Home Architecture Workbook is not under repository governance | Documentation Remediation | Remediation Required — referenced by `north-star.md`, absent from the repository. Precedent **#150** | **#176** |
| Household impact elements for the assessment record | Governance Routing | Open — determines whether an open decision is required; `assessment-to-platform.md` **must not be edited** before routing is accepted | **#177** |
| Voice evidence runtime — Phase 1, architecture and contracts | Implementation Roadmap | Open — **OD-80 resolved as DL-50**; ADR accepted | **#161** |
| Voice evidence runtime — Phase 2, App runtime foundation | Implementation Roadmap | Blocked on #161 | **#162** |
| Voice evidence runtime — Phase 3, channel-aware enrollment | Implementation Roadmap | Blocked on #162 and **OD-83** (#168) | **#163** |
| Voice evidence runtime — Phase 4, runtime matching and unbound evidence | Implementation Roadmap | Blocked on #163 | **#164** |
| Voice evidence runtime — Phase 5, Wyoming-compatible pipeline integration | Implementation Roadmap | Blocked on #164 | **#165** |
| Voice evidence runtime — Phase 6, advanced audio processing | Implementation Roadmap | Blocked on #165; **validation-required, not accepted behaviour** | **#166** |
| Voice evidence runtime — Phase 7, conversation-active evidence | Implementation Roadmap | **North Star only — not approved for implementation** | **#167** |

---

## Closed and resolved decisions

**Preserved, never recreated, never reopened.** Recorded here so that a reader who finds one of these
identifiers in an older document can see immediately that it is settled.

| ID | Disposition |
|---|---|
| **OD-02** | Closed — DL-43, DL-44, DL-45 |
| **OD-03** | Closed — DL-42, DL-44, DL-45 |
| **OD-08** | Closed — DL-39, DL-40. Per-class defaults deferred to **OD-51** |
| **OD-75** | Closed — **DL-48**, **DL-49**. Obligation condition and lifecycle separated; Care Evidence Record accepted; custody resolved as a Stewardship-owned Custody Period. **Formal acceptance review completed 2026-08-20, result PASS; issue #105 closed as the completed governance record** |
| **OD-14** | Resolved — native naming is an input, never an authority, and is never written back |
| **OD-16** | Resolved — accepted as **DL-38**, the Identity Fusion Function |
| **OD-33** | Closed — DL-43, DL-46, DL-47. Values held by **OD-05**, **OD-26**, **OD-49** |
| **OD-34** | Closed — DL-42, DL-44, DL-46, DL-47. Mechanism residual retained in **OD-01** |
| **OD-50** | Resolved — one escalation architecture. Residual is **OD-22** |
| **OD-80** | Closed — **DL-50**. A capability may declare an execution host; Wyoming is the preferred voice-pipeline boundary; a provider reports candidates and Identity alone resolves. Residuals separated as **OD-82** and **OD-83**. **OD-07** and **OD-66** are not resolved by it |
| **OD-82** | Closed — **DL-51**, **DL-52**. **Product disposition is stated per product**: Asset Intelligence remains a released standalone integration, **is not retired**, and **HTBW must never require it to be installed**; the standalone Voice Identity and Concierge integrations **sunset** while Identity and Concierge remain first-class responsibilities. **Adoption is one-time, authoritative, and terminating.** The non-negotiable constraint in [authority-order.md](authority-order.md) was **amended, not deleted**, and the canonical contradiction across `authority-order.md`, `greenfield-mandate.md`, `north-star.md`, and `adr-htbw-core-refoundation.md` is reconciled. Residual separated as **OD-85**. **OD-20** is narrowed but not closed |

---

## Maintenance rules

1. **One open decision, one issue.** Never two issues for one decision; never one issue for two
   separately closeable decisions.
2. **Preserve original OD identifiers.** Never reuse a retired one. Never invent a new one unless the
   accepted governance process requires it and the issue genuinely represents a newly discovered
   constitutional decision.
3. **Never reopen a closed decision.** Where a closure left a residual, it is tracked on the open
   decision that owns it, as recorded in the table above.
4. **When a decision closes**, update [decision-ledger.md](decision-ledger.md), update this index,
   update every dependent issue, and tick the item in Epic **#147**.
5. **Never close a decision on an assumption about an unverified platform capability** (**DL-30**).
   Unverifiable documentation leaves the decision open.
6. **A new open decision requires a ledger entry first**, then an issue, then a row here.
7. This index carries **identifier, title, status, issue link, dependency summary, and authority
   only**. The issue carries everything else.

---

## Related documents

- [decision-ledger.md](decision-ledger.md) — accepted decisions and open decisions in full
- [authority-order.md](authority-order.md) — how conflicts are resolved
- [document-register.md](document-register.md) — classification of every file
- [document-lifecycle.md](document-lifecycle.md) — status banners and supersession
