# Knowledge Query Experience Model

## Purpose

The Knowledge Query Experience Model defines how Concierge represents knowledge requests, knowledge responses, source references, uncertainty references, and explainability references for downstream productivity experiences.

This model is a consumption model for knowledge request references, knowledge response references, source references, uncertainty references, and explanation references.

This model does not define:

- provider implementations
- OpenAI integrations
- retrieval systems
- search engines
- inference engines

---

## Model Definition

Knowledge Query Experience Model is:

A consumption model representing knowledge requests, knowledge responses, source references, uncertainty references, and explainability references used throughout HTBW productivity experiences.

The model is NOT:

- an LLM provider
- a retrieval engine
- a search platform
- a knowledge governance authority

Knowledge Query Experience Model consumes governed inputs from Knowledge, Briefing, and Household Status Synthesis Contract authority, Provenance Model authority, Experience Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

knowledge_experience:
  knowledge_experience_id: knowexp_01J...
  knowledge_request_references: []
  knowledge_response_references: []
  source_references: []
  uncertainty_references: []
  knowledge_explainability_references: []
  provenance_references: []
  timestamp: 2026-07-10T12:00:00Z
  knowledge_experience_state: active

Required metadata:

- knowledge_experience_id
- timestamp
- knowledge_experience_state

Knowledge experience state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Knowledge Request Representation

Knowledge request representation captures the request-facing context required by downstream experiences.

Required concepts:

- knowledge requests
- request context
- request visibility references

Rules:

- the model represents requests
- the model does not execute requests
- the model does not own retrieval behavior

---

## Knowledge Response Representation

Knowledge response representation captures the response-facing context required by downstream experiences.

Required concepts:

- knowledge responses
- response references
- response visibility references

Rules:

- the model represents responses
- the model does not generate responses
- the model does not own response synthesis

---

## Source Reference Representation

Source reference representation captures source-backed knowledge linkage and visibility.

Required concepts:

- source references
- source linkage
- source visibility references

Rules:

- the model represents source references only
- the model does not own source authority
- the model does not calculate source trust

---

## Uncertainty Reference Representation

Uncertainty reference representation captures uncertainty state and confidence visibility.

Required concepts:

- uncertainty references
- confidence visibility references
- uncertainty awareness references

Rules:

- the model represents uncertainty state only
- the model does not calculate uncertainty
- the model does not own confidence algorithms

---

## Optional Knowledge Metadata

The following knowledge metadata may be included when useful and contract-compatible:

- style_reference
- room_delivery_reference
- future_knowledge_extension

Evaluation:

- style_reference: include when a downstream consumer needs a governed response style reference for person-aware or household-aware presentation without defining generation logic
- room_delivery_reference: include when room-sensitive delivery context is required for explainable presentation routing
- future_knowledge_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Provenance Relationship

Knowledge Experience may consume Provenance Model references.

Knowledge Experience does not define attribution semantics.

---

## Household Memory Relationship

Knowledge Experience may consume Household Memory references.

Memory authority remains external.

---

## Person Relationship

Knowledge Experience may reference Person Profile context.

Identity authority remains external.

---

## Room Relationship

Knowledge Experience may reference Room context.

Room authority remains external.

---

## Briefing Relationship

Briefing experiences consume Knowledge Experience references.

Knowledge Experience does not own briefing composition.

---

## Household Status Synthesis Relationship

Household Status Synthesis consumes Knowledge Experience references.

Knowledge Experience does not own synthesis behavior.

---

## Productivity Synthesis Relationship

Productivity synthesis consumes Knowledge Experience references.

Knowledge Experience does not own synthesis behavior.

---

## Occupancy Relationship

Knowledge Experience may reference occupancy-sensitive context.

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

- why a response was surfaced
- why a source was referenced
- why uncertainty exists
- why a response was considered source-backed

Required references:

- explanation_reference
- knowledge_reference
- source_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why was this response provided?
- Why was this source used?
- Why is this response uncertain?
- Why is this response considered reliable?

Machine explainability must support:

- request identifiers
- response identifiers
- source references
- uncertainty references
- timestamps

---

## Provenance Requirements

Knowledge Experience may reference provenance-aware attribution.

Knowledge Experience must consume Provenance Model references when attribution is needed.

No alternate attribution semantics are permitted.

---

## Non-Rights

Knowledge Query Experience Model does NOT own:

- provider integrations
- retrieval systems
- search systems
- response generation
- prompting
- provenance semantics
- occupancy semantics

---

## Model Example

Example structure:

knowledge_experience:
  knowledge_experience_id: knowexp_01J...
  knowledge_request_references:
    - knowledge_request_reference_id: knowreq_01J...
      request_context:
        query: "What is the status of the household?"
      request_visibility_reference:
        visibility_state: guest_safe
      provenance_reference: provenance.request.01J...
  knowledge_response_references:
    - knowledge_response_reference_id: knowresp_01J...
      response_visibility_reference:
        visibility_state: neutral
      provenance_reference: provenance.response.01J...
  source_references:
    - source_reference_id: source_01J...
      source_linkage:
        source_id: knowledge.base.01J...
      source_visibility_reference:
        visibility_state: explicit
  uncertainty_references:
    - uncertainty_reference_id: uncert_01J...
      confidence_visibility_reference:
        confidence_state: partial
      provenance_reference: provenance.uncertainty.01J...
  knowledge_explainability_references:
    - explanation_reference_id: explain_01J...
      knowledge_reference:
        knowledge_id: knowresp_01J...
      source_reference:
        source_id: knowledge.base.01J...
      provenance_reference: provenance.explainability.01J...
  provenance_references:
    - provenance_reference_id: provenance.knowledge_experience.01J...
  timestamp: 2026-07-10T12:00:00Z
  knowledge_experience_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Knowledge Feature | Supported | Notes |
|---|---|---|
| knowledge requests | yes | requests are represented without executing them |
| knowledge responses | yes | responses are represented without generating them |
| source references | yes | sources are represented without owning source authority |
| uncertainty references | yes | uncertainty is represented without calculating it |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| person references | yes | person context may be referenced without owning identity |
| room references | yes | room context may be referenced without owning room truth |
| briefing relationship | yes | knowledge references may participate in briefing without owning composition |
| household status synthesis relationship | yes | knowledge references may participate in status synthesis without owning behavior |
| productivity synthesis relationship | yes | knowledge references may participate in synthesis without owning behavior |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Knowledge, Briefing, and Household Status Synthesis Contract defines knowledge experience visibility, explainability, calm-by-default behavior, guest-safe limits, source attribution, and uncertainty handling.

2. Model responsibilities.

   Knowledge Query Experience Model represents knowledge request references, knowledge response references, source references, uncertainty references, and knowledge explainability references without taking ownership of provider behavior, retrieval behavior, response generation, or provenance semantics.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Knowledge Query Experience Model is the authoritative bridge between the Knowledge, Briefing, and Household Status Synthesis Contract and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/knowledge-query-experience-model.md](../models/knowledge-query-experience-model.md) as authoritative.

Future Briefing Experiences must treat [docs/models/knowledge-query-experience-model.md](../models/knowledge-query-experience-model.md) as authoritative.

Future Household Status Synthesis must treat [docs/models/knowledge-query-experience-model.md](../models/knowledge-query-experience-model.md) as authoritative.

Future Productivity Synthesis must treat [docs/models/knowledge-query-experience-model.md](../models/knowledge-query-experience-model.md) as authoritative.

Knowledge Query Experience Model consumes Knowledge, Briefing, and Household Status Synthesis Contract authority, Provenance Model authority, Household Memory Model authority, and Experience Model authority.
