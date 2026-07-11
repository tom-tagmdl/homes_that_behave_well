# Experience Model

## Purpose

The Experience Model defines how Concierge represents first-class household-facing experiences for planning and selection.

This model is a consumption model for experience categories, experience relationships, experience visibility representation, and explainability references.

This model does not define:

- orchestration
- runtime execution
- provider execution
- capability projection authority
- experience governance authority

---

## Model Definition

Experience Model is:

A consumption model representing experience categories and relationships used throughout Concierge planning and experience selection.

Experience Model is not:

- orchestration authority
- runtime authority
- execution authority
- capability projection authority

Experience Model consumes governed inputs from Experience Projection and Capability Projection.

---

## Canonical Model Structure

Required fields:

experience:
  experience_id: exp_01J...
  experience_category: lighting
  room_reference:
    area_id: living_room
  person_reference:
    person_id: person.tom
  capability_projection_reference:
    projection_id: capproj_01J...
  intent_reference:
    intent_id: intent.voice.lighting
  explainability_references: []
  timestamp: 2026-07-10T12:00:00Z
  experience_visibility_state: visible

Required metadata:

- timestamp
- experience_visibility_state

---

## Experience Category Model

Canonical experience categories are represented as governed consumption categories.

### 1. Lighting

Purpose: room-facing lighting awareness and presentation.

Relationship boundaries:

- consumes room context
- consumes capability projection context
- does not own room truth
- does not own capability authority

Consumption role:

- planning input for lighting-aware Concierge experiences

### 2. Audio

Purpose: audio and listening experience surfacing.

Relationship boundaries:

- consumes room and person context
- does not own media execution
- does not own device truth

Consumption role:

- planning input for audio-aware Concierge experiences

### 3. Video

Purpose: video and display experience surfacing.

Relationship boundaries:

- consumes room and person context
- does not own playback authority
- does not own display truth

Consumption role:

- planning input for video-aware Concierge experiences

### 4. Messaging

Purpose: outbound and inbound household messaging experiences.

Relationship boundaries:

- consumes identity, occupancy, and provenance-aware context
- does not own delivery behavior
- does not own messaging systems of record

Consumption role:

- planning input for message presentation and household coordination surfaces

### 5. Discovery

Purpose: guided discovery of available household experiences.

Relationship boundaries:

- consumes capability projection and room context
- does not own capability visibility
- does not own experience selection authority

Consumption role:

- planning input for discoverable experience surfaces

### 6. Climate

Purpose: comfort and environment-oriented household experiences.

Relationship boundaries:

- consumes environment and occupancy context
- does not own environmental truth
- does not own occupancy truth

Consumption role:

- planning input for climate-oriented experience surfaces

### 7. Calendar

Purpose: schedule-awareness experiences.

Relationship boundaries:

- consumes calendar provider context
- does not own calendar truth
- does not own provider execution

Consumption role:

- planning input for schedule-aware experiences

### 8. Email

Purpose: household email-awareness experiences.

Relationship boundaries:

- consumes email provider context
- does not own mailbox truth
- does not own provider execution

Consumption role:

- planning input for email-aware experiences

### 9. Task

Purpose: household task workflow experiences.

Relationship boundaries:

- consumes task provider context
- does not own task truth
- does not own provider execution

Consumption role:

- planning input for task-aware experiences

### 10. Shopping

Purpose: shopping list and grocery workflow experiences.

Relationship boundaries:

- consumes shopping provider context
- does not own shopping truth
- does not own provider execution

Consumption role:

- planning input for shopping-aware experiences

### 11. Knowledge

Purpose: knowledge retrieval and reference experiences.

Relationship boundaries:

- consumes governed knowledge sources
- does not own knowledge authority
- does not own provider execution

Consumption role:

- planning input for knowledge-oriented experiences

### 12. Briefing

Purpose: curated multi-source summary experiences.

Relationship boundaries:

- consumes calendar, email, task, shopping, memory, and status inputs
- does not own source truth
- does not own synthesis authority

Consumption role:

- planning input for briefing-oriented experiences

### 13. Household Status Synthesis

Purpose: synthesized state-of-home awareness experiences.

Relationship boundaries:

- consumes occupancy, environment, signal, and capability context
- does not own source truth
- does not own synthesis execution

Consumption role:

- planning input for household status synthesis experiences

The model represents categories.

The model does not implement categories.

---

## Room Relationship

Experience references Room Model.

Room remains authoritative.

Experience does not own room truth.

---

## Person Relationship

Experience references Person Profile.

Experience consumes identity context.

Experience does not own identity.

---

## Capability Projection Relationship

Experience consumes Capability Projection.

Capability Projection remains authoritative.

Experience does not own capability projection.

This aligns with the Capability Projection Model.

---

## Intent Relationship

Experiences may be selected in response to intents.

Intent remains external.

Experience does not own intent semantics.

---

## Experience Category Relationships

Relationship descriptions only:

- discovery and knowledge: discovery surfaces knowledge entry points and reference paths without owning knowledge authority
- knowledge and briefing: briefing may consume knowledge outputs as contextual inputs without owning either category
- briefing and household status synthesis: household status synthesis may contribute to briefing context without briefing owning synthesis authority
- calendar and email: both categories support productivity-awareness surfaces but remain separate provider-backed experiences
- task and shopping: both categories support household productivity workflows but remain separate provider-backed experiences
- messaging and notifications: messaging experiences may relate to notifications through presentation and awareness, but do not own delivery behavior
- restoration-relevant experiences: lighting, audio, video, climate, and productivity categories may participate in restoration planning without owning restoration policy

