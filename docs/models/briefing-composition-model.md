# Briefing Composition Model

## Purpose

The Briefing Composition Model defines how Concierge represents briefing sections, ordering semantics, source references, calm-by-default composition, and explainability references for downstream productivity experiences.

This model is a consumption model for briefing sections, source references, priority ordering, calm-by-default ordering, and explanation references.

This model does not define:

- synthesis engines
- briefing generation
- orchestration
- personalization
- runtime composition behavior

---

## Model Definition

Briefing Composition Model is:

A consumption model representing briefing sections, ordering semantics, source references, and explainability references used throughout HTBW productivity experiences.

The model is NOT:

- a synthesis engine
- a briefing generator
- a runtime orchestrator
- a briefing governance authority

Briefing Composition Model consumes governed inputs from Knowledge, Briefing, and Household Status Synthesis Contract authority, Calendar Experience Model authority, Email Experience Model authority, Task Experience Model authority, Shopping Experience Model authority, Knowledge Query Experience Model authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

briefing_composition:
  briefing_composition_id: briefcomp_01J...
  briefing_sections: []
  source_references: []
  priority_ordering: []
  calm_by_default_ordering: []
  briefing_explainability_references: []
  provenance_references: []
  timestamp: 2026-07-10T12:00:00Z
  briefing_composition_state: active

Required metadata:

- briefing_composition_id
- timestamp
- briefing_composition_state

Briefing composition state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Briefing Section Representation

Briefing section representation captures the section-facing structure required by downstream experiences.

Required concepts:

- briefing sections
- briefing section references
- section visibility references

Rules:

- the model represents sections
- the model does not generate content
- the model does not own section text generation

---

## Source Reference Representation

Source reference representation captures source-backed briefing linkage and visibility.

Required concepts:

- source references
- source linkage
- source visibility references

Rules:

- the model represents source references only
- the model does not own source authority
- the model does not calculate source trust

---

## Priority Ordering Representation

Priority ordering representation captures briefing ordering semantics and ordering visibility.

Required concepts:

- priority ordering
- ordering references
- ordering visibility references

Rules:

- the model represents ordering semantics
- the model does not calculate ordering
- the model does not own ranking behavior

---

## Calm-By-Default Ordering Representation

Calm-by-default ordering representation captures non-disruptive section ordering and calm-first visibility.

Required concepts:

- calm ordering
- non-disruptive section ordering
- calm-first visibility references

Rules:

- the model represents calm ordering semantics only
- the model does not implement urgency escalation
- the model does not own content prioritization policy

---

## Optional Composition Metadata

The following composition metadata may be included when useful and contract-compatible:

- guest_safe_composition_reference
- style_variation_reference
- future_briefing_extension

Evaluation:

- guest_safe_composition_reference: include when a downstream consumer needs a compact guest-safe boundary reference for composition filtering
- style_variation_reference: include when a governed style reference is needed for household-aware presentation without defining runtime personalization logic
- future_briefing_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Calendar Experience Relationship

Briefing Composition consumes Calendar Experience references.

Calendar Experience remains authoritative.

---

## Email Experience Relationship

Briefing Composition consumes Email Experience references.

Email Experience remains authoritative.

---

## Task Experience Relationship

Briefing Composition consumes Task Experience references.

Task Experience remains authoritative.

---

## Shopping Experience Relationship

Briefing Composition consumes Shopping Experience references.

Shopping Experience remains authoritative.

---

## Knowledge Experience Relationship

Briefing Composition consumes Knowledge Query Experience references.

Knowledge Experience remains authoritative.

---

## Message Experience Relationship

Briefing Composition may consume Messaging references when contract-authorized.

Messaging authority remains external.

---

## Weather / News Relationship

Briefing Composition may consume Weather and RSS News experience references.

Weather and news authority remain external.

---

## Home Status Relationship

Briefing Composition may consume Home Status references.

Home Status authority remains external.

---

## Asset Intelligence Relationship

Briefing Composition may consume Asset Intelligence references.

Asset Intelligence remains authoritative.

---

## Provenance Relationship

Briefing Composition may consume Provenance references.

No alternate attribution semantics permitted.

---

## Household Memory Relationship

Briefing Composition may consume Household Memory references.

Household Memory remains authoritative.

---

## Room Relationship

Briefing Composition may reference Room context.

Room authority remains external.

---

## Person Relationship

