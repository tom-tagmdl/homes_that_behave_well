# Room Vocabulary Registry Contract

## Purpose

This contract defines the authoritative boundary for room vocabulary definition, governance, and consumption across the HTBW platform.

This contract governs:

- room vocabulary definitions
- room aliases
- room naming
- room discovery vocabulary
- room context vocabulary
- room scope vocabulary
- merged-room vocabulary
- composite-room vocabulary
- floor vocabulary
- explainability requirements for vocabulary resolution

This contract does not govern:

- room truth
- occupancy truth
- identity truth
- runtime execution logic
- parser implementation

---

## Definition

Room Vocabulary is a governed registry of household-recognizable room terminology, aliases, scope identifiers, and interaction vocabulary used to support deterministic room-aware behavior.

Room Vocabulary is not:

- room truth
- occupancy authority
- interaction execution
- intent authority
- parser implementation

Room Vocabulary provides vocabulary.

Room Vocabulary does not provide room truth.

---

## Ownership Table

| Concern | Owner | Relationship |
|---|---|---|
| room truth | Foundation | Vocabulary references governed room truth and does not redefine it |
| room vocabulary | Vocabulary Registry under HTBW governance | Coordinator and projections consume vocabulary outputs |
| room aliases | Vocabulary Registry under HTBW governance | aliases map household language to governed vocabulary entries |
| room scopes | Vocabulary Registry under HTBW governance | scope terms map to governed room, area, floor, household, and composite scope language |
| composite room vocabulary | Vocabulary Registry under HTBW governance | composite names and aliases are governed vocabulary entries referencing composite definitions |
| merged room vocabulary | Vocabulary Registry under HTBW governance | merged terms are governed user-facing vocabulary for composite interaction spaces |
| room interaction | Concierge Coordinator V2 runtime orchestration | consumes vocabulary for context language and deterministic interaction resolution |
| capability projection | Concierge capability projection behavior under governance | consumes room vocabulary language for context-scoped capability projection |
| experience projection | Concierge experience projection behavior under governance | consumes room vocabulary language for context-scoped experience projection |
| explainability | HTBW governance policy applied by consuming contracts | vocabulary resolution decisions must be machine and human explainable |

Coordinator consumes Room Vocabulary.

Coordinator does not own Room Vocabulary.

---

## Room Vocabulary Categories

### 1. Room Names

Responsibilities:

- define canonical household-recognizable room names
- map each canonical name to governed room identity references
- enforce deterministic canonical-name resolution behavior

### 2. Room Aliases

Responsibilities:

- define approved alternate terms for canonical room names
- enforce deterministic alias-to-canonical mapping
- require explicit ambiguity handling for overlapping alias terms

### 3. Area Vocabulary

Responsibilities:

- define governed area terms that reference Foundation area truth
- keep area vocabulary distinguishable from parser behavior
- maintain deterministic area-term resolution

### 4. Floor Vocabulary

Responsibilities:

- define governed floor-level language used for interaction scope
- align floor vocabulary with floor-scope defaults in scope contracts
- preserve deterministic floor-term interpretation

### 5. Composite Room Vocabulary

Responsibilities:

- define governed names and aliases for explicit composite rooms
- preserve composite vocabulary as projection language, not room-truth ownership
- ensure deterministic composite-term resolution across member-area invocation paths

### 6. Merged Room Vocabulary

Responsibilities:

- support user-facing merged-room terminology as composite vocabulary
- define merged aliases and references without introducing hidden remapping
- preserve deterministic merged-term interpretation and discoverability

### 7. Household Scope Vocabulary

Responsibilities:

- define household-wide scope terms that remain distinct from room or floor terms
- align with concierge-wide scope semantics under governed scope contracts
- preserve deterministic scope-term interpretation

---

## Room Discovery Vocabulary

Room discovery vocabulary governs terms used to identify and confirm room context.

This includes language for:

- room discovery
- room identification
- room selection
- room awareness

Examples:

- Where am I?
- What room is this?
- Which room am I in?

Governance requirements:

- discovery terms must map to governed vocabulary entries
- discovery interpretation must be deterministic and explainable
- discovery terms must not redefine room truth ownership

This contract defines discovery vocabulary governance only.

This contract does not define parser logic.

---

## Room Scope Vocabulary

Room scope vocabulary governs language for:

- room scope
- area scope
- floor scope
- household scope
- composite scope

Scope vocabulary alignment requirements:

- must align with `docs/contracts/concierge-scope-contract.md`
- must align with `docs/contracts/room-interaction-contract.md`
- must preserve room override, floor default, concierge default precedence language

Scope vocabulary must remain deterministic and explainable for repeated inputs.

---

## Merged Room Vocabulary

Merged room vocabulary is a required governed acceptance area.

It defines vocabulary expectations for:

- merged rooms
- merged aliases
- merged interaction references
- merged-room discoverability

Alignment requirements:

- must align with ADR-013 non-regression governance
- must align with `docs/contracts/room-interaction-contract.md`

Household-facing ambiguity must not increase.

Merged-room terminology may be flexible, but resolution outcomes must remain deterministic.

---

