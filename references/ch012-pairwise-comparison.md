# Section 12: Pairwise Comparison

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** pairwise comparison  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When absolute scoring is hard, asking which output is better can produce useful evidence.

## Actions

- Review disagreement cases, especially when the judge chooses a fluent but factually weaker answer.
- Version B adds a deterministic fake clock and asserts that exactly three retries happen before the checkout flow gives up.
- Version A hides the timing problem and makes the suite slower.
- Version B explains the behavior and makes the test more stable.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for pairwise comparison needed to reproduce work on Pairwise Comparison.
- Report results for pairwise comparison by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Pairwise comparison asks which of two outputs is better. It is often easier and more reliable than asking for an absolute score, especially when quality is nuanced.
For example, reviewers may argue whether an answer is a 7 or 8, but agree that version B is clearer, safer, and more faithful than version A.

Sometimes it is easier to compare two outputs than to assign each one an exact score.

That is the idea behind pairwise comparison. You run the same input through two versions, such as an old prompt and a new prompt. Then a human or LLM judge decides which output is better according to the rubric: A, B, or tie.

After many cases, you calculate a win rate. For example, the new version may be preferred in 68% of cases, the old version in 21%, with 11% ties. That tells a clear story about preference.

Pairwise comparison is useful because absolute scoring can be difficult. Reviewers may disagree about whether an answer is a 7 or an 8. But they may agree that one answer is more correct, more complete, safer, or more useful than another.

This approach works well for prompt changes, model upgrades, ranking changes, summarization quality, writing quality, and assistant responses. It is especially helpful when the goal is to compare versions rather than certify an absolute level of quality.

The judge still needs a rubric. "Better" should not mean "longer" or "more confident." It should mean better according to product goals: more correct, more faithful, more helpful, safer, clearer, or more aligned with policy.

Bias control matters. Randomize whether the old or new output appears first. Hide version labels. Allow ties when neither output is clearly better. Review disagreement cases, especially when the judge chooses a fluent but factually weaker answer.

Pairwise comparison should not replace hard safety checks. A new answer may be better than the old one and still unacceptable. If both outputs violate policy, choosing the better one is not enough. The report should still track critical failures, failure rates, and category-level performance.

Used well, pairwise comparison gives Confidence Engineers another practical measurement tool. It helps answer the question teams often care about most: did this change make the product better than what we had before?

## Examples

### Example: BugPilot


> "Fix the flaky payment retry test."

Version A changes the test timeout from 5 seconds to 30 seconds. Version B adds a deterministic fake clock and asserts that exactly three retries happen before the checkout flow gives up.

Both versions may make CI green. Pairwise review asks which patch a human would rather ship, not merely which one passed. Version A hides the timing problem and makes the suite slower. Version B explains the behavior and makes the test more stable.

The pairwise question should be narrow:

- Which patch better preserves the product requirement?
- Which patch is easier to review?
- Which patch is less likely to hide a real regression?
- Which patch leaves better evidence for the next engineer?

The winner is not "the prettier answer." It is the patch a reviewer would trust more in production.


## Expert Notes

Blind the version labels, randomize side order, allow ties, and analyze win rate by category. Pairwise wins do not replace absolute gates because the better of two bad outputs can still be unacceptable.
