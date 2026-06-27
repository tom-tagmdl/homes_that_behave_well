# Scenario: Room Dashboard Awareness and Action

## Purpose

This scenario demonstrates how a user interacts with the Room Dashboard to:

- identify assets in distress
- understand what is wrong
- see recommended actions
- take appropriate corrective steps

It represents the primary user experience for monitoring and responding to environmental conditions.

---

## Scenario Overview

A user opens the dashboard for a room.

The system displays:

- overall room health
- assets within the room
- current issues
- recommended actions

The user must be able to:

- quickly identify problems
- understand causes
- decide what to do next

---

## Room Context

Room:

- area_id: living_room

Assets in room:

- grand_piano
- oil_painting
- display_cabinet

---

## Step 1: Room Dashboard Overview

Dashboard displays:

Status:

- room health: AMBER
- confidence: GOOD

Summary:

- key issue: humidity above recommended range

---

## Step 2: Asset Visibility

Each asset is shown as a card:

### Grand Piano

- risk: RED
- confidence: GOOD
- key issue: "Humidity above recommended range"

---

### Oil Painting

- risk: AMBER
- confidence: GOOD
- key issue: "Elevated UV exposure"

---

### Display Cabinet

- risk: GREEN
- no issues

---

## Step 3: Immediate Understanding

The user can immediately see:

- which assets are affected
- severity of issues
- primary cause for each issue

Rules:

- no asset should show a state without explanation
- no explanation should require navigation to another screen

---

## Step 4: Recommended Actions (Room Level)

Dashboard shows top recommendations:

- "Reduce humidity in the living room"
- "Limit sunlight exposure during peak hours"
- "Consider repositioning sensitive assets away from windows"

Rules:

- recommendations must be actionable
- recommendations must be prioritized
- recommendations must be limited (top 2–3)

---

## Step 5: Interaction Feedback

User selects:

- "Reduce humidity"

System behavior:

1. selection is immediately highlighted
2. button enters processing state
3. system prepares options or actions

---

## Step 6: Drill-Down to Asset

User clicks on:

- Grand Piano

Navigates to Asset Detail:

- maintains context (room, filters, scroll)
- shows detailed environment and exposure

---

## Step 7: Detailed Understanding

Asset Detail shows:

- humidity value: 58 percent
- requirement: 42–50 percent
- exposure impact:

  - window direction: southwest
  - directional match: true
  - exposure risk: HIGH

Explanation:

"Humidity is above the recommended range, and sunlight exposure is contributing to elevated conditions."

---

## Step 8: Action Options

User is presented with actions:

- adjust environment requirements (if appropriate)
- trigger automation (if available)
- review recommendations

Example actions:

- "Turn on dehumidifier"
- "Close blinds"
- "Relocate asset"

Rules:

- actions must map to real system capabilities
- actions must be safe and reversible where possible

---

## Step 9: System Response

User triggers:

- "Turn on dehumidifier"

System behavior:

- button shows immediate feedback
- automation executes
- environment begins to change

---

## Step 10: Re-Evaluation

System performs:

- updated environment snapshot
- re-evaluation

Results:

- humidity begins decreasing
- risk_state transitions from RED → AMBER (after debounce)

---

## Step 11: Feedback to User

Room Dashboard updates:

- grand_piano: AMBER
- overall room health improves

Optional message:

"Humidity levels are improving in the living room."

---

## Step 12: Stability and Completion

After sustained improvement:

- risk_state transitions to GREEN
- recommendations update or clear

Dashboard:

- shows stable state
- no active issues

---

## Failure Example

If no corrective action is available:

Dashboard shows:

- "Humidity is above range"
- "No automated control available"

Recommendation:

- "Manual intervention required"

---

## Key Principles Demonstrated

- immediate visibility of problems
- consistent information hierarchy
- clear mapping from issue → explanation → action
- limited and actionable recommendations
- immediate interaction feedback
- deterministic state transitions
- separation of evaluation and action

---

## UI Patterns Demonstrated

- room-level summary view
- asset card consistency
- progressive disclosure (dashboard → detail)
- explainable state representation
- action confirmation and feedback

---

## Architectural Alignment

Asset Intelligence:

- evaluates environment
- provides risk state and explanation

Coordinator:

- manages transitions
- provides consistent room snapshot

Entities:

- expose state to UI

Home Assistant Automations:

- perform actions on triggers

Concierge:

- optional reinforcement via messaging

---

## Final Outcome

The user:

- immediately understands room conditions
- identifies at-risk assets
- understands why issues exist
- takes corrective action with confidence

The system:

- remains calm and predictable
- clearly explains every state
- provides actionable guidance
- responds deterministically to changes

This creates a responsive and trustworthy experience.