## What Can I Call This Room?

This contract governs acceptable household naming flexibility while preserving deterministic resolution.

Governed areas:

- official room names
- approved aliases
- accepted household terminology
- deterministic vocabulary resolution

Rules:

- households may define flexible aliases within governed constraints
- alias sets must remain bounded and explainable
- ambiguous terms must require deterministic conflict handling and, when needed, explicit clarification

This section supports household flexibility without introducing ambiguity.

---

## Room Vocabulary And Capability Projection

Room Vocabulary provides room context language.

Capability Projection consumes room vocabulary.

Capability Projection does not own room vocabulary.

Capability availability and ownership remain governed by capability contracts and provider boundaries.

---

## Room Vocabulary And Experience Projection

Room Vocabulary provides experience context language.

Experience Projection consumes vocabulary.

Experience Projection does not own vocabulary.

Experience availability and ownership remain governed by experience contracts, models, and provider boundaries.

---

## Explainability Requirements

### Machine Explainability

Machine explainability must include:

- resolved room term
- source vocabulary entry
- alias resolution
- composite resolution
- merge-state resolution

### Human Explainability

Human explainability must include:

- why a room was selected
- why an alias was matched
- why a room reference was interpreted as resolved outcome

Explainability outputs must remain concise, deterministic, and auditable.

---

## Determinism Requirements

Determinism requirements:

- same vocabulary input -> same vocabulary resolution
- same alias -> same room interpretation
- same scope term -> same scope interpretation

Prohibited behavior:

- hidden alias resolution
- hidden room remapping
- hidden scope remapping

Determinism failures are contract violations.

---

## Non-Rights

Room Vocabulary does not own:

- room truth
- occupancy
- identity
- execution
- capabilities
- experiences

Room Vocabulary does not redefine authority.

---

## Relationship Notes

Room Vocabulary <-> Foundation

- Foundation remains source of room, area, floor, and occupancy truth
- Vocabulary references truth without owning or mutating it

Room Vocabulary <-> Room Interaction

- Room Interaction consumes vocabulary for context language and deterministic interpretation
- Room Interaction remains execution/orchestration behavior and does not own vocabulary governance

Room Vocabulary <-> Capability Projection

- Capability Projection consumes vocabulary for room-context language
- Capability Projection does not own vocabulary definitions

Room Vocabulary <-> Experience Projection

- Experience Projection consumes vocabulary for experience-context language
- Experience Projection does not own vocabulary definitions

Room Vocabulary <-> Composite Rooms

- Composite room names and aliases are governed vocabulary entries tied to explicit composite definitions
- Vocabulary does not define composite lifecycle behavior

Room Vocabulary <-> Merged Rooms

- Merged-room user terms are governed vocabulary references for composite interaction spaces
- Vocabulary does not redefine merged execution behavior

---

## V1 Parity Requirements

Aligned with ADR-013, this contract preserves:

- Composite scope outcomes
- Floor scope outcomes
- Merged-room discoverability
- Household-recognizable room naming

Implementation may change.

Outcomes may not regress.

---

## Contract Coverage Review

### What Remains In Existing Contracts

`docs/contracts/room-awareness-contract.md` remains authoritative for:

- room truth boundaries
- room environment model boundaries
- room posture interaction suppression boundaries

`docs/contracts/concierge-scope-contract.md` remains authoritative for:

- scope inheritance precedence rules
- room, floor, and concierge policy-resolution rules
- execution and policy scope boundaries

`docs/contracts/composite-room-contract.md` remains authoritative for:

- composite structure and lifecycle
- membership, inventory aggregation, and execution behavior
- composite interaction-space runtime behavior

`docs/contracts/room-interaction-contract.md` remains authoritative for:

- room/composite interaction orchestration behavior
- What Can I Do Here projection behavior
- deterministic interaction execution and explainability boundaries

### What Now Belongs To Room Vocabulary Registry Contract

This contract is now authoritative for:

- vocabulary definitions and category boundaries
- alias governance boundaries
- naming governance and accepted household terminology
- discovery vocabulary governance
- scope vocabulary governance language
- merged and composite vocabulary terminology governance
- vocabulary-specific explainability and determinism requirements

Duplication prevention rule:

- runtime behavior and truth ownership stay in existing contracts
- vocabulary governance and vocabulary resolution language stay in this contract

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

- Foundation remains authoritative for room, area, floor, and occupancy truth
- Vocabulary Registry is authoritative for governed room vocabulary definitions and aliases
- Coordinator V2 consumes vocabulary and remains orchestration-only
- Capability and Experience projections consume vocabulary and do not become vocabulary authorities

---

## Terminology Alignment

Canonical terminology in this contract:

- Room
- Area
- Floor
- Composite Room
- Merged Room
- Room Vocabulary
- Room Alias
- Scope Vocabulary
- Context
- Capability
- Experience
- Explainability
- Determinism

Legacy assumptions that imply hidden runtime remapping or ownership transfer are prohibited.

---

## Final Principle

Room Vocabulary Registry governs how households name and reference space.

It must preserve flexibility, determinism, explainability, and ownership safety.

It must never replace room truth authority.
