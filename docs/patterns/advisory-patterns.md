# Advisory Patterns

## Purpose

Advisory Patterns define how the system generates and presents recommendations.

Advisory is different from alerts.

- Alerts indicate that something is wrong
- Advisory suggests what could be improved

This distinction is critical to maintaining a calm and trustworthy system.

---

## Core Principle

Advisory guides the user.

It does not act on their behalf.

---

## Advisory vs Alert

### Alert

- Indicates a current problem
- Requires awareness or action
- May escalate to urgent messaging

Example:

Humidity exceeds safe range for sensitive assets.

---

### Advisory

- Suggests a potential improvement
- Does not require immediate action
- Never interrupts without cause

Example:

Consider lowering humidity to improve long-term preservation.

---

## Advisory Characteristics

Advisory must always be:

- optional
- informative
- non-intrusive
- explainable

Advisory must never:

- interrupt unnecessarily
- escalate without reason
- behave like an alert

---

## Advisory Sources

Advisory may be generated from:

- evaluation trends
- environment conditions
- configuration gaps
- sensor limitations
- historical patterns

Advisory is derived from system understanding, not assumptions.

---

## Types of Advisory

### Environment Advisory

Suggests changes to environmental conditions.

Examples:

- adjust humidity
- reduce temperature variation
- limit light exposure

---

### Configuration Advisory

Suggests improvements to system setup.

Examples:

- add missing sensors
- improve sensor coverage
- adjust aggregation rules

---

### Suitability Advisory

Suggests changes in how assets relate to rooms.

Examples:

- relocate sensitive asset
- avoid high-exposure placement
- match asset types to room conditions

---

### Predictive Advisory

Suggests future risk based on trends.

Examples:

- rising humidity patterns
- repeated exposure events
- seasonal environmental shifts

---

## Advisory Generation Rules

Advisory must be:

- based on real system data
- derived from defined logic
- consistent for the same inputs

Advisory must not:

- rely on assumptions
- introduce randomness
- change unpredictably between cycles

---

## Advisory and AI

AI may be used to enhance advisory.

AI may:

- suggest environment ranges
- explain complex relationships
- summarize conditions

AI must not:

- generate advisory without system context
- contradict known data
- create untraceable reasoning

All AI-assisted advisory must:

- be validated
- include explanation
- remain optional

---

## Presentation Rules

Advisory should be presented as:

- visual recommendations by default
- optional voice when appropriate
- grouped when multiple suggestions exist

Advisory should not:

- flood the user with suggestions
- repeat constantly
- interrupt active workflows

---

## Persistence Rules

Advisory must be:

- stored as historical recommendations
- timestamped
- immutable once recorded

Advisory must not:

- overwrite previous recommendations
- disappear without trace

This enables:

- auditability
- historical insight
- system learning

---

## Relationship to Evaluation

Evaluation determines state.

Advisory suggests improvement.

They must remain separate.

Evaluation:

- produces risk state
- is deterministic

Advisory:

- produces recommendations
- is optional guidance

---

## Interaction Model

When advisory is presented:

- the system may suggest an action
- the user must explicitly approve changes

Example:

System suggests new humidity range  
User confirms  
Asset Intelligence applies update via service

---

## Safety Rules

Advisory must never:

- apply changes automatically
- bypass validation
- create unsafe configurations

All recommended values must:

- fall within defined safe bounds
- be validated before use

---

## Final Principle

Advisory improves the system.

It does not control it.

If a suggestion becomes automatic, it is no longer advisory and must follow a different contract.
