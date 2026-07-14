# Section 8: Golden Sets and Live Sampling

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** golden set, live sampling, golden sets live sampling  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Stable regression examples and fresh real-world samples solve different problems. Mature AI
testing needs both.

## Actions

- Use both, and let each one improve the other.
- Define runnable checks that exercise golden set, live sampling, and golden sets live sampling.
- Set acceptable outcomes and blocker failures for golden set, live sampling, and golden sets live sampling before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for golden set, live sampling, golden sets live sampling needed to reproduce work on Golden Sets and Live Sampling.
- Report results for golden set, live sampling, golden sets live sampling by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Golden sets and live sampling answer different questions. Golden sets preserve known important cases. Live sampling discovers what is happening now.
For example, a golden set might contain past policy failures, while live sampling captures this week's new user questions and emerging abuse patterns.

A golden set is a curated collection of important test cases. It usually includes known edge cases, previous failures, high-risk policy boundaries, common user questions, and examples reviewed by domain experts.

Golden sets are valuable because they preserve hard-won knowledge. When a model once failed a refund boundary, leaked a sensitive field, or misunderstood a legal disclaimer, that example should not disappear from the test strategy. It should become part of the regression suite.

But golden sets have a weakness. They can get stale. Products change. Policies change. Users change. Abuse patterns change. A test set that represented reality six months ago may slowly become less useful. A system can also overfit to a golden set, performing well on familiar examples while failing on fresh ones.

Live sampling addresses that weakness. It uses recent production-like inputs, current support conversations, new edge cases, and real user behavior. Live samples reveal what is happening now, not only what the team already knows to worry about.

The two approaches answer different questions. Golden sets ask, "Did we regress on important known cases?" Live sampling asks, "How are we doing on current reality?"

A mature testing strategy uses both. Before release, run the golden set to catch regressions. During evaluation, sample realistic new cases to estimate current quality. After release, keep sampling production behavior to detect drift. When live sampling finds an important new failure, add it back into the golden set.

This creates a learning loop. The golden set becomes the team's memory. Live sampling becomes the team's contact with reality.

For LLM systems, this is especially important because the product surface changes quickly. Users discover new ways to ask questions. Attackers discover new prompt injection patterns. Retrieval data changes. Model versions change. Static tests alone cannot keep up.

The practical rule is simple: golden sets catch regressions; live sampling catches drift. Use both, and let each one improve the other.

## Examples

### Example: TunedSearch


> "did OpenAI just change API pricing?"

This is a bad fit for a frozen-only golden set. The correct answer depends on when the query is run, which source is authoritative, whether pricing changed quietly in docs before a blog post, and whether third-party summaries are already stale.

Use the golden set for stable behavior:

- The top result should prefer official provider documentation over SEO summaries.
- The snippet should show date or version evidence when available.
- The answer should avoid inventing a price when the page does not clearly say one.
- Sponsored, scraped, or outdated pricing pages should not win.

Then use live sampling to catch what the golden set will miss:

- new model names
- sudden pricing changes
- temporary outages
- renamed product tiers
- fresh forum rumors
- fast-moving comparison pages

The regression question is not, "Did the engine return the same result as last month?" It is, "Did the engine still use the right evidence strategy when the world changed?"


## Expert Notes

Golden sets should be versioned, deduplicated, labeled by risk, and periodically refreshed. Live samples should preserve privacy and represent the current traffic mix instead of only the cases that are easiest to review.
