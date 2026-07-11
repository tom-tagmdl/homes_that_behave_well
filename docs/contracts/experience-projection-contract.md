# Experience Projection Contract

## Purpose

This contract defines the authoritative boundary for experience visibility, availability, discoverability, composition, and explainability in Concierge V2.

This contract governs:

- experience visibility
- experience availability
- experience discoverability
- experience composition
- experience categorization
- experience explainability
- room-scoped experiences
- person-aware experiences
- productivity experiences
- household memory experiences
- briefing experiences
- household status synthesis experiences

This contract does not define orchestration or runtime execution logic.

---

## Definition

Experience Projection is a governed projection layer that determines what experiences are visible, available, discoverable, and explainable for a specific household interaction context.

Experience Projection is not:

- execution authority
- orchestration authority
- room truth authority
- identity authority
- capability authority
- productivity provider authority

Experience Projection determines what experiences exist in context and why they are visible or unavailable.

Experience Projection does not execute experiences.

---

## Ownership Table

| Concern | Owner | Experience Projection Relationship |
|---|---|---|
| room truth | Foundation | projection consumes room truth and does not redefine it |
| occupancy | Foundation | projection consumes occupancy as context influence input |
| attribution confidence | Voice Identity | projection consumes confidence and does not redefine identity outputs |
| room vocabulary | Vocabulary Registry under HTBW governance | projection consumes room language and alias context |
| room interaction | Concierge Coordinator V2 runtime orchestration | projection consumes resolved interaction context envelope |
| capability projection | Concierge capability projection under HTBW governance | projection consumes capability visibility outcomes as building blocks |
| experience projection | Concierge experience projection under HTBW governance | projection owns experience visibility, discoverability, composition, and availability decisions |
| household memory | Household Memory governance domain under HTBW authority | projection consumes memory context and does not own memory state |
| productivity providers | Calendar, email, tasks, shopping, knowledge, and briefing providers | projection consumes provider outputs and does not assume provider ownership |
| asset significance | Asset Intelligence | projection may consume significance-informed context and does not own significance truth |
| execution | Service contracts and execution orchestration paths | projection informs visibility/discoverability only and does not execute |
| explainability | HTBW governance policy applied by projection consumers | projection must emit machine and human explainability outputs |

Required ownership alignment:

- Foundation owns room and occupancy truth.
- Voice Identity owns attribution confidence.
- Capability Projection owns capability visibility and discoverability.
- Experience Projection owns experience visibility, discoverability, composition, and availability decisions.
- Asset Intelligence retains significance ownership.
- Coordinator V2 consumes projected experiences.

---

## Experience Category Matrix

| Experience Category | Purpose | Source Context | Projection Responsibility |
|---|---|---|---|
| Lighting | room-facing lighting awareness and behavior framing | room context, capability context, posture policy | determine lighting experience visibility and availability by context |
| Audio | audio and listening experience surfacing | room context, media context, capability context | determine audio experience discoverability and availability |
| Video | video and display experience surfacing | room context, display/media context, capability context | determine video experience discoverability and availability |
| Messaging | outbound and inbound household messaging experiences | room context, person context, communication policy | determine messaging experience visibility and suppression behavior |
| Discovery | guided discovery of available household experiences | room context, person context, capability context | determine which discovery experiences appear and why |
| Climate / Environment | comfort and environment-oriented household experiences | room context, occupancy context, environment context | determine climate/environment experience availability without owning environment truth |
| Calendar | schedule-awareness experiences | global context provider outputs, person context | determine calendar experience visibility and discoverability |
| Email | household email-awareness experiences | global context provider outputs, person context | determine email experience visibility and discoverability |
| Tasks | household task workflow experiences | provider task outputs, room/person context | determine task experience visibility and discoverability |
| Shopping | shopping list and grocery workflow experiences | provider shopping outputs, room/person context | determine shopping experience visibility and discoverability |
| Knowledge | knowledge retrieval and reference experiences | knowledge provider outputs, context envelope | determine knowledge experience visibility and discoverability |
| Briefing | curated multi-source summary experiences | global context, signal context, person preferences | determine briefing experience composition, visibility, and availability |
| Household Status Synthesis | synthesized state-of-home awareness experiences | occupancy, environment, signals, capability context | determine synthesis visibility and availability while preserving source ownership |
| Household Memory | continuity and recall experiences across interactions | household memory context, person and room context | determine memory-informed experience visibility and discoverability |

