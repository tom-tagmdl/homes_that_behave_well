# Capability Projection Model

## Purpose

The Capability Projection Model defines how Concierge represents projected capability sets for downstream consumption.

This model is a consumption model for projected capabilities, availability results, filtering outcomes, unsupported capabilities, and explainability references.

This model does not define:

- projection engines
- filtering logic
- service execution
- runtime orchestration

---

## Model Definition

Capability Projection Model is:

A consumption model representing the projected capability set available to Concierge after governance, filtering, visibility, occupancy, identity, and contextual considerations have been applied.

The model is not:

- projection authority
- filtering authority
- service authority
- execution authority

Capability projection remains governed by the Capability Projection Contract.

---

## Canonical Model Structure

Required fields:

capability_projection:
  projection_id: capproj_01J...
  projected_capabilities: []
  available_capabilities: []
  filtered_capabilities: []
  unsupported_capabilities: []
  explainability_references: []
  room_reference:
    area_id: living_room
  person_reference:
    person_id: person.tom
  occupancy_reference:
    occupancy_state: occupied
  timestamp: 2026-07-10T12:00:00Z

Required metadata:

- room_reference
- person_reference
- occupancy_reference
- timestamp

---

## Projected Capabilities

Projected capabilities represent the capability set visible to Concierge after governed projection.

Projected capabilities may include:

- capability identifiers
- visibility-ready capability labels
- capability presentation hints

Rules:

- projected capabilities represent results, not logic
- projected capabilities must remain deterministic for identical governed inputs
- projected capabilities must remain explainable

---

## Available Capabilities

Available capabilities represent the subset of projected capabilities eligible for use in the current context.

Availability semantics remain governed by the Capability Projection Contract.

Rules:

- available capabilities must reference governed capability identifiers
- availability must remain explainable
- available capabilities do not define execution eligibility outside governed projection outputs

---

## Filtered Capabilities

Filtered capabilities represent capabilities removed from the visible set by governed projection outcomes.

Filtered capability entries may include:

- capability identifiers
- filter reference identifiers
- filter rationale references

Rules:

- the model does not implement filtering
- filtered capabilities represent outcomes only
- filter rationale must remain explainable when provided

---

## Unsupported Capabilities

Unsupported capabilities represent capabilities that are known but unavailable, inaccessible, or inapplicable in the current context.

Unsupported entries may include:

- capability identifiers
- unsupported reason references
- explainability references

Rules:

- unsupported status must remain explainable
- unsupported capabilities must not be collapsed into available capabilities
- unsupported capabilities must not imply capability ownership transfer

---

## Explainability References

Explainability references support answers to:

- Why is this capability available?
- Why is this capability filtered?
- Why is this capability unsupported?

Required model references:

- explainability_reference
- projection_reference
- contract_reference

Rules:

- explainability references support explanation only
- explainability references do not implement explanation logic
- explainability references must remain traceable to governed contract and projection context

---

## Optional Lineage References

The following lineage references may be included when contract-authorized:

- source_lineage_reference
- filter_rationale_reference
- contract_version_reference

Evaluation:

- source_lineage_reference: include when a downstream consumer needs traceable origin context for a projected capability outcome
- filter_rationale_reference: include when a filtered capability needs explicit rationale lineage for explanation or debugging support
- contract_version_reference: include when the consumer needs a contract-version anchor for reproducibility or review

These references are optional because the base model must remain stable even when detailed lineage is not required.

---

## Room Relationship

Capability Projection references Room Model.

Room Model remains authoritative.

Capability Projection does not own room truth.

---

## Person Relationship

Capability Projection references Person Profile.

Capability Projection consumes identity context.

Capability Projection does not own identity.

---

## Occupancy Relationship

Capability Projection may consume occupancy context.

Capability Projection does not own occupancy semantics.

Occupancy Contract and Occupancy Model remain authoritative.

---

## Guest-Safe Filtering Relationship

Capability Projection supports guest-filtered capability representation.

