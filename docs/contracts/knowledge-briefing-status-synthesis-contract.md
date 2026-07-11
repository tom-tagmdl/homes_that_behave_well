# Knowledge, Briefing, and Household Status Synthesis Contract

## Purpose

This contract defines the authoritative boundary for Knowledge Experience, Briefing Experience, and Household Status Synthesis Experience.

This contract governs:

- governed inputs
- experience visibility
- explainability
- calm-by-default behavior
- guest-safe limits
- source attribution
- uncertainty handling

This contract does not define:

- runtime synthesis implementation
- ranking algorithms
- orchestration implementation
- OpenAI implementation details

---

## Knowledge Experience Definition

Knowledge Experience is a governed experience that provides information responses derived from authorized knowledge providers.

Knowledge Experience is not:

- source-of-record authority
- identity authority
- memory authority

Knowledge Experience consumes knowledge sources.

Knowledge Experience does not own knowledge sources.

---

## OpenAI Boundary Section

OpenAI may be a knowledge provider.

OpenAI is not:

- source of household truth
- source of calendar truth
- source of email truth
- source of task truth
- source of occupancy truth

OpenAI-generated information must remain attributable.

Uncertainty must remain visible.

---

## Knowledge Experience Categories

### 1. General Knowledge

Governance scope:

- general information responses
- non-household reference knowledge

### 2. Household Knowledge

Governance scope:

- household-relevant information responses
- governed household context responses

### 3. Contextual Knowledge

Governance scope:

- context-aware information responses
- situation-specific reference responses

### 4. Person-Aware Knowledge

Governance scope:

- person-aware response style
- confidence-bounded personalization

### 5. Room-Aware Knowledge

Governance scope:

- room-aware delivery style
- room-sensitive presentation context

### 6. Guided Knowledge Discovery

Governance scope:

- guided discovery of knowledge sources
- explainable knowledge navigation

All categories are governance only.

---

## Knowledge Uncertainty Requirements

Knowledge responses must define:

- uncertainty disclosure
- confidence communication
- source visibility

Prohibited behavior:

- hidden certainty
- hidden source substitution

---

## Briefing Experience Definition

Briefing Experience is a governed experience that aggregates authorized experience inputs into a concise, explainable information summary.

Briefing Experience is not:

- source-of-record authority
- synthesis authority
- orchestration authority

---

## Briefing Input Governance

Briefing may include governed inputs from:

- Weather
- RSS News
- Calendar
- Email
- Tasks
- Shopping
- Messages
- Home Status
- Asset Intelligence Signals

These are inputs.

Briefing does not own them.

---

## Briefing Experience Categories

### 1. Morning Briefing

Governance scope:

- morning-oriented summary presentation

### 2. Daily Briefing

Governance scope:

- day-oriented summary presentation

### 3. Travel Briefing

Governance scope:

- travel-oriented summary presentation

### 4. Schedule Briefing

Governance scope:

- schedule-oriented summary presentation

### 5. Productivity Briefing

Governance scope:

- productivity-oriented summary presentation

### 6. Status Briefing

Governance scope:

- household status-oriented summary presentation

### 7. Household Coordination Briefing

Governance scope:

- coordination-oriented summary presentation

All categories are governance only.

---

## Household Status Synthesis Definition

Household Status Synthesis is a governed experience that presents meaningful household awareness derived from approved signals and governed sources.

Household Status Synthesis is not:

- source authority
- occupancy authority
- event authority
- memory authority

---

## Household Status Inputs

Household Status Synthesis may consume governed inputs including:

- occupancy signals
- environmental signals
- calendar inputs
- task inputs
- shopping inputs
- messages
- household memory
- asset intelligence signals

Inputs remain authoritative.

Status Synthesis consumes them.

---

## What Should I Know

This section governs:

- What should I know?
- What is important?
- What requires attention?

Required behavior:

- align with calm-by-default philosophy
- prefer concise, relevant, low-noise outputs

---

## What Is Going On

This section governs:

- What is going on?
- What is happening in the household?
- What changed recently?

Required behavior:

- derive from governed inputs
- remain explainable and source-linked

---

## Open Loop Signals

This section governs:

