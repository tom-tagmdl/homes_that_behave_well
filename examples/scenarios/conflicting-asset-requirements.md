# Scenario: Conflicting Asset Requirements

## Purpose

This scenario demonstrates how the system handles conflicting environmental requirements between assets.

---

## Scenario

Room contains:

- grand_piano (humidity 42–50%)
- artwork (humidity 45–55%)

Current humidity: 52%

---

## Evaluation Results

- Piano: AMBER (above optimal range)
- Artwork: GREEN (within range)

---

## System Behavior

The system does NOT choose one asset over another.

---

## Advisory Output

"The room contains assets with conflicting humidity requirements. Adjusting humidity may benefit one asset while negatively affecting another."

---

## Recommendations

- maintain compromise range
- separate assets into different rooms
- implement localized control

---

## Key Principles

- system must not resolve conflicts automatically
- conflicts must be clearly explained
- user retains decision authority

---

## Final Outcome

User understands the conflict and makes an informed decision.
