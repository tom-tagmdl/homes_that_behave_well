# System Flow

## Purpose

This document describes how data and decisions move through the system during runtime.

It defines the flow from:

- sensor input
- environmental understanding
- asset evaluation
- decision making
- user-facing outcomes

---

## Core Principle

All system behavior follows a consistent, deterministic flow.

Each step transforms data in a controlled way.

No step may be skipped or merged.

---

## High-Level Flow

The system executes the following flow for each cycle:

Sensor Data → Environment Model → Exposure Model → Evaluation Engine → Coordinator → Store → Entities → Concierge

---

## Step 1: Sensor Data (Input)

Source:

- Home Assistant entities
- room configuration (sensor mappings)

Actions:

- read current state of configured sensors
- detect unavailable or stale values

Output:

- raw sensor values

Rules:

- no interpretation
- no transformation
- no persistence

---

## Step 2: Environment Model (Normalization)

Input:

- raw sensor data
- room configuration
- windows configuration

Actions:

- normalize all sensor values
- aggregate multiple sensors per signal
- construct full environment snapshot
- compute confidence level
- include windows domain

Output:

- environment snapshot

Rules:

- must always produce valid structure
- must not evaluate risk
- must not mutate state

---

## Step 3: Exposure Model (Spatial Interpretation)

Input:

- environment snapshot
- windows (room)
- asset placement
- external context (sun position)

Actions:

- determine directional alignment
- compute exposure pathways
- derive exposure-related values

Output:

- exposure projection

Rules:

- must be deterministic
- must not be stored
- must not evaluate final risk

---

## Step 4: Evaluation Engine (Decision)

Input:

- environment snapshot
- exposure projection
- asset requirements

Actions:

- compare current conditions to requirements
- determine risk state
- generate reasons for the result

Output:

- evaluation result:
  - risk state
  - candidate state
  - reasons

Rules:

- must be pure logic
- must not persist data
- must not access Home Assistant directly

---

## Step 5: Coordinator (Runtime Orchestration)

Input:

- evaluation results (all assets)
- prior system state

Actions:

- apply debounce rules
- determine state transitions
- generate events
- build runtime projections
- maintain in-memory state

Output:

- updated projections
- events

Rules:

- only coordinator may create events
- only coordinator may apply state transitions
- must not redefine evaluation logic

---

## Step 6: Store (Persistence)

Input:

- validated state transitions
- configuration updates
- service calls

Actions:

- persist asset state
- persist configuration
- record audit history

Output:

- stored data

Rules:

- must not evaluate logic
- must enforce schema
- must not accept partial writes

---

## Step 7: Entities (Projection)

Input:

- coordinator projections

Actions:

- expose current system state to Home Assistant
- provide lightweight views of data

Output:

- entity states and attributes

Rules:

- must be read-only
- must not compute logic
- must not store data

---

## Step 8: Concierge (Interaction)

Input:

- entity state
- system events
- user input

Actions:

- determine appropriate communication
- orchestrate service calls
- present information to user

Output:

- voice output
- UI responses
- guided actions

Rules:

- must not own data
- must not perform evaluation
- must not bypass service boundaries

---

## Service Flow

All state changes follow this flow:

User or system action → Service Call → Validation → Store Write → Coordinator Refresh

Rules:

- no direct store mutation
- validation required for all writes
- coordinator must re-evaluate after change

---

## Event Flow

Events are generated during coordinator processing.

Flow:

State change → Coordinator → Event creation → Store → Entities → Concierge

Rules:

- events must be immutable
- events must be timestamped
- events must be bounded

---

## Advisory Flow

Advisory is generated alongside evaluation.

Flow:

Environment + Exposure → Evaluation → Advisory → Concierge

Rules:

- advisory must not mutate state
- advisory must be explainable
- advisory must be optional

---

## AI-Assisted Flow

AI operates within controlled boundaries.

Flow:

System context → AI recommendation → Validation → Service Call → Store → Coordinator

Rules:

- AI must not write directly to system
- all AI output must be validated
- all changes must go through services

---

## Failure Handling

If any step encounters missing or invalid data:

- environment model reduces confidence
- exposure model ignores missing context
- evaluation continues with available inputs
- coordinator maintains stable state

The system must never:

- crash due to missing data
- produce undefined outputs
- partially apply changes

---

## Determinism Guarantee

For identical inputs:

- environment must be identical
- exposure must be identical
- evaluation must be identical
- outputs must be identical

---

## Final Principle

The system flows in one direction:

Input → Understanding → Interpretation → Decision → Action → Communication

No step may reverse, bypass, or duplicate another.

The flow must remain:

- deterministic
- explainable
- stable
