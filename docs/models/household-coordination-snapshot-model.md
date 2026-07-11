# Household Coordination Snapshot Model

## Purpose

The Household Coordination Snapshot Model defines how Concierge represents a point-in-time household coordination view across calendar, tasks, shopping, messaging, and home status domains.

This model is a consumption model for coordination snapshot representation, cross-domain coordination references, coordination visibility references, and coordination explainability references.

This model does not define:

- coordination engines
- synthesis algorithms
- prioritization behavior
- orchestration logic

---

## Model Definition

Household Coordination Snapshot Model is:

A consumption model representing a point-in-time household coordination view assembled from governed experience references across multiple domains.

The model is NOT:

- a coordination engine
- a planning engine
- a synthesis engine
- a governance authority

Household Coordination Snapshot Model consumes governed inputs from Household Coordination Contract authority, Knowledge, Briefing, and Household Status Synthesis Contract authority, Calendar Experience Model authority, Task Experience Model authority, Shopping Experience Model authority, Email Experience Model authority, Briefing Composition Model authority, Knowledge Query Experience Model authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

coordination_snapshot:
  coordination_snapshot_id: coordsnap_01J...
  calendar_references: []
  task_references: []
  shopping_references: []
  messaging_references: []
  home_status_references: []
  coordination_explainability_references: []
  provenance_references: []
  timestamp: 2026-07-10T12:00:00Z
  coordination_snapshot_state: active

Required metadata:

- coordination_snapshot_id
- timestamp
- coordination_snapshot_state

Coordination snapshot state is a governed presentation state and may be active, restricted, simplified, or unknown when contract-authorized.

---

## Calendar Reference Representation

Calendar reference representation captures scheduling awareness and coordination-aware calendar context.

Required concepts:

- calendar references
- scheduling awareness references
- coordination-aware calendar references

Rules:

- Calendar Experience remains authoritative
- the model does not own calendar truth
- the model does not define schedule behavior

---

## Task Reference Representation

Task reference representation captures task awareness and task-related coordination context.

Required concepts:

- task references
- ownership references
- due-awareness references

Rules:

- Task Experience remains authoritative
- the model does not own task truth
- the model does not define task behavior

---

## Shopping Reference Representation

Shopping reference representation captures shopping awareness and coordination shopping context.

Required concepts:

- shopping references
- shopping awareness references
- coordination shopping references

Rules:

- Shopping Experience remains authoritative
- the model does not own shopping truth
- the model does not define shopping behavior

---

## Messaging Reference Representation

Messaging reference representation captures household communication and coordination communication context.

Required concepts:

- messaging references
- household communication references
- coordination communication references

Rules:

- messaging authority remains external
- the model does not own messaging truth
- the model does not define delivery behavior

---

## Home Status Reference Representation

Home status reference representation captures household condition and coordination status context.

Required concepts:

- home status references
- household condition references
- coordination status references

Rules:

- home status authority remains external
- the model does not own home status truth
- the model does not define status computation

---

## Optional Coordination Metadata

The following coordination metadata may be included when useful and contract-compatible:

- urgency_reference
- open_loop_reference
- errand_grouping_reference

Evaluation:

- urgency_reference: include when a downstream coordination consumer needs a governed urgency marker as a reference only, without introducing prioritization logic
- open_loop_reference: include when unfinished-work context should be preserved as a reference for explainability or grouping
- errand_grouping_reference: include when errands need a compact grouping reference for coordination surfaces without defining grouping algorithms

These fields may only exist as references. Do not define prioritization algorithms.

---

## Calendar Experience Relationship

Household Coordination Snapshot consumes Calendar Experience references.

Calendar Experience remains authoritative.

---

## Task Experience Relationship

Household Coordination Snapshot consumes Task Experience references.

Task Experience remains authoritative.

---

## Shopping Experience Relationship

Household Coordination Snapshot consumes Shopping Experience references.

Shopping Experience remains authoritative.

---

## Email Experience Relationship

Household Coordination Snapshot may consume Email Experience references.

Email Experience remains authoritative.

---

## Briefing Composition Relationship

Briefing Composition may consume Coordination Snapshot references.

Coordination Snapshot does not own briefing behavior.

---

## Household Status Synthesis Relationship

Household Status Synthesis may consume Coordination Snapshot references.

Coordination Snapshot does not own synthesis behavior.

---

## Knowledge Experience Relationship

Knowledge Query Experience may contribute context references.

Knowledge Experience remains authoritative.

---

## Provenance Relationship

Coordination Snapshot may consume provenance-aware submodels.

No alternate attribution semantics permitted.

---

## Household Memory Relationship

Coordination Snapshot may consume Household Memory references.

Household Memory remains authoritative.

---

## Room Relationship

Coordination Snapshot may reference Room context.

Room authority remains external.

---

## Person Relationship

