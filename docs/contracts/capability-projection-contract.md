# Capability Projection Contract

## Purpose

This contract defines the authoritative boundary for capability visibility, availability, discoverability, explainability, and governed projection behavior in Concierge V2.

This contract governs:

- capability visibility
- capability availability
- room-scoped capabilities
- scope-scoped capabilities
- capability discoverability
- capability projection
- What Can I Do Here behavior
- capability explainability
- capability determinism

This contract must not define runtime execution logic.

---

## Definition

Capability Projection is a governed projection layer that determines what capabilities are visible and available to a household interaction context.

Capability Projection is not:

- execution authority
- room truth authority
- identity authority
- experience authority

Capability Projection determines visibility.

Capability Projection does not execute.

---

## Ownership Table

| Concern | Owner | Capability Projection Relationship |
|---|---|---|
| room truth | Foundation | projection consumes room truth context and does not redefine it |
| occupancy | Foundation | projection consumes occupancy state as policy input |
| attribution confidence | Voice Identity | projection consumes confidence signals as policy input |
| room vocabulary | Vocabulary Registry under HTBW governance | projection consumes room language and aliases |
| room interaction | Concierge Coordinator V2 runtime orchestration | projection consumes interaction context envelope |
| capability projection | Concierge capability projection under HTBW governance | projection owns capability visibility and availability decisions |
| experience projection | Concierge experience projection under HTBW governance | projection remains separate and consumes capability outputs |
| execution | Service contracts and execution orchestration paths | projection informs discoverability and availability but does not execute |
| explainability | HTBW governance policy applied by projection consumers | projection must emit machine and human explainability outputs |

Required ownership alignment:

- Foundation owns room truth.
- Voice Identity owns confidence.
- Capability Projection owns capability visibility.
- Coordinator consumes capability projections.

---

## Capability Categories

### 1. Room Capabilities

Projection responsibilities:

- determine visibility of capabilities within resolved room context
- apply room-scoped policy and availability constraints
- expose deterministic room capability discoverability

### 2. Area Capabilities

Projection responsibilities:

- determine capability visibility tied to area context language
- align area-level projection with governed room and area truth
- preserve deterministic area capability projection outcomes

### 3. Floor Capabilities

Projection responsibilities:

- determine floor-scoped capability visibility under floor defaults
- preserve deterministic floor capability discoverability
- avoid overriding explicit room-scoped visibility outcomes

### 4. Household Capabilities

Projection responsibilities:

- determine whole-household capability visibility under concierge-wide policy
- preserve deterministic household capability discoverability
- keep household projection distinct from room-specific visibility

### 5. Composite Room Capabilities

Projection responsibilities:

- project capabilities for explicit composite interaction spaces
- align capability visibility with composite membership and policy
- preserve deterministic composite capability visibility across member-area invocation

### 6. Merged Room Capabilities

Projection responsibilities:

- treat merged room as the user-facing projection term for composite interaction spaces
- ensure merged-room capability discoverability remains deterministic and explainable
- preserve merged-room visibility parity under ADR-013 governance

### 7. Productivity Capabilities

Projection responsibilities:

- determine visibility for productivity capability families (calendar, email, tasks, shopping, briefing, knowledge)
- apply policy-driven visibility constraints by context and eligibility
- preserve provider ownership boundaries and deterministic discoverability

### 8. Knowledge Capabilities

Projection responsibilities:

- determine visibility for governed knowledge capability surfaces
- preserve deterministic knowledge capability projection outcomes
- keep knowledge projection separate from knowledge ownership and execution behavior

This section defines projection responsibilities only.

This section does not define execution.

---

## What Can I Do Here

This section is mandatory capability governance.

Capability Projection owns governed answers for:

- What can I do here?
- What can I do in this room?
- What capabilities are available?
- Why are capabilities available?

Rules:

- answers must be produced from governed projection outputs
- answers must reflect room and scope context deterministically
- unavailable capabilities must be explainable as unavailable
- execution paths may consume these answers, but execution does not own them

---

## Room Vocabulary Relationship

Room Vocabulary provides room language.

Capability Projection consumes vocabulary.

Capability Projection does not own vocabulary.

Vocabulary ownership, alias governance, and room naming governance remain in the Room Vocabulary Registry Contract.

---

## Room Interaction Relationship

Room Interaction provides interaction context.

Capability Projection consumes interaction context.

Capability Projection does not own interaction context.

Interaction orchestration, responder behavior, and interaction execution boundaries remain in the Room Interaction Contract.

---

## Occupancy And Presence Relationship

Occupancy and Presence may influence capability visibility.

Occupancy and Presence do not directly grant capability authority.

Projection remains policy-driven.

Projection behavior must keep occupancy confidence and attribution confidence explicit and bounded.

---

## Productivity Capability Projection

Projection visibility governance must include:

- Calendar
- Email
- Tasks
- Shopping
- Briefing
- Knowledge

Rules:

