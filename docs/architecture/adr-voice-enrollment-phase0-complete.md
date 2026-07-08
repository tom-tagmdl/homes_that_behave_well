# ADR: Voice Enrollment Phase 0 Complete

## Status

Accepted and complete.

## Context

Concierge voice enrollment required a privacy-first, deterministic, externally stored, self-healing platform before production enrollment workflows could be built safely.

Phase 0 existed to establish that platform without changing runtime recognition behavior, profile generation behavior, or introducing user-facing workflow redesign.

The target architecture required:

- EnrollmentSession as lifecycle authority
- EnrollmentStorageProvider as artifact authority
- session.json as the durable session projection
- EnrollmentCleanupManager as cleanup executor
- fail-closed storage preflight before capture
- startup orphan reconciliation
- sanitized Repairs integration
- allowlist-only Diagnostics output
- architecture-protection tests to prevent regression

## Decision

Phase 0 is complete.

Concierge now has the platform foundations required for production voice enrollment implementation in Phase 1.

Future work must build on these foundations rather than bypass them.

## Architecture Summary

The completed Phase 0 platform establishes the following architecture:

- EnrollmentSession owns enrollment lifecycle state and transition authority
- EnrollmentStorageProvider owns temporary enrollment artifacts and storage policy
- session.json is the provider-owned durable projection of EnrollmentSession
- EnrollmentCleanupManager executes idempotent cleanup through the provider
- Storage Preflight blocks unsafe enrollment before capture and upload writes
- Startup Reconciliation identifies orphaned or invalid enrollment state and invokes cleanup
- Repairs surfaces actionable, sanitized operational failures
- Diagnostics exposes allowlisted operational summaries only

## Ownership Boundaries

The ownership model is now explicit:

- EnrollmentSession owns lifecycle
- EnrollmentStorageProvider owns artifacts
- session.json owns durable session projection
- EnrollmentCleanupManager executes cleanup but does not own lifecycle
- Repairs publishes issues but does not own lifecycle or cleanup
- Diagnostics projects operational state but does not own state or artifacts

Future voice enrollment features must consume these platform services rather than bypass them.

Required platform services:

- EnrollmentSession
- EnrollmentStorageProvider
- Session Manifest
- CleanupManager
- Preflight Validation
- Startup Reconciliation
- Repairs
- Diagnostics

Bypassing these services in future voice-enrollment work is an architectural defect.

## Operational Guarantees

Phase 0 now guarantees:

- raw enrollment recordings are external-storage-only
- unsafe storage conditions fail closed before capture begins
- temporary recording cleanup is idempotent
- startup reconciliation can identify orphan and invalid state
- structured operational failures can surface through Repairs
- operational visibility is available through sanitized Diagnostics
- runtime behavior is protected by architecture-focused tests

## Privacy Guarantees

Phase 0 enforces the following privacy guarantees:

- no raw enrollment recordings in Home Assistant config or persistent storage surfaces
- zero default retention intent for raw enrollment artifacts
- no diagnostics state dumps
- no manifest content exposure in diagnostics
- no repairs payloads with raw paths, audio names, embeddings, or profile internals
- no broad export of session internals merely because they exist in memory

## Testing Guarantees

Architecture-protection tests now exist to guard:

- EnrollmentSession lifecycle authority
- EnrollmentStorageProvider artifact authority
- session.json projection-only behavior
- CleanupManager execution-only behavior
- preflight fail-closed behavior
- startup reconciliation foundations
- Repairs mapping and idempotence
- Diagnostics allowlist-only behavior
- privacy non-disclosure boundaries
- idempotent behavior for repeated cleanup and issue operations

## Future Contribution Requirements

Future voice enrollment changes must satisfy all of the following:

- do not bypass EnrollmentSession for lifecycle transitions
- do not bypass EnrollmentStorageProvider for artifact reads, writes, validation, or deletion
- do not store raw enrollment artifacts in Home Assistant storage surfaces
- do not treat session.json as a new source of truth
- do not make CleanupManager a lifecycle owner
- do not publish unsanitized Repairs payloads
- do not reintroduce diagnostics dumps or unapproved operational fields
- do not weaken preflight fail-closed behavior
- do not implement provider-specific logic that creates policy drift between enrollment paths

Future voice enrollment features must consume these platform services rather than bypass them:

- EnrollmentSession
- EnrollmentStorageProvider
- Session Manifest
- CleanupManager
- Preflight Validation
- Startup Reconciliation
- Repairs
- Diagnostics