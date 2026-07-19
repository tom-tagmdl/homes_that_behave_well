# Service Contracts

## Purpose

Service Contracts define the API layer through which Concierge interacts with:

- UI
- integrations
- runtime execution
- external systems

All system interaction must occur through defined services.

Services provide the only supported mechanism for:

- reading state
- updating configuration
- executing actions
- retrieving interactions

---

## Core Principle

All system interaction flows through services.

UI does not execute logic.

Runtime does not bypass services.

---

## Service Design Rules

Services must:

- be deterministic
- have explicit inputs and outputs
- enforce validation before execution
- follow configuration-driven behavior

Services must not:

- contain hidden logic
- perform uncontrolled side effects
- bypass configuration or contracts

---

## Service Categories

Services are grouped into five categories:

1. Execution Services
2. Interaction Services
3. Signal Services
4. Configuration Services
5. Context Services

Scope model for configuration services:

- concierge-wide services define whole-home policy
- floor-wide services define floor defaults and shared infrastructure bindings
- room-wide services define local overrides

Effective resolution priority:

1. room-wide
2. floor-wide
3. concierge-wide

---

# 1. EXECUTION SERVICES

---

## Purpose

Execute actions within the home using predefined execution patterns.

---

## concierge.execute

Executes an action based on resolved intent.

Structure:

service: concierge.execute

input:
  target:
  area_id:
  composite_id:
  context:

behavior:

- resolve execution target from configuration
- apply execution hierarchy (scene → group → entity)
- execute via Home Assistant services

rules:

- must not perform runtime discovery
- must use preconfigured execution targets
- must execute in a single service call whenever possible
- when resolved actor_class is minor, intent handling must enforce configured minor_interaction_policy and allowed intent classes

---

## concierge.execute_direct

Used when an explicit entity or scene is already resolved.

Structure:

service: concierge.execute_direct

input:
  entity_id:
  service:
  data:

rules:

- must bypass orchestration logic
- must only be used for direct execution paths (alias-first)

---

# 2. INTERACTION SERVICES

---

## Purpose

Provide access to interaction model for UI and voice integration.

---

## concierge.get_interactions

Returns active interactions for a room or composite.

input:
  area_id:
  composite_id:

output:
  interactions:

rules:

- must return only active interactions
- must respect expiration rules
- must be ordered by priority

---

## concierge.update_interaction

Updates interaction state.

input:
  interaction_id:
  state:

rules:

- must validate state transition
- must not persist invalid states

---

## concierge.clear_interaction

Removes an interaction.

input:
  interaction_id:

rules:

- must remove interaction from runtime
- must not affect underlying signals

---

# 3. SIGNAL SERVICES

---

## Purpose

Provide access to household state.

---

## concierge.get_signal

Returns a specific signal.

input:
  signal_type:

output:
  signal:

rules:

- must use Signal Contract
- must not infer state
- must return deterministic results

---

## concierge.get_signals

Returns all available signals.

input:
  area_id:
  composite_id:

output:
  signals:

rules:

- must respect room enablement
- must filter unavailable signals

---

# 4. CONFIGURATION SERVICES

---

## Purpose

Manage configuration through controlled API.

All configuration updates must occur through these services.

---

## concierge.update_room_config

Updates room configuration.

input:
  area_id:
  configuration:

rules:

- must validate structure
- must enforce schema rules
- must write to store only after validation
- may override floor defaults for that room
- must support room posture override for local calm behavior (including naps and early sleep)
- must persist setup-authored device_groups and asset_groups with stable group_key and display_name vocabulary
- must reject invalid entity references and remove stale group members deterministically
- runtime must consume persisted group mappings; service updates must not depend on runtime category discovery

---

## concierge.update_floor_config

Updates floor configuration.

input:
  floor_id:
  thermostat_entity_ids:
  climate_strategy:
  speaker_group_entity_ids:
  media_defaults:
  posture_default:

rules:

- must validate floor_id exists in Home Assistant floor registry
- floor thermostat/HVAC bindings are the default for rooms on that floor
- room config may override floor defaults
- must not mutate room definitions directly

---

## concierge.get_floor_config

Returns floor configuration and effective defaults.

input:
  floor_id:

output:
  floor_config:
  effective_defaults:

rules:

- must return deterministic values
- must include missing/invalid binding diagnostics

---

## concierge.update_composite_config

Updates composite room configuration.

