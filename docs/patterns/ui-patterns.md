# UI Patterns

## Purpose

UI Patterns define how the system presents information and interacts with the user.

This ensures all interfaces are:

- consistent
- predictable
- explainable
- aligned with Home Assistant standards

---

## Core Principle

The user interface must feel native to Home Assistant while delivering a more disciplined and predictable experience.

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

Example:

User navigates:
Room → Asset → History tab  
Back returns to:
Room → same position and filters

---

## Cross-Domain Navigation

Cross-cutting views must remain independent.

Examples:

- Alerts
- Documents
- History

Rules:

- do not force users through a hierarchy
- preserve original context when returning

---

# 2. Information Hierarchy

Every screen must follow the same structure:

1. Status
2. Context
3. Explanation
4. Actions
5. History

---

## Example: Room Dashboard

Status:
- room health (Green/Amber/Red)
- confidence

Context:
- environment summary

Explanation:
- primary issue

Actions:
- recommendations

History:
- optional drill-down

---

# 3. Progressive Disclosure

The UI must reveal information progressively.

Rules:

- show summary by default
- expose detail through tabs or drill-down
- avoid overwhelming the user

---

## Example

Room Dashboard:
- high-level health and issues

Room Detail:
- tabs for:
  - overview
  - metrics
  - recommendations
  - history

---

# 4. State Visibility and Explainability

Every state must be explainable.

The UI must always show:

- what is happening
- why it is happening
- confidence in the result

---

## Example

Asset Card:

- Risk: RED
- Confidence: PARTIAL
- Reason: "Humidity above recommended range"

---

# 5. Empty State Handling

The UI must never show unexplained gaps.

When data is missing:

- explain why
- guide the user to resolve it

---

## Example

"Humidity data unavailable  
No sensor configured for this room"

---

# 6. Action Patterns

## Buttons

Buttons must follow Home Assistant conventions:

- primary actions: default style
- destructive actions: clearly marked
- destructive actions require confirmation

---

## Confirmation Pattern

Use confirmation dialogs for:

- deletes
- irreversible changes
- significant configuration updates

---

## Example

"Remove Asset?"  
Cancel | Confirm

---

# 7. Dialog (Popup) Patterns

All dialogs must:

- use Home Assistant native dialog components
- follow consistent layout
- be clearly labeled

Dialogs must not:

- implement custom frameworks
- override standard behavior

---

# 8. Iconography

The system uses a two-layer icon model:

### Layer 1: Native Icons

Use Home Assistant icons for:

- individual sensors
- individual entities

---

### Layer 2: System Icons

Use system-level icons for:

- environment categories
- asset risk states
- advisory groupings

---

## Example

- Temperature → thermometer icon  
- Room Environment → system category icon  

---

# 9. Color Semantics

Colors must convey meaning consistently.

---

## Standard Mapping

- Blue → environment / informational context  
- Green → safe / normal  
- Amber → warning  
- Red → risk / critical  
- Gray → unknown / unavailable  

---

## Rules

- use theme-defined colors
- avoid custom color systems
- do not use color alone to convey meaning

---

# 10. Layout Patterns

The UI must follow consistent structure.

---

## Rules

- top: summary / status
- middle: context and explanation
- bottom: detailed data and history

---

## Grouping

Group related data:

- by domain (climate, light, air)
- by function (status, config, history)

---

# 11. Consistency Rules

The same concept must appear the same way everywhere.

Examples:

- humidity always shown the same way
- risk colors always consistent
- icons always consistent

---

# 12. State Synchronization

UI must reflect real system state.

Rules:

- UI reads from coordinator projections
- no UI-driven computation
- no stale or inconsistent values

---

# 13. Voice and UI Alignment

Concierge and UI must match.

Rules:

- same terminology
- same explanations
- same risk descriptions

---

## Example

UI:
"Humidity above recommended range"

Voice:
"Humidity is above the recommended range for this asset"

---

# 14. Performance and Responsiveness

UI must feel immediate and stable.

Rules:

- no heavy logic in UI
- use cached coordinator data
- show loading states only when necessary

---

# 15. Interaction Feedback and Perceived Performance

## Purpose

The system must clearly communicate when a user action has been received, is in progress, and has completed.

The user must never be left wondering whether an action worked.

---

## Core Principle

Every user action must produce immediate, visible feedback.

---

## Immediate Feedback (Required)

When a user selects an option:

- the UI must respond instantly
- the action must visibly change state

Examples:

- button changes state (pressed / active)
- selection highlights immediately
- confirmation indicator appears

---

## In-Progress Feedback (Long-Running Actions)

For actions that take time:

- the system must indicate that processing is occurring

Examples:

- spinner or loading indicator
- disabled button with visual state
- progress indicator when appropriate

---

## Completion Feedback

When an action completes:

- the result must be visible
- the system must confirm success or failure

Examples:

- updated state reflected in UI
- confirmation message (non-intrusive)
- state transition (e.g., Green → Amber)

---

## Failure Feedback

When an action fails:

- the user must be clearly informed
- the reason must be explainable

Examples:

- "Unable to update asset — invalid configuration"
- "Sensor data unavailable — try again later"

The system must never silently fail.

---

## Button Behavior Rules

Buttons must:

- provide immediate visual feedback on click
- reflect disabled or loading states
- prevent duplicate actions while processing

Buttons must not:

- appear unresponsive
- allow repeated triggering during execution
- leave the user uncertain of state

---

## Optimistic vs Confirmed Updates

Where safe, the UI may use optimistic updates:

- immediately reflect expected state
- reconcile with actual result when complete

Where unsafe:

- wait for confirmed result before updating UI

---

## Timing Expectations

Feedback must:

- occur immediately on interaction (< 100ms perceived)
- show progress if action exceeds brief duration
- resolve clearly once complete

---

## Relationship to Coordinator

UI must reflect coordinator state changes.

Rules:

- UI does not simulate final state
- UI reflects actual system state when confirmed
- coordinator remains the source of truth

---

## Example Pattern

User clicks "Apply Environment Recommendation"

1. Button highlights immediately
2. Button enters loading state
3. System processes request
4. Asset state updates
5. Button returns to normal
6. New values appear in UI

---

## Final Principle

A system feels fast when users know what is happening.

Lack of feedback creates confusion, not delay.

---

# 16. User Experience Principles

The UI must always:

- prioritize clarity over cleverness
- minimize user effort
- avoid repetition
- provide confidence in system behavior

---

# Final Principle

The UI should not feel like a tool.

It should feel like a calm, predictable system that explains itself.