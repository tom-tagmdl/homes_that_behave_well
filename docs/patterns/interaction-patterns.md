# Interaction Patterns

## Purpose

Interaction Patterns define how Concierge surfaces actionable and contextual experiences to the user across voice and UI.

Interactions represent what the user can see, respond to, or act upon at a given moment.

Interactions are derived from:

- Signals (household state)
- Global Context (informational sources)
- Room capabilities

Interactions do not own data and must not persist system state.

---

## Core Principle

Signals define what is true.

Context defines what is known.

Interactions define what is available to the user right now.

---

## Interaction Model

An Interaction is a transient construct that represents a user-facing opportunity for awareness or action.

Structure:

interaction:
  id:
  type:
  source:
  summary:
  detail:
  actions:
  priority:
  expires_at:

Interactions are:

- ephemeral
- derived
- context-aware

Interactions must not be stored as system-of-record data.

---

## Interaction Types

Interactions fall into four primary types:

1. Context Display
2. Signal Awareness
3. Actionable
4. Guided Workflow

---

# 1. CONTEXT DISPLAY PATTERNS

---

## Context → Display

Used for presenting Global Context such as:

- news
- weather details
- time-based summaries

Flow:

- user requests context OR system includes context in summary
- Concierge retrieves context via service
- generates interaction
- UI renders context content

Example:

User:
Show me the news

Interaction:

summary:
Top headlines available

detail:
List of headlines

Rules:

- must use context-provided data
- must not fetch data directly in UI
- must remain consistent with speakable output

---

## Expanded Context Display

Used when additional detail is requested.

Example:

Show more details

Flow:

- context provider returns extended detail
- interaction updates
- UI reflects expanded state

Rules:

- expansion must be deterministic
- must not introduce new data sources dynamically

---

# 2. SIGNAL AWARENESS PATTERNS

---

## Signal → Awareness

Surfaces signal state to the user.

Example:

Laundry completes

Interaction:

summary:
Laundry is complete

actions:
Acknowledge

Rules:

- must be based on signal state
- must not re-evaluate logic
- must remain consistent with signal.speakable

---

## Passive Awareness

Signal is surfaced without interrupting the user.

Example:

Displayed on kiosk dashboard

Rules:

- must respect communication level
- must not trigger unnecessary voice output

---

## Aggregated Awareness

Multiple signals combined.

Example:

Morning dashboard:

- calendar
- laundry
- reminders

Rules:

- must use signal summaries
- must maintain ordering based on priority
- must avoid duplication

---

# 3. ACTIONABLE INTERACTION PATTERNS

---

## Actionable Interaction

Presents available actions to the user.

Example:

Shopping list

actions:
- Add item
- Remove item

Flow:

- interaction displays actions
- user selects via UI or voice
- Concierge invokes service

Rules:

- actions must map to service calls
- Concierge must not implement action logic
- responses must confirm execution

---

## Action + State Refresh

After an action, interaction must refresh.

Example:

Add milk → list updates

Rules:

- must retrieve updated signal state
- must reflect new summary
- must remain consistent across UI and voice

---

# 4. GUIDED WORKFLOW PATTERNS

---

## Step-Based Interaction

Used for guided setup or multi-step processes.

Example:

Learn this room

Interaction:

Step 1:
Select speaker

Step 2:
Confirm devices

Step 3:
Enable sensors

Rules:

- steps must be explicit
- progress must be deterministic
- must be resumable within session

---

## Contextual Workflow Trigger

Workflow begins based on user request.

Example:

User:
Set up this room

Rules:

- must resolve room context first
- must generate appropriate steps
- must not assume configuration

---

# INTERACTION LIFECYCLE

---

## Creation

Interactions are created when:

- user asks for information
- signal state changes
- workflow begins

---

## Update

Interactions must update when:

- signal state changes
- user performs an action
- additional detail is requested

---

## Expiration

Interactions must expire when:

- no longer relevant
- replaced by updated interaction
- timeout reached

Rules:

- expiration must be deterministic
- stale interactions must not remain visible

---

## Removal

Interactions must be removed when:

- explicitly dismissed
- underlying signal becomes unavailable
- context is no longer valid

---

# ROOM PROJECTION

---

## Interaction Surface

Each room may expose an Interaction Panel.

Personal devices may expose a Mobile Interaction Plane.

This panel displays:

- context interactions
- signal interactions
- actionable interactions

The mobile plane may display:

- pushed context digests
- actionable follow-up items
- read-later interaction content

Rules:

- panel must reflect current interactions only
- must not store independent state
- must remain synchronized with Concierge
- mobile plane must be derived from the same interaction and context outputs as room UI/voice
- when a person is selected or confidently resolved, mobile delivery targets must be filtered to that person's enabled targets

---

## Voice and UI Parity

Interactions must be accessible via:

- voice
- UI
- mobile app

Rules:

- both entry points must invoke same services
- UI must reflect voice-triggered interactions
- voice must reflect UI-triggered actions
- person-scoped target options (phone/tablet) must match people-card configuration and not expose unavailable targets
- mobile typed and mobile voice requests must follow the same intent path

---

## Mobile Room-Context Query Pattern

Example:

- user asks from phone: "what art is in this room"

Flow:

- resolve person from configured mobile target
- resolve room from BLE and supporting presence context
- if confidence is sufficient, return room-aware art summary
- if confidence is low, ask concise clarification

Rules:

- responses must include explainable room attribution when room context is used
- person identity may tune style and detail, not factual inventory
- room-context informational queries must never silently fall back to an arbitrary room

---

## Output Routing

Voice responses must follow audio routing rules:

1. preferred speaker
2. speaker candidates
3. voice device speaker fallback

UI rendering must be independent of audio routing.

---

# PRIORITY AND ORDERING

---

## Priority Levels

Interactions may be ordered by priority:

- urgent
- attention
- info

Rules:

- priority must be deterministic
- ordering must be stable
- higher priority interactions appear first

---

## Relevance Filtering

Interactions must be filtered based on:

- room context
- user presence
- system mode

Rules:

- irrelevant interactions must not be displayed
- filtering must be explainable

---

# FAILURE HANDLING

---

## Interaction Failure

If required data is unavailable:

- interaction must not be created
- user must receive clear response

Example:

I am unable to retrieve that information right now.

---

## Partial Data

If only partial data exists:

- interaction must display available information
- must not fabricate missing data

---

# AI ASSISTED INTERACTIONS

---

## AI Summarization

AI may combine multiple interactions into a unified presentation.

Rules:

- must use integration-provided data
- must not alter underlying state
- must remain explainable

---

# SEPARATION OF CONCERNS

---

Concierge must:

- generate interactions
- route actions
- manage lifecycle

Concierge must not:

- store interaction state permanently
- define signal logic
- define context data

UI must:

- render interactions only
- not perform service logic
- not fetch data independently

---

# FINAL PRINCIPLE

Interactions define what the user can do.

They must always be:

- current
- accurate
- actionable
- derived from system truth

The system must never present an interaction that it cannot fulfill.