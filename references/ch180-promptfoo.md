# Section 180: Appendix: Using Promptfoo

**Book location:** Appendices, Tools, Templates, and Reference  
**Use when:** LLM judge, retrieval, Promptfoo  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A lightweight eval tool turns prompt checks from vibes into repeatable tests that can run
locally, in CI, and before release.

## Actions

- Do not confuse tool output with truth.
- Treat Promptfoo as eval infrastructure, not a substitute for evaluation design and not something this book should document feature by feature.
- Version configs, lock datasets, track judge model changes, separate exploratory runs from release gates, and periodically compare automated scores against human raters.

## Evidence to Produce

- Include normal user tasks, edge cases, policy boundaries, prior production failures, and adversarial inputs.
- Preserve the inputs, versions, configurations, raw outcomes, and results for LLM judge, retrieval, Promptfoo needed to reproduce work on Appendix: Using Promptfoo.
- Report results for LLM judge, retrieval, Promptfoo by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

[Promptfoo](https://www.promptfoo.dev/docs/intro/) is a practical way to turn prompt checks, model comparisons, and red-team scenarios into repeatable evals. A Promptfoo workflow defines prompts, providers, test cases, assertions, and scoring rules in a versioned eval file, then runs that suite whenever the prompt, model, retrieval layer, tool policy, or application code changes.
For example, a support assistant team can compare two prompts across OpenAI, Anthropic, Gemini, and a local model, run 200 policy cases, score outputs with assertions or an LLM judge, and fail the build if the pass rate drops below the release threshold.

This chapter is not Promptfoo documentation. Tools change too quickly for that, and the details belong in the tool's own docs. The durable lesson is the workflow: put prompts, cases, providers, assertions, judges, thresholds, and release decisions into versioned eval infrastructure.

The practical value is structure. Instead of asking five people whether a new prompt feels better, write down the cases that matter. Include normal user tasks, edge cases, policy boundaries, prior production failures, and adversarial inputs.
The first goal is not perfect measurement. The first goal is to stop shipping changes that clearly break known behavior.

Promptfoo is useful because it supports several kinds of eval work that AI teams need repeatedly:

### Assertion-Based Validation

Assertions let you check whether outputs meet explicit conditions: valid JSON, required phrases, forbidden claims, policy compliance, tool-call shape, semantic similarity, latency thresholds, or specific expected answers. This is the bridge between traditional automated tests and fuzzy AI behavior.

### Automated Red Teaming

Red-team workflows generate adversarial scenarios such as prompt injections, jailbreak attempts, privacy attacks, unsafe requests, and tool-misuse probes. A clean average score can still hide a severe security or safety failure, so red-team cases should be treated as first-class release evidence.

### Multi-Model Comparison

The same prompt and same inputs can be run across multiple models, providers, temperatures, or prompt variants side by side. That makes cost, speed, accuracy, refusal behavior, formatting reliability, and safety tradeoffs visible instead of anecdotal.

### CI/CD Integration

Promptfoo evals can run inside development workflows such as GitHub Actions. A prompt change, model swap, system-message edit, policy update, retrieval change, or application-code change should trigger the same suite automatically. If the pass rate falls or severe failures appear, the team sees the regression before users do.

Do not confuse tool output with truth. Promptfoo is eval infrastructure, not a substitute for evaluation design. The rubric, dataset, labels, judge, and thresholds still need calibration.
The mature pattern is: start small, version the eval config, grow the golden set from production failures, review disagreement cases, and keep a human audit loop around high-risk decisions.

## Expert Notes

Treat Promptfoo as eval infrastructure, not a substitute for evaluation design and not something this book should document feature by feature. Version configs, lock datasets, track judge model changes, separate exploratory runs from release gates, and periodically compare automated scores against human raters.
