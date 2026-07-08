# Voice Enrollment Phase 0 Execution Package

## Purpose

This package defines implementation governance for Concierge Phase 0.

It is planning and execution guidance only.

It does not include production implementation code.

---

## Phase 0 Objective

Introduce architecture scaffolding without changing end-user behavior.

Phase 0 boundaries:

- browser enrollment workflow must remain functionally unchanged
- no satellite enrollment implementation yet
- no runtime recognition changes
- no profile generation logic changes
- no user-visible workflow redesign
- no persistent raw recording storage in Home Assistant surfaces

---

## Phase 0 Execution Tracker

### P0-01 Architecture constants and scaffolding

- [ ] Status: not started

Description:

Introduce lifecycle, manifest, and repairs constants.

Purpose:

Prevent state naming drift and ad-hoc issue keys.

Files affected:

- custom_components/concierge/const.py

Dependencies:

- approved HTBW voice enrollment architecture documents

Entry criteria:

- architecture package is accepted and committed

Exit criteria:

- constants exist for lifecycle states, cleanup outcomes, repairs issue ids, manifest schema version

Validation criteria:

- no runtime behavior changes
- imports compile cleanly

Test requirements:

- constants presence checks
- no regression in existing import paths

Risk level:

- low

### P0-02 EnrollmentSession foundation

- [ ] Status: not started

Description:

Add session model scaffolding and transition helper surface.

Purpose:

Introduce deterministic session ownership.

Files affected:

- custom_components/concierge/models.py
- custom_components/concierge/storage.py
- custom_components/concierge/services.py

New files required:

- custom_components/concierge/enrollment_session.py

Dependencies:

- P0-01

Entry criteria:

- lifecycle constants are available

Exit criteria:

- session create, load, and update scaffolding is available

Validation criteria:

- state names align with lifecycle architecture document

Test requirements:

- session lifecycle and transition tests

Risk level:

- medium

### P0-03 EnrollmentStorageProvider abstraction

- [ ] Status: not started

Description:

Introduce storage provider interface for temporary enrollment artifacts.

Purpose:

Enforce external-storage-only architecture boundary.

Files affected:

- custom_components/concierge/panel.py
- custom_components/concierge/services.py
- custom_components/concierge/const.py

New files required:

- custom_components/concierge/enrollment_storage.py

Dependencies:

- P0-01

Entry criteria:

- constants and baseline upload behavior are verified

Exit criteria:

- provider contract exists and current browser path remains behaviorally unchanged

Validation criteria:

- no raw audio moved into Home Assistant persistent storage surfaces

Test requirements:

- provider contract tests
- path-bounding tests

Risk level:

- medium

### P0-04 MountedPathEnrollmentStorageProvider contract foundation

- [ ] Status: not started

Description:

Define mounted-path provider readiness and session artifact operations.

Purpose:

Anchor current attached storage behavior behind policy-compliant contract.

Files affected:

- custom_components/concierge/enrollment_storage.py
- custom_components/concierge/panel.py

Dependencies:

- P0-03

Entry criteria:

- storage provider abstraction is present

Exit criteria:

- readiness, write, list, and delete contract surfaces are available

Validation criteria:

- operations are bounded under voice_enrollment/active/session_<id>

Test requirements:

- readiness fail cases
- bounded-path enforcement tests

Risk level:

- medium

### P0-05 EnrollmentCleanupManager foundation

- [ ] Status: not started

Description:

Add cleanup manager scaffolding with idempotent behavior.

Purpose:

Enable mandatory cleanup architecture without lifecycle bypass.

Files affected:

- custom_components/concierge/services.py
- custom_components/concierge/storage.py

New files required:

- custom_components/concierge/enrollment_cleanup.py

Dependencies:

- P0-02
- P0-03
- P0-04

Entry criteria:

- session and storage foundations are available

Exit criteria:

- repeated cleanup calls converge safely to clean state

Validation criteria:

- missing files/folders/manifests do not produce false cleanup failure

Test requirements:

- idempotence tests
- missing-artifact tolerance tests

Risk level:

- high

### P0-06 Session manifest lifecycle foundation

- [ ] Status: not started

Description:

Create, update, and delete session.json during session lifecycle.

Purpose:

Support deterministic restart recovery and orphan detection.

Files affected:

- custom_components/concierge/enrollment_session.py
- custom_components/concierge/enrollment_storage.py
- custom_components/concierge/services.py

Dependencies:

- P0-02
- P0-04
- P0-05

