# Voice Enrollment Lifecycle and State Machine

## Purpose

This document defines the approved lifecycle and state machine for Concierge voice enrollment sessions.

It is the canonical behavioral contract for session progression, terminal outcomes, and cleanup gating.

---

## Lifecycle Scope

This lifecycle applies to all enrollment providers:

- browser microphone provider
- satellite capture provider
- future Concierge-compatible satellite client provider

Provider differences must not change lifecycle and cleanup policy.

---

## Approved States

- idle
- preflight_validating
- preflight_failed
- session_created
- ready
- capture_pending
- capturing
- sample_received
- processing
- profile_building
- completed_pending_cleanup
- cancelled_pending_cleanup
- failed_pending_cleanup
- timeout_pending_cleanup
- cleanup_running
- cleanup_complete
- cleanup_failed

---

## Enrollment Lifecycle

1. User explicitly starts enrollment.
2. System validates storage and provider capability in preflight.
3. Session is created and moved to ready.
4. Capture provider collects samples into session storage.
5. Enrollment engine processes samples and builds profile.
6. Session enters terminal pending cleanup state.
7. Cleanup runs.
8. Session returns to idle only after cleanup completion.

---

## Transition Rules

### Preflight transitions

- idle -> preflight_validating
- preflight_validating -> preflight_failed
- preflight_validating -> session_created

### Capture transitions

- session_created -> ready
- ready -> capture_pending
- capture_pending -> capturing
- capturing -> sample_received
- sample_received -> processing
- processing -> profile_building when build criteria are met

### Terminal pending cleanup transitions

- profile_building -> completed_pending_cleanup on successful profile commit
- capturing, sample_received, processing, profile_building -> cancelled_pending_cleanup on cancel
- capturing, sample_received, processing, profile_building -> failed_pending_cleanup on unrecoverable error
- ready, capture_pending, capturing, sample_received, processing, profile_building -> timeout_pending_cleanup on expiration

### Cleanup transitions

- completed_pending_cleanup -> cleanup_running
- cancelled_pending_cleanup -> cleanup_running
- failed_pending_cleanup -> cleanup_running
- timeout_pending_cleanup -> cleanup_running
- cleanup_running -> cleanup_complete
- cleanup_running -> cleanup_failed
- cleanup_complete -> idle

---

## Terminal-State Cleanup Requirement

No enrollment session may reach final closure without cleanup attempt.

Terminal business outcomes must always flow through cleanup_running.

Disallowed behavior:

- completed -> idle without cleanup
- cancelled -> idle without cleanup
- failed -> idle without cleanup
- timeout -> idle without cleanup

---

## Cleanup Failure Handling

When cleanup fails:

- session enters cleanup_failed
- repairs issue is created with sanitized details
- diagnostics reflect cleanup failure status without sensitive artifacts

---

## Session Lifecycle Alignment

Each state transition must keep manifest metadata synchronized.

Session manifests exist to support:

- deterministic recovery
- orphan detection
- idempotent cleanup reconciliation

---

## Startup Reconciliation Lifecycle

On startup:

1. Validate external storage.
2. Scan active sessions.
3. Read manifest when present.
4. Detect stale or orphaned sessions.
5. Execute cleanup.
6. Raise repairs for unresolved failures.

---

## Related Documents

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [Implementation Verification Checklist](implementation-verification-checklist.md)
