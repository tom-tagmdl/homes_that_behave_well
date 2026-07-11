# ADR: Concierge V1 Household-Facing Outcome Preservation Governance

## ADR Number

ADR-013

## Status

Accepted.

## Context

Concierge V2 is allowed to refactor and replace implementation internals.

Concierge V2 must preserve foundational Concierge V1 household-facing outcomes.

This artifact defines non-regression governance for V1 outcome preservation and establishes the authoritative E3a readiness gate.

This ADR preserves outcomes, not implementation.

## Decision

### Artifact Type Decision

ADR selected.

Rationale:

- this decision sets cross-domain governance boundaries, not localized implementation guidance
- this decision establishes a mandatory epic closure gate (E3a), which requires authoritative ADR-level weight
- this decision defines durable non-regression policy expected to govern downstream contracts, models, and runtime behavior

An architecture note is not sufficient because the scope is governance authority and closure gating, not advisory runtime detail.

### Household-Facing Outcome Principle

Outcome Preservation is required.

Implementation Preservation is not required.

Governing question:

Can the household still achieve the same outcome?

Non-governing question:

Does it work the same internally?

### V1 Preservation Clusters

The following clusters define required V1 household-facing outcome preservation expectations.

#### 1. Composite / Floor Scope Behavior

Covered scopes:

- room scope
- area scope
- floor scope
- composite scope

Preservation requirements:

- scope-aware household behavior must remain available and deterministic
- composite and floor-level household outcomes must remain achievable
- scope selection must remain explainable

Implementation may change.

Outcome behavior may not regress.

This cluster defines outcome governance only and does not define implementation details.

#### 2. Merge / Unmerge Lifecycle

Covered lifecycle concerns:

- room merge
- room unmerge
- merged occupancy context
- merged interaction context
- merged execution behavior

Preservation requirements:

- merge lifecycle transitions must preserve expected household behavior continuity
- unmerge lifecycle transitions must preserve expected household behavior continuity
- merged-context behavior and unmerged-context behavior must remain deterministic and explainable

Implementation may change.

Lifecycle outcomes may not regress.

#### 3. Merged-Room Voice Determinism

Covered behavior:

- duplicate listeners
- merged-room interactions
- responder election
- deterministic responder selection
- conversation continuity

Preservation requirements:

- merged-room voice behavior remains deterministic
- responder election remains deterministic for equivalent governed inputs
- conversation continuity remains stable across merged interaction context
- household-facing ambiguity must not increase

#### 4. Execution Hierarchy Parity

Covered hierarchy:

- local execution
- room execution
- area execution
- floor execution
- household execution

Preservation requirements:

- execution hierarchy outcomes must remain available and deterministic
- hierarchy resolution must remain explainable
- hierarchy regression is prohibited

#### 5. Global Context Provider Parity

Covered context domains:

- weather
- environmental context
- occupancy context
- identity context
- household context
- productivity context

Preservation requirements:

- Global Context Provider outcomes required for household awareness must remain available
- context projection and use must remain deterministic and explainable
- provider outcome availability must not regress without explicit governance change

This cluster defines outcome expectations only and does not define implementation details.

### Non-Regression Governance

Regression is any change that prevents the household from achieving a previously governed foundational outcome.

Acceptable refactoring:

- internal code restructuring that preserves required outcomes
- execution-path replacement that preserves required outcomes
- contract and model updates when authorized and outcome-preserving

Acceptable replacement:

- subsystem replacement that preserves required outcomes, determinism, and explainability

Unacceptable outcome loss:

- inability to achieve previously required scope behavior outcomes
- increased ambiguity in merged-room voice outcomes
- hierarchy behavior drift that changes household-visible outcomes
- loss of required global context outcomes

Non-regression is measured by outcome continuity, not internal implementation similarity.

### E3a Readiness Parity Checklist

E3a readiness requires all checklist items to pass.

