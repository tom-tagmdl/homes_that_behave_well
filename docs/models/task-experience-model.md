# Task Experience Model

## Purpose

The Task Experience Model defines how Concierge represents task ownership, assignment, completion state, due-awareness, provenance linkage, and explainability references for downstream productivity experiences.

This model is a consumption model for task ownership references, assignment references, completion references, due-awareness references, provenance references, and explanation references.

This model does not define:

- task providers
- task storage
- synchronization behavior
- execution behavior
- provider systems of record

---

## Model Definition

Task Experience Model is:

A consumption model representing task ownership, assignment, completion state, due-awareness, provenance linkage, and task explainability references used throughout HTBW productivity experiences.

The model is NOT:

- a task provider
- a task engine
- a task storage platform
- a task governance authority

Task Experience Model consumes governed inputs from Task and Shopping Experience Contract authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

task_experience:
  task_experience_id: taskexp_01J...
  ownership_references: []
  assignment_references: []
  completion_references: []
  due_awareness_references: []
  provenance_references: []
  task_explainability_references: []
  timestamp: 2026-07-10T12:00:00Z
  task_experience_state: active

Required metadata:

- task_experience_id
- timestamp
- task_experience_state

Task experience state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Ownership Representation

Ownership representation captures the task-facing ownership context required by downstream experiences.

Required concepts:

- ownership references
- task ownership context
- ownership visibility references

Rules:

- the model represents ownership
- the model does not own identities
- the model does not own task truth

---

## Assignment Representation

Assignment representation captures task assignment awareness and responsible-party context.

Required concepts:

- assignments
- assignment references
- responsible-party references

Rules:

- the model represents assignment state only
- the model does not own assignment policy
- the model does not calculate assignment behavior

---

## Completion Representation

Completion representation captures task completion awareness and completion visibility.

Required concepts:

- completion references
- completion state
- completion visibility

Rules:

- the model represents completion awareness only
- the model does not own completion behavior
- the model does not own execution semantics

---

## Due-Awareness Representation

Due-awareness representation captures task due-date awareness and deadline-related context.

Required concepts:

- due-awareness
- due references
- deadline visibility references

Rules:

- the model consumes due-awareness state
- the model does not calculate due status
- the model does not own deadline computation

---

## Provenance Link Representation

Provenance link representation captures provenance linkage and explanation lineage for task experiences.

Required concepts:

- provenance references
- attribution links
- explanation lineage references

IMPORTANT:

- do not recreate provenance fields
- do not duplicate created_by
- do not duplicate assigned_to
- do not duplicate completed_by
- do not duplicate attribution_confidence
- do not duplicate explanation_source

The Task Experience Model must reference [docs/models/provenance-model.md](provenance-model.md).

---

## Optional Productivity Metadata

The following productivity metadata may be included when useful and contract-compatible:

- coordination_reference
- briefing_reference
- future_task_extension

Evaluation:

- coordination_reference: include when downstream coordination consumers need a compact reference to tie task context to household coordination without expanding the core model
- briefing_reference: include when briefing consumers need a direct reference for explainable task inclusion in summaries
- future_task_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Provenance Relationship

Task Experience consumes Provenance Model.

Provenance remains authoritative.

No provenance duplication permitted.

---

## Household Memory Relationship

Task Experience may consume Household Memory references.

Memory authority remains external.

Task Experience does not own memory state.

---

## Person Relationship

Task Experience may reference Person Profile.

Identity authority remains external.

Task Experience does not own identity truth.

---

## Room Relationship

Task Experience may reference Room context.

Room authority remains external.

Task Experience does not own room truth.

---

## Shopping Relationship

Shopping Experience may consume shared productivity context.

Task Experience does not own shopping behavior.

Task and shopping domains remain separate first-class models.

---

## Household Coordination Relationship

Household Coordination consumes Task Experience references.

Task Experience does not own coordination policy.

---

## Briefing Relationship

Briefing experiences consume Task Experience references.

Task Experience does not own briefing composition.

---

