# ADR: Occupancy and Presence Governance Boundaries

## ADR Number

ADR-012

## Status

Accepted.

## Context

Occupancy and Presence are first-class governance concepts in Homes That Behave Well.

Occupancy and Presence influence restoration eligibility, messaging eligibility, household memory relevance, interaction routing, household coordination, responder selection, and context resolution.

Without explicit governance boundaries, occupancy and presence behavior can drift into hidden certainty, identity overreach, room-truth overreach, privacy risk, and non-explainable coordination behavior.

This ADR establishes architecture authority for occupancy and presence governance across contracts, models, runtime services, messaging systems, restoration systems, memory systems, and downstream planning work.

## Decision

### Occupancy and Presence Definitions

Occupancy:

Governed determination that one or more people may be physically present within a room, area, interaction space, or household scope.

Presence:

Governed determination that a specific person may be participating in or associated with an interaction context.

Required distinctions:

- Occupancy does not equal Presence.
- Presence may consume occupancy.
- Occupancy does not imply identity certainty.
- Presence does not imply occupancy certainty.

### Occupancy and Presence Ownership Table

| Concern | Owner | Relationship |
|---|---|---|
| occupancy | Foundation truth services and governed occupancy context sources | consumed as governed context |
| presence | governed interaction context under HTBW policy using attribution inputs | consumed as governed context |
| room truth | Foundation | authoritative room, area, and device truth |
| identity attribution | Voice Identity | authoritative attribution confidence input |
| interaction space | Concierge runtime orchestration under governance | consumes occupancy and presence context |
| messaging eligibility | governed messaging policy and runtime orchestration | consumes occupancy and presence context for eligibility |
| restoration eligibility | governed restoration policy and runtime orchestration | consumes occupancy and presence context for eligibility |
| memory relevance | governed household memory policy and systems | consumes occupancy and presence context for relevance |
| occupancy governance | HTBW governance | authoritative governance owner |
| explainability policy | HTBW governance | authoritative explainability policy owner |

Ownership principles:

- Foundation owns occupancy and room truth.
- Voice Identity owns attribution confidence.
- HTBW owns governance.
- Coordinator consumes occupancy and presence.
- Coordinator does not own occupancy authority.

### Occupancy Lifecycle States

Governance defines the following occupancy lifecycle states:

#### 1. Unknown

Purpose:

- no reliable occupancy determination is currently available

Confidence interpretation:

- occupancy confidence is insufficient for certainty classification

Transition expectations:

- transitions only when governed context evidence improves or degrades deterministically

Governance implications:

- apply conservative visibility and neutral behavior defaults

#### 2. Possible

Purpose:

- early indication that occupancy may exist in scope

Confidence interpretation:

- weak but non-zero occupancy confidence

Transition expectations:

- may move to Unknown, Probable, or Present based on governed confidence updates

Governance implications:

- no certainty assumptions; behavior remains conservative and explainable

#### 3. Probable

Purpose:

- occupancy likely exists but does not yet satisfy present certainty threshold

Confidence interpretation:

- moderate confidence with bounded uncertainty

Transition expectations:

- may move to Present, Active, Possible, or Unknown under governed transitions

Governance implications:

- allow bounded context use with explicit confidence visibility

#### 4. Present

Purpose:

- occupancy is confidently established in scope

Confidence interpretation:

- strong occupancy confidence under governed policy

Transition expectations:

- may move to Active, Departing, Probable, or Unknown based on governed updates

Governance implications:

- eligible for governed context-driven behavior while preserving privacy and policy boundaries

#### 5. Active

Purpose:

- occupancy is present with active interaction or active participation signal

Confidence interpretation:

- strong occupancy confidence with active interaction context

Transition expectations:

- may move to Present, Departing, Probable, or Unknown

Governance implications:

- supports governed interaction, routing, and eligibility behavior with explicit explainability

#### 6. Departing

Purpose:

- occupancy likely transitioning out of scope

Confidence interpretation:

- occupancy confidence decaying with explicit transition visibility

Transition expectations:

- may move to Absent, Probable, or Unknown based on governed evidence

Governance implications:

- apply cautious behavior changes and avoid abrupt hidden state assumptions

#### 7. Absent

Purpose:

- occupancy is not currently established in scope

Confidence interpretation:

- confidence indicates absence under governed policy

Transition expectations:

- may move to Possible or Unknown when new governed context appears

Governance implications:

- no occupancy-based assumptions for person-aware eligibility behavior

### Occupancy and Identity Confidence Policy

Governance policy must keep occupancy confidence and identity confidence distinct and explicit.

Combined confidence cases:

#### Occupancy known and identity known

- both confidence states are explicit
- governed person-aware behavior may apply within policy boundaries

#### Occupancy known and identity unknown

