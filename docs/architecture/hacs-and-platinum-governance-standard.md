# Architecture Governance Standard: HACS and Platinum Governance Gates

## Status

Accepted.

## Purpose

This standard defines continuous architecture governance gates for HACS compliance and Home Assistant Platinum readiness across the HTBW platform roadmap.

This is a governance standard.

This is not an implementation specification.

## Artifact Type Decision

Selected artifact type: Architecture Governance Standard.

Rationale:

- this artifact defines continuous cross-cutting governance gates across all roadmap phases
- this artifact governs architecture, contracts, models, implementation verification, release readiness, and maintenance closure behavior
- this artifact is consumed by multiple epics and repositories as a reusable gate framework

Not selected:

- ADR: ADRs remain authoritative for bounded architecture decisions and ownership boundaries
- Architecture Governance Note: a note is advisory and does not provide sufficient governance framing for continuous closure gating across the platform

## Governance Scope

This governance applies to:

- architecture
- contracts
- models
- implementations
- documentation
- diagnostics
- repairability
- translations
- accessibility
- testing
- upgrades
- release readiness

This standard defines requirements, evidence expectations, and closure gates only.

## Required Governance Domains

The following governance domains are mandatory:

1. Diagnostics
2. Repairs
3. Translations
4. Accessibility
5. Testing
6. Configuration Flows
7. Options Flows
8. Documentation
9. Release Readiness
10. Upgradeability

## HTBW Domain Coverage Governance Matrix

All listed HTBW domains are mandatory consumers of this governance standard.

| Domain | Governance Expectation | Gate Consumption |
|---|---|---|
| Calendar | diagnostics, translation, accessibility, testing, and upgrade evidence must be demonstrable for calendar outcomes | planning, implementation, closure |
| Email | diagnostics, repairability, translation, accessibility, and release evidence must be demonstrable for email outcomes | planning, implementation, closure |
| Tasks | config/options quality, diagnostics, testing, and upgrade evidence must be demonstrable for task outcomes | planning, implementation, closure |
| Shopping | config/options quality, diagnostics, testing, and upgrade evidence must be demonstrable for shopping outcomes | planning, implementation, closure |
| Multi-Item Voice Capture | determinism-safe diagnostics, repair guidance, testing rigor, and explainability-supporting documentation evidence must be demonstrable | planning, implementation, closure |
| Knowledge | diagnostics, testing, accessibility, and documentation evidence must be demonstrable for knowledge outcomes | planning, implementation, closure |
| Briefing | diagnostics, translation, accessibility, testing, and release evidence must be demonstrable for briefing outcomes | planning, implementation, closure |
| Household Status Synthesis | diagnostics, testing, documentation, and upgrade evidence must be demonstrable for synthesis outcomes | planning, implementation, closure |
| Provenance | diagnostics, testing, documentation, and upgrade evidence must be demonstrable for provenance trust outputs | planning, implementation, closure |
| Occupancy | diagnostics, testing, documentation, and upgrade evidence must be demonstrable for occupancy governance outcomes | planning, implementation, closure |
| Presence | diagnostics, testing, documentation, and upgrade evidence must be demonstrable for presence governance outcomes | planning, implementation, closure |
| Coordination | diagnostics, repairs, testing, accessibility, documentation, release, and upgrade evidence must be demonstrable for coordinator outcomes | planning, implementation, closure |

## Phase-To-Gate Matrix

