# Environment Model

## Purpose

The Environment Model defines the standardized structure for representing room conditions in Asset Intelligence.

This model is consumed by Experience Projection and Household Status Synthesis.

Occupancy is referenced externally and is not owned here.

It provides a normalized, deterministic snapshot of the physical environment used for:

- asset evaluation
- advisory generation
- room awareness
- environmental profiling
- explainable recommendations

---

## Core Principle

The environment is derived, not stored.

It is computed at runtime using:

- configured sensors
- aggregation rules
- Home Assistant entity state
- room configuration
- spatial context

The environment model represents current physical conditions.

It does not interpret, decide, or act.

It remains environmental authority for environmental conditions only.

---

## Canonical Environment Domains

The canonical environment model includes the following domains:

- climate
- light
- air_quality
- particulates
- biological
- safety
- structural
- context
- control_context
- windows
- confidence
- last_updated

All domains should be present in the normalized environment object.

If data is unavailable, values should be null and confidence should be adjusted.

## Contract Alignment

This model aligns with:

- Experience Projection Contract
- Knowledge, Briefing, and Household Status Synthesis Contract
- Occupancy and Presence Contract

---

## Climate Domain

The climate domain represents temperature and moisture conditions.

Fields:

- temperature
- humidity
- dew_point

Expected examples:

- temperature in degrees Fahrenheit
- humidity as percent
- dew_point in degrees Fahrenheit

Rules:

- temperature and humidity are core environmental signals
- dew_point is optional but important for preservation insight
- missing climate values reduce confidence

---

## Light Domain

The light domain represents visible and ultraviolet light exposure.

Fields:

- lux
- uv

Expected examples:

- lux in lx
- uv as index or sensor-provided value

Rules:

- lux may be used for general light exposure
- uv may be used for preservation risk
- missing uv must not break evaluation
- missing light data may reduce confidence depending on asset type

---

## Air Quality Domain

The air quality domain represents volatile and reactive air pollutants.

Fields:

- voc
- formaldehyde
- ozone
- no2

Expected examples:

- voc in ppb
- formaldehyde in ppb
- ozone in ppb
- no2 in ppb

Rules:

- air quality values may influence advisory and long-term preservation guidance
- missing air quality values should not block core climate evaluation
- pollutant values must remain descriptive unless explicit evaluation rules exist

---

## Particulates Domain

The particulates domain represents airborne particulate matter.

Fields:

- pm25
- pm10

Expected examples:

- pm25 in micrograms per cubic meter
- pm10 in micrograms per cubic meter

Rules:

- particulates may influence advisory
- particulate values may matter for sensitive assets, instruments, archives, and artwork
- missing particulate data should reduce advisory confidence, not break evaluation

---

## Biological Domain

The biological domain represents biological risk indicators.

Fields:

- mold_index

Expected examples:

- mold_index as a numeric score or sensor-provided value

Rules:

- biological indicators may influence advisory and risk interpretation
- mold risk should be explainable and bounded
- missing biological data should not prevent environment creation

---

## Safety Domain

The safety domain represents direct hazard signals.

Fields:

- leak

Expected examples:

- leak as boolean, null, or unavailable

Rules:

- leak detection may create urgent risk
- leak signals should be treated differently from advisory-only signals
- unavailable leak data should be represented as null
- missing leak data should not be assumed safe

---

## Structural Domain

The structural domain represents environmental or physical stress signals.

Fields:

- pressure
- vibration

Expected examples:

- pressure in hPa
- vibration as boolean, intensity, or sensor-provided value

Rules:

- structural signals may influence risk for sensitive objects
- vibration may matter for musical instruments, fragile objects, and electronics
- pressure may support environmental interpretation but should not create risk unless rules exist

---

## Context Domain

The context domain represents ambient context not directly tied to asset requirements.

Fields:

- noise

Expected examples:

- noise in dB

Rules:

- context signals help explain room conditions
- context values should usually support advisory, not primary risk
- missing context data should not reduce core environment confidence unless required by a feature

---

## Control Context Domain

The control context domain represents environmental control and comfort indicators.

Fields:

- co2

Expected examples:

- co2 in ppm

Rules:

- control context may support advisory
- co2 may help identify ventilation or occupancy-related conditions
- control context should not mutate environment requirements directly

---

## Windows Domain

The windows domain defines spatial exposure context for the room.

Windows are not sensor data, but part of the normalized environment model.

They represent how external environmental factors can affect the room.

---

### Structure

The windows domain must include:

windows:
  entries:
    - window_id
      direction
      exposure_type (optional)

---

### Window Direction

Direction defines orientation relative to compass:

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
- direction must never be inferred automatically
- direction must remain stable unless configuration changes

---

### Multiple Windows

Rooms may contain multiple windows.

