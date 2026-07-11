# ADR: Experience Model Governance Boundaries

## ADR Number

ADR-007

## Status

Accepted.

## Context

Experience is a first-class architectural concept in Homes That Behave Well.

Experience governs household-facing outcomes across room context, person context, capabilities, continuity, and interaction patterns.

Without an explicit Experience governance ADR, downstream contracts, models, projections, and runtime implementations can drift and redefine Experience inconsistently.

This ADR establishes authoritative Experience governance boundaries for all downstream work.

## Decision

### Experience Definition

Experience is defined as:

A governed household-facing outcome model that coordinates capabilities, context, and interaction patterns to achieve an intended household outcome.

Experience is not:

- a capability registry
- a capability authority
- an intent
- a conversation
- a projection
- a source-of-record system

### Experience Ownership Table

| Concern | Owner | Experience Relationship |
|---|---|---|
| experience governance | HTBW governance | governed authority |
| experience definition | HTBW governance through ADRs, contracts, and models | governed definition and boundary source |
| capability definitions | contracts and model authority under HTBW governance | consumed for outcome coordination |
| room truth | Foundation | consumed as environment truth input |
| identity attribution | Voice Identity | consumed for confidence-aware eligibility and personalization |
| context | governed context providers and platform peers | consumed as eligibility and orchestration input |
| intent | governed intent resolution flow in Concierge runtime | may be fulfilled by experience execution path |
| experience projection | Concierge Coordinator V2 runtime behavior under governed policy | projects governed experiences |
| experience execution | Concierge orchestration via governed contracts and service interfaces | executes bounded, explainable experience path |
| experience diagnostics | owning domains plus Concierge orchestration metadata | provides explainable machine and human rationale |

Ownership principles:

- HTBW owns governance.
- Contracts define boundaries.
- Models define structure.
- Coordinator consumes experiences.
- Coordinator orchestrates experiences.
- Coordinator does not own experiences.

### Experience Domain Coverage Matrix

| Domain | Description | Governing Source | Experience Role | Ownership Boundaries |
|---|---|---|---|---|
| Lighting | household lighting outcome coordination and contextual presentation | Foundation truth and governed capability contracts | surface and orchestrate eligible lighting experiences | Experience consumes capabilities; does not own lighting truth or capability definitions |
| Audio | audio control and listening experience coordination | Foundation truth and governed capability contracts | coordinate room-aware and person-aware audio experiences | Experience does not own audio devices, states, or provider authority |
| Video | video and display interaction outcomes | Foundation truth and governed capability contracts | route and coordinate video experiences by scope and eligibility | Experience does not own video provider or device truth |
| Climate | comfort-oriented household outcomes for climate interaction | Foundation truth and governed capability contracts | coordinate climate experiences with bounded eligibility | Experience does not own climate truth or provider state authority |
| Messaging | household messaging and communication outcomes | governed messaging contracts and provider interfaces | present and orchestrate messaging experiences | Experience does not own message provider systems of record |
| Discovery | awareness and discovery outcomes for household opportunities | governed context and capability surfaces | present discoverable experiences under visibility policy | Experience does not define new capability authority |
| Calendar Experiences | household and personal schedule-aware outcomes | calendar provider systems and governed contracts | surface, summarize, and coordinate calendar experiences | Calendar providers remain systems of record |
| Email Experiences | communication awareness outcomes from email context | email provider systems and governed contracts | surface and coordinate email experiences | Email providers remain systems of record |
| Task Experiences | task execution and planning outcomes | configured task provider systems and governed contracts | coordinate task experiences and execution options | Task providers remain systems of record |
| Shopping Experiences | shopping list and purchasing workflow outcomes | configured shopping provider systems and governed contracts | coordinate shopping experiences and actionable paths | Shopping providers remain systems of record |
| Knowledge Experiences | governed knowledge retrieval outcomes for household needs | governed knowledge sources and contracts | retrieve and present knowledge experiences | Retrieval and presentation do not create knowledge governance ownership |
| Briefing Experiences | composed cross-domain awareness outcomes for users | governed context sources and briefing policy contracts | assemble and present briefing experiences | Briefing generation does not become source ownership |

### Relationship Model

Experience relationship to core concepts:

- Experiences consume room information.
- Experiences consume person information.
- Experiences consume capabilities.
- Experiences consume context.
- Experiences may fulfill intent.
- Experiences do not own room, person, capability, context, or intent domains.

### Productivity Boundaries

Productivity systems remain authoritative:

- Calendar systems remain systems of record.
- Email systems remain systems of record.
- Task providers remain systems of record.
- Shopping providers remain systems of record.

Experience orchestration does not replace provider ownership.

Experience orchestration consumes governed provider context.

Coordinator may present productivity experiences.

Coordinator may not become the productivity authority.

### Knowledge And Briefing Boundaries

Knowledge Experience:

- governed retrieval and presentation of knowledge context for household outcomes
- not a transfer of governance ownership for knowledge sources

Briefing Experience:

- governed assembly of cross-domain context into a household-facing briefing outcome
- not source ownership for the underlying domains

Knowledge retrieval is not governance ownership.

Briefing generation is not source ownership.

Coordinator assembles governed context.

Coordinator does not own the underlying knowledge domain.

### Experience Non-Rights

Experience does not own:

- governance
- contracts
- models
- room truth
- identity truth
- capability definition
- provider systems
- source-of-record ownership

Experience may not redefine architecture authority.

### Determinism Requirements

Experience determinism requirements:

- same governed inputs produce same experience set
- same context produces same experience eligibility
- same visibility rules produce same experience availability

Prohibited:

- hidden experience creation
- hidden eligibility rules
- hidden governance

### Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- experience identifier
- governing contract or model
- eligibility decision
- source lineage
- timestamps

Human explainability outputs must include:

- why an experience is available
- why it is unavailable
- why it was suggested
- why it was restricted

### Source-Of-Record Boundaries

Experience is not a source of record.

Experiences consume governed inputs.

Systems of record remain authoritative.

Coordinator remains a consumer and orchestrator.

## Consequences

Positive outcomes:

- establishes architecture authority for Experience as a first-class concept
- prevents governance and ownership drift from HTBW into runtime orchestration
- creates explicit domain coverage for household, productivity, and knowledge/briefing outcomes
- strengthens deterministic and explainable household interaction outcomes

Tradeoffs:

- requires stronger governance discipline for experience eligibility and visibility changes
- requires explicit explainability payloads and diagnostics for experience decisions

## Rejected Alternatives

### 1. Experience as capability ownership

Rejected because capability definitions and ownership remain governed by contracts, models, and provider authorities.

### 2. Experience as governance authority

Rejected because HTBW governance remains architecture authority.

### 3. Experience-owned productivity systems

Rejected because calendar, email, task, and shopping providers remain systems of record.

### 4. Experience-owned knowledge systems

Rejected because knowledge retrieval and briefing assembly do not transfer knowledge governance ownership.

### 5. Hidden experience creation

Rejected because hidden creation violates determinism, explainability, and governance boundaries.

### 6. Experience as a source of record

Rejected because Experience consumes governed inputs and does not replace authoritative systems of record.
