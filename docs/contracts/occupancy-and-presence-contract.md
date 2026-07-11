# Occupancy and Presence Contract

## Purpose

This contract defines the authoritative boundary for occupancy-aware and presence-aware behavior across Concierge V2.

This contract governs:

- occupancy states
- occupancy sources
- confidence concepts
- occupancy decision gates
- guest-safe behavior
- multi-person behavior
- explainability

This contract does not define:

- sensor fusion
- scoring algorithms
- detection implementation
- provider implementation

---

## Occupancy And Presence Definition

Occupancy And Presence is a governed representation of room occupancy and occupant awareness used by Concierge decision-making.

Occupancy and Presence answers:

- Is the room occupied?
- Who is believed to be present?
- How confident are we?
- Should occupancy influence a decision?

Occupancy and Presence is not:

- sensor fusion
- identity authority
- room authority
- execution authority

---

## Canonical Occupancy States

### 1. Empty Room

Definition: no occupant is currently established in the room scope.

Meaning: room-scoped occupancy influence should be minimal or neutral.

Downstream usage expectations: conservative routing, no assumed occupant-specific behavior.

### 2. Occupied Room

Definition: one or more occupants are established in the room scope.

Meaning: room occupancy is present and may influence governed behavior.

Downstream usage expectations: bounded occupancy-aware decisions are permitted.

### 3. Known Occupant

Definition: an occupant is associated with a known identity confidence context.

Meaning: occupant context may inform person-aware behavior within policy.

Downstream usage expectations: identity-linked behavior may apply conservatively and explainably.

### 4. Unknown Occupant

Definition: an occupant is present but identity is not confidently established.

Meaning: occupancy is present but identity-linked behavior must remain conservative.

Downstream usage expectations: visibility may remain available while personalization stays restricted.

### 5. Guest Occupant

Definition: an occupant is present and governed as guest-safe rather than personalized household membership.

Meaning: occupant is present but protected household context must remain restricted.

Downstream usage expectations: guest-safe defaults apply; private context is blocked.

### 6. Multiple Occupants

Definition: more than one occupant is established in the room scope.

Meaning: multi-person ambiguity or mixed attribution may require conservative policy.

Downstream usage expectations: conflict-aware explainability and bounded eligibility are required.

---

## Occupancy Ownership Matrix

| Concern | Owner | Occupancy Relationship |
|---|---|---|
| presence truth | Foundation | occupancy consumes presence truth and does not own it |
| occupancy truth | Foundation | occupancy consumes occupancy truth and does not own it |
| room truth | Foundation | occupancy references room truth and does not own it |
| attribution confidence | Voice Identity | occupancy consumes confidence and does not own it |
| identity confidence | Voice Identity | occupancy references identity confidence and does not own it |
| occupancy sources | Foundation and governed presence providers | occupancy consumes source inputs and does not own source systems |
| restoration | Experience Restoration | occupancy may influence restoration eligibility but does not authorize it |
| messaging | Messaging governance and runtime policy | occupancy may influence messaging eligibility but does not authorize it |
| notifications | notification governance and runtime policy | occupancy may influence notification eligibility but does not authorize it |
| household memory | Household Memory governance | occupancy may contribute context but does not own memory |
| personalization | Personalization governance | occupancy may contribute context but does not own personalization |
| occupancy governance | Occupancy and Presence Contract | occupancy semantics, states, confidence governance, decision governance, and explainability governance |

Required ownership alignment:

- Foundation owns presence truth, occupancy truth, room truth, and presence providers.
- Voice Identity owns attribution and identity confidence.
- This contract governs occupancy semantics and decision governance.
- This contract does not own sensors, sensor fusion, confidence algorithms, identity, or room truth.

---

## Occupancy Source Governance

Supported source categories:

- Foundation Presence
- BLE Presence
- Voice Identity Attribution
- Manual Occupancy
- Future Presence Providers

### Foundation Presence

