# Voice Profile Enrollment Architecture

## Purpose

This document defines the canonical Homes That Behave Well architecture for Concierge voice profile enrollment before implementation.

It establishes the source-of-truth decisions for:

- enrollment capture providers
- enrollment engine authority
- external storage handling
- session lifecycle
- cleanup and retention
- diagnostics and repairs
- supported-now and future provider boundaries

---

## Design Goals

- keep browser microphone enrollment as the preferred path
- support satellite capture as an alternate provider when feasible
- keep the existing enrollment engine as the sole authority for profile logic
- require external storage for all raw enrollment recordings
- enforce zero default retention of raw enrollment recordings
- enforce mandatory and idempotent cleanup
- preserve runtime recognition, room context, routing, and preference behavior
- remain local-first, deterministic, and self-healing

---

## Guiding Principles

- privacy over convenience
- explicit opt-in enrollment only
- personalization context only, never authentication
- deterministic lifecycle with mandatory cleanup
- provider parity across browser and satellite paths
- diagnostics and repairs must be actionable and sanitized

---

## Supported Enrollment Methods

### Preferred method

Browser microphone enrollment remains the preferred method when browser capture is available.

### Alternate method

Satellite capture is an alternate provider and must be capability-probed.

### Future method

A Concierge-compatible satellite client may be added for environments where native satellite capture is unavailable.

---

## Browser Enrollment Architecture

Browser enrollment must:

- validate external storage before capture starts
- create a tracked enrollment session
- write samples only into session-scoped external storage
- submit samples to the same enrollment engine pipeline
- trigger the same cleanup lifecycle on all terminal outcomes

Rationale:

The browser path is currently proven and should remain backward compatible while adopting the new lifecycle and privacy guarantees.

---

## Satellite Enrollment Architecture

Satellite enrollment must:

- be selected only when browser capture is unavailable or intentionally not used
- capability-probe supported Home Assistant capture mechanisms
- reject unsupported capture paths with clear, user-safe errors
- use the same session, storage, engine, and cleanup lifecycle as browser capture

Rationale:

This prevents unsupported API assumptions and avoids provider-specific policy drift.

---

## Provider Model

The architecture separates concerns into interchangeable providers:

- capture provider: obtains enrollment samples
- storage provider: persists temporary session artifacts externally
- enrollment engine: validates quality, builds embeddings and profiles, persists profile outputs

Rationale:

Provider substitution must not require enrollment engine changes.

---

## Enrollment Engine Authority

The enrollment engine is the only authority for:

- sample validation and quality analysis
- embedding generation
- profile generation and persistence
- profile update and replacement policy

Capture and storage providers must not own profile decision logic.

---

## Session Architecture

Each enrollment operation is a managed session with:

- session identity
- person reference
- provider metadata
- state
- expiration
- cleanup status
- session manifest

Every temporary recording must belong to a tracked session.

---

## Cleanup Architecture

Cleanup is a first-class lifecycle component.

Cleanup must run after:

- successful profile generation
- cancellation
- enrollment failure
- timeout
- startup reconciliation and orphan detection

Cleanup is mandatory and idempotent.

Rationale:

Privacy and retention guarantees are not enforceable unless cleanup is terminal-state gated.

---

## Storage Architecture

Raw enrollment recordings:

- must be written only to configured external storage
- must never be stored in Home Assistant config or persistent Home Assistant storage surfaces
- must be treated as temporary processing artifacts

Default retention for raw recordings is zero.

---

## Startup Recovery

On integration startup:

- validate external storage availability and writeability
- scan active enrollment sessions
- detect stale and orphaned session folders
- execute idempotent cleanup
- raise sanitized repairs for unresolved failures

Rationale:

The system must self-heal after restart without leaving abandoned raw recordings.

---

## Diagnostics Model

Diagnostics must use allowlist output and may include only sanitized operational metadata.

Diagnostics must not expose:

- raw audio
- raw audio paths
- embeddings
- profile vectors
- sensitive person payloads

---

## Repairs Model

Repairs issues are required for:

- external storage missing or misconfigured
- storage unavailable or not writable
- cleanup failures
- orphan cleanup failures
- capture provider unavailable or unsupported
- selected satellite unavailable

Repairs content must be actionable and sanitized.

---

## Future Extensibility

This architecture supports future additions without changing enrollment engine authority:

- additional capture providers
- additional external storage providers
- optional diagnostic retention mode with explicit opt-in and time limits

---

## Out-of-Scope Decisions

This architecture does not change:

- runtime speaker recognition behavior
- room context logic
- conversation routing logic
- preference resolution logic
- safety confirmation policy
- authentication model

Voice identity remains personalization context only.

---

## Related Documents

- [Voice Enrollment Lifecycle and State Machine](voice-enrollment-lifecycle-and-state-machine.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [Voice Enrollment Privacy and Data Handling Policy](voice-enrollment-privacy-and-data-handling-policy.md)
- [Voice Enrollment Domain Model](../models/voice-enrollment-domain-model.md)
- [Voice Profile Lifecycle Management](voice-profile-lifecycle-management.md)
- [Temporary Artifact Lifecycle Pattern](../patterns/temporary-artifact-lifecycle-pattern.md)
- [Voice Enrollment Modernization Roadmap](voice-enrollment-modernization-roadmap.md)
- [Implementation Verification Checklist](implementation-verification-checklist.md)
