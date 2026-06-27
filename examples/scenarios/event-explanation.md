# Scenario: Event Explanation (“Why Did This Happen?”)

## Purpose

This scenario demonstrates how the system explains a past event in a deterministic and understandable way.

---

## Scenario

User asks:

"Why did the piano go to RED yesterday?"

---

## Step 1: Context Resolution

Concierge determines:

- room: living_room
- asset: grand_piano

---

## Step 2: Event Lookup

Asset Intelligence retrieves:

- event: risk_state_changed
- timestamp: yesterday
- from: AMBER
- to: RED

---

## Step 3: Supporting Data

System retrieves:

- environment snapshot at time of event
- exposure conditions
- evaluation reasons

---

## Step 4: Explanation Assembly

Concierge constructs explanation:

"Yesterday, humidity rose above the recommended range and remained elevated. At the same time, sunlight exposure from the southwest window increased the effective environmental impact. Because the condition persisted, the system transitioned the piano to a RED risk state."

---

## Key Principles

- explanations must be derived, not generated
- explanation must match recorded data
- no inference beyond known data

---

## Final Outcome

User understands:

- what happened
- when it happened
- why it happened