input:
  composite_id:
  configuration:
  name:
  area_ids:

rules:

- must validate areas exist
- must enforce execution preferences
- must not conflict with room definitions
- must support merged room definitions where multiple areas resolve to one interaction context
- must support composite rename and membership edits in one deterministic update
- if area_ids becomes empty, composite must be dismantled and removed
- if area_ids removes some members, removed rooms must return to standalone projection
- composite inventory and selectors must be recalculated from remaining members only

---

## concierge.sync_composites

Validates and rebuilds merged room runtime projections.

input:
  add_missing:
  remove_invalid:

output:
  composites:
  validation_errors:

rules:

- must validate every member area exists
- must validate that voice invocation from any member area resolves to the same composite context
- must reject ambiguous membership unless explicitly allowed by policy
- must clear stale device references for rooms no longer in each composite

---

## concierge.update_global_context

Updates global context usage.

input:
  context_type:
  enabled:
  options:

rules:

- must not modify underlying providers
- must only affect usage

---

## concierge.update_alarm_authority

Updates person-level alarm control grants.

input:
  person_id:
  alarm_control:
    allowed:
    allowed_actions:
    disarm_allowed:
    requires_voice_attribution:
    requires_step_up_for_disarm:

rules:

- must validate person_id exists
- must validate grants against global alarm policy
- must write audit metadata for grant changes
- must reject disarm grant when global policy forbids disarm control

---

## concierge.control_alarm

Executes a protected alarm action through policy and authorization checks.

input:
  action:
  target_entity_id:
  auth_context:
    person_id:
    voice_attribution_confidence:
    step_up_verified:
    mobile_confirmation_id:
    mobile_confirmation_verified:
    source:

output:
  applied:
  denied_reason:
  pending_confirmation:
  confirmation_id:
  confirmation_expires_at:
  audit_id:

rules:

- must require global alarm provider enablement
- must require resolved person authorization for requested action
- voice attribution alone must not authorize disarm
- when disarm_step_up_required is true, must require step_up_verified
- when disarm_step_up_mode is app_confirmation, must require verified mobile confirmation before disarm
- app confirmation should target the authorized person's registered Home Assistant mobile device(s)
- if confirmation expires or fails, action must be denied and audited
- must produce auditable allow or deny outcomes

---

## concierge.update_global_policy

Updates concierge-wide policy.

input:
  quiet_hours:
  urgent_bypass:
  capability_toggles:

rules:

- quiet-hours policy is concierge-wide default
- room posture may increase suppression at room scope
- updates must validate policy consistency before persisting

---

## concierge.update_person_profile

Updates person profile configuration.

input:
  person_id:
  linked_area_id:
  ble_device_ids:
  aqara_presence_entity_ids:
  voice_profile_id:
  interaction_targets:
  household_classification:
  minor_interaction_policy:

rules:

- must validate person_id exists
- must validate linked interaction targets map to known mobile notify targets
- must enforce minor policy constraints deterministically
- when AI capability is unavailable, AI-dependent person policy fields must normalize to safe defaults
- when TTS capability is unavailable, mobile voice endpoint usage must be disabled
- capability normalization must not silently invent person data

---

## concierge.start_voice_enrollment

Starts explicit person voice enrollment.

input:
  person_id:
  consent_acknowledged:

rules:

- must require explicit consent acknowledgment
- must require voice enrollment capability to be enabled by global options
- must reject start requests when archive destination or archive enablement policy is not valid
- enrollment state persistence may remain intact when capability is disabled; runtime actions are gated by capability

---

## concierge.update_execution_preferences

Defines execution behavior.

input:
  area_id or composite_id:
  preferences:

rules:

- must enforce execution hierarchy
- must validate scenes and groups exist

---

## concierge.update_music_routing

Updates Music Assistant routing policy at concierge, floor, or room scope.

input:
  scope:
  scope_id:
  routing:
  tts_behavior:

rules:

- concierge scope enables capability and global safety policy
- floor scope defines default routing/group behavior
- room scope defines endpoint overrides
- TTS duck/pause/resume behavior must be deterministic

---

# 5. CONTEXT SERVICES

---

## Purpose

Provide access to global context (weather, news, email, etc.).

---

## concierge.get_context

Retrieves a global context item.

input:
  context_type:

output:
  context:

rules:

- must use Global Context Contract
- must not generate context independently

---

## concierge.update_news_sources

