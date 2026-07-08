# Voice Enrollment Privacy and Data Handling Policy

## Purpose

This policy defines privacy, data handling, and retention rules for Concierge voice enrollment.

It is the authoritative policy for handling enrollment recordings and related metadata.

---

## Core Policy

Voice enrollment is explicit, opt-in, local-first, and reversible.

Raw enrollment recordings are temporary processing inputs only.

---

## Data Classification

### Temporary sensitive artifacts

- raw enrollment recordings
- session manifest metadata
- transient in-memory buffers during enrollment processing

### Persistent artifacts

- voice profile outputs
- embedding or profile data already supported by the existing system
- sanitized enrollment audit metadata

---

## External Storage Requirement

Raw enrollment recordings must be stored only in configured external storage.

Raw recordings must not be stored in:

- Home Assistant config directory
- Home Assistant .storage
- recorder database
- entity state
- config entries
- diagnostics payloads
- persistent Home Assistant data structures

Enrollment must fail before capture when external storage is:

- missing
- unavailable
- not writable
- misconfigured
- permission denied

Failure behavior must include:

- no capture start
- no partial sample files
- repairs issue creation
- user-safe error explanation
- sanitized diagnostics status

---

## Retention Policy

Default retention policy is zero retention for raw enrollment recordings.

After successful profile generation, cancelled enrollment, failed enrollment, timeout, or restart reconciliation cleanup:

- raw recordings must be deleted
- session manifest must be deleted
- session folder must be removed

Future diagnostic retention mode may be added only if:

- disabled by default
- explicitly enabled by user
- time-limited
- clearly marked privacy-sensitive

---

## Consent Requirements

Enrollment requires explicit user initiation and consent.

The system must provide explicit paths to:

- pause
- revoke
- delete profile
- re-enroll

No silent enrollment is allowed.

---

## Guest Protections

Guests must never be automatically enrolled.

Normal voice traffic must never implicitly create enrollment sessions.

---

## Diagnostics Restrictions

Diagnostics must follow allowlist design.

Diagnostics may include:

- storage configured or not
- storage reachable or not
- storage writable or not
- active session count
- orphan session count
- cleanup status summaries
- provider availability summary
- retention mode

Diagnostics must not include:

- raw recordings
- raw recording paths
- sample payload contents
- embeddings or profile vectors
- sensitive person payloads

---

## Repairs Telemetry Boundaries

Repairs data must be actionable and sanitized.

Repairs must never include raw audio artifacts or sensitive filesystem details.

---

## User Expectation Statement

Enrollment recordings are temporary and should disappear automatically after their purpose is fulfilled.

Voice profile outputs may remain according to profile lifecycle policy.

---

## Related Documents

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [Identity Governance Reference](identity-governance-reference.md)
