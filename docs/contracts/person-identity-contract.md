# Person Identity Contract

## Purpose

This contract defines how person identity is represented and consumed by Concierge.

It establishes shared rules for:

- person attribution
- interaction style personalization
- enrollment and consent
- correction-based improvement

---

## Core Principle

Identity is behavioral context.

Identity does not redefine truth.

Identity does not bypass safety.

---

## Scope

This contract applies to:

- Concierge runtime orchestration
- person-aware response routing
- person preference projection in UI
- opt-in learning mode for attribution and style

This contract does not define authentication security.

---

## Required Inputs

Identity-capable implementations may read:

- Home Assistant person entities
- BLE room proximity devices
- Aqara room presence devices
- presence and occupancy context
- room and interaction space context
- conversation correlation context (`conversation_id`, `device_id`, `satellite_id`)
- explicit user corrections
- optional speaker-attribution provider output

Implementations must not assume any source is perfect.

---

## Required Outputs

Identity layer output must include:

- person_id or neutral
- confidence
- attribution_factors
- linked_identity_devices
- linked_presence_devices
- room_candidate
- room_confidence
- effective_interaction_style
- expiration metadata
- explainability summary

Identity outputs are short-lived runtime context and must not become long-lived
identity sessions unless an accepted ADR explicitly approves extended retention.

Runtime identity outputs must never include raw audio, embeddings, vectors, or
biometric internals.

---

## Decision Rights

Identity layer may:

- select an effective person context
- apply person style preferences
- recommend device binding during enrollment
- recommend responder election weighting
- recommend clarification when confidence is low
- contribute room candidate resolution from person-linked mobile endpoints and BLE proximity context

---

## Non-Rights

Identity layer must not:

- mutate foundational truth
- select execution targets directly
- bypass action safety policy
- produce hidden personalization behavior
- silently link or unlink devices without explicit consent
- infer age class (minor/adult) from behavior, voice, or usage patterns

---

## Confidence Rules

Identity confidence must be explicit.

Behavior by confidence:

- high confidence: apply person style
- medium confidence: apply person style with conservative fallback
- low confidence: apply neutral style and optionally ask concise clarification

Room behavior by confidence:

- high confidence: allow room-context informational responses
- medium confidence: allow room-context informational responses with conservative phrasing
- low confidence: ask room clarification before room-context responses

Low confidence must never block low-risk deterministic actions.

Runtime attribution reuse defaults should remain short-lived:

- known high confidence: 30 seconds
- known medium confidence: 15 seconds
- low confidence or ambiguous: 5 to 10 seconds
- unknown: no reuse
- unavailable: no reuse

Absolute cap: 60 seconds unless superseded by accepted ADR authority.

`conversation_id` is a correlation key and not identity authority.

---

## Enrollment And Consent Rules

Enrollment must be explicit and revocable.

Requirements:

- clear consent prompt
- clear purpose description
- clear delete profile option
- clear update profile option
- clear disable identity personalization option
- clear device binding and unbinding option
- clear voice enrollment and unenrollment option

No enrollment may occur silently.

Device bindings are part of the identity profile and must be editable from the people setup flow.

---

## Correction And Learning Rules

The system may learn from correction signals such as:

- wrong person attribution
- style mismatch feedback
- repeated manual style overrides

Learning must be:

- transparent
- reversible
- explainable
- bounded

Learning must never create surprising behavior shifts.

---

## Explainability Rules

Identity processing must produce two explainability forms.

Machine form:

- structured factors and confidence
- reason codes
- timestamps

Human form:

- plain-language explanation
- concise rationale
- no technical jargon unless user requests technical detail

---

## Failure Handling

If identity data is incomplete or stale:

- fall back to neutral household style
- continue deterministic command processing
- request clarification only when required

If no known-device/person linkage is available:

- classify interaction as guest-unlinked
- do not create inferred persistent person identity
- allow low-risk informational handling with neutral style

The system must not fail command execution only because identity is uncertain.

For identity-required and sensitive actions, policy may challenge or deny when
identity is missing, stale, ambiguous, or unavailable.

---

## Integration Responsibilities

### Concierge

Must:

- consume identity context when available
- apply person style within policy bounds
- preserve deterministic action behavior
- classify identity requirement before executing protected/person-scoped intents

Must not:

- invent identity without evidence
- use identity to bypass room context
- perform biometric comparison or speaker attribution logic

### Voice Identity

Must:

- perform attribution while audio is available
- own attribution context lifecycle and expiry
- publish safe attribution context outputs for consumers

Must not:

- transfer biometric internals across consumption boundaries

### Other Integrations

May:

- expose identity signals through explicit contracts

Must not:

- bypass identity contract outputs in Concierge

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-008 Personalization Governance Boundaries
- ADR-009 Household Memory Governance Boundaries
- ADR-010 Household Productivity Experience Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- HACS and Platinum Governance Standard

This contract defines identity-consumption boundaries and does not redefine identity governance ownership.

---

## Ownership Boundary Validation

Ownership constraints in this contract:

- Voice Identity remains authoritative for attribution and confidence outputs
- Foundation remains authoritative for room and occupancy truth used during attribution context resolution
- Coordinator V2 consumes identity context for orchestration and does not own attribution algorithms

---

## Terminology Alignment

Canonical terminology in this contract:

- Attribution
- Confidence
- Personalization
- Occupancy
- Presence
- Context
- Scope

Identity requirement classification vocabulary:

- `identity_not_required`
- `identity_optional`
- `identity_required`
- `identity_required_fresh`
- `identity_required_step_up`

Legacy V1 assumptions that identity can bypass governance or safety boundaries are prohibited.

---

## Final Principle

Person-aware interaction should improve comfort and reduce friction while preserving determinism, transparency, and user agency.
