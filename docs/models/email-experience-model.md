# Email Experience Model

## Purpose

The Email Experience Model defines how Concierge represents email awareness, importance indicators, summary references, source attribution references, and explainability references for downstream productivity experiences.

This model is a consumption model for email awareness context, importance indicators, summary references, attribution references, and explanation references.

This model does not define:

- mailbox behavior
- provider integrations
- synchronization behavior
- message delivery
- email systems of record

---

## Model Definition

Email Experience Model is:

A consumption model representing email awareness, importance indicators, summary references, attribution references, and explainability references used by HTBW productivity experiences.

The model is NOT:

- an email provider
- a mailbox implementation
- a mail transport system
- an email governance authority

Email Experience Model consumes governed inputs from Calendar and Email Experience Contract authority, Experience Model authority, Provenance Model authority, and Household Memory Model authority.

---

## Canonical Model Structure

Required fields:

email_experience:
  email_experience_id: emailexp_01J...
  email_awareness:
    email_reference:
      email_id: email.family.01J...
    email_awareness_state: known
    surfaced_email_references: []
    awareness_context_references: []
  importance_indicators: []
  summary_references: []
  source_attribution_references: []
  email_explainability_references: []
  provenance_references: []
  timestamp: 2026-07-10T12:00:00Z
  email_experience_state: active

Required metadata:

- email_experience_id
- timestamp
- email_experience_state

Email experience state is a governed presentation state and may be active, restricted, neutral, or unknown when contract-authorized.

---

## Email Awareness Representation

Email awareness represents the email-facing awareness required by downstream experiences.

Required concepts:

- email awareness
- surfaced email references
- awareness context references

Rules:

- the model represents awareness
- the model does not own mailbox data
- the model does not own email truth

---

## Importance Indicator Representation

Importance indicator representation captures relevance-aware email consumption.

Required concepts:

- importance indicators
- priority references
- awareness relevance references

Rules:

- the model consumes importance signals
- the model does not calculate importance
- the model does not define ranking behavior

---

## Summary Reference Representation

Summary reference representation captures the email summaries that may participate in downstream experiences.

Required concepts:

- summary references
- productivity summary inputs
- summarized awareness references

Rules:

- the model represents summary references only
- the model does not own summary generation
- the model does not own summary synthesis

---

## Source Attribution Representation

Source attribution representation captures the provenance-aware references used to explain email awareness.

Required concepts:

- attribution references
- source references
- explanation lineage references

Rules:

- the model consumes provenance
- the model does not define attribution semantics
- the model does not recreate attribution authority

---

## Optional Privacy Visibility Metadata

The following privacy metadata may be included when useful and contract-compatible:

- privacy_visibility_flag
- consent_visibility_reference
- future_email_extension

Evaluation:

- privacy_visibility_flag: include when a downstream consumer needs a compact visibility marker for guest-safe or consent-sensitive filtering
- consent_visibility_reference: include when visibility depends on a governed consent reference that must be preserved for explainability
- future_email_extension: exclude from the canonical core unless a future contract explicitly authorizes an additional governed extension field

These fields are optional because the base model must remain stable, reference-based, and consumption-only.

---

## Provenance Relationship

Email Experience consumes Provenance Model references.

Provenance Model remains authoritative.

Email Experience does not define attribution semantics.

No alternate attribution semantics are permitted.

---

## Household Memory Relationship

Email Experience may consume Household Memory references.

Household Memory authority remains external.

Email Experience does not own memory state.

---

## Person Relationship

Email Experience may reference Person Profile context.

Identity authority remains external.

Email Experience does not own identity truth.

---

## Room Relationship

Email Experience may reference Room context.

Room authority remains external.

Email Experience does not own room truth.

---

## Briefing Relationship

Briefing experiences consume Email Experience references.

Email Experience does not own briefing composition.

---

## Productivity Synthesis Relationship

Productivity synthesis consumes Email Experience references.

Email Experience does not own synthesis behavior.

---

## Email Awareness Relationship

Email awareness experiences consume Email Experience references.

Email Experience does not own notification or delivery behavior.

---

## Occupancy Relationship

