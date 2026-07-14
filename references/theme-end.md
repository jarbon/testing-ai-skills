# The End of One-Run Testing

**Book location:** Chapter 1  
**Use when:** behavior distributions, repeated runs, sampling, uncertainty, release confidence, determinism, personalization, makes non deterministic, exact assertions, evaluation criteria, refusal, compliance, exact assertions evaluation criteria, confidence engineer  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Define runnable checks that exercise behavior distributions, repeated runs, and sampling.
- Set acceptable outcomes and blocker failures for behavior distributions, repeated runs, and sampling before running the evaluation.
- Run representative cases for behavior distributions, repeated runs, and sampling and preserve the failures that would change the decision.
- Ask the same model to summarize a document ten times and you may get ten different summaries.
- Log the weather snapshot, store inventory, delivery promise, driver state, user location, model route, tool outputs, and policy version.
- Define runnable checks that exercise determinism, personalization, and makes non deterministic.
- Define runnable checks that exercise exact assertions, evaluation criteria, and refusal.
- Set acceptable outcomes and blocker failures for exact assertions, evaluation criteria, and refusal before running the evaluation.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [001 The Next Generation AI Builder Will Measure Uncertainty](ch001-measure-uncertainty.md)
- [002 What Makes a System Non-Deterministic?](ch002-makes-non-deterministic.md)
- [003 From Exact Assertions to Evaluation Criteria](ch003-exact-assertions-evaluation-criteria.md)
- [004 Scoring Quality from 0-10](ch004-scoring-quality-0-10.md)
- [005 Variance: Not All Differences Are Bugs](ch005-variance-differences-bugs.md)
- [006 Determinism](ch006-determinism.md)
