# Provenance Model

## Purpose

The Provenance Model defines how Homes That Behave Well represents attribution, provenance lineage, attribution confidence, and explanation references for downstream consumption.

This model is a consumption model for canonical provenance fields, attribution representation, explainability references, and provenance relationships.

This model does not define:

- storage implementation
- write paths
- attribution algorithms
- identity resolution
- occupancy semantics

---

## Model Definition

Provenance Model is:

A canonical consumption model representing attribution, provenance lineage, attribution confidence, and explanation references used throughout Homes That Behave Well.

This model is the authoritative provenance representation.

The model is NOT:

- a storage model
- a write-path model
- an identity authority
- a provenance governance authority

Provenance Model consumes governed inputs from Provenance Contract authority, Event Model authority, and Interaction Model authority.

---

## Canonical Model Structure

Required fields:

provenance:
  provenance_id: prov_01J...
  created_by:
    actor_reference:
      person_id: person.tom
    actor_state: known
    provenance_reference: provenance.created_by.01J...
  added_by:
    actor_reference:
      person_id: person.tom
    actor_state: known
    provenance_reference: provenance.added_by.01J...
  assigned_to:
    target_reference:
      person_id: person.jane
    target_state: known
    provenance_reference: provenance.assigned_to.01J...
  completed_by:
    actor_reference:
      person_id: person.tom
    actor_state: known
    provenance_reference: provenance.completed_by.01J...
  delivered_to:
    destination_reference:
      person_id: person.jane
    destination_state: known
    provenance_reference: provenance.delivered_to.01J...
  acknowledged_by:
    actor_reference:
      person_id: person.jane
    actor_state: known
    provenance_reference: provenance.acknowledged_by.01J...
  created_at: 2026-07-10T12:00:00Z
  completed_at: 2026-07-10T12:10:00Z
  created_in_room:
    room_reference:
      area_id: living_room
    room_state: known
    room_lineage_reference: provenance.room.living_room.01J...
  created_via:
    method: voice
    interaction_pathway: voice_command
    attribution_pathway: direct_action
  attribution_confidence:
    value: 0.92
    confidence_state: explicit
    visibility_state: explicit
    confidence_explainability_reference: explain.provenance.confidence.01J...
  explanation_source:
    source_reference: provenance.explainability.source.01J...
    lineage_reference: provenance.lineage.01J...
    attribution_explanation_references: []
  timestamp: 2026-07-10T12:10:00Z
  provenance_state: known

Required metadata:

- timestamp
- provenance_state

---

## Created By Representation

Created By represents the actor or system state that originated the artifact or action.

Rules:

- preserve identity authority elsewhere
- preserve provenance semantics from the contract
- use explicit actor references rather than inferred authorship

Created By may reference:

- person identifiers
- guest actor states
- unknown actor states
- system actor states

---

## Added By Representation

Added By represents the actor or system state that appended an item to a governed collection or context.

Rules:

- preserve identity authority elsewhere
- preserve contract semantics
- keep addition lineage explicit and explainable

Added By may reference:

- person identifiers
- guest actor states
- unknown actor states
- system actor states

---

## Assigned To Representation

Assigned To represents the target of a governed assignment or routing decision.

Rules:

- preserve identity authority elsewhere
- preserve assignment semantics from the contract
- do not infer ownership beyond the assigned target reference

Assigned To may reference:

- person identifiers
- room-linked targets when contract-authorized
- unknown targets when assignment is unresolved

---

## Completed By Representation

Completed By represents the actor or system state that completed the governed artifact or workflow.

Rules:

- preserve identity authority elsewhere
- preserve completion semantics from the contract
- do not conflate completion with ownership

Completed By may reference:

- person identifiers
- guest actor states
- unknown actor states
- system actor states

---

## Delivered To Representation

Delivered To represents the destination or recipient of a governed delivery.

Rules:

- preserve identity authority elsewhere
- preserve delivery semantics from the contract
- keep delivery lineage explicit and explainable

