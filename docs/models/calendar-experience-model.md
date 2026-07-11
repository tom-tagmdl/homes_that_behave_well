# Calendar Experience Model

## Purpose

The Calendar Experience Model defines how Concierge represents calendar context, free/busy awareness, coordination references, briefing references, and explainability references for downstream productivity experiences.

This model is a consumption model for calendar experience context, availability references, coordination references, briefing references, and explanation references.

This model does not define:

- calendar systems of record
- provider integrations
- synchronization behavior
- scheduling engines
- meeting creation

---

## Model Definition

Calendar Experience Model is:

A consumption model representing calendar context, availability information, coordination references, briefing references, and calendar explainability references used by HTBW productivity experiences.

The model is NOT:

- a calendar provider
- a scheduling engine
- a meeting management platform
- a calendar governance authority

Calendar Experience Model consumes governed inputs from Calendar and Email Experience Contract authority, Experience Model authority, Provenance Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

calendar_experience:
  calendar_experience_id: calexp_01J...
  calendar_context:
    calendar_reference:
      calendar_id: calendar.family
    calendar_context_state: known
    person_references: []
    room_references: []
  free_busy_references: []
  household_coordination_references: []
  briefing_references: []
  calendar_explainability_references: []
  provenance_references: []
  timestamp: 2026-07-10T12:00:00Z
  calendar_experience_state: active

Required metadata:

- calendar_experience_id
- timestamp
- calendar_experience_state

Calendar experience state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Calendar Context Representation

Calendar context represents the calendar-facing awareness required by downstream experiences.

Required concepts:

- calendar context references
- calendar experience references
- coordination-aware calendar references

Rules:

- the model represents context
- the model does not own calendar records
- the model does not own calendar truth

---

## Free/Busy Representation

Free/busy representation captures availability-aware calendar consumption.

Required concepts:

- availability windows
- busy windows
- free/busy references

Rules:

- the model consumes availability
- the model does not calculate availability
- the model does not define schedule computation

---

## Household Coordination Representation

Household coordination representation captures calendar-aware coordination inputs used by household planning.

Required concepts:

- coordination references
- household planning references
- coordination-aware calendar context

Rules:

- the model represents coordination references only
- the model does not own coordination policy
- the model does not own coordination execution

---

## Briefing Representation

Briefing representation captures the calendar inputs that may participate in briefing experiences.

Required concepts:

- briefing references
- briefing inputs
- briefing-aware calendar references

Rules:

- the model represents briefing references only
- the model does not own briefing composition
- the model does not own briefing synthesis

---

## Optional Productivity Metadata

The following productivity metadata may be included when useful and contract-compatible:

- multi_person_metadata
- source_metadata
- future_calendar_extension

Evaluation:

- multi_person_metadata: include when multiple household members contribute to or consume the same calendar experience and the consumer needs an explicit household-aware reference
- source_metadata: include when source transparency is needed for explainability, provenance linkage, or consumer filtering
- future_calendar_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Provenance Relationship

Calendar Experience consumes Provenance Model references.

Provenance Model remains authoritative.

Calendar Experience does not define attribution semantics.

No alternate attribution semantics are permitted.

---

## Household Memory Relationship

Calendar Experience may consume Household Memory references.

Household Memory authority remains external.

Calendar Experience does not own memory state.

---

## Person Relationship

Calendar Experience may reference Person Profile context.

Identity authority remains external.

Calendar Experience does not own identity truth.

---

## Room Relationship

Calendar Experience may reference Room context.

Room authority remains external.

Calendar Experience does not own room truth.

---

## Briefing Relationship

Briefing experiences consume Calendar Experience.

Calendar Experience does not own briefing composition.

---

## Household Coordination Relationship

Household Coordination consumes Calendar Experience references.

Calendar Experience does not own coordination policy.

---

## Productivity Synthesis Relationship

Productivity synthesis consumes Calendar Experience references.

Calendar Experience does not own synthesis logic.

---

## Occupancy Relationship

