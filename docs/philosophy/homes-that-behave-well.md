# Homes That Behave Well

## Overview

Homes That Behave Well is a philosophy for building smart home systems that are calm, predictable, and trustworthy.

This is not an automation framework.

It is a decision-support system for the home.

---

## Core Principles

### 1. Calm

The system should never overwhelm the user.

- No unnecessary alerts  
- No repetitive messaging  
- No background noise  

The home should speak only when it matters.

---

### 2. Predictable

The system must behave consistently.

- Same input leads to same output  
- No hidden logic  
- No surprising behavior  

If a user cannot predict what will happen, the system is broken.

---

### 3. Explainable

Every action must have a reason.

The system must always be able to answer:

- Why did this happen?  
- What triggered it?  
- What data was used?  

If the system cannot explain itself, it should not act.

---

### 4. Deterministic

All decisions must be based on defined logic.

- No randomness in system behavior  
- No hidden AI decisions  
- No implicit assumptions  

Evaluation must always be:

- repeatable  
- traceable  
- consistent  

---

### 5. Progressive Intelligence

The system becomes smarter as integrations are added.

- No reconfiguration required  
- No behavioral rewrites  
- No duplication of logic  

New integrations extend understanding, not complexity.

---

## Architectural Separation

The system enforces strict boundaries between responsibilities.

### Asset Intelligence

Owns:

- asset data  
- environment requirements  
- validation  
- persistence  
- evaluation  

Does not:

- manage user interaction  
- generate voice behavior  
- own orchestration  

---

### Concierge

Owns:

- interaction  
- orchestration  
- messaging  
- user experience  

Does not:

- own data  
- store state  
- evaluate raw environment data  
- mutate asset data directly  

---

### Homes That Behave Well

Defines:

- system rules  
- architecture contracts  
- behavioral expectations  
- cross-integration patterns  

---

## AI Philosophy

AI must be controlled, bounded, and explainable.

### Rules

- AI never mutates system state directly  
- AI produces recommendations only  
- All changes must go through validated services  
- All AI output must be explainable  

---

### Acceptable AI Role

AI may:

- suggest environment values  
- summarize complex data  
- provide reasoning for recommendations  

AI may not:

- write to the system of record  
- bypass validation  
- make untraceable decisions  

---

## Communication Model

All communication follows a strict hierarchy:

### Info
- Visual only  
- No interruption  

### Attention
- Visual plus optional voice  
- Non-urgent  

### Urgent
- Immediate voice  
- Interruptive if required  

### Night Mode
- Suppress all except urgent  

---

## Decision Model

The system follows a consistent flow:

Input → Environment → Evaluation → Decision → Action → Explanation

### Key Rules

- Evaluation must be deterministic  
- Decisions must be explainable  
- Actions must be validated  
- Explanations must be available  

---

## System Behavior Rules

The system must never:

- surprise the user  
- repeat unnecessary actions  
- act without explanation  
- bypass validation  
- overload the user with information  

The system must always:

- prioritize clarity over cleverness  
- prioritize trust over speed  
- degrade gracefully when data is incomplete  
- remain stable under changing conditions  

---

## Design Goal

A Home That Behaves Well:

- understands its environment  
- respects the user  
- explains its decisions  
- improves over time  
- never loses trust  

---

## Final Principle

If a feature makes the system:

- noisier  
- less predictable  
- harder to explain  

It should not be built.