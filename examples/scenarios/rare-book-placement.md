# Scenario: Rare Book Placement Suitability

## Purpose

This scenario demonstrates how the system determines whether a rare book can safely be placed in a room.

It shows:

- evaluation of room suitability
- use of historical environment behavior
- start/stop measurement analysis
- advisory-driven placement decisions
- explainable recommendations

---

## Scenario Overview

A rare book is being considered for placement in a library.

The system must determine:

- whether the room maintains stable environmental conditions
- whether fluctuations exceed acceptable tolerance
- whether the room is suitable for long-term preservation

---

## Asset Definition

Asset:

- name: Rare First Edition Book
- asset_type: archival_material

Placement (proposed):

- area_id: library
- near_window: false

Environment Requirements:

- temperature: 65 to 70 degrees Fahrenheit
- humidity: 45 to 50 percent
- light exposure: very low
- uv exposure: minimal

Sensitivity:

- high sensitivity to humidity swings
- high sensitivity to light exposure

---

## Room Configuration

Room:

- area_id: library

Sensors:

- temperature sensor
- humidity sensor
- light sensor

Historical Data Available:

- temperature trends
- humidity trends
- light exposure history

---

## Step 1: Current Environment Snapshot

Environment Model produces:

- temperature: 68
- humidity: 47
- lux: 50
- confidence: GOOD

Interpretation:

- current conditions are within acceptable range

---

## Step 2: Historical Behavior Analysis

System evaluates historical patterns using event history.

Collected Data:

- humidity frequently cycles between 42 and 58 percent
- temperature fluctuates between 64 and 74 degrees
- light exposure stable

---

## Step 3: Start and Stop Event Analysis

The system analyzes when conditions:

- enter acceptable range (start)
- exit acceptable range (stop)

Example:

Humidity:

- start (within range): 45 percent
- stop (exceeds range): 55 percent
- repeated oscillations observed

Temperature:

- start: 66 degrees
- stop: 72 degrees
- periodic over-range events

---

## Step 4: Stability Evaluation

Evaluation Engine determines:

- frequency of excursions outside acceptable range
- duration of unstable periods
- rate of environmental change

Result:

- frequent start/stop cycling detected
- environment not stable within required bounds

---

## Step 5: Suitability Evaluation

System evaluates room suitability for asset placement.

Criteria:

- sustained compliance with requirements
- low volatility in environment
- minimal threshold crossings

Result:

- room suitability: CONDITIONAL or NOT RECOMMENDED

Reasons:

- repeated humidity excursions
- temperature instability over time

---

## Step 6: Advisory

Advisory System generates:

Primary Advisory:

- "The library environment does not consistently maintain conditions required for this rare book."

Supporting Advisory:

- "Humidity fluctuates outside the recommended range."
- "Temperature exceeds acceptable limits periodically."
- "The room may not be suitable for long-term placement."

---

## Step 7: Recommended Actions

System provides options:

- add humidity control (humidifier or dehumidifier)
- improve HVAC stability
- relocate asset to a more stable room
- monitor environment before placing asset

---

## Step 8: User Interaction

User requests:

- "Can this book be placed in the library?"

Concierge response:

- summarizes suitability
- explains risk factors
- presents recommendations

Example:

"The current environment is stable at the moment, but historical data shows frequent humidity and temperature fluctuations. This room may not be suitable for long-term preservation without additional controls."

---

## Step 9: Decision Support

System allows:

- proceed with placement (with risk acknowledgment)
- delay placement
- implement improvements first

No automatic placement occurs.

---

## Step 10: Optional Monitoring After Placement

If asset is placed:

- system begins real-time monitoring
- alert thresholds apply
- escalation occurs if conditions degrade

---

## Failure Example

If historical data is insufficient:

- system cannot evaluate stability
- advisory generated:

"Insufficient environmental history to determine room suitability. Continue monitoring before placing this asset."

---

## Key Principles Demonstrated

- environment suitability is based on historical behavior, not snapshots
- start/stop thresholds define stability boundaries
- evaluation is deterministic and explainable
- advisory provides guidance without enforcing action
- system supports decision-making, not automation of placement
- missing data reduces confidence rather than causing failure

---

## Architectural Alignment

Asset Intelligence:

- evaluates suitability
- analyzes historical patterns
- produces explainable recommendations

Environment Model:

- provides current state

Event History:

- provides start/stop and fluctuation data

Concierge:

- explains suitability to the user
- supports informed decision-making

---

## Final Outcome

The system:

- evaluates whether the room maintains stable conditions over time
- identifies instability through start/stop threshold analysis
- provides clear reasoning for placement decisions
- recommends improvements or alternatives

This results in:

- informed asset placement decisions
- reduced risk to sensitive materials
- a calm, predictable, and explainable system
