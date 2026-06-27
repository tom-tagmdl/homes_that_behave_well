# Scenario: Piano Preservation

## Purpose

This scenario demonstrates how the system evaluates, explains, and guides preservation of a sensitive asset (a piano) within a room environment.

It shows:

- environment modeling
- exposure modeling
- evaluation
- advisory
- user interaction

---

## Scenario Overview

An acoustic piano is placed in a living room.

The room has:

- multiple environmental sensors
- windows facing southwest
- varying light exposure throughout the day

---

## Asset Definition

Asset:

- name: Grand Piano
- asset_type: instrument

Placement:

- area_id: living_room
- near_window: true
- facing_direction: southwest

Environment Requirements:

- humidity: 42 to 50 percent
- temperature: 65 to 72 degrees Fahrenheit
- light exposure: low to moderate
- uv exposure: minimal

Debounce Policy:

- red_transition_seconds: 300
- recovery_seconds: 600

---

## Room Configuration

Room:

- area_id: living_room

Windows:

- window_1:
  direction: southwest

Sensors:

- temperature sensor
- humidity sensor
- light sensor (lux)
- uv sensor

---

## Step 1: Environment Snapshot

Environment Model produces:

- temperature: 74
- humidity: 58
- lux: 213
- uv: present
- confidence: GOOD

Interpretation:

- humidity above recommended range
- temperature slightly elevated

---

## Step 2: Exposure Analysis

Exposure Model combines:

- environment values
- window direction (southwest)
- asset placement (near window, facing southwest)
- sun position (aligned with SW direction)

Derived Output:

- directional_match: true
- exposure_risk_level: HIGH
- effective_lux: elevated relative to measured lux

Interpretation:

- direct sunlight contributing to exposure
- environmental conditions amplified by window alignment

---

## Step 3: Evaluation

Evaluation Engine compares:

- environment snapshot
- exposure signals
- asset requirements

Result:

- risk_state: RED
- candidate_state: RED

Reasons:

- humidity above safe range
- sustained elevated temperature
- high exposure risk due to directional alignment

---

## Step 4: Coordinator Processing

Coordinator:

- applies debounce rules
- confirms sustained condition
- transitions asset state to RED
- generates event:

Event:

- type: risk_state_changed
- asset: grand_piano
- from: AMBER
- to: RED
- timestamp: recorded

---

## Step 5: UI Representation

Room Dashboard:

- room health: AMBER or RED depending on aggregate
- key issue: humidity above range

Asset Card:

- asset: Grand Piano
- risk: RED
- confidence: GOOD
- reason: humidity above recommended range

Asset Detail:

- environment values displayed
- exposure section shows:
  - azimuth
  - elevation
  - directional match = true
  - exposure risk = HIGH

---

## Step 6: Advisory

Advisory System generates:

Primary Advisory:

- "Humidity is above the recommended range for this piano."

Supporting Advisory:

- "Sunlight exposure is contributing to elevated conditions."
- "Consider reducing humidity to the recommended range."
- "Consider repositioning the asset or adjusting window treatment."

---

## Step 7: User Interaction

User opens asset detail.

User selects:

- "Adjust Environment Requirements" or
- "Apply Recommendation"

System behavior:

1. selection highlights immediately
2. button enters loading state
3. system processes request
4. recommended values displayed for confirmation

User confirms:

- humidity: 42 to 50
- temperature: 65 to 72

---

## Step 8: Service Flow

Concierge or UI calls:

asset_intelligence.set_environment_requirements

Flow:

- service call received
- validation performed
- store updated
- coordinator triggered

---

## Step 9: System Update

Coordinator re-runs evaluation:

- new requirements applied
- environment re-evaluated

Result:

- risk_state transitions from RED to AMBER or GREEN (depending on conditions)
- recovery timer applied

---

## Step 10: Feedback

UI:

- updated risk state displayed
- advisory updated

Concierge (if applicable):

- "The environment settings for the piano have been updated."

---

## Failure Example

If humidity sensor is missing:

Environment Model:

- humidity: null
- confidence: DEGRADED

System behavior:

- no crash
- advisory:

"Humidity data is unavailable. Add a humidity sensor to monitor conditions."

---

## Key Principles Demonstrated

- environment is derived, not stored
- exposure explains environmental impact
- evaluation is deterministic
- advisory is non-invasive
- all mutations occur through services
- UI provides immediate and clear feedback
- system degrades gracefully

---

## Final Outcome

The system:

- detects unsafe environmental conditions
- explains the risk clearly
- identifies contributing factors (sun exposure)
- suggests corrective actions
- allows safe, validated updates
- confirms changes to the user

The result is a calm, predictable, explainable system.