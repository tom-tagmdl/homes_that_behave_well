# ADR: Household Memory Governance Boundaries

## ADR Number

ADR-009

## Status

Accepted.

## Context

Household Memory is a governed architectural concern in Homes That Behave Well.

Household Memory supports continuity, context quality, experience selection, messaging, briefing, and personalization outcomes when used within governed boundaries.

Without explicit governance, memory behavior can drift into hidden inference, implicit authority transfer, unverifiable memory artifacts, or source-of-record confusion.

This ADR establishes architecture authority for Household Memory governance across contracts, models, projections, coordinators, experiences, briefing systems, messaging systems, and provenance systems.

## Decision

### Household Memory Definition

Household Memory is:

A governed collection of explainable, provenance-backed household memory artifacts that may be used to improve continuity, context, experiences, messaging, briefing, and personalization outcomes.

Household Memory is NOT:

- event history
- event source-of-record
- identity authority
- provenance authority
- message authority
- profile authority
- hidden learning system

Memory consumes governed information.

Memory does not own governed information.

### Household Memory Boundary Table

| Concern | Owner | Memory Relationship |
|---|---|---|
| event history | event producers and governed event systems | source input for bounded memory artifacts |
| signal history | signal providers and governed signal systems | source input for bounded memory artifacts |
| person identity | Voice Identity and identity governance authority | referenced under attribution and consent constraints |
| person profile | profile model and governed profile policy | referenced as bounded person-aware context |
| household memory | Concierge runtime memory behavior under HTBW governance | assembles and consumes governed memory artifacts |
| provenance | governed provenance policy and source lineage authority | required lineage and audit metadata for each memory artifact |
| continuity | Concierge runtime behavior under governed policy | consumes memory context for continuity outcomes |
| affinity | governed preference weighting policy | consumes memory context as bounded weighting signal |
| messaging context | governed messaging contracts and experience policy | memory may contribute contextual support |
| briefing context | governed briefing policy and context contracts | memory may contribute contextual support |
| experience context | governed experience policy and contracts | memory may contribute bounded context input |
| retention policy | HTBW governance policy | governs eligibility, expiration, removal, and reset constraints |
| explainability policy | HTBW governance policy | governs mandatory machine and human explainability outputs |

Ownership principles:

- HTBW owns governance.
- Event models own event structure.
- Signal models own signal structure.
- Identity governance owns attribution constraints.
- Household Memory consumes governed information.
- Household Memory does not become authority for any upstream domain.

### Event History Relationship

Event History is authoritative event record history under event governance.

Household Memory is a governed artifact set derived from governed inputs.

Event History ≠ Household Memory.

Event History does not equal Household Memory.

Event History may contribute to Household Memory.

Household Memory does not become the source of truth for events.

Household Memory may contain derived memory artifacts.

Event history remains authoritative for event records.

### Identity Linkage Boundaries

Identity linkage is bounded by attribution confidence, profile policy, and consent governance.

Attribution linkage boundaries:

- memory may reference attribution snapshots and confidence metadata
- memory may not redefine attribution semantics or confidence authority

Profile linkage boundaries:

- memory may reference governed profile context where policy allows
- memory may not redefine profile structure or profile authority

Identity confidence usage boundaries:

- confidence may gate memory influence eligibility
- low confidence requires neutral and bounded memory influence behavior

Consent boundaries:

- identity-linked memory influence requires governed consent state
- revoked consent immediately disables disallowed identity-linked influence paths

Household Memory may reference identity.

Household Memory does not own identity.

Household Memory does not override Voice Identity.

Household Memory does not become attribution authority.

### Provenance Alignment

Every memory artifact must include governed provenance metadata.

Machine provenance should include:

- originating event
- originating signal
- attribution linkage when available
- creation timestamp
- lineage metadata

Prohibited:

- unattributed memory
- unverifiable memory
- hidden memory creation

### Retention Principles

Retention governance defines policy behavior, not storage implementation.

Governance principles include:

- retention eligibility based on governed relevance and policy
- expiration behavior based on explicit policy boundaries
- relevance decay under deterministic policy rules
- user-directed removal capability
- household-directed removal capability
- memory reset behavior under governed policy

### Messaging And Briefing Relationship

Household Memory may support:

- Messaging Experiences
- Briefing Experiences
- Knowledge Experiences

Household Memory contributes context.

Household Memory does not become message authority.

Household Memory does not become knowledge authority.

Household Memory does not become briefing authority.

### Machine Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- memory identifier
- memory source
- memory lineage
- provenance chain
- attribution linkage
- timestamps

### Human Explainability Requirements

Human explainability outputs must include:

- why memory exists
- where memory originated
- why memory influenced behavior
- why memory did not influence behavior
- why memory was excluded

### Household Memory Non-Rights

Household Memory does not own:

- governance
- contracts
- models
- events
- signals
- identities
- profiles
- provider systems
- provenance
- source-of-record ownership

Household Memory may not redefine architecture authority.

### Determinism Requirements

Household Memory determinism requires:

- same governed inputs produce same memory outcomes
- same provenance inputs produce same lineage
- same retention rules produce same retention outcome

Prohibited:

- hidden memory creation
- hidden memory mutation
- hidden memory influence

### Source-Of-Record Boundaries

Event systems remain authoritative.

Signal systems remain authoritative.

Identity systems remain authoritative.

Household Memory consumes governed information.

Household Memory is not a source of record.

### Dependency For Future E10 Planning

This ADR is a mandatory dependency for future E10 planning.

Future E10 planning artifacts for contracts, models, projections, experiences, briefing, messaging, and provenance must consume this ADR and must not redefine Household Memory governance independently.

## Consequences

Positive outcomes:

- establishes architecture authority for Household Memory governance boundaries
- prevents hidden memory authority and source-of-record drift
- enforces provenance-backed and explainable memory behavior
- enables consistent cross-domain consumption for continuity, messaging, briefing, and personalization

Tradeoffs:

- requires stronger explainability and provenance validation in downstream work
- requires explicit policy handling for retention, consent, and identity linkage boundaries

## Rejected Alternatives

### 1. Household Memory as event authority

Rejected because event systems remain authoritative for event records.

### 2. Household Memory as identity authority

Rejected because identity attribution authority remains with Voice Identity under identity governance.

### 3. Household Memory without provenance

Rejected because unverifiable memory violates explainability, auditability, and governance requirements.

### 4. Hidden memory creation

Rejected because hidden creation violates determinism, explainability, and governance boundaries.

### 5. Household Memory as personalization authority

Rejected because personalization governance is bounded by dedicated governance authority and memory is only a bounded contextual input.

### 6. Household Memory as a source of record

Rejected because memory consumes governed information and does not replace authoritative source systems.
