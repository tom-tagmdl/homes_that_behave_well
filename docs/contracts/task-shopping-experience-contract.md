# Task and Shopping Experience Contract

## Purpose

This contract defines the authoritative boundary for Task and Shopping as household productivity experiences.

This contract governs:

- experience visibility
- task awareness
- assignment awareness
- completion awareness
- shopping awareness
- provenance boundaries
- explainability
- source attribution

This contract does not define:

- connector implementation
- Microsoft Graph implementation
- Microsoft To Do implementation
- storage implementation
- synchronization implementation

---

## Task Experience Definition

Task Experience is a governed productivity experience that surfaces task-related awareness, assignments, completion state, due awareness, and productivity context.

Task Experience is not:

- task authority
- assignment authority
- completion authority

Task Experience consumes task data.

Task Experience does not own task truth.

---

## Shopping Experience Definition

Shopping Experience is a governed productivity experience that surfaces shopping awareness, list interaction, shopping context, shopping completion, and household shopping coordination.

Shopping Experience is not:

- shopping list authority
- shopping item authority
- completion authority

Shopping Experience consumes shopping data.

Shopping Experience does not own shopping truth.

---

## Source Of Record Statement

When configured:

- Microsoft To Do remains the authoritative source of record for tasks, task assignments, task completion state, shopping lists, shopping items, and shopping completion state.
- Task and Shopping Experiences consume source data.
- Task and Shopping Experiences do not own source data.

---

## Productivity Ownership Matrix

| Concern | Owner | Task/Shopping Relationship |
|---|---|---|
| task truth | Microsoft To Do | experience consumes task truth and does not redefine it |
| assignment state | Microsoft To Do | experience consumes assignment state and does not own it |
| completion state | Microsoft To Do | experience consumes completion state and does not own it |
| shopping truth | Microsoft To Do | experience consumes shopping truth and does not redefine it |
| shopping completion state | Microsoft To Do | experience consumes shopping completion state and does not own it |
| identity confidence | Voice Identity | experience consumes confidence context and does not own identity authority |
| provenance | Provenance governance | experience consumes provenance and must preserve attribution |
| household memory | Household Memory | experience may consume memory context and does not own memory state |
| task experience | Task and Shopping Experience governance under this contract | owns task experience visibility, discoverability, explainability, and productivity interaction boundaries |
| shopping experience | Task and Shopping Experience governance under this contract | owns shopping experience visibility, discoverability, explainability, and productivity interaction boundaries |
| productivity experience | HTBW productivity experience governance | experience participates in productivity outcomes without source-of-record ownership |
| execution | Service contracts and orchestration paths | experience informs governed presentation only and does not execute provider behavior |

---

## Task Experience Categories

### 1. Personal Tasks

Governance scope:

- personal task visibility
- personal task awareness
- personal task summarization

### 2. Assigned Tasks

Governance scope:

- assigned task visibility
- assignment-aware task surfacing
- assignee-aware context

### 3. Shared Tasks

Governance scope:

- shared household task visibility
- shared task context
- collaboration-aware surfacing

### 4. Due Awareness

Governance scope:

- due-date awareness
- due-context surfacing
- due-aware prioritization context

### 5. Completion Awareness

Governance scope:

- task completion visibility
- completion state awareness
- completion attribution support

### 6. Household Productivity Awareness

Governance scope:

- household task relevance
- household productivity context
- task summary participation

### 7. Productivity Briefing Participation

Governance scope:

- inclusion in briefing output
- summary participation
- explainable briefing contribution

All categories are governance only and do not define provider implementation.

---

## Shopping Experience Categories

### 1. Shopping List Awareness

Governance scope:

- shopping list visibility
- list-level awareness
- list summarization

### 2. Shopping Item Awareness

Governance scope:

- shopping item visibility
- item-level awareness
- item-level summarization

### 3. Shared Shopping Awareness

Governance scope:

- shared household shopping visibility
- shared shopping context
- collaboration-aware shopping surfacing

### 4. Shopping Completion Awareness

Governance scope:

- item completion visibility
- completion state awareness
- completion attribution support

### 5. Shopping Coordination Awareness

Governance scope:

- coordination context
- shopping planning context
- shopping-related collaboration awareness

### 6. Shopping Briefing Participation

Governance scope:

- inclusion in briefing output
- summary participation
- explainable briefing contribution

### 7. Household Shopping Awareness

Governance scope:

- household shopping relevance
- household shopping context
- shopping summary participation

All categories are governance only and do not define provider implementation.

---

## Task Ownership And Assignment Semantics

This section governs:

- ownership awareness
- assignment awareness
- assignment visibility
- assignment attribution

Required statements:

- Task Experience consumes assignments.
- Task Experience does not own assignments.