Briefing Composition may reference Person Profile context.

Identity authority remains external.

---

## Occupancy Relationship

Briefing Composition may reference occupancy-sensitive context.

Occupancy remains externally governed.

No occupancy semantics may be defined here.

---

## Guest-Safe Composition

Guests may receive:

- restricted briefing composition
- simplified composition
- no composition

Unknown identities may receive:

- restricted composition
- simplified composition

The model supports composition boundaries through references only.

---

## Explainability References

Explainability references support answers to:

- why a section was included
- why a section was ordered
- why a source was included
- why calm-by-default ordering applied

Required references:

- explanation_reference
- briefing_reference
- source_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why was this section included?
- Why was this section first?
- Why was this source included?
- Why was calm ordering applied?

Machine explainability must support:

- section identifiers
- ordering references
- source references
- briefing references
- timestamps

---

## Provenance Requirements

Briefing Composition may reference provenance-aware attribution.

Briefing Composition must consume Provenance Model references when attribution is needed.

No alternate attribution semantics are permitted.

---

## Non-Rights

Briefing Composition Model does NOT own:

- synthesis engines
- runtime generation
- orchestration
- personalization
- provider integrations
- provenance semantics
- occupancy semantics

---

## Model Example

Example structure:

briefing_composition:
  briefing_composition_id: briefcomp_01J...
  briefing_sections:
    - briefing_section_id: section_01J...
      section_type: schedule
      section_visibility_reference:
        visibility_state: guest_safe
      provenance_reference: provenance.section.01J...
  source_references:
    - source_reference_id: source_01J...
      source_linkage:
        source_id: calendar.family
      source_visibility_reference:
        visibility_state: explicit
  priority_ordering:
    - ordering_reference_id: order_01J...
      ordered_section_reference:
        briefing_section_id: section_01J...
      ordering_visibility_reference:
        visibility_state: explicit
  calm_by_default_ordering:
    - calm_order_reference_id: calm_01J...
      non_disruptive_section_order: 1
      calm_first_visibility_reference:
        visibility_state: explicit
  briefing_explainability_references:
    - explanation_reference_id: explain_01J...
      briefing_reference:
        briefing_id: briefcomp_01J...
      source_reference:
        source_id: calendar.family
      provenance_reference: provenance.explainability.01J...
  provenance_references:
    - provenance_reference_id: provenance.briefing_composition.01J...
  timestamp: 2026-07-10T12:00:00Z
  briefing_composition_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Briefing Feature | Supported | Notes |
|---|---|---|
| briefing sections | yes | sections are represented without generating content |
| source references | yes | sources are represented without owning source authority |
| priority ordering | yes | ordering is represented without calculating ordering |
| calm-by-default ordering | yes | calm-first semantics are represented as reference-based ordering |
| calendar inputs | yes | calendar references can be consumed |
| email inputs | yes | email references can be consumed |
| task inputs | yes | task references can be consumed |
| shopping inputs | yes | shopping references can be consumed |
| knowledge inputs | yes | knowledge references can be consumed |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe composition | yes | composition boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Knowledge, Briefing, and Household Status Synthesis Contract defines briefing composition governance, calm-by-default behavior, guest-safe limits, source attribution, and explainability boundaries.

2. Model responsibilities.

   Briefing Composition Model represents sections, source references, priority ordering, calm-by-default ordering, and briefing explainability references without taking ownership of synthesis behavior, orchestration, personalization, or runtime generation.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Briefing Composition Model is the authoritative bridge between the Knowledge, Briefing, and Household Status Synthesis Contract and E13 Briefing Experiences.

Future E13 Productivity Experiences must treat [docs/models/briefing-composition-model.md](../models/briefing-composition-model.md) as authoritative.

Future Briefing Experiences must treat [docs/models/briefing-composition-model.md](../models/briefing-composition-model.md) as authoritative.

Future Household Status Synthesis must treat [docs/models/briefing-composition-model.md](../models/briefing-composition-model.md) as authoritative.

Future Coordination Experiences must treat [docs/models/briefing-composition-model.md](../models/briefing-composition-model.md) as authoritative.

Briefing Composition Model consumes Knowledge, Briefing, and Household Status Synthesis Contract authority, Calendar Experience Model authority, Email Experience Model authority, Task Experience Model authority, Shopping Experience Model authority, Knowledge Query Experience Model authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.
