# Section 63: AI-Generated Code That Looks Right but Is Wrong

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** generated code, generated code looks right wrong  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI-generated code often fails in a dangerous way: it looks clean, compiles, and still implements
the wrong behavior.

## Actions

- Do not only test the happy path the prompt described.
- Test the neighboring cases the prompt did not mention.
- Use property-based tests, metamorphic tests, boundary matrices, and requirement-to-test traceability.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for generated code, generated code looks right wrong needed to reproduce work on AI-Generated Code That Looks Right but Is Wrong.
- Report results for generated code, generated code looks right wrong by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The most common AI-generated code issue is not messy syntax. It is plausible code that solves a nearby problem instead of the actual problem. The names look right. The structure looks familiar. The bug hides in the assumptions.
For example, an AI coding assistant may implement a discount rule for total cart value, but the product requirement says the discount applies only to eligible items. The code passes simple tests and fails real billing behavior.

AI-generated code is optimized to produce something that resembles a good answer. That is useful, but it means Confidence Engineers must distrust surface polish. Clean code can still be semantically wrong.

AI-generated code failures tend to fall into two overlapping groups.

Common coding failures include:

- Misread requirement or product rule
- Missed edge cases and boundaries
- Wrong error handling or retry behavior
- Integration or API contract mismatch
- State, concurrency, or ordering bug
- Security, privacy, or permission gap
- Performance, memory, or scaling surprise
- Tests that pass but cover only the easy path

More AI-agent-shaped failures include:

- Solves a nearby problem, not the problem actually asked for
- Copies a pattern from the wrong endpoint or file
- Fabricates APIs, configs, flags, or schemas
- Adds silent fallbacks that hide real failures
- Changes tests or oracles to bless the bug
- Creates an over-broad abstraction for one local example
- Misses hidden context in files, tools, policies, or docs
- Lets multi-step edits drift out of sync across files
- Gives a confident rationale with weak or missing evidence

The practical rule is evidence before trust. Before accepting AI-generated code, ask for behavioral tests, negative cases, hidden edge cases, a diff rationale, the files and tools touched, a security review, and a rollback path.

Look for requirement drift. The generated code may ignore edge clauses, exception rules, ordering requirements, rounding rules, time zones, permissions, null behavior, or product-specific terminology.
Look for off-by-one and boundary mistakes. LLMs are good at producing loops and filters, but they often miss inclusive versus exclusive ranges, empty inputs, maximum lengths, pagination boundaries, and daylight-saving-time cases.
Look for fake generality. The code may create a broad abstraction that handles the example but does not match the domain. A generic validation helper may erase a critical product rule.
Look for silent fallback behavior. AI-generated code often catches errors, returns defaults, or logs and continues. That can hide real failures behind friendly-looking output.
The best test response is example-driven. Turn the requirement into concrete cases, especially counterexamples where a similar-looking implementation would be wrong.
Do not only test the happy path the prompt described. Test the neighboring cases the prompt did not mention. That is where plausible-but-wrong code usually reveals itself.
When reviewing AI-generated code, ask: what assumption did the model make that a human expert would not have made?

## Quick Applied Example


## Expert Notes

Use property-based tests, metamorphic tests, boundary matrices, and requirement-to-test traceability. AI-generated code should be judged by behavioral evidence, not by whether it looks idiomatic.
