# Event Model

## Purpose

Defines the structure and behavior of system events.

---
## Event Identity and Traceability

Each event must include:

- event_id
- correlation_id
- source

---

### event_id

- globally unique
- immutable
- must never be reused

---

### correlation_id

- groups related operations
- links service call → coordinator → event(s)

---

### source

Allowed values:

- system
- user
- ai_recommendation_applied

---

### Purpose

This ensures:

- full traceability of actions
- debugging capability
- linkage between cause and effect

---
## Event Types

The system supports the following event types:

- risk_state_changed
- environment_event
- advisory_event
- configuration_event
- custody_event
- document_event

---

### Rules

- event types must be explicitly defined
- no implicit or undefined event types are allowed
- all systems must use the same set of event types


---

## Event Structure

Each event must include:

- event_id
- correlation_id
- event_version
- type
- timestamp
- source
- created_at
- created_by
- actor
- origin
- cycle_id
- sequence_in_cycle
- supporting_data

Ownership fields:

- asset_id (required for asset-scoped events)
- area_id (required for room-scoped events)

Type-specific fields:

- previous_state (required for risk_state_changed)
- new_state (required for risk_state_changed)
- reason_codes (required for risk_state_changed)

Rules:

- at least one ownership field must be present (asset_id or area_id)
- both ownership fields may be present for cross-scope events
- required fields must exist for all events
- missing non-applicable fields must be null

Field format rules:

- timestamp and created_at must be ISO 8601 UTC timestamps (ending with Z)
- cycle_id must be a stable coordinator cycle identifier
- sequence_in_cycle must be an integer starting at 1
- event_id and correlation_id must be non-empty strings

## Event Versioning

All events must include a version identifier.

---

### Field

- event_version

---

### Rules

- event_version must be required
- initial version: 1
- version must increment on any breaking schema change

---

### Purpose

This ensures:

- backward compatibility
- safe schema evolution
- version-aware processing across systems

---

## Example

event:
  event_id: evt_01J1ABCDEF1234567890
  correlation_id: corr_01J1ABCDE99999999999
  event_version: 1
  type: risk_state_changed
  source: system
  created_at: 2026-06-27T10:00:00Z
  created_by: coordinator
  actor: system
  origin: evaluation
  cycle_id: 2026-06-27T10:00:00Z
  sequence_in_cycle: 3
  asset_id: grand_piano
  area_id: living_room
  timestamp: 2026-06-27T10:00:00Z
  previous_state: AMBER
  new_state: RED
  supporting_data:
    changed_signals:
      - climate.humidity
      - light.uv
    values:
      climate.humidity: 58
      light.uv: 4.3
  reason_codes:
    - HUMIDITY_HIGH
    - UV_EXPOSURE_HIGH

---
## Event Ordering Rules

Events must be processed in a deterministic order.

---

### Primary Order

- timestamp (ascending)

---

### Tie-Break Order

If timestamps are equal:

1. cycle_id (coordinator cycle)
2. sequence_in_cycle (incremental counter)
3. event_id (lexical order)

---

### Rules

- ordering must be stable across systems
- no ambiguity in event sequence is allowed
- timestamp comparisons must use normalized UTC instants

---

### Purpose

This ensures:

- reproducible history
- consistent explanations
- correct event replay behavior

---

## Persistence Rules

- persisted in store
- bounded history
- queryable for explanation and reporting

---

## Usage

Events support:

- explanation ("why did this happen")
- reporting (insurance, audit)
- system behavior tracking

---
## Supporting Data Structure

Each event type must include a defined supporting_data structure.

---

### Minimum Requirements by Event Type

risk_state_changed:
  - previous_state
  - new_state
  - reason_codes

environment_event:
  - changed_signals[]
  - values

advisory_event:
  - advisory_type
  - message

configuration_event:
  - field_changed
  - previous_value
  - new_value

custody_event:
  - custody_status
  - holder
  - effective_at

document_event:
  - document_type
  - action (added, removed, updated)

---

### Rules

- supporting_data must match event type
- fields must be consistent across implementations
- no free-form structures are allowed

---

### Purpose

This ensures:

- structured reporting
- predictable UI behavior
- consistency across systems
---
## Lifecycle Metadata

Each event must include metadata describing its origin.

---

### Fields

- created_at
- created_by
- actor
- origin

---

### Definitions

created_at:
- timestamp of event creation

created_by:
- system component responsible (e.g., coordinator)

actor:
- entity initiating the action (user, system, AI)

origin:
- trigger context (service_call, sensor_change, evaluation)

source:
- event producer classification (system, user, ai_recommendation_applied)

Distinction rule:
- source identifies who produced the event record
- actor identifies who initiated the business action
- origin identifies what triggered the event

---

### Purpose

This enables:

- audit trails
- accountability
- debugging
---
## History Retention Policy

Event history must be bounded.

---

### Default Limits

- max events per asset: 1000
- max global events: 50000

---

### Retention Strategy

- oldest events are discarded first (FIFO)
- critical events are retained at 2x default limits

Critical event criteria:

- type = risk_state_changed AND new_state = RED
- type = environment_event AND supporting_data includes safety.leak = true
- type = configuration_event for safety or hazard-related fields

---

### Rules

- system must never store unbounded history
- retention policy must be predictable and documented
- per-asset limit must be applied before global pruning
- global pruning must use FIFO based on deterministic event ordering

---

### Purpose

This ensures:

- consistent performance
- controlled storage growth
- predictable system behavior
---

## Final Principle

Events are the authoritative record of system behavior.