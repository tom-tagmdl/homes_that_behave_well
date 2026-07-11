# ADR: Coordinator V2 Governance Boundaries

## ADR Number

ADR-004

## Status

Accepted.

## Context

Coordinator V2 is an orchestration component inside Concierge.

It is a runtime consumer of governed context, not a governance authority.

Without an explicit ADR for Coordinator V2, downstream work risks redefining governance, contracts, models, ownership boundaries, or source-of-record responsibilities in implementation-specific ways.

This ADR establishes authoritative Coordinator V2 governance boundaries for all downstream Coordinator V2 work.

## Decision

Coordinator V2 is formally constrained as a consumer and orchestrator.

Coordinator V2 does not become:

- a platform service
- a governance authority
- a source-of-record authority
- a contract authority
- a model authority

Downstream epics and implementations must consume this ADR and must not redefine Coordinator governance independently.

### Coordinator V2 Envelope

Coordinator V2 decision envelope:

Person + Room + Context + Capabilities + Experience + Intent

| Envelope Component | Represents | Authoritative Source | Coordinator Role |
|---|---|---|---|
| Person | likely actor context and confidence-aware personalization input | Voice Identity attribution outputs, Home Assistant person records, governed profile policy | Consumes |
| Room | active room, area, and interaction-space truth | Foundation room, area, device, occupancy truth | Consumes |
| Context | current household and session context needed for routing and modality | Foundation truth, governed external provider outputs, policy surfaces | Consumes |
| Capabilities | available executable and informational capability set | contracts and provider capability surfaces | Consumes |
| Experience | configured interaction style and continuity behavior | governed experience policy and configured preferences | Consumes |
| Intent | resolved request target and action class | governed intent resolution path and contract-bound interfaces | Consumes |

Coordinator owns none of the envelope sources.

### Decision Rights Table

| Coordinator V2 MAY | Coordinator V2 MAY NOT |
|---|---|
| resolve interaction space | redefine governance |
| resolve conversation ownership | redefine contracts |
| assemble governed context | redefine models |
| select execution path | redefine source-of-record ownership |
| choose response modality | alter Foundation truth |
| choose clarification path | alter Voice Identity ownership |
| perform bounded orchestration | alter Asset Intelligence ownership |
| perform bounded planning | create new platform services |
| perform explainable routing | establish hidden state authorities |

### Determinism Requirements

Coordinator V2 deterministic obligations:

- same governed inputs produce same outcome
- ambiguity handling is bounded and policy-driven
- clarification behavior is explicit and deterministic
- no hidden inference chains
- no governance bypass through runtime shortcuts

Determinism is an architectural requirement because household predictability depends on stable, explainable behavior for repeated situations.

### Explainability Requirements

Explainability is an architectural requirement for Coordinator V2.

Machine explainability outputs must include:

- reason codes
- source lineage
- confidence
- timestamps

Human explainability outputs must include:

- plain-language rationale
- concise execution explanation
- clarification rationale where applicable

### Fail-Safe Boundaries

Coordinator V2 fail-safe behavior must preserve safety, explainability, and deterministic execution for:

- missing context
- conflicting context
- low confidence
- stale information
- unavailable providers
- ambiguous execution targets

Fail-safe behavior requirements:

- choose bounded fallback behavior rather than hidden guessing
- request concise clarification when deterministic resolution is not possible
- degrade to neutral and safe execution posture when confidence is insufficient
- avoid mutating source-of-record ownership in fallback paths
- emit explainable failure or clarification rationale

### Source-Of-Record Boundaries

Source-of-record ownership remains unchanged:

- Foundation owns truth.
- Asset Intelligence owns significance.
- Voice Identity owns attribution.
- External providers own their domains.

Coordinator V2 consumes governed outputs.

Coordinator V2 does not become a system of record.

## Consequences

Positive:

- establishes a single authority for Coordinator V2 governance boundaries
- prevents ownership and governance drift in downstream epics
- improves deterministic and explainable runtime behavior
- creates clear test and review expectations for Coordinator-related changes

Tradeoffs:

- requires stricter boundary validation in design and code review
- constrains ad-hoc runtime behaviors that are not contract-governed

## Rejected Alternatives

### 1. Coordinator as governance authority

Rejected because HTBW owns governance authority; Coordinator is runtime orchestration inside Concierge.

### 2. Coordinator as a fifth platform service

Rejected because platform architecture remains four services: Foundation, Asset Intelligence, Voice Identity, Concierge.

### 3. Coordinator as a system of record

Rejected because source-of-record ownership stays with Foundation, Voice Identity, Asset Intelligence, and external providers.

### 4. Coordinator-driven contract ownership

Rejected because contracts are architecture artifacts owned under HTBW governance, not runtime orchestration components.

### 5. Coordinator-owned identity authority

Rejected because Voice Identity owns attribution and confidence authority.

### 6. Coordinator-owned room truth

Rejected because Foundation owns room, device, and area truth.
