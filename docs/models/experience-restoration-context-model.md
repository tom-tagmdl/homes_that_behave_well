# Experience Restoration Context Model

## Purpose

The Experience Restoration Context Model defines how Concierge represents restoration candidates and restoration decision inputs for planning and suppression analysis.

This model is a consumption model for restoration candidate representation, restoration context representation, occupancy references, confidence references, and restoration explainability references.

This model does not define:

- restoration execution
- orchestration
- runtime behavior
- policy evaluation logic

---

## Model Definition

Experience Restoration Context Model is:

A consumption model representing restoration candidates, restoration decision inputs, occupancy references, confidence references, restoration suppression context, and restoration explainability references.

Experience Restoration Context Model is not:

- restoration authority
- restoration execution
- orchestration authority
- occupancy authority

Experience Restoration Context Model consumes governed inputs from Experience Restoration Contract authority, Occupancy and Presence Contract authority, Person Continuity Model authority, Person-Room Affinity Model authority, and Experience Model authority where policy and context allow.

---

## Canonical Model Structure

Required fields:

experience_restoration_context:
  restoration_context_id: restctx_01J...
  restoration_candidates: []
  confidence_references: []
  occupancy_references: []
  restoration_explanations: []
  timestamp: 2026-07-10T12:00:00Z
  restoration_context_state: ready

Required metadata:

- timestamp
- restoration_context_state

---

## Restoration Candidate Representation

Restoration candidates represent the governed restoration targets or candidate experiences under consideration.

Required concepts:

- restoration candidates
- restoration targets
- restoration context references

Rules:

- the model represents candidates
- the model does not execute restoration
- candidate references remain consumption-only and explainable

---

## Confidence Reference Representation

Confidence references represent gated confidence inputs used by restoration planning.

Required concepts:

- confidence references
- confidence visibility
- confidence explainability references

Rules:

- the model consumes confidence
- the model does not calculate confidence
- confidence authority remains external

---

## Occupancy Reference Representation

Occupancy references represent governed occupancy inputs used by restoration planning.

Required concepts:

- occupancy references
- occupancy gating hooks
- occupancy visibility references

Rules:

- occupancy authority remains external
- the model consumes occupancy only
- occupancy semantics are not defined here

---

## Restoration Explanation Representation

Restoration explanations represent the explainability inputs and references for restoration candidate consideration, eligibility, and suppression.

Required concepts:

- restoration explanations
- restoration eligibility explanations
- restoration suppression explanations

Rules:

- the model represents explanation references
- the model does not evaluate policy
- explanation authority remains external

---

## Optional Restoration Context Metadata

The following restoration context metadata may be included when useful and contract-compatible:

- conflict_indicator
- suppression_reason
- policy_reference

Evaluation:

- conflict_indicator: include when downstream consumers need to know that restoration inputs are in conflict or mutually constraining
- suppression_reason: include when restoration suppression needs a bounded explanation reference for planning or review
- policy_reference: include when a consumer needs the governing policy anchor used by restoration planning

These metadata fields are optional because the base model must remain stable and consumption-focused.

---

## Continuity Relationship

Experience Restoration Context references Person Continuity.

Continuity remains authoritative.

The model consumes continuity state only.

---

## Affinity Relationship

Experience Restoration Context may reference Person-Room Affinity.

Affinity remains authoritative.

The model consumes affinity state only.

---

## Occupancy Relationship

Experience Restoration Context consumes Occupancy and Presence Model.

Occupancy remains authoritative.

No occupancy semantics may be defined here.

---

## Experience Relationship

Experience Restoration Context references Experience Model.

Experience remains authoritative.

The model consumes experience context only.

---

## Person Relationship

Experience Restoration Context references Person Profile.

Identity remains authoritative.

The model does not own identity.

---

## Restoration Contract Relationship

Experience Restoration Contract governs restoration policy.

Experience Restoration Context Model represents restoration inputs only.

Do not redefine contract authority.

---

## Provenance Relationship

Restoration candidates may reference provenance-aware prior activity.

The model is not a provenance authority.

