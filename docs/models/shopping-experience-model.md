# Shopping Experience Model

## Purpose

The Shopping Experience Model defines how Concierge represents shopping items, ownership, duplicate indicators, completion state, provenance linkage, and explainability references for downstream productivity experiences.

This model is a consumption model for shopping item references, ownership references, duplicate indicators, completion references, provenance references, and explanation references.

This model does not define:

- shopping providers
- shopping storage
- inventory systems
- synchronization behavior
- execution behavior

---

## Model Definition

Shopping Experience Model is:

A consumption model representing shopping list items, ownership, duplicate indicators, completion state, provenance linkage, and explainability references used throughout HTBW productivity experiences.

The model is NOT:

- a shopping provider
- a shopping engine
- an inventory system
- a shopping governance authority

Shopping Experience Model consumes governed inputs from Task and Shopping Experience Contract authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

shopping_experience:
  shopping_experience_id: shopexp_01J...
  shopping_item_references: []
  ownership_references: []
  duplicate_indicators: []
  completion_references: []
  provenance_references: []
  shopping_explainability_references: []
  timestamp: 2026-07-10T12:00:00Z
  shopping_experience_state: active

Required metadata:

- shopping_experience_id
- timestamp
- shopping_experience_state

Shopping experience state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Shopping Item Representation

Shopping item representation captures the shopping-facing item context required by downstream experiences.

Required concepts:

- shopping items
- shopping visibility references
- shopping context references

Rules:

- the model represents shopping items
- the model does not own provider records
- the model does not own shopping truth

---

## Ownership Representation

Ownership representation captures shopping ownership awareness and ownership visibility.

Required concepts:

- ownership references
- shopping ownership context
- ownership visibility references

Rules:

- the model represents ownership
- the model does not own identity authority
- the model does not own identity truth

---

## Duplicate Indicator Representation

Duplicate indicator representation captures duplication awareness and duplicate-related visibility.

Required concepts:

- duplicate indicators
- duplicate visibility references
- duplicate awareness references

Rules:

- the model represents duplication awareness only
- the model does not resolve duplicates
- the model does not define merge behavior

---

## Completion Representation

Completion representation captures shopping completion awareness and completion visibility.

Required concepts:

- completion references
- completion state
- completion visibility references

Rules:

- the model represents completion awareness only
- the model does not own completion behavior
- the model does not own execution semantics

---

## Provenance Link Representation

Provenance link representation captures provenance linkage and explanation lineage for shopping experiences.

Required concepts:

- provenance references
- attribution linkage references
- explanation lineage references

IMPORTANT:

- do not recreate provenance fields
- do not duplicate created_by
- do not duplicate added_by
- do not duplicate assigned_to
- do not duplicate completed_by
- do not duplicate attribution_confidence
- do not duplicate explanation_source

The Shopping Experience Model must reference [docs/models/provenance-model.md](provenance-model.md).

---

## Optional Shopping Metadata

The following shopping metadata may be included when useful and contract-compatible:

- multi_item_lineage_reference
- briefing_reference
- future_shopping_extension

Evaluation:

- multi_item_lineage_reference: include when multiple shopping items were surfaced from a single upstream capture and the consumer needs a compact multi-item reference for explainability
- briefing_reference: include when briefing consumers need a direct reference for explainable shopping inclusion in summaries
- future_shopping_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Provenance Relationship

Shopping Experience consumes Provenance Model.

Provenance remains authoritative.

No provenance duplication permitted.

---

## Household Memory Relationship

Shopping Experience may consume Household Memory references.

Memory authority remains external.

Shopping Experience does not own memory state.

---

## Person Relationship

Shopping Experience may reference Person Profile.

Identity authority remains external.

Shopping Experience does not own identity truth.

---

## Room Relationship

Shopping Experience may reference Room context.

Room authority remains external.

Shopping Experience does not own room truth.

---

## Task Relationship

Task Experience and Shopping Experience may consume shared productivity context.

Shopping Experience does not own task behavior.

Task and shopping domains remain separate first-class models.

---

## Household Coordination Relationship

Household Coordination consumes Shopping Experience references.

Shopping Experience does not own coordination policy.

