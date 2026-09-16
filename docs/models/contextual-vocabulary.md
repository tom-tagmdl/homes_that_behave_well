# Contextual Vocabulary Model

> **Document status: Canonical model.**
> Terminology: [glossary.md](glossary.md). Owning responsibility: **Foundation**, as part of
> [room-configuration.md](room-configuration.md).
> Contract: [../contracts/contextual-vocabulary-contract.md](../contracts/contextual-vocabulary-contract.md)

---

## Purpose

Residents speak household language. The platform speaks platform language. Contextual Vocabulary is
the explicit, persisted bridge between them, scoped to a Room.

## Question answered

*What do you call this, here?*

---

## What residents must never need to know

- Home Assistant entity IDs
- Home Assistant device names
- Manufacturer names
- Model names
- Formal asset names
- Internal service names
- The individual member names of an explicitly configured group

---

## Mapping examples

| Vocabulary Term | Maps to |
|---|---|
| **Lights** | explicitly selected overhead ceiling lights |
| **Lamps** | explicitly selected table or floor lamps |
| **Shades** | explicitly selected shades in the Room |
| **Speakers** | explicitly selected Sonos music speakers |
| **TV** | the explicitly selected LG television |
| **Media Player** | the explicitly selected Apple TV |
| **Piano** | the asset whose authoritative name is *1918 A.B. Chase 6' Grand Piano* |

---

## The platform domain must not dictate household vocabulary

Home Assistant may classify several devices as `media_player`, while HTBW Room Vocabulary
distinguishes:

- Speakers
- TV
- Media Player

Home Assistant may classify both ceiling fixtures and table lamps as `light`, while HTBW Room
Vocabulary distinguishes:

- Lights
- Lamps

**This household distinction is preserved. The device domain is an implementation detail, not a
household concept.**

---

## Rules

1. **Vocabulary is explicitly configured.** A term exists because the household created it.
2. **Vocabulary is persisted.** It survives restarts, reconfiguration, and platform upgrades.
3. **Vocabulary is deterministic.** The same term in the same Room resolves to the same target set
   every time.
4. **Vocabulary resolution must not require a runtime search of all devices in the Room.**
5. **Vocabulary resolution must not rely on guessing from entity names.**
6. **Vocabulary does not rename or replace the authoritative asset.** It provides a human interaction
   term within the configured Room context.
7. **The same word may have different configured targets in different Rooms.** "Speakers" in the Den
   is not "Speakers" in the Living Space.
8. **A derived recognition form is subordinate to the configured term it came from.** It never becomes
   a vocabulary entry, and a configured term always outranks it.

---

## What a term may resolve to

- One asset
- Multiple assets
- A configured asset group
- A controllable capability
- A knowledge asset
- An experience endpoint

A term that resolves to a group is addressed as one thing. The resident says "Shades", and seven
configured shades respond, without the resident knowing there are seven.

---

## Ownership

> **Do not define vocabulary as owned by Concierge.**
>
> **Room Configuration owns the mapping. Concierge consumes the resolved target.**

| Step | Owner |
|---|---|
| Define the term and its target set | Room Configuration |
| Persist the mapping | Room Configuration |
| Resolve term → target set for a Room Context | Room Configuration |
| Decide whether the resolved action is permitted | Operational Trust |
| Decide what should happen | Concierge |
| Execute | Concierge, through governed interfaces |

### Resolution compiles down to native targets

A resolved target set should **compile or map to native Home Assistant target concepts and intent
slots** — entities, devices, Areas, labels, domains, and device classes — so that execution and
voice handling use the platform rather than a parallel mechanism.

> **HTBW vocabulary remains richer than the native concept, and must not be reduced to Home Assistant
> entity aliases.** It carries Room-scoped meaning, participating assets, explicit exclusions,
> configured capability exposure, and Merged Room semantics. A native alias carries none of those.

---

## Native names and aliases

**OD-14 is resolved: native naming information is an *input*, and never an *authority*.** Governed by
**DL-31** and
[../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md).

Home Assistant documents that Assist uses *"the names of your entities, areas and floors, as well as
any aliases you've configured"*, that aliases may be added to an **entity, an Area, or a Floor**, and
that configured aliases *"are not only used by Assist, but can also be used by Google Assistant"*.

