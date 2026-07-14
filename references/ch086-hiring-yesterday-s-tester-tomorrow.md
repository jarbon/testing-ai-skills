# Section 86: Anti-Patterns: Hiring Yesterday's Tester for Tomorrow's Systems

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** hiring yesterday s tester tomorrow  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality teams need people who can build evidence systems, not just execute inherited test
rituals.

## Actions

- Define runnable checks that exercise hiring yesterday s tester tomorrow.
- Set acceptable outcomes and blocker failures for hiring yesterday s tester tomorrow before running the evaluation.
- Run representative cases for hiring yesterday s tester tomorrow and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for hiring yesterday s tester tomorrow needed to reproduce work on Anti-Patterns: Hiring Yesterday's Tester for Tomorrow's Systems.
- Report results for hiring yesterday s tester tomorrow by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Many teams respond to AI risk by adding more traditional QA capacity. That can help for deterministic product surfaces, but it does not solve the core AI quality problem.
Tomorrow's systems require people who can combine testing intuition with statistics, coding, product judgment, AI tooling, data sense, and safety thinking.

Hiring for old rituals creates predictable gaps. The team gets more test cases, more checklists, and more bug tickets, but not necessarily better understanding of model behavior.
AI quality work asks different questions. How much variance is normal? Which samples are representative? Which failures are severe? Which judge can be trusted? What changed in the retriever? Which slice regressed? What evidence supports launch?
The people doing this work need enough coding skill to build harnesses and inspect traces. They need enough statistics to avoid fooling themselves. They need enough AI fluency to use agents and judges effectively. They need enough skepticism to challenge AI-generated answers.
They also need great communication skills. AI quality reports are decision artifacts. The best evaluator can explain uncertainty to product, engineering, legal, safety, and executives without hiding behind jargon.
A team built only around manual checking or brittle automation will move too slowly and miss the important risks.
The tempting shortcut is assuming the future of quality can be staffed by scaling the past.

## Expert Notes

The deeper move is to staff AI quality as a hybrid discipline: quality engineering, data evaluation, AI tooling, risk analysis, automation, and product judgment. This is a leverage role, not a checkbox role.
