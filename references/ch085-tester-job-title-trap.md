# Section 85: Anti-Patterns: The Old Tester Job Title Trap

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** tester job title trap  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Tester, engineer, developer, product manager, QA analyst, SDET, test automation engineer, search
quality engineer, and related roles are often too small for the work AI quality now requires.

## Actions

- Define runnable checks that exercise tester job title trap.
- Set acceptable outcomes and blocker failures for tester job title trap before running the evaluation.
- Run representative cases for tester job title trap and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for tester job title trap needed to reproduce work on Anti-Patterns: The Old Tester Job Title Trap.
- Report results for tester job title trap by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

The old job titles came from a narrower world: write test cases, automate checks, file bugs, maintain scripts, report pass/fail.
AI systems need a broader role. The next-generation quality professional needs automation, basic statistics, math literacy, creativity, product sense, and the ability to use AI and coding agents to do the work of testing AI.

The bigger shift is that the old boundaries between developer, tester, automation engineer, release engineer, and production quality owner are collapsing. AI now writes code, edits systems, generates tests, proposes fixes, calls tools, and sometimes runs the workflow itself. That means many developer roles are becoming validation, quality, and testing roles whether they use those words or not.

The merged role is Confidence Engineering. The job is to gain confidence in the operational quality of code, services, workflows, agents, and products produced by and with AI. The point is not to protect an old title. The point is to build enough evidence to trust the system in the real world.

This is not an insult to testers or SDETs. It is a scope problem. The work has expanded beyond the title.
A person testing AI must design evals, sample production traces, calibrate LLM judges, analyze disagreement, build harnesses, understand confidence intervals, inspect model and retrieval behavior, and use AI tools to move faster.
Automation remains essential, but it is not enough. Writing scripts around brittle pass/fail checks is not the center of AI quality. Designing measurement systems is.
The role also requires creativity. The best AI failures are often not in the obvious happy path. They appear in weird user intent, edge cases, adversarial prompts, ambiguous policy boundaries, and cross-system interactions.
Most importantly, AI quality professionals must use AI themselves. Coding agents, LLM judges, local models, data-labeling tools, trace analysis, and eval frameworks should be part of the daily workflow.
The practical failure mode is hiring for yesterday's checklist and expecting tomorrow's quality system.

## Expert Notes

When the system matters, define the role around outcomes: measuring behavior under uncertainty, building eval infrastructure, using AI-assisted tooling, interpreting statistics, tracing production behavior, and guiding release decisions. The title should reflect that scope. Confidence Engineering is not a renamed QA department; it is the operating discipline for deciding whether AI-produced software and AI-powered services are good enough to trust.
