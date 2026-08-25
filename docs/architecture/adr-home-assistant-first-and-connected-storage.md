# ADR: Home Assistant First, Connected Storage, and Native Experience

> **Document status: Canonical ADR.**
> Status: **Accepted**.
> Terminology: [../models/glossary.md](../models/glossary.md).

---

## Context

HTBW Core will be built greenfield in Home Assistant. Two opposite failure modes were available.

- **Building parallel primitives.** Inventing HTBW's own areas, devices, people, calendars, dashboards,
  and pickers, producing an integration that fights the platform and feels foreign.
- **Collapsing into the platform.** Treating Home Assistant objects as if they were household concepts,
  which destroys the distinctions the framework exists to make — a Device is not an Asset, an Area is
  not a Room, a `person` entity is not a Person.

Additionally, durable household knowledge — documentation, photos, manuals, receipts, appraisals,
vocabulary definitions, participation configuration, obligation history — had no recorded home, and the
repository contained no principle governing where it lives.

---

## Decision

Three principles are adopted: **P21 Home Assistant First**, **P22 Connected Storage**, **P23 Native
Experience**.

### P21 — Home Assistant First

Before HTBW builds a capability, the following review is required:

1. Does Home Assistant already provide this?
2. If yes, use it.
3. If partially, extend it natively rather than replacing it.
4. If no, build it — and record why.

Home Assistant provides areas, floors, devices, entities, the person registry, labels, calendars,
`todo` entities, the logbook, notifications, voice assistants and pipelines, the config-flow and
subentry system, the storage layer, and the frontend component library. HTBW does not reimplement any of
them.

HTBW owns what Home Assistant does not model: Rooms and Merged Rooms as interaction contexts, Room
Configuration, Contextual Vocabulary, Assets as household things, Stewardship obligations and
significance, Identity assertions with confidence, Truth as an authoritative fact engine, Continuity
sessions and preferences, Operational Trust policy, and the Decision Trace.

**Object distinctions are preserved.** A Home Assistant Device, Entity, or Area is never automatically
the same object as an HTBW Asset, Person, Pet, Room, or Service.

### P22 — Connected Storage

Durable household knowledge lives in **attached, household-controlled storage**, not hidden inside an
integration's private state.

Rules:

- Storage is explicitly configured by the household
- Content is human-inspectable where it is human-meaningful
- Content is portable and survives reinstalling the integration
- Every stored artifact carries **explicit traceability** back to the object it describes

Required traceability anchors:

| Anchor | Meaning |
|---|---|
| `HA Device ↔ Asset documentation` | Documents resolve to the asset, and to its backing devices |
| `HA Person ↔ Identity profile` | Identity artifacts resolve to a person |
| `Room Configuration ↔ Vocabulary definitions` | Terms resolve to the Room that defines them |
| `Asset ↔ Obligation history` | Care records resolve to the thing cared for |
| `Decision ↔ Decision Trace` | Explanations resolve to what happened |

Prohibited: storing household knowledge only in integration-private state; storing artifacts with no
resolvable anchor; exposing biometric internals or storage paths.

### P23 — Native Experience

HTBW must present as a **native part of Home Assistant**.

- Use Home Assistant components, pickers, selectors, dialogs, and theme tokens
- Follow Home Assistant configuration and options-flow conventions
- **Do not invent custom UI standards**
- One configuration, many surfaces — voice, panel, and Room Help present the same configured truth

### P25 — Vendor-agnostic framework

**Home Assistant is the first implementation environment, not a constraint on the architecture.** The
seven responsibilities, their contracts, and the assessment traceability model must remain expressible
without reference to any platform.

---

## Consequences

### Established

- [home-assistant-boundary.md](home-assistant-boundary.md) and
  [connected-storage.md](connected-storage.md)
- The object-distinction table binding every model
- The requirement that every stored artifact carries traceability

### Deliberately undecided

The **representation strategy** — whether HTBW objects become config entries, subentries, devices,
entities, registry records, private storage, or a combination — is **OD-01**. Choosing it prematurely
would let a platform mechanism determine the architecture, which P25 forbids.

The storage **format** was **OD-02** and the storage **technology, encryption, and synchronisation**
were **OD-03**. **Both are now closed.** Home Assistant is the storage provider, HTBW locates
artifacts through a governed reference rather than a schema, and file formats remain
capability-specific — recorded as **DL-42**, **DL-43**, **DL-44**, and **DL-45** in
[../governance/decision-ledger.md](../governance/decision-ledger.md).

### Costs accepted

- Mapping HTBW objects onto Home Assistant primitives requires deliberate, documented decisions rather
  than convenient reuse
- Household-controlled storage means household-visible content, which raises the privacy bar rather
  than lowering it

---

## Alternatives considered

| Alternative | Why rejected |
|---|---|
| Build HTBW primitives in parallel with Home Assistant's | Produces a foreign-feeling integration and duplicates platform maintenance |
| Map HTBW objects one-to-one onto HA objects | Destroys the distinctions the framework exists to make |
| Keep all knowledge in integration-private storage | Household knowledge becomes non-portable and invisible |
| Design the architecture around HA's config-entry model | Lets a platform mechanism determine the architecture; violates P25 |

---

## Open decisions

**OD-01** representation strategy; **OD-09** export and deletion mechanics. **OD-02** storage format
and **OD-03** storage technology are **closed** as DL-42, DL-43, DL-44, and DL-45.

---

## Related documents

- [home-assistant-boundary.md](home-assistant-boundary.md)
- [connected-storage.md](connected-storage.md)
- [principles.md](principles.md)
- [../governance/decision-ledger.md](../governance/decision-ledger.md)
