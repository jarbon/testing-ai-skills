# Section 179: Prediction 5: APIs and Interfaces Get Looser

**Book location:** Chapter 21, Predictions for the Tokenized Product Future  
**Use when:** 5 apis interfaces get looser  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI-native systems exchange intent, constraints, state, and tokens as much as fixed calls and
fixed screens.

## Actions

- Define runnable checks that exercise 5 apis interfaces get looser.
- Set acceptable outcomes and blocker failures for 5 apis interfaces get looser before running the evaluation.
- Run representative cases for 5 apis interfaces get looser and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for 5 apis interfaces get looser needed to reproduce work on Prediction 5: APIs and Interfaces Get Looser.
- Report results for 5 apis interfaces get looser by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Traditional APIs compress behavior into stable calls. That will remain important for high-integrity systems, but more AI-native systems will exchange richer and looser packets of intent, context, constraints, examples, tool schemas, and tokens.

This creates new quality questions. Was the intent understood? Were constraints preserved? Was the generated interface accessible? Did the system choose the right tool path? Did it expose too much data? Did it produce something that looks plausible but cannot be operated safely?

The more flexible the interface becomes, the more important the validation layer becomes.

## Expert Notes

Loose interfaces do not mean loose quality. They require stronger contracts around intent, constraints, permissions, provenance, generated artifacts, and validation before side effects reach users.
