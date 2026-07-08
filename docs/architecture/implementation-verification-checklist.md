# Implementation Verification Checklist

## Purpose

This checklist defines repository facts that must be verified before implementation begins.

It is the architecture-to-implementation integrity gate.

---

## Repository Fact Verification

### Enrollment storage and upload behavior

- verify existing enrollment upload endpoint behavior
- verify current sample write location and path normalization rules
- verify existing external storage resolution behavior

### Diagnostics and data exposure

- verify current diagnostics payload contents
- verify whether diagnostics currently include broad state snapshots
- verify where sensitive fields or path details may leak

### Event and lifecycle conventions

- verify existing event naming and payload conventions
- verify current enrollment lifecycle transition handling
- verify timeout and cancellation flow behavior

### Localization and user-safe messaging

- verify strings and translation key structures for new lifecycle and repair messages
- verify where preflight and provider capability errors should be surfaced to users

### Setup and startup hooks

- verify integration startup hook locations for storage preflight and orphan reconciliation
- verify where startup cleanup summaries should be surfaced

### Enrollment persistence boundaries

- verify what enrollment metadata is currently persisted
- verify whether raw recording references are persisted beyond temporary scope
- verify where profile lifecycle data and recording lifecycle data are currently coupled

### Provider feasibility boundaries

- verify current supported browser capture path behavior
- verify current Home Assistant-supported satellite capture feasibility in target environments
- verify unsupported-path handling and fallback messaging requirements

### Repairs integration points

- verify existing repairs usage patterns in related integrations if applicable
- verify issue creation and lifecycle strategy for storage and cleanup failures

### Security and logging boundaries

- verify current logging patterns for path and payload safety
- verify where sanitization is needed to avoid sensitive filesystem disclosure

### Test coverage baseline

- verify current service, panel, diagnostics, init, and config flow tests
- verify gaps for lifecycle, cleanup idempotence, startup reconciliation, and privacy assertions

---

## Required Pre-Coding Assertions

Before coding begins, confirm:

- external-storage-only recording handling can be enforced without ambiguity
- cleanup lifecycle can be made terminal-state mandatory
- cleanup can be made idempotent across overlapping triggers
- startup reconciliation has a deterministic integration hook
- diagnostics allowlist can exclude sensitive payloads
- repairs can be issued with actionable sanitized context
- browser and satellite providers can share a single lifecycle and cleanup policy

---

## Related Documents

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Voice Enrollment Lifecycle and State Machine](voice-enrollment-lifecycle-and-state-machine.md)
- [Voice Enrollment Storage, Cleanup, and Retention Architecture](voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [Voice Enrollment Modernization Roadmap](voice-enrollment-modernization-roadmap.md)
