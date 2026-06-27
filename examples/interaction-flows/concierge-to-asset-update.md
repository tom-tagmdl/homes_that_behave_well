# Interaction Flow: Concierge to Asset Update (Validated Service Path)

## Purpose

This interaction demonstrates how user intent is safely transformed into a system update.

It defines the full reverse path:

User intent → Concierge → Validation → Asset Intelligence service → Store → Coordinator → Updated system state

---

## Core Principle

All system changes must be:

- explicit
- validated
- explainable
- routed through services

No direct mutation is allowed.

---

## Scenario Overview

User asks:

"Can you lower the humidity requirement for this piano?"

The system must:

- understand the request
- validate the proposed change
- update the asset safely
- reflect the new state in the system

---

## Step 1: User Intent

User speaks:

"Lower the humidity requirement for this piano."

---

## Step 2: Context Resolution

Concierge determines:

- room: living_room
- asset: grand_piano

---

## Step 3: Intent Interpretation

Concierge interprets:

- action: update environment requirements
- target field: humidity range
- requested change: lower upper bound

---

## Step 4: Retrieve Current State

Concierge requests from Asset Intelligence:

- current environment requirements
- current environment conditions
- advisory suggestions (if available)

---

## Step 5: Recommendation (Optional AI)

If AI is used:

Concierge may request:

- suggested humidity range

Example result:

- recommended range: 42 to 50 percent

AI output must:

- be treated as untrusted
- be validated before use

---

## Step 6: User Confirmation

Concierge presents:

"The recommended humidity range for this piano is 42 to 50 percent. Would you like to apply this change?"

User responds:

"Yes"

---

## Step 7: Service Call

Concierge calls:

asset_intelligence.set_environment_requirements

Payload:

- asset_id: grand_piano
- humidity_min: 42
- humidity_max: 50

---

## Step 8: Validation

Asset Intelligence performs:

- schema validation
- range validation
- consistency checks

Rules:

- values must be within safe limits
- values must be complete
- invalid data must be rejected entirely

---

## Step 9: Store Update

If validation passes:

- asset record is updated in store

Changes are:

- persisted
- auditable
- versioned

---

## Step 10: Coordinator Refresh

Coordinator is triggered:

- reloads asset state
- re-runs evaluation using new requirements

---

## Step 11: System Re-Evaluation

Environment:

- humidity: 48

New Requirements:

- 42 to 50

Result:

- risk_state: GREEN

---

## Step 12: UI Update

UI reflects:

- updated requirements
- new risk state
- updated advisory

---

## Step 13: Feedback to User

Concierge responds:

"The humidity range has been updated. The piano is now within the recommended conditions."

---

## Failure Example

If invalid values are provided:

Concierge response:

"That range is outside safe limits for this asset. Please provide a valid range."

No changes are applied.

---

## Partial Failure Handling

If external dependencies fail:

- no partial write
- no inconsistent state
- error returned clearly

---

## Key Principles Demonstrated

- all updates go through services
- validation is mandatory
- AI output is advisory only
- coordinator remains the source of runtime truth
- UI reflects confirmed system state
- no silent changes

---

## Architectural Alignment

Concierge:

- interprets intent
- manages interaction
- does not mutate data

Asset Intelligence:

- validates inputs
- owns state changes
- updates store

Coordinator:

- re-evaluates system
- ensures consistency

---

## Flow Summary

User intent → Concierge → Validation → Service call → Store update → Coordinator → Updated state → UI + feedback

---

## Final Outcome

The system:

- safely applies user-requested changes
- maintains data integrity
- updates deterministically
- provides clear feedback

This ensures all actions are:

- controlled
- explainable
- trustworthy