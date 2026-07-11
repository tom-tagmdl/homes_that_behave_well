# Multi-Item Capture Interpretation Contract

## Purpose

This contract defines the authoritative boundary for multi-item capture interpretation.

This contract governs:

- decomposition governance
- interpretation semantics
- ambiguity handling semantics
- confirmation semantics
- lineage semantics
- explainability for interpretation outputs
- provenance consumption for interpretation outputs

This contract does not define:

- parser behavior
- speech recognition
- NLP processing
- interpretation engines
- confirmation workflows

---

## Interpretation Definition

Multi-Item Capture Interpretation is a governed interpretation process that decomposes an utterance into structured item outcomes for productivity workflows.

Multi-Item Capture Interpretation is not:

- parser authority
- NLP authority
- speech interpretation authority
- decomposition engine authority

Multi-Item Capture Interpretation consumes governed capture inputs and produces governed decomposition references.

Multi-Item Capture Interpretation does not own source truth.

---

## Source Of Record Statement

When configured:

- Utterance sources remain authoritative for the original capture text or speech-derived text.
- Task systems remain authoritative for task truth.
- Shopping systems remain authoritative for shopping truth.
- Provenance remains authoritative for attribution and lineage.

Multi-Item Capture Interpretation consumes references and does not own source data.

---

## Scope

Multi-Item Capture Interpretation may govern references for:

- utterance decomposition
- item decomposition
- task candidate decomposition
- shopping candidate decomposition
- ambiguity handling
- confirmation references
- lineage references
- provenance propagation references
- explainability references

All items are reference-based and consumption-only.

---

## Required Behavior

The contract requires support for:

- governed utterance decomposition
- traceable decomposition results
- preserved ambiguity references when needed
- preserved confirmation references when needed
- propagated provenance to decomposed items
- explainable interpretation outputs

The contract does not define how interpretation occurs.

---

## Guest-Safe Requirements

Guest-safe behavior must remain indirect and governed by consuming contracts.

Guest-safe interpretation outputs must support reference-based visibility boundaries only.

---

## Provenance Requirements

Multi-Item Capture Interpretation may consume provenance-aware references.

Multi-Item Capture Interpretation must preserve lineage and provenance propagation references.

Multi-Item Capture Interpretation does not own provenance semantics.

---

## Boundary Review

Multi-Item Capture Interpretation does not own:

- parser behavior
- speech recognition
- NLP processing
- interpretation engines
- task ownership
- shopping ownership
- provenance semantics
- occupancy semantics

Ownership drift is prohibited.

---

## Canonical Architecture Linkage

Multi-Item Capture Interpretation Contract is the authoritative contract source for V2-M18 Multi-Item Capture Result Model consumption and downstream E13 planning.

Future V2-M18 model work must treat this contract as a mandatory dependency.
# Multi-Item Capture Interpretation Contract

## Purpose

This contract defines the authoritative boundary for interpreting a single productivity utterance that contains multiple intended items or actions.

This contract governs:

- multi-item decomposition
- decomposition explainability
- confirmation requirements
- ambiguity handling
- provenance propagation
- productivity capture interpretation

This contract does not define:

- parser implementation
- NLP implementation
- decomposition algorithms
- execution engines

---

## Multi-Item Capture Definition

Multi-Item Capture Interpretation is a governed interpretation layer that represents how a single interaction may produce multiple productivity artifacts while preserving attribution, explainability, and user intent.

Multi-Item Capture Interpretation is not:

- parsing authority
- execution authority
- task authority
- shopping authority

---

## Source Utterance Governance

This section governs:

- single utterance capture
- interpreted intent groups
- decomposition boundaries

Required statement:

- A source utterance remains authoritative for all derived items.

---

## Decomposition Governance

This section governs:

- decomposition expectations
- item extraction expectations
- decomposition visibility

Required statement:

- Every derived item must remain traceable to its originating interaction.

---

## Decomposition Categories

### 1. Shopping Decomposition

Governance scope:

- shopping-oriented item extraction
- list-bound shopping capture interpretation

### 2. Task Decomposition

Governance scope:

- task-oriented item extraction
- task-bound productivity capture interpretation

### 3. Mixed Productivity Decomposition

Governance scope:

- simultaneous shopping and task extraction
- mixed productivity intent interpretation

### 4. Coordinated Multi-List Decomposition

Governance scope:

- multi-list routing interpretation
- destination-aware item grouping

### 5. Multi-Person Productivity Decomposition

Governance scope:

- person-specific decomposition boundaries
- assigned and delegated item interpretation

All categories are governance only.

---

## Provenance Propagation

Every decomposed item must inherit:

- source interaction reference
- attribution reference
- timestamp reference
- provenance lineage

No decomposed item may lose provenance.

This is a primary acceptance criterion.