| Phase | Diagnostics | Repairs | Translation | Accessibility | Testing | Config | Options | Documentation | Release | Upgrade |
|---|---|---|---|---|---|---|---|---|---|---|
| Architecture | define diagnostic responsibilities and sanitization boundaries | define recoverability and failure-handling boundaries | define localization expectations for user-facing architecture outputs | define architecture accessibility expectations for user-facing behavior surfaces | define architecture-level testability expectations and determinism assertions | define architecture requirements for config-flow governance boundaries | define architecture requirements for options-flow governance boundaries | define authoritative architecture documentation requirements | define architecture-level release gate criteria and compliance expectations | define architecture-level upgrade-safety constraints and compatibility expectations |
| Contract | specify diagnostics surfaces and required outputs in contracts | specify repair or actionable remediation boundaries in contracts | specify translation-facing contract fields and stability expectations | specify accessibility-relevant contract expectations for user-facing channels | specify contract validation and regression evidence expectations | specify contract requirements for config-flow behavior and failure handling | specify contract requirements for options-flow behavior and failure handling | specify contract documentation completeness and change tracking requirements | specify release-sensitive contract change governance and version impact expectations | specify upgrade-safe contract evolution expectations |
| Model | define model fields needed for diagnostics lineage and traceability | define model fields that support repair decisions and remediation explainability | define model structures needed for translation-safe user-facing values | define model support for accessibility-friendly rendering and messaging | define model-level validation and regression expectations | define model support for configuration-state consistency | define model support for options-state consistency | define model documentation and semantic definition completeness requirements | define release governance for model-change impact visibility | define upgrade governance for model evolution and compatibility |
| Implementation | expose required diagnostics and sanitize sensitive data | expose actionable repair pathways where recoverable issues exist | provide translation inventories for user-facing strings | satisfy accessibility readiness expectations for user-facing surfaces | provide automated and scenario-based verification evidence | implement governed configuration flow behavior | implement governed options flow behavior | maintain user and maintainer documentation quality and completeness | satisfy release-readiness gates before distribution | satisfy upgrade-safety gates and migration safety checks |
| Integration | validate integration diagnostics availability and quality | validate integration repair behavior and guidance quality | validate integration translation readiness and key coverage | validate integration accessibility behavior in user-facing paths | validate integration test coverage and regression quality | validate integration configuration readiness | validate integration options readiness | validate integration documentation readiness | validate integration release packaging and metadata readiness | validate integration upgrade and rollback safety behavior |
| Verification | review diagnostics evidence and sanitize conformance | review repair evidence and recoverability conformance | review translation coverage and quality evidence | review accessibility evidence and issue closure status | review test evidence, regressions, and deterministic behavior outcomes | review config-flow conformance evidence | review options-flow conformance evidence | review documentation evidence and completeness | review release evidence and governance sign-off readiness | review upgrade evidence and safety sign-off readiness |
| Release | publish diagnostics and supportability references | publish repair guidance for expected recoverable failures | publish translation status and user-facing language coverage notes | publish accessibility status and known constraints | publish verification and regression summary | publish configuration behavior notes and constraints | publish options behavior notes and constraints | publish release notes and operational guidance | complete release governance checks before artifact publication | publish upgrade notes, compatibility changes, and rollback guidance |
| Maintenance | retain diagnostics quality and privacy-safe output over time | retain actionable repair pathways and update guidance as needed | retain translation quality as strings evolve | retain accessibility quality as surfaces evolve | retain regression coverage and evidence quality over time | retain config-flow integrity through updates | retain options-flow integrity through updates | retain documentation freshness and governance alignment | retain release governance compliance in subsequent versions | retain upgrade safety and compatibility through subsequent versions |

## Platinum Governance Matrix

This matrix is the authoritative closure framework.

| Governance Area | Requirement | Evidence Required | Closure Gate |
|---|---|---|---|
| Diagnostics | diagnostics must be available, sanitized, and useful for supportability | diagnostics output samples, sanitization review artifacts, diagnostics documentation | fail if diagnostics are missing, unsafe, or non-actionable |
| Repairs | recoverable failures must provide actionable repair guidance | repair-flow documentation, issue examples, remediation validation evidence | fail if recoverable failure paths lack actionable repair guidance |
| Translation | user-facing text must have translation readiness and key inventory discipline | translation inventories, locale key coverage reports, review notes | fail if translation readiness is absent for user-facing surfaces |
| Accessibility | user-facing paths must align with accessibility expectations and platform norms | accessibility validation artifacts, issue-tracking evidence, remediation notes | fail if accessibility evidence is missing or unresolved critical barriers remain |
| Testing | deterministic behavior and regression-sensitive paths must be verified | test results, scenario verification reports, regression summaries | fail if testing evidence is insufficient for affected governance domains |
| Documentation | architecture, user, and maintainer docs must be complete and current | documentation inventory, release notes, operational guides | fail if documentation is incomplete for changed behavior or gate domains |
| Releases | release readiness must satisfy HACS and governance quality expectations | validation reports, metadata verification, release readiness checklist | fail if release readiness evidence is incomplete or invalid |
| Upgradeability | upgrade paths must preserve safety, explainability, and non-regression expectations | upgrade validation reports, compatibility notes, migration and rollback guidance | fail if upgrade safety cannot be demonstrated |

