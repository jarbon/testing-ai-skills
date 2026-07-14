# Section 7: Metamorphic Testing

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** metamorphic testing, metamorphic  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When there is no single correct answer, builders can change the input and check whether
important relationships still hold.

## Actions

- Define runnable checks that exercise metamorphic testing and metamorphic.
- Set acceptable outcomes and blocker failures for metamorphic testing and metamorphic before running the evaluation.
- Run representative cases for metamorphic testing and metamorphic and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for metamorphic testing, metamorphic needed to reproduce work on Metamorphic Testing.
- Report results for metamorphic testing, metamorphic by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Metamorphic testing checks relationships between outputs instead of requiring one exact answer. It is especially useful when there are many acceptable outputs but some properties must remain stable.
For example, rewriting a user question should not change the underlying refund policy. Translating a prompt should not remove a safety constraint.

Metamorphic testing is one of the most useful techniques for non-deterministic systems.

The idea is simple. Instead of checking one exact output, you change the input in a controlled way and test whether the relationship between outputs still makes sense.

Consider a refund-policy assistant. The user asks, "Can I return shoes after 45 days?" The policy says returns are allowed within 30 days only. The assistant should explain that the return is outside the standard window.

Now paraphrase the input: "I bought shoes a month and a half ago. Can I send them back?" The wording changed, but the policy fact did not. The answer should still preserve the 30-day rule.

That is a metamorphic relationship. The output does not need to be identical. It does need to remain consistent on the property that matters.

This technique is powerful because many AI systems do not have one perfect expected answer. A summary can be phrased many ways. A search result list can vary. A recommendation engine can return different valid items. But important relationships should still hold.

For summarization, adding an irrelevant sentence to the source should not dramatically change the main summary. For ranking, adding a clearly worse candidate should not cause the best candidate to disappear from the top results. For classification, changing a customer's name should not change a risk classification unless name is a valid and intended signal.

Metamorphic testing can also expose brittleness. If small typos, paraphrases, or irrelevant details cause large changes in factual answers, the system may be unreliable. If translating a policy question into another language changes the business rule, the multilingual behavior needs attention.

Useful transformations include paraphrasing, changing names, adding irrelevant details, reordering facts, shortening or lengthening the prompt, translating the input, and introducing realistic typos. Each transformation should have a clear expectation. The builder should know which property should remain stable and which variation is acceptable.

The strength of metamorphic testing is that it lets Confidence Engineers evaluate consistency without requiring a single golden output. It is a natural fit for LLMs, recommendation systems, ranking systems, search, classifiers, and AI agents.

When exact answers are hard to define, test the relationships that must remain true.

## Examples

### Example: TunedSearch

> best open model for coding agents July 2026

Now rewrite the same intent several ways:

- "top open-source LLM for agentic coding this month"
- "best local model for AI coding agents right now"
- "which open weights model is strongest for tool-using coding agents"
- "best OSS coding model current leaderboard"

These queries should not return identical results, but they should preserve the same intent. TunedSearch should still understand that the user wants current evidence about open or local models for coding-agent work, not a generic list of popular chatbots.

A good metamorphic test checks what should stay stable across wording changes:

- Current model evidence should stay near the top.
- Coding-agent benchmarks should matter more than general chat vibes.
- The result should distinguish open weights, open source, hosted APIs, and local-running models.
- Old leaderboard posts should not outrank current primary sources.
- Sponsored or hype pages should not become the top answer just because the wording changed.
- The answer should keep uncertainty visible, because "best" depends on repo language, tool use, context length, speed, cost, and hardware.

The regression question is not whether every query returns the same ranked list. It is whether harmless wording changes preserve the user's real intent and the evidence standard.

## Expert Notes

Expert metamorphic suites define relation types explicitly: invariance, monotonicity, symmetry, subset consistency, ranking stability, or conservation of key facts. Each relation should have a clear oracle for what must remain true after transformation.
