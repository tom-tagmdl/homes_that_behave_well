# Scenario: Missing Capability

> **Document status: Historical illustration.**
> Retained as a worked example from the pre-refoundation exploration. It is **not** current authority.
> Canonical scenarios: [../../docs/scenarios/README.md](../../docs/scenarios/README.md).
> Closest canonical successor: [../../docs/scenarios/room-vocabulary.md](../../docs/scenarios/room-vocabulary.md)
> Terminology in this document may be superseded; see
> [../../docs/models/glossary.md](../../docs/models/glossary.md).

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