- pending actions
- outstanding tasks
- unfinished work
- unresolved conditions

Status synthesis may surface them.

Status synthesis does not own them.

---

## Errands And Coordination Inputs

This section governs:

- shopping coordination
- calendar coordination
- task coordination
- household coordination

These remain input domains.

---

## Calm-By-Default Requirements

Required behavior:

- favor calm ordering over urgent ordering
- minimize noise and repetitive surfaces
- minimize interruptions
- prefer stable, low-surprise synthesis

Prohibited behavior:

- alarmist ordering
- attention inflation
- noisy synthesis

---

## Guest-Safe Limits

Required behavior:

- guest visibility must remain conservative
- guest restrictions must prevent private context disclosure
- guest-safe defaults must avoid personalization by default
- identity uncertainty restrictions must remain explicit

Required statements:

- Guests must not receive private household context.
- Unknown identities must not receive protected context.

---

## Source Attribution Requirements

Every surfaced item must support:

- source visibility
- attribution visibility
- provenance linkage

No hidden sources.

---

## Provenance Relationship

Knowledge, Briefing, and Status Synthesis consume provenance.

Provenance remains authoritative.

No alternate attribution systems allowed.

---

## Household Memory Relationship

Household Memory may contribute context.

Household Memory remains authoritative for memory governance.

These experiences do not own memory.

---

## Explainability Requirements

Human explainability must support:

- Why was this included?
- Why should I know this?
- Why is this important?
- Where did this come from?
- Why was this highlighted?

Machine explainability must support:

- source identifiers
- attribution lineage
- timestamps
- confidence metadata
- provenance references

---

## Non-Rights

Knowledge, Briefing, and Status Synthesis do not own:

- source systems
- occupancy
- memory
- identity
- provenance
- execution

---

## Determinism Requirements

Required rules:

- same governed inputs -> same inclusion result
- same visibility policy -> same output eligibility
- same attribution inputs -> same explanation result

Prohibited behavior:

- hidden source selection
- hidden synthesis logic
- hidden attribution

---

## Knowledge/Briefing/Status Coverage Matrix

| Experience Area | Knowledge | Briefing | Status Synthesis | Source Authority |
|---|---|---|---|---|
| Weather | no | yes | yes | Weather providers |
| RSS News | no | yes | no | RSS providers |
| Calendar | no | yes | yes | Microsoft 365 Calendar |
| Email | no | yes | yes | Microsoft 365 Email |
| Tasks | no | yes | yes | Microsoft To Do |
| Shopping | no | yes | yes | Microsoft To Do |
| Messages | no | yes | yes | governed messaging providers and contracts |
| Home Status | no | yes | yes | Foundation and governed status sources |
| Asset Intelligence | no | yes | yes | Asset Intelligence |
| General Knowledge | yes | yes | no | authorized knowledge providers |
| Coordination Signals | yes | yes | yes | governed productivity and coordination sources |
| Open Loop Signals | no | yes | yes | governed productivity and status sources |

---

## Boundary Review

This contract preserves explicit separation between:

- Knowledge Experience
- Briefing Experience
- Household Status Synthesis
- Household Memory
- Provenance
- Asset Intelligence
- Productivity Experiences
- OpenAI

Separation rules:

- Knowledge Experience provides governed information responses, not source-of-record authority
- Briefing Experience aggregates authorized inputs, not source ownership
- Household Status Synthesis presents derived awareness, not source authority
- Household Memory contributes context without transferring memory authority
- Provenance remains authoritative for attribution and lineage
- Asset Intelligence remains authoritative for significance and environmental interpretation
- Productivity Experiences remain inputs, not source owners
- OpenAI may contribute knowledge only within governed knowledge boundaries

Ownership overlap is prohibited.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Knowledge, Briefing, and Household Status Synthesis.

Future planning must treat this contract as a mandatory dependency for:

- E12 governance validation
- E13 productivity experience planning
- E14 provenance consumption

This contract package is authoritative input for roadmap planning and future quality gates.

---

## Final Principle

Knowledge, Briefing, and Household Status Synthesis are governed experience layers that consume authoritative sources, preserve calm-by-default behavior, and remain explainable, guest-safe, and attribution-bound.