---

## Productivity Experience Relationships

The following categories are productivity experiences:

- calendar
- email
- task
- shopping
- knowledge
- briefing
- household_status_synthesis

Rules:

- productivity experiences consume governed provider context and selected projections
- productivity experiences do not own productivity governance
- productivity experiences do not own provider systems of record

Aligns to:

- C9a
- C9b
- C9c

---

## Occupancy Relationship

Experiences may consume occupancy context.

Occupancy remains authoritative.

Experience Model does not define occupancy semantics.

---

## Restoration Relationship

Experience Restoration consumes Experience Model.

Experience Model does not own restoration policy.

Aligns with C7.

---

## Messaging Relationship

Messaging experiences consume this model.

Experience Model does not define messaging delivery behavior.

---

## Guest-Safe Experience Relationship

Experience visibility may be guest-filtered.

Guest-safe policy remains external.

The model only represents outcomes.

---

## Provenance Relationship

Productivity-related experiences may reference provenance-aware artifacts.

Experience Model does not own provenance.

Provenance remains authoritative.

---

## Household Memory Relationship

Household Memory may consume experiences as context.

Experience does not own memory.

---

## Explainability References

Explainability references support answers to:

- why an experience was available
- why an experience was selected
- why an experience was filtered
- why an experience was visible

Required references:

- explainability_reference
- capability_projection_reference
- contract_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Optional Extensibility Markers

The following markers may be included when useful and contract-compatible:

- category_metadata
- category_extensions
- future_category_marker

Evaluation:

- category_metadata: include when a consumer needs additional descriptive context for a category without changing category authority
- category_extensions: include when downstream planning needs controlled extension points without changing the base model meaning
- future_category_marker: include only when planning needs to reserve a category extension path without asserting new authority

These markers are optional because the base model must remain stable and authoritative.

---

## Explainability Requirements

Human explainability must support:

- Why was this experience shown?
- Why is this experience available?
- Why is this experience filtered?
- Why was this category chosen?

Machine explainability must support:

- experience identifiers
- category identifiers
- explainability references
- capability references
- timestamps

---

## Provenance Requirements

Experience Model may reference provenance-aware artifacts.

Experience Model is not a provenance authority.

No attribution ownership allowed.

---

## Non-Rights

Experience Model does not own:

- orchestration
- runtime execution
- capability projection logic
- room truth
- identity
- occupancy semantics
- provenance
- productivity governance

---

## Model Example

experience:
  experience_id: exp_01J123ABCDEF0001
  experience_category: briefing
  room_reference:
    area_id: living_room
  person_reference:
    person_id: person.tom
  capability_projection_reference:
    projection_id: capproj_01J123ABCDEF0001
  intent_reference:
    intent_id: intent.voice.briefing
  explainability_references:
    - explainability_reference: explain.experience.briefing.available
      capability_projection_reference: capproj_01J123ABCDEF0001
      contract_reference: docs/contracts/experience-projection-contract.md
    - explainability_reference: explain.experience.briefing.filtered
      capability_projection_reference: capproj_01J123ABCDEF0001
      contract_reference: docs/contracts/experience-projection-contract.md
  timestamp: 2026-07-10T12:00:00Z
  experience_visibility_state: visible

This example is illustrative only.

---

## Model Coverage Matrix

| Experience Area | Supported | Notes |
|---|---|---|
| lighting | yes | canonical category represented |
| audio | yes | canonical category represented |
| video | yes | canonical category represented |
| messaging | yes | canonical category represented |
| discovery | yes | canonical category represented |
| climate | yes | canonical category represented |
| calendar | yes | canonical category represented |
| email | yes | canonical category represented |
| task | yes | canonical category represented |
| shopping | yes | canonical category represented |
| knowledge | yes | canonical category represented |
| briefing | yes | canonical category represented |
| household_status_synthesis | yes | canonical category represented |
| room relationships | yes | room reference and authority preservation are represented |
| person relationships | yes | person reference and identity consumption are represented |
| capability relationships | yes | capability projection consumption is represented |
| occupancy references | yes | occupancy consumption is represented |
| provenance references | yes | provenance-aware artifact references are represented |
| guest-safe visibility | yes | guest-filtered visibility is represented as an outcome |

---

## Contract / Model Alignment Review

### Contract Authority

The Experience Projection Contract owns experience visibility, availability, discoverability, composition, categorization, explainability, and the policy boundaries for room-scoped, person-aware, productivity, household memory, briefing, and household status synthesis experiences.

### Model Responsibilities

The Experience Model owns experience categories, relationship descriptions, visibility-state representation, explainability references, and consumption-only representation of experience planning inputs.

### Gaps Identified

No gaps identified.

---

## Canonical Architecture Linkage

This model must appear in canonical traceability as the Experience consumption boundary.

Future planning must treat this model as an authoritative dependency for:

- E6 Experience Planning
- Coordinator V2
- Restoration Planning
- Productivity Experience Planning

---

## Final Principle

Experience Model represents governed experience planning inputs.

It does not decide experience visibility.

It does not execute experiences.

It preserves the Experience Projection Contract as the authority for experience semantics.