## HACS Governance Requirements

HACS governance expectations:

- installation readiness must be demonstrable
- configuration readiness must be demonstrable
- upgrade safety must be demonstrable
- documentation completeness must be demonstrable
- repairability must be demonstrable
- diagnostics exposure must be demonstrable and sanitized

This section defines governance requirements only.

This section does not define implementation patterns.

## Platinum Governance Requirements

Platinum governance is consumed from [docs/architecture/platinum-target-checklist.md](platinum-target-checklist.md).

Required governance expectations include:

- diagnostics quality
- user supportability
- repairability
- accessibility
- translation readiness
- testing rigor
- release governance

This standard does not redefine Platinum.

This standard consumes and operationalizes repository Platinum governance expectations.

## Cross-Repo Applicability

This governance standard applies across HTBW repositories:

- homes_that_behave_well
- concierge
- voice_identity
- asset_intelligence
- future HTBW repositories

This artifact is reusable and is the shared governance baseline for cross-repo gate evaluation.

## Epic Consumer Mapping

The following epics consume this governance for planning, implementation, and closure gates.

| Epic | Planning Gate Consumption | Implementation Gate Consumption | Closure Gate Consumption |
|---|---|---|---|
| E12 | must include this governance framework as required planning input | must implement and evidence applicable HACS and Platinum gates | may not close without demonstrated compliance against gate framework |
| E1 | must align contract planning with governance domains | must evidence diagnostics, repairability, testing, and documentation gates in contract work | may not close without governance-domain evidence for affected contract scope |
| E2 | must align model planning with governance domains | must evidence diagnostics lineage, testability, and upgrade-safety gates in model work | may not close without governance-domain evidence for affected model scope |
| E3 | must include gate framework in planning assumptions | must evidence applicable domain gates for implementation scope | may not close without gate compliance evidence |
| E3a | must consume this framework for parity and readiness planning | must evidence applicable gates for parity validation work | may not close without gate compliance evidence |
| E4 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E5 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E6 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E7 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E8 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E8a | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E9 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E10 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E13 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |
| E14 | must include governance-domain planning expectations | must evidence applicable implementation gates | may not close without gate compliance evidence |

This mapping defines governance consumption only.

This mapping does not define execution plans.

## E12 Governance Dependency

E12 must consume this governance artifact.

E12 may not be considered complete without demonstrating compliance to this gate framework.

If no dedicated E12 planning artifact exists, canonical architecture must include explicit dependency references to this governance standard for E12 planning and E12 closure evaluation.

## Evidence Requirements

For each gate domain, accepted evidence types are defined below.

| Gate Domain | Accepted Evidence Types |
|---|---|
| Diagnostics | diagnostics output samples, sanitized diagnostics payload examples, diagnostics documentation |
| Repairs | repair guidance documentation, remediation verification artifacts, issue-resolution evidence |
| Translations | translation inventories, locale key coverage reports, translation review artifacts |
| Accessibility | accessibility validation artifacts, remediation issue logs, accessibility review summaries |
| Testing | automated test results, scenario verification reports, regression summaries |
| Configuration Flows | configuration-flow validation reports, setup behavior documentation, error-handling verification artifacts |
| Options Flows | options-flow validation reports, options behavior documentation, error-handling verification artifacts |
| Documentation | architecture docs, user docs, maintainer docs, release notes, operational guidance |
| Release Readiness | validation reports, packaging and metadata verification artifacts, readiness checklists |
| Upgradeability | upgrade validation reports, compatibility notes, migration guidance, rollback guidance |

This section does not prescribe CI/CD implementation.

## Non-Rights

This governance artifact does NOT:

- mandate implementation patterns
- mandate specific tools
- redefine architecture ownership
- redefine ADR authority
- redefine contract authority
- redefine model authority

This artifact governs readiness and quality expectations only.
