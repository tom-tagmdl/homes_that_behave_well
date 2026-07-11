# HACS and Platinum Contract Compliance Checklist

## Purpose

This checklist defines the contract-level governance framework used to assess whether HTBW contract artifacts satisfy architectural, operational, maintainability, explainability, privacy, and readiness expectations.

This checklist is a governance review framework.

This checklist does not define:

- CI implementation
- test execution
- release implementation
- deployment implementation

---

## Checklist Definition

HACS and Platinum Contract Compliance Checklist is:

A contract-level governance review framework used to assess whether HTBW contract artifacts satisfy architectural, operational, maintainability, explainability, privacy, and readiness expectations.

---

## Contract Review Matrix

| Contract | Reviewed | Compliant | Notes |
|---|---|---|---|
| V2-C2 Room Interaction | yes | pass | deterministic context resolution, explainability, and non-rights are explicit |
| V2-C3 Room Vocabulary | yes | pass | room terminology and alias governance are explicit |
| V2-C4 Capability Projection | yes | pass | capability visibility and ownership boundaries are explicit |
| V2-C5 Experience Projection | yes | pass | experience visibility, discoverability, and explainability are explicit |
| V2-C6 Person Continuity and Affinity | yes | pass | consent-bounded influence and guest-safe protections are explicit |
| V2-C7 Experience Restoration | yes | pass | occupancy and confidence gates, privacy, and deferred closure dependency are explicit |
| V2-C8 Household Memory | yes | pass | memory/provenance boundaries, privacy, retention, and C11 dependency are explicit |
| V2-C9a Calendar and Email Experience | yes | pass | source-of-record, privacy, consent, and attribution are explicit |
| V2-C9b Task and Shopping Experience | yes | pass | source-of-record, assignment/completion, privacy, and attribution are explicit |
| V2-C9c Knowledge / Briefing / Status Synthesis | yes | pass | calm-by-default, guest-safe, OpenAI, provenance, and explainability are explicit |
| V2-C9d Multi-Item Capture Interpretation | yes | pass | provenance propagation, ambiguity, confirmation, and explainability are explicit |
| V2-C10 Provenance | yes | pass | canonical fields, confidence, lineage, and cross-domain applicability are explicit |
| V2-C11 Occupancy and Presence | yes | pass | occupancy states, confidence, guest-safe behavior, and model alignment are explicit |

---

## HACS Readiness Review

Contract review criteria for HACS readiness:

- diagnostics readiness
- repairability
- configuration visibility
- options visibility
- migration support
- upgradeability
- operator guidance

Pass criteria:

- contracts expose supportable, diagnosable, and recoverable boundaries
- contracts define explicit non-rights and ownership boundaries
- contracts preserve upgrade-safe governance evolution

Fail criteria:

- any contract lacks observable guidance for recovery or supportability
- any contract blurs ownership or source-of-record boundaries
- any contract prevents future config or options governance from being expressed

---

## Platinum Readiness Review

Contract review criteria for Platinum readiness:

- quality expectations
- diagnostics
- repairs
- accessibility
- translations
- testing expectations
- user guidance
- maintainability expectations

Pass criteria:

- contracts remain explicit, explainable, deterministic, and bounded
- contracts expose human-understandable governance language
- contracts support future validation, recovery, and user guidance work

Fail criteria:

- contracts omit explainability, ownership clarity, or recovery clarity
- contracts encode implementation details instead of governance boundaries
- contracts prevent future maintainability or review discipline

---

## Diagnostics Review Gate

Review whether contracts define:

- diagnosable behavior
- explainable behavior
- supportable behavior

Pass criteria:

- diagnosable behavior is explicit in contract language
- explainability requirements are present
- supportability or recovery guidance is present where relevant

Fail criteria:

- required diagnostics are missing
- behavior is opaque or not attributable

---

## Repairability Review Gate

Review whether contracts support:

- recoverability
- operator correction
- configuration correction
- explainability for recovery

Pass criteria:

- contracts describe recoverable failure boundaries
- contracts do not block operator correction or configuration correction pathways

Fail criteria:

- contracts create hidden failure modes
- contracts omit recovery explainability

---

## Translation Review Gate

Review whether contracts avoid:

- language-locked semantics
- UI-coupled semantics
- untranslated governance assumptions

Pass criteria:

- contract language is governance-oriented and stable across locales
- no UI-specific behavior is required to interpret the contract

Fail criteria:

- contract semantics depend on untranslated labels or UI assumptions

---

## Accessibility Review Gate

Review whether contracts expose:

- explainable outputs
- human-understandable outputs
- alternative presentation capability

Pass criteria:

- contract language supports clear explanation in accessible forms
- output expectations do not require inaccessible-only presentation

Fail criteria:

- contract semantics cannot be explained to users or maintainers clearly

---

## Documentation Review Gate

Review whether contracts provide:

- ownership clarity
- relationship clarity
- non-rights clarity
- explainability clarity

Pass criteria:

- ownership and non-rights are explicit
- contract relationships are explicit and bounded

Fail criteria:

- ownership drift or ambiguity remains in the contract set

---

## Config Flow Review Gate

Review whether contracts support:

- configuration governance
- future config flows
- future options flows

Pass criteria:

- contracts clearly separate configuration governance from execution

Fail criteria:

- contracts assume fixed configuration behavior with no governance language

---

## Options Flow Review Gate

Review whether contracts support:

- change management
- safe evolution
- optional capability introduction

Pass criteria:

- contracts permit evolution without redefining source-of-record authority

Fail criteria:

- contracts prevent safe future capability evolution

