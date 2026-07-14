# Section 76: Anti-Patterns: The Whack-a-Mole Tuning Trap

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** retrieval, fine-tuning, whack mole tuning trap  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Prompt patches and fine-tunes can remove one visible failure while creating quieter failures
nearby.

## Actions

- Define runnable checks that exercise retrieval, fine-tuning, and whack mole tuning trap.
- Set acceptable outcomes and blocker failures for retrieval, fine-tuning, and whack mole tuning trap before running the evaluation.
- Run representative cases for retrieval, fine-tuning, and whack mole tuning trap and preserve the failures that would change the decision.

## Evidence to Produce

- Include the original failure, nearby cases, counterexamples, slices, and known regressions.
- Preserve the inputs, versions, configurations, raw outcomes, and results for retrieval, fine-tuning, whack mole tuning trap needed to reproduce work on Anti-Patterns: The Whack-a-Mole Tuning Trap.
- Report results for retrieval, fine-tuning, whack mole tuning trap by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Early AI teams often respond to a bad example by patching the prompt, adding a rule, changing retrieval, or fine-tuning the model to avoid that mistake.
That can work, but it can also become whack-a-mole. The embarrassing failure disappears, and new failures appear in adjacent categories, languages, tones, or tool paths.

The practical failure mode is optimizing for the example that just hurt. Humans are naturally drawn to the vivid failure in front of them. The system, however, is a network of tradeoffs.
Adding a stricter refusal instruction may reduce unsafe compliance but increase refusal of harmless requests. Adding a longer policy prompt may improve correctness but hurt latency or instruction following. Fine-tuning for one tone may weaken another.
The only responsible way to tune is to run the broader eval suite. Include the original failure, nearby cases, counterexamples, slices, and known regressions.
Teams should also track metrics that might move in the wrong direction: over-refusal, under-refusal, helpfulness, latency, cost, groundedness, and escalation rate.
A fix should be judged by distribution movement, not by whether the demo case now looks good.
The tempting shortcut is celebrating the disappearance of one bad output before checking what the patch damaged.

## Expert Notes

At scale, every tuning change should have a blast-radius eval: original failures, adjacent prompts, benign counterexamples, slice checks, cost and latency metrics, and holdout confirmation.
