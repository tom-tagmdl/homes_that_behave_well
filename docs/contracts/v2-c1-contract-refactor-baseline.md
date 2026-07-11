# V2-C1 Contract Refactor Baseline

## Status

Accepted for E1 baseline use.

## Purpose

This artifact records the V2-C1 contract refactor baseline for Concierge-related contracts.

It documents:

- contract-by-contract gap analysis
- remediation decisions executed in V2-C1
- ownership and terminology validation outcomes
- E0 governance consumption coverage

## Grounding Scope

Authority order consumed before refactoring:

1. ADRs
2. Contracts
3. Models
4. Architecture and existing implementation documents
5. GitHub Issue #26 (read last)

E0 governance artifacts consumed:

- ADR-004 through ADR-013
- HACS and Platinum Governance Standard

## Contract-By-Contract Gap Analysis And Remediation

| Contract | Identified Gaps | Remediation Executed |
|---|---|---|
| docs/contracts/concierge-contract.md | missing explicit E0 governance consumption section, missing normalized ownership validation summary, terminology normalization needed for V2 concepts | added V2 Governance Consumption, Ownership Boundary Validation, and Terminology Alignment sections; clarified prohibition on legacy V1 ownership assumptions |
| docs/contracts/concierge-scope-contract.md | missing explicit governance consumption statement, ownership constraints implicit, terminology normalization needed for scope terms | added governance consumption, ownership validation, and terminology alignment sections with explicit Coordinator and source-of-record boundaries |
| docs/contracts/concierge-global-context-contract.md | ownership boundaries present but governance references incomplete; terminology alignment not explicit | added governance consumption, ownership validation, and terminology alignment sections; clarified prohibition on Concierge-owned context truth |
| docs/contracts/room-awareness-contract.md | room-truth ownership boundary needed stronger explicit statement; governance references missing | added governance consumption, ownership validation, and terminology alignment sections with explicit Foundation room-truth authority |
| docs/contracts/composite-room-contract.md | governance and ownership boundaries not explicitly tied to E0 set; terminology normalization needed | added governance consumption, ownership validation, and terminology alignment sections; clarified Composite Room as orchestration projection, not room-truth authority |
| docs/contracts/person-identity-contract.md | identity ownership boundaries directionally present but governance mapping incomplete | added governance consumption, ownership validation, and terminology alignment sections; reinforced Voice Identity ownership of attribution and confidence |
| docs/contracts/service-contracts.md | cross-cutting governance alignment was implicit; terminology alignment and ownership validation missing as dedicated sections | added V2 Governance Consumption, Ownership Boundary Validation, and Terminology Alignment sections at contract baseline level |
| docs/contracts/performance-contract.md | governance dependency and ownership preservation not explicitly surfaced | added governance consumption, ownership validation, and terminology alignment sections; reinforced no runtime ownership bypass via optimization |
| docs/contracts/concierge-signal-contract.md | governance mapping and ownership validation needed explicit statements | added governance consumption, ownership validation, and terminology alignment sections; reinforced provider-owned signal truth |
| docs/contracts/concierge-global-config-contract.md | governance mapping and ownership boundaries needed explicit normalization | added governance consumption, ownership validation, and terminology alignment sections; reinforced policy configuration boundary vs source-of-record ownership |

## Ownership Conflict Review

Validated constraints across the updated contract set:

- Foundation ownership preserved for room truth, area truth, device truth, and occupancy truth
- Voice Identity ownership preserved for attribution and confidence
- Asset Intelligence ownership preserved for significance and environmental interpretation
- Coordinator V2 remains orchestration-only and does not gain source-of-record ownership

Ownership conflicts found during V2-C1 review:

- none remaining after refactor pass

## Terminology Alignment Review

Canonical terminology normalized across contract updates:

- Room
- Area
- Floor
- Composite Room
- Vocabulary
- Capability
- Experience
- Personalization
- Household Memory
- Provenance
- Occupancy
- Presence
- Attribution
- Confidence
- Context
- Scope

Terminology normalization outcome:

- legacy V1 phrasing that implied hidden inference ownership or Coordinator ownership drift is explicitly prohibited in updated contracts

## Contract Coverage Matrix

| Contract | V2 Concepts Covered | Ownership Validated | Terminology Validated | Updated |
|---|---|---|---|---|
| docs/contracts/concierge-contract.md | Coordinator V2, Room Vocabulary, Capability Projection, Experience, Personalization, Household Memory, Productivity Experiences, Provenance, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/concierge-scope-contract.md | Coordinator V2, Room Vocabulary, Capability Projection, Experience, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/concierge-global-context-contract.md | Capability Projection, Experience, Productivity Experiences, Provenance, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/room-awareness-contract.md | Coordinator V2, Room Vocabulary, Experience, Provenance, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/composite-room-contract.md | Coordinator V2, Room Vocabulary, Capability Projection, Experience, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/person-identity-contract.md | Coordinator V2, Experience, Personalization, Household Memory, Productivity Experiences, Provenance, Occupancy, Presence, HACS, Platinum | yes | yes | yes |
| docs/contracts/service-contracts.md | Coordinator V2, Room Vocabulary, Capability Projection, Experience, Personalization, Household Memory, Productivity Experiences, Provenance, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/performance-contract.md | Coordinator V2, Capability Projection, Experience, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/concierge-signal-contract.md | Capability Projection, Experience, Household Memory, Productivity Experiences, Provenance, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |
| docs/contracts/concierge-global-config-contract.md | Coordinator V2, Capability Projection, Experience, Personalization, Productivity Experiences, Occupancy, Presence, V1 Preservation, HACS, Platinum | yes | yes | yes |

## Validation Against E0 Governance

All listed contracts were reviewed and refactored to consume E0 governance where architecturally applicable.

No contract in this pass introduces new governance authority or redefines E0 artifacts.

## Follow-On E1 Recommendations

1. Add explicit cross-links from each contract to specific models consumed in E2 for schema-level traceability.
2. Add a contract terminology glossary appendix to reduce drift during E1 follow-on issues.
3. Introduce contract lint checks for ownership-boundary language and prohibited ownership-transfer phrases.
4. Add structured acceptance checklists per contract for E1 closure reviews.

