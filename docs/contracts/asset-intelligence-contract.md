# Asset Intelligence Contract

## Purpose

Asset Intelligence is the authoritative system for managing assets, environments, and risk evaluation.

It is the system of record and decision engine for all asset-related logic.

This document defines what Asset Intelligence is allowed to do, and what it must never do.

---

## Core Responsibility

Asset Intelligence owns:

- Asset records and metadata
- Environment requirements for each asset
- Room environment configuration
- Risk evaluation
- Validation of all updates
- Persistence of all asset state
- Audit and event history

---

## System Role

Asset Intelligence is responsible for:

- Receiving validated service calls
- Updating the system of record
- Evaluating asset risk deterministically
- Producing advisory signals
- Exposing clean, structured services for other integrations

---

## Data Ownership Rules

Asset Intelligence is the only component that may:

- Create or modify asset records
- Store environment requirements
- Persist room configuration
- Record environmental history
- Maintain audit logs

No other system may write directly to asset data.

---

## Service Boundary

All mutations must go through services.

Required pattern:

Service call -> Validation -> Store write -> Coordinator refresh

No component may bypass this flow.

---

## Validation Rules

All incoming data must be validated before persistence.

Validation must ensure:

- Required fields are present
- Values are within allowed ranges
- Data shapes match the defined schema
- Invalid inputs are rejected early

Validation failures must:

- Stop execution
- Return clear error messages
- Never partially write data

---

## Evaluation Rules

Evaluation must always be:

- Deterministic
- Repeatable
- Explainable

Evaluation must never:

- use randomness
- rely on incomplete assumptions
- produce different outputs for identical inputs

All results must include:

- risk state
- supporting reasons
- evaluation timestamp

---

## Advisory Behavior

Asset Intelligence may produce advisory recommendations.

Advisory output must:

- never mutate the system directly
- be clearly separated from risk evaluation
- include explanation of reasoning

Advisory signals are optional guidance, not decisions.

---

## AI Integration Rules

AI must be strictly controlled and bounded.

AI may:

- generate suggested environment requirements
- summarize asset or environment state
- provide explanations for recommendations

AI may not:

- write directly to the system of record
- bypass validation logic
- change asset state without a service call

All AI output must:

- be validated before use
- be explainable
- be auditable

---

## Allowed Integration Behavior

Other integrations (such as Concierge) may:

- read asset data through exposed interfaces
- request updates via services
- request recommendations

Other integrations may not:

- write directly to the store
- perform evaluation logic
- override validation

---

## Coordinator Responsibility

The coordinator is responsible for runtime behavior.

The coordinator must:

- evaluate all assets in a shared room context
- apply deterministic logic
- generate events when state changes
- maintain in-memory projections for entities

The coordinator must not:

- perform validation logic
- define business rules
- access UI or interaction layers directly

---

## Store Responsibility

The store is the system of record.

The store must:

- persist all asset and environment data
- maintain audit history
- enforce schema consistency
- provide safe read and write access

The store must not:

- perform evaluation
- make decisions
- read Home Assistant state directly

---

## Entity Rules

Entities are projections only.

Entities must:

- read from coordinator data
- expose current state
- remain lightweight

Entities must not:

- perform evaluation
- persist data
- contain large history payloads
- perform input or output operations

---

## Failure Handling

The system must fail safely.

If data is invalid or incomplete:

- reject the operation
- preserve existing state
- return a clear error

The system must never:

- partially update state
- silently ignore invalid input
- produce undefined behavior

---

## Final Principle

Asset Intelligence is the authority on asset state.

If a capability involves:

- asset data
- environment requirements
- risk evaluation

It must be implemented in Asset Intelligence.

No other component may assume or replicate this role.