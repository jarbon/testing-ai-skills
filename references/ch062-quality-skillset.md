# Section 62: The New AI Quality Skillset

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** confidence interval, LLM judge, rubric, quality skillset  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The future AI builder is a rubric designer, sampling strategist, AI judge operator, risk
analyst, and statistical storyteller.

## Actions

- Define runnable checks that exercise confidence interval, LLM judge, and rubric.
- Set acceptable outcomes and blocker failures for confidence interval, LLM judge, and rubric before running the evaluation.
- Run representative cases for confidence interval, LLM judge, and rubric and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence interval, LLM judge, rubric, quality skillset needed to reproduce work on The New AI Quality Skillset.
- Report results for confidence interval, LLM judge, rubric, quality skillset by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The new AI quality skillset combines product judgment, evaluation design, sampling strategy, AI-assisted review, risk analysis, and statistical storytelling. The work becomes more strategic because the systems are less predictable.
For example, a developer may design a rubric in the morning, calibrate an LLM judge at noon, analyze confidence intervals in the afternoon, and explain a release recommendation to leadership by the end of the day, or AI might loop this all by itself.

The next generation AI builder does not only check whether one output matched one expectation. They evaluate behavior under uncertainty.

That requires a broader skillset.

The builder becomes a rubric designer. Non-deterministic systems need clear definitions of quality. The builder helps define what correctness, safety, completeness, tone, usefulness, policy compliance, reliability, and fairness mean for the product.

The builder becomes a sampling strategist. They decide which cases matter, how many samples are enough, which categories deserve deeper coverage, and which failures are rare but dangerous. Sampling is not administrative overhead. It is the foundation of credible evidence.

The builder becomes an AI judge operator. LLMs can help evaluate outputs at scale, but developers and quality specialists must write judge prompts, calibrate judge behavior, review disagreements, detect bias, and decide which cases require human escalation.

The Confidence Engineer becomes a risk analyst. They know that average quality is not enough. They watch the tails. They ask whether the system leaks data, violates policy, harms vulnerable users, takes irreversible actions, or fails in high-impact categories.

The Confidence Engineer becomes a statistical storyteller. They explain average scores, failure rates, confidence intervals, p-values, effect sizes, category breakdowns, and uncertainty in language the team can use. They do not hide behind math, and they do not ignore it. They translate evidence into a responsible recommendation.

> **The roles are merging.** These skillsets make developers, Confidence Engineers, and product managers more important, not less. AI does not remove the need for human judgment. It increases the need for people who can define quality, measure uncertainty, explain risk, and connect product intent to engineering evidence. The old boundaries between developer, tester, and PM get blurrier because AI quality work needs all three instincts at once: build the thing, know how it can fail, and understand what outcome the user actually needed.

A developer in this world does not say, "It passed once." They say, "Here is how often it behaved acceptably. Here is how bad the failures were. Here is how confident we are. Here is where the risk remains. Here is my ship recommendation."

That is the quality conversation modern AI products need.

The future of testing is not about pretending non-determinism can be forced into old patterns. It is about building new patterns that make unpredictable systems measurable, debuggable, and trustworthy enough to use.

## Expert Notes

The strongest AI builders become evaluation architects. They design systems that continuously measure quality, generate useful failure evidence, improve test assets from production learning, and make uncertainty understandable to non-statisticians.
