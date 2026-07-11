# Multi-Item Capture Result Model

## Purpose

The Multi-Item Capture Result Model defines how Concierge represents decomposition outcomes, utterance lineage, provenance propagation, and explainability references for downstream productivity experiences.

This model is a consumption model for utterance references, decomposition references, item lineage references, provenance propagation references, and explanation references.

This model does not define:

- parser behavior
- NLP interpretation
- speech recognition
- decomposition algorithms
- confirmation workflows

---

## Model Definition

Multi-Item Capture Result Model is:

A consumption model representing the structured result of a governed utterance decomposition process, including lineage and provenance propagation.

The model is NOT:

- a parser
- an interpretation engine
- a speech recognition system
- a governance authority

Multi-Item Capture Result Model consumes governed inputs from Multi-Item Capture Interpretation Contract authority, Provenance Model authority, Task Experience Model authority, Shopping Experience Model authority, Experience Model authority, Household Memory Model authority, Person Profile Model authority, Room Model authority, Interaction Model authority, and Occupancy and Presence Model authority.

---

## Canonical Model Structure

Required fields:

capture_result:
  capture_result_id: capres_01J...
  utterance_reference:
    utterance_id: utterance_01J...
  decomposition_references: []
  item_lineage_references: []
  provenance_propagation_references: []
  decomposition_explainability_references: []
  timestamp: 2026-07-10T12:00:00Z
  capture_result_state: active

Required metadata:

- capture_result_id
- timestamp
- capture_result_state

Capture result state is a governed presentation state and may be active, restricted, reduced, or unknown when contract-authorized.

---

## Utterance Representation

Utterance representation captures the original utterance and its visibility boundaries.

Required concepts:

- original utterance
- utterance references
- utterance visibility references

Rules:

- the model represents utterances
- the model does not interpret them
- the model does not own utterance processing

---

## Decomposition Representation

Decomposition representation captures decomposition outcomes and decomposed item visibility.

Required concepts:

- decomposition results
- decomposed item references
- decomposition visibility references

Rules:

- the model represents decomposition outcomes only
- the model does not perform decomposition
- the model does not own decomposition behavior

---

## Item Lineage Representation

Item lineage representation captures parent-child decomposition relationships and traceability.

Required concepts:

- lineage references
- parent-child decomposition references
- decomposition traceability references

Rules:

- the model represents lineage only
- the model does not calculate lineage
- the model does not define interpretation algorithms

---

## Provenance Propagation Representation

Provenance propagation representation captures propagated provenance and attribution lineage for decomposed items.

Required concepts:

- propagated provenance references
- attribution propagation references
- explanation lineage references

IMPORTANT:

- do not recreate provenance fields
- do not duplicate created_by
- do not duplicate added_by
- do not duplicate assigned_to
- do not duplicate completed_by
- do not duplicate attribution_confidence
- do not duplicate explanation_source

The model must consume [docs/models/provenance-model.md](provenance-model.md).

---

## Optional Interpretation Metadata

The following interpretation metadata may be included when useful and contract-compatible:

- ambiguity_reference
- confirmation_reference
- future_capture_extension

Evaluation:

- ambiguity_reference: include when a downstream consumer needs a governed ambiguity marker for explainability without defining interpretation behavior
- confirmation_reference: include when a downstream consumer needs a governed confirmation marker for traceability without defining confirmation workflows
- future_capture_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

Ambiguity and confirmation may only exist as references.

---

## Task Experience Relationship

Multi-Item Capture may produce Task Experience references.

Task Experience remains authoritative.

---

## Shopping Experience Relationship

Multi-Item Capture may produce Shopping Experience references.

Shopping Experience remains authoritative.

---

## Provenance Relationship

Multi-Item Capture consumes Provenance Model.

Provenance remains authoritative.

No provenance duplication permitted.

---

## Household Memory Relationship

Multi-Item Capture may consume Household Memory references.

Household Memory remains authoritative.

---

## Person Relationship

Multi-Item Capture may reference Person Profile.

Identity authority remains external.

---

## Room Relationship

Multi-Item Capture may reference Room context.

Room authority remains external.

---

## Interaction Relationship

Multi-Item Capture consumes Interaction Model references.

Interaction remains authoritative.

---

## Occupancy Relationship

Multi-Item Capture may reference occupancy-sensitive context.

Occupancy remains externally governed.

No occupancy semantics may be defined here.

---

## Guest-Safe Behavior

Guest-safe behavior is governed by consuming contracts.

The model supports only reference-based boundaries.

Guests may receive:

