# Section 48: Regression Testing When Outputs Keep Changing

**Book location:** Chapter 7, Release Readiness for AI Systems  
**Use when:** regression testing, regression outputs keep changing  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When exact outputs drift, regression testing has to protect invariants, not fossilize
yesterday's wording.

## Actions

- Define what must remain true: required facts, policy boundaries, refusal behavior, ranking relevance, citation grounding, tool permission checks, or latency limits.
- Define runnable checks that exercise regression testing and regression outputs keep changing.
- Set acceptable outcomes and blocker failures for regression testing and regression outputs keep changing before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for regression testing, regression outputs keep changing needed to reproduce work on Regression Testing When Outputs Keep Changing.
- Report results for regression testing, regression outputs keep changing by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Regression testing for non-deterministic systems is not about freezing every output. It is about detecting when behavior gets worse on the properties that matter.
For example, a summary can change wording without regressing, but it regresses if it drops a key risk, invents a fact, or becomes less usable for the target user.

Traditional regression tests often compare current output to an expected output. That is useful for deterministic systems. For LLMs, search, ranking, and agents, exact comparison often creates noise.
The better pattern is invariant-based regression. Define what must remain true: required facts, policy boundaries, refusal behavior, ranking relevance, citation grounding, tool permission checks, or latency limits.
A regression suite should contain known important cases, past failures, high-risk categories, and representative examples. Each case should define the properties being protected.
Expected outputs can still be useful as examples, but they should not be treated as the only acceptable response unless the product truly requires exact wording.
Regression reports should distinguish acceptable drift from true degradation. If the wording changed but the answer stayed correct, do not burn the team's attention. If the score dropped, a hard failure appeared, or a high-risk category weakened, slow down.
Baseline refresh is part of the work. Old expected outputs can become stale when products, policies, or user needs change. Refresh deliberately, not casually.

### Example: CartCare Chatbot

> Is my ice cream still arriving before it melts?

This is a better chatbot regression case than it looks. The right answer depends on live order state, driver location, local weather, store substitution status, delivery ETA, packaging type, and the store's cold-chain policy. A fixed expected response would be silly. A vague "sounds helpful" rubric would be too weak.

The test should allow the wording to change, but not the evidence discipline:

- CartCare must check the current order, not answer from general grocery policy.
- It must use the live ETA or clearly say when ETA is unavailable.
- It must notice that ice cream is temperature-sensitive.
- It must not promise safety or quality if the delivery window is already risky.
- It should offer concrete options: continue waiting, substitute, cancel, refund, or escalate.
- It should preserve a calm, practical tone instead of cheerfully hand-waving the customer's concern.

The regression question is not whether CartCare says the same sentence every time. It is whether the bot grounds the answer in the live delivery facts that determine whether the ice cream is likely to survive the trip.

## Expert Notes

The deeper move is to keep separate baselines for examples, rubrics, labels, model versions, and judge versions. A regression can come from the product, the evaluator, the dataset, or the policy changing underneath the test.
