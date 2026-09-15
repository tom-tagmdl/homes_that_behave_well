# ADR: Truth as a First-Class Fact Engine

> **Document status: Canonical ADR.**
> Status: **Accepted**. Supersedes every "Foundation owns truth" statement.
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Context

Five documents asserted that Foundation owns truth, including the capability-projection contract, the
experience-projection contract, the occupancy-and-presence contract, the room model, and the
room-awareness contract.

That assertion produced three failures.

1. **Description and evaluation were merged.** Foundation describes what exists. Deciding what is
   currently true is a different activity with different inputs, different confidence semantics, and a
   different failure mode.
2. **Evidence and fact were conflated.** A sensor reading, a voice match, and a BLE beacon are
   evidence. *The Den is occupied* is a fact. Without a distinct owner, evidence was frequently treated
   as fact.
3. **Uncertainty had nowhere to live.** Foundation's outputs are definitional and do not carry
   confidence, provenance, freshness, coverage, or validity. Facts must carry all five.

Meanwhile, `canonical-architecture.md` prohibited introducing a fifth platform service, which made it
impossible to give truth an owner at all.

---

## Decision

**Truth is a first-class authoritative fact engine.**

- **Foundation defines what a Fact *is*.**
- **Truth decides what is factual now.**

Every published fact carries a subject, a statement, confidence, provenance, freshness, validity, and —
for composite facts — coverage. **A statement whose confidence, provenance, or freshness cannot be given
is not published as a fact.**

### Truth must not

Trigger actions, control devices, make resident-facing behavioral decisions, own preferences, own
authority, hide uncertainty, or automatically convert weak evidence into a definitive fact.

### The composite-fact division

| Step | Owner |
|---|---|
| Declare which sensors are eligible contributors | **Room Configuration** (Foundation) |
| Calculate the composite fact | **Truth** |
| Select sensors at runtime | **Prohibited** |

Room Configuration does not calculate Truth. Truth does not own the sensor inventory. Concierge does
not choose sensors at runtime.

### Conflicting evidence

**No consumer may resolve competing Truths by inventing a preferred fact.** Truth may resolve to a
reduced-confidence fact under a governed rule, publish an unresolved fact, publish `unknown`, or
withdraw a fact. Silently choosing the most recent, highest-confidence, or most convenient evidence
without recording the conflict is prohibited.

---

## Consequences

### Superseded

Every statement that Foundation owns truth, and the "no fifth platform service" prohibition that
prevented Truth from existing.

### Established

- [../models/truth.md](../models/truth.md) and
  [../contracts/truth-contract.md](../contracts/truth-contract.md)
- `unknown`, `unresolved`, `stale`, `withdrawn`, and `unavailable` as first-class outputs every consumer
  must be able to represent
- The rule that **absence of evidence is never evidence of absence**

### Consequences for consumers

- Stewardship evaluates obligations against facts, and reports `unknown` obligation state when the
  governing fact is unknown — never `met`
- Operational Trust treats `unknown` as `undecidable`, never as permission
- Concierge must be able to act, ask, or refuse under uncertainty, and must say so

### Costs accepted

- More states to represent, and more explanation surface
- Composite aggregation left deliberately open (**OD-17**) rather than fixed prematurely

---

## Alternatives considered

| Alternative | Why rejected |
|---|---|
| Keep truth inside Foundation | Merges description with evaluation; leaves confidence and provenance homeless |
| Give each consumer its own derivation | Guarantees conflicting representations of household state |
| Let Concierge arbitrate conflicting evidence | Makes the orchestrator the authority on reality, which is the failure this ADR prevents |

---

## Open decisions

**OD-17** aggregation algorithm and coverage thresholds; **DL-59** (resolved OD-18) validity defaults per fact class;
**OD-19** governed conflict-resolution rules.

---

## Related documents

- [../models/truth.md](../models/truth.md)
- [../contracts/truth-contract.md](../contracts/truth-contract.md)
- [adr-room-configuration-ownership.md](adr-room-configuration-ownership.md)
- [../governance/decision-ledger.md](../governance/decision-ledger.md)
