# Scenario: Artwork Risk and Insurance Reporting

## Purpose

This scenario demonstrates how the system monitors risk for a high-value artwork and provides structured, explainable information suitable for insurance and documentation purposes.

It shows:

- environmental risk detection
- exposure analysis
- advisory generation
- financial and insurance context
- document handling
- exportable reporting

---

## Scenario Overview

A framed painting is displayed in a living room.

The room has:

- windows facing southwest
- variable sunlight exposure throughout the day
- incomplete humidity control

The artwork is insured and requires:

- stable humidity
- minimal UV exposure
- documented environmental history

---

## Asset Definition

Asset:

- name: Oil Painting
- asset_type: artwork

Placement:

- area_id: living_room
- near_window: true
- facing_direction: southwest

Environment Requirements:

- humidity: 45 to 55 percent
- temperature: 65 to 72 degrees Fahrenheit
- lux: low to moderate
- uv: minimal

---

## Financial and Insurance Data

Purchase:

- purchase_date: recorded
- purchase_price: stored
- source: gallery or auction

Valuation:

- estimated_value: updated periodically
- valuation_date: recorded
- method: appraisal

Insurance Context:

- insured: true
- policy_reference: external (document system)
- coverage limits: external (document system)

Rules:

- financial data is stored in the asset model
- policy documents are stored externally
- only references are stored in the system

---

## Documents

Linked documents:

- appraisal document
- purchase receipt
- insurance policy reference
- restoration records (if applicable)

Storage:

- documents are stored in external storage
- asset stores only references and metadata

---

## Step 1: Environment Snapshot

Environment Model produces:

- temperature: 73
- humidity: 60
- lux: 250
- uv: present
- confidence: GOOD

Interpretation:

- humidity above recommended range
- light exposure elevated
- UV present and relevant to material sensitivity

---

## Step 2: Exposure Analysis

Exposure Model combines:

- lux and UV levels
- window direction: southwest
- asset placement: near window
- sun alignment: active

Derived Output:

- directional_match: true
- exposure_risk_level: HIGH
- effective_uv: elevated

Interpretation:

- direct sunlight increasing UV exposure
- exposure risk amplified by placement

---

## Step 3: Evaluation

Evaluation Engine compares:

- environment snapshot
- exposure projection
- asset requirements

Result:

- risk_state: RED

Reasons:

- humidity exceeds safe range
- UV exposure above acceptable levels
- sustained directional light exposure

---

## Step 4: Coordinator Processing

Coordinator:

- confirms sustained condition
- transitions state to RED
- generates event:

Event:

- type: risk_state_changed
- asset: oil_painting
- from: AMBER
- to: RED
- timestamp: recorded

---

## Step 5: Advisory

Advisory System generates:

Primary Advisory:

- "UV exposure and humidity exceed safe limits for this artwork."

Supporting Advisory:

- "Consider reducing humidity to protect the material."
- "Reduce direct sunlight exposure using window treatments."
- "Reposition the artwork away from the window."

---

## Step 6: Insurance Relevance

The system identifies that:

- asset is high value
- asset is insured
- risk state is RED

System flags:

- potential impact to insured condition
- need for documented environmental history

---

## Step 7: Insurance Data Preparation

The system can generate a structured report including:

### Asset Summary

- asset name
- asset type
- valuation
- location (room)

---

### Environmental History

- time-series of temperature and humidity
- light and UV exposure patterns
- confidence levels

---

### Risk Events

- timestamps of risk state transitions
- duration of elevated risk conditions
- explanation of each transition

---

### Exposure Analysis

- window direction
- directional exposure events
- derived exposure risk levels

---

### Advisory History

- recommendations generated
- timestamps of advisory events
- user actions taken (if any)

---

## Step 8: Document Integration

Report includes references to:

- appraisal document
- insurance policy reference
- prior condition reports

Rules:

- no binary documents stored in system
- only references included
- external storage resolves the content

---

## Step 9: Export for Insurance

The system can produce an export:

Format:

- structured JSON or PDF (future)
- includes all relevant fields
- includes referenced documents

Example output sections:

- asset metadata
- valuation summary
- risk history
- environmental history
- exposure analysis
- advisory actions

---

## Step 10: User Interaction

User views asset detail:

- sees RED risk state
- sees explanation
- sees advisory

User selects:

- "Generate Report for Insurance"

System behavior:

1. button highlights immediately
2. loading indicator appears
3. report is generated
4. confirmation shown
5. report reference displayed

---

## Failure Example

If required history is missing:

- system generates partial report
- clearly indicates missing data

Example:

"Environmental history incomplete for this period"

The system must never:

- fabricate data
- omit known limitations
- misrepresent conditions

---

## Key Principles Demonstrated

- asset model includes financial and insurance context
- environment and exposure drive risk detection
- advisory remains separate from action
- external storage is used for documents
- system produces explainable, auditable outputs
- reports are generated from deterministic data

---

## Final Outcome

The system:

- detects environmental risk to the artwork
- explains why risk exists
- provides actionable recommendations
- maintains structured financial and document records
- produces insurance-ready reporting
- ensures data is explainable, auditable, and accurate

The result is a system that supports both preservation and accountability.