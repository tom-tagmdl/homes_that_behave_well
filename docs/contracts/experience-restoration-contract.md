# Experience Restoration Contract

## Purpose

This contract defines the authoritative boundary for restoration eligibility governance, restoration policy governance, and restoration explanation governance in Concierge V2.

This contract governs:

- room default restoration
- guest fallback restoration
- person-room restoration
- identity confidence restoration gates
- occupancy confidence restoration gates
- multi-person restoration conflict behavior
- quiet-hours restoration behavior
- posture-aware restoration behavior
- restoration explainability
- restoration eligibility

This contract does not define:

- execution sequences
- automation logic
- provider integrations
- orchestration implementation

---

## Experience Restoration Definition

Experience Restoration is a governed policy framework that determines whether restoration of a prior household experience is eligible, permitted, explainable, and appropriate.

Experience Restoration is not:

- execution authority
- identity authority
- occupancy authority
- continuity authority
- affinity authority

Restoration consumes governed context.

Restoration does not own governed context.

---

## Restoration Ownership Matrix

| Concern | Owner | Restoration Relationship |
|---|---|---|
| room truth | Foundation | restoration consumes room truth for eligibility context and does not own room truth |
| occupancy truth | Foundation | occupancy influences eligibility and remains externally authoritative |
| identity confidence | Voice Identity | confidence gates restoration eligibility and remains externally authoritative |
| person continuity | Person Continuity governance | continuity provides restoration candidates and remains externally authoritative |
| person affinity | Person Affinity governance | affinity provides restoration preferences and remains externally authoritative |
| experience projection | Experience Projection governance | restoration consumes projected experience context without ownership transfer |
| household memory | Household Memory governance | memory provides restoration context and does not authorize restoration |
| restoration | Experience Restoration governance under this contract | owns restoration eligibility, policy, and explanation governance |
| personalization | Personalization governance under ADR-008 | contributes context and does not authorize restoration |
| provenance | Provenance governance under ADR-011 | explains restoration decisions and does not authorize restoration |
| execution | Service contracts and orchestration paths | execution remains outside restoration authority |
| explainability | HTBW governance policy applied by restoration consumers | restoration must emit machine and human explainability outputs |

Required ownership alignment:

- Foundation owns room and occupancy truth.
- Voice Identity owns identity confidence.
- continuity governance owns continuity.
- affinity governance owns affinity.
- restoration governance owns restoration eligibility governance.
- execution remains outside restoration.

---

## Restoration Categories

### 1. Room Default Restoration

Governance scope:

- default room restoration behavior
- room-level restoration eligibility
- room-default restoration policy

Rules:

- room restoration consumes room truth
- room restoration does not own room truth
- room-default behavior must be deterministic and explainable

### 2. Guest Fallback Restoration

Governance scope:

- guest-safe fallback restoration behavior
- restricted restoration behavior for guest interactions

Rules:

- guest restoration must be privacy-safe
- guest restoration is policy-bounded and restricted by default
- guest restoration must remain explainable

### 3. Person-Room Restoration

Governance scope:

- identity-aware restoration
- continuity-aware restoration
- affinity-aware restoration

Rules:

- restoration consumes continuity and affinity
- restoration does not own continuity and affinity
- person-room restoration eligibility is confidence and policy gated

### 4. Media Restoration

Governance scope:

- media-oriented restoration candidates
- media continuity-influenced restoration eligibility

Rules:

- media restoration is governed by eligibility policy only
- media restoration must not imply execution authority

### 5. Environment Restoration

Governance scope:

- environment-aware restoration eligibility context
- posture and quiet-hours influenced restoration context

Rules:

- environment restoration consumes governed context and policy gates
- environment restoration must remain explainable and deterministic

### 6. Notification Restoration

Governance scope:

- restoration of notification style or mode where policy permits

Rules:

- notification restoration is policy-constrained
- guest and unknown protections must remain enforced

### 7. Experience Restoration

Governance scope:

- restoration of prior experience category when eligible
- restoration suppression behavior when policy disallows

Rules:

- restoration may consume experience projection context
- restoration does not own experience projection authority

### 8. Productivity Restoration

Governance scope:

- productivity-related restoration candidates for calendar, email, tasks, shopping, knowledge, and briefing contexts

Rules:

- providers remain systems of record
- productivity restoration is eligibility and visibility governance only
- private productivity context must not be restored for guest or unknown identities

---

## Room Default Restoration

Room default restoration must define:

- default room restoration
- room-level restoration eligibility
- room-default behavior

Required statements:

- room restoration consumes room truth
- room restoration does not own room truth

---

## Person-Room Restoration

Person-room restoration must define:

- identity-aware restoration
- continuity-aware restoration
- affinity-aware restoration

Required statements:

- restoration consumes continuity and affinity
- restoration does not own continuity and affinity

---

## Identity Confidence Gates

Restoration behavior must be governed for:

- high confidence identity
- medium confidence identity
- low confidence identity
- unknown identity

Rules:

- identity confidence influences restoration eligibility
- identity confidence does not belong to restoration
- Voice Identity remains authoritative
- low or unknown confidence must use conservative restoration eligibility behavior

---

## Occupancy Confidence Gates

Restoration behavior must be governed for:

- known occupancy
- uncertain occupancy
- unknown occupancy
- conflicting occupancy

Rules:

- occupancy influences restoration eligibility
- occupancy authority remains external
- uncertain, unknown, or conflicting occupancy must remain visible in explainability outputs

---

## Multi-Person Conflict Behavior

Governance must define behavior for:

