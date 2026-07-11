# ADR: Household Productivity Experience Governance Boundaries

## ADR Number

ADR-010

## Status

Accepted.

## Context

Household Productivity Experiences are first-class HTBW experience domains.

These experiences deliver household-facing outcomes by assembling governed provider context with governed HTBW context.

Without a dedicated governance ADR, productivity behavior can drift into source-of-record confusion, hidden synthesis, guest-unsafe visibility, and ownership boundary violations.

This ADR establishes architecture authority for Calendar, Email, Task, Shopping, Multi-Item Voice Capture, Knowledge, Briefing, and Household Status Synthesis experiences.

## Decision

### Productivity Experience Definition

Productivity Experience is:

A governed household-facing experience that assembles and presents productivity-related context, status, actions, and synthesis using authoritative provider systems and governed HTBW context.

Productivity Experience is NOT:

- a provider system
- a mailbox
- a calendar system
- a task system
- a shopping system
- a knowledge authority
- a source-of-record system

### Household Productivity Experience Domain Boundary Matrix

| Domain | Purpose | System Of Record | Experience Role | Ownership Boundary |
|---|---|---|---|---|
| Calendar Experience | schedule awareness and planning outcomes | configured calendar providers | assemble and present governed calendar context | calendar providers remain authoritative |
| Email Experience | communication awareness and summarization outcomes | configured email providers | assemble and present governed email context | email providers remain authoritative |
| Task Experience | task awareness and status outcomes | configured task providers | assemble and present governed task context | task providers remain authoritative |
| Shopping Experience | household shopping awareness and list outcomes | configured shopping providers | assemble and present governed shopping context | shopping providers remain authoritative |
| Multi-Item Voice Capture Experience | governed capture of multiple list or task items from one utterance | configured shopping and task providers | present deterministic, explainable capture outcome for provider execution paths | capture experience does not own parser authority or provider state |
| Knowledge Experience | governed knowledge retrieval outcomes | configured knowledge systems | retrieve and present explainable knowledge context | knowledge systems remain authoritative |
| Briefing Experience | cross-domain synthesized awareness outcome | provider systems and governed context domains | synthesize and present briefing output | briefing is synthesis and not source ownership |
| Household Status Synthesis Experience | cross-domain household status synthesis outcome | foundational and provider source domains | synthesize explainable household status context | synthesis is derived context and not source truth |

### Calendar Experience Governance

Calendar Experience supports:

- event awareness
- schedule awareness
- schedule summarization
- day planning
- availability understanding

Calendar provider remains system of record.

Experience consumes governed context.

Experience does not own calendar data.

### Email Experience Governance

Email Experience supports:

- email awareness
- summarization
- prioritization context
- communication context

Email provider remains system of record.

Experience does not become mailbox authority.

### Task Experience Governance

Task Experience supports:

- task review
- task awareness
- task summarization
- task status context

Task provider remains system of record.

### Shopping Experience Governance

Shopping Experience supports:

- shopping list awareness
- shopping list review
- item tracking
- household shopping context

Shopping systems remain systems of record.

### Multi-Item Voice Capture Experience

Multi-Item Voice Capture Experience governs multi-item requests such as adding multiple shopping or task items in one utterance.

Governance requirements:

- deterministic capture expectations
- explainable parsing outcomes
- person-aware ownership handling under governed identity and personalization constraints
- guest-safe behavior with conservative visibility and execution boundaries

This ADR governs experience boundaries only and does not define parsing implementation logic.

### Knowledge Experience Governance

Knowledge Experience supports:

- answering questions
- presenting governed knowledge context
- explainable knowledge retrieval

Knowledge retrieval does not create knowledge ownership.

Knowledge systems remain authoritative.

### Briefing Experience Governance

Briefing Experience may consume:

- calendar information
- email information
- tasks
- shopping
- household memory
- household status
- knowledge context

Briefing is synthesis.

Briefing is not source ownership.

### Household Status Synthesis Governance

Household Status Synthesis may synthesize:

- room status
- occupancy
- presence
- environmental status
- tasks
- schedules
- alerts
- household memory

Synthesis is derived context.

Synthesis is not a source of truth.

### Person-Aware Boundaries

Productivity Experiences must define deterministic, explainable behavior for:

- household member
- enrolled person
- guest
- unknown user
- low-confidence attribution

Person-aware behavior in productivity domains must align with:

- ADR-008 Personalization Governance
- identity governance constraints

### Guest-Safe Requirements

Guest behavior must:

- avoid private context disclosure
- avoid identity assumption
- avoid personalization by default
- remain explainable

Unknown-user behavior must default to conservative visibility rules.

### Explainability Requirements

Explainability is mandatory.

Machine explainability outputs must include:

- experience identifier
- source systems used
- synthesis inputs
- visibility decisions
- attribution confidence
- timestamps

Human explainability outputs must include:

- why information appears
- why information is hidden
- why synthesis produced a result
- why guest restrictions were applied

### Source-Of-Record Boundaries

Calendar systems remain authoritative.

Email systems remain authoritative.

Task systems remain authoritative.

Shopping systems remain authoritative.

Knowledge systems remain authoritative.

Household Status Synthesis is not authoritative.

Productivity Experiences are not sources of record.

### Productivity Experience Non-Rights

Productivity Experiences do not own:

- calendars
- mailboxes
- tasks
- shopping systems
- knowledge systems
- source systems
- governance
- contracts
- models

Productivity Experiences may not redefine architecture authority.

### Determinism Requirements

Productivity determinism requires:

- same governed inputs produce same experience output
- same visibility rules produce same experience output
- same synthesis inputs produce same synthesis output

Prohibited:

- hidden synthesis
- hidden privilege elevation
- hidden visibility changes

### Dependency For Future E13 Planning

This ADR is a mandatory dependency for future E13 planning.

Future E13 planning artifacts for productivity contracts, models, coordinator behavior, projections, and synthesis behavior must consume this ADR and must not redefine productivity experience governance independently.

## Consequences

Positive outcomes:

- establishes architecture authority for governed productivity experience domains
- prevents source-of-record drift into Concierge productivity orchestration
- enforces explainable synthesis and guest-safe visibility behavior
- creates clear boundaries for multi-item capture and household status synthesis

Tradeoffs:

- requires stronger explainability and visibility-policy validation in downstream work
- requires explicit governance discipline for synthesis and person-aware behavior changes

## Rejected Alternatives

### 1. Productivity Experience as calendar authority

Rejected because calendar providers remain authoritative systems of record.

### 2. Productivity Experience as mailbox authority

Rejected because email providers remain authoritative systems of record.

### 3. Productivity Experience as task authority

Rejected because configured task providers remain authoritative systems of record.

### 4. Productivity Experience as shopping authority

Rejected because configured shopping providers remain authoritative systems of record.

### 5. Hidden synthesis without explainability

Rejected because hidden synthesis violates determinism, explainability, and governance boundaries.

### 6. Guest access by implicit elevation

Rejected because guest behavior must remain conservative, explicit, and policy-bounded.
