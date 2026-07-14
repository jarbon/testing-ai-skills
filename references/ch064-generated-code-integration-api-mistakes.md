# Section 64: AI-Generated Code Integration and API Mistakes

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** generated code, integration, API mistake, generated code integration api mistakes  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI coding tools are confident around APIs, libraries, and frameworks, even when the details are
stale, invented, or incompatible with your codebase.

## Actions

- Use contract tests, sandbox calls, schema validation, and type checks where possible.
- Define runnable checks that exercise generated code, integration, and API mistake.
- Set acceptable outcomes and blocker failures for generated code, integration, and API mistake before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for generated code, integration, API mistake, generated code integration api mistakes needed to reproduce work on AI-Generated Code Integration and API Mistakes.
- Report results for generated code, integration, API mistake, generated code integration api mistakes by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI-generated code frequently fails at integration boundaries. It may call the wrong method, use an old API, invent a parameter, misunderstand an SDK, or ignore a local helper that the codebase already relies on.
For example, a generated payment integration may use a deprecated field from an old blog post, skip an idempotency key, or call a client library pattern that no longer exists in the installed version.

Integration bugs happen because AI tools learn patterns from many versions of many libraries. The answer may be reasonable for some project, some year, and some dependency version, but not this one.
Confidence Engineers should inspect package versions, framework conventions, local wrappers, feature flags, environment variables, and deployment configuration. A generated snippet that works in isolation may fail inside the real system.
Look for hallucinated APIs. If a method name looks too perfect, verify it against installed docs or type definitions. LLMs often invent helper methods that should exist but do not.
Look for dependency drift. The code may rely on behavior from a newer library than the project uses, or preserve a workaround from an older library that no longer applies.
Look for missing operational details: retries, timeouts, idempotency, rate limits, authentication scopes, pagination, partial failures, and error mapping.
Mock-only tests are not enough. They can confirm the code calls the fake interface you created, while the real API rejects the request.
Use contract tests, sandbox calls, schema validation, and type checks where possible. The closer the test gets to the real boundary, the more useful it becomes.
AI-generated integration code should always be reviewed against the local system, not just against the prompt that produced it.

## Quick Applied Example


## Expert Notes

Combine static analysis, type checking, contract tests, real sandbox calls, dependency lockfile review, and production-like configuration tests. The most expensive AI-generated code bugs often live at system boundaries.
