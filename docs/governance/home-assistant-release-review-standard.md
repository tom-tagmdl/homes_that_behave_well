# Home Assistant Release Review Standard

> **Document status: Operational.**
> A **repeatable process standard**. It defines *how* a monthly Home Assistant release review is
> conducted and *what* it must produce.
> **This document is not architecture-of-record and creates no authority.** It decides nothing,
> classifies nothing, and grants no responsibility. Where it disagrees with
> [decision-ledger.md](decision-ledger.md), [authority-order.md](authority-order.md), or any canonical
> model or contract, **those prevail and this document is wrong**.
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Why this document exists

**P21 Home Assistant First** and the **DL-30** ordered burden of proof are *preconditions* evaluated
when HTBW proposes a construct. They are triggered by an HTBW proposal, never by the calendar.

That leaves a gap this standard closes: **Home Assistant changes every month, and HTBW had no
recurring obligation to look.** The three P21 capability reviews recorded in
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) are pinned to
**documentation version 2026.8.2** with no re-verification trigger, no owner, and no staleness rule.
A verified capability can silently become a stale claim, and a planned HTBW capability can silently
become duplicative.

**A monthly review is a verification obligation, not a decision-making forum.** It produces evidence.
It never accepts architecture, never closes an open decision, and never closes a GitHub issue.

---

## Cadence and trigger

| Element | Rule |
|---|---|
| **Trigger** | Publication of an official Home Assistant Core monthly release blog post |
| **Cadence** | Once per release, within the release month |
| **Also in scope** | Patch releases published for that version, and developer-blog posts linked from that release |
| **Owner** | HTBW repository execution agent, under Tom Grounds' review |
| **Terminating?** | **No.** This is a standing obligation, unlike the one-time verification backlog in **#146** |
| **Output location** | One GitHub issue per release, linked to Epic **#147**, plus any bounded documentation synchronisation it justifies |

**A month with no material change is a valid and complete outcome.** It is recorded as such, with the
sources reviewed, and it is not a failure.

---

## 1. Required review scope

Each monthly review must review, and record as reviewed:

- Official Home Assistant release notes, including the backward-incompatible changes section
- Linked official developer documentation and developer-blog posts
- Relevant official architecture documentation
- Relevant Core and Frontend source code, where documentation is insufficient
- Relevant pull requests, architecture discussions, and issues
- Integration quality-scale requirements
- Deprecations, with their announced removal versions
- Backward-incompatible changes
- Accessibility changes
- Security changes
- Configuration and setup patterns, including config flows and options flows
- Native entities, devices, persons, areas, floors, and labels
- Events, services, actions, context, traces, storage, Recorder, diagnostics, repairs, and logging
- Assist, voice, conversation, and resident-interaction capabilities
- HACS and custom-integration implications

**A scope element that was checked and found to contain nothing material is recorded as checked.**
An unrecorded element is an unmet obligation, not an absence of change.

---

## 2. Required determination per material change

For every **material** change, the review records all ten of the following. A change is *material*
when it touches a responsibility, a cross-cutting concern, a named HTBW requirement, a governed
artifact, or an open decision. Fewer than ten answers is an incomplete determination.

| # | Determination |
|---|---|
| 1 | **What changed** |
| 2 | **How Home Assistant implemented it** |
| 3 | **Which native architecture or extension point is available** |
| 4 | **Which HTBW responsibility or cross-cutting concern is affected** |
| 5 | **Which ADR, decision, contract, model, architecture document, implementation component, test, roadmap item, or GitHub issue is affected** |
| 6 | **Whether Home Assistant satisfies the HTBW requirement** — `Fully` / `Partially` / `Not at all` / `Differently, requiring reconciliation` |
| 7 | **What HTBW should do** — `Adopt` / `Reuse` / `Extend` / `Integrate` / `Simplify` / `Retire` / `Preserve unchanged` / `Research further` |
| 8 | **What HTBW work would become duplicative** |
| 9 | **What differentiated HTBW requirement remains** |
| 10 | **What evidence supports the conclusion** |

