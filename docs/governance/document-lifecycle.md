# Document Lifecycle

> **Document status: Canonical governance.**
> Authority: [authority-order.md](authority-order.md).

---

## Purpose

Every Markdown file in this repository has a status. **No HTBW Markdown file may be unclassified.**

---

## Statuses

| Status | Meaning | Authority |
|---|---|---|
| **Canonical (constitutional)** | Defines the framework itself | Subordinate only to [../architecture/north-star.md](../architecture/north-star.md) |
| **Canonical** | Defines a responsibility, model, contract, or governance rule | Rank 3 in the authority order |
| **Active — subordinate** | Currently useful and consistent with canon, but not itself authoritative | Rank 4; canon prevails on conflict |
| **Historical — superseded** | Predates the refoundation and conflicts with canon | Rank 4/5; retained as evidence only |
| **Historical illustration** | A worked example retained for context, replaced by a canonical scenario | Evidence only |
| **Operational** | Checklists, development guides, and process documents | Non-architectural |

---

## Banner templates

Every file carries its banner immediately after the H1 title.

> The link paths in the templates below are **illustrative**. `<Responsibility>`, `<name>`, and
> `<path>` are placeholders, and every relative path must be rewritten relative to the directory of
> the file the banner is placed in. These template blocks are fenced examples and are deliberately
> excluded from link validation.

### Canonical (constitutional)

```markdown
> **Document status: Canonical (constitutional).**
> Subordinate only to [north-star.md](north-star.md).
> Terminology: [docs/models/glossary.md](../models/glossary.md).
```

### Canonical

```markdown
> **Document status: Canonical model.**
> Terminology: [glossary.md](glossary.md). Owning responsibility: **<Responsibility>**.
> Contract: [../contracts/<name>-contract.md](../contracts/<name>-contract.md)
```

### Active — subordinate

```markdown
> **Document status: Active — subordinate to the HTBW canonical architecture.**
> Canonical authority: [docs/architecture/framework.md](framework.md) and
> [docs/models/glossary.md](../models/glossary.md).
> Where this document conflicts with canonical authority, canonical authority prevails.
```

### Historical — superseded

```markdown
> **Document status: Historical — superseded by the HTBW constitutional refoundation.**
> This document predates the refoundation recorded in
> [docs/governance/decision-ledger.md](../governance/decision-ledger.md).
> It is retained as architectural evidence. It is **not** current authority.
> Canonical replacement: [<name>](<path>).
> Canonical terminology: [docs/models/glossary.md](../models/glossary.md).
```

### Historical illustration

```markdown
> **Document status: Historical illustration.**
> Retained as a worked example from the pre-refoundation exploration.
> Canonical scenarios: [docs/scenarios/README.md](../../docs/scenarios/README.md).
> Terminology in this document may be superseded; see
> [docs/models/glossary.md](../../docs/models/glossary.md).
```

---

## Supersession procedure

1. Create or identify the canonical replacement.
2. Add the Historical banner to the superseded document, naming the replacement explicitly.
3. Record the supersession in [decision-ledger.md](decision-ledger.md).
4. Update the disposition in [document-register.md](document-register.md).
5. **Do not delete the superseded document.** Evidence is preserved.

---

## Rules

1. A document may not claim authority it does not have. A banner is required, not optional.
2. Superseded terminology inside a historical document is **not** rewritten. The banner directs the
   reader to [../models/glossary.md](../models/glossary.md).
3. A canonical document must not link to a historical document as its authority.
4. A historical document may be cited as evidence, provenance, or origin of a preserved discovery.
5. Partial supersession is expressed inside the document — see the Historical appendix pattern in
   [../contracts/concierge-contract.md](../contracts/concierge-contract.md).
6. Every new Markdown file must be added to [document-register.md](document-register.md).

---

## Dispositions used in the register

| Disposition | Meaning |
|---|---|
| **Keep** | Unchanged and consistent with canon |
| **Revise** | Retained with a status banner applied |
| **Supersede** | Replaced by a canonical document; banner names the replacement |
| **Merge** | Content absorbed into a canonical document; original retained as evidence |
| **Archive** | Retained for history only; no ongoing role |
| **New** | Created by the refoundation |

**No file is deleted by the refoundation.**

---

## Related documents

- [authority-order.md](authority-order.md)
- [document-register.md](document-register.md)
- [decision-ledger.md](decision-ledger.md)