Email Experience may reference occupancy-sensitive context.

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

- why an email highlight was surfaced
- why a summary reference was included
- why an importance indicator was included
- why attribution information was presented

Required references:

- explanation_reference
- email_reference
- provenance_reference

Rules:

- explainability references support explanation only
- explainability references do not implement selection logic
- explainability references do not implement orchestration logic

---

## Explainability Requirements

Human explainability must support:

- Why was this email surfaced?
- Why was this summary created?
- Why was this email important?
- Why was this attribution shown?

Machine explainability must support:

- email identifiers
- importance references
- summary references
- provenance references
- timestamps

---

## Provenance Requirements

Email Experience may reference provenance-aware attribution.

Email Experience must consume Provenance Model references.

No alternate attribution semantics are permitted.

---

## Non-Rights

Email Experience Model does NOT own:

- mailbox behavior
- provider integrations
- synchronization
- message delivery
- provenance semantics
- occupancy semantics
- productivity policy

---

## Model Example

Example structure:

email_experience:
  email_experience_id: emailexp_01J...
  email_awareness:
    email_reference:
      email_id: email.family.01J...
    surfaced_email_references:
      - email_reference_id: emailref_01J...
        relevance_state: highlighted
    awareness_context_references:
      - awareness_context_reference_id: aware_01J...
        awareness_context_state: household_relevant
  importance_indicators:
    - importance_indicator_id: importance_01J...
      priority_state: important
      provenance_reference: provenance.importance.01J...
  summary_references:
    - summary_reference_id: summary_01J...
      summary_role: briefing_input
      provenance_reference: provenance.summary.01J...
  source_attribution_references:
    - attribution_reference_id: attribution_01J...
      source_reference:
        source_id: mailbox.family
      explanation_lineage_reference: provenance.attribution.01J...
  email_explainability_references:
    - explanation_reference_id: explain_01J...
      email_reference:
        email_id: email.family.01J...
      provenance_reference: provenance.explainability.01J...
  provenance_references:
    - provenance_reference_id: provenance.email_experience.01J...
  timestamp: 2026-07-10T12:00:00Z
  email_experience_state: active

Illustrative only.

No implementation logic.

---

## Model Coverage Matrix

| Email Feature | Supported | Notes |
|---|---|---|
| email awareness | yes | awareness is represented through email references and governed awareness state |
| importance indicators | yes | importance is consumed, not calculated |
| summary references | yes | summary participation is represented without owning summary synthesis |
| source attribution references | yes | attribution remains provenance-based |
| provenance references | yes | provenance remains authoritative |
| household memory references | yes | memory remains external and reference-based |
| person references | yes | person context may be referenced without owning identity |
| room references | yes | room context may be referenced without owning room truth |
| occupancy references | yes | occupancy-sensitive context may be referenced without defining occupancy semantics |
| guest-safe visibility | yes | visibility boundaries are expressed through references and governed states |

---

## Contract / Model Alignment Review

1. Contract authority.

   The Calendar and Email Experience Contract defines email experience visibility, discoverability, explainability, privacy, consent, source attribution, and household productivity boundaries.

2. Model responsibilities.

   Email Experience Model represents email awareness, importance indicators, summary references, source attribution references, and email explainability references without taking ownership of mailbox truth, provider execution, synchronization, or message delivery.

3. Any gaps identified.

   No gaps identified.

---

## Canonical Architecture Linkage

Email Experience Model is the authoritative bridge between the Calendar and Email Experience Contract and E13 Productivity Experiences.

Future E13 Productivity Experiences must treat [docs/models/email-experience-model.md](../models/email-experience-model.md) as authoritative.

Future Briefing Generation must treat [docs/models/email-experience-model.md](../models/email-experience-model.md) as authoritative.

Future Email Awareness Experiences must treat [docs/models/email-experience-model.md](../models/email-experience-model.md) as authoritative.

Future Productivity Synthesis must treat [docs/models/email-experience-model.md](../models/email-experience-model.md) as authoritative.

Email Experience Model consumes Calendar and Email Experience Contract authority, Provenance Model authority, Household Memory Model authority, and Experience Model authority.
