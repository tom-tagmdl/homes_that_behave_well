# Messaging Patterns

## Purpose

Messaging Patterns define how the system communicates with the user.

This ensures that all communication is:

- calm
- consistent
- context-aware
- non-intrusive

Concierge is responsible for applying these patterns.

---

## Core Principle

The system should speak only when it adds value.

Silence is the default state.

---

## Communication Levels

All system communication must be categorized into one of the following levels.

### Info

Used for low-priority information.

Characteristics:

- Visual only
- No interruption
- No voice output

Examples:

- Status updates
- Historical information
- Passive insights

---

### Attention

Used when the user may benefit from awareness.

Characteristics:

- Visual display required
- Optional voice delivery
- Non-urgent

Examples:

- Environmental drift beginning
- Advisory recommendations
- Suggested actions

---

### Urgent

Used when immediate awareness is required.

Characteristics:

- Immediate voice output
- Interruptive if necessary
- High visibility

Examples:

- Risk state change to critical
- Water leak detected
- Severe environmental violation

---

### Night Mode

Special rule applied during quiet hours.

Characteristics:

- Suppresses Info and Attention messages
- Allows Urgent messages only
- Minimizes disruption

---

## Messaging Behavior Rules

The system must:

- Avoid repetition
- Avoid unnecessary escalation
- Combine related messages when possible
- Respect user context and timing

The system must never:

- repeat the same message without change
- escalate without cause
- interrupt casually
- overwhelm the user with multiple simultaneous messages

---

## Context Awareness

Messaging must consider:

- Room context (area)
- Time of day
- User presence
- Active modes (guest mode, night mode)

Messaging must adapt based on context.

Example:

- The same event may be visual-only during the day
- But suppressed entirely at night unless urgent

---

## Progressive Messaging

The system should evolve messaging based on state progression.

Example:

- Initial condition → Attention
- Worsening condition → Urgent

Messages should reflect the direction and severity of change.

---

## Debounce and Stability

Messaging must respect system stability rules.

The system should not:

- fire messages on transient changes
- react to brief fluctuations
- oscillate between states

Messaging must align with:

- debounce timing
- confirmed state transitions

---

## Explanation Requirement

Every message must be explainable.

Messages should include:

- what is happening
- why it matters
- what action (if any) is recommended

If the system cannot explain a message clearly, it should not send it.

---

## AI Messaging Rules

AI may assist in generating message content.

AI must:

- remain consistent with system facts
- not invent conditions or data
- produce explainable output

AI must not:

- exaggerate urgency
- introduce new information not in the system
- override messaging rules

---

## Example Patterns

Example: Advisory

"Humidity has been above recommended levels for items in this room. You may want to reduce humidity to protect sensitive assets."

Example: Urgent

"A potential water leak has been detected in the living room. Immediate attention is recommended."

Example: Info

"Humidity levels returned to normal range."

---

## Final Principle

Good messaging:

- is timely
- is relevant
- is minimal
- is understandable

Bad messaging:

- is noisy
- is repetitive
- is unclear
- is unnecessary

The system must always choose clarity and restraint over volume.