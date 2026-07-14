# Section 192: Testing AI Review Loops with Coding Agents

**Book location:** Chapter 9, Generated Code Changes the Job  
**Use when:** review loops coding agents  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A coding agent should not be the only judge of its own work. Use AI-assisted review loops to add
fast, skeptical, evidence-oriented checking close to the development workflow.

## Actions

- Use AI-assisted review loops to add fast, skeptical, evidence-oriented checking close to the development workflow.
- Define when they run, what targets they cover, which findings block release, how reports are stored, how fixes are verified, and where human review is required.
- Version the review prompt, save the evidence, and periodically compare the reviewer against human findings so the loop itself does not quietly drift.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for review loops coding agents needed to reproduce work on Testing AI Review Loops with Coding Agents.
- Report results for review loops coding agents by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

When an AI coding agent builds something, the first pass often looks convincing. The code compiles. The page loads. The document reads smoothly. The answer sounds confident. But AI-generated work can still contain broken flows, weak edge-case handling, misleading copy, accessibility problems, missing tests, stale assumptions, privacy leaks, and risky changes.

The useful pattern is separation of roles. One agent can build. Another reviewer, prompt, rubric, or tool can inspect. A developer or responsible owner then decides what evidence is strong enough to trust. That loop is healthier than asking the same builder to reassure itself that the work is good.

For code, an AI-assisted review loop should check both static and live behavior when possible. Static review catches suspicious diffs, missing tests, bad assumptions, risky dependencies, and security mistakes. Live review catches what code review often misses: broken flows, confusing interactions, layout problems, inaccessible controls, slow paths, and user-visible roughness.

For documents, the review loop should look for clarity, structure, unsupported claims, contradiction, missing audience context, weak examples, dated claims, and places where an artifact sounds polished but fails its job.

For URLs and product flows, the review loop can act like a small swarm of skeptical users. It should exercise paths the developer did not think about and report concrete findings instead of a generic "looks good."

Good review-loop prompts are specific. Name the target, the audience, the risk, and the evidence expected. "Review the signup flow for mobile usability, privacy copy, error states, and account-recovery risk" is better than "does this look fine?" "Review this eval report for missing slices, weak rubrics, and unearned release confidence" is better than "check my eval."

The output should be decision-oriented. A useful review report says what was inspected, what was found, how severe each finding is, what evidence supports it, and what next action would reduce risk. It should create work that a developer can act on without a meeting.

An AI-assisted review loop is not magic and should not replace domain evals, unit tests, security review, human judgment, or production monitoring. Its value is speed, skepticism, and forcing the builder to confront evidence outside the first draft.

## Applied Example

### Example: BugPilot


> Agent A writes the patch. Agent B reviews it. Agent C decides whether the review is right.

That sounds robust until all three agents share the same blind spot. The eval should include independent tools, procedural checks, human spot review, and cases where the correct answer is "no code change."

Recursive AI review adds confidence only when the layers fail differently.


## Expert Notes

The deeper move is to make AI-assisted review loops part of the development contract. Define when they run, what targets they cover, which findings block release, how reports are stored, how fixes are verified, and where human review is required.

The point is not to worship the reviewer. The point is to create an independent quality loop close enough to the coding agent that it actually gets used. Version the review prompt, save the evidence, and periodically compare the reviewer against human findings so the loop itself does not quietly drift.
