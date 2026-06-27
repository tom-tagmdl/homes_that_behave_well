# Room Model

## Purpose

The Room Model defines how physical spaces are represented and configured within the system.

A room is the central context that connects:

- environment sensing
- asset placement
- evaluation
- advisory
- interaction

---

## Core Principle

The room defines context.

Everything that happens in the system happens within a room.

---

## Room Identity

A room is defined by:

- area_id

Rules:

- area_id must match Home Assistant area
- area_id is the single source of truth for room identity
- no alternate identifiers may be used

---

## Room Layers

The room consists of three layers:

### 1. Configuration (stored)
### 2. Runtime Environment (derived)
### 3. Events and History

---

# 1. ROOM CONFIGURATION (STORED)

---

## Environment Configuration

Defines how the environment is constructed.

Fields include:

- sensor mappings by domain
- aggregation rules per signal

Example structure:

environment_config:
  climate:
    temperature:
      source_entities[]
      aggregation
    humidity:
      source_entities[]
      aggregation
    dew_point:
      source_entities[]
      aggregation

  light:
    lux:
      source_entities[]
      aggregation
    uv:
      source_entities[]
      aggregation

  air_quality:
    voc
    formaldehyde
    ozone
    no2

  particulates:
    pm25
    pm10

  biological:
    mold_index

  safety:
    leak

  structural:
    pressure
    vibration

  context:
    noise

  control_context:
    co2

---

## Configuration Schema Contract

Room configuration must use canonical structure and stable naming.

Required fields:

- area_id: string
- environment_config: object

Optional fields:

- windows: list
- room_alert_config: object

Rules:

- area_id must be non-empty and match Home Assistant area_id
- environment_config signal keys must use canonical names from environment model
- unknown signal keys must be rejected by validation
- configuration updates must follow service call -> validation -> store write

---

## Aggregation Rules

Each signal must define an aggregation method:

- mean
- min
- max

Rules:

- aggregation must be explicit
- no default implicit aggregation
- must be consistent across cycles

---

## Windows (Spatial Configuration)

Fields:

- windows[]

Each window may include:

- direction
- exposure_type

Rules:

- window direction must be explicitly defined
- no inferred spatial data
- windows influence exposure analysis

---

## Room Alert Configuration

Optional configuration for room-level behavior.

Fields may include:

- degraded monitoring thresholds
- alert suppression rules

Rules:

- must not override system-wide messaging patterns
- must remain bounded and explainable

---

# 2. RUNTIME ENVIRONMENT (DERIVED)

---
## Windows and Spatial Context

The room environment must include structured window data as part of the environment context.

Windows are not sensors, but they directly influence environmental interpretation and exposure.

---

### Windows Structure

The environment snapshot must include:

windows:
  entries:
    - window_id
      direction
      exposure_type (optional)

---

### Window Direction

Window direction defines orientation relative to the compass:

- north
- northeast
- east
- southeast
- south
- southwest
- west
- northwest

Rules:

- direction must be explicitly configured
- direction must not be inferred automatically
- direction must be used in exposure calculations

---

### Multiple Windows

Rooms may contain multiple windows.

Rules:

- all windows must be listed
- order does not imply importance
- exposure logic may evaluate each window independently

---

### Relationship to Environment

Windows must appear alongside environment data in the same snapshot.

Windows are part of:

- spatial context
- exposure modeling
- advisory generation

---

### Relationship to Exposure Analysis

Window data may be combined with:

- sun position (azimuth and elevation)
- asset placement
- room orientation

To derive:

- directional exposure
- light amplification
- exposure risk

Derived values are runtime only and must not be persisted.

---

### Relationship to Asset Placement

Exposure depends on both:

- room window orientation
- asset placement within the room

Example:

- asset near southwest window
- sun azimuth matches window direction

This may increase light exposure risk.

---

### Rules

Windows must:

- be explicitly configured
- be included in environment snapshot
- be used in spatial and exposure modeling

Windows must not:

- be inferred without configuration
- be treated as sensor data
- directly generate risk without evaluation logic

---

### Final Principle

Windows define exposure potential.

