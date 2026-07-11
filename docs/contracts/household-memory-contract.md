# Household Memory Contract

## Purpose

This contract defines the authoritative boundary for household memory eligibility governance, visibility governance, explanation governance, privacy boundaries, retention governance, and retrieval boundaries.

This contract governs:

- memory eligibility
- memory visibility
- memory explainability
- memory privacy boundaries
- memory retention governance
- memory attribution requirements
- memory retrieval boundaries
- memory relationship to event history and provenance

This contract does not define:

- storage implementation
- indexing implementation
- query implementation
- retrieval engine implementation

---

## Household Memory Definition

Household Memory is a governed representation of meaningful household history derived from authoritative event history and provenance sources.

Household Memory is not:

- event history
- provenance
- storage implementation
- execution authority

Household Memory consumes history.

Household Memory consumes provenance.

Household Memory does not replace either.

---

## Memory Ownership Matrix

| Concern | Owner | Household Memory Relationship |
|---|---|---|
| event history | Event History authority | memory consumes historical events and chronology; event history remains authoritative |
| provenance | Provenance authority | memory consumes attribution and lineage; provenance remains authoritative |
| identity | Voice Identity | memory consumes identity context and confidence context without ownership transfer |
| room truth | Foundation | memory consumes room context for visibility and explanation scope |
| occupancy | Foundation | memory consumes occupancy context for visibility and relevance gates |
| continuity | Person Continuity governance | memory may consume continuity context and does not redefine continuity authority |
| affinity | Person Affinity governance | memory may consume affinity context and does not redefine affinity authority |
| household memory | Household Memory governance under this contract | owns memory eligibility, memory visibility, memory explanation, and retrieval boundaries |
| explainability | HTBW governance policy applied by memory consumers | memory must provide machine-readable and human-readable explainability outputs |
| execution | Service contracts and orchestration paths | memory informs explainability and retrieval boundaries only; memory does not execute |

Required ownership alignment:

- Event History remains authoritative for events.
- Provenance remains authoritative for attribution and lineage.
- Household Memory governs memory visibility and interpretation under this contract.

---

## Event History Relationship

Household Memory consumes Event History.

Event History remains authoritative.

Household Memory may not redefine events.

Household Memory may not rewrite history.

---

## Provenance Relationship

Household Memory consumes Provenance.

Provenance remains authoritative.

Memory explanations must reference provenance.

Household Memory does not generate alternate attribution.

This relationship aligns with ADR-011.

---

## Identity-Linked Memory

Identity-linked memory governs:

- person-related memory context
- identity-linked memory visibility
- identity confidence impacts on visibility and explanation

Required statements:

- identity authority remains with Voice Identity
- Household Memory consumes identity context
- Household Memory does not own identity

---

## Room-Linked Memory

Room-linked memory governs:

- room-related memory context
- room history context
- room-associated memory visibility

Required statements:

- Foundation remains authoritative for room truth
- Household Memory consumes room context

---

## Who Did This

This section governs attribution questions such as:

- who performed an action
- who initiated an event
- who changed a state

Required statements:

- answers derive from provenance
- memory does not invent attribution

---

## What Happened While I Was Away

This section governs:

- absence summaries
- historical summaries
- activity summaries

Required statements:

- summaries derive from event history and provenance
- memory does not create alternate historical truth

---

## Why Did This Happen

This section governs:

- explanation requests
- causality requests
- rationale requests

Required statements:

- explanations derive from provenance
- memory consumes explanations
- memory does not create alternate provenance

---

## Memory Categories

### 1. Identity-Linked Memory

Governance scope:

- person-associated memory context
- confidence-gated person memory visibility

### 2. Room-Linked Memory

Governance scope:

- room-associated memory context
- room-scoped memory visibility

### 3. Occupancy-Linked Memory

Governance scope:

- occupancy-informed memory relevance
- occupancy-informed memory visibility gates

### 4. Experience Memory

Governance scope:

- prior experience context memory surfaces
- experience history references grounded in event and provenance authority

### 5. Activity Memory

