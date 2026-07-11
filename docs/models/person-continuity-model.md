# Person Continuity Model

## Purpose

The Person Continuity Model defines how Concierge represents continuity state associated with a person for planning and restoration-related experiences.

This model is a consumption model for continuity state representation, continuity references, continuity explainability, and continuity relationships.

This model does not define:

- learning algorithms
- storage algorithms
- personalization rules
- runtime execution

---

## Model Definition

Person Continuity Model is:

A consumption model representing continuity state associated with a person based on previously observed context and experience references.

Person Continuity Model is not:

- a learning system
- a personalization authority
- a storage authority
- a restoration authority

Person Continuity Model consumes governed inputs from Person Profile, Interaction Model, Room Model, and Experience Model.

---

## Canonical Model Structure

Required fields:

person_continuity:
  continuity_id: continuity_01J...
  person_reference:
    person_id: person.tom
  last_activity:
    activity_reference: activity.last_known_music
    activity_label: music
    activity_state: known
    activity_explainability_reference: explain.continuity.last_activity
  last_media:
    media_reference: media.last_playlist
    media_label: playlist
    media_continuity_state: known
  last_room:
    room_reference:
      area_id: living_room
    room_continuity_state: known
  last_interaction_context:
    interaction_reference:
      interaction_id: interaction.voice.followup_01J...
    continuity_context_reference: continuity.context.recent
    conversational_continuity_references: []
  timestamp: 2026-07-10T12:00:00Z
  continuity_state: known

Required metadata:

- timestamp
- continuity_state

---

## Last Activity Representation

Last activity represents the most recently observed activity context associated with the person.

Activity fields may include:

- activity_reference
- activity_label
- activity_state
- activity_explainability_reference

Rules:

- the model represents activity state
- the model does not infer activity
- activity references remain consumption-only and explainable

---

## Last Media Representation

Last media represents the most recently observed media continuity context associated with the person.

Media fields may include:

- media_reference
- media_label
- media_continuity_state
- media_explainability_reference

Rules:

- the model represents media continuity
- the model does not implement media restoration
- media continuity remains a planning input only

---

## Last Room Representation

Last room represents the most recently observed room context associated with the person.

Room fields may include:

- room_reference
- room_continuity_state
- room_explainability_reference

Rules:

- room authority remains external
- the model references room context only
- room continuity does not own room truth

---

## Last Interaction Context Representation

Last interaction context represents the most recently observed interaction and conversational continuity state.

Interaction fields may include:

- interaction_reference
- continuity_context_reference
- conversational_continuity_references

Rules:

- the model represents context
- the model does not define conversational behavior
- interaction history remains authoritative

---

## Optional Continuity Metadata

The following continuity metadata may be included when useful and contract-compatible:

- freshness_marker
- continuity_timestamp
- reset_reference

Evaluation:

- freshness_marker: include when downstream consumers need a clear staleness or recency marker for continuity context
- continuity_timestamp: include when consumers need a separate continuity-observation timestamp from the model timestamp
- reset_reference: include when continuity needs to reference a governed reset or purge event for explanation

These markers are optional because the base model must remain stable and consumable.

---

## Person Relationship

Person Continuity references Person Profile.

Person Profile remains authoritative.

Person Continuity does not own identity.

---

## Room Relationship

Person Continuity references Room Model.

Room authority remains external.

---

## Interaction Relationship

Person Continuity references Interaction Model.

Interaction history remains authoritative.

---

## Experience Relationship

Person Continuity may reference Experience Model.

Experience authority remains external.

---

## Restoration Relationship

Experience Restoration may consume continuity context.

Person Continuity does not own restoration policy.

Aligns with V2-C7.

---

## Affinity Relationship

Affinity remains externally governed.

Person Continuity may coexist with affinity references.

Do not merge continuity and affinity authority.

---

## Provenance Relationship

Person Continuity may reference provenance-aware events.

Person Continuity is not a provenance authority.

No attribution ownership allowed.

