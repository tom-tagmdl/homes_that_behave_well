# Concierge Global Configuration Contract

## Purpose

The Concierge Global Configuration Contract defines system-wide settings for Concierge.

It governs:

- provider enablement and connectivity
- global communication policy
- default behavior used when floor or room overrides are not configured

Global configuration is foundational and must remain separate from floor and room configuration.

---

## Core Principle

Global config defines defaults and policy.

Floor and room config define local behavior.

Global config must not remove room-level control of posture.

---

## Scope Boundary

Global configuration applies to:

- concierge-wide capability toggles (AI, TTS, Music Assistant, Asset Intelligence connectivity)
- whole-home context provider selection (weather, news, calendar, alarm)
- quiet-hours defaults
- urgent bypass policy
- protected-action policy for alarm control
- audit archive connection and destination policy
- minor AI safety policy

Global configuration does not own:

- room posture
- room entity bindings
- floor thermostat/HVAC routing details
- room-level weather/news projection priority ordering
- person-level alarm control grants
- per-activity audit content assembled at runtime

Global weather/news source ownership rule:

- Global configuration defines which weather and news sources are available to Concierge
- Room configuration may choose the ordering of those available sources for room projection
- Room configuration must not reference sources that are not globally enabled

Global alarm ownership rule:

- Global configuration defines the alarm provider connection and baseline alarm-control policy
- Person profiles define who is allowed to perform alarm control actions
- Alarm control availability in runtime must require both policy permission and resolved person authorization

Global audit archive ownership rule:

- archive storage connection and destination path are global integration settings
- archive runtime content is produced by Concierge activity services
- room and person configuration may influence activity context, but not archive destination wiring
- archive policy toggles are inactive until a valid destination_uri is configured

---

## Global Configuration Structure

concierge_global_config:
  providers:
    context:
      weather:
      news:
        provider_type:
        provider_id:
        enabled:
        selected_feed_ids:
        include_topics:
        exclude_topics:
        max_headlines_per_digest:
        freshness_window_minutes:
        dedupe_window_hours:
        source_priority_map:
        ai_summary_enabled:
      calendar:
      alarm_status:
        provider_type:
        provider_id:
        entity_id:
        enabled:
        allow_arm:
        allow_disarm:
        disarm_step_up_required:
        disarm_step_up_mode:
        disarm_step_up_timeout_seconds:
        disarm_mobile_confirm_requires_pin:
        audit_required:
    ai:
      enabled:
      local_first:
      provider:
      model:
      minor_safety_mode:
      minor_general_qna_enabled:
      minor_allowed_intent_classes:
      minor_content_filter_level:
    tts:
      enabled:
      provider:
      default_voice:
    music_assistant:
      enabled:
      provider:
      tts_ducking:
      tts_resume:
  communication:
    quiet_hours:
      enabled:
      start:
      end:
      timezone:
    urgent_bypass:
      enabled:
      allow_voice:
  defaults:
    posture_default:
    summary_style:
  audit:
    archive:
      enabled:
      storage_provider:
      destination_uri:
      export_schedule:
      retention_days:
      include_reference_excerpts:

Alarm policy notes:

- disarm_step_up_mode examples: spoken_confirmation, app_confirmation, presence_plus_confirmation
- voice attribution alone must not directly authorize protected alarm actions
- app_confirmation should use Home Assistant mobile push confirmation when available
- when disarm_mobile_confirm_requires_pin is true, mobile approval must include a PIN or equivalent secure local unlock flow

---

## Quiet-Hours Policy

Quiet-hours is concierge-wide policy.

Rules:

- quiet-hours defines the default suppression window across the home
- quiet-hours does not force room posture values
- room posture may further suppress interactions for one room (nap or early sleep)
- urgent behavior must follow urgent_bypass policy

---

## Room Posture Interaction

Room posture remains room-scoped.

Rules:

- room posture may suppress info and attention for that room at any time
- room posture does not alter global quiet-hours for other rooms
- effective communication behavior must be explainable as:
  room posture override -> floor default -> global quiet-hours default

---

## Thermostat and HVAC Defaults

Thermostat and HVAC zone routing should default to floor scope.

Global config may define policy but not specific per-floor entity bindings.

Examples of allowed global policy:

- allow proactive climate recommendations
- allow climate actions during quiet-hours (true/false)

Examples of floor-owned configuration:

- floor thermostat entity_id
- floor climate strategy defaults

---

## Music Assistant Configuration

Music Assistant is a concierge-wide capability toggle with local routing behavior.

Rules:

- enabling Music Assistant is global
- floor/room bindings decide where playback and TTS route
- Music Assistant must be treated as a capability provider, not only media_player passthrough
- pause/duck/resume behavior around TTS must be deterministic

---

## Validation Rules

Global config updates must:

- validate provider availability
- reject unsupported provider values
- reject invalid quiet-hours windows
- reject conflicting urgent_bypass combinations
- reject news configuration when selected_feed_ids contains unknown feed IDs
- reject negative or zero headline limits and freshness windows
- reject invalid source_priority_map values
- reject alarm control policy combinations that reduce protected-action safeguards
- reject invalid or unreachable archive destination configuration
- reject archive policy enablement when destination_uri is missing
- reject minor AI policy where minor_general_qna_enabled is true and minor_allowed_intent_classes is empty

Invalid updates must not partially apply.

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-008 Personalization Governance Boundaries
- ADR-010 Household Productivity Experience Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract defines global policy configuration boundaries and does not redefine governance authority.

---

## Ownership Boundary Validation

Ownership constraints in this contract:

- global policy remains configuration and orchestration policy, not source-of-record reassignment
- Foundation remains authoritative for room and occupancy truth
- Voice Identity remains authoritative for attribution and confidence outputs
- Coordinator V2 remains orchestration-only and policy-consuming

---

## Terminology Alignment

Canonical terminology in this contract:

- Global Configuration
- Room
- Floor
- Scope
- Capability
- Attribution
- Confidence
- Context

Legacy V1 assumptions that blur global policy with room-truth ownership are prohibited.

---

## Final Principle

Global configuration sets whole-home policy.

Room posture still controls local calm behavior.

This separation is required for deterministic and user-respectful interaction behavior.