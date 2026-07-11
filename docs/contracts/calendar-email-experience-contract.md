# Calendar and Email Experience Contract

## Purpose

This contract defines the authoritative boundary for Calendar and Email as household productivity experiences.

This contract governs:

- experience visibility
- experience discoverability
- experience boundaries
- explainability
- privacy
- consent
- source attribution
- household productivity experiences

This contract does not define:

- connector implementation
- Microsoft Graph implementation
- transport implementation
- provider synchronization

---

## Calendar Experience Definition

Calendar Experience is a governed productivity experience that surfaces calendar-derived awareness, context, coordination, and briefing information.

Calendar Experience is not:

- calendar authority
- event authority
- scheduling authority

Calendar Experience consumes calendar data.

Calendar Experience does not own calendar truth.

---

## Email Experience Definition

Email Experience is a governed productivity experience that surfaces email-derived awareness, context, priorities, and briefing information.

Email Experience is not:

- mailbox authority
- email message authority
- transport authority

Email Experience consumes email data.

Email Experience does not own email truth.

---

## Source Of Record Statement

When configured:

- Microsoft 365 Calendar remains the authoritative source of record for schedules, meetings, calendar events, and availability.
- Microsoft 365 Email remains the authoritative source of record for email messages, email state, and mailbox information.
- Calendar and Email Experiences consume source data.
- Calendar and Email Experiences do not own source data.

---

## Productivity Ownership Matrix

| Concern | Owner | Calendar/Email Relationship |
|---|---|---|
| calendar truth | Microsoft 365 Calendar | experience consumes calendar truth and does not redefine it |
| meeting truth | Microsoft 365 Calendar | experience consumes meeting truth and does not own it |
| email truth | Microsoft 365 Email | experience consumes email truth and does not redefine it |
| mailbox truth | Microsoft 365 Email | experience consumes mailbox truth and does not own it |
| identity confidence | Voice Identity | experience consumes confidence context and does not own identity authority |
| room truth | Foundation | experience consumes room context and does not own room truth |
| occupancy | Foundation | experience consumes occupancy context and does not own occupancy truth |
| household memory | Household Memory | experience may consume memory context and does not own memory state |
| provenance | Provenance governance | experience consumes provenance and must preserve attribution |
| calendar experience | Calendar and Email Experience governance under this contract | owns calendar experience visibility, discoverability, explainability, and composition boundaries |
| email experience | Calendar and Email Experience governance under this contract | owns email experience visibility, discoverability, explainability, and composition boundaries |
| briefing experience | Briefing synthesis under HTBW governance | experience may participate in briefing, but briefing is not source ownership |
| execution | Service contracts and orchestration paths | experience informs governed presentation only and does not execute provider behavior |

---

## Calendar Experience Categories

### 1. Personal Schedule Awareness

Governance scope:

- personal schedule visibility
- personal schedule summarization
- calendar-derived awareness for the current person

### 2. Multi-Person Awareness

Governance scope:

- awareness across multiple people
- overlapping calendar context
- shared schedule interpretation

### 3. Free/Busy Awareness

Governance scope:

- free/busy visibility
- free/busy comparisons
- availability awareness

### 4. Shared Schedule Awareness

Governance scope:

- shared schedule context
- household coordination context
- shared planning visibility

### 5. Coordination Awareness

Governance scope:

- coordination context
- timing awareness
- household collaboration context

### 6. Briefing Participation

Governance scope:

- inclusion in briefing output
- summary participation
- explainable briefing contribution

### 7. Travel Awareness

Governance scope:

- travel-related calendar context
- trip-aware timing context
- calendar-derived travel relevance

### 8. Reservation Awareness

Governance scope:

- reservation-related schedule context
- appointment-like timing context
- reservation visibility and briefing relevance

All categories are governance only and do not define provider implementation.

---

## Email Experience Categories

### 1. Awareness Experience

Governance scope:

- email-derived awareness
- inbox-aware context
- household communication awareness

### 2. Importance Surfacing

Governance scope:

- priority context
- importance highlighting
- explainable surfacing decisions

### 3. Travel Highlights

Governance scope:

- travel-related email context
- itinerary and trip relevance
- travel briefing contribution

### 4. Reservation Highlights

Governance scope:

- reservation-related email context
- booking and confirmation relevance
- reservation briefing contribution

### 5. Delivery Highlights

Governance scope:

- delivery-related email context
- shipment and notification relevance
- delivery briefing contribution

### 6. Briefing Participation

Governance scope:

- inclusion in briefing output
- summary participation
- explainable briefing contribution

### 7. Action Awareness

