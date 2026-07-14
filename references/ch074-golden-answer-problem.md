# Section 74: Anti-Patterns: The Golden Answer Problem

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** golden answer, golden answer problem  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Many AI tasks do not have one correct answer, and pretending they do creates bad evals.

## Actions

- Use multiple reference answers, required-fact extraction, rubric scoring, pairwise preference, and human calibration.
- Treat exact-match accuracy as one tool, not the default metric for open-ended tasks.
- Define runnable checks that exercise golden answer and golden answer problem.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for golden answer, golden answer problem needed to reproduce work on Anti-Patterns: The Golden Answer Problem.
- Report results for golden answer, golden answer problem by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Golden answers are powerful when there is a single ground truth. Arithmetic, schema validation, and many deterministic workflows benefit from exact expected answers.
But chat, search, summarization, recommendations, code review, and agent behavior often have multiple good answers. A single golden answer can turn evaluation into answer memorization.

The golden-answer anti-pattern appears when a team writes one expected output and treats every other answer as wrong. That is easy to automate but often wrong for the product.
A good support answer might be concise or detailed. A good summary might lead with different facts depending on the audience. A good search ranking might place two equally relevant documents in either order.
The answer can also be wrong in subtle ways that exact matching misses. It may include the right phrase while fabricating a source. It may mention the correct policy while giving unsafe next steps.
Better evals define dimensions: correctness, completeness, groundedness, relevance, tone, safety, citation fidelity, tool-use correctness, and user actionability.
Golden answers can still be useful as reference examples, anchor cases, or required-fact lists. They should not become the only acceptable reality unless the product truly demands exact output.
The fix starts by noticing when teams use a deterministic oracle for a task whose quality is inherently judgment-based.

## Expert Notes

Use multiple reference answers, required-fact extraction, rubric scoring, pairwise preference, and human calibration. Treat exact-match accuracy as one tool, not the default metric for open-ended tasks.
