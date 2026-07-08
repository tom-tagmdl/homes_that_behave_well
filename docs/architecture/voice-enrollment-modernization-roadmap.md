# Voice Enrollment Modernization Roadmap

## Purpose

This roadmap defines phased implementation sequencing for the approved voice enrollment architecture.

It is implementation planning, not implementation code.

---

## Phase 0: Architecture Scaffolding

### Objective

Establish architecture-aligned scaffolding for sessions, storage, cleanup, diagnostics, and repairs boundaries.

### Scope

- lifecycle scaffolding
- policy wiring points
- cross-document alignment with canonical architecture references

### Deliverables

- session lifecycle scaffolding
- storage provider scaffolding
- cleanup manager scaffolding
- diagnostics allowlist and repairs taxonomy definitions

### Risks

- under-scoped lifecycle boundaries
- drift between architecture and implementation seams

### Exit Criteria

- all architectural invariants have represented scaffolding points
- implementation can proceed without revisiting architectural decisions

---

## Phase 1: Session Manager

### Objective

Introduce deterministic session lifecycle ownership.

### Scope

- session creation and transition enforcement
- manifest synchronization
- terminal pending-cleanup gating

### Deliverables

- managed enrollment session lifecycle
- lifecycle transition policy enforcement

### Risks

- legacy paths bypassing session manager

### Exit Criteria

- all enrollment paths are session-tracked and state-machine governed

---

## Phase 2: Storage Provider

### Objective

Enforce external-storage-only temporary artifact handling.

### Scope

- mounted path storage provider
- preflight readiness checks
- session-scoped artifact writes

### Deliverables

- provider abstraction
- mandatory preflight storage validation

### Risks

- external storage environment variability

### Exit Criteria

- capture cannot start unless storage preflight succeeds

---

## Phase 3: Cleanup Manager

### Objective

Enforce mandatory and idempotent cleanup lifecycle.

### Scope

- success, cancel, failure, timeout cleanup
- startup reconciliation cleanup
- overlap-safe cleanup behavior

### Deliverables

- cleanup manager execution path
- idempotent cleanup guarantees

### Risks

- concurrency race conditions between cleanup triggers

### Exit Criteria

- no terminal outcome bypasses cleanup

---

## Phase 4: Browser Enrollment Migration

### Objective

Migrate existing browser flow to session-governed lifecycle without behavior regression.

### Scope

- backward-compatible browser UX
- session and cleanup parity adoption

### Deliverables

- browser provider integrated with session and cleanup managers

### Risks

- UX regressions in current browser enrollment behavior

### Exit Criteria

- browser behavior remains backward compatible and policy compliant

---

## Phase 5: Satellite Capture Provider

### Objective

Add capability-probed satellite provider path.

### Scope

- supported-now capability checks
- unsupported-path handling
- parity with browser lifecycle and cleanup policy

### Deliverables

- alternate satellite provider path where feasible
- clear unsupported path behavior where not feasible

### Risks

- environment-dependent capability differences

### Exit Criteria

- satellite path works only when genuinely supported and never weakens policy guarantees

---

## Phase 6: Repairs and Diagnostics

### Objective

Operationalize proactive remediation and sanitized observability.

### Scope

- repairs issue taxonomy
- diagnostics allowlist implementation
- user-safe operational messaging

### Deliverables

- actionable repairs
- privacy-safe diagnostics outputs

### Risks

- over-disclosure in diagnostics
- under-actionable repairs

### Exit Criteria

- diagnostics and repairs meet privacy and operational goals

---

## Phase 7: Hardening and Telemetry

### Objective

Improve resilience, reconciliation reliability, and lifecycle confidence.

### Scope

- startup recovery hardening
- cleanup overlap hardening
- lifecycle telemetry summaries

### Deliverables

- hardened lifecycle behavior under failure and restart conditions

### Risks

- edge-case race conditions under high churn

### Exit Criteria

- lifecycle and resilience test suites pass consistently

---

## Related Documents

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Implementation Verification Checklist](implementation-verification-checklist.md)
