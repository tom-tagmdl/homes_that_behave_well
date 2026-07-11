# Concierge Scope Contract

## Purpose

This contract defines the configuration and execution scope model for Concierge.

It formalizes three scopes:

- concierge-wide
- floor-wide
- room-wide

The goal is deterministic behavior with clear inheritance and override rules.

---

## Core Principle

Scope determines where a setting applies.

Priority determines which setting is effective.

For overlapping settings, the most specific valid scope wins.

---

## Scope Definitions

### Concierge-Wide

Applies to the entire home.

Examples:

- global context providers (weather, news, calendar)
- global quiet-hours policy
- capability enablement (AI, TTS, Music Assistant, Asset Intelligence connection)
- safety policy defaults

### Floor-Wide

Applies to all rooms on a floor.

Examples:

- thermostat/HVAC zone bindings
- floor media routing defaults
- floor speaker groups
- floor presence posture defaults

### Room-Wide

Applies only to one Home Assistant area.

Examples:

- room posture (day, night, sleep, away, nap)
- room speaker and voice assistant binding
- room device_groups and asset_groups with user-defined display names ("what do you call this")
- room persona and voice overrides

Grouping rules:

- room grouping vocabulary is configuration-authored and extensible
- Concierge must resolve follow-up phrases against configured group display names and vocabulary aliases
- Concierge must not depend on a hardcoded closed set of group names
- effective group membership must come from persisted setup selections; no runtime regrouping/inference

---

## Effective Resolution Order

For settings that exist at multiple scopes:

1. room-wide override
2. floor-wide default
3. concierge-wide default

If no valid value exists, Concierge must fail safely and explain what is missing.

Context projection precedence:

- source availability remains concierge-wide
- projection ordering for weather and news may be room-wide
- effective source order for a room is resolved as:
1. room projection priority (if valid)
2. concierge-wide source order

Room projection priority must only reference concierge-wide available sources.

---

## Communication Suppression Rules

### Quiet-Hours Policy

Quiet-hours is concierge-wide policy.

It defines default suppression windows and urgent bypass behavior.

### Room Posture Priority

Room posture remains room-wide and may increase suppression at any time.

This enables room-local behavior such as naps or early sleep without changing whole-home quiet-hours.

Rules:

- room posture may suppress info and attention interactions for that room
- room posture does not change concierge-wide quiet-hours for other rooms
- urgent handling must follow explicit urgent bypass policy

---

## Climate and Thermostat Boundaries

Thermostat and HVAC control is floor-wide by default.

Rationale:

- many homes have one thermostat per floor or zone
- room actions often map to shared floor equipment

Rules:

- thermostat targets should be configured at floor scope
- room-specific climate entities may override floor bindings when explicitly configured
- concierge-wide thermostat configuration is allowed only for true whole-home systems

---

## Music Assistant Scope Behavior

Music Assistant enablement is concierge-wide capability.

Operational routing should be floor-wide or room-wide.

Examples:

- concierge-wide: provider enabled, global safety policy for duck/pause/resume
- floor-wide: preferred group or default playback zone
- room-wide: preferred endpoint and room exceptions

Rules:

- Music Assistant must be treated as a capability provider, not only media_player control
- playback and TTS interaction must remain deterministic and explainable

---

## UI Model Requirement

Concierge UI must expose setup in three sections:

1. concierge-wide settings
2. floor-wide settings
3. room cards

Room pages must show inherited defaults and room overrides so effective behavior is visible.

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-006 Capability Projection Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract defines scope boundaries only.

This contract does not transfer governance authority to Coordinator V2.

---

## Ownership Boundary Validation

Scope policy boundaries in this contract preserve:

- Foundation ownership of room, area, and occupancy truth
- Voice Identity ownership of attribution and confidence
- Coordinator V2 orchestration-only role under governed scope rules

---

## Terminology Alignment

Canonical scope terminology in this contract:

- Room
- Area
- Floor
- Composite Room
- Context
- Scope

Legacy V1 terminology that implied hidden runtime inference is out of scope.

---

## Final Principle

Concierge must behave as configured, not inferred.

Scope and precedence must be explicit, deterministic, and explainable.
