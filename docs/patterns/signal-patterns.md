# Signal Patterns

## Purpose

Signal Patterns define reusable interaction behaviors for how Concierge consumes and presents Signals.

They ensure consistent behavior across:

- voice interactions
- UI presentation
- automation and announcements

Patterns do not define signal data.

Patterns define how signals are used.

---

## Core Principle

Signals represent state.

Patterns define how that state is revealed.

---

## Pattern Categories

Signal interaction patterns fall into four categories:

1. Query Patterns
2. Announcement Patterns
3. Suppression Patterns
4. Action Patterns

---

# 1. QUERY PATTERNS

---

## Query → Response

The most common pattern.

User requests signal information.

Concierge:

- resolves room context
- determines signal relevance
- retrieves signal via service
- delivers speakable response

Example:

User:
Is the laundry done?

Flow:

- resolve room
- identify signal: laundry
- retrieve signal
- return signal.speakable

Rules:

- Concierge must not interpret raw data
- Concierge must use signal.speakable directly
- response must match current signal state

---

## Summary Query

User asks for grouped or aggregated information.

Example:

What is going on today?

Flow:

- retrieve multiple signals
- combine summaries
- present in ordered format

Example output:

You have two events today. The laundry is done. There are five items on your shopping list.

Rules:

- order must be deterministic
- higher relevance signals first
- no duplication

---

## Contextual Query

Query depends on room or time context.

Example:

What should I know?

Flow:

- resolve room
- retrieve enabled signals for the room
- filter by relevance
- construct response

Rules:

- must respect room-level signal enablement
- must not include disabled signals
- must degrade gracefully if no signals

---

# 2. ANNOUNCEMENT PATTERNS

---

## Event → Announcement

Triggered when a signal emits a state change.

Examples:

- laundry.complete
- dishwasher.clean

Flow:

- signal emits event
- Concierge evaluates context
- decides whether to announce

Example output:

The laundry is done.

Rules:

- must use signal speakable output
- must respect communication level (info, attention, urgent)
- must not repeat announcements unnecessarily

---

## Conditional Announcement

Announcement depends on context.

Conditions may include:

- user presence
- active room
- time of day
- system mode (night, guest)

Example:

If someone is home:
The laundry is done.

If no one is home:
No announcement.

Rules:

- decisions must be deterministic
- conditions must be explainable
- no probabilistic behavior

---

## Delayed Announcement

Announcement is delayed until appropriate moment.

Example:

Laundry completes during night mode

Behavior:

- suppress immediate announcement
- deliver next morning or when user is active

Rules:

- must honor suppression policies
- must not lose signal state
- delayed delivery must still be relevant

---

# 3. SUPPRESSION PATTERNS

---

## Mode-Based Suppression

Signals are suppressed based on system mode.

Example:

Night Mode:

- suppress info
- suppress attention
- allow urgent

Rules:

- must follow Concierge communication model
- must be consistent across signals

---

## Repetition Suppression

Prevents repeated announcements for the same state.

Example:

Laundry complete must not be announced multiple times.

Rules:

- state change must trigger announcement once
- repeated identical state must be ignored

---

## Relevance Suppression

Suppress signals that are not relevant.

Example:

User in office:

- do not announce laundry unless requested

Rules:

- must consider room context
- must consider user interaction patterns

---

# 4. ACTION PATTERNS

---

## Action Invocation

User invokes a signal-supported action.

Example:

Add milk to the shopping list

Flow:

- resolve signal: shopping_list
- call action service
- confirm result

Response:

Milk has been added to your shopping list.

Rules:

- must call provider service
- must not modify signal directly
- must confirm success or failure

---

## Action + State Response

Action is followed by updated signal state.

Example:

Remove eggs from the list

Response:

Eggs have been removed. You now have three items on your shopping list.

Rules:

- updated state must be retrieved after action
- response must remain consistent with signal model

---

# SIGNAL PRIORITY AND ORDERING

---

## Priority Handling

Signals may be delivered in priority order.

Example ordering:

1. urgent events (safety)
2. time-sensitive (calendar)
3. state completion (laundry)
4. informational (shopping list)

Rules:

- ordering must be deterministic
- ordering must not vary between executions
- priority must be explainable

---

## Aggregation Pattern

Multiple signals are combined into one response.

Example:

Good morning:

- weather (context)
- calendar (signal)
- reminders (signal)

Rules:

- must not overwhelm the user
- must prioritize clarity
- must maintain consistent ordering

---

# ROOM PROJECTION BEHAVIOR

---

## Signal Availability

Signals are global but may be enabled per room.

Rules:

- disabled signals must not appear
- enabled signals must always be accessible
- projection must not modify signal state

---

## Output Routing

Signal responses must follow audio routing rules:

1. preferred room speaker
2. room speaker candidates
3. voice device speaker (fallback)

Rules:

- ordering must be enforced
- fallback must always be available
- no response may be dropped due to missing speakers

---

# FAILURE PATTERNS

---

## Signal Unavailable

If a signal is unavailable:

Response must be:

I do not have access to that information right now.

Rules:

- must not fabricate data
- must not guess state

---

## Partial Data

If signal detail is missing:

Response must fallback to available summary.

Rules:

- must remain accurate
- must not extrapolate missing information

---

# AI ASSISTED PATTERNS

---

## AI Summarization

AI may combine multiple signals into a natural summary.

Example:

You have a busy day with two meetings. The laundry is done, and you have a few items left on your shopping list.

Rules:

- must use signal-provided data
- must not invent or alter state
- must remain explainable

---

# FINAL PRINCIPLE

Signals define what is true.

Patterns define how truth is delivered.

Concierge must remain:

- deterministic
- explainable
- consistent across all interactions