Rules:

- all windows must be listed
- each window is independent
- ordering does not imply priority

---

### Relationship to Environment

Windows exist alongside sensor-derived values in the environment snapshot.

Example:

- lux represents measured light
- windows represent potential exposure sources

Windows are part of environment context, not measured conditions.

---

### Relationship to Exposure Modeling

Windows may be combined with:

- sun position (azimuth and elevation)
- asset placement (near window, facing direction)

To derive:

- directional exposure
- sun alignment
- exposure risk

Derived values must:

- be runtime only
- not be stored in the environment model
- be explainable

---

### Relationship to Asset Placement

Exposure depends on both:

- window orientation
- asset placement

Example:

- asset near southwest window
- sun azimuth aligns with window direction

This increases exposure risk.

---

### Rules

Windows must:

- be explicitly configured
- be included in every environment snapshot
- remain immutable within a single evaluation cycle

Windows must not:

- be treated as sensor data
- be inferred without configuration
- directly generate risk or advisory

All meaning must be derived through evaluation.

---

### Final Principle

Windows define exposure pathways.

They do not define current environmental conditions.

They must always be interpreted with environment data and asset placement.

---

## Normalized Structure

The normalized environment object should follow this conceptual shape:

environment:
  climate:
    temperature
    humidity
    dew_point
  light:
    lux
    uv
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
  windows:
    entries
  confidence
  source_status
  last_updated

---

### Canonical Schema Contract

The normalized environment object must use stable field names and types.

Type constraints:

- climate.temperature: number | null
- climate.humidity: number | null
- climate.dew_point: number | null
- light.lux: number | null
- light.uv: number | null
- air_quality.voc: number | null
- air_quality.formaldehyde: number | null
- air_quality.ozone: number | null
- air_quality.no2: number | null
- particulates.pm25: number | null
- particulates.pm10: number | null
- biological.mold_index: number | null
- safety.leak: boolean | null
- structural.pressure: number | null
- structural.vibration: number | boolean | null
- context.noise: number | null
- control_context.co2: number | null
- windows.entries: list
- confidence: GOOD | PARTIAL | DEGRADED | STALE
- source_status: object
- last_updated: ISO 8601 UTC timestamp (ending with Z)

Rules:

- all required domains must exist in every snapshot
- missing values must be null
- schema shape must not vary across implementations

---

## Required Domains

The normalized environment object must always include:

- climate
- light
- air_quality
- particulates
- biological
- safety
- structural
- context
- control_context
- windows
- confidence
- source_status
- last_updated

Required presence does not mean every value must be populated.

Unavailable values must be represented as null.

---

## Required Core Signals

The following signals are core to the environmental health model:

- temperature
- humidity
- confidence
- last_updated

If temperature or humidity are missing:

- the environment object must still be returned
- confidence must be reduced
- evaluation must degrade gracefully

---

## Optional Signals

The following signals are optional but supported:

- dew_point
- lux
- uv
- voc
- formaldehyde
- ozone
- no2
- pm25
- pm10
- mold_index
- leak
- pressure
- vibration
- noise
- co2
- windows

Optional signals may influence:

- advisory
- asset-specific risk
- long-term profiling
- room suitability guidance

Optional signals must not break environment generation if missing.

---

## Null Handling

If a value is unavailable:

- the field must still exist
- the value must be null
- source_status should explain why the value is unavailable
- confidence should be reduced when appropriate

The system must not fail due to missing data.

---

## Source Status

Each domain or signal may include source status information.

Source status should describe:

- configured source entities
- unavailable sources
- stale sources
- missing configuration
- aggregation method used

Source status exists to support explainability.

It should not be used as a decision engine.

Minimum schema:

source_status:
  configured_sources: number
  unavailable_sources: number
  stale_sources: number
  missing_configuration: string[]
  aggregation:
    <domain>.<signal>: mean | min | max | none

Rules:

- source_status must be present on every snapshot
- counts must be non-negative integers
- aggregation entries must use canonical signal naming

---

## Data Sources

Environment values are derived from:

- configured Home Assistant entities
- aggregation rules
- current sensor states
- room configuration
- explicitly configured spatial data

Each measurable signal may have:

- one source entity
- multiple source entities
- no configured source entity

---

## Aggregation Rules

When multiple sensors exist for a signal, aggregation must be explicit.

Supported aggregation examples:

- mean
- min
- max

Aggregation must be:

- explicitly configured
- deterministic
- consistent across cycles

No signal should use implicit aggregation.

Missing-value handling:

- unavailable values must be excluded from aggregation
- if all values are unavailable, aggregated result must be null
- aggregation order must not affect output

---

## Confidence Model

Every environment object must include a confidence level.

Confidence levels:

GOOD

- required data is present and recent

PARTIAL