| Checklist Item | Expected Outcome | Validation Requirement | Pass Criteria |
|---|---|---|---|
| Composite Scope | Household can achieve composite-scope outcomes with deterministic and explainable behavior | Validate composite-scope interaction and execution outcomes under governed inputs | Composite outcome behavior matches governed baseline without increased ambiguity |
| Floor Scope | Household can achieve floor-scope outcomes with deterministic and explainable behavior | Validate floor-scope interaction and execution outcomes under governed inputs | Floor outcome behavior matches governed baseline without scope drift |
| Merge Lifecycle | Household experiences stable behavior continuity through merge transitions | Validate merge transition outcomes for interaction, occupancy context, and execution behavior | Merge transitions preserve governed outcomes and deterministic behavior |
| Unmerge Lifecycle | Household experiences stable behavior continuity through unmerge transitions | Validate unmerge transition outcomes for interaction, occupancy context, and execution behavior | Unmerge transitions preserve governed outcomes and deterministic behavior |
| Merged-Room Voice | Household receives deterministic merged-room voice responses with stable continuity | Validate duplicate-listener scenarios, responder election, and continuation behavior | Deterministic responder outcome is preserved and ambiguity does not increase |
| Execution Hierarchy | Household can achieve outcomes across local/room/area/floor/household hierarchy levels | Validate hierarchy resolution and execution outcome parity for governed scenarios | Hierarchy outcomes are preserved and hierarchy regression is absent |
| Global Context Providers | Household can access required global context outcomes across governed domains | Validate provider-outcome availability and projection behavior across weather/environmental/occupancy/identity/household/productivity domains | Required context outcomes remain available and explainable |
| Determinism | Same governed inputs produce same household-facing outcomes | Validate repeated governed scenarios across scope, merged-room, and hierarchy behavior | Repeat runs produce equivalent outcomes without hidden divergence |
| Explainability | Machine and human rationale are available for key household-facing decisions | Validate rationale payloads for responder, scope, merge-state, and execution-path decisions | Rationale is complete, bounded, and understandable for required decision points |

### Determinism Requirements

Determinism requirements are mandatory:

- same governed inputs produce same household-facing outcome
- same merged-room state produces same responder outcome
- same hierarchy inputs produce same execution outcome

Prohibited:

- increased ambiguity
- non-deterministic responder behavior
- hierarchy drift

### Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- responder rationale
- scope resolution rationale
- merge-state rationale
- execution-path rationale

Human explainability outputs must include:

- why a responder was chosen
- why a scope was selected
- why a merged room responded
- why an execution path was selected

### Non-Rights

This preservation artifact does NOT:

- prevent architectural improvement
- require implementation compatibility
- require API compatibility
- require internal code preservation

This artifact only protects household-facing outcomes.

### Source-Of-Record And Ownership Boundaries

Foundation remains authoritative for room, area, occupancy, and environmental truth.

Voice Identity remains authoritative for attribution confidence.

Provider systems remain authoritative for their domains.

Concierge remains an orchestrator and consumer under governance boundaries.

### E3a Dependency Gate

E3a may not be closed until the parity checklist is satisfied.

The E3a Readiness Parity Checklist is the authoritative E3a readiness gate.

If no E3a planning artifact exists, canonical architecture must include explicit future dependency reference to this ADR for E3a planning.

## Consequences

Positive outcomes:

- formalizes V1 household-facing outcome preservation as enforceable governance
- enables implementation modernization without household-facing regression
- establishes deterministic and explainable non-regression expectations for E3a execution

Tradeoffs:

- requires explicit parity validation evidence during E3a closure
- requires stronger boundary discipline when replacing internal implementation paths

## Rejected Alternatives

### 1. Preserve V1 implementation internals

Rejected because implementation preservation is not the governance objective.

### 2. Define parity as advisory architecture note only

Rejected because E3a closure gating requires authoritative ADR-level governance.

### 3. Allow merged-room responder ambiguity if behavior is mostly acceptable

Rejected because merged-room determinism and ambiguity control are mandatory household-facing requirements.

### 4. Preserve API compatibility as the primary parity definition

Rejected because household-facing outcome continuity is the governing baseline, not API shape continuity.
