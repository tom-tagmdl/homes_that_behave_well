# Voice Enrollment Domain Model

## Purpose

This document defines platform-level domain concepts for Concierge voice enrollment.

It describes behavior, boundaries, responsibilities, and relationships without prescribing code.

---

## Domain Concepts

### EnrollmentSession

Represents one explicit voice enrollment operation for one person reference.

Owns:

- session identity
- person reference
- provider metadata
- lifecycle state
- expiration and cleanup status
- sample progression metadata

### EnrollmentSessionManager

Owns session orchestration.

Responsibilities:

- create and track enrollment sessions
- validate and apply lifecycle transitions
- update manifest state
- track sample progression
- route terminal outcomes into cleanup flow

### EnrollmentCleanupManager

Owns temporary artifact reconciliation.

Responsibilities:

- execute cleanup for success, cancellation, failure, timeout
- execute startup orphan detection and cleanup
- enforce idempotent cleanup semantics
- emit cleanup result events
- trigger repairs when cleanup cannot complete

### EnrollmentStorageProvider

Owns temporary artifact storage boundary.

Responsibilities:

- validate storage readiness
- provide bounded session storage paths
- persist temporary samples and session manifest
- support deterministic deletion and reconciliation

### MountedPathEnrollmentStorageProvider

Default external storage provider for mounted path destinations.

Responsibilities:

- enforce operations within enrollment storage root
- validate reachability and writeability
- support session-scoped temporary storage only

### EnrollmentCaptureProvider

Represents a capture input provider.

Responsibilities:

- advertise capability
- capture and deliver session-bound samples
- support cancellation

### BrowserMicCaptureProvider

Preferred capture provider when browser capture is available.

### AssistPipelineSatelliteCaptureProvider

Alternate provider when supported Home Assistant capture capabilities are available and capability-probed.

### ConciergeSatelliteClientCaptureProvider

Future provider for external client push workflows in environments where native satellite capture is unavailable.

### CaptureProviderResolver

Owns provider selection policy.

Responsibilities:

- apply preferred provider precedence
- resolve provider by runtime capability
- return explicit unsupported reasons when no provider is feasible

### RetentionPolicyManager

Owns raw artifact retention policy.

Responsibilities:

- enforce zero default raw-audio retention
- gate optional future diagnostic retention mode
- verify cleanup policy compliance

---

## Relationship Model

1. Session manager creates EnrollmentSession.
2. Provider resolver selects EnrollmentCaptureProvider.
3. Capture provider delivers temporary samples.
4. Storage provider persists temporary session artifacts externally.
5. Enrollment engine consumes samples and commits profile outputs.
6. Session manager marks terminal pending-cleanup state.
7. Cleanup manager deletes temporary artifacts and closes lifecycle.
8. Retention policy manager verifies no default retention breach.

---

## Ownership Boundaries

- Enrollment engine owns profile quality and profile persistence decisions.
- Capture providers do not own profile policy.
- Storage providers do not own profile policy.
- Cleanup manager owns artifact destruction and reconciliation.

---

## Behavioral Invariants

- every sample belongs to exactly one tracked session
- every terminal session outcome flows through cleanup
- cleanup is idempotent and deterministic
- raw recording retention default is zero
- provider differences must not change lifecycle guarantees

---

## Related Documents

- [Voice Profile Enrollment Architecture](../architecture/voice-profile-enrollment-architecture.md)
- [Voice Enrollment Lifecycle and State Machine](../architecture/voice-enrollment-lifecycle-and-state-machine.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](../architecture/voice-enrollment-storage-cleanup-and-retention-architecture.md)
