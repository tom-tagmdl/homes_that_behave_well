# Identity Governance Reference

## Purpose

This document records HTBW identity governance constraints used by Concierge and Voice Identity integrations.

Governance authority remains in HTBW architecture, ADRs, contracts, and models.

---

## Core Principle

Identity must remain local-first, explainable, consent-based, and reversible.

Identity context improves orchestration quality but does not replace foundational truth or safety policy.

---

## Voice Enrollment Reference Map

| Aspect | Authoritative Document |
|---|---|
| Platform boundary for identity service ownership | [adr-voice-identity-platform-service.md](adr-voice-identity-platform-service.md) |
| End-to-end enrollment architecture | [voice-profile-enrollment-architecture.md](voice-profile-enrollment-architecture.md) |
| Enrollment lifecycle states and transitions | [voice-enrollment-lifecycle-and-state-machine.md](voice-enrollment-lifecycle-and-state-machine.md) |
| Storage, cleanup, retention rules | [voice-enrollment-storage-cleanup-and-retention-architecture.md](voice-enrollment-storage-cleanup-and-retention-architecture.md) |
| Privacy and data handling policy | [voice-enrollment-privacy-and-data-handling-policy.md](voice-enrollment-privacy-and-data-handling-policy.md) |
| Domain responsibilities and ownership | [../models/voice-enrollment-domain-model.md](../models/voice-enrollment-domain-model.md) |
| Voice profile output lifecycle | [voice-profile-lifecycle-management.md](voice-profile-lifecycle-management.md) |
| Reusable temporary-artifact pattern | [../patterns/temporary-artifact-lifecycle-pattern.md](../patterns/temporary-artifact-lifecycle-pattern.md) |
| Implementation sequencing | [voice-enrollment-modernization-roadmap.md](voice-enrollment-modernization-roadmap.md) |
| Pre-coding verification gate | [implementation-verification-checklist.md](implementation-verification-checklist.md) |

---

## Service Ownership

- Voice Identity owns attribution confidence outputs and voice profile lifecycle.
- Concierge consumes identity outputs for orchestration and communication decisions.
- Foundation remains source of truth for room, area, device, occupancy, and presence facts.

Concierge must not own attribution algorithms or fingerprint lifecycle internals.

---

## Data Residency Matrix

Default posture is local-first.

| Data / Capability | Default Residency | Cloud Allowed | Notes |
|---|---|---|---|
| Voice samples | Local | Exception only | Capture and processing should remain in-home whenever possible. |
| Speaker embeddings | Local | Exception only | Identity trust data should not leave network by default. |
| Voice profiles | Local | Exception only | Profiles remain local unless explicit opt-in exception. |
| Person profiles | Local | No default cloud path | Home context records remain local. |
| Confidence history | Local | Exception only | Export only with explicit consent. |
| Corrections and learning records | Local | Exception only | Must remain auditable and reversible. |
| Diagnostics payloads | Local | Optional export | Only when diagnostics sharing is enabled. |

---

## Consent and Revocation Lifecycle

Required lifecycle:

1. enrollment requested
2. purpose explained
3. consent granted
4. capture and processing
5. profile created or updated
6. confidence and metadata recorded
7. pause or revoke available at any time
8. revocation immediately stops active use
9. explicit delete removes governed artifacts per policy
10. re-enrollment remains available

Rules:

- no silent enrollment
- revocation is immediate
- deletion is explicit
- consent remains scoped and auditable

---

## Confidence Policy

Confidence bands govern personalization and clarification behavior, not ownership or truth mutation.

- high confidence: allow direct personalization
- medium confidence: conservative personalization
- low confidence: neutral style and deterministic routing
- very low confidence: concise clarification when necessary

Low confidence must not block safe, deterministic low-risk actions.

---

## Responder Election Policy

Concierge must elect one primary responder when multiple assistants hear the same request.

Election inputs may include:

- interaction space
- room proximity
- attribution confidence
- presence and occupancy
- conversation ownership
- posture and activity

Rules:

- one primary responder
- suppress duplicates
- preserve conversation continuity
- log explainable reason codes

---

## Learning and Rollback Policy

Learning is allowed only when bounded and reversible.

Allowed adjustments:

- personalization style weighting
- responder weighting
- confidence calibration

Learning must not rewrite foundational truth or source-of-record ownership.

---

## Diagnostics And Explainability Policy

Explainability should be available in:

- machine form: confidence values, reason codes, source lineage, timestamps
- human form: plain-language explanation and concise rationale

Diagnostics should explain:

- why attribution was selected
- why room or interaction-space context was selected
- why a responder was elected
- why a cloud exception path was used when applicable

---

## Voice Training Safety Boundary

Voice training may improve attribution quality, but it must not become hidden authentication.

Rules:

- opt-in only
- revocable
- bounded to approved Concierge uses
- cannot bypass safety confirmations
- cannot authorize protected actions on its own

---

## Cloud Exception Governance

Cloud usage is an explicit exception.

A cloud path may be used only when:

- user opt-in is explicit
- purpose is explained
- local path cannot satisfy capability
- scope is bounded and revocable

Cloud use must be visible in setup and diagnostics.

---

## Room And Person Setup Separation Rule

- rooms-and-areas setup governs room/space definitions and device scope
- people setup governs person profile, device binding, and voice enrollment
- runtime must reuse setup-authored mappings and avoid hidden category inference

---

## Compatibility and Versioning Rule

Household-facing outcome preservation is required.

Implementation compatibility, API compatibility, and legacy data-model compatibility are not required by default.

When schemas evolve:

- publish explicit versioning
- preserve deterministic household outcomes
- avoid hidden migration behavior that violates architecture boundaries

---

## Terminology

- Identity Context: person-aware context consumed by Concierge from governed signals
- Voice Profile: enrolled speaker profile governed by Voice Identity lifecycle
- Attribution Snapshot: runtime attribution confidence output
- Interaction Space: active room or merged-space context for orchestration
- Local-first: identity data remains local unless explicit cloud exception policy applies

---

## Final Principle

Identity governance is architecture-owned by HTBW and runtime-consumed by Concierge. Governance does not move into runtime orchestration.