They do not represent conditions.

They must always be combined with environment data and asset placement to derive meaning.

## Environment Snapshot

The room produces a single environment snapshot per evaluation cycle.

This snapshot includes:

- all environment domains
- confidence level
- source status
- last updated time

Rules:

- exactly one snapshot per room per cycle
- shared across all assets in the room
- must be deterministic

Snapshot contract:

- snapshot must include all required environment domains
- confidence must use enum: GOOD | PARTIAL | DEGRADED | STALE
- last_updated must be ISO 8601 UTC timestamp (ending with Z)
- source_status must be present with stable schema

---

## Confidence

Confidence reflects:

- data completeness
- sensor availability
- data freshness

Values:

- GOOD
- PARTIAL
- DEGRADED
- STALE

Rules:

- must be included in every snapshot
- must influence evaluation and advisory behavior
- must follow precedence: STALE > DEGRADED > PARTIAL > GOOD
- identical inputs must produce identical confidence results

---

## Source Status

Tracks:

- available sensors
- unavailable sensors
- stale sensors
- aggregation applied

Rules:

- used for explainability
- must not drive decision logic directly

Minimum schema:

source_status:
  configured_sources: number
  unavailable_sources: number
  stale_sources: number
  missing_configuration: string[]
  aggregation:
    <domain>.<signal>: mean | min | max | none

Rules:

- source_status must be present for every room snapshot
- counts must be non-negative integers
- aggregation keys must use canonical signal naming

---

# 3. ASSET RELATIONSHIP

---

## Room to Asset Mapping

Each asset must:

- reference area_id
- inherit room environment context

Rules:

- assets do not define environment
- assets do not override room context
- assets are evaluated using room snapshot

---

## Shared Evaluation Context

For each evaluation cycle:

- one room snapshot is created
- all assets in the room use that snapshot

This ensures:

- consistency
- determinism
- no drift between assets

Deterministic evaluation order:

- assets in a room must be evaluated in lexical order by asset_id
- event generation must follow evaluation order for equal-priority outputs

---

# 4. SPATIAL CONTEXT

---

## Derived Spatial Data

The system may derive spatial context using:

- window direction
- sun position
- asset placement

Derived outputs may include:

- directional light exposure
- azimuth alignment
- elevation impact

Rules:

- derived values must not be persisted
- derived values must be explainable
- derived values must not alter configuration

---

# 5. EVENT MODEL

---

## Room-Level Events

Room events may include:

- environment updates
- confidence changes
- configuration changes
- spatial updates

Required event linkage:

- cycle_id
- sequence_in_cycle
- correlation_id (when generated from service flow)

---

## Event Rules

Events must be:

- timestamped
- immutable
- structured

Events must not:

- be modified once written
- be duplicated

Ordering rules:

- primary: timestamp ascending
- tie-break: cycle_id, then sequence_in_cycle, then event_id lexical

---

# 6. RELATIONSHIP TO OTHER MODELS

---

## Room and Environment Model

The room produces the environment model.

The environment model must:

- reflect configured sensors
- be computed per room
- remain independent of evaluation

---

## Room and Asset Model

The room provides context for assets.

Assets depend on:

- room environment
- room configuration
- spatial context

---

## Room and Advisory

The room may generate advisory at the room level.

Examples:

- unsuitable room conditions for asset types
- missing sensors
- environmental instability

Rules:

- advisory must not mutate room configuration
- advisory must remain optional
- room-level advisory must be produced by advisory/evaluation outputs, not by UI logic

---

## Room and AI

AI may:

- suggest sensor additions
- recommend configuration improvements
- propose spatial adjustments

AI must not:

- modify room configuration directly
- bypass validation
- invent spatial data

---

# 7. FAILURE HANDLING

If room configuration is incomplete:

- environment must still be generated
- confidence must be reduced
- evaluation must continue

The system must never:

- fail due to missing sensors
- assume values not provided
- produce undefined output

---

# FINAL PRINCIPLE

The room defines context.

The environment describes conditions.

Assets define requirements.

Evaluation determines risk.

All system behavior must flow through the room.