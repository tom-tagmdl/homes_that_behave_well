# ADR: Capability Projection Governance Boundaries

## ADR Number

ADR-006

## Status

Accepted.

## Context

Capability Projection is a mandatory architectural behavior for household interaction quality.

Users must be able to ask, deterministically and explainably:

- What can I do here?
- What can I do in this room?
- What can I do right now?
- What can you help me with?
- What can this device do?

Capability Projection is governed behavior, not runtime feature improvisation.

Coordinator V2 may assemble capability projections from governed sources.

Coordinator V2 may not define capability governance, create capabilities, or infer capability ownership.

## Decision

Capability Projection is defined as:

A governed representation of capabilities available within a specific execution context.

Capability Projection is not:

- capability ownership
- capability governance
- capability creation
- capability inference without contract authority

Capabilities remain governed by contracts and canonical models.

Projection is consumption.

Projection is not authority.

### Capability Projection Ownership Table

| Concern | Owner | Projection Role |
|---|---|---|
| capability definition | contracts and canonical model authority under HTBW governance | consumes definitions |
| capability governance | HTBW governance | consumes governed policy |
| capability availability | capability providers and runtime availability surfaces | consumes current availability |
| capability projection | Concierge Coordinator V2 runtime behavior | assembles and projects |
| experience projection | Concierge runtime orchestration under governed policy | projects experience-facing view |
| capability diagnostics | governed diagnostic surfaces by owning domains and Concierge orchestration metadata | consumes and presents explainable outcomes |
| capability visibility | governed policy and authorization boundaries | applies deterministic visibility filtering |

Ownership principles:

- HTBW owns governance.
- Contracts define capabilities.
- Coordinator consumes capabilities.
- Coordinator projects capabilities.
- Coordinator does not own capabilities.

### Projection Sources

Projection may consume:

- room context
- room vocabulary context
- person context
- identity confidence
- guest status
- occupancy
- presence
- experience context
- capability contracts
- runtime availability

Explicit prohibitions:

- hidden capability creation
- inferred capability ownership
- projection-created governance

### Person And Guest Filtering

Projection filtering must be deterministic and explainable for:

- household member
- enrolled person
- guest
- unknown person
- anonymous interaction

Filtering rules:

- projection uses governed visibility rules only
- projection does not rely on hidden authorization assumptions
- guest visibility must never use implicit privilege elevation
- unknown and anonymous interactions use bounded neutral visibility policies

### Unsupported Capability Handling

When a capability:

- exists but is unavailable
- exists but is inaccessible
- is not available in room context
- is not available for guest context
- is disabled
- has no execution path

Projection behavior must:

- explain the limitation
- not fabricate availability
- return deterministic outcomes

### Explainability Requirements

Explainability is mandatory.

Machine explainability outputs should include:

- capability identifier
- governing contract
- visibility decision
- projection reason
- eligibility factors
- timestamps

Human explainability outputs should allow Concierge to explain:

- why a capability appears
- why a capability does not appear
- why a capability is restricted
- why a guest cannot access something
- why a room-specific capability is unavailable

### Determinism Requirements

Projection determinism requirements:

- same governed inputs produce same projected capability set
- same visibility rules produce same output
- same context produces same projection
- hidden runtime inference is prohibited

Projection must be predictable and reproducible.

### Performance Requirements

Performance constraints for projection behavior:

- bounded runtime behavior
- efficient deterministic filtering
- deterministic refresh behavior
- explainability preservation under performance pressure

Performance optimizations must not alter projection correctness.

### Source-Of-Record Boundaries

Contracts remain authority for capabilities.

Models remain authority for capability structure.

Coordinator consumes governed capabilities.

Coordinator projects governed capabilities.

Coordinator does not become capability authority.

Capability Projection is not a system of record.

### Failure And Fallback Behavior

When any of the following are unavailable or incomplete:

- contract data
- projection source
- identity
- room context
- capability metadata

Fallback behavior must remain:

- explainable
- deterministic
- safe

Fallback must use bounded degradation and explicit limitation messaging rather than hidden inference.

## Consequences

Positive outcomes:

- establishes architecture authority for capability projection behavior
- prevents capability governance drift into runtime orchestration
- improves deterministic and explainable household experience
- creates explicit guest and unsupported-capability handling expectations

Tradeoffs:

- requires stronger governance discipline for visibility and projection policy changes
- requires explicit explainability payloads for projection decisions

## Rejected Alternatives

### 1. Coordinator-owned capability governance

Rejected because Coordinator is a consumer and orchestrator, not a governance authority.

### 2. Projection-generated capabilities

Rejected because capability creation must remain contract-governed and source-owned.

### 3. Capability ownership through runtime projection

Rejected because projection consumes owned capabilities and does not redefine ownership.

### 4. Hidden capability inference

Rejected because hidden inference breaks determinism, explainability, and governance boundaries.

### 5. Capability visibility without explainability

Rejected because capability projection must be auditable and user-explainable by architecture requirement.

### 6. Guest access through implicit elevation

Rejected because guest behavior must follow explicit governed visibility rules and safe authorization boundaries.
