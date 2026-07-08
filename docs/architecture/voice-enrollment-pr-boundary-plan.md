# Voice Enrollment Phase 0 PR Boundary Plan

## Purpose

This document defines review-safe pull request boundaries for Concierge Phase 0 implementation.

The plan enforces:

- small reviewable PRs
- no mixed concerns
- minimal regression risk
- backward-compatible browser enrollment behavior

---

## PR-1: Architecture Constants and Scaffolding

Scope:

- add lifecycle, cleanup, manifest, and repairs constants

Files affected:

- custom_components/concierge/const.py

Risks:

- low

Required tests:

- constants presence and import checks

Exit criteria:

- constants available for downstream PRs
- no behavior change

---

## PR-2: EnrollmentSession Foundation

Scope:

- add session scaffolding and transition helper surfaces

Files affected:

- custom_components/concierge/enrollment_session.py
- custom_components/concierge/models.py
- custom_components/concierge/storage.py

Risks:

- medium

Required tests:

- session lifecycle and transition validity tests

Exit criteria:

- session scaffolding available with no browser flow changes

---

## PR-3: Storage Provider Abstraction

Scope:

- add EnrollmentStorageProvider abstraction
- introduce mounted-path provider contract foundation

Files affected:

- custom_components/concierge/enrollment_storage.py
- custom_components/concierge/panel.py
- custom_components/concierge/services.py

Risks:

- medium

Required tests:

- provider contract tests
- bounded-path operation tests

Exit criteria:

- existing browser upload path remains behaviorally unchanged

---

## PR-4: Cleanup Manager Foundation

Scope:

- add EnrollmentCleanupManager scaffolding
- add idempotent cleanup semantics

Files affected:

- custom_components/concierge/enrollment_cleanup.py
- custom_components/concierge/services.py

Risks:

- high

Required tests:

- repeated cleanup idempotence tests
- missing-artifact tolerance tests

Exit criteria:

- cleanup converges safely without false failure on already-clean artifacts

---

## PR-5: Manifest Lifecycle

Scope:

- implement session manifest create/update/delete foundation

Files affected:

- custom_components/concierge/enrollment_session.py
- custom_components/concierge/enrollment_storage.py
- custom_components/concierge/services.py

Risks:

- medium

Required tests:

- manifest lifecycle tests
- manifest field allowlist tests

Exit criteria:

- manifest present during active session only and deleted by cleanup path

---

## PR-6: Preflight Validation

Scope:

- add external storage fail-fast checks before capture

Files affected:

- custom_components/concierge/services.py
- custom_components/concierge/panel.py
- custom_components/concierge/config_flow.py

Risks:

- high

Required tests:

- storage missing preflight failure test
- storage unwritable preflight failure test
- no partial artifact creation test

Exit criteria:

- enrollment capture blocked when storage health checks fail

---

## PR-7: Startup Reconciliation

Scope:

- add startup orphan detection and cleanup trigger foundation

Files affected:

- custom_components/concierge/__init__.py
- custom_components/concierge/coordinator.py
- custom_components/concierge/enrollment_cleanup.py

Risks:

- high

Required tests:

- startup orphan detection test
- orphan cleanup success and unresolved-failure paths

Exit criteria:

- startup can reconcile stale or orphaned active sessions safely

---

## PR-8: Repairs Framework

Scope:

- add repairs scaffolding and issue mappings for approved failure classes

Files affected:

- custom_components/concierge/repairs.py
- custom_components/concierge/services.py
- custom_components/concierge/const.py

Risks:

- medium

Required tests:

- issue key mapping tests
- sanitization tests for issue payloads

Exit criteria:

- repairs are actionable and sanitized for storage and cleanup failures

---

## PR-9: Diagnostics Allowlist

Scope:

- replace broad diagnostics output with policy-safe allowlist output

Files affected:

- custom_components/concierge/diagnostics.py
- tests/test_diagnostics.py

Risks:

- medium

Required tests:

- diagnostics non-disclosure tests
- allowlist snapshot tests

Exit criteria:

- diagnostics output excludes raw paths, raw audio, embeddings, and profile internals

---

## PR-10: Phase 0 Test Completion

Scope:

- complete and stabilize all Phase 0 protection tests

Files affected:

- tests/test_services.py
- tests/test_init.py
- tests/test_panel.py
- tests/test_config_flow.py
- tests/test_enrollment_cleanup.py
- tests/test_enrollment_storage.py

Risks:

- medium

Required tests:

- all protection tests defined in execution package

Exit criteria:

- architecture boundary tests pass
- backward compatibility and privacy invariants pass

---

## PR Boundary Enforcement Rules

- each PR should include one concern area only
- no PR should combine storage, cleanup, and diagnostics changes unless required by direct dependency
- browser behavior regression checks are mandatory in every PR touching enrollment paths
- no PR in Phase 0 may implement satellite capture behavior

---

## Related Documents

- [voice-enrollment-phase0-execution-package.md](voice-enrollment-phase0-execution-package.md)
- [voice-enrollment-modernization-roadmap.md](voice-enrollment-modernization-roadmap.md)
- [implementation-verification-checklist.md](implementation-verification-checklist.md)
