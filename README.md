# Homes That Behave Well

Homes That Behave Well is a design philosophy and architectural framework for building calm, predictable, and trustworthy smart home systems using Home Assistant.

This repository defines the shared architecture, contracts, and behavioral patterns used across all integrations in the Homes Platform, including:

- Asset Intelligence
- Concierge
- Future intelligence layers (security, energy, presence, etc.)

---

## Purpose

This repository is not a runtime integration.

It exists to:

- Define system-wide rules and contracts
- Provide consistent architectural guidance
- Serve as the Copilot grounding layer
- Enable multi-repo development without drift
- Support a future advisory and design platform

---

## Core Philosophy

Homes should:

- Be calm — no unnecessary interruptions
- Be predictable — consistent behavior across scenarios
- Be explainable — every action has a clear reason
- Be deterministic — same inputs lead to same outputs
- Be progressively intelligent — improve as integrations are added

---

## System Model

The platform is built from independent integrations:

| Layer | Responsibility |
|------|----------------|
| Asset Intelligence | System of record, evaluation, validation |
| Concierge | Orchestration, interaction, user experience |
| Homes That Behave Well | Architecture, contracts, philosophy |

---

## Key Principle

Concierge never owns data.  
Asset Intelligence never owns interaction.  
Homes That Behave Well defines the rules of behavior.

---

## AI Philosophy

- AI never mutates system state directly
- AI produces recommendations only
- All changes must go through validated services
- All AI-driven actions must be explainable and auditable

---

## Repository Structure

docs/
  philosophy/
  architecture/
  contracts/
  patterns/
  models/

examples/
  scenarios/
  interaction-flows/

---

## How This Is Used

This repository is loaded into the VS Code workspace alongside:

- Asset Intelligence
- Concierge

This allows Copilot to:

- Follow architecture rules
- Respect integration boundaries
- Generate consistent implementations

---

## Design Goal

This system is not automation.

It is:

A decision-support system for the home.