# Concierge Global Configuration Contract

## Purpose

The Concierge Global Configuration defines system-level settings that control how Concierge operates across the entire home.

This configuration governs:

- AI provider configuration
- voice and speech behavior
- system-wide execution rules
- external integration connections

Global Configuration is foundational and must be separated from room-level and interaction-level configuration.

---

## Core Principle

Global Configuration defines how the system operates.

Room and UI configuration define how the system behaves.

---

## Scope

Global Configuration applies to:

- all rooms
- all interactions
- all execution paths

It is not scoped to any individual room or user interaction.

---

## Configuration Layers

Global Configuration consists of three layers:

1. System Providers
2. Behavior Rules
3. Integration Connections

---

# 1. SYSTEM PROVIDERS

---

## Purpose

Defines the providers used for AI and voice capabilities.

---

## AI Configuration

AI must be explicitly configured and must follow local-first execution rules.

Structure:

ai:
  enabled:
  local_first:
  action_llm:
    provider:
    model:
    endpoint:
    api_key:
    timeout:
  tts_llm:
    provider:
    model:
    voice:
    endpoint:

---

## Rules

AI must:

- be optional and configurable
- operate only when deterministic execution is not sufficient
- never be required for core system functionality

AI must not:

- directly execute actions
- determine execution strategy
- override system-defined behavior

---

## TTS Configuration

Defines text-to-speech behavior.

Structure:

tts:
  provider:
  default_voice:
  volume_profile:

Rules:

- must support Home Assistant native TTS when available
- must not delay execution
- must integrate with audio routing model

---

# 2. BEHAVIOR RULES

---

## Purpose

Defines system-wide behavior constraints and policies.

---

## Execution Behavior

Structure:

behavior:
  prefer_local_execution:
  require_deterministic_execution:
  allow_ai_for:
    - summarization
    - disambiguation
    - recommendations
  block_ai_for:
    - execution
    - device_control
    - state_interpretation

---

## Rules

The system must:

- prefer local execution over external calls
- remain deterministic for all actions
- execute immediately once intent is resolved

The system must not:

- depend on AI for execution decisions
- introduce latency due to unnecessary processing

---

## AI Fallback Rules

Structure:

fallback:
  allow_llm_fallback:
  require_confirmation_for_actions:

Rules:

- fallback must be explicit
- user safety must be preserved
- all AI-driven actions must be explainable

---

# 3. INTEGRATION CONNECTIONS

---

## Purpose

Defines external system connections and authentication.

Examples:

- Microsoft 365
- weather providers
- news providers
- third-party APIs

---

## Connection Model

Structure:

connections:
  microsoft_365:
    connected:
    permissions:
  weather:
    provider:
  news:
    provider:

---

## Rules

Connections must:

- be configured behind the integration settings (gear icon)
- separate authentication from usage
- expose capabilities to Concierge via contracts

Connections must not:

- expose credentials in UI
- bypass integration boundaries
- embed logic within Concierge

---

# CONFIGURATION ACCESS MODEL

---

## UI Separation

Global Configuration must be accessed via:

- Home Assistant integration options (gear icon)

It must not be exposed in:

- room configuration UI
- interaction panels
- end-user dashboards

---

## Usage vs Configuration

Rules:

- configuration defines system capability
- UI defines how capability is used

Example:

Connecting Microsoft 365 → configuration  
Enabling calendar in Concierge → UI  

---

# RELATIONSHIP TO OTHER MODELS

---

## Global Context

Global Configuration enables Global Context sources.

It does not define how they are used.

---

## Signals

Global Configuration enables integrations that provide signals.

It does not define signal state or behavior.

---

## Execution

Global Configuration defines rules governing execution.

Execution Patterns define how actions occur.

---

## Concierge

Concierge consumes Global Configuration but does not modify it.

---

# FAILURE HANDLING

---

If configuration is incomplete:

- system must continue operating in local-only mode
- AI capabilities must be disabled
- execution must remain deterministic

The system must never:

- fail completely due to missing configuration
- attempt unsafe fallback behavior

---

# SECURITY RULES

---

Global Configuration must:

- protect credentials and API keys
- ensure secure communication with external services
- restrict unauthorized access

Sensitive data must never be exposed in:

- UI panels
- interaction models
- logs visible to users

---

# SYSTEM BEHAVIOR RULES

---

The system must:

- remain local-first
- be deterministic by default
- allow controlled extensibility via providers

The system must not:

- rely on external systems for core functionality
- introduce nondeterministic behavior
- blur separation between configuration and execution

---

# FINAL PRINCIPLE

Global Configuration defines the foundation of the system.

It enables capability, but does not define experience.

Concierge uses this foundation to deliver a consistent, reliable, and context-aware interaction model across the home.