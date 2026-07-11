# System Flow

## Purpose

This document defines canonical runtime flow across the HTBW platform.

It preserves model-level rationale while aligning with the four-service architecture and Coordinator V2 constraints.

---

## Core Principle

System behavior must be deterministic, explainable, and bounded.

Concierge orchestrates decisions and execution but does not replace system-of-record ownership.

---

## Platform Runtime Flow

```text
Input -> Foundation Truth -> Asset Significance Context -> Voice Attribution Context -> Coordinator V2 Decisioning -> Governed Service Execution -> Projection and Communication
```

---

## Step 1: Input Reception

Inputs may originate from:

- voice
- UI
- automation triggers
- provider events

Rules:

- all inputs enter one governed execution path
- no bypass around contracts

---

## Step 2: Foundation Truth Retrieval

Foundation is the source of truth for room, area, device, occupancy, presence, and environmental state.

Rules:

- foundation truth is consumed, not rewritten by Concierge
- room and area resolution must not use parallel Concierge-owned registries

---

## Step 3: Asset Significance Retrieval

Asset Intelligence provides significance, care, and risk outcomes.

Useful model detail retained:

- environment snapshots and exposure projections can inform significance outcomes
- advisory outputs may be generated from these evaluations without mutating state

Rules:

- Concierge consumes outcomes
- Concierge does not reimplement domain evaluation logic

---

## Step 4: Voice Attribution Retrieval

Voice Identity provides attribution and confidence outputs when available.

Rules:

- Concierge consumes confidence and reason outputs
- Concierge does not own fingerprint generation, attribution algorithms, or model internals

---

## Step 5: Coordinator V2 Decisioning

Coordinator V2 is a consumer and orchestrator.

Coordinator V2 may:

- resolve interaction space and conversation ownership
- apply policy and confidence-aware behavior
- route response modality and execution target selection
- emit explainable decision metadata

Coordinator V2 must not:

- redefine governance
- redefine contracts or models
- redefine source-of-record ownership

---

## Step 6: Governed Service Execution

All state mutations must occur through governed services.

Rules:

- no direct store mutation
- no hidden side-channel writes
- validation and policy gates before execution

---

## Step 7: Projection

Entities and interaction views project state for Home Assistant surfaces.

Rules:

- projections are read-focused
- projections are not systems of record

---

## Step 8: Communication And Audit

Concierge provides user-facing communication and orchestration traces.

Rules:

- communication must remain explainable and deterministic
- audit is orchestration metadata and references, not full provider log duplication

---

## Service Flow

All mutations follow:

Service Call -> Validation -> Store Write -> Coordinator Refresh

Rules:

- validation required for all writes
- no partial writes

---

## Event Flow

Coordinator processing may emit bounded events.

Rules:

- events are immutable and timestamped
- events include source lineage and reason codes where applicable

---

## Advisory And AI-Assisted Flow

Advisory and AI-assisted recommendations are bounded flows.

Rules:

- advisory does not mutate state directly
- AI output must be validated before service execution
- AI cannot bypass governance, contracts, or policy

---

## Failure Handling And Determinism

Failure behavior:

- missing or stale inputs degrade confidence
- system returns bounded outputs instead of crashing
- no partial state application

Determinism requirement:

- identical governed inputs produce identical decision outcomes

---

## Source-Of-Record Preservation

Authoritative systems remain:

- Foundation for room, area, device, occupancy, presence, and environmental truth
- Asset Intelligence for significance and care evaluation
- Voice Identity for attribution and confidence outputs
- provider systems for calendar, email, and task or shopping domains

Concierge consumes and orchestrates these domains.

---

## No Fifth Service Guardrail

This flow does not introduce a fifth platform service.

Adapters and projections are implementation mechanisms, not additional platform services.

---

## Final Principle

Runtime behavior is correct when household-facing outcomes are preserved while canonical ownership boundaries remain intact.