---

## Briefing Relationship

Briefing experiences consume Shopping Experience references.

Shopping Experience does not own briefing composition.

---

## Multi-Item Capture Relationship

Multi-Item Capture may consume Shopping Experience references.

Shopping Experience does not own capture interpretation.

---

## Occupancy Relationship

Shopping Experience may reference occupancy-sensitive context.

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

The model may also support guest-addition restriction references without defining policy.

---

## Explainability References

Explainability references support answers to:

- why an item is visible
- why an item is duplicated
- why an item is marked complete
- why an item is highlighted

Required references:

- explanation_reference
- shopping_reference
- provenance_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why is this item visible?
- Why is this item duplicated?
- Why is this item complete?
- Why is this item highlighted?

Machine explainability must support:

- shopping item identifiers
- duplicate references
- completion references
- provenance references
- timestamps

---

## Provenance Requirements

Shopping Experience must consume Provenance Model references.

Shopping Experience may not define alternate attribution fields.

Shopping Experience may not duplicate provenance semantics.

---

## Non-Rights

Shopping Experience Model does NOT own:

- shopping providers
- synchronization
- inventory systems
- execution behavior
- provenance semantics
- occupancy semantics
- coordination policy

---

## Model Example

Example structure:

shopping_experience:
  shopping_experience_id: shopexp_01J...
  shopping_item_references:
    - shopping_item_reference_id: shopitem_01J...
      shopping_item_state: visible
      provenance_reference: provenance.shopping_item.01J...
  ownership_references:
    - ownership_reference_id: own_01J...
      shopping_ownership_state: shared
      provenance_reference: provenance.ownership.01J...
  duplicate_indicators:
    - duplicate_indicator_id: dup_01J...
      duplicate_state: potential_duplicate
      provenance_reference: provenance.duplicate.01J...
  completion_references:
    - completion_reference_id: complete_01J...
      completion_state: incomplete
      provenance_reference: provenance.completion.01J...
  provenance_references:
    - provenance_reference_id: provenance.shopping_experience.01J...
  shopping_explainability_references:
    - explanation_reference_id: explain_01J...
      shopping_reference:
        shopping_item_id: shopping.family.01J...
      provenance_reference: provenance.explainability.01J...
  timestamp: 2026-07-10T12:00:00Z
  shopping_experience_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Shopping Feature | Supported | Notes |
|---|---|---|
| shopping items | yes | shopping items are represented through shopping item references |
| ownership | yes | ownership is represented without owning identity authority |
| duplicate indicators | yes | duplication awareness is represented without resolving duplicates |
| completion | yes | completion is represented without owning execution behavior |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| person references | yes | person context may be referenced without owning identity |
| room references | yes | room context may be referenced without owning room truth |
| task relationship | yes | task and shopping remain separate first-class models |
| briefing relationship | yes | shopping references may participate in briefing without owning composition |
| coordination relationship | yes | shopping references may participate in household coordination without owning policy |
| multi-item capture relationship | yes | shopping references may participate in capture without owning capture interpretation |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Task and Shopping Experience Contract defines shopping awareness, shopping completion, provenance boundaries, explainability, and source attribution boundaries for productivity experiences.

2. Model responsibilities.

   Shopping Experience Model represents shopping item references, ownership references, duplicate indicators, completion references, provenance linkage references, and shopping explainability references without taking ownership of provider truth, synchronization, execution behavior, or provenance semantics.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Shopping Experience Model is the authoritative bridge between the Task and Shopping Experience Contract, the Provenance Model, and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/shopping-experience-model.md](../models/shopping-experience-model.md) as authoritative.

Future Household Coordination must treat [docs/models/shopping-experience-model.md](../models/shopping-experience-model.md) as authoritative.

Future Briefing Experiences must treat [docs/models/shopping-experience-model.md](../models/shopping-experience-model.md) as authoritative.

Future Multi-Item Capture must treat [docs/models/shopping-experience-model.md](../models/shopping-experience-model.md) as authoritative.

Shopping Experience Model consumes Task and Shopping Experience Contract authority, Provenance Model authority, Household Memory Model authority, and Experience Model authority.
