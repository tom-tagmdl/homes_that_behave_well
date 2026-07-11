# Household Memory Model

## Purpose

The Household Memory Model defines how Concierge represents household memory references and their relationships to provenance, events, occupancy-aware context, visibility boundaries, and explanations.

This model is a consumption model for memory references, memory relationships, explanation references, and memory visibility references.

This model does not define:

- storage implementation
- retrieval engines
- memory indexing
- memory query behavior
- provenance semantics

---

## Model Definition

Household Memory Model is:

A consumption model representing household memory references and their relationships to provenance, events, occupancy-aware context, visibility boundaries, and explanations.

The model is NOT:

- a storage model
- a retrieval model
- a provenance authority
- a memory governance authority

Household Memory Model consumes governed inputs from Household Memory Contract authority, Provenance Contract authority, Provenance Model authority, Event Model authority, and occupancy-aware context where policy allows.

---

## Canonical Model Structure

Required fields:

household_memory:
  memory_reference_id: memoryref_01J...
  memory_references: []
  provenance_references: []
  event_references: []
  explanation_references: []
  memory_state: active
  timestamp: 2026-07-10T12:00:00Z

Required metadata:

- memory_state
- timestamp

---

## Memory Reference Representation

Memory references represent the household memory items and their visibility references.

Required concepts:

- memory references
- memory visibility references
- memory lineage references

Rules:

- the model represents memories
- the model does not store memories
- memory references remain consumption-only and explainable

---

## Provenance Reference Representation

Provenance references represent attribution and provenance linkage for memory items.

Required concepts:

- provenance references
- provenance linkage
- attribution linkage

Rules:

- the model consumes provenance
- the model does not recreate provenance fields
- do not duplicate created_by, assigned_to, attribution_confidence, or explanation_source

The Household Memory Model must reference [docs/models/provenance-model.md](provenance-model.md).

---

## Event Reference Representation

Event references represent event lineage and event relationships associated with memory items.

Required concepts:

- event references
- event lineage
- event relationships

Rules:

- Event Model remains authoritative
- the model consumes event context only
- the model does not define event execution

---

## Explanation Reference Representation

Explanation references represent explanation references, explanation visibility, and explanation linkage.

Required concepts:

- explanation references
- explanation visibility
- explanation linkage

Rules:

- the model represents explanation references only
- the model does not own explanation rendering
- explanation authority remains external

---

## Optional Memory Metadata

The following memory metadata may be included when useful and contract-compatible:

- retention_marker
- visibility_marker
- future_memory_extension

Evaluation:

- retention_marker: include when a downstream consumer needs a bounded retention reference for memory lifecycle interpretation without defining retention policy
- visibility_marker: include when visibility state needs a compact reference for explainability or downstream filtering
- future_memory_extension: include when a controlled placeholder is needed for future memory-aware capabilities without expanding the canonical core

These fields are optional because the base model must remain stable and reference-based.

---

## Provenance Relationship

Household Memory consumes Provenance Model.

Provenance Model remains authoritative.

No provenance field duplication is permitted.

---

## Event Relationship

Household Memory consumes Event Model.

Event authority remains external.

---

## Interaction Relationship

Household Memory may reference Interaction Model context.

Interaction authority remains external.

---

## Person Relationship

Household Memory may reference Person Profile.

Identity authority remains external.

---

## Room Relationship

Household Memory may reference Room Model context.

Room authority remains external.

---

## Occupancy Relationship

Household Memory may reference occupancy-sensitive context.

Occupancy remains external.

No occupancy semantics may be defined here.

---

## Restoration Relationship

Experience Restoration Context may consume memory references.

Household Memory does not own restoration behavior.

---

## Explanation Surface Relationship

Explanatory experiences may consume memory references.

Household Memory does not own explanation rendering.

---

## Guest-Safe Visibility

Guests may receive:

- restricted visibility
- neutral visibility
- no visibility

Unknown identities may receive:

- restricted visibility
- neutral visibility

The model supports visibility boundaries through references only.

Do not create guest policy.

---

## Explainability References

Explainability references support answers to:

- why a memory exists
- where a memory originated
- how a memory is linked
- why a memory is visible

Required references:

- explanation_reference
- memory_reference
- provenance_reference

---

## Explainability Requirements

Human explainability must support:

- Why is this memory present?
- Where did this memory come from?
- Why is this memory visible?
- How is this memory connected?

Machine explainability must support:

- memory identifiers
- provenance references
- event references
- explanation references
- timestamps

---

## Provenance Requirements

The Household Memory Model must consume the Provenance Model.

The Household Memory Model may not define alternate attribution fields.

The Household Memory Model may not duplicate canonical provenance semantics.

---

## Non-Rights

Household Memory Model does not own:

- provenance semantics
- storage implementation
- retrieval behavior
- occupancy semantics
- identity resolution
- explanation rendering

---

## Model Example

household_memory:
  memory_reference_id: memoryref_01J123ABCDEF0001
  memory_references:
    - memory_reference: memory.bedtime_routine.living_room
      memory_visibility_reference: memory.visibility.restricted
      memory_lineage_reference: memory.lineage.01J123ABCDEF0001
  provenance_references:
    - provenance_reference: prov_01J123ABCDEF0001
      provenance_linkage: provenance.linkage.memory.bedtime_routine
      attribution_linkage: attribution.linkage.person.tom
  event_references:
    - event_reference: evt_01J123ABCDEF9999
      event_lineage: event.lineage.bedtime_routine
      event_relationship: source_event
  explanation_references:
    - explanation_reference: explain.memory.bedtime_routine
      memory_reference: memory.bedtime_routine.living_room
      provenance_reference: prov_01J123ABCDEF0001
      visibility_reference: memory.visibility.restricted
  memory_state: active
  timestamp: 2026-07-10T12:00:00Z

This example is illustrative only.

---

## Model Coverage Matrix

| Memory Feature | Supported | Notes |
|---|---|---|
| memory references | yes | represented as consumption-only references |
| provenance references | yes | provenance model is referenced, not recreated |
| event references | yes | event references are explicit and external |
| explanation references | yes | explanation links remain reference-only |
| event relationship | yes | event context is consumed without authority transfer |
| interaction relationship | yes | interaction context may be referenced |
| room relationship | yes | room context may be referenced |
| person relationship | yes | person profile may be referenced |
| occupancy relationship | yes | occupancy-sensitive context may be referenced |
| restoration relationship | yes | restoration context may consume memory references |
| explanation surfaces | yes | explanatory experiences may consume memory references |
| guest-safe visibility | yes | restricted, neutral, and no visibility states are supported |

---

## Contract / Model Alignment Review

### Contract Authorities

The Household Memory Contract owns memory governance, memory visibility semantics, memory retention semantics, and memory explanation semantics.

The Provenance Contract owns attribution semantics, provenance semantics, and canonical provenance fields.

### Model Responsibilities

The Household Memory Model owns memory reference representation, memory relationship representation, memory explanation representation, and memory visibility references as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Household Memory consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E10 Household Memory Planning
- Memory-Aware Experiences
- Memory-Aware Productivity Experiences
- Household Summarization

This model consumes Household Memory Contract authority, Provenance Contract authority, Provenance Model authority, and Event Model authority.

---

## Final Principle

Household Memory Model represents governed memory references and relationships.

It does not own provenance semantics, storage, retrieval behavior, occupancy semantics, identity resolution, or explanation rendering.

It preserves the Household Memory Contract and Provenance Contract as the authorities for memory governance and attribution semantics.