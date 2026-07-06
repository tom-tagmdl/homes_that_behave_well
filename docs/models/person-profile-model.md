# Person Profile Model

## Purpose

The Person Profile Model defines how Concierge stores and resolves person-aware interaction preferences.

This model is for interaction behavior, not authentication.

It may include action authorization grants defined by policy (for example, alarm control permissions), but it does not define the authentication mechanism itself.

---

## Core Principle

A person profile describes how someone prefers to interact with the home.

It does not change what is true.

It changes how Concierge communicates and confirms.

---

## Person Identity

Each profile is anchored to a Home Assistant person.

Required field:

- person_id

Rules:

- person_id must map to a valid Home Assistant person entity
- profile must remain valid if attribution confidence is low by falling back to neutral

---

## Profile Structure

Example structure:

person_profile:
  person_id: person.david
  display_name: David
  enabled: true
  identity_devices:
    ble_proximity_devices:
      - device_tracker.david_iphone
      - device_tracker.david_watch
    voice_profiles:
      - voice_profile.person_david_main
  supporting_presence_devices:
    - binary_sensor.family_room_presence
    - binary_sensor.office_presence
  interaction_style:
    verbosity: minimal
    tone: direct
    follow_up_mode: low
    confirmation_mode: brief
  channel_preferences:
    quiet_posture_voice: suppress
    default_channel: mixed
  security_authorizations:
    alarm_control:
      allowed: true
      allowed_actions:
        - arm_away
        - arm_home
      disarm_allowed: false
      requires_voice_attribution: true
      requires_step_up_for_disarm: true
      preferred_step_up_channel: mobile_app
      mobile_target_devices:
        - mobile_app_david_phone
  interaction_targets:
    mobile_app_targets:
      - target_id: mobile_app_david_phone
        device_class: phone
        enabled: true
      - target_id: mobile_app_david_ipad
        device_class: tablet
        enabled: true
    preferred_read_later_target: mobile_app_david_ipad
  household_classification:
    is_minor: false
    guardian_controls_required: false
  minor_interaction_policy:
    ai_access_mode: restricted
    allow_general_qna: false
    allowed_intent_classes:
      - room_context_info
      - household_help
    enforce_content_filter_level: strict
  learning:
    adaptive_updates_enabled: true
    last_style_update: 2026-07-01T09:00:00Z
  metadata:
    created_at: 2026-07-01T08:00:00Z
    updated_at: 2026-07-01T09:00:00Z

---

## Required Fields

- person_id
- enabled
- identity_devices
- interaction_style
- metadata.created_at
- metadata.updated_at

When a person has protected-action grants, `security_authorizations` must be present and valid.

---

## Interaction Style Fields

Allowed values:

- verbosity: minimal | balanced | detailed
- tone: direct | conversational
- follow_up_mode: low | balanced | proactive
- confirmation_mode: silent | brief | explained

---

## Effective Style Resolution

Effective style is resolved using layered precedence:

1. session override
2. person profile
3. household default
4. neutral fallback

Room posture may further suppress or reroute delivery modality.

---

## Attribution Snapshot Model

Example runtime snapshot:

identity_snapshot:
  person_id: person.tom
  confidence: 0.86
  attribution_factors:
    - presence_match
    - room_proximity
    - conversation_owner_match
  effective_style:
    verbosity: detailed
    tone: conversational
    follow_up_mode: balanced
    confirmation_mode: explained
  expires_at: 2026-07-01T09:15:00Z

---

## Consent Model

Enrollment and personalization require explicit consent state.

Example:

consent:
  personalization_enabled: true
  device_binding_enabled: true
  voice_training_enabled: true
  granted_at: 2026-07-01T08:30:00Z
  revoked_at: null

Rules:

- if consent is revoked, identity personalization must be disabled
- revocation must be applied immediately

---

## Learning Record Model

Learning records capture reversible adjustments.

Example:

style_adjustment:
  person_id: person.david
  trigger: repeated_feedback_be_briefer
  prior_style:
    verbosity: balanced
  new_style:
    verbosity: minimal
  confidence_change: +0.08
  created_at: 2026-07-01T09:30:00Z
  reversible: true

device_binding_adjustment:
  person_id: person.david
  trigger: explicit_device_link
  linked_device: device_tracker.david_iphone
  linked_device_type: ble_proximity
  created_at: 2026-07-01T09:35:00Z
  reversible: true

---

## Validation Rules

- unknown style values must be rejected
- disabled profiles must not be applied
- stale snapshots must not persist beyond freshness policy
- all profile updates must be auditable
- protected-action grants must be explicit, auditable, and revocable
- disarm permissions must require explicit grant and step-up policy compliance
- interaction target IDs must map to valid Home Assistant mobile notify targets
- disabled interaction targets must not be exposed as selectable delivery options
- person-scoped delivery options must be filtered to enabled targets in that person's profile
- minor classification must be explicitly configured and must never be inferred automatically
- when is_minor is true, guardian_controls_required should default to true unless explicitly overridden by policy
- when is_minor is true, minor_interaction_policy must be present and valid
- when allow_general_qna is false, general open-ended Q&A intents must be blocked for that profile

Capability boundary rules:

- person profile storage is durable across temporary capability disablement
- when AI capability is disabled, AI-dependent person policy behavior must degrade to safe defaults at execution time
- when TTS capability is disabled, mobile voice endpoint behavior must be suppressed at execution time
- voice enrollment data may remain stored while enrollment actions are disabled by capability gates
- capability disablement must gate behavior, not infer or fabricate replacement profile data

---

## Final Principle

The person profile model should make interaction feel personalized, respectful, and predictable while staying bounded by room context and system policy.
