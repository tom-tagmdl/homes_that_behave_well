# ADR: Provenance Governance Boundaries

## ADR Number

ADR-011

## Status

Accepted.

## Context

Provenance is a first-class cross-domain architecture concern in Homes That Behave Well.

Provenance underpins trustable coordination, messaging history, memory explainability, task and shopping attribution, productivity synthesis, delivery and acknowledgement history, and household-facing explanations.

Without explicit governance, provenance can drift into hidden inference, ambiguous attribution certainty, room-truth confusion, or source-of-record overreach.

This ADR establishes architecture authority for provenance ownership boundaries, non-rights, taxonomy categories, attribution semantics, explainability, and future E14 provenance planning dependencies.

## Decision

### Provenance Definition

Provenance is:

A governed attribution and lineage model that records how, where, when, by whom or by what confidence level, and through which method a household action, observation, message, memory, or synthesized output came into being.

Provenance is NOT:

- event history itself
- identity authority
- room truth authority
- message authority
- household memory authority
- source-of-record authority
- hidden inference authority

Provenance explains lineage.

Provenance does not own the thing being explained.

### Provenance Ownership Table

| Concern | Owner | Provenance Relationship |
|---|---|---|
| event records | governed event systems and producers | references lineage and attribution context |
| signal records | governed signal systems and providers | references lineage and attribution context |
| identity attribution | Voice Identity and identity governance authority | references attribution outputs and confidence states |
| room truth | Foundation | references room, area, and interaction-space context |
| method/channel | execution and interaction channel sources under contracts | records how an action or observation occurred |
| message history | governed messaging systems and contracts | references messaging lineage for trustable explanation |
| household memory | governed household memory domain | references memory lineage and influence context |
| productivity actions | productivity provider systems and governed experience contracts | references action lineage and attribution context |
| task/shopping actions | configured task and shopping provider systems | references provider-originated action lineage |
| delivery history | provider and channel delivery systems | references delivery state lineage |
| acknowledgement history | governed acknowledgement channels and systems | references acknowledgement state lineage |
| provenance governance | HTBW governance | defines provenance boundaries and policy constraints |
| retention policy | HTBW governance policy | governs retention eligibility, expiration, and removal boundaries |
| explainability policy | HTBW governance policy | governs required machine and human explainability outputs |

Ownership principles:

- HTBW owns provenance governance.
- Event models define event structure.
- Service contracts define service boundaries.
- Identity governance defines attribution constraints.
- Foundation owns room truth.
- Provenance references governed domains.
- Provenance does not become authority for governed domains.

### Canonical Field Taxonomy Statement

Canonical provenance field taxonomy categories must include:

- action type
- subject
- actor
- actor confidence
- identity linkage
- room linkage
- method/channel
- source system
- originating event
- originating signal
- timestamp
- lineage
- delivery state
- acknowledgement state
- completion state
- confidence state
- unknown state

This ADR defines taxonomy categories only.

Concrete payload schemas are defined in downstream contracts and models.

### Required Attribution Semantics

#### 1. Created

Meaning:

- an artifact, state entry, or record came into being under governed execution

Required provenance questions:

- what was created
- who or what created it
- when it was created
- where it was associated
- how creation occurred

Actor and identity handling:

- actor may be known, guest, unknown, or system
- identity confidence state must be explicit when identity-linked

Room and context handling:

- include room, area, interaction-space, or explicit unknown room state where applicable

Method and channel handling:

- include voice, UI, automation, provider event, scheduled action, or system-generated method state

Unknown and confidence handling:

- unknown or low-confidence actor and room states remain explicit and not collapsed

Explainability expectation:

- machine and human forms must explain creation lineage and confidence state

#### 2. Added

Meaning:

- an item or entry was appended to an existing governed collection or context

Required provenance questions:

- what was added
- to which collection or context
- by whom or by what method
- when and where it occurred

Actor and identity handling:

- identity linkage must remain bounded by confidence and consent policy

Room and context handling:

- include explicit room linkage or unknown room state when context is room-sensitive

Method and channel handling:

- include channel and method used to add the item

Unknown and confidence handling:

- low-confidence actor and room states remain visible and explainable

Explainability expectation:

- explain why addition is attributed and why confidence is high, low, or unknown

#### 3. Assigned

Meaning:

- ownership, responsibility, or routing association was set under governed policy

Required provenance questions:

- what was assigned
- to whom or to what target
- by which policy path and method
- when and where assignment occurred

Actor and identity handling:

- attribution must identify assigner state and assignee linkage under policy constraints

Room and context handling:

- include room linkage when assignment is room-sensitive

Method and channel handling:

- include assignment channel and initiation method

Unknown and confidence handling:

- unknown assignment actors or targets remain explicit and non-inferred

Explainability expectation:

- provide rationale for assignment path and attribution confidence

#### 4. Completed

Meaning:

- a governed action, task, or workflow reached completion state

Required provenance questions:

- what was completed
- by whom or by what method
- when completion occurred
- where completion was associated

Actor and identity handling:

- actor state includes known, guest, unknown, or system with explicit confidence

Room and context handling:

- include room linkage for room-associated completions

Method and channel handling:

- include completion channel and originating method

Unknown and confidence handling:

- unknown or low-confidence completion actors remain explicit

Explainability expectation:

- explain completion attribution, lineage, and confidence state

#### 5. Delivered

Meaning:

- a message, response, or output was delivered through a governed channel

Required provenance questions:

- what was delivered
- to whom or to what destination
- when delivery occurred
- through which channel and method

