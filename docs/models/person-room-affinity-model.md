# Person-Room Affinity Model

## Purpose

The Person-Room Affinity Model defines how Concierge represents person-room affinity and preference relationships for room-aware planning and personalization consumption.

This model is a consumption model for affinity relationship representation, room preference representation, preference explainability references, and affinity relationships.

This model does not define:

- personalization logic
- adaptive logic
- learning algorithms
- runtime execution

---

## Model Definition

Person-Room Affinity Model is:

A consumption model representing person-room preference relationships that may influence room-aware experience selection, notification behavior, media preference application, and environmental preference application.

Person-Room Affinity Model is not:

- a recommendation engine
- a personalization authority
- a learning engine
- a restoration authority

Person-Room Affinity Model consumes governed inputs from Person Continuity and Affinity Contract authority, Person Profile Model authority, Room Model authority, and occupancy-aware context where policy allows.

---

## Canonical Model Structure

Required fields:

person_room_affinity:
  affinity_id: affinity_01J...
  person_reference:
    person_id: person.tom
  room_reference:
    area_id: living_room
  notification_preferences:
    notification_affinity_state: preferred
    room_aware_notification_preferences: []
    notification_affinity_references: []
  media_preferences:
    media_affinity_state: preferred
    room_aware_media_preferences: []
    media_affinity_references: []
  environment_preferences:
    environment_affinity_state: preferred
    room_aware_environment_preferences: []
    environment_affinity_references: []
  timestamp: 2026-07-10T12:00:00Z
  affinity_state: known

Required metadata:

- timestamp
- affinity_state

---

## Person-Room Preference Representation

Person-room affinity represents stable or governed preference relationships between a person and a room context.

Required preference concepts:

- person-room affinity
- room preference relationships
- preference references

Rules:

- the model represents preferences
- the model does not determine preferences
- room references remain externally authoritative

---

## Notification Preference Representation

Notification preferences represent room-aware notification tendencies and delivery-style preferences.

Required concepts:

- notification preferences
- room-aware notification preferences
- notification affinity references

Rules:

- the model represents notification preference relationships
- the model does not implement notification behavior
- delivery behavior remains externally governed

---

## Media Preference Representation

Media preferences represent room-aware media tendencies and media presentation preferences.

Required concepts:

- media preferences
- room-aware media preferences
- media affinity references

Rules:

- the model represents media preference relationships
- the model does not implement media selection
- media execution remains external

---

## Environment Preference Representation

Environment preferences represent room-aware environment tendencies and comfort-related preference relationships.

Required concepts:

- environmental preferences
- room-aware environment references
- environmental affinity references

Rules:

- the model represents environment preference relationships
- the model does not control environments
- environmental truth remains external

---

## Optional Affinity Metadata

The following affinity metadata may be included when useful and contract-compatible:

- preference_strength
- preference_source_reference
- preference_timestamp

Evaluation:

- preference_strength: include when consumers need bounded weighting between competing room-aware preferences or candidate experiences
- preference_source_reference: include when downstream explainability needs a lineage reference for why the affinity exists
- preference_timestamp: include when consumers need recency, freshness, or reset-aware interpretation of the affinity state

These metadata fields are optional because the base model must remain stable and consumption-focused.

---

## Person Relationship

Person-Room Affinity references Person Profile.

Person Profile remains authoritative.

Affinity does not own identity.

---

## Room Relationship

Person-Room Affinity references Room Model.

Room Model remains authoritative.

Affinity does not own room truth.

---

## Continuity Relationship

Person-Room Affinity may coexist with Person Continuity.

Continuity remains externally governed.

Do not merge affinity and continuity authority.

Aligns with V2-M5.

---

## Restoration Relationship

Restoration may consume affinity context.

Affinity does not own restoration policy.

Aligns with C7.

---

## Messaging Relationship

Messaging experiences may consume notification preferences.

Affinity does not own messaging delivery behavior.

---

## Experience Relationship

Experience Model may consume affinity context.

Affinity does not own experience selection.

---

## Provenance Relationship

Preference settings may optionally reference provenance lineage.

Person-Room Affinity is not a provenance authority.

No attribution ownership allowed.