| Object | Home Assistant owns | HTBW behaviour |
|---|---|---|
| Native name | The Device or Entity name, including any registry name the resident set | **Read through the native reference.** Never duplicated as an independently maintained HTBW name |
| Native Assist alias | The alias, on the objects Home Assistant documents — **entity, Area, and Floor** | **Read.** May seed a term. Never overwritten by HTBW, and never a second store |
| Native Assist exposure | Whether an assistant may target the entity | A platform boundary HTBW may narrow and must never bypass |
| Contextual Vocabulary term | Nothing | **HTBW extension, held by reference to the native target** |

> **No native Device-level alias is documented.** Do not assert one. Do not describe native aliases as
> globally unique, globally conflicting, Area-scoped, Device-scoped, or assistant-scoped — Home
> Assistant documents none of those characterisations, and explicitly describes the **same alias
> applied to entities in different Areas**, matched in conjunction with the Area name.

### Seeding

When a native Device or Entity first becomes a participating target and no term exists for it, HTBW
may **seed** the term from native naming information.

A seed is a **starting point**. It is not a second authority, not continuous synchronisation, not a
permanent copy, and not an instruction to write anything back. It carries no claim that the native
name is the best household term.

Applicable native sources, in order of applicability: an applicable native Assist alias; the native
Entity name; the native Device name; any other documented native display name; and, only as a
deterministic fallback, a value derived from a native identifier.

**Where several native aliases apply, HTBW must not silently choose one.** All applicable native
values are offered as selectable seeds, attributed to Home Assistant, and none becomes active
vocabulary without acceptance. **Home Assistant does not document a precedence among an object's
aliases**, so no precedence is asserted; which seed is offered first is an implementation mapping, not
an architectural decision, and it does not reopen this model.

### The seed-once lifecycle

Seed status is a value of the **mapping source** this model already records for explainability. **It
is not a new model.**

| Mapping source | Meaning | Behaviour when the native value later changes |
|---|---|---|
| `native_seed` | Proposed from a native value; not yet accepted; no term is active | May be refreshed from the native value |
| `accepted_native_seed` | The resident accepted the native value unchanged | May be refreshed **only** where the accepted lifecycle permits it |
| `household_defined` | The resident supplied or edited the term | **Never automatically overwritten.** HTBW may surface that the native value changed and offer re-import |

A term whose target no longer resolves is `broken_mapping`; a term the household withdraws is removed
through the ordinary Room Configuration lifecycle, and its history is retained. **Seed status and
resolution state are different axes and must not be collapsed.**

### No automatic write-back

> **HTBW must never automatically write Room-scoped Contextual Vocabulary into native Home Assistant
> aliases.**

The rule does **not** rest on a claim that Home Assistant treats aliases as globally conflicting — the
documentation states the opposite for Area-disambiguated cases. It rests on four differences that the
documentation does support:

1. **A native alias is shared beyond Assist.** Home Assistant documents that configured aliases may
   also be used by Google Assistant. Writing an HTBW term back would change behaviour outside HTBW,
   in a surface HTBW does not govern.
2. **An HTBW term may not name a single entity at all.** It may resolve to a configured group, a
   capability, a knowledge asset, or an experience endpoint. There is no native alias equivalent.
3. **HTBW Room context is not Area context.** A Room may span Areas, and a Merged Room changes the
   applicable target set without changing any native object.
4. **Participation and explicit exclusion are not representable as an alias.** The Beam's exclusion
   from *Speakers* is configuration, and an alias cannot carry it.

Equally, **HTBW never automatically imports native alias changes over a household-defined term.**
Divergence between the native name and the household term is **intentional and supported**, and
nothing in either direction is synchronised.

An explicit, separate, resident-initiated action to publish an eligible object-scoped term as a native
alias is **neither required nor adopted here**. Home Assistant documents alias editing as a resident
interface action; **no integration-facing alias-writing capability is documented**, so none is claimed.
Were such an action ever adopted, it would have to be explicit, separate from saving a Room
Configuration, validated, limited to a term naming exactly one native object, never used for a group or
context-dependent term, never a means of altering exposure, and clearly identified as changing native
Home Assistant configuration. **The canonical behaviour remains no write-back.**

### Groups stay in HTBW

A term resolving to a group is a Room Configuration mapping. **HTBW does not write the group term as
an alias onto every member.** Native targets are referenced, not copied.

Where a native target concept — an Area, a Floor, a label, a domain, a device class, or a documented
intent slot — already expresses the required set safely, **prefer the native target** and record which
native representation was used. Retain HTBW resolution only where Room-specific participation,
exclusions, grouping, or household meaning is additionally required. **Do not construct a duplicate
group for convenience.**