- some data is missing or unavailable

DEGRADED

- significant data is missing or unavailable

STALE

- available data is outdated

---

## Confidence Rules

Confidence must:

- be included in every environment object
- influence evaluation and advisory behavior
- never be inferred without data

Confidence must decrease when:

- required sensors are unavailable
- values are unknown
- data is stale
- configuration is incomplete

---

## Evaluation Relationship

The environment model is an input to evaluation.

The environment model must not evaluate risk by itself.

Correct flow:

Environment model produces current conditions.

Evaluation engine compares current conditions to asset requirements.

Coordinator applies runtime behavior and state transitions.

## Occupancy Relationship

Occupancy context is external to the environment model.

The model may reference occupancy-adjacent significance in explanation, but it does not own occupancy or presence truth.

## Household Status Synthesis Relationship

Household status synthesis may consume environment outputs.

The environment model does not own household status synthesis authority.

## Experience Projection Relationship

Experience projection may consume environment outputs for context-aware visibility and briefing surfaces.

The environment model does not own experience projection authority.

---

## Advisory Relationship

The environment model provides context for advisory.

Advisory may use environment data to suggest:

- environmental improvements
- sensor additions
- placement changes
- room suitability concerns

Advisory must not mutate the environment model.

---

## Safety Relationship

Safety signals may require special handling.

Example:

- leak may produce urgent risk behavior

Safety signals must still follow the same model rules:

- explicit source
- normalized value
- source status
- explainable result

---

## Spatial Relationship

Window and exposure data may influence interpretation.

Spatial context may support:

- light exposure advisory
- sun alignment logic
- placement recommendations

Spatial data must be:

- explicitly configured
- deterministic
- separate from raw sensor data

---

## Time Handling

The environment model must include last_updated.

last_updated represents the time the environment snapshot was produced or last refreshed.

All values in a single environment snapshot must be treated as belonging to the same evaluation cycle.

Rules:

- last_updated must be ISO 8601 UTC timestamp (ending with Z)
- all signal timestamps in a snapshot must be normalized to the same cycle reference time
- cycle timestamp must be coordinator-derived

---

## Unit Normalization Rules

Environment values must be normalized to canonical units before evaluation.

Canonical units:

- climate.temperature: degrees Fahrenheit
- climate.humidity: percent (0-100)
- climate.dew_point: degrees Fahrenheit
- light.lux: lx
- air_quality.voc: ppb
- air_quality.formaldehyde: ppb
- air_quality.ozone: ppb
- air_quality.no2: ppb
- particulates.pm25: micrograms per cubic meter
- particulates.pm10: micrograms per cubic meter
- structural.pressure: hPa
- context.noise: dB
- control_context.co2: ppm

Rules:

- conversions must happen before aggregation when source units differ
- conversion logic must be deterministic
- unknown or unsupported units must yield null and reduce confidence

---
## Confidence Calculation Rules

Confidence must be derived using measurable conditions.

---

### GOOD

- all required sensors present
- all data updated within freshness threshold

---

### PARTIAL

- some non-critical sensors missing
- core signals (temperature, humidity) present

---

### DEGRADED

- one or more core signals missing
- or inconsistent data across sensors

---

### STALE

- data older than defined TTL

---

### Data Freshness Threshold (TTL)

Default:

- core signal data older than 5 minutes and up to 15 minutes -> DEGRADED
- core signal data older than 15 minutes -> STALE

Core signals:

- climate.temperature
- climate.humidity

Precedence:

- STALE has highest precedence
- DEGRADED has next precedence
- PARTIAL has next precedence
- GOOD applies only when no higher-precedence condition exists

Deterministic classification rules:

- STALE if any core signal is older than stale TTL
- DEGRADED if any core signal is missing, invalid, or older than degraded TTL
- PARTIAL if core signals are present and fresh, but one or more non-core signals are missing/unavailable
- GOOD only if core signals are present, fresh, and no required configured signal is missing

---

### Rules

- confidence must be recalculated every cycle
- confidence must never be inferred
- missing data reduces confidence, not functionality
- identical inputs must produce identical confidence results
---
## Stability Rules

The environment model must produce stable output.

It must not:

- introduce randomness
- mutate configuration
- evaluate risk
- generate events
- apply debounce logic

Debounce and transition behavior belong outside the environment model.

---

## Failure Handling

The environment model must never fail completely.

If data is invalid, missing, stale, or unavailable:

- return a valid environment object
- set missing values to null
- update source_status
- reduce confidence where appropriate

The system must never:

- crash due to missing sensors
- assume values that do not exist
- produce undefined results

---

## Final Principle

The environment model describes the room.

It does not decide what the room means.

If a feature requires meaning, risk, recommendation, messaging, or action, that feature belongs outside the environment model.