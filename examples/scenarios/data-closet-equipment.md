# Scenario: Data Closet Equipment Protection and Automated Response

## Purpose

This scenario demonstrates how the system monitors and protects critical computer equipment in a data closet.

It shows:

- environmental monitoring
- deterministic evaluation
- exposure not required (controlled space)
- entity-driven automation
- escalation workflow
- urgent human intervention

---

## Scenario Overview

A data closet contains:

- network infrastructure
- server equipment
- storage systems

This equipment requires:

- stable temperature
- controlled humidity
- proper airflow

The room is actively managed through:

- fans
- ventilation
- humidifier

---

## Asset Definition

Asset:

- name: Data Closet Equipment
- asset_type: electronics

Placement:

- area_id: data_closet
- near_window: false

Environment Requirements:

- temperature: 65 to 75 degrees Fahrenheit
- humidity: 40 to 55 percent

Debounce Policy:

- red_transition_seconds: 120
- recovery_seconds: 300

---

## Room Configuration

Room:

- area_id: data_closet

Sensors:

- temperature sensor
- humidity sensor

Control Devices:

- ventilation fan
- circulation fan
- humidifier

---

## Step 1: Environment Snapshot

Environment Model produces:

- temperature: 82
- humidity: 30
- confidence: GOOD

Interpretation:

- temperature above safe range
- humidity below safe range

---

## Step 2: Evaluation

Evaluation Engine compares:

- environment values
- asset requirements

Result:

- risk_state: RED

Reasons:

- temperature exceeds safe range
- humidity below minimum threshold

---

## Step 3: Coordinator Processing

Coordinator:

- confirms sustained out-of-range condition
- applies debounce rules
- transitions state to RED

Generated Event:

- type: risk_state_changed
- asset: data_closet_equipment
- from: AMBER
- to: RED
- timestamp: recorded

---

## Step 4: Entity State (Automation Trigger)

The asset entity exposes:

- state: RED
- attributes:
  - temperature_out_of_range: true
  - humidity_out_of_range: true

This entity becomes the trigger for automation.

---

## Step 5: Automation Layer (Home Assistant)

Automation listens to asset state:

Trigger:

- asset state changes to RED

Condition:

- temperature above threshold OR
- humidity below threshold

Action:

1. Turn on ventilation fan
2. Turn on circulation fan
3. Turn on humidifier

---

## Step 6: System Response

Control systems activate:

- airflow increases
- humidity begins recovering
- temperature begins decreasing

System waits for recovery period.

---

## Step 7: Re-evaluation

Coordinator re-runs evaluation:

Environment:

- temperature: 78 (still above range)
- humidity: 35 (still below range)

Result:

- remains RED

---

## Step 8: Escalation Condition

System detects:

- prolonged RED state
- recovery actions not effective

Escalation Criteria:

- RED state persists beyond defined duration
- environment not returning toward acceptable range

---

## Step 9: Urgent Messaging

Concierge is triggered via event.

Message Type:

- URGENT

Message:

"Data closet temperature and humidity are outside safe limits and automated correction is not resolving the issue. Immediate attention is required."

---

## Step 10: Notification Delivery

Concierge determines:

- appropriate delivery method
- appropriate person or device

Actions:

- sends urgent notification
- optionally triggers voice message
- directs alert to responsible person

---

## Step 11: Human Intervention

User inspects:

- ventilation system
- airflow obstruction
- HVAC supply
- humidifier function

User resolves underlying issue.

---

## Step 12: Recovery

Environment stabilizes:

- temperature returns within range
- humidity returns within range

Coordinator detects:

- conditions improving
- transition from RED → AMBER → GREEN

Debounce ensures:

- stable transition
- no oscillation

---

## Step 13: Resolution Feedback

System updates:

- asset state: GREEN

Concierge message (optional):

"Data closet conditions have returned to normal."

---

## Failure Example

If temperature sensor fails:

Environment Model:

- temperature: null
- confidence: DEGRADED

System behavior:

- does not trigger false automation
- advisory generated:

"Temperature data unavailable in data closet. Verify sensor."

---

## Key Principles Demonstrated

- evaluation is deterministic
- entity state is the automation trigger
- Asset Intelligence does not control devices directly
- automation layer performs actuation
- escalation is event-driven
- messaging is calm but escalates appropriately
- system degrades safely when data is incomplete

---

## Architectural Alignment

Asset Intelligence:

- evaluates conditions
- exposes state

Home Assistant Automations:

- respond to state
- control devices

Concierge:

- communicates outcomes
- escalates when needed

---

## Final Outcome

The system:

- detects environmental risk early
- initiates automated corrective actions
- monitors effectiveness of those actions
- escalates when automation is insufficient
- ensures human intervention when required

This results in:

- protected equipment
- minimal downtime risk
- controlled and explainable system behavior