---

## Occupancy Relationship

Affinity may be consumed alongside occupancy-aware policies.

Occupancy remains externally governed.

Affinity does not define occupancy semantics.

---

## Guest-Safe Fallback

Guest identities may have:

- no affinity
- neutral affinity
- affinity suppression

Unknown identities may have:

- no affinity
- neutral affinity

Guest-safe policy remains external.

The model must support affinity absence.

---

## Explainability References

Explainability references support answers to:

- why an affinity exists
- why a preference exists
- why a room preference was applied
- why an affinity was unavailable

Required references:

- explainability_reference
- affinity_reference
- contract_reference

---

## Explainability Requirements

Human explainability must support:

- Why was this preference considered?
- Why was this room preference referenced?
- Why was this affinity used?
- Why was affinity unavailable?

Machine explainability must support:

- affinity identifiers
- room references
- preference references
- timestamps

---

## Provenance Requirements

Preference lineage references are optional.

Person-Room Affinity Model is not a provenance authority.

No attribution ownership allowed.

---

## Non-Rights

Person-Room Affinity Model does not own:

- personalization rules
- adaptive logic
- learning systems
- storage implementation
- restoration policy
- occupancy semantics
- provenance

---

## Model Example

person_room_affinity:
  affinity_id: affinity_01J123ABCDEF0001
  person_reference:
    person_id: person.tom
  room_reference:
    area_id: living_room
  notification_preferences:
    notification_affinity_state: preferred
    room_aware_notification_preferences:
      - quiet_hours_suppressed
      - voice_prompt_only
    notification_affinity_references:
      - notification_affinity_01J123ABCDEF0001
  media_preferences:
    media_affinity_state: preferred
    room_aware_media_preferences:
      - prefer_jazz
      - prefer_low_volume
    media_affinity_references:
      - media_affinity_01J123ABCDEF0001
  environment_preferences:
    environment_affinity_state: preferred
    room_aware_environment_preferences:
      - warmer_temperature
      - softer_lighting
    environment_affinity_references:
      - environment_affinity_01J123ABCDEF0001
  explainability_references:
    - explainability_reference: explain.affinity.selected
      affinity_reference: affinity_01J123ABCDEF0001
      contract_reference: docs/contracts/person-continuity-affinity-contract.md
  timestamp: 2026-07-10T12:00:00Z
  affinity_state: known

This example is illustrative only.

---

## Model Coverage Matrix

| Affinity Feature | Supported | Notes |
|---|---|---|
| room preferences | yes | represented through room references and room-aware preference entries |
| notification preferences | yes | represented through notification preferences and affinity references |
| media preferences | yes | represented through media preferences and affinity references |
| environment preferences | yes | represented through environment preferences and affinity references |
| person relationship | yes | person profile is referenced and preserved as authoritative |
| room relationship | yes | room model is referenced and preserved as authoritative |
| continuity relationship | yes | continuity may coexist without shared authority |
| restoration relationship | yes | restoration may consume affinity context |
| messaging relationship | yes | messaging may consume notification preferences |
| experience relationship | yes | experience planning may consume affinity context |
| provenance references | yes | optional lineage references are supported |
| occupancy references | yes | occupancy-aware consumption is supported |
| guest-safe fallback | yes | no, neutral, and suppressed affinity states are supported |

---

## Contract / Model Alignment Review

### Contract Authority

The Person Continuity and Affinity Contract owns continuity governance, affinity governance, preference semantics, consent requirements, guest fallback behavior, reset obligations, retention requirements, and explainability requirements.

### Model Responsibilities

The Person-Room Affinity Model owns affinity relationship representation, room preference representation, preference explainability references, and room-aware preference relationships as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Person-Room Affinity consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E7 Person Affinity Planning
- Restoration Planning
- Messaging Consumption
- Room-Aware Experience Consumption

This model consumes Person Continuity and Affinity Contract authority, Person Profile Model authority, and Room Model authority.

---

## Final Principle

Person-Room Affinity Model represents governed room-aware preference context.

It does not own identity, restoration, messaging delivery, or experience selection.

It preserves the Person Continuity and Affinity Contract as the authority for continuity and affinity semantics.