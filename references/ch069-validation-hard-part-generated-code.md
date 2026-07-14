# Section 69: Validation Is the Hard Part of AI-Generated Code

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** generated code, validation hard part generated code  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI makes code generation cheap. It does not make the cost of proving that code safe, correct,
and maintainable cheap.

## Actions

- Use superlinear growth and the O(n^2) pairwise surface as planning heuristics for interaction risk, not literal forecasts.
- Use dependency analysis, contract checks, risk scoring, mutation testing, property-based tests, historical defect replay, and production trace replay to keep validation efficient as AI-generated code volume rises.
- Define runnable checks that exercise generated code and validation hard part generated code.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for generated code, validation hard part generated code needed to reproduce work on Validation Is the Hard Part of AI-Generated Code.
- Report results for generated code, validation hard part generated code by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The seductive part of AI-generated code is speed. A model can produce hundreds or thousands of lines in minutes, or entire products overnight. The expensive part is figuring out whether those lines correctly interact with everything already in the system.
For example, a generated billing change may touch discounts, taxes, refunds, invoices, entitlements, audit logs, account permissions, and support workflows. The code may be short, but the validation surface is large.

Testing AI-generated code is often not a simple linear function of the number of new lines. Validation can grow superlinearly when a change touches many existing behaviors, data contracts, permissions, dependencies, UI assumptions, APIs, deployment settings, and production workflows.

If n independently changing components can interact pairwise, the interaction surface can approach n(n-1)/2, or roughly O(n^2). That is a planning model, not a universal law and not a claim that every pair requires its own test. Small isolated changes with strong contracts can remain inexpensive. Broad changes with weak boundaries can expand the validation surface much faster than the diff size suggests.
This is why generation feels easy and validation feels hard. The model can emit code locally. The Confidence Engineer has to reason globally.
Line count is also misleading. Ten generated lines in an authorization helper can create more risk than 500 generated lines of UI layout. Validation cost follows interaction, criticality, and blast radius, not raw size.
AI-generated code also creates correlated risk. The same mistaken assumption can appear in the implementation, tests, comments, and mocks because they were all generated from the same prompt.
Coverage numbers can become dangerous here. A generated test suite may cover the generated code while failing to challenge the generated assumption.
The answer is not to validate every interaction equally. That would collapse under scale. The answer is risk-based validation: identify what the change can touch, where failure would be severe, which assumptions are new, and which contracts must hold.
Future AI coding systems will win not by generating the most code, but by generating code with a validation plan: affected contracts, impacted workflows, targeted tests, security checks, trace replays, and rollback criteria.

## Expert Notes

Estimate validation effort by interaction graph, not lines of code. Use superlinear growth and the O(n^2) pairwise surface as planning heuristics for interaction risk, not literal forecasts. Use dependency analysis, contract checks, risk scoring, mutation testing, property-based tests, historical defect replay, and production trace replay to keep validation efficient as AI-generated code volume rises.
