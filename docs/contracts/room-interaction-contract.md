# Room Interaction Contract

## Purpose

This contract defines deterministic interaction behavior for:

- Room interactions
- Merged room interactions
- Composite room interactions
- Floor-scoped interaction defaults

It governs interaction resolution and response behavior only.

It does not redefine source-of-record ownership.

---

## Definition

Room interaction is the runtime decision process that resolves:

- where an interaction is happening
- what interaction context applies
- which capabilities are available in that context
- how the response is delivered deterministically

Interaction context is resolved from governed room and presence truth before intent execution.

---

## Ownership And Source-Of-Record Boundaries

| Domain | Source Of Record | Room Interaction Role |
|---|---|---|
| Room, area, floor, occupancy, presence truth | Foundation | Consume for deterministic context resolution |
| Attribution and confidence | Voice Identity | Consume for interaction style and confidence handling |
| Capability significance and environmental interpretation | Asset Intelligence | Consume capability outcomes and room relevance |
| Runtime interaction orchestration | Concierge Coordinator V2 | Resolve and route interactions under governed contracts |

Room Interaction must not transfer ownership from any source-of-record owner to Coordinator V2.

---

## Room Interaction

Room interaction applies when a single Home Assistant area is the resolved interaction space.

Rules:

- `area_id` is the room identity anchor
- room posture is the local interaction suppression authority
- room overrides resolve before floor and concierge defaults
- room interaction behavior must be explainable in machine and human form

Room interaction must remain deterministic across voice and UI for the same resolved context.

---

## Merged And Composite Room Interaction

Merged room is an allowed user-facing term for Composite Room.

Composite interaction rules:

- member areas must be explicitly configured
- context resolves to one composite interaction space when any member area invokes
- interaction visibility and execution target the composite context, not individual member divergence
- membership changes must deterministically recalculate inventory and remove stale references

Merged and composite interaction must be projection behavior only and must not alter physical room truth.

---

## Floor Interaction Defaults

Floor interaction defaults are used when room overrides are not present.

Floor defaults may define:

- shared interaction infrastructure routing
- floor posture defaults
- floor media and climate interaction defaults

Resolution precedence:

1. room override
2. floor default
3. concierge-wide default

Floor defaults must never override explicit room posture for that room.

---

## What Can I Do Here Surface

The "What Can I Do Here" surface must be context-scoped and deterministic.

Rules:

- listed actions must be executable through governed service contracts
- listed actions must reflect resolved room or composite capability availability
- unavailable actions must be omitted or marked unavailable with explainable reason
- responses must be consistent across voice and UI for the same context and policy state

This surface is a projection of available capability contracts, not a new source of capability truth.

---

## Intent Boundaries

Room interaction orchestration may:

- resolve context
- select eligible capabilities
- route intent to governed service interfaces
- request concise clarification for low-confidence context

Room interaction orchestration must not:

- invent capability state
- bypass service contracts
- mutate source-of-record state outside explicit service calls
- hide unresolved context ambiguity

Intent handling must preserve context-before-intent execution posture.

---

## Merged-Room Voice Determinism

When voice is invoked from any member area of an enabled composite:

- the same merged interaction context must resolve every time
- responder election and response policy must remain deterministic
- follow-up interaction must retain the active merged interaction space until closure or explicit context change

Low-confidence room attribution must trigger concise clarification rather than hidden room guessing.

---

## V1 Parity And Non-Regression

Room interaction changes must preserve household-facing outcome continuity for Concierge V1 capabilities.

Parity rules:

- no regressions in room-scoped interaction reliability
- no regressions in merged-room response consistency
- no regressions in explainability of context resolution and suppression behavior

Implementation updates may change internals but must preserve governed outcomes.

---

## Explainability Requirements

### Machine Explainability

Room interaction decisions must expose structured explainability fields:

- resolved interaction space (`area_id` or `composite_id`)
- confidence and reason codes
- applied scope precedence (room, floor, concierge)
- applied suppression or policy gates

### Human Explainability

Room interaction must provide concise human-readable rationale for:

- why this room or composite context was selected
- why an action is available or unavailable
- why an interaction was suppressed, clarified, or delivered

Explainability must be available without exposing internal implementation details.

---

## Determinism Requirements

For identical governed inputs, room interaction outputs must be identical across runs.

Determinism applies to:

- context resolution
- capability projection
- responder election
- suppression and delivery channel behavior

Runtime discovery, hidden inference, and nondeterministic fallback are out of scope.

---

## Non-Rights

This contract does not grant room interaction orchestration the right to:

- redefine room, floor, occupancy, or presence truth
- redefine attribution or confidence truth
- redefine capability ownership
- create autonomous state mutation paths outside governed service contracts
- create policy behavior that is not explainable and auditable

---

## Relationship Notes

This contract composes with:

- `docs/contracts/room-awareness-contract.md`
- `docs/contracts/composite-room-contract.md`
- `docs/contracts/concierge-scope-contract.md`
- `docs/contracts/service-contracts.md`
- `docs/contracts/concierge-contract.md`
- `docs/models/room-model.md`
- `docs/models/interaction-model.md`

This contract does not replace those documents and must remain aligned with their authoritative boundaries.

---

## Contract Coverage Review

| Coverage Domain | Included | Notes |
|---|---|---|
| Room interaction definition and boundary | yes | Explicit room context and scope precedence rules |
| Merged/composite interaction behavior | yes | Deterministic merged context and membership recalculation rules |
| Floor interaction defaults | yes | Floor defaults with room-first override protection |
| What Can I Do Here interaction projection | yes | Deterministic, contract-backed capability surface |
| Intent boundary and non-rights | yes | Explicit orchestration rights and prohibited behavior |
| Explainability and determinism | yes | Machine and human explainability with deterministic guarantees |
| V1 parity and non-regression expectations | yes | Household-facing outcome continuity preserved |

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract consumes governance and does not redefine governance authority.

---

## Ownership Boundary Validation

Ownership constraints preserved by this contract:

- Foundation remains authoritative for room, area, floor, occupancy, and presence truth
- Voice Identity remains authoritative for attribution and confidence outputs
- Asset Intelligence remains authoritative for significance and environmental interpretation
- Coordinator V2 remains orchestration-only and does not become a system of record

---

## Terminology Alignment

Canonical terminology in this contract:

- Room
- Area
- Floor
- Composite Room
- Interaction Space
- Occupancy
- Presence
- Attribution
- Confidence
- Capability
- Context
- Scope

Legacy V1 assumptions that imply hidden runtime room inference or ownership transfer are prohibited.

---

## Final Principle

Room interaction must be deterministic, explainable, and ownership-safe.

It must always resolve context first, then execute intent through governed service boundaries.
