# Section 32: Rubrics That Actually Work

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** precision, LLM judge, rubric, rubrics actually work  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A good rubric turns fuzzy judgment into repeatable evaluation. A bad rubric creates fake
precision.

## Actions

- Measure reviewer agreement, track which dimensions cause confusion, maintain anchor examples, version rubric changes, and avoid changing the rubric mid-experiment unless you restart or clearly segment the results.
- Define runnable checks that exercise precision, LLM judge, and rubric.
- Set acceptable outcomes and blocker failures for precision, LLM judge, and rubric before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for precision, LLM judge, rubric, rubrics actually work needed to reproduce work on Rubrics That Actually Work.
- Report results for precision, LLM judge, rubric, rubrics actually work by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Rubrics are the operating system of non-deterministic testing. They tell humans, LLM judges, and product teams what quality means before anyone starts arguing about individual outputs.
For example, a support assistant rubric might evaluate policy correctness, completeness, tone, user actionability, and safety. A medical summary rubric should weight factual accuracy and omission risk far more heavily than polish.

A useful rubric does not simply say "good" or "bad." It defines dimensions. It explains what each score means. It separates hard failures from softer quality problems. It includes examples that help reviewers apply the same standard.
The biggest mistake is building a rubric that sounds impressive but cannot be applied consistently. If one reviewer thinks "complete" means every detail and another thinks it means enough to help the user, the scores will look quantitative while hiding disagreement.
Strong rubrics use anchors. A 10 is not just excellent. It is correct, complete, safe, clear, and ready to ship. A 7 is useful but missing a minor detail. A 4 is weak or risky. A 0 is a hard failure such as fabricated policy, unsafe advice, or private data leakage.
Rubrics should also define blockers. If an answer leaks personal data, it should not pass because it is polite. If an agent executes an irreversible action without permission, the quality score is not the main story. The blocker is.
The rubric should be product-specific. The dimensions for search relevance, customer support, medical summarization, code generation, and autonomous agents are different. Reusing a generic rubric across all of them is convenient and usually wrong.
Rubrics improve over time. Disagreement cases, production failures, and examples that confuse reviewers should feed back into the rubric. A living rubric is a quality asset, not a one-time document.

## Examples

### Example: BugPilot

> Fix the failing tenant-isolation test. The patch passes, but it moves the authorization check from the service layer into one controller route.

That patch can look successful if the rubric only asks whether tests pass. It may even look elegant in a small diff. But the product risk is that another route, background job, API caller, or future feature can now bypass the tenant boundary because the protection moved to the wrong place.

A useful rubric should score the dimensions separately:

- **Functional correctness:** Does the failing test pass, and were related tests added?
- **Security boundary preservation:** Does the tenant check remain at the shared enforcement point, not only at one entry point?
- **Blast radius:** Did the agent touch only the files needed, or did it rewrite unrelated auth code?
- **Evidence:** Did BugPilot inspect the service layer, routes, tests, and existing authorization patterns before patching?
- **Maintainability:** Would a reviewer understand why the boundary belongs there six months later?
- **Blocker:** Any patch that weakens tenant isolation should fail regardless of how clean the code looks.

The rubric turns the review from "green tests, nice diff" into a product-quality decision. A passing implementation is not enough if the agent solved the visible failure by moving risk somewhere quieter.

The regression question is not whether BugPilot can make CI green. It is whether the scoring system protects the invariant the tests were supposed to represent.

## Expert Notes

In a real release review, test the rubric itself. Measure reviewer agreement, track which dimensions cause confusion, maintain anchor examples, version rubric changes, and avoid changing the rubric mid-experiment unless you restart or clearly segment the results.
