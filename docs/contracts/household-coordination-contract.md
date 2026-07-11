# Household Coordination Contract

## Purpose

This contract defines the authoritative boundary for Household Coordination as a first-class governed concern.

This contract governs:

- shared availability
- shared calendar coordination
- household schedule awareness
- task coordination
- shopping coordination
- messaging coordination
- household status participation
- errands awareness
- open-loop awareness
- coordination visibility
- coordination explainability
- person-aware coordination
- guest-safe coordination
- provenance consumption

This contract does not define:

- provider implementations
- scheduling engines
- runtime orchestration
- synthesis engines
- messaging engines

---

## Contract Definition

Household Coordination is:

A governed cross-domain awareness capability that represents household-relevant coordination information derived from authoritative experience domains.

Household Coordination is not:

- a scheduling engine
- a workflow engine
- a household planner
- a task platform
- a calendar platform

Household Coordination consumes governed references.

Household Coordination does not own source systems of record.

---

## Shared Availability

Purpose:

- represent household availability context needed for coordination awareness

Authority boundaries:

- calendar systems remain authoritative for availability truth
- this contract governs coordination consumption obligations only

Visibility considerations:

- person-scoped and household-scoped visibility must remain explicit
- guest and unknown identities must receive reduced or restricted visibility

Explainability requirements:

- explain why availability appears
- explain why availability is hidden or reduced

---

## Shared Calendar Coordination

Purpose:

- represent calendar-linked coordination context for shared household planning awareness

Authority boundaries:

- calendar systems remain authoritative
- coordination consumes calendar references and does not own scheduling behavior

Visibility considerations:

- visibility must be bounded by person scope and guest-safe policy

Explainability requirements:

- explain why calendar items participate in coordination
- explain why calendar items are not visible

---

## Household Schedule Awareness

Purpose:

- represent household schedule-level awareness without becoming a planner

Authority boundaries:

- this contract governs awareness and consumption boundaries only
- schedule systems remain authoritative

Visibility considerations:

- support household, person, and restricted views

Explainability requirements:

- explain why a schedule context appears
- explain why it is relevant for household coordination

---

## Task Coordination

Purpose:

- represent task participation in household coordination awareness

Authority boundaries:

- task systems remain authoritative for task, assignment, and completion truth
- this contract does not define task execution behavior

Visibility considerations:

- assigned and shared task visibility must be policy-bounded

Explainability requirements:

- explain why a task appears in coordination
- explain visibility restrictions for task participation

---

## Shopping Coordination

Purpose:

- represent shopping participation in household coordination awareness

Authority boundaries:

- shopping systems remain authoritative for list and completion truth
- this contract does not define shopping execution behavior

Visibility considerations:

- shared shopping visibility must remain bounded by policy

Explainability requirements:

- explain why a shopping item appears in coordination
- explain why shopping context is visible or restricted

---

## Messaging Coordination

Purpose:

- represent messaging participation in household coordination awareness

Authority boundaries:

- messaging systems remain authoritative for message truth and delivery truth
- this contract does not define messaging engine behavior

Visibility considerations:

- private messaging context must remain protected

Explainability requirements:

- explain why messaging context participates in coordination
- explain why messaging context is restricted

---

## Household Status Coordination

Purpose:

- represent household status participation in coordination awareness surfaces

Authority boundaries:

- household status synthesis remains externally governed
- this contract governs participation boundaries and visibility obligations only

Visibility considerations:

- visibility must remain bounded by household policy and person scope

Explainability requirements:

- explain why household status participates in coordination
- explain visibility and participation boundaries

---

## Errands Awareness

Purpose:

- represent errands context relevant to household coordination awareness

Authority boundaries:

- errands context is consumed from authoritative experience domains
- this contract does not define routing or execution engines

Visibility considerations:

- errands visibility must support restricted and guest-safe modes

Explainability requirements:

- explain why errands are included
- explain why errands are hidden or reduced

---

## Open Loop Awareness