**Every conclusion is classified**, using the classes already required by
[htbw-architecture-execution-grounding-standard.md](htbw-architecture-execution-grounding-standard.md):
confirmed repository state, confirmed Home Assistant behaviour, confirmed implementation behaviour,
architectural analysis, recommendation, question requiring technical validation, or question
requiring Tom Grounds' eyes-and-ears validation.

**An unverifiable capability is recorded as unverified, never as absent.** Under **DL-30**, an
undocumented evaluation does not discharge the burden, and treating missing documentation as a
missing capability is prohibited.

---

## 3. Required Open-Issue Impact Review

Every monthly review performs an impact review against Epic **#147** and all materially related
issues, and identifies:

- Newly discovered architectural evidence
- Existing issues changed by the Home Assistant developments
- Issues whose acceptance criteria may now be **partially** or **fully** satisfied by Home Assistant
- Candidate formal acceptance reviews
- Dependency and sequencing changes
- Contradictions, whether repository-versus-platform or repository-versus-repository
- Duplicate HTBW work that may be removed
- New issues that may be required
- ADR, contract, model, documentation, implementation, and test updates required

---

## 4. Prohibitions

- **No issue is closed automatically.** Formal acceptance review remains a separate step.
- **No accepted decision is reopened** by a monthly review. A platform change that appears to
  contradict an accepted decision is recorded as a contradiction and routed to an open decision or a
  new one, under the ledger's own maintenance rules.
- **No new open-decision identifier is allocated without a ledger row first.**
- **No HTBW capability is built, simplified, or retired by a monthly review.** The review recommends;
  a governed decision disposes.
- **A new Home Assistant capability does not by itself justify an HTBW capability.** The **DL-30**
  ladder still applies in order, and *HTBW builds nothing* remains a passing outcome under **P21**.
- **A monthly review does not install or upgrade Home Assistant.** Where development-environment
  validation is required, the repository's existing deployment scripts are used, and Home Assistant
  eyes-and-ears validation remains Tom Grounds' responsibility.

---

## 5. Required output

One GitHub issue per release, titled `Home Assistant <version> Architecture-Impact Review`, linked to
Epic **#147**, containing:

1. Release identifier, publication date, and the exact release-notes URL
2. Every source reviewed, with links, and the review classification of each
3. The material-change table, with all ten determinations per row
4. Explicit "checked, nothing material" entries for the remaining scope elements
5. The Open-Issue Impact Review
6. Governance comments posted, and to which issues
7. Documentation synchronisation performed, if any, with exact paths and headings
8. Items requiring Tom Grounds' eyes-and-ears validation
9. Items explicitly deferred
10. An explicit statement that no issue was closed automatically

A row in the **Non-decision governed work** table of
[open-decision-issue-index.md](open-decision-issue-index.md) records the standing process and each
release review.

---

## 6. Relationship to the one-time verification backlog

**#146** is a *terminating* backlog: it verifies a fixed list of capabilities so that ten blocked open
decisions can close, and its exit criteria end it. **This standard is not terminating.**

They interact in one direction only: a monthly review may **supply evidence to** a #146 item, or
**add an item to** #146 where a release exposes a new undischarged burden. A monthly review never
discharges a #146 item on its own authority, and never closes #146.

---

## 7. Staleness of prior reviews

Each P21 capability review recorded in
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md) states the
documentation version it was conducted against. **A monthly review must check whether that release
invalidated any previously verified row**, and if it did, record the affected row, the change, and
the resulting burden status. A verified row that a later release contradicts becomes **unverified**
again, and any decision that relied on it is reported as relying on stale evidence.

---

## Related documents

- [authority-order.md](authority-order.md)
- [decision-ledger.md](decision-ledger.md) — **DL-16**, **DL-30**, **DL-31**, **DL-41**, **DL-42**, **DL-46**
- [open-decision-issue-index.md](open-decision-issue-index.md)
- [htbw-architecture-execution-grounding-standard.md](htbw-architecture-execution-grounding-standard.md)
- [../architecture/principles.md](../architecture/principles.md) — **P21**
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
- [../architecture/connected-storage.md](../architecture/connected-storage.md)
