# Scenario: Missing Capability

## Purpose

This scenario demonstrates how the system behaves when a problem exists but no automated solution is available.

---

## Scenario

Humidity is above acceptable range.

No dehumidifier exists.

---

## Evaluation

- risk_state: RED

---

## System Behavior

System does NOT attempt automation.

---

## Advisory Output

"Humidity is above recommended levels, but no humidity control system is configured."

---

## Recommendation

"Consider adding a dehumidifier to enable automated correction."

---

## Key Principles

- system must not fabricate capability
- system must clearly communicate limitations
- recommendations must be realistic

---

## Final Outcome

User understands both the problem and the limitation.