## Productivity Synthesis Relationship

Productivity synthesis consumes Task Experience references.

Task Experience does not own synthesis behavior.

---

## Occupancy Relationship

Task Experience may reference occupancy-sensitive context.

Occupancy remains externally governed.

No occupancy semantics may be defined here.

---

## Guest-Safe Visibility

Guest users may receive:

- restricted visibility
- neutral visibility
- no visibility

Unknown identities may receive:

- restricted visibility
- neutral visibility

The model supports visibility boundaries through references only.

---

## Explainability References

Explainability references support answers to:

- why a task is visible
- why a task is assigned
- why a task is due
- why a task is highlighted

Required references:

- explanation_reference
- task_reference
- provenance_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why is this task visible?
- Why is this task assigned?
- Why is this task due?
- Why is this task highlighted?

Machine explainability must support:

- task identifiers
- assignment references
- due references
- provenance references
- timestamps

---

## Provenance Requirements

Task Experience must consume Provenance Model references.

Task Experience may not define alternate attribution fields.

Task Experience may not duplicate provenance semantics.

---

## Non-Rights

Task Experience Model does NOT own:

- task providers
- synchronization
- execution behavior
- provider integrations
- provenance semantics
- occupancy semantics
- coordination policy

---

## Model Example

Example structure:

task_experience:
  task_experience_id: taskexp_01J...
  ownership_references:
    - ownership_reference_id: own_01J...
      task_ownership_state: owned
      provenance_reference: provenance.ownership.01J...
  assignment_references:
    - assignment_reference_id: assign_01J...
      responsible_party_reference:
        person_id: person.tom
      provenance_reference: provenance.assignment.01J...
  completion_references:
    - completion_reference_id: complete_01J...
      completion_state: incomplete
      provenance_reference: provenance.completion.01J...
  due_awareness_references:
    - due_reference_id: due_01J...
      due_state: due_soon
      provenance_reference: provenance.due.01J...
  provenance_references:
    - provenance_reference_id: provenance.task_experience.01J...
  task_explainability_references:
    - explanation_reference_id: explain_01J...
      task_reference:
        task_id: task.family.01J...
      provenance_reference: provenance.explainability.01J...
  timestamp: 2026-07-10T12:00:00Z
  task_experience_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Task Feature | Supported | Notes |
|---|---|---|
| ownership | yes | ownership is represented through task ownership references |
| assignment | yes | assignment is represented without owning assignment policy |
| completion | yes | completion is represented without owning execution behavior |
| due-awareness | yes | due-awareness is consumed, not calculated |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| person references | yes | person context may be referenced without owning identity |
| room references | yes | room context may be referenced without owning room truth |
| shopping relationship | yes | task and shopping remain separate first-class models |
| briefing relationship | yes | task references may participate in briefing without owning composition |
| coordination relationship | yes | task references may participate in household coordination without owning policy |
| productivity synthesis | yes | task references may participate in synthesis without owning synthesis behavior |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Task and Shopping Experience Contract defines task awareness, assignment awareness, completion awareness, due awareness, provenance boundaries, explainability, and source attribution boundaries for productivity experiences.

2. Model responsibilities.

   Task Experience Model represents task ownership references, assignment references, completion references, due-awareness references, provenance linkage references, and task explainability references without taking ownership of provider truth, synchronization, execution behavior, or provenance semantics.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Task Experience Model is the authoritative bridge between the Task and Shopping Experience Contract, the Provenance Model, and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/task-experience-model.md](../models/task-experience-model.md) as authoritative.

Future Household Coordination must treat [docs/models/task-experience-model.md](../models/task-experience-model.md) as authoritative.

Future Briefing Experiences must treat [docs/models/task-experience-model.md](../models/task-experience-model.md) as authoritative.

Future Productivity Synthesis must treat [docs/models/task-experience-model.md](../models/task-experience-model.md) as authoritative.

Task Experience Model consumes Task and Shopping Experience Contract authority, Provenance Model authority, Household Memory Model authority, and Experience Model authority.
