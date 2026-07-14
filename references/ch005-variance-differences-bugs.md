# Section 5: Variance: Not All Differences Are Bugs

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** variance, variance differences bugs  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Good testing distinguishes harmless variation from variation that changes facts, safety,
reliability, or user trust.

## Actions

- Define that boundary before testing.
- Report variance by dimension.
- Score variance, factual variance, latency variance, ranking variance, policy variance, and action variance are not interchangeable.

## Evidence to Produce

- Report variance by dimension.
- Preserve the inputs, versions, configurations, raw outcomes, and results for variance, variance differences bugs needed to reproduce work on Variance: Not All Differences Are Bugs.
- Report results for variance, variance differences bugs by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Variance is the spread of behavior across runs. In a non-deterministic system, some spread is expected and even useful. The evaluator's job is to decide which differences preserve the user's outcome and which differences change the truth, risk, action, or experience.

Define that boundary before testing. Otherwise a brittle assertion will reject harmless wording while an overly permissive judge waves through a changed policy or unsafe action.

| Variance type | Acceptable example | Blocker example | Measurement |
| --- | --- | --- | --- |
| Wording | "Expected delivery is Friday" instead of "The package should arrive Friday" | "The package will arrive Friday" when the system cannot guarantee it | Semantic equivalence plus required-fact and prohibited-claim checks |
| Structure | The same support answer appears as a short paragraph or three readable bullets | An API returns prose instead of valid JSON, or a medical warning is buried after five paragraphs | Schema validation, required-section checks, readability, and task completion |
| Facts and policy | The explanation varies while the verified 24-hour cancellation cutoff stays unchanged | One run says 24 hours and another says 48 hours | Grounded fact accuracy, citation checks, and policy-version assertions |
| Safety | A refusal explains the same boundary in different respectful language | One rare run provides unsafe instructions, exposes a secret, or skips required confirmation | Severe-failure rate, repeated adversarial runs, and risk-slice review |
| Latency | A nightly report completes at 1:03 a.m. one day and 1:17 a.m. the next, both before its deadline | A voice assistant usually answers in 400 milliseconds but sometimes stalls for 8 seconds | p50, p95, p99, timeout rate, and user-visible service-level objectives |
| Ranking | The authoritative result remains first while two useful lower results swap places | The authoritative result falls below ads, stale pages, or unsafe advice | NDCG, top-k success, blocker-at-rank checks, and slice-level ranking stability |
| Tools and actions | The agent chooses either of two read-only paths that return the same authorized evidence | A run charges a card, deletes data, or changes an account without the required approval | Tool-trace assertions, permission checks, side-effect logs, and reversibility tests |

The table makes an important distinction visible: acceptable variance is conditional. Bullets are harmless only when formatting is not a contract. Latency spread is harmless only when the user deadline is still met. Ranking movement is harmless only when the evidence users need remains visible. A different tool path is harmless only when permissions and side effects remain equivalent.

This avoids two bad extremes. Treating every difference as a failure creates noisy tests that punish useful flexibility. Treating all variation as normal hides factual drift, unsafe tails, policy violations, and operational instability.

Non-deterministic testing is the discipline of drawing this line with product evidence. Variation is not the enemy. Unmeasured variation that changes user impact is.

## Expert Notes

Report variance by dimension. Score variance, factual variance, latency variance, ranking variance, policy variance, and action variance are not interchangeable. A single average can hide the type of instability users will actually feel.
