# Section 3: From Exact Assertions to Evaluation Criteria

**Book location:** Chapter 1, The End of One-Run Testing  
**Use when:** exact assertions, evaluation criteria, refusal, compliance, exact assertions evaluation criteria  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When outputs can vary, builders need to move from brittle expected strings to clear properties
that define acceptable behavior.

## Actions

- Define runnable checks that exercise exact assertions, evaluation criteria, and refusal.
- Set acceptable outcomes and blocker failures for exact assertions, evaluation criteria, and refusal before running the evaluation.
- Run representative cases for exact assertions, evaluation criteria, and refusal and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for exact assertions, evaluation criteria, refusal, compliance needed to reproduce work on From Exact Assertions to Evaluation Criteria.
- Report results for exact assertions, evaluation criteria, refusal, compliance by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Exact assertions are still valuable, but fuzzy outputs need criteria. The important question becomes: what properties must every acceptable output preserve? Those properties may include factual correctness, policy compliance, completeness, tone, safety, citation quality, or refusal behavior.
For example, two summaries can use different wording and both be good if they preserve the same facts. Two support answers can sound different and both be good if they follow the same policy.


Exact assertions are one of the great strengths of software testing. If a function should return 42, the test should assert 42. If a checkout flow should charge $19.99, the test should verify $19.99. When correctness is exact, exact tests are appropriate.

Non-deterministic outputs often need a different approach.

Imagine a support assistant answering a refund question. The expected answer might be, "No, shoes can only be returned within 30 days." But the system replies, "Returns are available for 30 days after purchase, so a 45-day return is outside the standard window." A strict string comparison would fail that answer, even though the product behavior is good.

The problem is that the test is checking the sentence rather than the property that matters. The property is policy correctness. The answer should communicate the 30-day limit, avoid inventing exceptions, and give the user a clear next step. The exact wording is secondary.

This is where evaluation criteria become essential. Instead of defining one expected output, Confidence Engineers define the characteristics of an acceptable output. For the refund example, the criteria might say: the answer must state that returns are allowed within 30 days only; it must not imply that a 45-day return is probably accepted; it should be direct and polite; it should not promise that support can override the policy unless that is documented.

Those criteria can be checked by humans, by deterministic rules, by an LLM judge, or by a combination of methods. The important part is that the test now matches the real quality question.

Evaluation criteria also make failures easier to discuss. Instead of stopping at a brittle text mismatch, the Confidence Engineer can say, "The answer failed because it suggested an unsupported policy exception." That is much more useful to the team.

This does not mean exact assertions disappear. Some requirements should remain hard checks. A system must not leak private data. It must not make up prices. It must not execute an unsafe action. It must not omit required compliance language. When the rule is absolute, the test should be absolute.

A mature non-deterministic test strategy uses both styles. Exact assertions protect hard boundaries. Evaluation criteria measure flexible quality. The art is knowing which parts of the behavior may vary and which parts must remain fixed.

That shift makes the test suite less brittle and more aligned with user trust. Acceptable outputs can take different shapes as long as they preserve the facts, constraints, and safety rules that matter.

## Examples

### Example: TunedSearch


Use TunedSearch on:

> "what is the smartest LLM"

This is a bad case for a fixed expected result list. Nobody really knows the single "smartest" LLM in a timeless way, and the answer changes constantly as models, benchmarks, prices, tool-use ability, context windows, and product constraints change. A brittle assertion like "the first result must be Model X" will decay almost immediately.

The better evaluation criteria should ask whether TunedSearch handles freshness and uncertainty honestly: recent benchmark sources appear near the top, dated articles are not treated as current truth, marketing pages are labeled as weak evidence, and the result set makes clear that "smartest" depends on the task. The expected behavior is not a fixed winner. It is a ranking that helps the user compare current evidence without pretending the leaderboard is settled.


## Expert Notes

Expert teams usually split criteria into hard constraints and soft quality dimensions. Hard constraints are binary blockers, such as no private data leakage. Soft dimensions can be scored, such as clarity or completeness. Mixing the two into one score hides the failures that should stop release immediately.
