# Room Vocabulary Registry Model

## Purpose

The Room Vocabulary Registry Model defines how Concierge represents governed room vocabulary entries and their relationships for downstream planning and consumption.

This model is a consumption model for vocabulary entries, aliases, capability mappings, conflict indicators, room relationships, and explainability references.

This model does not define:

- parser behavior
- NLU behavior
- UI behavior
- vocabulary governance authority
- room truth
- capability projection authority

---

## Model Definition

Room Vocabulary Registry Model is:

A consumption model representing registered room vocabulary entries, aliases, capability mappings, conflict indicators, room relationships, and explainability references.

Room Vocabulary Registry Model is not:

- parser authority
- NLU authority
- room truth authority
- capability projection authority

Room Vocabulary Registry Model consumes governed vocabulary outputs from the Room Vocabulary Registry Contract and Room Model authority.

---

## Canonical Model Structure

Required fields:

room_vocabulary_registry:
  vocabulary_entry_id: vocab_01J...
  vocabulary_entry:
    term: living room
    term_type: canonical_room_name
    vocabulary_visibility_state: visible
  aliases: []
  capability_mappings: []
  conflict_indicators: []
  room_references: []
  explainability_references: []
  timestamp: 2026-07-10T12:00:00Z
  vocabulary_state: active

Required metadata:

- timestamp
- vocabulary_state

---

## Vocabulary Entry Representation

Vocabulary entries represent canonical room terms registered for deterministic room-aware behavior.

Vocabulary entry fields may include:

- term
- term_type
- vocabulary_visibility_state
- scope_reference
- lifecycle_state

Rules:

- the model represents vocabulary entries
- the model does not determine vocabulary
- visibility is represented, not authored by runtime logic

---

## Alias Representation

Aliases represent alternate room references and normalization relationships.

Alias fields may include:

- alias_id
- alias_term
- normalization_target_reference
- alias_scope_reference
- alias_visibility_state

Rules:

- the model stores relationships only
- the model does not perform normalization
- aliases remain deterministic references to governed vocabulary entries

---

## Capability Mapping Representation

Capability mappings represent vocabulary-to-capability relationships.

Capability mapping fields may include:

- mapping_id
- vocabulary_entry_reference
- capability_reference
- mapping_state
- capability_scope_reference

Rules:

- capability governance remains external
- the model records mappings only
- the model does not define capability behavior

---

## Conflict Indicator Representation

Conflict indicators represent known ambiguity or duplication conditions.

Conflict indicator fields may include:

- conflict_id
- conflict_type
- conflicting_term_references
- conflict_state
- resolution_hint_reference

Rules:

- the model represents known conflicts
- the model does not resolve conflicts
- conflict state remains explainable and bounded

---

## Room Relationship Representation

Room relationship entries represent associations between vocabulary and room context.

Room relationship fields may include:

- room_reference_id
- room_reference
- relationship_type
- room_scope_reference

Rules:

- room relationships are references only
- room truth remains external
- room associations remain deterministic and explainable

---

## Explainability References

Explainability references support answers to:

- why a term resolved
- why a term matched
- why a term conflicted
- why a term was unavailable

Required references:

- explainability_reference
- vocabulary_reference
- contract_reference

Rules:

- explainability references support explanation only
- explainability references do not implement resolution logic
- explainability references must remain traceable to governed vocabulary and room context

---

## Optional Normalization Hints

The following normalization hints may be included when useful and contract-compatible:

- normalization_hint
- preferred_term_reference
- future_normalization_marker

Evaluation:

- normalization_hint: exclude from required core structure because the model stores relationships, not normalization logic
- preferred_term_reference: include when a downstream consumer needs a deterministic tie-break hint for explanation or presentation support
- future_normalization_marker: exclude from required core structure because future planning belongs in canonical architecture linkage, not in the model authority itself

These hints are optional because the registry must remain a consumption model, not a normalization engine.

---

## Room Relationship

Room Vocabulary Registry references Room Model.

Room Model remains authoritative.

Room Vocabulary Registry does not own room truth.

---

## Composite Room Relationship

Vocabulary entries may reference composite or merged room concepts.

Composite room governance remains external.

The model represents relationships only.

---

## Capability Projection Relationship

Capability Projection may consume vocabulary mappings.

Room Vocabulary Registry does not own capability projection.

This aligns with V2-M2.

---

## Experience Relationship

Experience Model may consume vocabulary relationships.

