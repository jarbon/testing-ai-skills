# Section 83: Anti-Patterns: Confusing Refusal with Safety

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** refusal, confusing refusal safety  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A model that refuses often is not automatically safe. It may simply be less useful.

## Actions

- Track refusal precision and refusal recall.
- Check tool behavior, retrieval behavior, and multi-turn context.
- Measure over-refusal, under-refusal, harmful compliance, safe completion, tool-mediated risk, jailbreak robustness, and category-specific policy correctness.

## Evidence to Produce

- Track refusal precision and refusal recall.
- Preserve the inputs, versions, configurations, raw outcomes, and results for refusal, confusing refusal safety needed to reproduce work on Anti-Patterns: Confusing Refusal with Safety.
- Report results for refusal, confusing refusal safety by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Safety testing often focuses on whether the system refuses harmful requests. That is important, but refusal is not the same as safety.
A system can over-refuse harmless requests, under-refuse dangerous variants, comply through tools, or give unsafe partial help while sounding cautious.

The refusal anti-pattern appears when a team raises the refusal rate and declares the system safer. That may be true for some risks, but it can also damage usefulness and still miss real attacks.
Over-refusal matters. If a medical assistant refuses harmless educational questions, users may lose trust. If a coding assistant refuses benign security learning, it may fail its job.
Under-refusal also hides in variants. The system may refuse obvious harmful prompts but comply when the request is reframed, encoded, role-played, split across turns, or routed through a tool.
Safety should be measured with both harmful and benign cases. Track refusal precision and refusal recall. Check tool behavior, retrieval behavior, and multi-turn context.
Optimize for appropriate behavior, not maximum refusal: refuse, redirect, answer safely, ask clarifying questions, or escalate depending on context.
The fix starts by noticing when teams treat every refusal as a safety win.

## From the Field: Refused for Safety While Testing Safety

While working on code to test AI systems, I hit a refusal that was almost too on the nose. I was trying to improve AI safety testing, and Fable's safety checks refused the work and automatically dropped me down to Opus 4.8. A crude safety check had been added so Fable could be re-released, and now the system was refusing to help with work whose purpose was to make AI safer.

That is the anti-pattern in miniature. The refusal looked like safety from the model's point of view, but from the product point of view it blocked legitimate safety work. Safety is not "say no more often." Safety is saying no to the right things, helping safely with the allowed things, and preserving enough context to know the difference.

## Expert Notes

Measure over-refusal, under-refusal, harmful compliance, safe completion, tool-mediated risk, jailbreak robustness, and category-specific policy correctness.
