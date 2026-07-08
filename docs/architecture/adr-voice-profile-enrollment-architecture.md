# ADR: Voice Profile Enrollment Architecture

## Status

Accepted

Supersedes: implicit browser-centric enrollment behavior without standardized session manifest, cleanup gating, and startup reconciliation guarantees.

---

## Context

Concierge needs a voice profile enrollment architecture that is privacy-first, deterministic, and local-first while supporting both browser and satellite capture providers.

The platform requires:

- explicit opt-in enrollment
- external-storage-only temporary recording handling
- strict lifecycle control and cleanup
- provider parity
- clear supported-now versus future boundaries

---

## Decision

We will:

- keep browser microphone enrollment as the preferred path
- support satellite enrollment as an alternate capability-probed provider
- keep the existing enrollment engine as the sole authority for validation, quality analysis, embedding generation, and profile persistence
- require external storage for all raw enrollment recordings
- treat recordings as temporary artifacts with zero default retention
- require managed sessions with session manifests for deterministic recovery and cleanup
- require terminal-state cleanup gating and idempotent cleanup behavior
- require startup reconciliation and orphan cleanup
- use diagnostics allowlist output and proactive repairs

---

## Consequences

### Positive consequences

- stronger privacy guarantees for raw enrollment audio
- deterministic lifecycle behavior across providers
- self-healing startup behavior
- lower risk of storage drift and retained sensitive artifacts
- clear architectural extensibility boundaries

### Tradeoffs

- additional lifecycle and storage scaffolding before implementation
- stricter preflight gating may block enrollment when storage is unhealthy
- more explicit operational handling for cleanup and reconciliation

---

## Alternatives Considered

- browser-only enrollment with no satellite path
- permanent recording retention for troubleshooting
- storing raw recordings inside Home Assistant storage surfaces
- separate browser and satellite lifecycle systems
- treating voice identity as authentication
- default raw-audio diagnostics retention

---

## Rejected Alternatives

### Storing recordings permanently

Rejected because enrollment recordings are temporary processing artifacts and not durable records.

### Storing recordings inside Home Assistant storage

Rejected because this violates external-storage-only handling and increases sensitive retention exposure.

### Treating voice identity as authentication

Rejected because platform policy defines voice identity as personalization context only.

### Separate browser and satellite enrollment systems

Rejected because separate lifecycle rules would create policy drift and weaker guarantees.

### Retaining raw recordings for diagnostics by default

Rejected because default behavior must be privacy-first with zero raw-audio retention.

---

## References

- [Voice Profile Enrollment Architecture](voice-profile-enrollment-architecture.md)
- [Identity Governance Reference](identity-governance-reference.md)
- [Voice Identity Trust and Data Residency Policy](voice-identity-trust-and-data-residency-policy.md)
