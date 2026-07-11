# Context Before Intent

## Purpose

This document defines the Context Before Intent execution pattern for Concierge.

The pattern is an orchestration strategy, not a governance transfer and not a new platform service.

---

## Core Statement

A Home That Behaves Well establishes context before intent.

Context is resolved before final intent interpretation so runtime decisions are deterministic, explainable, and low-friction.

---

## Platform Alignment

The pattern aligns to the four-service model:

- Foundation provides room and home-state truth
- Asset Intelligence provides significance and care context
- Voice Identity provides attribution and confidence context
- Concierge orchestrates and decides what should happen

No ownership boundaries change under this pattern.

---

## Component Responsibilities

### Foundation (System Of Record)

Foundation owns factual room, area, device, occupancy, and presence truth.

Foundation does not decide responder ownership or execution intent.

### Coordinator V2 (Decision And Orchestration)

Coordinator V2 consumes governed context and decides routing and orchestration behavior.

Coordinator V2 does not own attribution algorithms, fingerprint lifecycle internals, or foundational truth.

---

## Interaction Space Rationale

Interaction space is the bounded area where a conversation is happening.

It is derived from governed inputs such as:

- room and area context
- occupancy and presence
- attribution confidence when available
- recent interaction continuity

Personalization and restoration-related continuity behavior must consume governed policy from [adr-personalization-governance.md](adr-personalization-governance.md).

Rationale:

- narrows execution scope before intent resolution
- reduces ambiguity and clarification churn
- improves deterministic response latency

---

## Conversation Ownership Rationale

Conversation ownership keeps multi-turn interactions coherent.

Rules:

- one active owner at a time
- follow-ups remain in scope until timeout or explicit shift
- ownership changes are explicit, explainable, and bounded

Benefits:

- lower latency from reduced re-resolution
- better user predictability
- less cross-room context thrashing

---

## Bounded Behavioral Guidance

### Contextual Resolution

1. resolve inside local scope first
2. expand only when ambiguity remains
3. honor explicit user scope overrides

### Clarification And Low Confidence

- unambiguous and safe: execute directly
- ambiguous: concise clarification
- low confidence but safe and reversible: proceed with explicit explainability

### Learning Through Corrections

- correction signals may adjust future weighting
- behavior remains deterministic, reversible, and auditable
- learning does not rewrite source-of-record ownership

---

## Source-Of-Record Protection

Context Before Intent does not change source-of-record ownership.

Provider and peer-service systems remain authoritative for their domains.

---

## Performance Intent

The pattern improves household-facing responsiveness by reducing runtime ambiguity and narrowing decision space before execution.

Performance gains must not come from bypassing contracts, governance, or safety policy.

---

## Final Principle

Context Before Intent is valid only when it preserves deterministic behavior, explicit boundaries, and canonical ownership across the HTBW platform.
