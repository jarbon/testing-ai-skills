# Section 175: Prediction 1: Validation Becomes the Compute Sink

**Book location:** Chapter 21, Predictions for the Tokenized Product Future  
**Use when:** monitoring, trace, 1 validation becomes compute sink  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When generation becomes cheap, validation becomes the expensive part of engineering.

## Actions

- Treat validation compute as product infrastructure.
- Define runnable checks that exercise monitoring, trace, and 1 validation becomes compute sink.
- Set acceptable outcomes and blocker failures for monitoring, trace, and 1 validation becomes compute sink before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for monitoring, trace, 1 validation becomes compute sink needed to reproduce work on Prediction 1: Validation Becomes the Compute Sink.
- Report results for monitoring, trace, 1 validation becomes compute sink by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

When generation is cheap, teams generate more candidates. More candidates require more filtering. More filtering requires more evals, judges, traces, simulations, canaries, safety checks, and production monitoring.

This is why testing AI will become a compute problem. Every prompt variant, model route, generated patch, personalized interface, and agent trajectory can be evaluated many ways: correctness, risk, cost, latency, policy fit, safety, accessibility, privacy, and business value.

The practical release question becomes: how much validation compute should we spend to gain enough confidence for this risk level?

## Expert Notes

Treat validation compute as product infrastructure. Budget it by risk, uncertainty, and business value instead of letting every generated candidate receive the same shallow check.
