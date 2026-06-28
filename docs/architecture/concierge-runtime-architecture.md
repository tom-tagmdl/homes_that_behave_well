# Concierge Runtime Architecture

## Purpose

The Concierge Runtime Architecture defines how the Concierge system executes at runtime.

It describes:

- how voice input is processed
- how room context is resolved
- how signals and context are retrieved
- how actions are executed
- how interactions are generated

This document connects all contracts, models, and patterns into a single deterministic execution flow.

---

## Core Principle

The system must execute deterministically.

Once intent is known, the system must act immediately without runtime ambiguity.

---

## High-Level Flow

The Concierge runtime follows this lifecycle:

1. Input received (voice or UI)
2. Resolution (direct or Concierge)
3. Context determination (room or composite)
4. Capability retrieval (signals, context, execution targets)
5. Execution or response generation
6. Interaction update (if applicable)

---

## Input Sources

Inputs originate from:

- Voice (Home Assistant Assist or external assistant)
- UI (Interaction panel or dashboard)
- Events (signal changes)
- Automations (internal triggers)

All inputs must enter the same execution pipeline.

---

## Resolution Layer

### Step 1: Voice Resolution

Voice input is first processed by Home Assistant.

Flow:

- Assist attempts to match entity name or alias
- If match is found:
  → direct entity service execution
- If no match:
  → forwarded to Concierge

---

### Step 2: Concierge Resolution

Concierge is responsible for:

- ambiguous commands
- multi-entity actions
- contextual queries
- signal-based requests

Examples:

- What should I do here
- Close everything
- Is the laundry done

Concierge must:

- resolve intent deterministically
- avoid guessing
- follow defined contracts

---

## Context Resolution

### Room Context

The system determines:

- area_id from invoking device
- room projection configuration

---

### Composite Context

If the resolved room belongs to a composite:

- promote to composite context

Rules:

- composite context overrides individual room scope
- must remain deterministic

---

## Runtime Model Assembly

The runtime model is assembled from preconfigured data.

It includes:

room_runtime_model:
  area_id:
  composite_id:
  execution_targets:
  audio:
  enabled_signals:
  global_overlays:
  entity_mappings:
  scene_bindings:

Rules:

- must be precomputed
- must not require runtime discovery
- must be consistent across executions

---

## Capability Retrieval

### Signals

Retrieved via:

- signal providers
- Signal Contract

Used for:

- household state
- actionable awareness

---

### Global Context

Retrieved via:

- context providers
- Global Context Contract

Used for:

- weather
- news
- email summaries

---

## Execution Path

All actions must follow execution patterns.

### Execution Hierarchy

1. Scene
2. Group
3. Direct entity control

---

### Execution Flow

If execution target is defined:

- call target directly

If not:

- fallback according to execution hierarchy

---

### Example

Command:
Close the shades

Execution:

- scene → scene.turn_on
- group → cover service call
- entity → batched entity control

---

## Audio Routing

Audio must follow strict priority:

1. preferred speaker
2. speaker candidates
3. voice device speaker fallback

Audio resolution must not delay execution.

---

## Interaction Generation

Interactions are generated when:

- signals change
- user requests information
- workflows begin

Interaction model:

interaction:
  id:
  type:
  source:
  summary:
  detail:
  actions:
  priority:
  expires_at:

Rules:

- interactions are ephemeral
- must not persist state
- must reflect system truth

---

## Voice + UI Parity

Both voice and UI must:

- invoke the same services
- use the same execution logic

Rules:

- UI must not bypass Concierge
- voice must not bypass execution patterns

---

## AI Integration

AI is optional and must be bounded.

### When AI is Allowed

- summarization
- disambiguation
- recommendations

---

### When AI is Not Allowed

- execution decisions
- service calls
- state interpretation

---

### AI Execution Flow

If deterministic path exists:

- execute immediately

If not:

- invoke AI (if enabled)
- produce structured result
- return to deterministic execution

---

## Event Handling

Signals may emit events:

- laundry.complete
- dishwasher.clean
- calendar.event_starting

Concierge must:

- evaluate context
- decide on interaction or notification
- avoid duplicate behavior

---

## Performance Requirements

The system must:

- avoid runtime entity discovery
- use precomputed configuration
- execute actions in a single call when possible
- avoid iterative loops

---

## Failure Handling

### Resolution Failure

If input cannot be resolved:

- return clear response
- do not guess intent

---

### Execution Failure

If execution target is unavailable:

- fallback to next strategy
- provide user feedback

---

### Data Failure

If signals or context are unavailable:

- degrade gracefully
- never fabricate results

---

## Security Model

The system must:

- respect integration boundaries
- avoid exposing sensitive configuration
- prevent unauthorized execution

---

## System Constraints

The system must:

- be deterministic
- be explainable
- be context-aware
- be fast

The system must not:

- rely on probabilistic execution
- perform hidden logic
- bypass defined contracts

---

## Final Principle

The runtime architecture defines how the system behaves in real time.

All interactions must follow:

- known context
- known capability
- known execution path

The system must never hesitate once intent is understood.