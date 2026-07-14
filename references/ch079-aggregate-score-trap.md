# Section 79: Anti-Patterns: The Aggregate Score Trap

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** RAG, aggregate score, aggregate score trap  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Overall quality can improve while important users, languages, tasks, or risk categories get
worse.

## Actions

- Do not create so many slices that every result becomes noise.
- Choose the ones that matter, then ensure they have enough sample size or targeted evidence.
- Define slice thresholds before the run.
- Use confidence intervals per slice, risk-weighted reporting, and minimum quality bars for groups where failure has high cost.

## Evidence to Produce

- Include protected classes when relevant, regulatory categories, high-value workflows, high-risk actions, and historically weak segments.
- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, aggregate score, aggregate score trap needed to reproduce work on Anti-Patterns: The Aggregate Score Trap.
- Report results for RAG, aggregate score, aggregate score trap by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Aggregate scores are useful for summaries, but they are dangerous when they hide slices. An AI system can look better overall and still regress for a critical group.
For example, a model upgrade may improve common English support questions while making Spanish account recovery worse. The average score rises while a real product risk grows.

The same trap appears when the aggregate score does not move at all. Two models can both score 8.2 overall while behaving very differently underneath. The new model might improve short factual answers, regress long multi-turn conversations, become safer on obvious harmful prompts, and become worse on subtle policy boundaries. The headline score says "same quality." The product reality says "different risk profile."

The aggregate score trap is a version of Simpson's paradox in quality work. The blended metric can point one direction while important subgroups point another.
AI systems are especially vulnerable because behavior varies across language, region, domain, prompt style, device, user expertise, policy category, risk level, and data availability.
A release report should show the aggregate only after the important slices are visible. If a high-risk slice fails its minimum threshold, the average should not wash it away.
Slices should be chosen based on product reality, not only convenience. Include protected classes when relevant, regulatory categories, high-value workflows, high-risk actions, and historically weak segments.
When comparing models, also report churn: which slices improved, which slices regressed, which failure modes changed, and whether the new behavior is operationally acceptable. A model swap is not neutral just because the average score is unchanged.
Do not create so many slices that every result becomes noise. Choose the ones that matter, then ensure they have enough sample size or targeted evidence.
The mistake I see teams make is treating the average user as if that person actually exists.

## Expert Notes

Define slice thresholds before the run. Use confidence intervals per slice, risk-weighted reporting, and minimum quality bars for groups where failure has high cost.

Expert teams also compare the shape of quality, not only the level. For every model, prompt, retriever, or policy change, report a slice-delta table: unchanged aggregate score, improved slices, regressed slices, changed failure modes, and operational risks introduced by the churn. Churn is evidence. It tells the team whether the new system is merely different, safely better, or quietly risky.
