# Person Continuity and Affinity Contract

## Purpose

This contract defines the authoritative boundary for person continuity and person affinity governance in Concierge V2.

This contract governs:

- continuity eligibility
- continuity visibility
- continuity explainability
- room affinity
- media affinity
- environment affinity
- notification affinity
- guest fallback behavior
- unknown-user behavior
- consent requirements
- retention requirements
- reset obligations

This contract does not define:

- machine learning
- recommendation engines
- storage implementation
- training approaches

---

## Person Continuity Definition

Person Continuity is a governed representation of recent person-associated context that may be used to restore, resume, or continue household experiences.

Examples include:

- last music genre
- last playlist
- last podcast
- last TV show
- last media source
- last room
- last activity
- last experience category

Person Continuity is not:

- identity ownership
- person profile ownership
- learning authority
- hidden inference authority

---

## Person Affinity Definition

Person Affinity is a governed representation of recurring person-room preferences and experience preferences that may influence household behavior when permitted.

Examples include:

- preferred room lighting
- preferred room volume
- preferred room audio source
- preferred room video source
- preferred notification style
- preferred room experience patterns

Person Affinity is not:

- room truth
- identity ownership
- execution authority
- learning engine authority

---

## Boundary Matrix

| Concern | Owner | Relationship |
|---|---|---|
| identity | Voice Identity | continuity and affinity consume identity context and do not own identity truth |
| identity confidence | Voice Identity | confidence gates continuity and affinity eligibility without ownership transfer |
| person profile | Person Profile governance and models | continuity and affinity consume profile context and do not own profile authority |
| person continuity | Person Continuity governance under this contract | continuity governance owns eligibility and visibility policy boundaries |
| person affinity | Person Affinity governance under this contract | affinity governance owns affinity visibility policy boundaries |
| room truth | Foundation | affinity consumes room truth and does not redefine it |
| occupancy | Foundation | occupancy may influence continuity or affinity eligibility and does not create authority |
| household memory | Household Memory governance domain under HTBW authority | memory may consume continuity context and does not own continuity authority |
| personalization | Personalization governance under ADR-008 | personalization consumes continuity and affinity and does not own either |
| restoration | Restoration policy and orchestration boundaries | restoration may consume continuity and affinity and does not receive authority transfer |
| experience projection | Experience Projection governance | experience projection may consume continuity/affinity context and remains separate authority |
| execution | Service contracts and execution orchestration paths | continuity and affinity inform eligibility only and do not execute |

Required ownership alignment:

- Voice Identity owns identity and identity confidence.
- Person Profile owns profile attributes, preferences, and metadata.
- this contract owns continuity governance boundaries.
- this contract owns affinity governance boundaries.
- Foundation owns room truth and occupancy.
- Coordinator V2 consumes continuity and affinity and does not own either authority.

---

## Continuity Categories

### 1. Media Continuity

Governance scope:

- last music genre
- last playlist
- last podcast
- last media source

Rules:

- continuity is eligibility context only
- continuity must remain consent-gated and explainable
- continuity does not grant execution rights

### 2. Entertainment Continuity

Governance scope:

- last TV show
- last entertainment app or source
- last entertainment session context

Rules:

- entertainment continuity may influence restoration candidates
- continuity must not create hidden auto-execution
- visibility must be policy-bounded and deterministic

### 3. Room Continuity

Governance scope:

- last room context for person-associated activity
- room-linked continuity eligibility

Rules:

- room continuity consumes Foundation room truth
- room continuity does not own room truth
- low-confidence identity or occupancy limits continuity eligibility

### 4. Activity Continuity

Governance scope:

- last known activity class
- recently active interaction category

Rules:

- activity continuity may guide continuity visibility
- activity continuity must remain explainable and reversible
- activity continuity must not become hidden inference authority

### 5. Experience Continuity

Governance scope:

- last experience category used
- previously active experience context

Rules:

- experience continuity may influence experience restore candidates
- experience continuity does not own experience projection authority
- policy and consent remain mandatory gates

### 6. Productivity Continuity

Governance scope:

- recently used productivity experience context (calendar, email, tasks, shopping, knowledge, briefing)
- person-associated continuity hints for productivity surfaces

Rules:

- providers remain systems of record
- productivity continuity is visibility and continuity context only
- continuity must not expose private productivity context to guests or unknown identities

---

## Affinity Categories

### 1. Lighting Affinity

Governance scope:

- preferred lighting style per person and room context

Rules:

- affinity may influence eligible experience presentation
- affinity does not own lighting truth or execution

### 2. Audio Affinity

Governance scope:

- preferred volume ranges
- preferred audio source tendencies

Rules:

- affinity may influence ranking or visibility only
- affinity must remain bounded by consent and policy

### 3. Video Affinity

Governance scope:

- preferred video source tendencies
- preferred viewing context tendencies

Rules:

- affinity may influence discoverability only
- affinity does not authorize playback execution

### 4. Notification Affinity

Governance scope:

- preferred notification style
- preferred notification modality tendencies

Rules:

- affinity may influence communication style under policy
- urgent and safety policy rules remain authoritative

### 5. Room Affinity

Governance scope:

- recurring person-room preference tendencies

Rules:

- room affinity consumes room truth
- room affinity does not own room truth
- room affinity must never mutate Foundation room state

### 6. Environment Affinity

Governance scope:

- recurring person-environment preference tendencies for comfort-oriented experiences

Rules:

- environment affinity may influence experience visibility when permitted
- environment affinity does not redefine environmental truth ownership

---

## Consent Requirements

Continuity and Affinity require governed consent.

Consent governance must define:

- explicit opt-in expectations
- explicit opt-out expectations
- consent visibility to the household member
- consent revocation behavior

Rules:

- no continuity or affinity influence is allowed without valid consent state
- revoked consent must disable disallowed continuity and affinity influence immediately
- consent state must be machine and human explainable

---

## Reset Requirements

Reset obligations are mandatory and governance-defined.

Required reset scopes:

- continuity reset
- affinity reset
- household reset
- person reset

Rules:

- reset behavior must be explicit, bounded, and auditable
- resets must remove or deactivate governed continuity or affinity influence according to policy
- this contract defines obligations only and does not define reset implementation

---

## Retention Requirements

Retention governance must define:

- retention eligibility
- expiration expectations
- removal expectations
- redaction expectations

Rules:

- retention behavior must be deterministic under the same policy and consent state
- private continuity and affinity context must be removable and redactable under policy
- this contract defines governance only and does not define storage implementation

---

## Unknown Identity Behavior

Required behaviors:

- unknown identity handling
- low-confidence identity handling
- conflicting identity handling

Mandatory protections:

- unknown identities may not inherit continuity
- unknown identities may not inherit affinity
- identity uncertainty must remain visible

Rules:

- low-confidence identity must use conservative, neutral behavior by default
- conflicting identity signals must not silently select private continuity or affinity
- clarification may be requested when policy requires certainty

---

## Guest Fallback Behavior

Required guest-safe behaviors:

- guest user behavior
- guest continuity behavior
- guest affinity behavior
- guest-safe defaults

Mandatory protections:

- guests must not receive private person continuity
- guests must not receive private affinity data

Rules:

- guest behavior must default to neutral and privacy-preserving handling
- guest behavior must remain deterministic and explainable
- guest behavior may use only policy-allowed non-private context

---

## Room Relationship

Person Affinity consumes room truth.

Person Affinity does not own room truth.

Foundation remains authoritative for room truth.

---

## Occupancy Relationship

Occupancy may influence continuity eligibility.

Occupancy does not create continuity authority.

Occupancy does not create affinity authority.

Occupancy remains a governed context influence, not an ownership transfer path.

---

## Personalization Relationship

Personalization consumes continuity and affinity.

Personalization does not own continuity.

Personalization does not own affinity.

This relationship must align with ADR-008.

---

## Household Memory Relationship

Household Memory may consume continuity context.

Household Memory does not own continuity.

Continuity does not own memory.

This relationship must align with ADR-009.

---

## Restoration Relationship

Restoration may consume continuity.

Restoration may consume affinity.

Continuity and Affinity do not authorize restoration.

Policy remains authoritative.

This relationship must align with E8 and E8a requirements.

---

## Explainability Requirements

### Machine Explainability

Machine explainability must include:

- continuity source
- continuity category
- affinity source
- affinity category
- consent state
- visibility rationale
- retention state

### Human Explainability

Human explainability must include:

- why continuity applied
- why continuity did not apply
- why affinity applied
- why affinity did not apply
- why guest fallback occurred
- why unknown-user protections were applied

Explainability must remain concise, deterministic, and auditable.

---

## Non-Rights

Continuity and Affinity do not own:

- identity
- room truth
- occupancy truth
- household memory
- profile ownership
- execution
- orchestration

Continuity and Affinity may not redefine architecture authority, governance boundaries, or source-of-record ownership.

---

## Determinism Requirements

Determinism requirements:

- same consent state -> same continuity eligibility
- same affinity state -> same affinity visibility
- same identity confidence -> same continuity eligibility
- same guest state -> same fallback behavior