Delivered To may reference:

- person identifiers
- room-scoped delivery targets when contract-authorized
- unknown destinations when delivery is unresolved

---

## Acknowledged By Representation

Acknowledged By represents the actor or system state that acknowledged the governed artifact.

Rules:

- preserve identity authority elsewhere
- preserve acknowledgement semantics from the contract
- do not infer intent from acknowledgement alone

Acknowledged By may reference:

- person identifiers
- guest actor states
- unknown actor states
- system actor states

---

## Created At Representation

Created At represents the creation timestamp for the governed artifact.

Rules:

- represent the timestamp only
- do not define lifecycle behavior
- preserve temporal traceability without altering source-of-record authority

---

## Completed At Representation

Completed At represents the completion timestamp for the governed artifact.

Rules:

- represent the timestamp only
- do not define lifecycle behavior
- preserve temporal traceability without altering source-of-record authority

---

## Created In Room Representation

Created In Room represents room lineage and room context references associated with the origin event.

Rules:

- room authority remains external
- room context is referenced, not owned
- room lineage must remain traceable to Foundation room truth

---

## Created Via Representation

Created Via represents the creation source, interaction pathway, and attribution pathway.

Rules:

- the model represents provenance
- the model does not define behavior
- the model does not define execution paths

Created Via may include:

- voice
- ui
- automation
- provider_event
- scheduled_action
- system_generated

---

## Attribution Confidence Representation

Attribution Confidence represents the confidence associated with attribution.

Rules:

- the model consumes confidence
- the model does not calculate confidence
- confidence visibility and explainability must remain explicit

Attribution Confidence may include:

- value
- confidence class
- visibility state
- confidence explainability references

---

## Explanation Source Representation

Explanation Source represents the explanation origin, explanation lineage, and attribution explanation references.

Rules:

- this field is mandatory
- the model must preserve explanation origin and lineage explicitly
- explanation source must remain traceable to governed upstream context

---

## Optional Domain Extensions

The following domain extension metadata may be included when useful and contract-compatible:

- domain_extension
- extension_reference
- future_extension_marker

Evaluation:

- domain_extension: include only when a downstream consumer needs a contract-authorized domain-specific provenance extension that still preserves canonical provenance semantics
- extension_reference: include when a controlled extension needs a durable reference for traceability or diagnostics
- future_extension_marker: include when a future provenance-aware capability needs a placeholder without altering the canonical core

These fields are optional because the canonical model must remain stable and authoritative without requiring domain-specific extensions.

---

## Event Relationship

Provenance references Event Model.

Event Model remains authoritative.

Provenance does not own event execution.

---

## Interaction Relationship

Provenance references Interaction Model.

Interaction remains authoritative.

---

## Household Memory Relationship

Household Memory consumes Provenance.

Provenance does not own memory.

Aligns with C8.

---

## Task and Shopping Relationship

Task and Shopping experiences consume Provenance.

Provenance remains authoritative.

Aligns with C9b.

---

## Calendar and Email Relationship

Calendar and Email experiences consume Provenance.

Aligns with C9a.

---

## Knowledge / Briefing Relationship

Knowledge, Briefing, and Status experiences consume Provenance.

Aligns with C9c.

---

## Multi-Item Capture Relationship

Multi-Item Capture consumes Provenance.

Aligns with C9d.

---

## Person Relationship

Provenance may reference persons.

Identity authority remains external.

---

## Room Relationship

Provenance may reference rooms.

Room authority remains external.

---

## Occupancy Relationship

Provenance may reference occupancy-derived context.

Occupancy remains authoritative.

No occupancy semantics may be defined here.

---

## Guest-Safe Attribution

Guest attribution states:

- guest attribution
- unknown attribution
- unresolved attribution

The model must support attribution uncertainty.

Do not invent identities.

---

## Explainability References

Explainability references support answers to:

- who performed an action
- how attribution was determined
- why attribution confidence exists
- where explanation originated

Required references:

- explanation_source
- attribution_confidence
- provenance_reference

---

## Explainability Requirements

Human explainability must support:

- Who did this?
- How do we know?
- Why is confidence high or low?
- Where did this attribution originate?

Machine explainability must support:

- provenance identifiers
- attribution identifiers
- confidence identifiers
- explanation references
- timestamps

---

## Provenance Requirements

This is the canonical provenance model.

All future provenance-aware models must consume these fields.

No alternate provenance semantics are permitted.

---

## Non-Rights

Provenance Model does not own:

- storage implementation
- write-path behavior
- identity resolution
- occupancy semantics
- event execution
- interaction execution

---

## Model Example

provenance:
  provenance_id: prov_01J123ABCDEF0001
  created_by:
    actor_reference:
      person_id: person.tom
    actor_state: known
    provenance_reference: provenance.created_by.01J123ABCDEF0001
  assigned_to:
    target_reference:
      person_id: person.jane
    target_state: known
    provenance_reference: provenance.assigned_to.01J123ABCDEF0001
  completed_by:
    actor_reference:
      person_id: person.tom
    actor_state: known
    provenance_reference: provenance.completed_by.01J123ABCDEF0001
  created_in_room:
    room_reference:
      area_id: living_room
    room_state: known
    room_lineage_reference: provenance.room.living_room.01J123ABCDEF0001
  created_via:
    method: voice
    interaction_pathway: voice_command
    attribution_pathway: direct_action
  attribution_confidence:
    value: 0.92
    confidence_state: explicit
    visibility_state: explicit
    confidence_explainability_reference: explain.provenance.confidence.01J123ABCDEF0001
  explanation_source:
    source_reference: provenance.explainability.source.01J123ABCDEF0001
    lineage_reference: provenance.lineage.01J123ABCDEF0001
    attribution_explanation_references:
      - explain.provenance.created_by.01J123ABCDEF0001
  created_at: 2026-07-10T12:00:00Z
  completed_at: 2026-07-10T12:10:00Z
  timestamp: 2026-07-10T12:10:00Z
  provenance_state: known

This example is illustrative only.

---

## Model Coverage Matrix

| Provenance Feature | Supported | Notes |
|---|---|---|
| created_by | yes | explicit actor representation with provenance reference |
| added_by | yes | explicit actor representation with provenance reference |
| assigned_to | yes | explicit target representation with provenance reference |
| completed_by | yes | explicit actor representation with provenance reference |
| delivered_to | yes | explicit destination representation with provenance reference |
| acknowledged_by | yes | explicit actor representation with provenance reference |
| created_at | yes | represented as canonical timestamp |
| completed_at | yes | represented as canonical timestamp |
| created_in_room | yes | room lineage and context references are explicit |
| created_via | yes | creation source and interaction pathway are explicit |
| attribution_confidence | yes | represented, not calculated |
| explanation_source | yes | mandatory explanation origin and lineage reference |
| household memory | yes | memory consumers can reference provenance |
| productivity experiences | yes | productivity experiences can consume provenance |
| multi-item capture | yes | capture workflows can consume provenance |
| guest-safe attribution | yes | guest, unknown, and unresolved states are represented |

---

## Contract / Model Alignment Review

### Contract Authority

The Provenance Contract owns provenance governance, attribution semantics, provenance field definitions, confidence semantics, and explanation semantics.

### Model Responsibilities

The Provenance Model owns provenance data representation, canonical provenance field representation, provenance explainability representation, and provenance relationships as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Provenance consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E10 Household Memory Planning
- E13 Productivity Experiences
- E14 Multi-Item Capture
- Future attribution-aware planning

This model consumes Provenance Contract authority, Event Model authority, and Interaction Model authority.

---

## Final Principle

Provenance Model represents canonical attribution and lineage semantics.

It does not own storage, write paths, identity resolution, occupancy semantics, event execution, or interaction execution.

It preserves the Provenance Contract as the authority for provenance governance and explanation semantics.