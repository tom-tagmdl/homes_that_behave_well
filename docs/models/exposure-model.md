# Exposure Model

## Purpose

The Exposure Model defines how environmental conditions, spatial context, and asset placement combine to produce exposure risk.

Exposure is a runtime-derived model.

It is not stored in the system of record.

---

## Core Principle

Exposure explains how the environment affects an asset.

The environment provides conditions.

Spatial context provides pathways.

Exposure combines them.

---

## Model Type

Exposure is a runtime projection.

It depends on:

- room environment snapshot
- window configuration
- asset placement
- external context (such as sun position)

Exposure must be:

- deterministic
- explainable
- reproducible

---

## Input Components

### 1. Environment Data

From the environment model:

- lux
- uv
- temperature
- humidity
- other domain signals

This represents current conditions.

---

### 2. Windows

From room configuration:

- window direction
- exposure type

Windows define possible environmental entry points.

---

### 3. Asset Placement

From asset model:

- near_window
- facing_direction
- exposure_zone

Placement defines how exposed the asset is.

---

### 4. External Context

External context may include:

- sun azimuth
- sun elevation
- time of day
- seasonal patterns

This provides dynamic environmental alignment.

---

## Derived Fields

The exposure model may produce:

- exposure_risk_level
- directional_match (true or false)
- azimuth
- elevation
- effective_lux
- effective_uv

---

## Directional Match

Directional match determines whether a window is aligned with the sun.

Example logic:

- window facing southwest
- sun azimuth within matching range

Result:

- directional_match = true

Rules:

- must be deterministic
- must be explainable
- must use explicit directional mapping

---

## Exposure Risk

Exposure risk indicates how conditions affect the asset.

Typical values:

- NONE
- LOW
- MODERATE
- HIGH

Rules:

- must be derived from environment + placement
- must not be stored
- must be recalculated every cycle

---

## Effective Exposure

Effective exposure combines:

- measured environment values
- spatial alignment
- placement proximity

Example:

- measured lux = 200
- asset near aligned window
- effective exposure > 200

Rules:

- must be explainable
- must not introduce arbitrary scaling
- must be consistent across identical inputs

---

## Relationship to Evaluation

Exposure does not determine risk directly.

Evaluation determines risk.

Flow:

Environment + Exposure -> Evaluation -> Risk state

Exposure provides:

- additional context
- supporting signals

---

## Relationship to Advisory

Exposure may drive advisory.

Examples:

- reposition asset
- reduce light exposure
- adjust window treatments

Advisory must:

- explain exposure contribution
- not modify exposure directly

---

## Persistence Rules

Exposure must not be stored.

Exposure must:

- be derived at runtime
- be recalculated each cycle
- be included only in projections

---
## Deterministic Exposure Computation Rules

Exposure must be computed using explicit, reproducible logic.

---

### Directional Matching

Directional match must be determined by comparing:

- window direction
- external azimuth

Allowed tolerance:

- ±22.5 degrees from window direction

Example:

- window: southwest (225°)
- azimuth: 210° → match = true
- azimuth: 260° → match = false

### Angular Difference Calculation

Directional matching must use shortest circular distance.

---

### Formula

difference = min(
  abs(azimuth - window_direction),
  360 - abs(azimuth - window_direction)
)

---

### Rule

- matching threshold: ±22.5°
- must consider circular wrap-around

---

### Example

- window: north (0°)
- azimuth: 350°
→ difference = 10° → match = true
---

### Multi-Window Handling

If multiple windows exist:

- evaluate each window independently
- select the highest exposure impact

Rules:

- exposure impact must not be averaged across windows
- the maximum contributing window defines exposure

---
### Multi-Window Tie-Break Rule

If two or more windows produce equal exposure impact:

- select window with lowest window_id (lexical order)

---

### Example

window_1 vs window_2 → choose window_1
---

### Effective Lux Calculation

Effective lux must consider:

- measured lux
- directional match
- proximity (near_window)

Example rules:

- if directional_match AND near_window:
  effective_lux = measured_lux × factor (from deterministic factor table)

- if no alignment:
  effective_lux = measured_lux

---

### Effective UV Handling

UV exposure must follow:

- UV present + directional alignment → elevated exposure risk
- UV absent → no UV-based exposure impact

---

### Determinism Rule

Given identical inputs:

- exposure output must be identical

No randomness is allowed.

---
### Missing Data Default Rules

If data is missing:

- near_window:
  default = false

- facing_direction:
  default = null (no directional influence)

- azimuth:
  default = null and directional_match = false

- exposure_zone:
  default = unknown

- elevation:
  default = null

---

### Rules

- missing data must not produce inconsistent output
- defaults must be applied consistently

Deterministic defaults:

- if azimuth is null, directional_match must be false
- if no windows are configured, directional_match must be false
- if measured_lux is null, effective_lux must be null
- if measured_uv is null, effective_uv must be null
---

## Exposure Output Schema

The exposure model must return a consistent object.

---

### Structure

exposure:
  directional_match: boolean
  exposure_risk_level: NONE | LOW | MODERATE | HIGH
  matched_window_id: string or null
  applied_factor: number
  azimuth: number or null
  elevation: number or null
  effective_lux: number or null
  effective_uv: number or null

---

### Rules

- all fields must exist
- missing values must be null
- schema must not vary across implementations
- azimuth must be normalized to [0, 360)
- elevation must be clamped to [-90, 90] when provided

Numeric precision rules:

- effective_lux and effective_uv must be rounded to 2 decimal places
- applied_factor must be rounded to 2 decimal places
- angular computations must use shortest circular distance before threshold comparison

Output semantics:

- matched_window_id is the window that determined final exposure impact
- applied_factor must match the factor table for the chosen window/exposure zone

---

## AI Usage

AI may assist with:

- explaining exposure impact
- suggesting mitigation strategies

AI must not:

- modify exposure calculations
- override deterministic logic

---

## Failure Handling

If spatial or external context is missing:

- exposure must still be computed
- missing factors must be ignored
- results must remain valid

The system must never:

- fail due to missing sun data
- assume invalid spatial alignment
---
### Effective Lux Factor Rules

Effective lux must use fixed multipliers.

---

### Factor Table (Deterministic)

If directional_match AND near_window:

- exposure_zone: direct
  factor: 2.0

- exposure_zone: adjacent
  factor: 1.5

- exposure_zone: indirect or unknown
  factor: 1.2

If no directional match:

- factor: 1.0

Exposure zone normalization:

- allowed values: direct, adjacent, indirect, unknown
- matching must be case-insensitive
- unrecognized values must map to unknown

---

### Rules

- factors must be fixed, not ranges
- no runtime variation allowed
- same input → same output

---

## Final Principle

Exposure describes how conditions reach the asset.

It does not define the conditions.

It must always remain:

- derived
- deterministic
- explainable