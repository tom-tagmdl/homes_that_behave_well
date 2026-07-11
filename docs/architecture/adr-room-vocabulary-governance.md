# ADR: Room Vocabulary Governance Boundaries

## ADR Number

ADR-005

## Status

Accepted.

## Context

Room Vocabulary is a governed architectural concern, not an implementation detail.

Room Vocabulary is required for:

- deterministic room reference resolution
- human-friendly room interaction
- merged-room consistency
- explainable room selection behavior
- capability-scoping support

Room identity and room vocabulary are distinct concerns.

- Room identity is foundational truth owned by Foundation.
- Room vocabulary is a governed resolution mechanism that references room truth.

Coordinator V2 consumes governed vocabulary outputs and may not define vocabulary governance independently.

## Decision

HTBW architecture establishes Room Vocabulary governance as authoritative for downstream contracts, models, and implementation behavior.

Coordinator V2 is a consumer of governed vocabulary outputs.

Coordinator V2 does not own vocabulary governance, room identity, room truth, or source-of-record responsibilities.

### Room Vocabulary Definition

Room Vocabulary includes:

- canonical room names
- aliases
- human-friendly references
- conversational references
- merged-room references
- scoped room references

Room Vocabulary provides deterministic reference resolution.

Room Vocabulary does not own room truth.

### Room Vocabulary Governance Table

| Governance Element | Definition | Authoritative Owner | Coordinator Role |
|---|---|---|---|
| Canonical room name | primary governed label for a room identity | HTBW architecture governance referencing Foundation room truth | Consumes |
| Allowed aliases | approved alternate terms mapped to canonical room identity | HTBW architecture governance | Consumes |
| Managed vocabulary lifecycle | create, update, deprecate, retire vocabulary terms under governance | HTBW architecture governance | Consumes |
| Vocabulary change governance | review and approval requirements for vocabulary updates | HTBW architecture governance | Consumes |
| Conflict management governance | deterministic conflict detection and resolution policy | HTBW architecture governance | Consumes |
| Merged-room vocabulary governance | naming and alias rules for governed merged-room contexts | HTBW architecture governance | Consumes |

### Room Vocabulary Uniqueness Policy

Room vocabulary must remain deterministic under explicit uniqueness rules.

| Policy Area | Requirement | Prohibited Ambiguity |
|---|---|---|
| Globally unique vocabulary | canonical room names must be globally unique in a household scope | duplicate canonical names |
| Context-scoped vocabulary | scoped references must declare deterministic scope boundaries | unresolved cross-scope references |
| Alias uniqueness | alias terms must either be globally unique or governed by explicit scope qualification | same alias with no deterministic tie-breaker |
| Conversational shorthand | shorthand terms must resolve via deterministic normalization and scope rules | ambiguous shorthand with no clarification path |

Conflict resolution behavior is deterministic:

- reject non-governed duplicate canonical names
- require explicit scope qualification when alias overlap is governed but non-unique globally
- issue deterministic clarification when ambiguity remains after scope application

### Merged-Room Vocabulary Governance Table

| Merged-Room Concern | Governance Rule | Deterministic Resolution Priority |
|---|---|---|
| Merged-room naming | merged-room names are explicitly governed definitions, not inferred runtime constructs | explicit merged-room name match first |
| Merged-room aliases | aliases are governed and tied to explicit merged-room identity | alias match under merged-room scope second |
| Inheritance behavior | merged-room may inherit member-room vocabulary only through governed allowlist rules | governed inherited term resolution third |
| Overlap handling | overlap across room and merged-room terms requires deterministic precedence and clarification policy | deterministic clarification when tie remains |

Deterministic overlap handling:

- room vocabulary overlap is resolved by governance-defined precedence rules
- alias overlap is resolved by scope qualification and precedence rules
- merged-room overlap is resolved by explicit merged-room governance definitions

Coordinator V2 must not invent merged-room semantics.

### Vocabulary-To-Capability Boundaries

Vocabulary may assist routing.

Vocabulary does not define capabilities.

Capabilities remain governed independently through contracts and capability sources.

Explicit prohibitions:

- no capability ownership through vocabulary
- no vocabulary-driven governance redefinition
- no runtime invention of capability hierarchy through vocabulary

### Determinism Requirements

Room Vocabulary behavior must be deterministic:

- same vocabulary input produces same resolution result
- conflict handling is deterministic
- merged-room handling is deterministic
- fallback behavior is deterministic and bounded

Coordinator and downstream consumers must receive predictable outcomes for governed inputs.

### Explainability Requirements

Explainability is an architectural requirement.

Machine explainability outputs must include:

- matched term
- matched alias
- resolution path
- conflict outcome
- merged-room reasoning
- timestamps

Human explainability outputs must include:

- why a room was selected
- why an alias matched
- why a merged room was chosen
- why clarification was requested

### Conflict Handling Requirements

Conflict handling must be deterministic and explainable for:

- duplicate aliases
- overlapping names
- merged-room conflicts
- stale room definitions
- deleted room references
- ambiguous conversational references

Conflict behavior requirements:

- apply deterministic precedence rules first
- fall back to deterministic clarification when required
- emit explainability outputs for both machine and human paths

### Source-Of-Record Boundaries

Foundation owns room truth.

Room Vocabulary references room truth.

Coordinator consumes vocabulary outputs.

Coordinator does not own room identity.

Coordinator does not own room truth.

Vocabulary does not become a source of record.

## Consequences

Positive outcomes:

- establishes authoritative governance for room vocabulary across contracts, models, and implementation
- prevents ownership drift from HTBW governance into runtime orchestration
- improves deterministic and explainable room resolution behavior
- strengthens merged-room consistency and conflict handling discipline

Tradeoffs:

- requires stricter governance controls for vocabulary lifecycle changes
- requires deterministic clarification behavior in ambiguous conversational cases

## Rejected Alternatives

### 1. Coordinator-owned vocabulary governance

Rejected because Coordinator is a consumer and orchestrator, not a governance authority.

### 2. Vocabulary as room truth authority

Rejected because Foundation owns room truth and vocabulary only references that truth.

### 3. Runtime-generated vocabulary with no governance

Rejected because unguided runtime generation causes non-deterministic behavior and governance drift.

### 4. Vocabulary-driven capability ownership

Rejected because capability ownership is governed independently and cannot be redefined by vocabulary.

### 5. Non-deterministic conflict resolution

Rejected because household predictability requires deterministic and explainable conflict handling.

### 6. Implicit merged-room creation

Rejected because merged-room semantics must be explicitly governed and not inferred at runtime.