Purpose:

- represent open-loop awareness for unfinished or unresolved household coordination items

Authority boundaries:

- open-loop references consume authoritative task, shopping, and status domains
- this contract does not define prioritization or synthesis engines

Visibility considerations:

- open-loop visibility must remain policy-bounded and guest-safe

Explainability requirements:

- explain why an item is considered open loop
- explain why open-loop context is visible

---

## Person-Aware Coordination

Person-aware coordination must support:

- household members
- known people
- person-scoped coordination context

Identity authority remains external.

Coordination may consume person context but may not redefine identity, confidence, or authorization authority.

---

## Guest-Safe Coordination

Guest-safe coordination must support:

- guest visibility limits
- reduced visibility
- guest-safe participation boundaries
- unknown identity boundaries

Guest-safe policies remain contract-governed.

Guests and unknown identities must not inherit private person-scoped coordination context.

---

## Provenance Consumption

Household Coordination must consume:

- Provenance Contract semantics
- Provenance Model references

Household Coordination may not create:

- alternate attribution systems
- alternate provenance fields

No provenance duplication is permitted.

---

## Explainability Requirements

Human explainability must support:

- why an item appears
- why it is relevant
- why it is visible
- why it participates in coordination

Machine explainability must support:

- source references
- domain references
- provenance references
- visibility references

Explainability is mandatory for surfaced and restricted coordination outcomes.

---

## Cross-Domain Coordination Matrix

| Domain | Can Participate | Authority Source | Notes |
|---|---|---|---|
| Calendar | yes | Calendar and Email Experience Contract | Calendar remains source of schedule truth; coordination consumes references |
| Email | yes | Calendar and Email Experience Contract | Email remains source of message truth; coordination uses bounded awareness references |
| Tasks | yes | Task and Shopping Experience Contract | Task ownership, assignment, and completion remain task-domain authorities |
| Shopping | yes | Task and Shopping Experience Contract | Shopping list and completion remain shopping-domain authorities |
| Messaging | yes | Messaging systems and contracts | Coordination may consume messaging context without owning delivery behavior |
| Household Status | yes | Knowledge, Briefing, and Household Status Synthesis Contract | Status participation is bounded and explainable |
| Briefing | yes | Knowledge, Briefing, and Household Status Synthesis Contract | Coordination may consume briefing references without owning briefing generation |
| Knowledge | yes | Knowledge, Briefing, and Household Status Synthesis Contract | Knowledge remains source authority; coordination consumes references only |
| Household Memory | yes | Household Memory Contract | Memory remains authoritative for memory governance and visibility semantics |
| Provenance | yes | Provenance Contract and Provenance Model | Provenance remains authoritative for attribution and lineage semantics |

---

## Calendar Relationship

Consumed authority:

- Calendar and Email Experience Contract

Ownership retained by source system:

- calendar systems retain schedule and availability authority

Restrictions:

- this contract does not define scheduling behavior

---

## Email Relationship

Consumed authority:

- Calendar and Email Experience Contract

Ownership retained by source system:

- email systems retain mailbox and message authority

Restrictions:

- this contract does not define mailbox behavior

---

## Task Relationship

Consumed authority:

- Task and Shopping Experience Contract

Ownership retained by source system:

- task systems retain task, assignment, and completion authority

Restrictions:

- this contract does not define task execution or assignment engines

---

## Shopping Relationship

Consumed authority:

- Task and Shopping Experience Contract

Ownership retained by source system:

- shopping systems retain list and item completion authority

Restrictions:

- this contract does not define shopping execution behavior

---

## Messaging Relationship

Consumed authority:

- messaging contracts and systems

Ownership retained by source system:

- messaging systems retain delivery and message truth authority

Restrictions:

- this contract does not define messaging engines

---

## Household Status Relationship

Consumed authority:

- Knowledge, Briefing, and Household Status Synthesis Contract

Ownership retained by source system:

- household status synthesis remains externally governed

Restrictions:

