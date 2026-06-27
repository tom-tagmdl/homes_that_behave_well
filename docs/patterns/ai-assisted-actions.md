# AI Assisted Actions

## Purpose

AI Assisted Actions define how artificial intelligence interacts with the system.

This ensures that AI enhances the system without compromising:

- determinism
- safety
- explainability
- trust

---

## Core Principle

AI may suggest.

The system decides.

---

## Roles and Boundaries

AI is not part of the system of record.

AI operates as an external advisor that provides:

- recommendations
- summaries
- reasoning

AI does not:

- make final decisions
- modify system state directly
- bypass validation or services

---

## Allowed AI Capabilities

AI may be used to:

- suggest environment requirements for assets
- generate advisory recommendations
- summarize system state
- explain relationships between conditions and risk

All AI output must be treated as untrusted input until validated.

---

## Prohibited AI Behavior

AI must never:

- write directly to the store
- call internal functions without a service boundary
- introduce values outside defined limits
- produce outputs that cannot be explained

Any attempt to bypass system constraints must be rejected.

---

## Standard Flow

All AI-assisted actions must follow this pattern:

1. Gather system context
   - asset data
   - room environment
   - configuration
   - current conditions

2. Generate AI recommendation
   - structured output
   - clear reasoning

3. Validate recommendation
   - ensure correct schema
   - enforce bounds
   - confirm required fields

4. Present recommendation
   - user-facing explanation
   - optional confirmation

5. Apply via service (optional)
   - explicit approval
   - validated service call
   - store update
   - coordinator refresh

---

## Validation Requirements

All AI output must be validated before use.

Validation must ensure:

- values are within safe ranges
- data matches expected structure
- required fields are present
- no unsupported fields are introduced

Invalid AI output must:

- be rejected completely
- never partially applied
- be logged if necessary

---

## User Interaction Model

AI-assisted actions should follow a guided interaction.

Example:

- System provides recommendation
- User reviews recommendation
- User confirms action
- System applies change via service

Direct automatic application is not allowed.

---

## Service Enforcement

All state changes resulting from AI must flow through services.

Correct pattern:

AI recommendation -> validated service call -> store update -> coordinator refresh

No exceptions are allowed.

---

## Explainability Requirement

Every AI-assisted action must include:

- what is being suggested
- why the suggestion was made
- what data was used

The system must be able to answer:

- why was this recommended
- how was it derived

If explanation is not possible, the action must not proceed.

---

## Context Usage

AI must use system-provided context only.

Context may include:

- asset metadata
- room environment snapshot
- configuration data
- historical patterns

AI must not:

- invent context
- assume missing data
- override confidence indicators

---

## Confidence Awareness

AI must respect system confidence levels.

If confidence is:

- GOOD: full recommendations allowed
- PARTIAL: limited recommendations
- DEGRADED: caution required
- STALE: recommendations should be suppressed

AI must adapt behavior based on confidence.

---

## Safety Constraints

AI-generated values must:

- fall within system-defined safe limits
- respect domain constraints
- avoid extreme or unsafe conditions

Examples:

- humidity must remain within safe biological limits
- temperature must remain within operational ranges

Unsafe suggestions must be rejected.

---

## Logging and Audit

AI-assisted actions should be traceable.

The system should record:

- source of recommendation (AI)
- timestamp
- input context
- generated output
- whether it was applied

This ensures:

- auditability
- debugging capability
- system trust

---

## Integration Responsibilities

### Asset Intelligence

Must:

- handle validation of AI output
- own all state changes
- enforce safety rules
- persist results and audit data

---

### Concierge

Must:

- initiate AI-assisted workflows
- present results to the user
- manage interaction flow

Must not:

- validate business rules
- modify system state directly

---

## Failure Handling

If AI fails or returns invalid output:

- the system must stop the action
- no state changes should occur
- the user may be informed of failure

The system must never:

- apply incomplete recommendations
- silently ignore validation failures
- produce undefined behavior

---

## Final Principle

AI enhances intelligence.

It does not control the system.

If a capability depends on AI:

- the system must still behave correctly without it
- the result must remain deterministic after validation