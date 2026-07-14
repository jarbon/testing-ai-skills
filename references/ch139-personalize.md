# Section 139: Testing When Not to Personalize

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** personalization, personalize  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The best personalized system knows when user preference should not control the answer.

## Actions

- Measure both personalization lift and personalization harm.
- Define runnable checks that exercise personalization and personalize.
- Set acceptable outcomes and blocker failures for personalization and personalize before running the evaluation.

## Evidence to Produce

- Include preference-reversal tests, counterfactual profiles, safety and authority thresholds, exploration requirements, and protected domains where personalization must be limited.
- Preserve the inputs, versions, configurations, raw outcomes, and results for personalization, personalize needed to reproduce work on Testing When Not to Personalize.
- Report results for personalization, personalize by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Personalization is useful when user context improves the outcome. It becomes dangerous when preference is confused with truth, safety, fairness, or public interest. A user may prefer fast answers, familiar sources, optimistic advice, or a narrow viewpoint. The system still needs to decide when accuracy, freshness, diversity, legality, and safety matter more.

This is where many personalization systems fail. They optimize for what the user previously clicked, bought, praised, or tolerated. But past behavior is not the same as current need. A person who usually reads sports news may still need emergency information. A person who likes short answers may still need a complete warning. A developer who prefers one framework may still need the repository's existing architecture.

Testing should include "do not personalize" cases as first-class eval cases, not edge cases discovered after harm occurs.

## Expert Notes

At scale, define a personalization override policy. Include preference-reversal tests, counterfactual profiles, safety and authority thresholds, exploration requirements, and protected domains where personalization must be limited. Measure both personalization lift and personalization harm.