Updates global news feed inclusion and curation policy.

input:
  provider_type:
  provider_id:
  selected_feed_ids:
  include_topics:
  exclude_topics:
  max_headlines_per_digest:
  freshness_window_minutes:
  dedupe_window_hours:
  source_priority_map:
  ai_summary_enabled:

output:
  applied:
  rejected_feed_ids:

rules:

- must validate selected feeds against discovered provider feeds
- must reject unsupported or unavailable providers
- must apply atomically
- must not mutate provider-side configuration

---

## concierge.get_news_digest

Returns curated news digest output for a request profile.

input:
  profile:
  area_id:
  person_id:
  delivery_channel:
  delivery_target_id:
  max_items:

output:
  headlines:
  speakable:
  dashboard_payload:
  mobile_payload:
  generated_at:

rules:

- must use deterministic dedupe and scoring
- must only include configured and enabled feeds
- must remain within freshness window
- must return empty digest explicitly when no eligible items exist
- when area_id resolves to a room with dashboard targets, must return a dashboard_payload variant suitable for UI projection
- when area_id resolves to a room or person with phone targets, must return a mobile_payload variant suitable for Home Assistant mobile push delivery
- when person_id is provided, delivery_target_id must be one of that person's enabled mobile_app_targets
- if delivery_target_id is omitted and person_id is provided, Concierge may use that person's preferred_read_later_target when valid

---

## concierge.get_summary

Returns a combined summary.

input:
  area_id:
  include_signals:
  include_context:

output:
  summary:

rules:

- may use AI for summarization (if allowed)
- must remain grounded in real data

---

## concierge.resolve_mobile_context

Resolves person and room context for mobile voice or typed requests.

input:
  mobile_target_id:
  person_id:
  request_text:

output:
  resolved_person_id:
  person_confidence:
  resolved_area_id:
  room_confidence:
  attribution_factors:
  clarification_required:

rules:

- must fuse person-linked mobile device identity with available presence context
- must expose room confidence explicitly
- when room_confidence is low, must set clarification_required true

---

## concierge.push_person_message

Delivers a person-scoped message to the requested household output channel.

input:
  person_id:
  target_id:
  message:
  title:
  data:

output:
  sent:
  person_id:
  target_id:
  service:
  messaging_governance_boundary:

rules:

- must resolve delivery against the best available room context before falling back to the person's linked room
- must treat explicit entity targets as higher priority than symbolic target names when both are valid
- web UI and dashboard-style targets must use Home Assistant persistent notification delivery
- voice-assistant targets must use Assist Satellite announce semantics and may synthesize TTS media first when TTS is configured
- speaker targets must use the room's configured TTS settings when present
- when room TTS settings are blank, delivery must fall back to integration-level voice defaults without inventing new voice settings
- mobile targets must route through the person's configured mobile notify targets
- delivery decisions must remain deterministic and explainable

---

## concierge.get_room_art_summary

Returns room-aware art inventory and descriptions for an identified person.

input:
  area_id:
  person_id:
  detail_level:
  include_descriptions:

output:
  area_id:
  room_name:
  artworks:
  speakable:

rules:

- must return art inventory grounded in configured room and asset data
- must not fabricate unknown artwork attributes
- person context may tune verbosity and detail level only
- when area_id is unresolved and room confidence is low, must require clarification instead of guessing

---

# 6. AUDIT SERVICES

---

## Purpose

Provide stitched orchestration auditability without duplicating full upstream logs.

---

## concierge.record_activity_event

Appends a Concierge orchestration activity event.

input:
  activity_id:
  correlation_id:
  started_at:
  channel:
  actor_class:
  intent_class:
  request_summary:
  resolved_person_id:
  resolved_area_id:
  confidence:
  external_refs:

output:
  recorded:

rules:

- must be append-only
- must store orchestration metadata and references, not full duplicated source logs
- external_refs must support voice, service context, automation trace, and notification IDs when available
- for actor_class=guest, intent_class and outcome fields must be retained even when request_summary is minimized
- for actor_class=minor, intent_class and outcome fields must be retained and request_summary should be minimized by default

---

## concierge.close_activity_outcome

Closes a previously recorded activity with final outcome.

input:
  activity_id:
  ended_at:
  outcome:
  outcome_reason:
  actions_taken:
  policy_gates:

output:
  closed:

rules:

- outcome is required for every closed activity
- must capture success, partial, denied, failed, or canceled
- must include denial/failure reason codes when applicable

