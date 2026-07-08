# Voice Enrollment Storage, Cleanup, and Retention Architecture

## Purpose

This document defines storage, cleanup, and retention architecture for Concierge voice enrollment temporary artifacts.

It is the canonical source for external storage dependency, session layout, cleanup guarantees, and retention boundaries.

---

## External Storage Dependency

Enrollment recordings require configured external storage.

Enrollment must fail before recording starts if storage is:

- missing
- unavailable
- not writable
- misconfigured
- permission denied

Failure handling must include:

- no capture start
- no partial file creation
- repairs issue
- clear user-safe error
- sanitized diagnostics

---

## Minimal Session Storage Layout

Default layout:

voice_enrollment/
  active/
    session_<id>/
      session.json
      sample_001.wav
      sample_002.wav

This architecture intentionally uses active session storage only.

---

## Why Quarantine and Diagnostics Recording Archives Are Excluded

Default design excludes quarantine and diagnostics recording archives because:

- raw enrollment audio is highly sensitive
- permanent or semi-permanent recording archives increase privacy risk
- default retention policy is zero raw-audio retention
- operational diagnostics do not require raw audio retention

Any future diagnostic retention mode must be explicit opt-in and time-limited.

---

## Session Manifest Design

Each active session folder must include session.json.

Manifest purpose:

- deterministic cleanup
- startup recovery
- orphan detection
- idempotent reconciliation

Manifest contains non-sensitive operational metadata only.

Manifest is temporary and must be deleted during cleanup.

---

## Cleanup Architecture

Cleanup is handled by a dedicated enrollment cleanup manager.

Cleanup triggers:

- successful profile generation
- cancellation
- enrollment failure
- timeout
- startup reconciliation
- orphan detection

Cleanup operations:

- delete sample files
- delete session manifest
- remove session folder
- release runtime buffers
- emit cleanup result event

---

## Idempotent Cleanup Requirements

Cleanup must be safe when called repeatedly for the same session.

Cleanup must not fail only because:

- sample files are already deleted
- session folder is already removed
- manifest is already missing
- cleanup already ran from another trigger path

Missing artifacts are treated as already-clean unless there is clear storage or permission failure.

---

## Success Cleanup

After profile commit:

- delete all temporary recordings
- delete session manifest
- remove session folder
- release buffers
- mark cleanup complete

Only profile outputs and sanitized metadata may remain.

---

## Cancel Cleanup

On cancellation:

- delete temporary recordings
- delete session manifest
- remove session folder
- release resources
- mark cleanup complete

---

## Failure Cleanup

On enrollment failure:

- delete temporary recordings
- delete session manifest
- remove session folder
- release buffers
- record diagnostics-safe failure metadata only

---

## Timeout Cleanup

On timeout:

- transition to timeout pending cleanup
- run cleanup
- remove all temporary artifacts
- emit timeout cancellation event

---

## Startup Orphan Detection and Reconciliation

On startup:

1. validate storage health
2. scan active session folders
3. load manifests where present
4. treat missing or invalid manifests as orphaned sessions
5. run idempotent cleanup
6. create repairs for unresolved cleanup failures

---

## Cleanup Invariants

- no terminal session without cleanup attempt
- no retained raw recordings after successful enrollment in default mode
- provider path must not weaken cleanup policy
- startup reconciliation uses same cleanup semantics as runtime terminal cleanup

---

## Retention Architecture

Default mode:

- zero retention for raw enrollment recordings

Future diagnostic retention mode may be added only if:

- disabled by default
- explicit user opt-in
- strict time limit
- diagnostics-safe controls and tests

---

## Related Documents

- [Voice Enrollment Lifecycle and State Machine](voice-enrollment-lifecycle-and-state-machine.md)
- [Voice Enrollment Privacy and Data Handling Policy](voice-enrollment-privacy-and-data-handling-policy.md)
- [Temporary Artifact Lifecycle Pattern](../patterns/temporary-artifact-lifecycle-pattern.md)