Source role: governed presence context from Foundation-owned sources.

Contribution expectations: provide room-scoped presence context with explicit confidence visibility.

Ownership boundaries: Foundation owns the source truth; occupancy consumes the input.

### BLE Presence

Source role: proximity-informed presence signal input.

Contribution expectations: provide bounded presence evidence and confidence references.

Ownership boundaries: source systems remain external; occupancy consumes the signal.

### Voice Identity Attribution

Source role: attribution-confidence input from Voice Identity.

Contribution expectations: provide identity-linked confidence references and actor context.

Ownership boundaries: Voice Identity owns attribution confidence; occupancy consumes it.

### Manual Occupancy

Source role: explicitly asserted occupancy input.

Contribution expectations: provide user- or admin-asserted occupancy context.

Ownership boundaries: manual input is still governed context, not occupancy truth ownership.

### Future Presence Providers

Source role: additional governed presence sources.

Contribution expectations: provide lineage-aware, explainable occupancy inputs.

Ownership boundaries: future providers remain source owners; occupancy consumes their inputs.

Required statement:

- Occupancy consumes source inputs.
- Occupancy does not own source systems.

---

## Confidence Governance

Canonical confidence concepts:

- BLE confidence
- Voice Identity confidence
- Presence confidence
- Composite confidence

### BLE Confidence

Represents confidence derived from BLE presence evidence.

Visibility: must remain explicit when surfaced.

Explainability: must show BLE lineage and source references.

Usage: may influence occupancy and occupant state visibility, but does not authorize detection algorithms.

### Voice Identity Confidence

Represents confidence derived from identity attribution context.

Visibility: must remain explicit when surfaced.

Explainability: must show identity-linked confidence references.

Usage: may influence known occupant context, guest-safe restrictions, and personalization gates.

### Presence Confidence

Represents confidence that presence is established in room scope.

Visibility: must remain explicit when surfaced.

Explainability: must show source references and timestamps.

Usage: may influence occupancy-aware decisions, not authorize them.

### Composite Confidence

Represents combined governed confidence context across sources.

Visibility: must remain explicit when surfaced.

Explainability: must preserve the contributing source references.

Usage: may inform multi-person or conflict-aware decisions.

Do not define algorithms.

---

## Confidence Gate Matrix

| Confidence Type | May Influence | May Not Authorize |
|---|---|---|
| BLE Confidence | Restoration, Notifications, Messaging, Personalization | execution, identity authority, room truth |
| Voice Confidence | Restoration, Notifications, Messaging, Personalization | execution, identity authority, room truth |
| Presence Confidence | Restoration, Notifications, Messaging, Personalization | execution, identity authority, room truth |
| Composite Confidence | Restoration, Notifications, Messaging, Personalization | execution, identity authority, room truth |

---

## Unknown Occupant Governance

Unknown occupant behavior must be conservative and explainable.

Required governance:

- unknown occupants remain visible
- unknown attribution behavior must stay explicit
- restricted behavior expectations must block private or identity-sensitive assumptions

Prohibited behavior:

- invisible assumptions
- hidden attribution guesses

---

## Guest Occupant Governance

Guest occupant behavior must be guest-safe and conservative.

Required governance:

- guest occupant behavior must not reveal protected household context
- guest-safe restrictions must prevent private personalization and memory inheritance
- guest visibility expectations must remain explicit and explainable

Required statements:

- Guests must not inherit private personalization.
- Guests must not inherit private memory.
- Guests must not inherit protected experiences.

---

## Multi-Person Governance

Governance must define behavior for:

- multiple known occupants
- known + guest occupants
- conflicting occupants
- mixed attribution states

Required behavior:

- visibility expectations must remain explicit
- conflict visibility must remain explicit
- explainability expectations must show how occupancy state and confidence influenced the decision surface

Do not define resolution algorithms.

---

## Restoration Gate Governance

Occupancy may influence restoration eligibility.

Occupancy does not authorize restoration.

