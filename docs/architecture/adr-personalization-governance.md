# ADR: Personalization Governance Boundaries

## ADR Number

ADR-008

## Status

Accepted.

## Context

Personalization is a governed architectural concern in Homes That Behave Well.

Personalization affects messaging style, continuity behavior, affinity weighting, restoration behavior, and person-aware experience adaptation.

Without explicit governance boundaries, personalization can drift into hidden behavior changes, governance override, or unauthorized authority transfer into runtime orchestration.

This ADR establishes architecture authority for personalization governance across contracts, models, projections, coordinators, and implementations.

## Decision

### Personalization Definition

Personalization is:

A governed adaptation of household interactions using approved person-aware context while preserving safety, consent, explainability, and reversibility.

Personalization is NOT:

- identity ownership
- profile ownership
- governance ownership
- hidden learning
- hidden behavior modification
- source-of-record ownership

### Personalization Boundary Table

| Concern | Owner | Personalization Relationship |
|---|---|---|
| person profile | profile models and governed profile policy | consumed as governed profile context |
| identity attribution | Voice Identity | consumed as confidence-aware attribution input |
| continuity | Concierge runtime behavior under governed policy | consumed as bounded interaction continuity signal |
| affinity | governed preference weighting policy and signals | consumed as preference weighting input |
| messaging style | Concierge interaction behavior under governed contracts and profile policy | adapted when policy and consent allow |
| restoration preferences | governed restoration policy and user preferences | consumed as restoration guidance input |
| experience preferences | governed experience policy and person preference signals | consumed for experience personalization eligibility |
| household memory | governed household memory policy and approved data surfaces | consumed as bounded personalization context |
| consent state | governed consent lifecycle policy and profile consent state | required gate for personalization behavior |
| personalization policy | HTBW governance through ADRs, contracts, and models | defines allowed adaptation boundaries |

Ownership principles:

- Voice Identity owns attribution.
- Profile models own profile structure.
- HTBW owns governance.
- Coordinator consumes governed personalization signals.
- Coordinator does not own personalization authority.

### Profile Vs Continuity Vs Affinity

Person Profile:

- who the person is
- profile facts
- profile preferences
- governed profile information

Continuity:

- conversation continuity
- interaction continuity
- session continuity
- context continuity

Affinity:

- learned preference weighting
- presentation preferences
- experience preference signals

Required separations:

- Profile does not equal Continuity.
- Profile does not equal Affinity.
- Continuity does not equal Affinity.

These concepts are related but independently governed.

### Messaging Personalization Boundaries

Personalization may influence:

- tone
- greeting style
- formality level
- preferred phrasing

Personalization must not influence:

- factual truth
- room truth
- identity confidence
- capability availability
- source-of-record boundaries

Messaging personalization must remain explainable and reversible.

### Restoration Personalization Boundaries

Personalization may influence:

- restoration preferences
- room restoration candidates
- experience restoration candidates

Prohibited:

- hidden restoration behavior
- non-explainable restoration decisions
- restoration without policy boundaries

### Consent And Reversal Requirements

Personalization requires explicit consent and reversible controls.

Required controls:

- opt-in requirements
- opt-out requirements
- temporary disablement
- permanent disablement
- preference reset
- affinity reset
- continuity reset where appropriate

Personalization must always be reversible.

Users must be able to return to neutral behavior.

### Guest And Unknown User Safe Defaults

Required safe defaults for:

- Guest
- Unknown User
- Low-Confidence Attribution
- No Attribution Available

Defaults must be:

- safe
- minimally personalized
- deterministic
- explainable

Guest behavior must never assume private preferences.

Unknown-user behavior must default to neutral experience.

### Policy Constraints

Personalization must not:

- override governance
- override contracts
- override source-of-record ownership
- override safety requirements
- create hidden authority

### Determinism Requirements

Personalization determinism requires:

- same governed inputs produce same personalization outcome
- same profile state produces same personalization response
- same policy state produces same behavior

Prohibited:

- hidden behavior changes
- hidden preference changes
- hidden personalization paths

### Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- personalization source
- profile inputs used
- continuity inputs used
- affinity inputs used
- consent state
- confidence level
- timestamps

Human explainability outputs must include:

- why personalization occurred
- why personalization did not occur
- why personalization was restricted
- why guest-safe mode was used
- why neutral mode was used

### Source-Of-Record Boundaries

Voice Identity remains authority for attribution.

Profile models remain authority for profile structure.

Systems of record remain authoritative.

Coordinator consumes governed personalization context.

Coordinator does not become personalization authority.

Personalization is not a source of record.

## Consequences

Positive outcomes:

- establishes architecture authority for personalization governance boundaries
- prevents hidden personalization and authority drift into runtime orchestration
- enforces consent-aware, reversible, deterministic person-aware behavior
- provides explicit guest-safe and unknown-user behavior constraints

Tradeoffs:

- requires stricter policy and explainability validation for personalization changes
- requires explicit reset and reversal handling for continuity and affinity paths

## Rejected Alternatives

### 1. Coordinator-owned personalization governance

Rejected because Coordinator is a consumer and orchestrator, not a governance authority.

### 2. Hidden personalization learning

Rejected because hidden learning violates explainability, consent, and reversibility requirements.

### 3. Affinity overriding governance

Rejected because affinity weighting must remain bounded by governed policy and safety constraints.

### 4. Continuity overriding identity confidence

Rejected because continuity is a context signal and cannot replace attribution confidence authority.

### 5. Personalized behavior without consent

Rejected because personalization requires explicit and revocable consent.

### 6. Personalized behavior for guests by default

Rejected because guest-safe defaults must remain minimally personalized and privacy-preserving.
