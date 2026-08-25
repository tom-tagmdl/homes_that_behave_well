# HTBW Contracts

> **Document status: Canonical index.**
> Terminology: [../models/glossary.md](../models/glossary.md).
> Framework authority: [../architecture/framework.md](../architecture/framework.md).

---

## What a contract is

A contract is the **explicit boundary** of a responsibility. It states what may be relied upon, what
must never be assumed, and what happens when the responsibility cannot answer.

Contracts exist because of two principles:

- **P3 — Every boundary requires an explicit contract.**
- **P4 — No responsibility may quietly assume another's data.**

A contract is not an API specification. HTBW contracts are **vendor-agnostic**: they describe
obligations between responsibilities, not transport, schema, or platform mechanics.

---

## Required sections of a contract

Every canonical contract states:

1. Owning responsibility
2. What it guarantees
3. What it will never guarantee
4. What consumers may rely upon
5. What consumers must never assume
6. Uncertainty and unknown representation
7. Failure and degradation behavior
8. Privacy constraints
9. Explainability contributions
10. Open decisions

---

## Canonical contracts

| Contract | Responsibility | Question |
|---|---|---|
| [foundation-contract.md](foundation-contract.md) | Foundation | What exists, and how do we describe it? |
| [room-configuration-contract.md](room-configuration-contract.md) | Foundation | What participates, what is exposed, and who may act here? |
| [contextual-vocabulary-contract.md](contextual-vocabulary-contract.md) | Foundation | What do you call this, here? |
| [stewardship-contract.md](stewardship-contract.md) | Stewardship | What matters, and what must be cared for? |
| [identity-contract.md](identity-contract.md) | Identity | Who do we believe this is? |
| [truth-contract.md](truth-contract.md) | Truth | What is actually true now? |
| [continuity-contract.md](continuity-contract.md) | Continuity | What should be remembered, resumed, or transferred? |
| [operational-trust-contract.md](operational-trust-contract.md) | Operational Trust | What is allowed? |
| [concierge-contract.md](concierge-contract.md) | Concierge | What should happen now? |

---

## Universal contract rules

These apply to every contract above.

1. **Uncertainty is a first-class output.** `unknown`, `ambiguous`, and `unavailable` are valid
   answers and must be representable by every consumer.
2. **Absence of evidence is never a positive assertion.** Not-observed is not not-present. Not-known
   is not compliant. Not-prohibited is not permitted.
3. **No consumer may re-derive a producer's output.** If Truth is unavailable, a consumer must not
   compute its own facts from raw evidence.
4. **No consumer may promote a weaker statement into a stronger one.** An identity assertion must not
   be recorded as a presence fact. A learned suggestion must not be recorded as policy.
5. **Every contract output carries provenance** sufficient for a Decision Trace.
6. **Every contract fails closed.** Degradation reduces capability; it never expands authority.
7. **No cycles.** See [../architecture/dependency-view.md](../architecture/dependency-view.md).

---

## Historical contracts

The pre-refoundation contracts in this directory are retained as architectural evidence. Their
disposition is recorded in
[../governance/document-register.md](../governance/document-register.md). Where they conflict with a
canonical contract, the canonical contract prevails.

---

## Related documents

- [../architecture/framework.md](../architecture/framework.md)
- [../architecture/dependency-view.md](../architecture/dependency-view.md)
- [../architecture/failure-and-degradation.md](../architecture/failure-and-degradation.md)
- [../governance/authority-order.md](../governance/authority-order.md)