### Merged Rooms

A Merged Room is a Room, and vocabulary behaves identically in one. Because **participation in a
Merged Room is explicit and never inherited automatically**, merged vocabulary is **declared** in the
Merged Room's configuration rather than accumulated from its constituents. Where constituent Rooms use
the same term for different targets and the merged configuration does not declare the outcome, the
result is `ambiguous` and is surfaced, not guessed. Explicit exclusions survive merging, constituent
membership is retained so unmerging restores constituent behaviour, and **no native alias changes at
any point**. **A Merged Room has no native projection: DL-68 (resolved OD-70) found no proven consumer
requiring one, and Assist/Conversation must never receive one**, because this model's own resolution
rule above means HTBW already compiles a term to a concrete governed target set before any native
targeting occurs — a native stand-in would let Home Assistant's built-in conversation agent bypass
that curation entirely.

---

## Changing or withdrawing a term — the household consequence is open

This model governs how a term **comes into existence**: it is created by the household, may be seeded
from a native value, resolves deterministically, and becomes `broken_mapping` when its target no longer
resolves. Of removal it says only that a term the household withdraws is **removed through the ordinary
Room Configuration lifecycle, and its history is retained**.

> **History retained is not habit preserved.** **What the home owes the people who still use the old
> word is not settled, and is OD-86.**

Open there, and deliberately unanswered here: whether a superseded term is recognised at all and for how
long; whether the home may say that a word it once understood is no longer configured, and which
responsibility says it; how a change is explained afterwards, given that under **P30** a Decision Trace
references the exact vocabulary version and so remains accurate while the household habit does not;
what is owed regarding household-authored automations, scripts, and scenes that named the previous
target; and what becomes of retained references and of Continuity values captured under the earlier
term.

**Nothing is asserted here.** **No transitional alias, deprecation window, grace period, or withdrawal
behaviour is introduced by recording this**, and none may be inferred from it. Rule 6 stands unchanged:
vocabulary never renames or replaces the authoritative asset. HTBW references household automations as
named executors and **never rewrites, wraps, or migrates them**.

**This question exists because it was once owned and was not carried forward.** The superseded
`adr-room-vocabulary-governance.md`, `room-vocabulary-registry-contract.md`, and
`room-vocabulary-registry-model.md` carried a *managed vocabulary lifecycle*. **They are Historical and
are not reactivated** — they are evidence that the question existed, never authority for its answer.

**Inheritance across scopes is a different question and remains OD-13.**

---

## Recognition forms

**A resident configures one term. HTBW may derive additional forms of that term so that ordinary
speech is understood.** A recognition form is a **projection of the configured term** — the same
pattern **DL-31** applies to native objects — and never a second vocabulary record.

| Authoritative term | May be recognised as |
|---|---|
| Lamp | Lamp, Lamps |
| Shade | Shade, Shades |
| Speaker | Speaker, Speakers |
| Shades | Shades, Shade |

> **The authoritative term is whatever the household configured, in whatever form they chose.** This
> model's own examples — *Lights*, *Lamps*, *Shades*, *Speakers* — are plural, and remain valid
> exactly as configured. **HTBW must not require a singular term, must not rewrite a configured term
> into another form, and must not add a second field for any other form.**

A recognition form is:

- **generated**, from the configured term alone
- **not independently configured, owned, exposed, or persisted as vocabulary**
- **traceable** to the authoritative term, and explainable
- **resolved to exactly the authoritative term's target set** — nothing more and nothing less

> **Derivation never reads the target.** A recognition form is derived from the configured term, never
> from a native name, an alias, an entity ID, a device class, or a domain. Rule 5 — *resolution must
> not rely on guessing from entity names* — is unchanged and unweakened.

### A configured term always wins

| Situation | Outcome |
|---|---|
| The spoken word matches a configured term in this Room | The configured mapping resolves. **Derivation is not consulted at all** |
| It matches only a derived form of one configured term | That term resolves, to that term's target set |
| It matches derived forms of two or more configured terms, and no configured term | `ambiguous`. Ask which was meant. **Never guess** |

This uses the resolution states this model already defines. **It is not a new state model, and it
adds no new field.**

### Grammatical form is not group meaning

**Pluralisation does not multiply targets.**

