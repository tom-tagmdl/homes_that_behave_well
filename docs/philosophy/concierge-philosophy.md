# Concierge Philosophy

## Purpose

The Concierge Philosophy defines the guiding principles behind the design and behavior of the Concierge system.

It explains:

- what Concierge is
- what it is not
- how it thinks
- how it behaves

This philosophy ensures the system remains consistent, predictable, and aligned with the concept of a home that behaves well.

---

## Core Principle

Concierge is not a voice assistant.

Concierge is the interaction layer of a context-aware home.

---

## What Concierge Is

Concierge is:

- a room-aware orchestration system
- a deterministic execution engine
- a unifying interaction layer across voice and UI
- a system that reflects structured knowledge about the home

Concierge exists to:

- make the home understandable
- make the home predictable
- make the home responsive without complexity

---

## What Concierge Is Not

Concierge is not:

- a generic AI assistant
- a cloud-first system
- a probabilistic decision engine
- a device-centric control layer

Concierge must never:

- guess what to do
- infer behavior without configuration
- act without explainability

---

## Room-First Thinking

Concierge operates on a room-first model.

The room is the fundamental unit of context.

Every interaction is grounded in:

- where the user is
- what exists in that room
- what is configured for that room

If rooms are grouped:

- composite rooms represent experience
- physical rooms remain unchanged

---

## Deterministic Behavior

Concierge must behave deterministically.

This means:

- identical input produces identical output
- execution paths are predefined
- no runtime decision-making occurs

The system must:

- know what to do before a request is made
- execute immediately once intent is resolved

---

## Configuration Over Inference

Concierge is driven by configuration, not discovery.

The system must:

- rely on stored configuration
- avoid runtime discovery
- avoid pattern guessing

All system behavior must be:

- explicitly defined
- validated
- reusable

---

## Local-First Execution

Concierge must always prefer local execution.

This means:

- direct entity or scene execution is preferred
- Home Assistant capabilities are used first
- external systems are avoided unless necessary

The home must function fully without dependency on external services.

---

## AI as Assist, Not Authority

AI is optional and bounded.

AI may:

- summarize information
- assist with disambiguation
- improve natural language responses

AI must not:

- decide how actions are executed
- control devices directly
- override system rules
- introduce uncertainty into execution

Concierge must always remain in control.

---

## Alias-First Voice Model

Voice interaction must follow Home Assistant's native model.

This means:

- entity names and aliases are the source of truth
- scenes define primary actions
- Assist resolves commands first

Concierge only intervenes when:

- no direct match exists
- a command spans multiple entities
- context is required

---

## Execution Philosophy

Execution must be:

- immediate
- single-path
- preconfigured

The system must:

- prefer scenes
- use groups when necessary
- fall back to entity control only when required

The system must never:

- determine how to execute at runtime
- introduce delay through decision layers

---

## Interaction Model

Interactions represent what the system surfaces to the user.

They must be:

- current
- actionable
- explainable

The UI does not control the home.

The UI reveals a system that already knows what to do.

---

## UI Philosophy

The interface must feel:

- calm
- predictable
- native to Home Assistant

The UI must:

- reflect system state
- avoid complexity
- provide clarity over control

The UI must not:

- contain business logic
- act as the source of truth
- simulate behavior

---

## System Transparency

Concierge must always be explainable.

The user must be able to understand:

- what is happening
- why it is happening
- what will happen next

The system must never:

- act invisibly
- hide decision-making
- produce unexplained results

---

## Performance as a Design Principle

Performance is not an optimization.

Performance is a design requirement.

The system must:

- execute quickly
- avoid unnecessary processing
- rely on precomputed models

The system must never hesitate once intent is known.

---

## Consistency Over Cleverness

Concierge values consistency over intelligence.

The system must:

- behave the same way every time
- avoid unpredictable variation
- prioritize reliability over novelty

---

## The Experience Goal

The system should feel like:

- a home that understands context
- a system that explains itself
- an environment that behaves predictably

The user should feel:

- confident
- informed
- at ease

---

## Final Principle

A well-designed home does not require explanation.

It behaves as expected.

Concierge exists to make that possible.