Room Vocabulary Registry does not own experiences.

This aligns with V2-M3.

---

## Provenance Relationship

Vocabulary registrations may optionally reference provenance lineage.

Room Vocabulary Registry is not a provenance model.

No attribution ownership allowed.

---

## Occupancy Relationship

No direct occupancy semantics.

Occupancy remains external.

The model may reference room context only.

---

## Guest-Safe Relationship

Guest-safe behavior is external.

The model supports guest-safe consumers through vocabulary representation only.

---

## Explainability Requirements

Human explainability must support:

- Why did this room term resolve?
- Why did this room term match?
- Why was this room term considered ambiguous?
- Why was this room term unavailable?

Machine explainability must support:

- vocabulary identifiers
- alias identifiers
- room references
- capability mappings
- explainability references

---

## Provenance Requirements

Vocabulary lineage references are optional.

Room Vocabulary Registry Model is not a provenance authority.

No attribution ownership allowed.

---

## Non-Rights

Room Vocabulary Registry Model does not own:

- parser logic
- NLU behavior
- UI behavior
- room truth
- capability projection logic
- provenance
- occupancy semantics

---

## Model Example

room_vocabulary_registry:
  vocabulary_entry_id: vocab_01J123ABCDEF0001
  vocabulary_entry:
    term: living room
    term_type: canonical_room_name
    vocabulary_visibility_state: visible
  aliases:
    - alias_id: alias_01J123ABCDEF0001
      alias_term: lounge
      normalization_target_reference: vocab_01J123ABCDEF0001
      alias_scope_reference: household_scope
      alias_visibility_state: visible
    - alias_id: alias_01J123ABCDEF0002
      alias_term: front room
      normalization_target_reference: vocab_01J123ABCDEF0001
      alias_scope_reference: household_scope
      alias_visibility_state: visible
  capability_mappings:
    - mapping_id: map_01J123ABCDEF0001
      vocabulary_entry_reference: vocab_01J123ABCDEF0001
      capability_reference: capabilities.lights
      mapping_state: active
      capability_scope_reference: room_scope
  conflict_indicators:
    - conflict_id: conflict_01J123ABCDEF0001
      conflict_type: duplicate_alias
      conflicting_term_references:
        - alias_01J123ABCDEF0001
        - alias_01J123ABCDEF0002
      conflict_state: explainable
      resolution_hint_reference: explain.vocabulary.alias_scope
  room_references:
    - room_reference_id: roomref_01J123ABCDEF0001
      room_reference:
        area_id: living_room
      relationship_type: canonical_room_reference
      room_scope_reference: area_scope
  explainability_references:
    - explainability_reference: explain.vocabulary.living_room.resolved
      vocabulary_reference: vocab_01J123ABCDEF0001
      contract_reference: docs/contracts/room-vocabulary-registry-contract.md
  timestamp: 2026-07-10T12:00:00Z
  vocabulary_state: active

This example is illustrative only.

---

## Model Coverage Matrix

| Vocabulary Feature | Supported | Notes |
|---|---|---|
| vocabulary entries | yes | canonical room terms are represented |
| aliases | yes | alternate references are represented |
| capability mappings | yes | vocabulary-to-capability relationships are represented |
| conflict indicators | yes | known ambiguity and duplicate states are represented |
| room relationships | yes | room associations are represented |
| composite room references | yes | composite and merged room references are represented |
| explainability references | yes | term resolution and conflict explainability are represented |
| provenance references | yes | optional lineage references are represented |
| guest-safe consumer support | yes | guest-safe consumers may consume vocabulary representation outcomes |

---

## Contract / Model Alignment Review

### Contract Authority

The Room Vocabulary Registry Contract owns vocabulary governance, alias governance, capability mapping governance, conflict governance, merged-room and composite vocabulary governance, and explainability requirements for vocabulary resolution.

### Model Responsibilities

The Room Vocabulary Registry Model owns vocabulary representation, alias representation, capability mapping representation, conflict indicator representation, room relationship representation, and explainability references as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Room Vocabulary Registry consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E4 Room Vocabulary Planning
- Capability Projection Planning
- Experience Planning
- Composite Room Planning

This model consumes Room Vocabulary Registry Contract authority and Room Model authority.

---

## Final Principle

Room Vocabulary Registry Model represents governed vocabulary relationships.

It does not determine vocabulary.

It does not resolve conflicts.

It preserves the Room Vocabulary Registry Contract as the authority for vocabulary semantics.