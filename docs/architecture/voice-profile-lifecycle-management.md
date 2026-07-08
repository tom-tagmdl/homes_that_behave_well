# Voice Profile Lifecycle Management

## Purpose

This document defines lifecycle management for voice profile outputs and their relationship to enrollment sessions.

It separates profile lifecycle from raw recording lifecycle.

---

## Core Principle

Voice profile lifecycle is durable profile governance.

Enrollment recording lifecycle is temporary artifact handling.

These lifecycles are related but not equivalent.

---

## Create Profile

Profile creation occurs only after explicit enrollment flow and successful engine validation.

Rules:

- explicit opt-in required
- quality checks required
- profile commit required before session success
- temporary recording cleanup required after commit

---

## Re-enroll Profile

Re-enrollment refreshes profile outputs through a new explicit session.

Rules:

- same consent and lifecycle requirements as initial enrollment
- same temporary artifact handling and cleanup policy
- previous profile handling follows replacement policy

---

## Replace Profile

Replacement updates active profile representation with newly generated output.

Rules:

- replacement must be deterministic and auditable
- replacement cannot retain raw enrollment recordings by default
- temporary session artifacts are always cleaned

---

## Delete Profile

Delete removes the active profile from personalization use according to Concierge profile policy.

Rules:

- delete is explicit and user-visible
- delete path is reversible only through re-enrollment
- delete operation is independent from temporary recording cleanup because raw recordings should already be cleaned

---

## Revoke Profile

Revoke disables profile use for personalization until re-enabled or replaced.

Rules:

- revocation is immediate
- revocation does not authorize retention of raw enrollment recordings

---

## Suspend Profile (Future Consideration)

Suspend is a potential future state for temporary profile deactivation.

Constraints:

- must remain explicit
- must not weaken privacy defaults
- must not imply recording retention

---

## Profile Update Rules

- only explicit enrollment sessions may create or update voice profiles
- normal runtime voice commands must never train profiles implicitly
- guest traffic must never auto-enroll or auto-update profiles

---

## Cleanup Requirements During Replacement

Profile replacement sessions must follow full cleanup lifecycle:

- success pending cleanup
- cleanup running
- cleanup complete

No replacement path may bypass cleanup.

---

## Profile Ownership Model

- profile belongs to person identity reference
- enrollment session owns temporary recordings
- profile lifecycle and recording lifecycle are intentionally decoupled

---

## Related Documents

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Voice Enrollment Privacy and Data Handling Policy](voice-enrollment-privacy-and-data-handling-policy.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](voice-enrollment-storage-cleanup-and-retention-architecture.md)
