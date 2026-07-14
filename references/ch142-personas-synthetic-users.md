# Section 142: Testing AI Personas and Synthetic Users

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** human rater, RAG, synthetic user, personas synthetic users  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Synthetic users can expand coverage, but they are test instruments. They are not reality.

## Actions

- Treat personas as generators and probes, not judges of record.
- Track persona prompt, model, seed, intended population, known limitations, calibration results, and which failures were confirmed by human review or production traces.
- Define runnable checks that exercise human rater, RAG, and synthetic user.

## Evidence to Produce

- Track persona prompt, model, seed, intended population, known limitations, calibration results, and which failures were confirmed by human review or production traces.
- Preserve the inputs, versions, configurations, raw outcomes, and results for human rater, RAG, synthetic user, personas synthetic users needed to reproduce work on Testing AI Personas and Synthetic Users.
- Report results for human rater, RAG, synthetic user, personas synthetic users by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI personas and synthetic users are useful because they let teams explore more situations than a human rater budget can cover. They can simulate new users, experts, confused users, angry users, multilingual users, accessibility needs, privacy-sensitive users, enterprise admins, or developers with specific workflows.

They are especially useful for personalization because the number of possible user contexts is enormous. Instead of collecting human labels for every profile, a team can use synthetic users to generate candidate failures, stress-test assumptions, and identify slices worth deeper human review.

The danger is that synthetic users inherit the biases, blind spots, and assumptions of the model that created them. They can make coverage look larger while making reality smaller.

## Expert Notes

Treat personas as generators and probes, not judges of record. Track persona prompt, model, seed, intended population, known limitations, calibration results, and which failures were confirmed by human review or production traces. Synthetic users are excellent for finding questions. They are dangerous when treated as answers.