---

## concierge.get_activity_timeline

Returns activities for a requested time window.

input:
  start:
  end:
  actor_class:
  person_id:
  area_id:
  channel:

output:
  activities:

rules:

- results must be chronologically ordered
- each item must include outcome and stitched external references
- queries such as "what activities did you facilitate yesterday" must be supported through this timeline model
- guest timeline entries must be readable without requiring person identity resolution
- minor timeline entries should omit unnecessary free-text detail unless explicitly permitted by policy

---

## concierge.export_activity_archive

Exports a self-contained readable archive package for offline retention.

input:
  start:
  end:
  destination:
  include_reference_excerpts:

output:
  archive_uri:
  item_count:
  generated_at:

rules:

- exported archive must be readable without live access to source integrations
- package should include concise normalized excerpts and stitched references required for reconstruction
- package must not duplicate full raw logs unless explicitly required by policy
- archive must be immutable and retention-policy governed

---

# VOICE INTEGRATION FLOW

---

Voice processing must follow:

1. Assist resolves entity or alias
2. If match:
   → concierge.execute_direct

3. If no match:
   → concierge.execute (orchestrated)

rules:

- must prefer direct execution
- must minimize latency
- must remain deterministic

---

# UI INTEGRATION FLOW

---

UI must:

- call services for all actions
- never invoke execution directly
- never modify store directly

Example:

User clicks action →

- UI calls concierge.execute
- runtime performs action
- UI updates via get_interactions

---

# AI INTEGRATION

---

AI may be invoked only through services.

AI usage must be:

- optional
- bounded
- controlled by global configuration

AI must not:

- directly call execution services
- bypass validation
- modify system state

---

# VALIDATION REQUIREMENTS

---

All services must:

- validate inputs
- validate entity existence
- validate configuration integrity

Invalid requests must:

- be rejected
- return clear error messages

---

# PERFORMANCE REQUIREMENTS

---

Services must:

- use precomputed configuration
- avoid runtime discovery
- execute in a single call when possible

The system must not:

- introduce loops in execution path
- perform template processing at runtime

---

# FAILURE HANDLING

---

If service fails:

- return clear response
- do not retry indefinitely
- do not produce partial execution

Fallback must:

- follow execution hierarchy
- remain deterministic

---

# SECURITY RULES

---

Services must:

- respect integration boundaries
- prevent unauthorized access
- protect sensitive data

Sensitive configuration must not be exposed through service outputs.

---
# CAPABILITY MODEL

---

## Purpose

Defines callable system capabilities exposed by Concierge.

Capabilities represent:

- actions (play music)
- informational queries (air quality)
- advisory responses (why something happened)

---

## Structure

capabilities:

  <capability_id>:
    type:
    domain:
    requires_context:

Example:

capabilities:

  speak_air_quality:
    type: informational

  play_music:
    type: action

  explain_music_choice:
    type: advisory

---

## Types

- action
- informational
- advisory

---

## Rules

Capabilities must:

- map to a service or execution path
- be deterministic
- be reusable across voice and UI

Capabilities must not:

- embed logic in UI or automations
- duplicate execution paths

---

# V2 GOVERNANCE CONSUMPTION

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-008 Personalization Governance Boundaries
- ADR-009 Household Memory Governance Boundaries
- ADR-010 Household Productivity Experience Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

Service contracts define interfaces and validation behavior.

Service contracts do not redefine architecture ownership or governance authority.

---

# OWNERSHIP BOUNDARY VALIDATION

Service boundaries preserve:

- Foundation ownership of room, area, device, and occupancy truth
- Voice Identity ownership of attribution and confidence
- Asset Intelligence ownership of significance and environmental interpretation
- Coordinator V2 orchestration-only role under governed contracts

Service execution must not create ownership drift.

---

# TERMINOLOGY ALIGNMENT

Canonical terminology used in this contract:

- Room
- Area
- Floor
- Composite Room
- Capability
- Experience
- Personalization
- Household Memory
- Provenance
- Occupancy
- Presence
- Attribution
- Confidence
- Context
- Scope

Legacy V1 assumptions that allow hidden inference or direct runtime ownership transfer are prohibited.

---

# FINAL PRINCIPLE

Services define how the system is used.

All behavior must pass through:

- explicit contracts
- validated inputs
- deterministic execution

The system must never operate outside of defined service boundaries.