Coordination Snapshot may reference Person Profile context.

Identity authority remains external.

---

## Occupancy Relationship

Coordination Snapshot may reference occupancy-sensitive context.

Occupancy remains externally governed.

No occupancy semantics may be defined here.

---

## Guest-Safe Visibility

Guests may receive:

- restricted coordination visibility
- simplified coordination visibility
- no coordination visibility

Unknown identities may receive:

- restricted visibility
- simplified visibility

The model supports coordination boundaries through references only.

---

## Explainability References

Explainability references support answers to:

- why a coordination item was included
- why a task appears in the snapshot
- why a shopping item appears in the snapshot
- why a coordination grouping exists

Required references:

- explanation_reference
- coordination_reference
- source_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why is this item in the coordination view?
- Why is this task included?
- Why is this shopping item included?
- Why is this grouped together?

Machine explainability must support:

- coordination identifiers
- source references
- task references
- calendar references
- timestamps

---

## Provenance Requirements

Coordination Snapshot may consume provenance-aware references from contributing experience models.

The model may not define attribution semantics.

The model may not duplicate provenance semantics.

---

## Non-Rights

Household Coordination Snapshot Model does NOT own:

- coordination engines
- prioritization
- synthesis algorithms
- orchestration
- provider integrations
- provenance semantics
- occupancy semantics

---

## Model Example

Example structure:

coordination_snapshot:
  coordination_snapshot_id: coordsnap_01J...
  calendar_references:
    - coordination_reference_id: calcoord_01J...
      calendar_reference:
        calendar_id: calendar.family
      provenance_reference: provenance.calendar.01J...
  task_references:
    - coordination_reference_id: taskcoord_01J...
      task_reference:
        task_id: task.family.01J...
      provenance_reference: provenance.task.01J...
  shopping_references:
    - coordination_reference_id: shopcoord_01J...
      shopping_reference:
        shopping_item_id: shopping.family.01J...
      provenance_reference: provenance.shopping.01J...
  messaging_references:
    - coordination_reference_id: msgcoord_01J...
      messaging_reference:
        message_id: message.family.01J...
      provenance_reference: provenance.messaging.01J...
  home_status_references:
    - coordination_reference_id: statuscoord_01J...
      home_status_reference:
        status_id: home.status.01J...
      provenance_reference: provenance.status.01J...
  coordination_explainability_references:
    - explanation_reference_id: explain_01J...
      coordination_reference:
        coordination_snapshot_id: coordsnap_01J...
      source_reference:
        source_id: calendar.family
      provenance_reference: provenance.explainability.01J...
  provenance_references:
    - provenance_reference_id: provenance.coordination_snapshot.01J...
  timestamp: 2026-07-10T12:00:00Z
  coordination_snapshot_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Coordination Feature | Supported | Notes |
|---|---|---|
| calendar references | yes | calendar references are consumed without owning calendar truth |
| task references | yes | task references are consumed without owning task behavior |
| shopping references | yes | shopping references are consumed without owning shopping behavior |
| messaging references | yes | messaging references are consumed without owning messaging truth |
| home status references | yes | home status references are consumed without owning status truth |
| briefing relationship | yes | snapshot references may participate in briefing without owning briefing behavior |
| household status synthesis relationship | yes | snapshot references may participate in synthesis without owning synthesis behavior |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |
| coordination metadata references | yes | metadata remains reference-only and avoids prioritization algorithms |

---

## Contract / Model Alignment Review

1. Contract authorities.

   The Household Coordination Contract defines coordination governance, coordination semantics, coordination visibility semantics, and coordination planning semantics. The Knowledge, Briefing, and Household Status Synthesis Contract governs related briefing and synthesis boundaries.

2. Model responsibilities.

   Household Coordination Snapshot Model represents cross-domain coordination references, visibility references, and explainability references without taking ownership of engines, prioritization, synthesis, orchestration, or provider behavior.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Household Coordination Snapshot Model is the authoritative bridge between the Household Coordination Contract and E14 Household Coordination consumption.

Future E14 Household Coordination must treat [docs/models/household-coordination-snapshot-model.md](../models/household-coordination-snapshot-model.md) as authoritative.

Future Coordination Experiences must treat [docs/models/household-coordination-snapshot-model.md](../models/household-coordination-snapshot-model.md) as authoritative.

Future Household Planning must treat [docs/models/household-coordination-snapshot-model.md](../models/household-coordination-snapshot-model.md) as authoritative.

Future Household Status Synthesis must treat [docs/models/household-coordination-snapshot-model.md](../models/household-coordination-snapshot-model.md) as authoritative.

Household Coordination Snapshot Model consumes Household Coordination Contract authority, Knowledge, Briefing, and Household Status Synthesis Contract authority, Calendar Experience Model authority, Task Experience Model authority, Shopping Experience Model authority, Email Experience Model authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.