- multiple known occupants
- known occupant plus guest
- conflicting affinities
- conflicting continuity
- conflicting restoration candidates

Rules:

- visibility of conflict state is required
- explainability for conflict-constrained restoration eligibility is required
- this contract defines governance only and does not define conflict-resolution algorithms

---

## Quiet Hours Interaction

Quiet-hours policy must influence restoration behavior.

Governance includes:

- quiet-hours influence
- restoration suppression
- restoration modification
- restoration eligibility impacts

Rules:

- quiet-hours policy is a mandatory restoration policy input
- quiet-hours does not create restoration authority

---

## Posture Interaction

Posture policy must influence restoration eligibility.

Required posture contexts:

- sleep posture
- focus posture
- entertainment posture
- work posture
- guest posture

Rules:

- posture influences restoration eligibility
- posture does not authorize restoration

---

## Guest Fallback Restoration

Guest fallback restoration must define:

- guest restoration behavior
- privacy-safe defaults
- restricted restoration

Required protections:

- guests must not inherit private continuity
- guests must not inherit private affinity

---

## Unknown Identity Restoration

Unknown identity restoration must define:

- unknown-user restoration
- low-confidence restoration
- restricted restoration

Required protections:

- unknown identities may not inherit continuity
- unknown identities may not inherit affinity

---

## Personalization Relationship

Personalization contributes context.

Personalization does not authorize restoration.

This relationship aligns with ADR-008.

---

## Continuity and Affinity Relationship

Continuity provides restoration candidates.

Affinity provides restoration preferences.

Neither authorizes restoration.

---

## Household Memory Relationship

Memory may provide restoration context.

Memory does not authorize restoration.

This relationship aligns with ADR-009.

---

## Provenance Relationship

Provenance explains restoration decisions.

Provenance does not authorize restoration.

This relationship aligns with ADR-011.

---

## Explainability Requirements

### Machine Explainability

Machine explainability must include:

- restoration candidate
- restoration category
- confidence gates evaluated
- occupancy gates evaluated
- quiet-hours influence
- posture influence
- provenance linkage
- timestamps

### Human Explainability

Human explainability must include:

- why restoration occurred
- why restoration did not occur
- why restoration was suppressed
- why guest fallback was used
- why confidence prevented restoration

---

## Non-Rights

Restoration does not own:

- room truth
- occupancy truth
- identity
- continuity
- affinity
- memory
- execution

---

## Determinism Requirements

Determinism requirements:

- same confidence state -> same restoration eligibility
- same occupancy state -> same restoration eligibility
- same quiet-hours policy -> same restoration eligibility
- same posture inputs -> same restoration eligibility

Prohibited behavior:

- hidden restoration triggers
- hidden confidence overrides
- hidden occupancy overrides

---

## Restoration Policy Dependency Matrix

| Policy Source | Consumed By Restoration | Authority Retained By |
|---|---|---|
| Voice Identity | identity confidence gates and identity-aware restoration eligibility | Voice Identity governance |
| Occupancy | occupancy confidence gates and occupancy-informed restoration eligibility | Foundation occupancy governance |
| Personalization | personalization context for restoration eligibility evaluation | Personalization governance under ADR-008 |
| Continuity | restoration candidates and continuity-aware restoration context | Person Continuity governance |
| Affinity | restoration preferences and affinity-aware restoration context | Person Affinity governance |
| Household Memory | memory-informed restoration context and eligibility signals | Household Memory governance under ADR-009 |
| Provenance | restoration decision lineage and explainability linkage | Provenance governance under ADR-011 |
| Quiet Hours | suppression and modification policy input for restoration eligibility | global configuration and policy governance |
| Posture | local posture policy input for restoration eligibility | room and scope policy governance |

---

## V1 Parity Requirements

Aligned with ADR-013, this contract preserves:

- media restoration outcomes
- room restoration outcomes
- notification restoration outcomes

Implementation may change.

Outcome behavior may not regress.

---

## Relationship Notes

Restoration <-> Identity Confidence

- restoration consumes confidence gates
- Voice Identity retains confidence authority

Restoration <-> Occupancy

- occupancy influences restoration eligibility
- Foundation retains occupancy authority

Restoration <-> Continuity

- continuity provides restoration candidates
- continuity retains authority and does not authorize restoration

Restoration <-> Affinity

- affinity provides restoration preferences
- affinity retains authority and does not authorize restoration

Restoration <-> Personalization

- personalization contributes context
- personalization does not authorize restoration

Restoration <-> Household Memory

- memory contributes restoration context
- memory does not authorize restoration

Restoration <-> Provenance

- provenance explains restoration decisions
- provenance does not authorize restoration

Restoration <-> Coordinator V2

- Coordinator V2 consumes governed restoration outputs
- Coordinator V2 does not become restoration authority

---

## Deferred Closure Note (C11 Dependency)

V2-C7 implementation may complete, but issue closure remains blocked until V2-C11 is completed and validated.

This dependency is mandatory for closure and must not be removed.

---

## Contract Coverage Review

What remains in other governance artifacts:

- identity and confidence authority remain in Voice Identity and person identity contract
- occupancy authority remains in Foundation and occupancy governance
- continuity and affinity authority remain in person continuity and affinity contract
- execution authority remains in service contracts and orchestration contracts

What this contract now owns:

- restoration eligibility governance
- restoration policy governance
- restoration explanation governance

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

This contract consumes governance and does not redefine governance authority.

---

## Final Principle

Experience Restoration governs whether restoration is eligible, policy-permitted, and explainable.

It consumes governed context without owning that context.

It must remain deterministic, explainable, ownership-safe, and guest-safe.