No attribution ownership allowed.

---

## Guest-Safe Fallback

Guest identities may have:

- restoration suppression
- neutral restoration context
- no restoration candidates

Unknown identities may have:

- restoration suppression
- neutral restoration context

Guest-safe policy remains external.

The model must support restoration absence.

---

## Explainability References

Explainability references support answers to:

- why restoration was considered
- why restoration was applied
- why restoration was suppressed
- why restoration conflicted

Required references:

- explainability_reference
- restoration_reference
- contract_reference

---

## Explainability Requirements

Human explainability must support:

- Why was this restoration candidate considered?
- Why was restoration allowed?
- Why was restoration suppressed?
- Why was restoration unavailable?

Machine explainability must support:

- restoration identifiers
- candidate references
- occupancy references
- confidence references
- timestamps

---

## Provenance Requirements

Restoration context may reference provenance-aware activity history.

The model is not a provenance authority.

No attribution ownership allowed.

---

## Non-Rights

Experience Restoration Context Model does not own:

- restoration execution
- restoration decisions
- occupancy semantics
- confidence calculation
- personalization policy
- provenance
- orchestration

---

## Model Example

experience_restoration_context:
  restoration_context_id: restctx_01J123ABCDEF0001
  restoration_candidates:
    - restoration_reference: rest_01J123ABCDEF0001
      candidate_type: prior_experience
      candidate_label: evening_music_resume
      candidate_context_reference: experience.music.evening
  confidence_references:
    - confidence_reference: voice_identity.confidence.tom
      confidence_value: 0.91
      confidence_visibility: explicit
      confidence_explainability_reference: explain.restoration.confidence.tom
  occupancy_references:
    - occupancy_reference: occupancy_presence.family_room.2026-07-10T11:59:30Z
      occupancy_state: occupied
      occupancy_confidence_reference: occupancy.confidence.family_room
  restoration_explanations:
    - explainability_reference: explain.restoration.candidate_selected
      restoration_reference: rest_01J123ABCDEF0001
      contract_reference: docs/contracts/experience-restoration-contract.md
  suppression_example:
    suppression_reason: guest_safe_policy
    suppression_reference: rest_suppressed_guest_safe
  timestamp: 2026-07-10T12:00:00Z
  restoration_context_state: ready

This example is illustrative only.

---

## Model Coverage Matrix

| Restoration Feature | Supported | Notes |
|---|---|---|
| restoration candidates | yes | represented as consumption-only candidate references |
| confidence references | yes | represented, not calculated |
| occupancy references | yes | represented as governed occupancy inputs |
| restoration explanations | yes | represented through explainability references |
| continuity relationship | yes | continuity state is consumed without authority transfer |
| affinity relationship | yes | affinity state is consumed without authority transfer |
| experience relationship | yes | experience context is consumed without authority transfer |
| occupancy relationship | yes | occupancy context is consumed without authority transfer |
| provenance references | yes | prior activity history may be referenced for lineage |
| guest-safe fallback | yes | suppression and neutral context are supported |
| conflict indicators | yes | optional conflict references are supported |
| suppression reasons | yes | optional suppression references are supported |

---

## Contract / Model Alignment Review

### Contract Authority

The Experience Restoration Contract owns restoration governance, restoration eligibility semantics, restoration policy semantics, and restoration explainability semantics.

### Model Responsibilities

The Experience Restoration Context Model owns restoration candidate representation, restoration context representation, restoration decision inputs, and restoration explainability references as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Experience Restoration consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E8 Experience Restoration Planning
- Occupancy-Aware Planning
- Restoration Explainability
- Restoration Suppression Analysis

This model consumes Experience Restoration Contract authority, Occupancy and Presence Contract authority, Person Continuity Model authority, Person-Room Affinity Model authority, and Experience Model authority.

---

## Final Principle

Experience Restoration Context Model represents governed restoration inputs.

It does not own restoration execution, restoration decisions, occupancy truth, or adaptive orchestration.

It preserves the Experience Restoration Contract as the authority for restoration policy and explainability semantics.