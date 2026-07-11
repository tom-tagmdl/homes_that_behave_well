# Room Awareness Contract

## Purpose

Room Awareness defines how the system understands physical space.

It establishes a shared model for:

- rooms (areas)
- environment data
- assets within rooms
- contextual behavior

This contract ensures all integrations interpret rooms the same way.

---

## Core Principle

A room is defined by a Home Assistant area.

The area_id is the single source of truth for room identity.

---

## Room Definition

A room must be represented as:

- area_id (primary key)
- floor_id (resolved from Home Assistant floor registry)
- environment configuration
- optional spatial characteristics

Rooms do not store derived values.

Derived values are computed at runtime.

---

## Floor Relationship

Rooms inherit defaults from the floor they belong to.

Examples:

- thermostat and HVAC zone defaults
- floor speaker/media routing defaults
- floor posture defaults

Room-level configuration may override floor defaults for that room only.

This must be deterministic and explainable.

---

## Environment Model

The room environment is a normalized snapshot.

It is produced by combining:

- configured sensors
- aggregation rules
- current sensor states

The environment model must include:

- temperature
- humidity
- light
- air quality (if available)
- structural conditions (if available)
- confidence level
- last updated timestamp

---

## Environment Rules

The environment model must:

- always return a valid structure
- degrade gracefully when data is missing
- never throw exceptions due to missing data

Missing or invalid data must reduce confidence, not break the system.

---

## Confidence Model

Every room environment must include a confidence level:

- GOOD – all required data present
- PARTIAL – some data missing
- DEGRADED – significant data missing
- STALE – data outdated

Confidence affects:

- evaluation reliability
- advisory quality
- user messaging

---

## Asset Relationship

Assets are always evaluated in the context of a room.

Each asset must:

- be associated with an area_id
- be evaluated against the room environment snapshot

Multiple assets in the same room must:

- use the same environment snapshot
- produce consistent evaluations

---

## Evaluation Context

Evaluation must use:

- a single room environment snapshot per cycle
- all assets in that room evaluated against that snapshot

This ensures:

- deterministic behavior
- no per-entity drift
- consistent results across assets

---

## Spatial Awareness

Rooms may include spatial characteristics such as:

- window direction
- exposure type
- asset placement relative to windows

These factors may influence:

- light exposure
- temperature variation
- environmental risk

Spatial data must:

- be explicitly defined
- never inferred without data

---

## Event Relationship

Room-level changes may generate events, including:

- environment changes
- confidence changes
- configuration updates
- asset movement within the room

Events must:

- be structured
- be timestamped
- be immutable once recorded

---

## Integration Responsibilities

### Asset Intelligence

Must:

- define and store room environment configuration
- generate environment snapshots
- evaluate assets using room context

Must not:

- assume room data beyond defined configuration
- infer missing sensor data without marking confidence

---

### Concierge

Must:

- use room context for interaction
- adapt messaging based on room state and confidence
- reference room-aware capabilities
- honor room posture as the effective local calm/interaction override

Must not:

- define or compute environment models
- override environment data

---

## Room Posture Rules

Room posture is room-scoped and remains authoritative for local interaction suppression.

Rules:

- room posture may suppress info and attention interactions even when global quiet-hours are inactive
- room posture may be temporarily set for scenarios such as naps or early sleep
- room posture affects only the specific room and must not modify other rooms
- urgent handling must follow explicit global urgent bypass policy

---

## AI Usage Rules

AI may use room context to:

- suggest improvements
- recommend sensor additions
- propose environment adjustments

AI must not:

- redefine room structure
- override environment configuration directly
- ignore confidence levels

---

## Failure Handling

If room configuration is incomplete:

- the system must still return a valid environment object
- confidence must be reduced accordingly
- no evaluation should fail completely

The system must never:

- crash due to missing sensors
- assume values that do not exist
- produce undefined results

---

## V2 Governance Consumption

This contract consumes and aligns with:

- ADR-004 Coordinator V2 Governance Boundaries
- ADR-005 Room Vocabulary Governance Boundaries
- ADR-007 Experience Model Governance Boundaries
- ADR-011 Provenance Governance Boundaries
- ADR-012 Occupancy and Presence Governance Boundaries
- ADR-013 Concierge V1 Household-Facing Outcome Preservation Governance
- HACS and Platinum Governance Standard

This contract defines room-awareness boundaries and does not redefine architecture authority.

---

## Ownership Boundary Validation

Ownership boundaries in this contract:

- Foundation remains authoritative for room, area, floor, device, and occupancy truth
- room environment interpretation may consume configured signals but does not move room-truth ownership
- Concierge consumes room-awareness outputs and does not own room truth

---

## Terminology Alignment

Canonical terminology in this contract:

- Room
- Area
- Floor
- Composite Room
- Occupancy
- Presence
- Context
- Confidence
- Scope

Legacy V1 assumptions that blur room truth ownership into orchestration are prohibited.

---

## Final Principle

The room is the shared context of truth.

All environment understanding and asset evaluation must flow through the room model.

If a feature depends on:

- environment conditions
- spatial context
- asset placement

It must use the room awareness model.