Guest-safe policy remains governed externally.

The model represents outcomes only.

---

## Experience Selection Relationship

Experience Projection consumes Capability Projection.

Capability Projection does not own experience selection.

This aligns with the Experience Projection Contract.

---

## Provenance Relationship

Capability Projection may reference provenance lineage.

Provenance remains authoritative.

Capability Projection does not own provenance.

---

## Household Memory Relationship

Household Memory may reference projected capabilities as context.

Capability Projection does not own memory.

---

## Productivity Relationship

Calendar and Email, Task and Shopping, Knowledge, Briefing, Household Status Synthesis, and Multi-Item Capture experiences may consume capability projections.

Capability Projection does not own productivity experiences.

---

## Explainability Requirements

Human explainability must support:

- Why is this capability available?
- Why is this capability filtered?
- Why is this capability unsupported?
- Why was this capability shown?

Machine explainability must support:

- capability identifiers
- explainability references
- projection references
- filter rationale references
- timestamps

---

## Provenance Requirements

Capability Projection may reference lineage.

Capability Projection is not a provenance authority.

Capability Projection does not own attribution.

---

## Non-Rights

Capability Projection Model does not own:

- capability governance
- capability filtering
- capability execution
- room truth
- person truth
- occupancy truth
- provenance
- experience selection

---

## Model Example

capability_projection:
  projection_id: capproj_01J123ABCDEF0001
  projected_capabilities:
    - capability_id: lights.turn_on
      display_label: Lights
  available_capabilities:
    - capability_id: lights.turn_on
      availability_state: available
  filtered_capabilities:
    - capability_id: media.play_music
      filter_reference: filter.guest_safe_media
      rationale_reference: explain.capability.guest_safe
  unsupported_capabilities:
    - capability_id: thermostat.set_temperature
      unsupported_reason: unavailable_in_room_context
      explainability_reference: explain.capability.room_unavailable
  explainability_references:
    - explainability_reference: explain.capability.available.lights
      projection_reference: projection.room.living_room
      contract_reference: docs/contracts/capability-projection-contract.md
  room_reference:
    area_id: living_room
  person_reference:
    person_id: person.tom
  occupancy_reference:
    occupancy_state: occupied
  timestamp: 2026-07-10T12:00:00Z

This example is illustrative only.

---

## Model Coverage Matrix

| Capability Area | Supported | Notes |
|---|---|---|
| projected capabilities | yes | projected capability results are represented |
| available capabilities | yes | availability is represented as a projected outcome |
| filtered capabilities | yes | filter outcomes and references are represented |
| unsupported capabilities | yes | unsupported outcomes are represented |
| explainability references | yes | explanation-supporting references are represented |
| room references | yes | room context is represented via room_reference |
| person references | yes | identity context is represented via person_reference |
| occupancy references | yes | occupancy context is represented via occupancy_reference |
| guest-safe filtering | yes | guest-safe outcomes are represented as filtered projection results |
| provenance references | yes | lineage references may be represented when contract-authorized |

---

## Contract / Model Alignment Review

### Contract Authority

The Capability Projection Contract owns projection governance, availability semantics, visibility semantics, filtering semantics, and explainability expectations.

### Model Responsibilities

The Capability Projection Model owns projected result shape, projected capability relationships, explainability references, and consumption-only representation of projection outcomes.

### Gaps Identified

No authority gap is introduced by this model.

Potential follow-up work for downstream planning:

- confirm consumers preserve this model as a consumption boundary
- confirm runtime projection code emits shapes compatible with this model

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Capability Projection consumption boundary.

Future planning must treat this model as a mandatory dependency for:

- E5 Capability Projection Planning
- Coordinator V2
- Experience Projection
- productivity experience planning
- status synthesis

---

## Final Principle

The Capability Projection Model represents governed projection outcomes.

It does not decide capability visibility.

It does not execute capabilities.

It preserves the Capability Projection Contract as the authority for projection semantics.