Governance scope:

- household activity history summaries
- action and state transition memory references

### 6. Notification Memory

Governance scope:

- notification history memory references
- notification attribution and delivery context visibility

### 7. Household Status Memory

Governance scope:

- state-of-home historical context summaries
- household status memory visibility and explainability boundaries

All categories define governance boundaries only and do not define implementation.

---

## Privacy Requirements

Memory privacy governance must define:

- visibility constraints
- privacy controls
- disclosure boundaries
- access expectations

Required statement:

- memory visibility must respect governance constraints

---

## Retention Requirements

Memory retention governance must define:

- retention eligibility
- expiration eligibility
- purge eligibility
- redaction eligibility

This contract does not define storage implementation.

---

## Guest Behavior

Guest behavior governance must define:

- guest memory visibility
- guest memory restrictions
- guest-safe defaults

Required statement:

- guests must not receive private household memory

---

## Unknown Identity Behavior

Unknown identity behavior governance must define:

- unknown-user memory visibility
- low-confidence visibility
- restricted visibility

Required statement:

- unknown identities may not inherit private memory context

---

## Human-Readable Explanation Requirements

Human-readable memory explanations must support:

- What happened?
- Who did this?
- Why did this happen?
- What happened while I was away?

Human explanations must remain understandable.

---

## Machine-Readable Explanation Requirements

Machine-readable memory explanations must support:

- event identifiers
- provenance identifiers
- attribution lineage
- timestamps
- confidence metadata
- room context

Machine explanations must remain traceable.

---

## Non-Rights

Household Memory does not own:

- event history
- provenance
- identity
- room truth
- occupancy truth
- execution

---

## Determinism Requirements

Determinism requirements:

- same event history -> same memory result
- same provenance -> same explanation result
- same visibility policy -> same memory visibility

Prohibited behavior:

- hidden memory invention
- hidden attribution invention
- hidden historical modification

---

## Memory / Provenance Relationship Map

Household Memory <-> Event History

- memory consumes event records, chronology, and historical context from Event History authority

Household Memory <-> Provenance

- memory consumes attribution and lineage context from Provenance authority

Household Memory <-> Identity

- memory consumes identity context and confidence boundaries from Voice Identity authority

Household Memory <-> Room Truth

- memory consumes room scope context from Foundation room truth authority

Household Memory <-> Occupancy

- memory consumes occupancy context and confidence boundaries from Foundation occupancy authority

Household Memory <-> Coordinator V2

- Coordinator V2 consumes memory outputs for explainability and context-aware interaction behavior

---

## Boundary Review

This contract preserves explicit separation between:

- Event History
- Provenance
- Household Memory
- Continuity
- Affinity
- Identity

Separation rules:

- Event History remains authoritative for events and chronology
- Provenance remains authoritative for attribution and lineage
- Household Memory governs memory eligibility, visibility, explanation, and retrieval boundaries
- Continuity and Affinity remain separate governance domains and are consumed context only
- Identity remains authoritative in Voice Identity

Semantic duplication across these domains is prohibited.

---

## Deferred Closure Note (C11 Dependency)

V2-C8 implementation may complete, but issue closure remains blocked until V2-C11 is completed and validated.

This dependency is mandatory and must not be removed.

---

## Contract Coverage Review

What remains in other authority artifacts:

- event ownership remains with Event History authority
- attribution and lineage ownership remain with Provenance authority
- identity ownership remains with Voice Identity authority
- room and occupancy truth ownership remain with Foundation authority

What this contract now governs:

- memory eligibility governance
- memory visibility governance
- memory explanation governance
- memory retrieval governance boundaries
- memory privacy and retention governance boundaries

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-008 Personalization Governance Boundaries
- ADR-009 Household Memory Governance Boundaries
- ADR-010 Household Productivity Experience Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract consumes governance and does not redefine governance authority.

---

## Final Principle

Household Memory provides governed memory visibility and explainability derived from authoritative event history and provenance.

Household Memory must never duplicate event ownership, provenance ownership, or source-of-record truth authority.