Calendar Experience may reference occupancy-sensitive context.

Occupancy remains externally governed.

No occupancy semantics may be defined here.

---

## Guest-Safe Visibility

Guest users may receive:

- restricted calendar visibility
- neutral calendar visibility
- no visibility

Unknown identities may receive:

- restricted visibility
- neutral visibility

The model supports visibility boundaries through references only.

---

## Explainability References

Explainability references support answers to:

- why a calendar item was included
- why an availability window was included
- why a coordination reference was included
- why a briefing reference was included

Required references:

- explanation_reference
- calendar_reference
- provenance_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why is this calendar item relevant?
- Why was this availability window shown?
- Why was this briefing item included?
- Why was this coordination item included?

Machine explainability must support:

- calendar identifiers
- availability references
- coordination references
- briefing references
- timestamps

---

## Provenance Requirements

Calendar Experience may reference provenance-aware attribution.

Calendar Experience must consume Provenance Model references.

No alternate attribution semantics are permitted.

---

## Non-Rights

Calendar Experience Model does NOT own:

- scheduling behavior
- meeting creation
- provider integrations
- synchronization
- provenance semantics
- occupancy semantics
- coordination policy

---

## Model Example

Example structure:

calendar_experience:
  calendar_experience_id: calexp_01J...
  calendar_context:
    calendar_reference:
      calendar_id: calendar.family
    person_references:
      - person_id: person.tom
    room_references:
      - area_id: kitchen
    calendar_context_state: known
  free_busy_references:
    - free_busy_reference_id: freebusy_01J...
      availability_window:
        start: 2026-07-10T17:00:00Z
        end: 2026-07-10T19:00:00Z
      busy_window:
        start: 2026-07-10T18:00:00Z
        end: 2026-07-10T18:30:00Z
      calendar_reference:
        calendar_id: calendar.family
      provenance_reference: provenance.free_busy.01J...
  household_coordination_references:
    - coordination_reference_id: coord_01J...
      household_coordination_state: relevant
      provenance_reference: provenance.coordination.01J...
  briefing_references:
    - briefing_reference_id: brief_01J...
      briefing_role: planning_input
      provenance_reference: provenance.briefing.01J...
  calendar_explainability_references:
    - explanation_reference_id: explain_01J...
      calendar_reference:
        calendar_id: calendar.family
      provenance_reference: provenance.explainability.01J...
  provenance_references:
    - provenance_reference_id: provenance.calendar_experience.01J...
  timestamp: 2026-07-10T12:00:00Z
  calendar_experience_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Calendar Feature | Supported | Notes |
|---|---|---|
| calendar context | yes | context is represented through calendar references and governed context state |
| free/busy | yes | availability is consumed, not calculated |
| household coordination references | yes | coordination references remain reference-only |
| briefing references | yes | briefing participation is represented without owning briefing composition |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| person references | yes | person context may be referenced without owning identity |
| room references | yes | room context may be referenced without owning room truth |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Calendar and Email Experience Contract defines calendar and email experience visibility, discoverability, explainability, privacy, consent, source attribution, and household productivity boundaries.

2. Model responsibilities.

   Calendar Experience Model represents calendar context, free/busy consumption, household coordination references, briefing references, calendar explainability references, and provenance-aware references without taking ownership of calendar truth, scheduling behavior, or provider execution.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Calendar Experience Model is the authoritative bridge between the Calendar and Email Experience Contract and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/calendar-experience-model.md](../models/calendar-experience-model.md) as authoritative.

Future Briefing Generation must treat [docs/models/calendar-experience-model.md](../models/calendar-experience-model.md) as authoritative.

Future Household Coordination must treat [docs/models/calendar-experience-model.md](../models/calendar-experience-model.md) as authoritative.

Future Productivity Synthesis must treat [docs/models/calendar-experience-model.md](../models/calendar-experience-model.md) as authoritative.

Calendar Experience Model consumes Calendar and Email Experience Contract authority, Provenance Model authority, Household Memory Model authority, and Experience Model authority.