Assignment visibility must remain explainable and bounded by identity and authorization context.

---

## Person-Aware Task Scenarios

This section governs:

- my tasks
- another person's tasks when authorized
- shared household tasks
- assigned tasks
- completed tasks

Required statements:

- identity and authorization remain external authorities.
- Task Experience consumes person-aware context.
- Task Experience does not replace identity or authorization governance.

---

## Multi-Item Shopping Capture

This section governs governance expectations for:

- multiple items in one request
- grouped additions
- shopping capture awareness

Required statements:

- the contract recognizes multi-item shopping capture requirements.
- the contract does not define implementation.

---

## Duplicate Detection Expectations

This section governs governance expectations for:

- duplicate awareness
- duplicate visibility
- duplicate handling expectations

Required statements:

- duplicate handling must remain explainable.
- the contract does not define duplicate detection algorithms.

---

## Shopping Completion Attribution

This section governs:

- who completed an item
- who added an item
- who modified an item

Required statements:

- attribution derives from provenance.
- the contract must not invent attribution.

---

## Provenance Relationship

Task and Shopping Experiences consume provenance.

Provenance remains authoritative.

Task and Shopping Experiences do not generate alternate attribution.

This aligns with ADR-011.

---

## Household Memory Relationship

Household Memory may consume task and shopping events.

Household Memory does not own task truth.

Household Memory does not own shopping truth.

---

## Privacy And Consent

This section governs:

- visibility constraints
- assignment visibility
- shopping visibility
- consent boundaries
- disclosure boundaries

Required statement:

- Task and Shopping Experiences must respect privacy and authorization boundaries.

---

## Explainability Requirements

Human explainability must support:

- Why is this task visible?
- Why is this assignment visible?
- Why is this item on the list?
- Who completed this item?
- Why was this highlighted?

Machine explainability must support:

- source system
- source identifier
- attribution lineage
- timestamps
- confidence metadata

---

## Source Attribution Requirements

Task and Shopping Experiences must explicitly require:

- task attribution
- shopping attribution
- completion attribution
- source transparency

No hidden attribution.

---

## Non-Rights

Task and Shopping Experiences do not own:

- tasks
- assignments
- shopping lists
- shopping items
- completion state
- provider records
- provenance
- identity
- execution

---

## Determinism Requirements

Required rules:

- same source inputs -> same visibility outcome
- same completion state -> same awareness outcome
- same provenance -> same attribution outcome

Prohibited behavior:

- hidden attribution
- hidden ownership
- hidden completion interpretation

---

## Task/Shopping Experience Coverage Matrix

| Experience Area | Task | Shopping | Briefing | Source Of Record |
|---|---|---|---|---|
| Personal Tasks | yes | no | yes | Microsoft To Do |
| Assigned Tasks | yes | no | yes | Microsoft To Do |
| Shared Tasks | yes | no | yes | Microsoft To Do |
| Due Awareness | yes | no | yes | Microsoft To Do |
| Completion Awareness | yes | yes | yes | Microsoft To Do |
| Household Productivity Awareness | yes | yes | yes | Microsoft To Do |
| Productivity Briefing Participation | yes | yes | yes | Microsoft To Do |
| Shopping List Awareness | no | yes | yes | Microsoft To Do |
| Shopping Item Awareness | no | yes | yes | Microsoft To Do |
| Shared Shopping Awareness | no | yes | yes | Microsoft To Do |
| Shopping Completion Awareness | no | yes | yes | Microsoft To Do |
| Shopping Coordination Awareness | no | yes | yes | Microsoft To Do |
| Shopping Briefing Participation | no | yes | yes | Microsoft To Do |
| Household Shopping Awareness | no | yes | yes | Microsoft To Do |

---

## Boundary Review

This contract preserves explicit separation between:

- Task Experience
- Shopping Experience
- Productivity Experience
- Household Memory
- Provenance
- Microsoft To Do Source System

Separation rules:

- Task Experience remains a governed experience, not task authority
- Shopping Experience remains a governed experience, not shopping authority
- Productivity Experience consumes Task and Shopping experiences and does not become source-of-record
- Household Memory may consume task and shopping events but does not own task or shopping truth
- Provenance remains authoritative for attribution and lineage
- Microsoft To Do remains the source-of-record for task and shopping truth when configured

Ownership overlap is prohibited.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Task and Shopping Experience.

Future planning must treat this contract as a mandatory dependency for:

- E12 governance validation
- E13 productivity experience planning
- E14 provenance consumption

This contract is the authoritative input for productivity planning and multi-item capture planning.

---

## Final Principle

Task and Shopping Experiences are governed household productivity experiences that consume authoritative Microsoft To Do source data, household memory, and provenance without taking ownership of source truth.