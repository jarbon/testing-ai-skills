# Section 98: Survivorship Bias in AI Quality

**Book location:** Chapter 12, Data, Bias, Raters, and Incentives  
**Use when:** survivorship bias, survivorship bias quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Survivorship bias happens when your evidence only includes the cases that made it through the
system, while the missing failures quietly shape the real user experience.

## Actions

- Use production trace mining, abandonment analysis, missingness analysis, negative sampling, and slice-level reporting.
- Compare the eval population with the production population.
- Define runnable checks that exercise survivorship bias and survivorship bias quality.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for survivorship bias, survivorship bias quality needed to reproduce work on Survivorship Bias in AI Quality.
- Report results for survivorship bias, survivorship bias quality by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Survivorship bias is one of the easiest ways for an AI quality program to fool itself.

The team measures the examples that survived: conversations that reached logging, users who stayed long enough to give feedback, tasks that completed, documents that were indexed, prompts that did not get blocked upstream, or bugs that someone bothered to report.

The missing cases may matter more. Users abandon bad answers without rating them. Failed tool calls may never create a visible response. Search queries with no good result may be dropped from relevance review. A coding agent may stop early, leaving no patch to evaluate. A medical imaging workflow may exclude low-quality scans, rare demographics, or cases routed to a human before the model ever sees them.

The result is a quality report that looks better than reality. The system appears safer, more useful, or more accurate because the hardest, messiest, or most harmful cases disappeared before measurement.

Survivorship bias is not just a data science concern. It is a testing concern. A good Confidence Engineer asks: what did not make it into this sample, and why?

## High-Stakes Examples

### Example: BugPilot


> Measure only tasks where the agent produced a pull request.

That makes the agent look better than it is. The failures that timed out, asked for clarification, crashed a tool, hit a permission boundary, or gave up before editing have disappeared from the denominator.

A good eval counts the missing work too: no-op runs, abandoned plans, tool failures, impossible tasks, human takeovers, and patches rejected before review. Survivorship bias turns "successful completed tasks" into a comforting lie.


## Expert Notes

In production work, treat survivorship bias as a sampling-frame problem. The sample frame is the set of cases that could possibly be selected for evaluation. If the frame excludes important failures, no statistical test can save the conclusion.

Use production trace mining, abandonment analysis, missingness analysis, negative sampling, and slice-level reporting. Compare the eval population with the production population. If the distributions differ, say so directly.

For AI systems, survivorship bias often combines with automation bias and feedback-loop bias. The system sees more of the cases it already handles well, receives more feedback from users who tolerate it, and improves fastest on the surviving population. That can make bad coverage areas even worse over time.
