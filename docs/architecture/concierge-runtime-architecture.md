# Concierge Runtime Architecture

## Purpose

This document defines Concierge runtime behavior under HTBW governance.

It connects contracts, models, and patterns into a deterministic runtime execution architecture while preserving Coordinator V2 boundaries.

---

## Architectural Position

Concierge is the orchestration and interaction service in the four-service platform.

Concierge is not a governance authority and not a source-of-record authority.

---

## Coordinator V2 Role

Coordinator V2 is a consumer and orchestrator.

Coordinator V2 consumes:

- Foundation truth
- Asset Intelligence significance and care outcomes
- Voice Identity attribution and confidence outputs
- governed personalization context for continuity, affinity, and restoration behavior
- governed policy context

Coordinator V2 orchestrates:

- interaction space resolution
- conversation ownership
- response and modality routing
- intent and action planning
- execution through governed service interfaces

Coordinator V2 must not:

- redefine governance
- redefine contracts or models
- replace any source of record

Personalization governance authority for continuity, affinity, and restoration behavior is defined in [adr-personalization-governance.md](adr-personalization-governance.md).

---

## Runtime Layering

Concierge runtime layers are execution layers, not platform services.

1. Foundation truth consumption
2. Context assembly
3. Intent and action planning
4. Policy and safety evaluation
5. Service execution and projection

These layers do not alter four-service platform ownership.

---

## Governance-Grade Runtime Policies

### Layer Contract Standard

Each runtime layer should publish explicit:

- purpose
- allowed inputs
- required outputs
- decision rights
- non-rights
- freshness policy
- explainability payload
- failure behavior

### Cross-Layer Governance Rules

- lower-layer truth is not overwritten by higher-layer inference
- higher layers may narrow, weight, route, and personalize
- higher layers may not rewrite foundational truth
- override attempts must emit governance-visible rationale

### Decision-Right Isolation

- decision rights must be explicit per layer
- out-of-scope decisions fail policy validation
- boundary changes must be versioned as architecture updates

---

## Context Before Intent

Concierge establishes room, interaction-space, and conversation context before final intent resolution.

This enables:

- lower ambiguity
- deterministic routing
- faster household-facing outcomes

For person-scoped message delivery, Concierge must resolve the most relevant room context first and then route the message to the appropriate output channel for that room or person.
Supported delivery channels include voice assistant announcement, room speaker TTS, dashboard or kiosk display, web UI notification, and mobile notification.
Channel choice must remain explainable and follow governed fallback precedence rather than hidden inference.

---

## Interaction-Space And Conversation Policy

### Interaction Space

Interaction space may map to:

- a single room
- a merged space
- a bounded logical area

### Conversation Ownership

- one active owner for a conversation
- follow-up commands inherit scoped context until timeout
- ownership transition requires explicit trigger (timeout, context shift, correction)

---

## Decision Rights and Non-Rights

Coordinator V2 decision rights:

- choose responder and modality under policy
- choose scoped execution path
- apply confidence-aware interaction style and clarification thresholds

Coordinator V2 non-rights:

- cannot rewrite Foundation truth
- cannot redefine Asset Intelligence evaluation semantics
- cannot redefine Voice Identity attribution semantics
- cannot establish new governance or ownership domains

---

## Safety And Explainability Requirements

Runtime behavior must remain:

- deterministic
- explainable
- auditable
- reversible where policy requires

Explainability must include:

- machine form: confidence, reason codes, source lineage, timestamps
- human form: plain-language rationale and concise summary

Low-confidence behavior:

- may continue for safe and reversible actions
- requires concise clarification for risk or ambiguity classes defined by contract

---

## Respectful Redirect Policy

When local foundational context conflicts with a request target:

- identify likely intended scope
- explain local mismatch clearly
- request confirmation before cross-scope execution

---

## Contract Test And Proof Expectations

Architecture compliance should be provable with:

- decision-right isolation tests
- context freshness tests
- posture and modality routing tests
- explainability rendering tests
- respectful-redirect tests
- learning and rollback tests

Expected evidence artifacts:

- decision traces
- reason codes
- explanation payloads
- correction and adaptation records

---

## Source-Of-Record Boundaries in Runtime

- Foundation remains source of truth for room and home-state facts.
- Voice Identity remains source of truth for attribution confidence outputs.
- Asset Intelligence remains source of truth for asset significance outputs.
- Calendar, email, and task providers remain source of truth for their domains.

Concierge must consume and route, not replace.

---

## No Fifth Service Constraint

Coordinator V2, adapters, and runtime context layers do not constitute a fifth platform service.

The platform remains:

- Foundation
- Asset Intelligence
- Voice Identity
- Concierge

---

## Final Principle

Concierge runtime is architecture-compliant when it improves household outcomes without moving governance or source-of-record ownership out of canonical platform boundaries.
