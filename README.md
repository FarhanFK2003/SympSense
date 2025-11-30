# SympSense
SYMPSENSE - A Micro Health Multi-Agent Symptom Insight System

This project implements a multi-agent AI system designed to assist users in understanding their symptoms, assessing potential severity, and receiving actionable suggestions. Built as part of the Google x Kaggle AI Agents Intensive, the system demonstrates modern agent architecture principles including multi-agent orchestration, parallel agent execution, deterministic fallbacks, memory, and optional Gemini model reasoning.

The goal is not to replace medical professionals, but to show how agent-based AI frameworks can structure health-related decision support workflows in a transparent, modular, and safe way.

## Project Overview

Many individuals experience mild or confusing symptoms but are unsure whether the issue is urgent or manageable at home. This micro-health agent system provides:

- A quick, safe, and structured symptom extraction

- A lightweight severity triage

- Actionable suggestions & precautions

- Simple pattern analysis from recent symptom history

This system is designed to be:

- Reliable (deterministic baseline logic always works)
- Extendable (easily add new agents or medical rules)
- Transparent (all decisions are explicit & logged)
- Model-optional (works with or without Gemini API access)

## Architecture

The system consists of four collaborative agents orchestrated by a central coordinator:

### SymptomAgent

Extracts symptoms from user input using a keyword-based deterministic engine and (optionally) Gemini for improved comprehension.

### TriageAgent

Evaluates symptom severity based on simple rule-based logic
→ e.g., shortness of breath = urgent, multiple combined symptoms = moderate.

### SuggestionAgent

Provides actionable next steps and safety precautions based on the identified symptoms.

### TrendAgent

Uses short-term memory to detect recurring symptoms, offering context about symptom history and potential patterns.

### MultiAgentCoordinator

- Manages message passing
- Executes agents in parallel for improved performance
- Aggregates final structured output

## What This Agent Can Do

Given a user input such as:

> “I’ve had a fever and headache for two days and now feeling very tired.”

The agent produces a structured triage output:

```json
{
  "symptoms": ["fever", "headache", "fatigue"],
  "severity": "moderate",
  "severity_reason": "multiple symptoms detected",
  "suggestions": ["Paracetamol if suitable", "Monitor your condition"],
  "precautions": ["Rest", "Hydrate"],
  "trends": { "fever": 2, "fatigue": 2 },
  "disclaimer": "This is not medical advice. For emergencies contact local services."
}
```
## Safety & Limitations

This tool is not medical advice and should not be used for diagnosis, emergency decision-making, or professional recommendation.

Instead, it is a technical exploration of how AI agents can work together to structure early health triage workflows safely and transparently.