- Capability Projection determines visibility and discoverability for these capability families
- provider systems remain systems of record for their domains
- projection may limit visibility by policy, scope, and context without transferring provider ownership
- productivity capability visibility outcomes must remain deterministic and explainable

---

## Merged Room Capability Projection

Merged-room capability projection is a required acceptance area.

Required governance:

- merged-room capability visibility
- merged-room capability discoverability
- merged-room determinism

Alignment requirements:

- align with ADR-013
- align with Room Interaction Contract

Household-facing ambiguity may not increase.

---

## Experience Projection Relationship

Capability Projection answers:

- What can I do?

Experience Projection answers:

- What experiences are available?

Capability Projection must not own Experiences.

Experience Projection must not own Capabilities.

Both projections may compose, but ownership boundaries remain separate.

---

## Explainability Requirements

### Machine Explainability

Machine explainability must include:

- capability identifier
- projection source
- room context
- scope context
- visibility rationale
- occupancy influence
- timestamps

### Human Explainability

Human explainability must include:

- why capability appears
- why capability does not appear
- why capability is limited
- why capability is available in this context

Explainability must remain concise, deterministic, and auditable.

---

## Determinism Requirements

Determinism requirements:

- same room context -> same projected capabilities
- same scope context -> same projected capabilities
- same occupancy state -> same projection result

Prohibited behavior:

- hidden capability visibility
- hidden capability suppression
- hidden projection logic

Determinism failures are contract violations.

---

## Non-Rights

Capability Projection does not own:

- execution
- room truth
- occupancy truth
- identity authority
- experience authority
- governance authority

Capability Projection may not redefine architecture authority, contracts, or source-of-record ownership.

---

## V1 Parity Requirements

Aligned with ADR-013, this contract preserves:

- room-scoped capability discoverability
- composite-scope capability discoverability
- floor-scope capability discoverability
- merged-room capability discoverability

Implementation may change.

Household-facing outcomes may not regress.

---

## Relationship Notes

Capability Projection <-> Room Vocabulary

- Room Vocabulary supplies governed room language and alias context
- Capability Projection consumes language for deterministic visibility and discoverability

Capability Projection <-> Room Interaction

- Room Interaction supplies interaction context envelope
- Capability Projection consumes context for scoped capability answers

Capability Projection <-> Experience Projection

- Capability Projection exposes actionable capability visibility
- Experience Projection exposes experience availability without capability ownership transfer

Capability Projection <-> Occupancy / Presence

- Occupancy and Presence influence visibility policy decisions
- Occupancy and Presence do not transfer capability authority

Capability Projection <-> Coordinator V2

- Coordinator V2 consumes projection outputs for explainable orchestration
- Coordinator V2 does not become capability governance authority

---

## Contract Coverage Review

### What Remains In Existing Contracts

`docs/contracts/room-vocabulary-registry-contract.md` remains authoritative for:

- room naming and alias governance
- room discovery and scope vocabulary governance
- merged/composite terminology governance

`docs/contracts/room-interaction-contract.md` remains authoritative for:

- interaction context resolution
- interaction-space behavior and merged-room interaction determinism
- interaction-level What Can I Do Here orchestration boundary

`docs/contracts/concierge-contract.md` remains authoritative for:

- overall orchestration responsibilities
- cross-capability communication behavior and policy boundaries
- system-level non-rights and source-of-record boundaries

### What Now Belongs To Capability Projection Contract

This contract is authoritative for:

- capability visibility and availability governance
- capability discoverability governance
- scope-specific capability projection governance
- projection explainability and determinism requirements
- projection relationship boundaries to vocabulary, interaction, occupancy, experience, and coordinator

Duplication prevention rule:

- vocabulary ownership stays in room vocabulary contract
- interaction ownership stays in room interaction contract
- orchestration ownership stays in concierge contract
- capability projection ownership stays in this contract

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

This contract consumes governance.

This contract does not redefine governance authority.

---

## Ownership Boundary Validation

Ownership boundaries preserved by this contract:

- Foundation remains authoritative for room and occupancy truth
- Voice Identity remains authoritative for attribution confidence
- Capability Projection remains authoritative for capability visibility and availability projection decisions
- Experience Projection remains a separate governed projection surface
- execution ownership remains outside projection boundaries
- Coordinator V2 consumes projection outputs and remains orchestration-only

---

## Terminology Alignment

Canonical terminology in this contract:

- Capability Projection
- Capability Visibility
- Capability Availability
- Room Scope
- Area Scope
- Floor Scope
- Household Scope
- Composite Room
- Merged Room
- Occupancy
- Presence
- Attribution
- Confidence
- Explainability
- Determinism

Legacy assumptions that imply hidden projection logic, hidden suppression, or ownership transfer are prohibited.

---

## Final Principle

Capability Projection governs what capabilities are visible and available in context.

It must be deterministic, explainable, policy-bounded, and ownership-safe.

It does not execute.