Entry criteria:

- session and storage foundations are available

Exit criteria:

- manifest exists only during active session and is removed during cleanup

Validation criteria:

- manifest fields remain non-sensitive and policy-compliant

Test requirements:

- manifest create/update/delete tests
- manifest field allowlist tests

Risk level:

- medium

### P0-07 External storage preflight validation foundation

- [ ] Status: not started

Description:

Add fail-fast storage validation before enrollment capture begins.

Purpose:

Enforce external storage dependency and prevent partial artifact creation.

Files affected:

- custom_components/concierge/services.py
- custom_components/concierge/panel.py
- custom_components/concierge/config_flow.py

Dependencies:

- P0-04

Entry criteria:

- provider readiness contract is available

Exit criteria:

- capture is blocked when storage is missing, unavailable, not writable, misconfigured, or permission denied

Validation criteria:

- no partial sample artifacts created when preflight fails

Test requirements:

- missing storage preflight tests
- permission denied preflight tests

Risk level:

- high

### P0-08 Startup orphan reconciliation foundation

- [ ] Status: not started

Description:

Add startup scan and reconciliation trigger for abandoned session folders.

Purpose:

Provide self-healing restart behavior.

Files affected:

- custom_components/concierge/__init__.py
- custom_components/concierge/coordinator.py
- custom_components/concierge/enrollment_cleanup.py

Dependencies:

- P0-05
- P0-06

Entry criteria:

- cleanup and manifest lifecycle foundations are in place

Exit criteria:

- startup can detect and reconcile orphaned sessions

Validation criteria:

- folders missing valid manifests are treated as orphaned and reconciled safely

Test requirements:

- startup orphan detection tests
- orphan cleanup success and failure tests

Risk level:

- high

### P0-09 Repairs framework foundation

- [ ] Status: not started

Description:

Add centralized repairs scaffolding for enrollment storage and cleanup failures.

Purpose:

Ensure proactive and actionable remediation.

Files affected:

- custom_components/concierge/services.py
- custom_components/concierge/__init__.py
- custom_components/concierge/const.py

New files required:

- custom_components/concierge/repairs.py

Dependencies:

- P0-01
- P0-05
- P0-07
- P0-08

Entry criteria:

- failure classes are mapped to architecture-approved issue types

Exit criteria:

- repairs are generated with sanitized details for policy-approved failure classes

Validation criteria:

- repairs payloads do not expose sensitive paths or audio detail

Test requirements:

- repairs issue key mapping tests
- repairs payload sanitization tests

Risk level:

- medium

### P0-10 Diagnostics allowlist foundation and test completion

- [ ] Status: not started

Description:

Switch diagnostics to allowlist output and complete Phase 0 protection tests.

Purpose:

Prevent privacy regressions and architecture drift.

Files affected:

- custom_components/concierge/diagnostics.py
- tests/test_diagnostics.py
- tests/test_services.py
- tests/test_init.py
- tests/test_panel.py
- tests/test_config_flow.py

New files recommended:

- tests/test_enrollment_cleanup.py
- tests/test_enrollment_storage.py

Dependencies:

- all prior Phase 0 items

Entry criteria:

- session, storage, cleanup, preflight, and reconciliation foundations are in place

Exit criteria:

- diagnostics output is policy-safe and all required Phase 0 protection tests pass

Validation criteria:

- diagnostics include only approved operational fields

Test requirements:

- non-disclosure tests for paths/audio/embeddings/profile internals

Risk level:

- high

---

## Dependency Graph

Directed dependencies:

1. Constants -> Session foundation
2. Constants -> Storage abstraction
3. Session + Storage -> Cleanup foundation
4. Session + Storage -> Manifest lifecycle
5. Storage -> Preflight validation
6. Cleanup + Manifest lifecycle -> Startup reconciliation
7. Preflight + Cleanup + Startup reconciliation -> Repairs foundation
8. Session + Cleanup + Repairs -> Diagnostics allowlist
9. All items -> Phase 0 test completion

Independent early work:

- constants
- session scaffolding
- storage abstraction interface

Must not be implemented before prerequisites:

- startup reconciliation before cleanup and manifest lifecycle
- preflight enforcement before storage readiness contract
- diagnostics allowlist finalization before lifecycle summaries are available

---

## Test-First Strategy

### Tests that should exist before implementation proceeds

- browser enrollment compatibility baseline
- storage preflight failure baseline
- diagnostics non-disclosure baseline

### Required protection tests

