# Performance Contract

## Purpose

The Performance Contract defines the rules and expectations for system responsiveness, execution speed, and runtime efficiency.

It ensures that Concierge operates as a fast, deterministic system and avoids the latency commonly associated with traditional automation approaches.

---

## Core Principle

Performance is achieved through preparation, not optimization.

The system must be configured in advance so that execution requires no decision-making at runtime.

---

## Performance Model

Performance is governed by three phases:

1. Precomputation (configuration and modeling)
2. Resolution (intent and context determination)
3. Execution (action or response)

---

## Performance Requirements

The system must:

- resolve requests quickly and deterministically
- execute actions with minimal latency
- avoid runtime computation whenever possible
- use preconfigured data for all decisions

The system must not:

- perform heavy computation during execution
- rely on runtime discovery
- introduce unnecessary processing layers

---

## No Runtime Discovery Rule

The system must not perform dynamic discovery during execution.

Discovery is allowed at startup or configuration time. Runtime must use precomputed results only.

Prohibited behaviors:

- scanning entities at runtime
- filtering domains dynamically
- inferring relationships during execution
- building mappings on demand

All relationships must be:

- explicitly defined
- stored
- reused

---

## Precomputed Runtime Model

All runtime behavior must be based on a precomputed model.

Example:

room_runtime_model:
  execution_targets:
  audio:
  entity_mappings:
  scene_bindings:

Rules:

- must be built during configuration
- must be reused at runtime
- must not be regenerated per request

---

## Execution Performance

Execution must follow:

- scene → group → entity hierarchy

Rules:

- prefer scene-based execution
- minimize number of service calls
- execute in a single call whenever possible

---

## Single-Call Rule

The system must execute actions in a single service call when possible.

Example:

Preferred:
scene.turn_on(scene.all_shades_closed)

Not permitted:
loop through individual entities for execution

---

## Loop Avoidance Rule

The system must avoid:

- iterative loops over entities
- sequential service calls per device

If entity-level execution is required:

- must batch calls efficiently
- must minimize overhead

---

## Voice Resolution Performance

Voice processing must:

- prioritize alias-based resolution
- prefer direct entity execution
- bypass Concierge when possible

Flow:

Assist → entity match → direct execution

Concierge involvement must be minimal for direct commands.

---

## Concierge Resolution Performance

When Concierge is used:

- intent must be resolved quickly
- context must be predefined
- execution path must already exist

Concierge must not:

- perform extended reasoning for simple commands
- re-evaluate configuration at runtime

---

## Interaction Performance

Interactions must:

- be generated from existing state
- not trigger additional computation
- be lightweight and ephemeral

Rules:

- must not require full system recomputation
- must update only on relevant changes

---

## Signal Performance

Signal retrieval must:

- use precomputed or cached state
- avoid recomputing values per request
- rely on provider integrations

Signals must not:

- require aggregation at runtime
- trigger heavy processing on request

---

## Global Context Performance

Global context retrieval must:

- use efficient integration calls
- support caching where appropriate
- avoid repeated external requests

Summarization (including AI):

- must only occur when requested
- must not block system responsiveness

---

## AI Performance Constraints

AI must not:

- block execution of deterministic actions
- introduce latency for basic commands
- be required for system operation

AI may be used for:

- summarization
- disambiguation
- recommendations

Rules:

- AI calls must be optional
- AI must be asynchronous where possible
- results must not delay core execution

---

## Audio Performance

Audio output must:

- follow precomputed routing
- avoid runtime speaker discovery
- execute without blocking actions

Audio must not:

- delay execution of commands
- introduce extra processing steps

---

## UI Performance

The UI must:

- reflect precomputed state
- not fetch unrelated data
- not trigger execution logic

Rules:

- UI is read-only for state
- UI updates must be efficient and targeted

---

## Configuration Performance

Configuration must:

- eliminate runtime decision-making
- define execution paths in advance
- enable direct lookup during execution

Rules:

- configuration must be complete
- incomplete configuration must degrade gracefully

---

## Failure Performance

Failures must:

- resolve quickly
- avoid retries that introduce delay
- provide immediate feedback

Fallback behavior must:

- be predefined
- be deterministic

---

## Caching Strategy

The system may use caching for:

- signals
- context data
- runtime models

Rules:

- cache must be consistent
- cache must invalidate on change
- stale data must not be served

---

## Scalability Rules

The system must:

- maintain performance as rooms increase
- maintain performance as devices increase
- avoid complexity growth at runtime

Performance must scale with:

- configuration, not execution

---

## System Constraints

The system must:

- remain fast under all conditions
- execute without hesitation
- provide consistent response times

The system must not:

- degrade due to increased configuration complexity
- rely on unpredictable execution paths

---

## Measurement Guidance

Performance should be evaluated by:

- time to execute command
- consistency of response time
- number of service calls per action

Preferred outcomes:

- single-call execution
- minimal latency
- predictable behavior

---

## Final Principle

Performance is a design decision, not an outcome.

The system must be built so that:

- execution is immediate
- behavior is predictable
- latency is minimized

The system must never think at runtime—it must already know what to do.