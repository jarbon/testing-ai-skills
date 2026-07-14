# Section 78: Anti-Patterns: The Static Test Plan

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** retrieval, static test plan  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A frozen test plan can look responsible while the AI system keeps changing underneath it.

## Actions

- Define runnable checks that exercise retrieval and static test plan.
- Set acceptable outcomes and blocker failures for retrieval and static test plan before running the evaluation.
- Run representative cases for retrieval and static test plan and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for retrieval, static test plan needed to reproduce work on Anti-Patterns: The Static Test Plan.
- Report results for retrieval, static test plan by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Traditional test plans often assume a relatively stable product surface. AI systems are less stable because prompts, models, policies, tools, retrieval indexes, user behavior, and data distributions change.
A static plan can become theater: detailed, polished, and no longer connected to the current risk.

The static-plan anti-pattern appears when a team writes a large plan once and treats it as quality coverage for months. Meanwhile the model changes, the policy changes, the retriever changes, and production users discover new paths.
A plan that does not absorb production failures is aging. A plan that does not version prompts and rubrics is incomplete. A plan that ignores new tools and data sources is stale.
AI testing needs living eval suites. The suite should grow from production traces, red-team discoveries, bug clusters, policy changes, customer escalations, and model upgrades.
This does not mean chaos. The plan should define stable principles: risk categories, quality dimensions, slice strategy, sampling rules, escalation criteria, and release thresholds.
The cases and rubrics should evolve deliberately, with versioning and notes about comparability.
The fix starts by noticing when documentation is treated as coverage after the system and risk have moved on.

## Expert Notes

The deeper move is to maintain a living quality system: versioned evals, changelogs, production trace mining, drift monitors, rubric updates, and explicit compatibility rules for trend comparisons.
