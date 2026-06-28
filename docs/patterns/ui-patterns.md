# UI Patterns

## Purpose

UI Patterns define how the system presents information and interacts with the user.

They ensure all interfaces are:

- consistent
- predictable
- explainable
- aligned with Home Assistant standards
- derived from system configuration and runtime models

---

## Core Principle

The user interface must feel native to Home Assistant while delivering a more disciplined and predictable experience.

---

## Foundational Rule

The UI is a projection of configuration and runtime state.

The UI must not:

- execute system logic directly
- act as a source of truth
- store independent state

---

## System Boundary (Critical)

The system is divided into:

### Global Configuration (Gear ⚙️)

- AI providers
- external integrations (M365, etc.)
- authentication and system settings

Not exposed in main UI.

---

### Operational UI (Concierge Interface)

- rooms
- interactions
- signals
- global context usage
- scene exposure and configuration

---

## Foundations

The UI must always:

- reflect system state clearly
- preserve user context
- avoid unnecessary complexity
- prioritize understanding over control

---

# 1. Navigation Patterns

## Breadcrumb Navigation

Breadcrumbs must:

- always be visible
- reflect the user's entry path
- be fully clickable
- not force hierarchy

Example:

Home > Living Room > Painting  
Alerts > Painting  
Documents > Appraisal  

---

## Back Navigation

Back navigation must restore:

- selected tab
- filters
- scroll position (best effort)

---

## Cross-Domain Navigation

Cross-cutting views must remain independent.

Examples:

- Alerts
- Documents
- History
- Interactions

Rules:

- do not force hierarchy
- preserve original context

---

# 2. Information Hierarchy

Every screen must follow:

1. Status
2. Context
3. Explanation
4. Actions
5. History

---

## Example: Room Dashboard

Status:
- room state
- confidence

Context:
- environment summary
- global context availability

Explanation:
- primary issue or insight

Actions:
- available interactions

History:
- optional drill-down

---

# 3. Progressive Disclosure

The UI must reveal information progressively.

Rules:

- show high-level state first
- allow drill-down for detail
- never overwhelm the user

---

# 4. State Visibility and Explainability

The UI must always show:

- what is happening
- why it is happening
- confidence in the result

---

# 5. Empty State Handling

The UI must never show unexplained gaps.

When data is missing:

- explain why
- guide resolution

---

# 6. Action Patterns

## Core Rule

UI actions do NOT execute system behavior directly.

UI must:

- call services
- reflect results

---

## Buttons

Buttons must:

- follow HA standards
- provide immediate feedback
- reflect loading/disabled state

---

## Confirmation

Required for:

- destructive actions
- major configuration changes

---

# 7. Dialog (Popup) Patterns

Dialogs must:

- use HA native components
- be consistent in layout

---

# 8. Iconography

### Layer 1: Native

- entities
- sensors

### Layer 2: System

- signals
- context
- interactions

---

# 9. Color Semantics

- Blue → context  
- Green → normal  
- Amber → warning  
- Red → critical  
- Gray → unknown  

---

# 10. Layout Patterns

Structure:

- top → summary
- middle → context and explanation
- bottom → detail and history

---

# 11. Consistency Rules

The same concept must appear identically everywhere.

---

# 12. State Synchronization

UI must:

- read from runtime models (coordinator/store)
- not compute state
- not simulate final state

---

# 13. Voice and UI Alignment

Voice and UI must match:

- terminology
- explanation
- behavior

---

# 14. Performance and Responsiveness

UI must:

- feel immediate
- not perform heavy logic
- rely on precomputed data

---

# 15. Interaction Feedback and Perceived Performance

## Rule

Every user action must produce immediate visible feedback.

### Immediate Feedback

- highlight selection
- update state instantly

### In-Progress Feedback

- spinner
- disabled state

### Completion Feedback

- state update
- confirmation

---

# 16. Interaction Panel Pattern (NEW)

## Purpose

Provides a unified surface for:

- signals
- context
- actions
- workflows

---

## Structure

Room Interaction Panel:

- Context (weather, news, email)
- Signals (laundry, calendar)
- Actions (available controls)
- Workflows (setup, guided flows)

---

## Rules

- must display only active interactions
- must not store independent state
- must reflect interaction model

---

# 17. Scene and Alias Visibility (NEW)

Scenes must be visible and configurable.

UI must show:

- scene name
- aliases (from Home Assistant)
- enable/disable for room
- composite inclusion

---

## Rules

- aliases are source-of-truth (HA)
- UI may allow editing aliases
- UI must not duplicate phrase systems

---

# 18. Global Context UI Pattern (NEW)

Global context must be configurable in UI.

Examples:

- weather
- news
- calendar
- email

---

## Rules

- enable/disable per context
- configure summarization behavior
- support per-room projection

---

# 19. Configuration Projection Rule (CRITICAL)

UI must always reflect:

- configuration (store)
- runtime state (models)

UI must never:

- be the source of configuration truth
- modify behavior outside services

---

## Flow

UI → service call → validation → store update → runtime update → UI refresh

---

# 20. Optimistic vs Confirmed Updates

Optimistic:

- safe UI-only updates

Confirmed:

- required for state changes and execution

---

# 21. Relationship to Runtime

UI must:

- call Concierge services
- render interaction model
- reflect execution results

UI must not:

- directly manipulate entities
- bypass execution patterns
- perform orchestration

---

# 22. User Experience Principles

The UI must always:

- prioritize clarity
- minimize effort
- build trust
- avoid noise

---

# Final Principle

The UI is not a control surface.

It is a window into a system that already knows what to do.

The user should feel:

- confident
- informed
- in control—without needing to manage complexity
