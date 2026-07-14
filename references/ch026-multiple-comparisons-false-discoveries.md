# Section 26: Multiple Comparisons and False Discoveries

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** multiple comparisons, multiple comparisons false discoveries  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The more slices, variants, and metrics you inspect, the more likely one lucky result will look
real.

## Actions

- Run one test and that risk may be acceptable.
- Run a hundred tests and the chance that at least one looks significant by luck can become large.
- Use holdout sets, preregistered primary metrics, adjusted thresholds, or false-discovery-rate methods when many comparisons are part of the process.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for multiple comparisons, multiple comparisons false discoveries needed to reproduce work on Multiple Comparisons and False Discoveries.
- Report results for multiple comparisons, multiple comparisons false discoveries by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

Multiple comparisons are the statistics version of repeatedly rolling dice and only remembering the lucky roll. If you look at enough variants, slices, and metrics, something will appear impressive by chance.

The math can get formal, but the practical warning is plain: the more places you searched for a win, the less you should trust the one shiny win you found unless you confirm it on fresh evidence.


## Overview

Multiple comparisons are a trap in AI evaluation. If you compare many prompts, many models, many categories, and many metrics, some result will look impressive by chance.

For example, testing twenty prompt variants and picking the one with the best p-value is not the same as proving that variant is truly best. You may have selected noise.

The problem is simple. Every statistical test has some chance of producing a false positive. Run one test and that risk may be acceptable. Run a hundred tests and the chance that at least one looks significant by luck can become large.

The arithmetic is blunt. If 100 independent null comparisons each use p < 0.05 as the discovery threshold, the chance that at least one produces a false positive is `1 - 0.95^100`, or about 99.4%. That does not mean every dashboard win is fake. It means the more places you look, the more you need holdouts, correction methods, or a clean confirmation run.

AI teams do this constantly. They compare many prompt rewrites, many temperatures, many model versions, many judge prompts, many query slices, and many category breakdowns. Then they celebrate the best-looking result without accounting for how many chances they gave luck to win.

I saw a search-flavored version of this at Bing. If you keep running similar ranker experiments through a noisy relevance system and only remember the best high-water mark, someone will eventually look brilliant by accident. The mistake is not that they explored. Exploration is good. The mistake is treating the best result from many repeated looks as if it came from one clean planned comparison.

This also happens in dashboards. One category turns green, one metric improves, one segment looks great, and the team treats it as a discovery. But if the team inspected dozens of cuts, the one shiny result may not mean much.

The fix is not to stop exploring. Exploration is useful. The fix is to label exploration as exploration and confirm important discoveries with a fresh holdout set or a planned test.

For release decisions, predefine the primary metric and key segments. Secondary metrics can provide color, but they should not silently become the main evidence after the run.

Teams can also use correction methods or false-discovery controls when many formal comparisons are unavoidable. The practical lesson is even simpler: the more you looked, the less impressed you should be by the single best thing you found.

## High-Stakes Examples

### Example: BugPilot

> Find the best BugPilot configuration for fixing flaky Playwright tests in our checkout repo.

The team tries 200 combinations: five prompts, four models, three tool-permission profiles, four retry policies, and a few judge rubrics. One configuration scores 91% on the eval. The current production setup scores 84%. Everyone wants to celebrate the seven-point jump.

That jump may be real. It may also be the configuration that got lucky.

This is the multiple-comparisons trap. If you try enough combinations, one will often look unusually good by chance, especially when the eval set is small, the tasks are noisy, and the judge has variance. The more knobs the team turns, the more suspicious the best score should become.

Before promoting the winner, ask for evidence that survives the search:

- Was the winning configuration chosen before the test, or discovered after 199 other tries?
- Does it still win on a fresh holdout set the team did not tune against?
- Does it improve the same task slices, or only one noisy cluster?
- Does it reduce flaky-test fixes by deleting or weakening tests?
- Does it increase cost, latency, tool calls, or risky file edits?
- Does it still win when the eval is rerun several times?

The release decision should not be based on the best number found during exploration. It should be based on a clean confirmation run, with the candidate frozen, the eval set held out, and the tradeoffs visible.

The regression question is not whether BugPilot can produce one heroic score. It is whether the apparent improvement survives a fair test after the search is over.

## Expert Notes

Separate exploratory analysis, confirmatory analysis, and monitoring. Use holdout sets, preregistered primary metrics, adjusted thresholds, or false-discovery-rate methods when many comparisons are part of the process. When a dashboard contains dozens of segments, report how many comparisons were inspected and which ones were planned before the run.