- this contract does not define synthesis behavior

---

## Briefing Relationship

Consumed authority:

- Knowledge, Briefing, and Household Status Synthesis Contract

Ownership retained by source system:

- briefing composition and generation remain externally governed

Restrictions:

- this contract does not define briefing generation

---

## Knowledge Relationship

Consumed authority:

- Knowledge, Briefing, and Household Status Synthesis Contract

Ownership retained by source system:

- knowledge authority remains with knowledge systems and contracts

Restrictions:

- this contract does not define knowledge retrieval engines

---

## Household Memory Relationship

Consumed authority:

- Household Memory Contract

Ownership retained by source system:

- household memory governance remains external

Restrictions:

- this contract does not define memory storage or retrieval engines

---

## Provenance Relationship

Consumed authority:

- Provenance Contract
- Provenance Model

Ownership retained by source system:

- provenance governance remains authoritative for attribution and lineage semantics

Restrictions:

- no alternate attribution semantics
- no provenance field duplication

---

## Visibility Model

The contract defines visibility obligations for:

- person-scoped visibility
- household visibility
- guest-safe visibility
- restricted visibility

The contract defines obligations and boundaries only.

The contract does not define implementation behavior.

---

## Non-Rights

Household Coordination Contract does not own:

- calendar systems of record
- task systems of record
- shopping systems of record
- messaging systems of record
- briefing generation
- synthesis behavior
- orchestration behavior
- runtime execution

Ownership drift is prohibited.

---

## Household Coordination Snapshot Consumption

This contract is authoritative for:

- docs/models/household-coordination-snapshot-model.md

The model consumes this contract.

The model is not authority.

---

## Contract Coverage Matrix

| Coordination Area | Governed | Notes |
|---|---|---|
| availability | yes | shared availability awareness is governed and reference-based |
| schedule awareness | yes | schedule context is governed without planner ownership |
| task coordination | yes | task participation is governed while task authority remains external |
| shopping coordination | yes | shopping participation is governed while shopping authority remains external |
| messaging coordination | yes | messaging participation is governed while delivery authority remains external |
| household status | yes | status participation is governed through bounded consumption |
| errands | yes | errands awareness is governed without execution ownership |
| open loops | yes | open-loop awareness is governed and explainable |
| person awareness | yes | person-aware coordination is governed with external identity authority |
| guest-safe coordination | yes | guest-safe and unknown-identity boundaries are contract-governed |
| provenance consumption | yes | provenance semantics are consumed from provenance authorities |
| explainability | yes | human and machine explainability obligations are governed |

---

## Contract Alignment Review

Alignment set:

- Provenance Contract
- Calendar and Email Experience Contract
- Task and Shopping Experience Contract
- Knowledge, Briefing, and Household Status Synthesis Contract
- Household Coordination Contract

1. Ownership boundaries.

	Ownership boundaries are preserved. Household Coordination consumes references and does not take ownership of calendar, email, task, shopping, messaging, briefing, knowledge, household status, memory, or provenance source-of-record authorities.

2. Consumption boundaries.

	Consumption boundaries are explicit and contract-governed for domain participation, visibility, guest-safe behavior, explainability, and provenance consumption.

3. Identified gaps.

	No gaps identified.

---

## Canonical Architecture Linkage

Household Coordination Contract is the authoritative contract source for:

- E14 Household Coordination
- Household Coordination Snapshot Model
- Future Coordination Experiences
- Household Planning Experiences

Future Household Coordination Snapshot Model consumption must treat [docs/contracts/household-coordination-contract.md](household-coordination-contract.md) as authoritative.

Future E14 Household Coordination must treat [docs/contracts/household-coordination-contract.md](household-coordination-contract.md) as authoritative.

Future Household Planning Experiences must treat [docs/contracts/household-coordination-contract.md](household-coordination-contract.md) as authoritative.

Future Coordination Experiences must treat [docs/contracts/household-coordination-contract.md](household-coordination-contract.md) as authoritative.
