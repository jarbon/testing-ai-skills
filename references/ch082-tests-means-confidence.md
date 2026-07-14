# Section 82: Anti-Patterns: More Tests Means More Confidence

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** RAG, tests means confidence  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A larger eval can still be weak if it is redundant, biased, synthetic in the same way, or
disconnected from risk.

## Actions

- Test value comes from information gain.
- Measure marginal value of added cases.
- Define runnable checks that exercise RAG and tests means confidence.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for RAG, tests means confidence needed to reproduce work on Anti-Patterns: More Tests Means More Confidence.
- Report results for RAG, tests means confidence by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

More tests often help, but count alone is not coverage. Ten thousand easy, repetitive cases can provide less confidence than a smaller, well-designed suite.
For AI systems, the value of an eval depends on behavioral coverage, risk coverage, label quality, slice coverage, and production relevance.

The more-tests anti-pattern happens when teams increase case count and assume confidence rises automatically. It does not.
If the new tests are near-duplicates, they mostly reduce uncertainty about behavior the team already understood. If they are synthetic in the same style, they may create synthetic bias. If they miss high-risk slices, they inflate confidence where it is least needed.
Test value comes from information gain. A case is useful when it teaches the team something about an important behavior, boundary, risk, or population.
This is why coverage maps matter. Count cases by behavior, user journey, risk category, slice, failure mode, and production frequency. Then ask where uncertainty remains.
A good eval often combines representative samples, targeted edge cases, adversarial cases, production regressions, and known failure clusters.
The thing to watch for is buying confidence by the pound.

## Expert Notes

Measure marginal value of added cases. Prioritize cases that reduce uncertainty in high-risk areas, increase slice coverage, expose boundaries, or represent production frequency.