---

## Upgradeability Review Gate

Review whether contracts support:

- migration
- backward-compatible governance evolution
- future extensibility

Pass criteria:

- contracts preserve compatibility boundaries and upgrade expectations

Fail criteria:

- contracts create brittle or non-evolvable governance definitions

---

## Privacy Review Gate

Review all contracts for:

- privacy boundaries
- guest-safe behavior
- consent requirements
- disclosure controls

Explicitly review:

- C6
- C7
- C8
- C9a
- C9b
- C9c
- C11

Pass criteria:

- private context is bounded by explicit consent and guest-safe requirements

Fail criteria:

- any contract allows protected context to escape governance boundaries

---

## Retention Review Gate

Review all contracts for:

- retention obligations
- expiration expectations
- purge expectations
- redaction expectations

Pass criteria:

- retention or expiry semantics are explicit where contract scope requires them

Fail criteria:

- contract scope requires retention governance but omits it

---

## Explainability Review Gate

Review all contracts for:

- human explainability
- machine explainability
- source visibility
- attribution visibility

Explicitly review:

- C5
- C7
- C8
- C9a
- C9b
- C9c
- C10
- C11

Pass criteria:

- contracts expose explainable, source-visible behavior boundaries

Fail criteria:

- source or attribution visibility is hidden or omitted

---

## Operator Error Surface Review Gate

Review whether contracts define:

- ambiguity visibility
- uncertainty visibility
- confidence visibility
- failure visibility

Pass criteria:

- contracts preserve visible uncertainty and failure conditions

Fail criteria:

- contracts permit hidden assumptions or invisible failures

---

## Room Vocabulary Compliance Review

Review:

- C3

Pass criteria:

- room vocabulary and alias governance remain authoritative and unblurred

---

## Capability Projection Compliance Review

Review:

- C4

Pass criteria:

- capability visibility remains separate from experience visibility and runtime execution

---

## Experience Model Compliance Review

Review:

- C5

Pass criteria:

- experience model governance remains deterministic, explainable, and source-bounded

---

## Personalization Compliance Review

Review:

- C6

Pass criteria:

- personalization remains consent-bounded and guest-safe

---

## Household Memory Compliance Review

Review:

- C8

Pass criteria:

- memory consumes provenance and history without redefining either

---

## Productivity Experience Compliance Review

Review:

- C9a
- C9b
- C9c
- C9d

Pass criteria:

- productivity experiences preserve source-of-record boundaries, attribution, consent, and explainability

---

## Provenance Compliance Review

Review:

- C10

Pass criteria:

- provenance semantics are canonical, cross-domain, and explainable

---

## Occupancy Compliance Review

Review:

- C11

Pass criteria:

- occupancy semantics, guest-safe behavior, and explainability are explicit and model-aligned

---

## V1 Capability Preservation Review

Review whether:

- ADR-013 obligations remain satisfied
- household-facing outcomes remain preserved
- governance evolution did not regress capabilities

Pass criteria:

- contracts preserve V1 household-facing outcomes while refining governance boundaries

Fail criteria:

- governance evolution removes or weakens preserved household-facing capabilities

---

## E1 Completion Gate

| Contract Domain | Complete | Pass | Notes |
|---|---|---|---|
| V2-C2 Room Interaction | yes | pass | reviewed against compliance gates |
| V2-C3 Room Vocabulary | yes | pass | reviewed against compliance gates |
| V2-C4 Capability Projection | yes | pass | reviewed against compliance gates |
| V2-C5 Experience Projection | yes | pass | reviewed against compliance gates |
| V2-C6 Person Continuity and Affinity | yes | pass | reviewed against compliance gates |
| V2-C7 Experience Restoration | yes | pass | reviewed against compliance gates |
| V2-C8 Household Memory | yes | pass | reviewed against compliance gates |
| V2-C9a Calendar and Email Experience | yes | pass | reviewed against compliance gates |
| V2-C9b Task and Shopping Experience | yes | pass | reviewed against compliance gates |
| V2-C9c Knowledge / Briefing / Status Synthesis | yes | pass | reviewed against compliance gates |
| V2-C9d Multi-Item Capture Interpretation | yes | pass | reviewed against compliance gates |
| V2-C10 Provenance | yes | pass | reviewed against compliance gates |
| V2-C11 Occupancy and Presence | yes | pass | reviewed against compliance gates |

Final gate:

- E1 Ready: yes, when all reviewed contract domains remain pass-compliant
- E1 Not Ready: any omitted domain, fail state, or unresolved governance gap

---

## E12 Consumption Gate

Conditions required before E12 may consume E1 outputs:

- all E1 contract domains are present and reviewed
- HACS readiness criteria are pass-compliant
- Platinum readiness criteria are pass-compliant
- privacy and explainability gates are pass-compliant
- no unresolved governance gaps remain in E1 contract boundaries

---

## Checklist Scoring Guidance

PASS:

- the contract satisfies the checklist gate without unresolved issues

PASS WITH OBSERVATIONS:

- the contract satisfies the checklist gate but has non-blocking observations that should be tracked

FAIL:

- the contract does not satisfy the checklist gate or leaves a required boundary undefined

---

## Canonical Architecture Linkage

This checklist must appear in canonical traceability as the final E1 contract-level quality gate.

Future planning must treat this checklist as a mandatory dependency for:

- E12
- all future epics consuming E1 outputs

This checklist is the final E1 contract-level quality gate.

---

## Final Principle

Contracts are ready only when governance, explainability, privacy, maintainability, and operational review criteria are explicitly satisfied.