Actor and identity handling:

- delivery attribution includes recipient identity state when available under policy

Room and context handling:

- include room association where delivery was context-scoped

Method and channel handling:

- include channel and mechanism of delivery

Unknown and confidence handling:

- unknown recipients or low-confidence linkage remain explicit

Explainability expectation:

- explain why delivery occurred and why visibility constraints applied

#### 6. Acknowledged

Meaning:

- a delivered output or request received an explicit acknowledgement state

Required provenance questions:

- what was acknowledged
- who or what acknowledged it
- when acknowledgement occurred
- through which method or channel

Actor and identity handling:

- acknowledgement actor state must include explicit confidence or unknown state

Room and context handling:

- include room linkage when acknowledgement is room-sensitive

Method and channel handling:

- include acknowledgement method and channel

Unknown and confidence handling:

- unknown acknowledgers and low-confidence linkage remain explicit

Explainability expectation:

- explain why acknowledgement is attributed, un-attributed, or low-confidence

### Identity Linkage Boundaries

Provenance linkage may reference:

- known person
- enrolled person
- guest
- unknown user
- low-confidence attribution
- no attribution available

Provenance may reference identity attribution.

Provenance does not own identity.

Provenance does not override Voice Identity.

Provenance does not become attribution authority.

Unknown and low-confidence states must remain explicit and explainable.

### Room Linkage Boundaries

Provenance linkage may reference:

- room
- area
- interaction space
- merged-room context
- unknown room
- low-confidence room context

Provenance may reference room context.

Provenance does not own room truth.

Foundation remains authority for room, device, and area truth.

Unknown room states must remain explicit.

### Method And Channel Linkage

Provenance method and channel linkage may reference:

- voice
- UI
- automation
- provider event
- scheduled action
- system-generated action

Method linkage explains how an action occurred.

Method linkage does not become execution authority.

### Unknown And Confidence Handling

Deterministic provenance handling is required for:

- unknown actor
- unknown room
- unknown method
- low identity confidence
- low room confidence
- conflicting attribution
- conflicting room context

Unknown states must not be collapsed into assumed certainty.

Low confidence states must remain visible in machine and human explainability.

### Retention Principles

Retention governance defines policy behavior, not storage implementation.

Governance principles include:

- provenance retention eligibility
- retention duration governance
- expiration
- redaction
- user-directed removal
- household-directed removal
- privacy-safe minimization

### Messaging, Memory, And Synthesis Relationship

Provenance supports:

- messaging history
- household memory
- productivity experiences
- briefing experiences
- household status synthesis
- future E14 provenance work

Provenance supports explanation and trust.

Provenance does not become message authority.

Provenance does not become memory authority.

Provenance does not become synthesis authority.

### Machine Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- provenance identifier
- action type
- actor or unknown actor state
- identity confidence
- room or unknown room state
- method/channel
- source system
- lineage
- timestamp
- confidence state

### Human Explainability Requirements

Human explainability outputs must include:

- who or what performed the action
- where the action was associated
- how the action occurred
- when it occurred
- why attribution is known, unknown, or low-confidence
- why attribution influenced or did not influence behavior

### Provenance Non-Rights

Provenance does not own:

- governance
- contracts
- models
- events
- signals
- identities
- profiles
- rooms
- messages
- memory
- provider systems
- source-of-record ownership

Provenance may not redefine architecture authority.

### Determinism Requirements

Provenance determinism requires:

- same governed action inputs produce same provenance outcome
- same identity confidence inputs produce same attribution state
- same room context inputs produce same room linkage state
- same method inputs produce same method linkage state
- same retention rules produce same retention outcome

Prohibited:

- hidden provenance creation
- hidden attribution certainty
- hidden room certainty
- hidden provenance mutation
- hidden provenance influence

### Source-Of-Record Boundaries

Event systems remain authoritative.

Signal systems remain authoritative.

Identity systems remain authoritative.

Foundation remains authoritative for room, device, and area truth.

Provider systems remain authoritative for their domains.

Provenance consumes and explains governed information.

Provenance is not a source of record.

### E14 Dependency Mapping

This ADR is a required dependency for future E14 provenance planning.

Future E14 planning must consume this ADR for:

- provenance contracts
- provenance models
- provenance payloads
- provenance diagnostics
- messaging history provenance
- household memory provenance
- task, shopping, and action attribution

If no dedicated E14 planning artifact exists, canonical architecture must include an explicit future E14 dependency reference to this ADR.

## Consequences

Positive outcomes:

- establishes architecture authority for provenance governance across domains
- strengthens trustable explanations for coordination, messaging, memory, and synthesis
- prevents provenance authority drift into identity, room truth, or source-of-record ownership
- enforces explicit unknown and confidence state handling for household-facing predictability

Tradeoffs:

- requires stronger downstream contract and model governance for provenance taxonomy and explainability
- requires explicit policy enforcement for confidence visibility, redaction, and retention minimization

## Rejected Alternatives

### 1. Provenance as event authority

Rejected because event systems remain authoritative for event records.

### 2. Provenance as identity authority

Rejected because identity attribution authority remains with Voice Identity under identity governance.

### 3. Provenance as room truth authority

Rejected because Foundation remains authority for room, device, and area truth.

### 4. Provenance without confidence states

Rejected because hidden certainty and missing confidence states violate explainability and trust boundaries.

### 5. Provenance without human explainability

Rejected because household trust requires plain-language lineage and attribution reasoning.

### 6. Provenance as a source of record

Rejected because provenance explains governed information and does not replace authoritative source domains.
