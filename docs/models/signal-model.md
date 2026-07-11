# Signal Model

## Purpose

The Signal Model defines the structure used to represent household state in a consistent, reusable, and integration-agnostic way.

Signals provide normalized, human-consumable representations of real-world conditions that can be used across Concierge, UI, and voice interactions.

This model is a consumption model for signal truth, provenance references, and explainable presentation.

---

## Core Structure

A Signal is represented as:

signal:
  id:
  type:
  provider:
  available:
  state:
  summary:
  detail:
  speakable:
  provenance_reference:
  occupancy_reference:
  explainability:
  actions:

---

## Field Definitions

### id

A unique identifier for the signal.

- Must be stable across sessions
- Used for referencing the signal in services and UI

Example:
calendar.family
laundry.main_floor

---

### type

Defines the category of signal.

Common values:

- calendar
- shopping_list
- laundry
- dishwasher
- reminders
- delivery

Used by Concierge to determine how to route and present the signal.

---

### provider

The integration responsible for the signal.

Examples:

- calendar
- todo
- sensor-based integration
- custom appliance integration

The provider owns all logic and state behind the signal.

The signal model consumes provider truth and does not redefine it.

---

### available

Boolean indicating whether the signal is currently usable.

true:
- Integration is available
- Required entities exist
- Configuration is valid

false:
- Signal cannot be used
- Concierge must not attempt to access state

---

### state

A normalized representation of the signal’s current condition.

Must be:

- Deterministic
- Integration-defined
- Stable across requests

Examples:

laundry:
  state: running

laundry:
  state: complete

dishwasher:
  state: clean

calendar:
  state: upcoming_events

shopping_list:
  state: has_items

---

### summary

A short, human-readable description of the signal state.

Used for:

- UI display
- Dashboards
- Lists

Examples:

Laundry is complete  
There are 5 items on the shopping list  
You have 2 events today  

---

### detail

Optional extended information about the signal.

Used when additional context is needed in UI or expanded responses.

Examples:

Next event is at 2 PM with Project Team  
Laundry finished 10 minutes ago  
Milk and eggs are still on the list  

---

### speakable

A fully composed natural language response suitable for voice output.

Must:

- Require no additional formatting
- Be concise and natural
- Reflect the current signal state

Examples:

The laundry is done.  
You have two events today. Your next meeting is at 2 PM.  
There are five items on your shopping list.  

Concierge must use this field directly and must not reconstruct speech.

---

### actions

Optional list of supported actions.

Each action must correspond to a callable service exposed by the provider.

Structure:

actions:
  - id:
    label:
    service:

Example:

actions:
  - id: add_item
    label: Add Item
    service: shopping_list.add_item

  - id: remove_item
    label: Remove Item
    service: shopping_list.remove_item

Concierge may invoke actions but must not define their behavior.

## Contract Alignment

This model aligns with:

- Capability Projection Contract
- Occupancy and Presence Contract
- Provenance Contract
- Knowledge, Briefing, and Household Status Synthesis Contract

---

## Example Signals

### Laundry Signal

signal:
  id: laundry.main_floor
  type: laundry
  provider: appliance_integration
  available: true
  state: complete
  summary: Laundry is complete
  detail: Laundry finished 8 minutes ago
  speakable: The laundry is done.
  actions:

---

### Calendar Signal

signal:
  id: calendar.family
  type: calendar
  provider: calendar
  available: true
  state: upcoming_events
  summary: You have 2 events today
  detail: Next event is at 2 PM with Project Team
  speakable: You have two events today. Your next meeting is at 2 PM.
  actions:

---

### Shopping List Signal

signal:
  id: shopping_list.primary
  type: shopping_list
  provider: todo
  available: true
  state: has_items
  summary: There are 5 items on your shopping list
  detail: Milk, eggs, bread, and two more items
  speakable: There are five items on your shopping list.
  actions:
    - id: add_item
      label: Add Item
      service: shopping_list.add_item
    - id: remove_item
      label: Remove Item
      service: shopping_list.remove_item

---

## Model Rules

Signals must:

- Represent real system state
- Be provided entirely by the owning integration
- Be consistent across UI and voice
- Be deterministic and repeatable

Signals must remain explainable and provenance-referenceable when contract-authorized.

Signals must not duplicate provenance, occupancy, or occupancy-presence authority.

Signals must not:

- Expose raw entity values directly
- Require interpretation by Concierge
- Contain partial or ambiguous state

---

## Relationship to Concierge

Concierge consumes signals.

Concierge:

- Requests signal data via services
- Determines when signals are relevant
- Chooses how to present signals (voice, UI, or both)

Concierge must not:

- Modify signal structure
- Store signal data
- Infer or override signal state

---

## Relationship to Room Context

Signals are whole-home constructs.

They are projected into rooms by Concierge.

Room configuration determines:

- Whether a signal is available in that room
- Whether it can be spoken or displayed

Signals themselves remain independent of room scope.

---

## Final Principle

The Signal Model defines how the home expresses what is happening.

Integrations define the truth.

Concierge delivers that truth to the user in a clear and meaningful way.

The model remains consumption-only for capability, provenance, occupancy, and status synthesis workflows.