| Concept | What it is | Where it comes from |
|---|---|---|
| *Lamps* as a **recognition form** of *Lamp* | The same meaning, said differently | Derived |
| *Lamps* as a **group term** — the Corner, Sofa, and Bookcase lamps | A different, larger target set | **Explicitly configured**, as *Groups stay in HTBW* above |

Where the household has configured *Lamps* as a group, that configured mapping resolves — because a
configured term always wins. **A plural form alone never creates, implies, or expands a group**, and
nothing here changes existing group behaviour.

### Language, display, and scope

Derivation is **language-dependent**. HTBW must not assume the morphology of one language applies to
another. Where a form cannot be derived safely, **HTBW derives nothing** and the configured term still
resolves exactly as configured.

Residents may be shown which forms will be understood, alongside the term they configured, so that
behaviour is visible rather than hidden. **The display is read-only and derived; only the
authoritative term is editable.** This is an architecture expectation — it prescribes no frontend
technology, layout, or component, and requires no additional stored value.

Recognition forms participate exactly as their authoritative term participates — in Room Help,
participation, exposure, authority, target resolution, and Merged Rooms alike. **They introduce no
Merged Room semantics of their own**, and **OD-70** remains untouched.

---

## Knowledge assets

A vocabulary term may resolve to a knowledge asset rather than a controllable capability.

```
Authoritative asset name:  1918 A.B. Chase 6' Grand Piano
Room vocabulary term:      Piano
Resident asks:             "Tell me about the piano"
Resolution:                Room Context → term "Piano" → that asset → asset knowledge
```

The asset's authoritative identity is unchanged. The vocabulary term is an interaction alias, not a
rename.

---

## Consumes

- The Room's participation set from [room-configuration.md](room-configuration.md)
- Foundation asset identifiers and capability descriptions

## Provides

- Deterministic term → target-set resolution scoped to a Room
- The exposed-term list used by Room Help
- Configuration provenance for explainability

---

## Explicit non-responsibilities

Contextual Vocabulary does **not**:

- Decide whether the resolved action is permitted
- Decide what should happen
- Rename the authoritative asset
- Discover targets at runtime
- Infer meaning from entity naming conventions

---

## Failure behavior

| Condition | Behavior |
|---|---|
| Term not configured in this Room | State that the term is not configured here. Offer to show what is available. Never runtime-search. |
| Term maps to targets that no longer exist | Report a broken mapping as a configuration problem. Do not silently substitute. |
| Term maps ambiguously (two configured mappings match) | Ask which was meant, offering only exposed options. Record the ambiguity. |
| Term resolves to a partially available group | Apply the configured partial-availability policy; report which members were unavailable. |
| The Room Context is unresolved | Do not attempt vocabulary resolution. Resolve the Room first. |

## Privacy considerations

Exposing a term makes a capability discoverable by anyone who can speak in the Room. Sensitive
capabilities must be protected by Operational Trust authority, not by an obscure term.

## Explainability requirements

Every resolution records: Room Context, term, resolved target set, mapping source. Every failed or
ambiguous resolution records the reason and what the resident could do about it.

Where a derived recognition form was matched, the resolution records **the form heard and the
authoritative term it resolved to**, so that the household can see why a word was understood.
Explanations are still spoken in the household term. **Residents are never required to understand
linguistic mechanics to receive a usable explanation.**

---

## Representative scenarios

- [../scenarios/room-vocabulary.md](../scenarios/room-vocabulary.md)

## Open decisions

| ID | Question |
|---|---|
| OD-02 | **Closed — DL-43, DL-44, DL-45.** Vocabulary definitions are located through a governed artifact reference; encoding remains capability-specific |
| OD-13 | Whether vocabulary terms may be inherited from Home scope and overridden per Room |
| OD-14 | **Resolved.** Native aliases are an **input** — a seed — and never an authority. See *Native names and aliases* above |
| OD-86 | **What the home owes the household when a term is changed, retargeted, or withdrawn.** Raised 2026-08-27. See *Changing or withdrawing a term* above. A wake-word change is admissible there only as a household-vocabulary sub-question and remains deferred behind **#146** |

## Related documents

- [room-configuration.md](room-configuration.md)
- [room.md](room.md)
- [../contracts/contextual-vocabulary-contract.md](../contracts/contextual-vocabulary-contract.md)
- [../architecture/home-assistant-boundary.md](../architecture/home-assistant-boundary.md)
