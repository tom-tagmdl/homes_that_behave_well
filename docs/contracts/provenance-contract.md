# Provenance Contract

## Purpose

This contract defines the canonical cross-domain provenance authority for Homes That Behave Well.

This contract governs:

- attribution semantics
- provenance lineage
- provenance explainability
- attribution confidence
- source lineage
- canonical provenance fields

This contract does not define:

- storage implementation
- service implementation
- UI implementation
- execution logic

---

## Provenance Definition

Provenance is the governed representation of who, what, where, when, and how a household artifact, event, activity, decision, or action originated or changed over time.

Provenance is not:

- identity authority
- memory authority
- task authority
- shopping authority

Provenance explains.

Provenance does not execute.

---

## Canonical Provenance Field Set

Canonical provenance fields are:

### created_by

Purpose: identify who or what originated the artifact.

Semantics: records the governed creator actor or system state.

Ownership relationship: Voice Identity and governed source systems provide the input; provenance records it.

Intended usage: creation attribution and explainability.

### added_by

Purpose: identify who or what appended an item to a collection.

Semantics: records the actor or system responsible for addition.

Ownership relationship: provenance records addition lineage; provider or interaction systems originate the action.

Intended usage: shopping/task addition explanation and lineage.

### assigned_to

Purpose: identify the target of a governed assignment.

Semantics: records assignment destination or assignee state.

Ownership relationship: provenance records assignment linkage; identity governance remains external.

Intended usage: task assignment explanation and routing.

### completed_by

Purpose: identify who or what completed an artifact or workflow.

Semantics: records completion actor or system state.

Ownership relationship: provenance records completion lineage; task/shopping authority remains external.

Intended usage: completion attribution and auditing.

### delivered_to

Purpose: identify the destination or recipient of a governed delivery.

Semantics: records who or what received the delivered artifact.

Ownership relationship: provenance records delivery lineage; messaging/reminder systems remain external.

Intended usage: message/reminder delivery explanation.

### acknowledged_by

Purpose: identify who or what acknowledged the artifact.

Semantics: records acknowledgement actor or system state.

Ownership relationship: provenance records acknowledgement lineage; identity remains external.

Intended usage: acknowledgement explanation and audit.

### created_at

Purpose: record when the artifact originated.

Semantics: ISO 8601 UTC creation timestamp.

Ownership relationship: provenance records the timestamp; timing remains descriptive, not authoritative over source truth.

Intended usage: ordering and explainability.

### completed_at

Purpose: record when completion occurred.

Semantics: ISO 8601 UTC completion timestamp.

Ownership relationship: provenance records completion time; external domain authority defines completion truth.

Intended usage: completion explanation and chronology.

### created_in_room

Purpose: record the room context where origin occurred.

Semantics: room reference associated with origin context.

Ownership relationship: Foundation remains authoritative for room truth; provenance references it.

Intended usage: room-linked explanation and lineage.

### created_via

Purpose: record the method or channel of origin.

Semantics: voice, UI, automation, provider event, scheduled action, or system-generated channel.

Ownership relationship: execution/channel systems provide the input; provenance records it.

Intended usage: method/channel explainability.

### attribution_confidence

Purpose: record confidence associated with attribution.

Semantics: explicit attribution confidence value or class.

Ownership relationship: Voice Identity remains authoritative for identity confidence; provenance consumes it.

Intended usage: explainability and conservative downstream decisions.

### explanation_source

Purpose: record the source of the provenance explanation.

Semantics: source reference used to explain the attribution path.

Ownership relationship: provenance records explanation lineage; source systems remain external.

Intended usage: machine and human explanation generation.

---

## Provenance Ownership Matrix

| Concern | Owner | Provenance Relationship |
|---|---|---|
| identity | Voice Identity | provenance references identity outputs and confidence states |
| attribution confidence | Voice Identity | provenance consumes confidence and does not own it |
| room truth | Foundation | provenance references room, area, and interaction-space context |
| occupancy truth | Foundation | provenance references occupancy context without owning it |
| event history | Event systems and producers | provenance references lineage and attribution context |
| household memory | Household Memory | provenance references memory lineage and influence context |
| shopping | Shopping Experience and provider systems | provenance references shopping item lineage and attribution |
| tasks | Task Experience and provider systems | provenance references task lineage and attribution |
| messages | messaging systems and contracts | provenance references message lineage and delivery history |
| reminders | reminder systems and contracts | provenance references reminder lineage and delivery history |
| productivity actions | productivity provider systems and governed experience contracts | provenance references action lineage and attribution context |
| provenance | Provenance governance | provenance defines attribution and lineage semantics |

Ownership principles:

- Voice Identity owns identity and attribution confidence.
- Foundation owns room truth and occupancy truth.
- Provenance defines provenance semantics.
- Provenance references governed domains.
- Provenance does not become authority for governed domains.

---

## Attribution Confidence Governance

Attribution confidence must remain explicit.

Required behavior:

