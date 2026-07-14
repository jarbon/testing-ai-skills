# Section 114: Testing LLM Training Data and AI Pollution

**Book location:** Chapter 15, How Models Work  
**Use when:** benchmark, synthetic data, llm training data pollution  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The model learns from the data it eats, including bad data, stale data, biased data, and
increasingly AI-generated data.

## Actions

- Define runnable checks that exercise benchmark, synthetic data, and llm training data pollution.
- Set acceptable outcomes and blocker failures for benchmark, synthetic data, and llm training data pollution before running the evaluation.
- Run representative cases for benchmark, synthetic data, and llm training data pollution and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for benchmark, synthetic data, llm training data pollution needed to reproduce work on Testing LLM Training Data and AI Pollution.
- Report results for benchmark, synthetic data, llm training data pollution by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

LLMs are trained on enormous mixtures of text, code, documents, conversations, and sometimes synthetic data. That scale creates power, but it also hides problems: private information, copyrighted material, toxic content, benchmark leakage, duplicates, outdated facts, language imbalance, and low-quality AI-generated content.

AI pollution is the growing problem of models training on outputs from earlier models. This can create feedback loops where language becomes smoother but less grounded, diversity shrinks, wrong claims repeat, and synthetic consensus looks like truth.

Testing training data directly is hard for closed models, but product teams can still test symptoms: memorization, benchmark contamination, stale knowledge, source imbalance, language quality gaps, and behavior that looks copied from common internet patterns instead of grounded evidence.

## From the Field: The Bug Database Wouldn't Learn

At one point, I had the same idea many engineers have when they see a large historical dataset: train a model on it and predict useful things. Chrome had a large open bug database, which made it tempting. I wanted to predict features such as whether a new bug would be fixed or rejected, who might fix it, how long it might take, and the eventual priority or severity.

So I wrote training loops and infrastructure against the bug data. It felt like the kind of thing that should work. There was a lot of data. The targets sounded practical. The payoff would be obvious if the model could learn the patterns.

Nothing converged.

Only after enough failed experiments did I step back and ask whether there was a stable pattern to learn in the first place. The answer was probably no. The labels were not clean truth. They were the exhaust of a messy human process. Triage rotated through different developers, testers, and PMs. The combinations of people changed. Priorities changed. One week might become a security push. Another might become a privacy push. Another might become a performance push. During those periods, bugs could be reprioritized in batches, assigned differently, fixed sooner, or ignored longer for reasons that were not really in the bug text.

That is the lesson: before training on historical data, ask whether the data represents a stable relationship or just a record of shifting human decisions. A big dataset can still be too noisy, too inconsistent, or too policy-dependent to learn from. Some problems are not impossible because the model is weak. They are impossible because the target keeps changing.

This also applies to eval data. If your labels come from rotating reviewers, changing policies, changing business priorities, and crisis-driven reprioritization, the model may learn the politics of the process instead of the quality concept you care about. Failed experiments are evidence too. They tell you where the world is not as learnable as the spreadsheet made it look.

## Expert Notes

In production work, test training-data risk through provenance audits, data cards, contamination checks, deduplication reports, benchmark-leakage probes, memorization tests, synthetic-data ratio tracking, and downstream slice evals. For closed models, treat these as vendor-risk questions and product-level stress tests.