All required categories are governed by projection responsibilities only.

---

## What Experiences Are Available Here

Experience Projection owns governed answers for:

- What experiences are available here?
- What can Concierge help me with?
- Why is this experience available?
- Why is this experience unavailable?

Rules:

- answers must be produced from governed projection outputs
- answers must remain deterministic for identical context inputs
- unavailable experiences must provide concise explainable rationale
- projection outputs may be consumed by orchestration and delivery flows without ownership transfer

Ownership separation:

- Capability Projection answers: What can I do?
- Experience Projection answers: What experiences are available?

Ownership blur between capability and experience surfaces is prohibited.

---

## Room Relationship

Room Interaction provides room context.

Room Vocabulary provides room language.

Experience Projection consumes both.

Experience Projection owns neither.

Room truth ownership remains with Foundation.

---

## Person Relationship

Person context may influence experience visibility, discoverability, and composition.

Identity confidence may influence conservative projection behavior and clarification needs.

Experience Projection consumes person context.

Experience Projection does not own identity.

Voice Identity remains authoritative for attribution and confidence outputs.

---

## Capability Projection Relationship

Capabilities are building blocks.

Experiences are household-facing outcomes.

Capability Projection and Experience Projection are separate governed concerns.

Neither owns the other.

Experience Projection may consume capability outputs as context, but capability ownership remains in Capability Projection governance.

---

## Intent Relationship

Context-before-intent remains authoritative.

Experience Projection may influence discovery and framing.

Experience Projection does not own intent interpretation.

Experience Projection does not replace intent resolution.

Intent interpretation and execution routing remain separate governed responsibilities.

---

## Household Memory Relationship

Household Memory may influence experience availability, discoverability, continuity, and composition.

Experience Projection consumes memory context.

Experience Projection does not own memory.

Memory authority remains external to Experience Projection.

---

## Productivity Experience Governance

Projection governance must include visibility and discoverability for:

- Calendar
- Email
- Tasks
- Shopping
- Knowledge
- Briefing

Rules:

- providers remain systems of record for productivity domains
- Experience Projection governs discoverability and availability decisions only
- projection may apply policy-bounded visibility limits by room, person, and scope context
- projection must preserve deterministic and explainable outcomes

---

## Household Status Synthesis Governance

Experience Projection governs household status synthesis visibility and availability for:

- household status experiences
- occupancy-informed experiences
- environment-informed experiences
- synthesized experiences

Rules:

- synthesis is derived from governed inputs
- synthesis is not a source-of-record authority
- synthesis must preserve ownership boundaries for occupancy, environment, signal, and capability sources
- synthesized output must remain explainable and deterministic

---

## Merged Room Experience Governance

Merged-room experience governance is a required acceptance area.

Required governance:

- merged-room experiences
- merged-room discoverability
- merged-room visibility
- responder consistency

Alignment requirements:

- align with ADR-013
- align with Room Interaction Contract

Household-facing ambiguity may not increase.

---

## Explainability Requirements

### Machine Explainability

Machine explainability must include:

- experience identifier
- projection source
- room context
- person context
- scope context
- visibility rationale
- availability rationale
- timestamps

### Human Explainability

Human explainability must include:

- why experience appears
- why experience is available
- why experience is unavailable
- why room context mattered
- why person context mattered

Explainability outputs must remain concise, deterministic, and auditable.

---

## Determinism Requirements

Determinism requirements:

- same room context -> same experience visibility
- same person context -> same experience visibility
- same scope context -> same experience visibility
- same memory context -> same experience visibility

