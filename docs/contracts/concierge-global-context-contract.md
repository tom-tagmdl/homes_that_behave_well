# Concierge Global Context Contract

## Purpose

Global Context provides shared, whole-home informational capabilities that can be accessed and presented by Concierge in any room.

Global Context represents ambient, continuously available information about the home or external environment.

It is not stateful in the same way as Signals and does not represent actionable household state.

---

## Core Principle

Global Context defines what the system knows about the world.

Signals define what is happening in the home.

Concierge combines both to provide meaningful awareness.

---

## Definition

Global Context represents:

- Informational data sources
- Broad, non-stateful awareness
- Continuously available reference information

Examples include:

- Weather
- Time and date
- News
- Email summaries
- External system awareness

Global Context must be human-consumable and ready for presentation.

---

## Key Characteristics

Global Context is:

- Informational
- Stateless or continuously updating
- Non-actionable (primarily)
- Globally available across the home

Global Context is not:

- A representation of task completion
- A trigger for automation decisions
- A replacement for Signals

---

## Context Categories

Global Context may include:

### Ambient Context

- weather
- time
- external conditions

### Informational Content

- news
- briefings
- summaries

### External System Context

- email (e.g., unread summaries)
- external alerts
- general information feeds

---

## Ownership Rules

Global Context is owned and exposed by integrations.

Examples:

- Weather → weather integration
- Time → system clock / Home Assistant core
- News → feed integration
- Email → external provider (e.g., Microsoft 365)

Provider adapter rule:

- Global Context must support entity-sourced and event-sourced providers
- Event-sourced providers (for example Feedreader) must be normalized into the same context structure before Concierge consumption

Concierge must never:

- generate its own context data
- store context state
- infer context outside provided services

---

## Context Structure

Each Global Context source must expose the following structure:

context:
  id:
  type:
  provider:
  available:
  summary:
  detail:
  speakable:

News context must additionally support:

news_context:
  source_profile:
  feeds:
  curated_headlines:
  digest_generated_at:
  freshness_window_minutes:

---

## Field Definitions

### id

Unique identifier of the context source.

Examples:

weather.home  
time.system  
news.morning_briefing  
email.summary  

---

### type

Defines the category of context.

Examples:

- weather
- time
- news
- email

---

### provider

The integration providing the context.

---

### available

Boolean indicating whether the context is currently available.

Concierge must check availability before use.

---

### summary

Short, human-readable description suited for UI display.

Examples:

Partly cloudy, 85 degrees  
3 headlines available  
2:15 PM  
5 unread emails  

---

### detail

Optional extended information.

Examples:

High of 92, low of 75, humidity 60 percent  
Top headline details  
Email subject summaries  

---

### speakable

Fully composed response suitable for voice output.

Examples:

It is currently partly cloudy and 85 degrees.  
Here are today’s top headlines.  
You have five unread emails.  

Concierge must use this directly and must not reconstruct phrasing.

---

## Service Interface Requirements

Global Context must be accessible via services.

Minimum capabilities:

- Retrieve current context
- Retrieve summary
- Retrieve speakable output

Concierge must interact only via defined services.

---

## Room Projection Model

Global Context is not owned by rooms but may be projected into rooms.

Rooms may:

- enable or disable specific context types
- control whether context is speakable
- control inclusion in summaries
- define ordered source priority for context projection (for example weather and news)

Example:

room:
  global_overlays:
    weather: true
    news: false
    email: true
  context_projection_priority:
    weather:
      - weather.national
      - weather.local_station
    news:
      - news.general
      - news.business

Rules:

- context must not be duplicated per room
- enablement affects visibility only
- data remains global
- if a room exposes dashboard targets, Global Context projection may include a dashboard payload for that room
- dashboard payload and speakable payload must be derived from the same underlying context selection
- if a room exposes phone targets, Global Context projection may include a mobile payload for that room
- mobile payload, dashboard payload, and speakable payload must remain selection-consistent
- room source priority may reorder only globally available sources
- room source priority must never expand global availability
- when room priority is absent, projection uses global default source order

---

## External Data Source Model

Global Context may originate from external systems.

These systems must follow a separation model:

### Connection (Global Configuration)

- authentication
- API setup
- provider selection

### Usage (UI Configuration)

- enable/disable context
- define behavior
- define summarization preferences

Example:

Microsoft 365:

Connection:
- configured in integration settings

Usage:
- enable email summaries
- enable calendar summaries

---

## Interaction Model

Global Context is primarily:

- query-driven
- summary-driven

Examples:

What is the weather  
What time is it  
What is the news today  
Do I have any emails  

Concierge must:

- resolve request
- retrieve context
- deliver response

---
## Media Boundary

Media-related data that depends on room playback state or recent playback history does not belong in Global Context.

Examples:

- last played in this room
- continue playing reference
- room-scoped playback memory

These values are room-scoped retained operational values and must be modeled outside Global Context.

Global Context may still expose broad informational media summaries only when they are integration-provided and globally meaningful.

---
## Summarization Behavior

Some context may require summarization.

Examples:

- news
- email
- long-form external data

Summarization rules:

- must use provider data only
- may use AI if enabled
- must remain accurate and explainable

News summarization rules:

- must run deterministic deduplication before summarization
- must apply configured source and topic weighting before final selection
- must expose score rationale for selected headlines
- must respect configured freshness window and max headlines

---

## AI Usage

AI may assist with:

- summarizing long-form context
- improving natural language delivery

AI must not:

- create context data
- replace integration-provided values
- introduce unverifiable information

---

## Communication Rules

Global Context follows Concierge communication levels:

- Info → visual only
- Attention → optional voice
- Urgent → rarely applicable

Channel behavior:

- visual channel includes dashboard or UI payload delivery
- voice channel uses speakable output when policy permits
- quiet or low-disturbance posture should prefer visual channel over voice

Global Context is typically:

- user-requested
- included in summaries

It must not be:

- proactively announced without intent
- disruptive or noisy

Morning briefing inclusion:

- news may be included in morning briefing when enabled
- news section must use curated digest output, not raw feed order
- briefings must cap headline count according to configured profile
- when room dashboard is available, morning briefing should project a visual digest card/panel payload

---

## Failure Handling

If context is unavailable:

Concierge must:

- provide a clear response
- avoid guessing or fabricating data

Example:

I am unable to retrieve the weather right now.

---

## Relationship to Signals

Global Context and Signals are distinct:

Global Context:
- Informational
- Continuous
- Non-actionable

Signals:
- Stateful
- Actionable
- Represent household conditions

Concierge must:

- use Global Context for awareness
- use Signals for state-driven decisions

---

## System Behavior Rules

Global Context must:

- be accurate and integration-provided
- be consistent across interactions
- be safe for repeated use

Global Context must not:

- trigger automation decisions
- override signal-based logic
- introduce ambiguity

---

## Final Principle

Global Context provides awareness of the world.

Signals provide awareness of the home.

Concierge brings both together to create a complete, context-aware experience.