- occupancy context may influence scoped behavior
- identity-linked behavior remains neutral and conservative

#### Occupancy unknown and identity known

- identity context may inform bounded interaction behavior
- occupancy-linked behavior remains conservative until occupancy confidence improves

#### Occupancy unknown and identity unknown

- apply neutral and privacy-safe default behavior
- avoid certainty assumptions and require explicit explainability for limitations

Required policy constraints:

- uncertainty must not be collapsed into certainty
- occupancy confidence and identity confidence states must remain explainable

### Guest and Unknown Policy

Required behavior for guest, unknown user, low-confidence attribution, and unverified occupancy:

- safe by default
- privacy-preserving
- conservative visibility
- deterministic

Guest behavior must not expose private household context.

Unknown-user behavior must default to neutral behavior.

### Multi-Person Policy

Governance must define explicit behavior for:

- multiple known occupants
- known and guest occupants
- multiple unidentified occupants
- conflicting identity signals
- conflicting occupancy signals

Policy requirements:

- conflict visibility must be explicit
- confidence treatment must remain explicit and bounded
- explainability must describe conflict-aware behavior and limitations

This section defines governance only and does not define conflict-resolution algorithms.

### Restoration Eligibility Governance

Occupancy and Presence may influence:

- room restoration
- experience restoration
- continuity restoration
- personalization restoration

Occupancy and Presence provide governed context.

Occupancy and Presence do not directly authorize restoration.

Restoration remains governed by policy.

### Messaging Eligibility Governance

Occupancy and Presence may influence:

- who can receive messaging
- who can hear messaging
- who can be included in messaging context

Occupancy and Presence inform eligibility.

Occupancy and Presence do not grant authority.

Private information must remain protected.

### Household Memory Relationship

Occupancy and Presence may influence:

- memory relevance
- memory context
- memory explainability

Occupancy and Presence contribute context.

Occupancy and Presence do not become memory authority.

### Machine Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- occupancy state
- presence state
- occupancy confidence
- identity confidence
- room linkage
- interaction space
- timestamps
- confidence rationale

### Human Explainability Requirements

Human explainability outputs must include:

- why occupancy was inferred
- why presence was inferred
- why certainty is limited
- why guest-safe behavior was applied
- why restoration or messaging behavior changed

### Policy Mapping Note

This policy mapping note governs how states inform policy domains.

Governed mapping inputs:

- occupancy states
- presence states
- confidence states

Governed mapping outputs:

- restoration governance
- messaging governance
- memory governance
- personalization governance

This mapping is governance-only and does not define implementation logic.

### Occupancy and Presence Non-Rights

Occupancy and Presence do not own:

- governance
- contracts
- models
- identity authority
- room truth authority
- memory authority
- personalization authority
- source-of-record ownership

Occupancy and Presence may not redefine architecture authority.

### Determinism Requirements

Occupancy and Presence determinism requires:

- same governed inputs produce same occupancy state
- same confidence inputs produce same confidence classification
- same policy inputs produce same governance outcome

Prohibited:

- hidden occupancy certainty
- hidden presence certainty
- hidden policy elevation
- hidden state mutation

### Source-Of-Record Boundaries

Foundation remains authoritative for occupancy and room truth.

Voice Identity remains authoritative for attribution confidence.

Provider systems remain authoritative for their domains.

Occupancy and Presence consume governed information.

Occupancy and Presence are not sources of record.

### Closure Dependency Mapping

This ADR is a mandatory dependency for:

- E8a
- E8
- E9
- E10

If planning artifacts do not yet exist, canonical architecture must include explicit future dependency references to this ADR for E8a, E8, E9, and E10 planning.

## Consequences

Positive outcomes:

- establishes architecture authority for occupancy and presence governance boundaries
- creates explicit lifecycle and confidence governance constraints for predictable behavior
- strengthens guest-safe and unknown-user protection in context-driven decisions
- improves explainable restoration, messaging, and memory eligibility behavior

Tradeoffs:

- requires stronger policy validation for confidence and multi-person conflict handling
- requires explicit explainability and governance mapping enforcement in downstream contracts and models

## Rejected Alternatives

### 1. Occupancy as identity authority

Rejected because identity attribution authority remains with Voice Identity.

### 2. Presence as identity authority

Rejected because presence context does not transfer attribution authority ownership.

### 3. Occupancy without confidence states

Rejected because hidden certainty violates determinism and explainability requirements.

### 4. Presence without explainability

Rejected because household trust requires explicit rationale for presence-linked behavior.

### 5. Guest behavior without privacy boundaries

Rejected because guest-safe defaults and privacy protection are mandatory governance constraints.

### 6. Occupancy or Presence as a source of record

Rejected because source-of-record ownership remains with Foundation, Voice Identity, and provider systems.