- confidence visibility must remain present when attribution is surfaced
- low-confidence attribution must remain visible and bounded
- unknown attribution must remain visible as unknown rather than collapsed

Required statement:

- Voice Identity remains authoritative.
- Provenance consumes attribution confidence.

---

## Unknown Attribution Handling

Governance must define behavior for:

- unknown actor
- uncertain actor
- conflicting actor

Required statements:

- unknown attribution remains visible
- hidden attribution assumptions are prohibited

Unknown and conflicting states must be represented explicitly rather than inferred away.

---

## Room Attribution Governance

The created_in_room field must remain explicit when room context is available.

Required behavior:

- room-reference expectations must use authoritative room references
- room lineage expectations must remain traceable to Foundation room truth

Required statement:

- Foundation remains authoritative for room truth.

---

## Source Lineage Governance

Source lineage categories include:

- source lineage
- origin lineage
- action lineage
- explanation lineage

Every attributed artifact must support lineage.

---

## Domain Applicability Matrix

| Domain | Uses Provenance | Required Fields |
|---|---|---|
| Shopping | yes | added_by, completed_by, created_at, attribution_confidence |
| Tasks | yes | created_by, assigned_to, completed_by, created_at, completed_at |
| Messages | yes | delivered_to, acknowledged_by, created_by, created_at |
| Reminders | yes | created_by, delivered_to, acknowledged_by |
| Household Memory | yes | created_by, created_at, explanation_source, attribution_confidence |
| Productivity Write Actions | yes | created_by, created_via, created_at, explanation_source |
| Coordination Actions | yes | created_by, assigned_to, created_in_room, created_via, attribution_confidence |

---

## Shopping Provenance

Shopping provenance must support:

- added_by
- completed_by
- created_at
- attribution confidence

Shopping consumes provenance.

Shopping does not own provenance.

---

## Task Provenance

Task provenance must support:

- created_by
- assigned_to
- completed_by
- created_at
- completed_at

Tasks consume provenance.

Tasks do not own provenance.

---

## Message Provenance

Message provenance must support:

- delivered_to
- acknowledged_by
- created_by
- created_at

Messages consume provenance.

---

## Reminder Provenance

Reminder provenance must support:

- created_by
- delivered_to
- acknowledged_by

Reminders consume provenance.

---

## Household Memory Relationship

Household Memory consumes provenance.

Provenance remains authoritative.

Household Memory may not redefine attribution.

---

## Productivity Write Action Relationship

Productivity write actions consume provenance.

Provenance remains authoritative.

---

## Multi-Item Capture Relationship

Multi-item capture must propagate provenance.

No derived item may lose provenance.

Align with V2-C9d.

---

## Explainability Requirements

Human explainability must support:

- Who did this?
- Who created this?
- Who completed this?
- Why do we believe this?
- Where did this come from?

Machine explainability must support:

- provenance field values
- lineage references
- attribution confidence
- timestamps
- source references

---

## Non-Rights

Provenance does not own:

- identity
- room truth
- occupancy truth
- memory
- shopping records
- task records
- messages
- reminders
- execution

---

## Determinism Requirements

Required rules:

- same lineage inputs -> same provenance result
- same confidence inputs -> same attribution result
- same source references -> same explanation outcome

Prohibited behavior:

- hidden attribution
- hidden lineage
- hidden provenance generation

---

## Provenance Field Applicability Matrix

| Field | Shopping | Tasks | Messages | Reminders | Memory | Productivity |
|---|---|---|---|---|---|---|
| created_by | yes | yes | yes | yes | yes | yes |
| added_by | yes | no | no | no | no | yes |
| assigned_to | no | yes | no | no | no | yes |
| completed_by | yes | yes | no | no | no | yes |
| delivered_to | no | no | yes | yes | no | yes |
| acknowledged_by | no | no | yes | yes | no | yes |
| created_at | yes | yes | yes | yes | yes | yes |
| completed_at | yes | yes | no | no | no | yes |
| created_in_room | yes | yes | yes | yes | yes | yes |
| created_via | yes | yes | yes | yes | yes | yes |
| attribution_confidence | yes | yes | yes | yes | yes | yes |
| explanation_source | yes | yes | yes | yes | yes | yes |

---

## Boundary Review

This contract preserves explicit separation between:

- Provenance
- Identity
- Household Memory
- Shopping
- Tasks
- Messages
- Reminders

Separation rules:

- Provenance defines attribution and lineage semantics only
- Identity remains authoritative in Voice Identity
- Household Memory may consume provenance without redefining it
- Shopping, Tasks, Messages, and Reminders consume provenance and do not own it
- provenance duplication elsewhere is prohibited

Ownership overlap is prohibited.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Provenance.

Future planning must treat this contract as a mandatory dependency for:

- E9 planning
- E10 planning
- E12 planning
- E13 planning
- E14 planning

This contract becomes a foundational authority for multiple future epics.

---

## Final Principle

Provenance provides canonical, explainable attribution and lineage semantics across HTBW while leaving identity, room truth, occupancy truth, memory, and execution outside its authority.