Prohibited behavior:

- hidden experience visibility
- hidden experience suppression
- hidden context influence

Determinism failures are contract violations.

---

## Non-Rights

Experience Projection does not own:

- room truth
- occupancy truth
- identity authority
- capability authority
- productivity provider ownership
- asset significance ownership
- orchestration
- execution

Experience Projection may not redefine architecture authority, governance boundaries, or source-of-record ownership.

---

## V1 Parity Requirements

Aligned with ADR-013, this contract preserves:

- room-scoped experience discoverability
- floor-scoped experience discoverability
- composite-scope experience discoverability
- merged-room experience discoverability

Implementation may change.

Household-facing outcomes may not regress.

---

## Relationship Notes

Experience Projection <-> Capability Projection

- Capability Projection provides capability visibility and availability building blocks.
- Experience Projection composes household-facing experiences from governed context.

Experience Projection <-> Room Interaction

- Room Interaction provides resolved interaction context envelope.
- Experience Projection consumes context and does not own interaction orchestration.

Experience Projection <-> Room Vocabulary

- Room Vocabulary provides governed room language and alias context.
- Experience Projection consumes language context and does not own vocabulary governance.

Experience Projection <-> Household Memory

- Household Memory provides continuity and history context.
- Experience Projection consumes memory influence and does not own memory truth.

Experience Projection <-> Occupancy / Presence

- Occupancy and Presence influence policy-bounded experience visibility.
- Occupancy and Presence do not transfer experience ownership.

Experience Projection <-> Coordinator V2

- Coordinator V2 consumes experience projection outputs for orchestration and delivery.
- Coordinator V2 does not become experience governance authority.

---

## Contract Coverage Review

### What Remains In Existing Contracts

`docs/contracts/capability-projection-contract.md` remains authoritative for:

- capability visibility and availability governance
- capability discoverability governance
- capability explainability and determinism boundaries

`docs/contracts/room-interaction-contract.md` remains authoritative for:

- interaction context resolution
- merged/composite interaction behavior
- interaction-level deterministic routing and responder behavior

`docs/contracts/room-vocabulary-registry-contract.md` remains authoritative for:

- room naming and alias governance
- room/scope vocabulary governance
- merged/composite terminology governance

`docs/contracts/concierge-contract.md` remains authoritative for:

- concierge orchestration boundaries
- cross-capability communication behavior
- system-level non-rights and source-of-record boundaries

### What Now Belongs To Experience Projection Contract

This contract is authoritative for:

- experience visibility governance
- experience availability governance
- experience discoverability governance
- experience composition governance
- experience category governance
- experience projection explainability and determinism requirements
- projection relationship boundaries to room, person, capability, memory, occupancy, and coordinator

Duplication prevention rule:

- capability ownership stays in capability projection contract
- room interaction ownership stays in room interaction contract
- room vocabulary ownership stays in room vocabulary contract
- orchestration ownership stays in concierge contract
- experience projection ownership stays in this contract

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
- Voice Identity remains authoritative for attribution and confidence outputs
- Capability Projection remains authoritative for capability visibility and discoverability
- Experience Projection is authoritative for experience visibility, discoverability, composition, and availability decisions
- Household Memory authority remains external to experience projection
- Asset Intelligence remains authoritative for significance and environmental interpretation
- Coordinator V2 consumes projection outputs and remains orchestration-only

---

## Terminology Alignment

Canonical terminology in this contract:

- Experience Projection
- Experience Visibility
- Experience Availability
- Experience Discoverability
- Experience Composition
- Room Context
- Person Context
- Scope Context
- Household Memory
- Occupancy
- Presence
- Attribution
- Confidence
- Explainability
- Determinism

Legacy assumptions that imply hidden projection logic, hidden suppression, or ownership transfer are prohibited.

---

## Final Principle

Experience Projection governs what household-facing experiences are visible and available in context.

It must remain deterministic, explainable, policy-bounded, and ownership-safe.

It does not execute.