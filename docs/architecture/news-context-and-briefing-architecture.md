# News Context And Briefing Architecture

## Purpose

This document defines the official architecture for news ingestion, curation, and delivery in Concierge.

It establishes a deterministic, local-first path from configured feeds to room-aware and person-aware briefings.

---

## Scope

This architecture covers:

- news provider connection and configuration
- feed selection and inclusion policy
- headline ingestion and normalization
- deduplication and importance scoring
- curated summary generation
- room and person-aware delivery
- morning briefing composition

This architecture does not define:

- third-party provider implementation details
- UI styling specifics
- speech synthesis internals

---

## Homes That Behave Well Alignment

News behavior must remain:

- deterministic
- explainable
- calm
- local-first

Rules:

- provider data is the source of truth
- Concierge may summarize, rank, and filter but must not invent facts
- user-selected feeds and policies control curation
- briefings must respect quiet-hours and posture policy

---

## Problem Statement

Some news providers in Home Assistant are entity-based, while others (such as Feedreader) are event-sourced.

A UI that only lists entity providers can omit valid configured providers.

Therefore, Concierge news architecture must support both:

- entity-based providers
- event-sourced providers

---

## Canonical Architecture

### Layer 1: Provider Adapter Layer

Provider adapters normalize provider differences into a single Concierge News Source model.

Adapter types:

- Entity Adapter: reads provider state/services
- Event Adapter: subscribes to provider events and normalizes payloads

Examples:

- Feedreader uses an Event Adapter
- future headline integrations may use Entity or Event adapters

Output contract:

- normalized headline candidate events
- source metadata
- provider availability state

---

### Layer 2: Ingestion And Normalization Layer

Concierge stores normalized headline records in local retained state.

Each record must include:

- source_id
- feed_id
- title
- url
- published_at
- summary
- content_hash
- first_seen_at
- last_seen_at

Normalization rules:

- title trim and whitespace normalization
- URL canonicalization when possible
- deterministic content hash
- duplicate detection by hash and URL

---

### Layer 3: Curation Layer

Curation selects a concise set of high-value items from normalized records.

Curation stages:

1. freshness filtering
2. duplicate collapse
3. source and topic weighting
4. importance scoring
5. final selection by profile and mode

Curation output:

- curated headlines list
- explainable score breakdown per selected headline
- speakable summary payload

---

### Layer 4: Delivery Layer

Delivery projects curated news into:

- on-demand responses
- morning briefing bundles
- room overlays (when enabled)
- room dashboard cards or panels (when a dashboard endpoint exists in that room)

Delivery rules:

- never bypass posture and quiet-hours policy
- voice delivery is opt-in by context level
- use room audio routing rules for output target
- when room dashboard targets are configured, Concierge must provide a visual digest payload suitable for read-at-a-glance consumption

---

## Multi-Channel Delivery Model

News orchestration must support parallel output channels:

- Voice channel (TTS): optional, context and posture governed
- Visual channel (dashboard): preferred for low-disturbance and read-later usage
- Mobile channel (phone push): explicit personal read-later delivery

Channel rules:

- visual delivery is allowed even when TTS is suppressed
- TTS and dashboard payloads must derive from the same curated digest set
- mobile payload must derive from the same curated digest set used for voice/dashboard
- when both channels are enabled, voice should deliver concise highlights while dashboard carries fuller detail
- if a room has no dashboard endpoint configured, visual delivery is skipped without error
- if a room or person has no eligible phone target configured, mobile delivery is skipped without error
- explicit "send to phone" requests should prefer mobile delivery without requiring spoken full-detail playback

---

## News Source Configuration Model

News configuration is global and user-managed.

Required configuration fields:

- provider_type (feedreader, other)
- provider_id
- enabled
- selected_feed_ids
- include_topics
- exclude_topics
- language_filters
- max_headlines_per_digest
- freshness_window_minutes

Optional behavior fields:

- source_priority_map
- dedupe_window_hours
- ai_summary_enabled

Room projection ordering rule:

- global config defines available news sources
- room config may define preferred ordering of those available sources for projection and briefing emphasis
- room ordering may not reference non-enabled global sources

Example:

- Bedroom order: general first, business second
- Office order: business first, general second

---

## Importance Scoring Model

Scoring must be deterministic and explainable.

Recommended score dimensions:

- freshness_score
- source_priority_score
- topic_match_score
- duplicate_penalty
- recency_decay

Example deterministic score:

score = freshness + source_priority + topic_match - duplicate_penalty - decay

All scoring weights must be configurable in global policy and versioned.

---

## Feed Inclusion Model

Users must be able to select which feeds are included in Concierge curation.

Rules:

- default: no feed is implicitly included without explicit enablement
- selected feeds define ingestion scope
- excluded feeds are not considered for scoring or summaries
- feed changes apply without requiring schema migration

---

## Morning Briefing Composition

Morning Briefing is a composed output built from multiple context providers.

Default section order:

1. weather
2. calendar
3. home alerts and signals
4. overnight or morning news digest
5. commute and traffic (if configured)

News contribution rules:

- must use curated digest output
- must cap headline count per profile
- must provide short and detailed speakable variants
- should provide a dashboard-friendly visual variant when a room dashboard exists
- should provide a phone-friendly mobile variant when a room/person phone target exists

---

## Runtime Ownership

Provider integrations own raw data.

Concierge owns:

- normalization state
- curation state
- ranking policy application
- speakable composition

Concierge must not own:

- provider connection credentials
- provider-side content generation

---

## Privacy And Data Residency

News ingestion is local-first.

Rules:

- feed content is processed locally by default
- AI summarization is optional and explicit
- if cloud summarization is enabled, this is local/cloud hybrid behavior and must be clearly disclosed

---

## Failure Handling

If provider is unavailable:

- report unavailable clearly
- fall back to other enabled news sources
- avoid stale replay outside freshness window

If no curated headlines are available:

- return an explicit no-news-available response

---

## Service And Contract Alignment

This architecture extends and constrains:

- Concierge Global Context Contract
- Concierge Global Configuration Contract
- Service Contracts
- Performance Contract

News behavior must be implemented through those contracts and not as ad-hoc runtime behavior.

---

## Implementation Phases

### Phase 1: Provider Inclusion And Feed Selection

- support event-sourced provider adapters (Feedreader)
- show selectable feeds in Concierge UI
- persist feed inclusion config

### Phase 2: Local Curation Engine

- normalized storage model
- dedupe and scoring pipeline
- explainable curated output

### Phase 3: Briefing Delivery

- on-demand news intent responses
- morning briefing composition with news section
- room and person-aware delivery controls

---

## Final Principle

News in Concierge is not a raw feed passthrough.

It is a deterministic context capability: explicitly configured, locally curated, explainable, and delivered in the right room at the right moment.