Prohibited behavior:

- hidden continuity inheritance
- hidden affinity inheritance
- hidden identity assumptions

Determinism failures are contract violations.

---

## V1 Parity Requirements

Aligned with ADR-013, this contract preserves:

- media continuity outcomes
- room restoration continuity outcomes
- notification style continuity outcomes

Implementation may change.

Household-facing outcomes may not regress.

---

## Relationship Notes

Continuity <-> Person Profile

- person profile provides governed profile context inputs.
- continuity consumes profile context and does not own profile authority.

Continuity <-> Voice Identity

- Voice Identity provides identity and confidence context.
- continuity eligibility is confidence-gated and does not own identity authority.

Continuity <-> Household Memory

- continuity may contribute bounded continuity context to memory consumers.
- memory remains separate authority and does not transfer ownership.

Continuity <-> Restoration

- restoration may consume continuity context for candidate selection.
- continuity does not authorize restoration execution.

Affinity <-> Room Truth

- affinity consumes Foundation room truth.
- affinity does not own or mutate room truth.

Affinity <-> Personalization

- personalization consumes affinity signals when policy allows.
- personalization does not own affinity governance.

Affinity <-> Occupancy

- occupancy may influence affinity eligibility boundaries.
- occupancy does not create affinity ownership.

Affinity <-> Coordinator V2

- Coordinator V2 consumes affinity outputs for orchestration.
- Coordinator V2 does not become affinity authority.

---

## Boundary Review

Required separations:

- Person Profile owns profile attributes, profile preferences, and profile metadata.
- Person Continuity governs continuity eligibility, visibility, and continuity explainability.
- Person Affinity governs affinity eligibility, visibility, and affinity explainability.
- Identity remains authoritative in Voice Identity.
- Personalization consumes profile, continuity, and affinity under ADR-008 boundaries.

Ownership overlap prevention rules:

- profile data ownership must not be reassigned to continuity or affinity governance
- continuity and affinity must not infer identity authority
- personalization must not absorb continuity or affinity authority
- coordinator must remain consumer-only for continuity and affinity governance

---

## Contract Coverage Review

### What Remains In Existing Contracts

`docs/contracts/person-identity-contract.md` remains authoritative for:

- identity attribution and confidence outputs
- enrollment and identity consent boundaries

`docs/contracts/experience-projection-contract.md` remains authoritative for:

- experience visibility and discoverability governance
- experience composition and availability boundaries

`docs/contracts/concierge-contract.md` remains authoritative for:

- orchestration boundaries
- communication and execution policy posture boundaries

`docs/contracts/service-contracts.md` remains authoritative for:

- service execution and mutation boundaries
- runtime invocation interfaces

### What Now Belongs To This Contract

This contract is authoritative for:

- person continuity governance boundaries
- person affinity governance boundaries
- consent, reset, and retention obligations for continuity and affinity
- guest-safe and unknown-identity protections for continuity and affinity
- continuity and affinity explainability and determinism requirements

Duplication prevention rule:

- identity ownership stays in person identity contract and Voice Identity governance
- profile ownership stays in person profile model governance
- experience ownership stays in experience projection governance
- orchestration ownership stays in concierge contract
- continuity and affinity ownership stays in this contract

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-008 Personalization Governance Boundaries
- ADR-009 Household Memory Governance Boundaries
- ADR-010 Household Productivity Experience Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract consumes governance.

This contract does not redefine governance authority.

---

## Ownership Boundary Validation

Ownership boundaries preserved by this contract:

- Voice Identity remains authoritative for identity, identity confidence, attribution, and enrollment
- Person Profile remains authoritative for profile attributes, preferences, and metadata
- Foundation remains authoritative for room truth and occupancy truth
- continuity and affinity governance remain bounded to eligibility, visibility, and explainability policies
- restoration and personalization remain consumers and do not receive ownership transfer
- Coordinator V2 consumes continuity and affinity outputs and remains orchestration-only

---

## Terminology Alignment

Canonical terminology in this contract:

- Person Continuity
- Person Affinity
- Identity
- Identity Confidence
- Person Profile
- Room Truth
- Occupancy
- Household Memory
- Personalization
- Restoration
- Experience Projection
- Consent
- Retention
- Reset
- Explainability
- Determinism

Legacy assumptions that imply hidden inheritance, hidden identity assumptions, or ownership drift are prohibited.

---

## Final Principle

Person continuity and person affinity provide governed, consent-bounded context that improves household continuity without transferring identity, profile, room-truth, or execution ownership.

They must remain deterministic, explainable, guest-safe, and ownership-safe.