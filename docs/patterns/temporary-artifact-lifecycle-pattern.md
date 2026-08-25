# Temporary Artifact Lifecycle Pattern

> **Document status: Active — subordinate to the HTBW canonical architecture.**
> Canonical authority: [../architecture/framework.md](../architecture/framework.md) and
> [../models/glossary.md](../models/glossary.md).
> Where this document conflicts with canonical authority, canonical authority prevails.

## Purpose

This reusable Homes That Behave Well pattern defines how temporary artifacts should be managed across platform components.

It formalizes the sequence:

Create -> Track -> Process -> Commit -> Cleanup -> Verify

---

## Pattern Intent

Temporary artifacts should exist only as long as necessary to produce intended durable outputs.

Default behavior must prioritize:

- deterministic cleanup
- minimal retention
- recovery-safe reconciliation
- diagnostics-safe observability

---

## Pattern Flow

### 1. Create

- initialize bounded artifact scope
- assign artifact or session identity
- validate preconditions before generation

### 2. Track

- maintain explicit state and metadata
- track ownership and lifecycle transitions
- record enough operational metadata to support recovery

### 3. Process

- perform processing within bounded lifecycle scope
- avoid persistence expansion beyond required temporary context

### 4. Commit

- persist only intended durable outputs
- ensure commit is explicit and auditable

### 5. Cleanup

- remove temporary artifacts
- release runtime resources
- enforce idempotent cleanup behavior

### 6. Verify

- verify clean terminal state
- reconcile after restart and remove orphans
- raise actionable sanitized repairs for unresolved issues

---

## Pattern Invariants

- temporary artifacts are not default durable records
- terminal outcomes are cleanup-gated
- cleanup is idempotent
- startup reconciliation is required where temporary artifacts may remain after interruption
- diagnostics use allowlist model

---

## Application Examples

This pattern applies to:

- voice enrollment
- temporary media upload processing
- AI-generated intermediate assets
- image processing pipelines
- document transformation staging
- temporary caching workflows

---

## Voice Enrollment Mapping

Voice enrollment is a direct instance of this pattern:

- Create: start EnrollmentSession
- Track: maintain session manifest and state
- Process: validate and build profile
- Commit: persist profile outputs
- Cleanup: delete temporary recordings and manifest
- Verify: startup orphan reconciliation and cleanup

---

## Observed refinements from legacy implementations

**Non-normative.** Harvested from the Concierge, Voice Identity and Asset Intelligence
documentation sets. These sharpen the invariants above without adding to them, and none
of the values named is canonical.

**Idempotent is not the same as complete.** One implementation distinguishes a cleanup
that removed artifacts from a cleanup that found nothing to remove. Both are successful
and neither is an error, but collapsing them loses the ability to tell an interrupted
session from a session that never wrote anything.

**Reconciliation needs a taxonomy, not a scan.** Rather than looking for stray files, the
same implementation enumerates the distinct ways the pattern can be left inconsistent — a
working directory with no session record, a session record with no manifest, a manifest
with no artifacts, and artifacts under an unreadable manifest — and handles each
explicitly. Naming the failure modes is what makes reconciliation reviewable.

**Cleanup that could not run must say so.** Where the storage dependency is unavailable,
cleanup is reported as unresolved and retried when the dependency returns. It is never
reported as successful, which is the same requirement the artifact-lifecycle decision
places on parent removal.

**Failure detail is sanitised at the boundary.** Diagnostics receive a governed code
rather than the underlying error text, consistent with the allowlist invariant above and
with the rule that artifact internals and storage paths are never exposed.

**A temporary artifact may carry its own expiry.** One implementation gives a generated
export a short, unconditional lifetime, so the artifact removes itself even if no
subsequent step runs. Where the consumer is immediate, self-expiry is a stronger guarantee
than a cleanup step that depends on a later stage completing.

**Bound the payload as well as the count.** Another implementation caps individual field
length, collection size and nesting depth when writing bounded history, summarising heavy
nested structures rather than embedding them. A count-only bound still permits an
unbounded record.

---

## Related Documents

- [Voice Enrollment Storage, Cleanup, and Retention Architecture](../architecture/voice-enrollment-storage-cleanup-and-retention-architecture.md)
- [Voice Enrollment Lifecycle and State Machine](../architecture/voice-enrollment-lifecycle-and-state-machine.md)
