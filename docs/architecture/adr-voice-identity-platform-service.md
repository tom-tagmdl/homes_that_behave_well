# ADR: Voice Identity as a First-Class HTBW Platform Service

## 1. Status

Accepted.

## 2. Context

Concierge voice enrollment established production browser and satellite enrollment workflows with shared lifecycle, consent handling, cleanup behavior, and person linkage.

Those foundations are necessary but not sufficient for functional voice-identity completion.

A real durable speaker fingerprint is required before voice enrollment can be considered functionally complete.

Fingerprint generation, fingerprint artifact lifecycle, model/version governance, runtime speaker attribution, confidence scoring, and identity-resolution contracts are a distinct bounded domain from Concierge context and coordinator responsibilities.

## 3. Decision

Voice Identity is a standalone HTBW platform service and repository consumed by Concierge.

Concierge integrates Voice Identity as an optional platform capability.

Voice Identity owns speaker fingerprint generation and future runtime speaker attribution.

Concierge remains the context engine and coordinator.

## 4. Rationale

- isolates model/runtime dependency complexity from Concierge orchestration scope
- preserves clean platform boundaries across context, identity, and domain intelligence
- supports optional capability enablement and graceful degradation
- enables independent identity model/version lifecycle governance
- keeps biometric/fingerprint lifecycle behind dedicated service boundaries

## 5. Platform Responsibility Boundary

| Platform Service | Owns | Answers |
|---|---|---|
| Foundation | rooms, spaces, devices, presence, occupancy, environmental state, source-of-truth platform facts | What is true? |
| Asset Intelligence | assets, asset metadata, environmental constraints, protection rules, care intelligence, asset risk/care summaries | What matters? |
| Voice Identity | fingerprint generation, fingerprint artifacts and references, fingerprint quality, model/version metadata, runtime speaker attribution, match confidence, no-match reasoning | Who is interacting? |
| Concierge | people configuration, permissions, room context, conversation and activity context, coordinator, intent and response routing, user experience | What should happen? |

## 6. Voice Identity Responsibilities

Voice Identity owns:

- voice enrollment fingerprint generation
- speaker fingerprint artifacts and references
- fingerprint model/version and schema governance
- enrollment quality outputs
- future runtime speaker attribution
- speaker match confidence outputs
- no-match and low-confidence reason codes

Voice Identity does not own Concierge coordinator policy decisions.

## 7. Concierge Responsibilities

Concierge owns:

- people setup and profile configuration
- room, conversation, and activity context
- permission and policy evaluation
- coordinator decision flow
- response and intent routing
- enrollment orchestration UX and lifecycle consumption

Concierge consumes Voice Identity outputs and must not own fingerprint model internals.

## 8. Asset Intelligence Relationship

Asset Intelligence remains the domain service for asset truth, risk, and care intelligence.

Voice Identity does not replace or subsume asset intelligence responsibilities.

Concierge may combine identity context and asset context, but those contexts remain independently owned by Voice Identity and Asset Intelligence.

## 9. Foundation Relationship

Foundation remains source-of-truth for rooms, spaces, devices, presence, occupancy, and environmental state.

Voice Identity is not a substitute source-of-truth for foundational home state.

Identity outputs are fused with Foundation truth by Concierge at decision time.

## 10. Privacy and Local-First Requirements

- raw enrollment recordings are temporary processing artifacts
- speaker fingerprints are durable local-first identity artifacts
- fingerprint vectors must not be exposed in diagnostics, telemetry, repairs, service responses, or manifest projections
- Concierge stores fingerprint metadata/reference only
- Voice Identity owns fingerprint generation and artifact lifecycle
- cloud fingerprinting is not the default architecture

## 11. HACS / Distribution Considerations

- Concierge can be installed independently
- Voice Identity can be installed independently
- Concierge may expose Voice Identity capability/status in global settings
- Concierge must degrade gracefully when Voice Identity is unavailable

Recommended capability states include:

- not installed
- installed but unavailable
- connected
- model unavailable
- fingerprint generation unavailable
- attribution unavailable

## 12. Future Coordinator Integration

Concierge coordinator should consume Voice Identity as identity context input.

Target runtime flow:

Voice Assistant / Browser / Satellite
  -> Voice Identity
  -> Resolved Person + Confidence + Reason Code
  -> Concierge Coordinator
  -> Permissions + Context + Intent
  -> Action

Enrollment-time flow:

Browser or Satellite Capture
  -> Concierge Enrollment Workflow
  -> Voice Identity Fingerprint Generation
  -> Fingerprint Artifact Reference
  -> Concierge VoiceProfile Metadata
  -> Temporary Recording Cleanup

## 13. Consequences

Positive outcomes:

- stronger architectural separation between identity engine and context engine
- clearer ownership for biometric data lifecycle
- independent iteration velocity for identity technology and model governance
- more explicit integration contracts between platform services

Tradeoffs:

- additional integration boundary to maintain
- explicit capability detection and fallback logic required in Concierge
- cross-repository version compatibility management required

## 14. Non-Goals

Voice Identity does not own:

- room context
- permission policy decisions
- coordinator decisions
- intent routing
- user interface
- Home Assistant person configuration
- device control
- asset intelligence

Concierge does not own:

- fingerprint model internals
- embedding generation
- vector comparison algorithms
- speaker attribution algorithms
- identity model lifecycle