1. Browser enrollment compatibility

Protects:

- backward compatibility of current user flow

Failure condition:

- user-visible behavior changes in browser enrollment workflow

2. Cleanup idempotence

Protects:

- overlap safety for cancel, timeout, failure, and restart cleanup paths

Failure condition:

- repeated cleanup calls produce hard failures or leave artifacts

3. Diagnostics non-disclosure

Protects:

- privacy policy and telemetry boundaries

Failure condition:

- diagnostics include raw paths, raw audio, embeddings, or profile internals

4. Storage preflight failures

Protects:

- fail-fast policy and no partial file creation

Failure condition:

- capture starts when storage is unavailable or unwritable

5. Orphan cleanup

Protects:

- startup self-healing behavior

Failure condition:

- orphaned session folders remain unreconciled

6. Session manifest lifecycle

Protects:

- deterministic cleanup and restart recovery

Failure condition:

- manifest missing during active session or retained after cleanup

---

## Implementation Review Checklist (Merge Gate)

### Architecture compliance

- [ ] Change maps to authoritative HTBW voice enrollment documents.
- [ ] Scope remains within Phase 0 boundaries.
- [ ] Lifecycle assumptions align with approved state machine.

### Policy and privacy compliance

- [ ] External storage remains mandatory for raw enrollment recordings.
- [ ] Default retention for raw recordings remains zero.
- [ ] No new persistent raw recording storage in Home Assistant surfaces.
- [ ] Guest protections and explicit consent boundaries are preserved.

### Cleanup compliance

- [ ] Terminal outcomes route through cleanup scaffolding.
- [ ] Cleanup behavior is idempotent by design.
- [ ] Startup reconciliation uses cleanup manager path.

### Diagnostics and repairs compliance

- [ ] Diagnostics use allowlist output only.
- [ ] Diagnostics do not expose raw paths, raw audio, embeddings, or profile internals.
- [ ] Repairs payloads are actionable and sanitized.

### Backward compatibility

- [ ] Browser enrollment behavior remains unchanged.
- [ ] Runtime recognition behavior remains unchanged.
- [ ] Profile generation behavior remains unchanged.
- [ ] No satellite provider implementation is introduced in Phase 0.

### Auditable merge evidence

- [ ] Required tests added and passing.
- [ ] PR scope statement and risk statement provided.
- [ ] Architecture authority references included in PR description.

---

## Architecture-to-Code Mapping

| Architecture Document | Implementation Components |
|---|---|
| voice-profile-enrollment-architecture.md | session scaffolding, provider seams, cleanup gating surfaces |
| adr-voice-profile-enrollment-architecture.md | scope boundaries and rejected-alternative enforcement |
| voice-enrollment-domain-model.md | enrollment_session, enrollment_storage, enrollment_cleanup, repairs ownership boundaries |
| voice-enrollment-privacy-and-data-handling-policy.md | preflight fail-fast checks, diagnostics restrictions, repairs sanitization |
| voice-enrollment-lifecycle-and-state-machine.md | state constants, transition helpers, terminal pending-cleanup paths |
| voice-enrollment-storage-cleanup-and-retention-architecture.md | storage provider, cleanup manager, manifest lifecycle, startup reconciliation |
| voice-profile-lifecycle-management.md | guardrails that preserve profile lifecycle boundaries and prevent recording lifecycle coupling |
| temporary-artifact-lifecycle-pattern.md | create-track-process-commit-cleanup-verify implementation pattern |
| implementation-verification-checklist.md | pre-coding and phase-exit verification gates |
| voice-enrollment-modernization-roadmap.md | phase sequencing and implementation order |

---

## Future Phase Preview

### Phase 1

Move from scaffolding to enforced session orchestration across enrollment terminal paths while preserving browser behavior.

### Phase 2

Mature storage provider enforcement and preflight policy coverage with operational hardening.

### Phase 3

Complete cleanup and reconciliation hardening, then strengthen repairs and diagnostics operational readiness.

---

## Related Documents

- [voice-profile-enrollment-architecture.md](voice-profile-enrollment-architecture.md)
- [voice-enrollment-lifecycle-and-state-machine.md](voice-enrollment-lifecycle-and-state-machine.md)
- [voice-enrollment-storage-cleanup-and-retention-architecture.md](voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [implementation-verification-checklist.md](implementation-verification-checklist.md)
- [voice-enrollment-modernization-roadmap.md](voice-enrollment-modernization-roadmap.md)
