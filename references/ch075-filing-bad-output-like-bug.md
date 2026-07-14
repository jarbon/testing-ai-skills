# Section 75: Anti-Patterns: Filing Every Bad Output Like a Bug

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** filing bad output like bug  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

One bad AI output is usually evidence of a behavior pattern, not a single defect with a surgical
fix.

## Actions

- Define runnable checks that exercise filing bad output like bug.
- Set acceptable outcomes and blocker failures for filing bad output like bug before running the evaluation.
- Run representative cases for filing bad output like bug and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for filing bad output like bug needed to reproduce work on Anti-Patterns: Filing Every Bad Output Like a Bug.
- Report results for filing bad output like bug by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

In deterministic software, a bug report often points to a fixable defect. Click this button, see this crash, patch this code path.
AI failures are different. One bad output may be a sample from a broader probability distribution. Fixing that one output can move the distribution and create new failures somewhere else.

This does not mean bad outputs should be ignored. It means they should be filed with the right mental model. The failure is evidence. The question is what larger behavior it represents.
A single hallucinated answer might point to a retrieval gap, a weak refusal policy, a vague prompt, a model limitation, a missing tool contract, or a poorly calibrated judge. Filing it as "the model said X" is not enough.
The team may not be able to fix that exact output without harming neighboring behavior. A prompt patch can reduce one failure and increase over-refusal. Fine-tuning can suppress one pattern and introduce another. Retrieval changes can improve one topic and degrade another.
Better issue reports describe failure family, severity, affected slices, reproduction envelope, nearby examples, likely components, and suggested eval coverage. They ask whether the distribution improved after the fix.
The unit of work becomes the failure pattern, not the screenshot of one embarrassing answer.
The mistake I see teams make is treating probabilistic system behavior like a broken button.

## From the Field: Search Bugs That Went to Dev Null

At Bing, we had plenty of internal Microsoft feedback that looked like ordinary bug reports: "I searched for this X, and the results are wrong." Sometimes the report even included the order the person thought the results should have used. In a procedural product, that kind of report feels natural. Find the defect, patch the code path, close the bug.

AI-powered search did not work the way SQL full-text search did. One query is an anecdote, not a measurement. The internal Microsoft audience was also not the core Bing audience. A lot of real Bing users were older, did not change their default search engine, and some of them thought they were using Google. Smart engineers had strong opinions about search quality, but their taste was not the market.

The deeper problem was regression. If you tune the ranker, change the training data, or add a special rule to satisfy one internal complaint, you may improve that one query and quietly damage thousands of neighboring queries. You still have to evaluate the whole engine.

A clever person built a page where employees could enter a query, compare Bing and Google side by side, and choose which result set looked better. In theory, that could become pairwise preference data. In practice, it was mostly a pressure valve. People felt heard, but almost all of that anecdotal data effectively went to `/dev/null`.

The lesson is not that feedback is useless. The lesson is that feedback must be converted into samples, slices, preference tests, and reproducible eval cases before it deserves product weight. Do not spot-weld a model-backed system because one smart internal user hated one output.

## Expert Notes

AI issue tracking should include cluster id, slice, severity, sample count, confidence, regression cases, mitigation hypothesis, and post-fix distribution movement. The fix is not done when one example disappears.