---

## Occupancy Relationship

Person Continuity may reference occupancy-sensitive contexts.

Occupancy remains externally governed.

Do not define occupancy semantics.

---

## Guest-Safe Fallback

Guest identities may have:

- null continuity state
- neutral continuity state

Unknown identities may have:

- null continuity state
- neutral continuity state

The model must support continuity absence.

Guest-safe policy remains external.

---

## Explainability References

Explainability references support answers to:

- why a continuity reference exists
- why a room reference exists
- why a media reference exists
- why an interaction reference exists

Required references:

- explainability_reference
- continuity_reference
- contract_reference

---

## Explainability Requirements

Human explainability must support:

- Why was this continuity state selected?
- Why was this last room referenced?
- Why was this last activity referenced?
- Why was this continuity state unavailable?

Machine explainability must support:

- continuity identifiers
- interaction references
- room references
- media references
- timestamps

---

## Provenance Requirements

Person Continuity may reference lineage-aware events.

Person Continuity Model is not a provenance authority.

No attribution ownership allowed.

---

## Non-Rights

Person Continuity Model does not own:

- personalization rules
- affinity rules
- learning algorithms
- storage implementation
- restoration policy
- occupancy semantics
- provenance

---

## Model Example

person_continuity:
  continuity_id: continuity_01J123ABCDEF0001
  person_reference:
    person_id: person.tom
  last_activity:
    activity_reference: activity.last_known_reading
    activity_label: reading
    activity_state: known
    activity_explainability_reference: explain.continuity.last_activity.reading
  last_media:
    media_reference: media.last_playlist
    media_label: playlist
    media_continuity_state: known
  last_room:
    room_reference:
      area_id: living_room
    room_continuity_state: known
  last_interaction_context:
    interaction_reference:
      interaction_id: interaction.voice.followup_01J123ABCDEF0001
    continuity_context_reference: continuity.context.recent
    conversational_continuity_references:
      - conversation_01J123ABCDEF0001
  explainability_references:
    - explainability_reference: explain.continuity.selected
      continuity_reference: continuity_01J123ABCDEF0001
      contract_reference: docs/contracts/person-continuity-affinity-contract.md
  timestamp: 2026-07-10T12:00:00Z
  continuity_state: known

This example is illustrative only.

---

## Model Coverage Matrix

| Continuity Feature | Supported | Notes |
|---|---|---|
| last activity | yes | represented with activity references and explainability |
| last media | yes | represented with media references and continuity state |
| last room | yes | represented with room references and continuity state |
| last interaction context | yes | represented with interaction and conversational continuity references |
| person relationship | yes | person profile is referenced and preserved as authoritative |
| room relationship | yes | room model is referenced and preserved as authoritative |
| interaction relationship | yes | interaction model is referenced and preserved as authoritative |
| experience relationship | yes | experience model may be referenced as context only |
| restoration relationship | yes | restoration may consume continuity context |
| affinity relationship | yes | affinity is referenced as externally governed and separate |
| provenance references | yes | provenance-aware events may be referenced |
| occupancy references | yes | occupancy-sensitive contexts may be referenced |
| guest-safe fallback | yes | null or neutral continuity state is supported |

---

## Contract / Model Alignment Review

### Contract Authority

The Person Continuity and Affinity Contract owns continuity governance, affinity governance, continuity semantics, affinity semantics, guest fallback behavior, and continuity explainability requirements.

### Model Responsibilities

The Person Continuity Model owns continuity state representation, continuity references, continuity explainability references, and continuity relationships as a consumption-only model.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Person Continuity consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E7 Person Continuity Planning
- Restoration Planning
- Experience Consumption
- Personalization Consumption

This model consumes Person Continuity and Affinity Contract authority and Person Profile Model authority.

---

## Final Principle

Person Continuity Model represents governed continuity context.

It does not own identity, restoration, or personalization.

It preserves the Person Continuity and Affinity Contract as the authority for continuity semantics.