Restoration remains governed by Restoration Contract.

This aligns with V2-C7.

---

## Messaging Gate Governance

Occupancy may influence messaging eligibility.

Occupancy does not authorize messaging.

Messaging remains externally governed.

---

## Notification Gate Governance

Occupancy may influence notification eligibility.

Occupancy does not authorize notification delivery.

---

## Personalization Relationship

Personalization consumes occupancy context.

Occupancy does not own personalization.

This aligns with ADR-008.

---

## Household Memory Relationship

Household Memory may consume occupancy context.

Occupancy does not own memory.

This aligns with ADR-009.

---

## Provenance Relationship

Occupancy may reference provenance.

Provenance remains authoritative.

Occupancy does not own attribution.

---

## Explainability Requirements

Human explainability must support:

- Why was the room considered occupied?
- Why was the room considered empty?
- Why was guest state used?
- Why was unknown state used?
- Why did occupancy affect this decision?

Machine explainability must support:

- occupancy state
- source references
- confidence references
- identity confidence references
- timestamps

---

## Non-Rights

Occupancy and Presence does not own:

- presence truth
- room truth
- identity
- confidence algorithms
- sensor fusion
- execution

---

## Determinism Requirements

Required rules:

- same occupancy inputs -> same occupancy state
- same confidence inputs -> same confidence visibility
- same source inputs -> same explainability result

Prohibited behavior:

- hidden occupancy assumptions
- hidden guest assumptions
- hidden confidence overrides

---

## Occupancy Policy Matrix

| Occupancy State | Restoration | Messaging | Notifications | Memory | Personalization |
|---|---|---|---|---|---|
| empty room | low influence | low influence | low influence | low influence | low influence |
| occupied room | moderate influence | moderate influence | moderate influence | moderate influence | moderate influence |
| known occupant | moderate influence | moderate influence | moderate influence | moderate influence | moderate influence |
| unknown occupant | conservative influence | conservative influence | conservative influence | conservative influence | conservative influence |
| guest occupant | restricted influence | restricted influence | restricted influence | restricted influence | restricted influence |
| multiple occupants | conflict-aware influence | conflict-aware influence | conflict-aware influence | conflict-aware influence | conflict-aware influence |

This matrix defines governance influence, not execution.

---

## Boundary Review

This contract preserves explicit separation between:

- Occupancy
- Presence
- Identity
- Personalization
- Restoration
- Household Memory
- Messaging
- Foundation Truth

Separation rules:

- Occupancy governs occupancy semantics only
- Presence remains a distinct governed concept
- Identity remains authoritative in Voice Identity
- Personalization remains external to occupancy
- Restoration remains external to occupancy
- Household Memory remains external to occupancy
- Messaging remains externally governed
- Foundation remains authoritative for truth sources

Ownership overlap is prohibited.

---

## Contract / Model Alignment Review

### 1. Contract authority

This contract is the authority for occupancy semantics, occupancy states, confidence governance, guest-safe behavior, multi-person behavior, and decision gating.

### 2. Model consumption responsibilities

The Occupancy and Presence Model consumes this contract by representing occupancy state, occupancy confidence, identity confidence references, occupancy source references, freshness, and explainability inputs.

### 3. Gaps identified

- The model includes optional conflict and freshness evaluation; this contract authorizes conservative, explainable use of those concepts without defining algorithms.
- The model uses a compact occupancy-state enumeration; this contract provides the semantic meaning and downstream usage expectations.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Occupancy and Presence.

Future planning must treat this contract as a mandatory dependency for:

- E8a
- E8
- E9
- E10
- E12

V2-C11 satisfies the dependency blocking closure of V2-C7 Experience Restoration and V2-C8 Household Memory when no remaining dependency gaps exist.

---

## Final Principle

Occupancy and Presence provide governed, explainable occupancy-aware context for Concierge while leaving presence truth, room truth, identity, and execution outside this contract's authority.