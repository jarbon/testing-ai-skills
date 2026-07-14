# Section 25: Power Analysis and Minimum Detectable Effect

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** sample size, power analysis, power analysis minimum detectable effect  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Before asking whether a change won, builders should decide what size of win would actually
matter.

## Actions

- Define runnable checks that exercise sample size, power analysis, and power analysis minimum detectable effect.
- Set acceptable outcomes and blocker failures for sample size, power analysis, and power analysis minimum detectable effect before running the evaluation.
- Run representative cases for sample size, power analysis, and power analysis minimum detectable effect and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for sample size, power analysis, power analysis minimum detectable effect needed to reproduce work on Power Analysis and Minimum Detectable Effect.
- Report results for sample size, power analysis, power analysis minimum detectable effect by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

Power analysis sounds advanced, but the everyday version is simple: a small flashlight will not reveal everything in a huge dark room. A small eval will not reveal every small quality difference.

The gentle starting question is not "Which equation do we use?" It is "What size of improvement would change our decision?" Once the team answers that, the math helps decide whether the planned sample is capable of seeing that improvement.

## Overview

Power analysis asks whether your evaluation has enough data to detect the effect you care about. Minimum detectable effect asks how large a change must be before the test is likely to notice it.
For example, 30 samples might detect a huge quality drop, but it probably will not reliably detect a tiny 0.1-point improvement. That is not a failure of math. It is a mismatch between sample size and decision.

Many teams run an eval, see no statistically significant difference, and conclude that two systems are the same. That can be wrong. The test may simply be too small to detect the difference.
The first question should be product-driven: what improvement is worth acting on? A 0.05-point score improvement may not justify a more expensive model. A 0.5-point improvement with lower failure rate might.
Power analysis helps Confidence Engineers design the evaluation before looking at results. If the team wants to detect a 0.3-point score improvement with reasonable confidence, the sample size should be chosen for that goal.
This changes the conversation. Instead of saying, "We tested 40 examples and saw nothing," the Confidence Engineer can say, "With 40 examples, this eval can only detect large changes. It is underpowered for the small improvement product is asking about."
Power also matters for failure rates. Detecting a drop from 10% failures to 5% is much easier than detecting a drop from 1.0% to 0.5%. Rare events require more data or targeted tests.
A rough two-proportion calculation makes the scale visible. At 95% confidence and about 80% power, detecting a failure-rate drop from 10% to 5% requires roughly 430-440 independent cases per version. Detecting a drop from 1.0% to 0.5% requires roughly 4,500 cases per version. Those are planning numbers, not commandments, but they explain why rare failures often need targeted stress suites, production monitoring, or risk-based sampling instead of a tiny general eval.
A good evaluation plan states the target effect size, expected noise, sample size, and decision threshold before the run. That keeps teams from inventing the goal after seeing the results.


## Quick Applied Example

### Example: BugPilot


> Compare the old coding agent with a new agent that claims to reduce security regressions.

The team has 60 historical repo tasks. The old agent introduced a security issue in 6 of them. The new agent introduces a security issue in 4 of them. That looks better: 10% down to about 7%.

But the sample is too small to trust the difference. Two fewer failures may be real improvement, ordinary sampling noise, or luck from the particular tasks chosen.

Before running the eval, define the minimum effect that matters:

- A drop from 10% to 9% may not justify a risky model migration.
- A drop from 10% to 5% might be worth shipping.
- A drop from 10% to 2% might justify extra cost and latency.
- A result from 6 failures to 4 failures should trigger more sampling, not celebration.

Power analysis asks the practical question first: how many cases would we need to detect the improvement we actually care about?

The release question is not, "Did the new agent win this sample?" It is, "Was this eval large enough to notice a meaningful win?"


## Expert Notes

Expert teams distinguish statistical power from business value. High power helps detect a chosen effect, but the minimum meaningful effect should come from product risk, user impact, cost, and operational tradeoffs.