---

## Decomposition Attribution Matrix

| Artifact Type | Must Retain Source Utterance | Must Retain Attribution | Must Retain Timestamp | Must Retain Provenance |
|---|---|---|---|---|
| Shopping Item | yes | yes | yes | yes |
| Task Item | yes | yes | yes | yes |
| Reminder Item | yes | yes | yes | yes |
| Coordinated Item | yes | yes | yes | yes |

---

## Confirmation Policy

This section governs:

- successful interpretation
- ambiguous interpretation
- incomplete interpretation
- uncertain decomposition

Guidance:

- confirmation is optional when decomposition is complete, unambiguous, and low-risk
- confirmation is expected when decomposition creates multiple derived items with user-visible grouping that may need review
- confirmation is required when ambiguity, destination uncertainty, or assignment uncertainty would otherwise create a risky or misleading interpretation

Do not define implementation logic.

---

## Ambiguity Governance

This section governs:

- unclear items
- unclear ownership
- unclear destination lists
- mixed intent content

Required statement:

- Ambiguity must remain visible.

Prohibited behavior:

- invisible assumptions

---

## Error Handling Expectations

This section governs:

- partial decomposition
- failed decomposition
- conflicting decomposition
- validation failures

Required statement:

- Errors must remain explainable.

---

## Multi-List Scenarios

This section governs:

- multiple shopping lists
- multiple task lists
- shopping + task combinations
- destination uncertainty

Examples:

- Add milk to Costco and batteries to Target.
- Add eggs to groceries and call plumber to tasks.

Do not define execution behavior.

---

## Multi-Person Scenarios

This section governs:

- assigned tasks
- household tasks
- person-specific tasks
- delegated items

Required statement:

- Identity remains authoritative.

The contract does not own identity.

---

## Shopping Experience Relationship

Shopping Experience may consume decomposition outputs.

Multi-Item Capture Interpretation does not own shopping items.

---

## Task Experience Relationship

Task Experience may consume decomposition outputs.

Multi-Item Capture Interpretation does not own tasks.

---

## Household Memory Relationship

Household Memory may consume decomposition outcomes.

Household Memory does not own decomposition governance.

---

## Provenance Relationship

Provenance remains authoritative for attribution.

Multi-Item Capture Interpretation consumes provenance.

No alternate attribution systems permitted.

---

## Explainability Requirements

Human explainability must support:

- What items were extracted?
- Why were they separated?
- Why was confirmation requested?
- Why was an item rejected?
- Why was ambiguity detected?

Machine explainability must support:

- source utterance identifier
- decomposition references
- attribution lineage
- timestamps
- confidence references

---

## Non-Rights

Multi-Item Capture Interpretation does not own:

- tasks
- shopping items
- provenance
- identity
- execution
- parsing engines

---

## Determinism Requirements

Required rules:

- same interpreted utterance -> same decomposition
- same provenance inputs -> same attribution outputs
- same ambiguity state -> same confirmation expectations

Prohibited behavior:

- hidden decomposition
- hidden attribution loss
- hidden ambiguity resolution

---

## Multi-Item Coverage Matrix

| Scenario | Supported | Provenance Required | Confirmation Consideration |
|---|---|---|---|
| Multi-item shopping | yes | yes | optional or required depending on ambiguity and risk |
| Multi-item tasks | yes | yes | optional or required depending on ambiguity and risk |
| Mixed tasks + shopping | yes | yes | likely required when intent groups are mixed or ambiguous |
| Multi-person assignments | yes | yes | required when ownership or assignee is uncertain |
| Multi-list routing | yes | yes | required when destination lists are uncertain |
| Ambiguous decomposition | yes | yes | required |
| Partial decomposition | yes | yes | required for user-visible review or correction |

---

## Boundary Review

This contract preserves explicit separation between:

- Multi-Item Capture Interpretation
- Shopping Experience
- Task Experience
- Provenance
- Household Memory
- Identity

Separation rules:

- Multi-Item Capture Interpretation governs decomposition and explanation boundaries only
- Shopping Experience owns shopping experience visibility and awareness
- Task Experience owns task experience visibility and awareness
- Provenance remains authoritative for attribution and lineage
- Household Memory may consume decomposition outcomes without owning decomposition governance
- Identity remains authoritative for person and assignee context

Ownership overlap is prohibited.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Multi-Item Capture Interpretation.

Future planning must treat this contract as a mandatory dependency for:

- E12 governance validation
- E13 productivity experience planning
- E14 provenance consumption

This contract becomes authoritative input for shopping capture planning, task capture planning, and multi-item productivity workflows.

---

## Final Principle

Multi-Item Capture Interpretation preserves provenance, intent traceability, and explainability while decomposing one utterance into multiple governed productivity artifacts.