- restricted result visibility
- reduced visibility
- no visibility

Unknown identities may receive:

- restricted visibility
- reduced visibility

---

## Explainability References

Explainability references support answers to:

- why the utterance was decomposed
- why specific items were produced
- how lineage was determined
- how ambiguity was represented

Required references:

- explanation_reference
- decomposition_reference
- lineage_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why was this item created?
- Why were these items separated?
- Why is lineage represented this way?
- Why was ambiguity preserved?

Machine explainability must support:

- utterance identifiers
- decomposition identifiers
- lineage identifiers
- provenance identifiers
- timestamps

---

## Provenance Requirements

Multi-Item Capture Result Model must consume Provenance Model references.

The model may not define alternate attribution semantics.

The model may not duplicate provenance semantics.

Provenance must be propagatable to decomposed items.

---

## Non-Rights

Multi-Item Capture Result Model does NOT own:

- parser behavior
- decomposition behavior
- interpretation engines
- speech recognition
- provenance semantics
- occupancy semantics

---

## Model Example

Example structure:

capture_result:
  capture_result_id: capres_01J...
  utterance_reference:
    utterance_id: utterance_01J...
    utterance_visibility_reference:
      visibility_state: guest_safe
  decomposition_references:
    - decomposition_reference_id: decomp_01J...
      decomposed_item_reference:
        item_id: task.family.01J...
      decomposition_visibility_reference:
        visibility_state: explicit
      provenance_propagation_reference: provenance.decomp.01J...
  item_lineage_references:
    - lineage_reference_id: lineage_01J...
      parent_child_decomposition_reference:
        parent_item_id: utterance_01J...
        child_item_id: task.family.01J...
      decomposition_traceability_reference: trace.01J...
  provenance_propagation_references:
    - provenance_propagation_reference_id: provprop_01J...
      propagated_provenance_reference: provenance.item.01J...
      explanation_lineage_reference: provenance.lineage.01J...
  decomposition_explainability_references:
    - explanation_reference_id: explain_01J...
      decomposition_reference:
        decomposition_reference_id: decomp_01J...
      lineage_reference:
        lineage_reference_id: lineage_01J...
      provenance_reference: provenance.explainability.01J...
  timestamp: 2026-07-10T12:00:00Z
  capture_result_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Capture Feature | Supported | Notes |
|---|---|---|
| utterance references | yes | utterances are represented without interpretation |
| decomposition references | yes | decomposition outcomes are represented without performing decomposition |
| lineage references | yes | lineage is represented without calculating lineage |
| provenance propagation | yes | provenance remains propagatable to decomposed items |
| ambiguity references | yes | ambiguity is reference-based only |
| confirmation references | yes | confirmation is reference-based only |
| task relationship | yes | tasks may be produced as references without taking ownership |
| shopping relationship | yes | shopping may be produced as references without taking ownership |
| provenance relationship | yes | provenance remains authoritative |
| household memory relationship | yes | memory remains external and reference-based |
| interaction relationship | yes | interaction references may contribute to capture context |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authorities.

   The Multi-Item Capture Interpretation Contract defines decomposition governance, interpretation semantics, ambiguity handling, confirmation semantics, lineage semantics, explainability, and provenance consumption boundaries. The Provenance Contract defines attribution and lineage semantics.

2. Model responsibilities.

   Multi-Item Capture Result Model represents utterance references, decomposition references, item lineage references, provenance propagation references, and decomposition explainability references without taking ownership of parser behavior, interpretation behavior, speech recognition, or provenance semantics.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Multi-Item Capture Result Model is the authoritative bridge between the Multi-Item Capture Interpretation Contract, the Provenance Model, and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/multi-item-capture-result-model.md](../models/multi-item-capture-result-model.md) as authoritative.

Future Task Creation Workflows must treat [docs/models/multi-item-capture-result-model.md](../models/multi-item-capture-result-model.md) as authoritative.

Future Shopping Creation Workflows must treat [docs/models/multi-item-capture-result-model.md](../models/multi-item-capture-result-model.md) as authoritative.

Future Multi-Item Capture Consumption must treat [docs/models/multi-item-capture-result-model.md](../models/multi-item-capture-result-model.md) as authoritative.

Multi-Item Capture Result Model consumes Multi-Item Capture Interpretation Contract authority, Provenance Model authority, Task Experience Model authority, Shopping Experience Model authority, Experience Model authority, Household Memory Model authority, Person Profile Model authority, Room Model authority, Interaction Model authority, and Occupancy and Presence Model authority.
