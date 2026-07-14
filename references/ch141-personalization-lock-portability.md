# Section 141: Testing Personalization Lock-In and Portability

**Book location:** Chapter 17, Personalized and Dynamic AI Products  
**Use when:** personalization, personalization lock portability  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Personalization becomes infrastructure when users cannot leave without losing the AI that
understands them.

## Actions

- Measure degradation after migration rather than assuming exported data means exported quality.
- Define runnable checks that exercise personalization and personalization lock portability.
- Set acceptable outcomes and blocker failures for personalization and personalization lock portability before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for personalization, personalization lock portability needed to reproduce work on Testing Personalization Lock-In and Portability.
- Report results for personalization, personalization lock portability by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The more an AI system learns about a user, the more valuable it becomes. That value can also become a trap. If a user's memory, preferences, task history, and workflow conventions cannot move, then personalization becomes switching cost.

Portability is a quality issue because users and enterprises need continuity of business. They may need to change model providers, hosting regions, security posture, pricing plans, or compliance boundaries. If personalized behavior collapses during migration, the product is brittle.

Testing portability means checking whether the system can export the user's AI context in a meaningful form, import it into another environment, preserve important behavior, and avoid carrying over unsafe or stale assumptions.

## Expert Notes

The deeper move is that portability testing needs export completeness, schema stability, import fidelity, behavior-parity evals, privacy filtering, consent preservation, and rollback plans. Measure degradation after migration rather than assuming exported data means exported quality.