Governance scope:

- actionable email context
- follow-up awareness
- task-like signal surfacing without task ownership transfer

### 8. Household Productivity Awareness

Governance scope:

- household productivity context from email
- family and household relevance
- explainable household productivity surfacing

All categories are governance only and do not define provider implementation.

---

## Multi-Person Calendar Scenarios

Calendar Experience must define governance for:

- calendar awareness across multiple people
- shared schedule awareness
- coordination visibility
- free/busy comparisons

Required statements:

- Calendar Experience consumes awareness.
- Calendar Experience does not own calendars.

---

## Person-Aware Experiences

Calendar and Email Experiences must define:

- person-aware calendar visibility
- person-aware email visibility
- consent boundaries
- confidence boundaries

Required statement:

- identity remains authoritative.

---

## Email Privacy And Consent

Calendar and Email Experiences must define:

- consent requirements
- privacy constraints
- message visibility constraints
- access expectations
- disclosure boundaries

Required statement:

- Email experiences must respect privacy controls.

---

## Briefing Integration

Calendar and Email Experiences participate in:

- briefing experiences
- summary experiences
- productivity experiences

Required statements:

- briefings consume experiences
- briefings do not become source-of-record

---

## Household Memory Relationship

Household Memory may consume productivity events.

Household Memory does not own calendar truth.

Household Memory does not own email truth.

---

## Provenance Relationship

Calendar and Email Experiences must provide attribution.

Calendar and Email Experiences consume provenance.

Provenance remains authoritative.

---

## Explainability Requirements

Human explainability must support:

- Why did this appear?
- Where did this information come from?
- Why was this highlighted?
- Why is this relevant?

Machine explainability must support:

- source system
- source identifier
- attribution lineage
- timestamps
- confidence indicators

---

## Source Attribution Requirements

Calendar and Email Experiences must explicitly require:

- calendar attribution
- email attribution
- source visibility
- source transparency

No hidden sources.

---

## Non-Rights

Calendar and Email Experiences do not own:

- calendars
- meetings
- messages
- mailboxes
- provider records
- identity
- occupancy
- execution

---

## Determinism Requirements

Required rules:

- same source inputs -> same experience visibility
- same consent state -> same visibility outcome
- same source attribution -> same explanation outcome

Prohibited behavior:

- hidden source selection
- hidden data interpretation
- hidden attribution

---

## Calendar/Email Experience Coverage Matrix

| Experience Area | Calendar | Email | Briefing | Source Of Record |
|---|---|---|---|---|
| Personal Schedule Awareness | yes | no | yes | Microsoft 365 Calendar |
| Multi-Person Awareness | yes | no | yes | Microsoft 365 Calendar |
| Free/Busy Awareness | yes | no | yes | Microsoft 365 Calendar |
| Shared Schedule Awareness | yes | no | yes | Microsoft 365 Calendar |
| Coordination Awareness | yes | no | yes | Microsoft 365 Calendar |
| Briefing Participation | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |
| Travel Awareness | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |
| Reservation Awareness | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |
| Awareness Experience | no | yes | yes | Microsoft 365 Email |
| Importance Surfacing | no | yes | yes | Microsoft 365 Email |
| Travel Highlights | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |
| Reservation Highlights | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |
| Delivery Highlights | no | yes | yes | Microsoft 365 Email |
| Action Awareness | no | yes | yes | Microsoft 365 Email |
| Household Productivity Awareness | yes | yes | yes | Microsoft 365 Calendar and Microsoft 365 Email |

---

## Boundary Review

This contract preserves explicit separation between:

- Calendar Experience
- Email Experience
- Briefing Experience
- Household Memory
- Provenance
- Microsoft 365 source systems

Separation rules:

- Calendar Experience remains a governed experience, not calendar authority
- Email Experience remains a governed experience, not mailbox authority
- Briefing Experience consumes Calendar and Email experiences and does not become source-of-record
- Household Memory may consume productivity events but does not own calendar or email truth
- Provenance remains authoritative for attribution and lineage
- Microsoft 365 remains the source-of-record for calendar and email truth when configured

Ownership overlap is prohibited.

---

## Canonical Architecture Linkage

This contract must appear in canonical traceability as the governance boundary for Calendar and Email Experience.

Future planning must treat this contract as a mandatory dependency for:

- E12 governance validation
- E13 productivity experience planning
- E14 provenance consumption

This contract is the authoritative input for productivity planning.

---

## Final Principle

Calendar and Email Experiences are governed household productivity experiences that consume authoritative Microsoft 365 source data, household memory, and provenance without taking ownership of source truth.