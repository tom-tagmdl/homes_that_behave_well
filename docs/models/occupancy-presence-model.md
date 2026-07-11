# Occupancy and Presence Model

## Purpose

The Occupancy and Presence Model defines how Concierge consumes occupancy and presence information for downstream decision-making.

This model governs:

- occupancy state representation
- occupancy confidence representation
- identity confidence references
- occupancy source references
- guest modeling
- unknown occupancy modeling
- multi-occupant modeling

This model is consumption-only.

This model does not define:

- occupancy detection
- presence detection
- confidence algorithms
- detection implementation

---

## Model Definition

Occupancy and Presence Model is:

A consumption model representing occupancy state, occupancy confidence, identity confidence references, and occupancy source references used by Concierge decision-making.

The model is not:

- occupancy detection
- presence detection
- occupancy authority
- identity authority

---

## Occupancy State Enumeration

Canonical occupancy states are:

- empty
- occupied
- known
- unknown
- guest
- multi_occupant

No additional occupancy states are defined unless contract-authorized.

---

## Canonical Model Structure

Required fields:

occupancy_presence:
  occupancy_state: empty | occupied | known | unknown | guest | multi_occupant
  occupancy_confidence:
    value: 0.0
    source_references: []
  occupancy_source_references: []
  identity_confidence_references: []
  room_reference:
    area_id: living_room
  timestamp: 2026-07-10T12:00:00Z
  freshness:
    state: fresh
    observed_at: 2026-07-10T11:58:00Z

Required metadata:

- room_reference
- timestamp
- freshness

---

## Confidence Representation

The model references confidence for occupancy state and identity-linked context.

Occupancy confidence representation must support:

- confidence value or confidence class
- confidence source linkage
- confidence reference metadata

The model references confidence.

The model does not calculate confidence.

---

## Identity Confidence References

Identity confidence references must support:

- identity confidence reference identifiers
- person references
- attribution references

Identity authority remains external.

Identity confidence references are explainability inputs only.

---

## Occupancy Source References

Occupancy source references must support:

- source identifiers
- source lineage
- source references

This supports explainability.

This does not define detection.

---

## Conflict Reference Evaluation

Optional fields:

- occupancy_conflict_reference
- conflicting_source_reference

Evaluation:

- included as optional contract-gated references for downstream explainability when contract-authorized
- excluded from required core structure because conflict semantics are not part of the minimum consumption contract

---

## Freshness Reference Evaluation

Optional fields:

- freshness_state
- freshness_reference

Evaluation:

- included as optional contract-gated references because freshness is required for explainability and downstream policy decisions
- represented through freshness metadata in the canonical structure so consumers can distinguish stale, fresh, and unknown states without calculating freshness here

---

## Room Relationship

Occupancy references Room Model.

Room Model remains authoritative.

Occupancy does not own room truth.

---

## Person Relationship

Occupancy references Person Profile.

Occupancy references Identity Confidence.

Occupancy does not own identity.

---

## Event Relationship

Occupancy may participate in event interpretation.

Occupancy does not own event history.

---

## Restoration Relationship

Experience Restoration consumes occupancy model.

Occupancy model does not authorize restoration.

---

## Messaging Relationship

Messaging may consume occupancy state.

Occupancy model does not authorize messaging.

---

## Household Memory Relationship

Household Memory may consume occupancy state.

Occupancy model does not own memory.

---

## Explainability Requirements

Human explainability must support:

- Why was the room considered occupied?
- Why was the room considered empty?
- Why was occupancy confidence used?
- Why was guest state used?

Machine explainability must support:

- occupancy state
- occupancy confidence
- source references
- identity confidence references
- timestamps
- freshness references

---

## Provenance Requirements

Occupancy model may reference lineage.

Occupancy model is not a provenance authority.

Occupancy model does not own attribution.

---

## Guest-Safe Modeling

The model must explicitly represent:

- guest state
- unknown state

Guest-safe behavior must be representable.

Unknown-state behavior must be representable.

---

## Non-Rights

Occupancy model does not own:

- occupancy truth
- presence truth
- detection algorithms
- confidence algorithms
- identity authority
- room authority

---

## Model Example

occupancy_presence:
  occupancy_state: occupied
  occupancy_confidence:
    value: 0.92
    source_references:
      - source_id: occupancy.foundation.family_room
        source_type: foundation_presence
        lineage: foundation.presence.room_scope
  occupancy_source_references:
    - source_id: sensor.family_room_motion
      source_type: motion_sensor
      lineage: sensor.motion -> foundation.occupancy
    - source_id: sensor.family_room_ble
      source_type: ble_presence
      lineage: ble.proximity -> voice_identity -> occupancy
  identity_confidence_references:
    - person_id: person.tom
      confidence: 0.86
      attribution_reference: voice_identity.snapshot.tom_2026_07_10
  room_reference:
    area_id: family_room
  timestamp: 2026-07-10T12:00:00Z
  freshness:
    state: fresh
    observed_at: 2026-07-10T11:59:30Z

This example is illustrative only.

---

## Model Coverage Matrix

| Capability | Supported | Notes |
|---|---|---|
| empty | yes | canonical occupancy state |
| occupied | yes | canonical occupancy state |
| known | yes | canonical occupancy state |
| unknown | yes | canonical occupancy state |
| guest | yes | canonical occupancy state |
| multi_occupant | yes | canonical occupancy state |
| occupancy confidence | yes | represented, not calculated |
| identity confidence reference | yes | references external identity authority |
| source reference | yes | supports explainability and lineage |
| freshness | yes | represented for downstream policy and explanation |
| explainability | yes | required for downstream consumers |

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the occupancy and presence consumption boundary.

Future planning must treat this model as a mandatory dependency for:

- E8a occupancy planning
- restoration
- messaging
- household memory

---

## Final Principle

The Occupancy and Presence Model is a consumption model only.

It preserves Foundation ownership of occupancy and presence truth while providing deterministic, explainable inputs for downstream Concierge decisions.