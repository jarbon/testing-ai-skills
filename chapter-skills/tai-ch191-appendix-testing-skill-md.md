---
name: tai-ch191-appendix-testing-skill-md
description: 'Apply chapter 191 of Testing AI, Appendix: Testing SKILL.md, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to appendix: testing skill.md.'
---

# Appendix: Testing SKILL.md

Skill name: `tai-ch191-appendix-testing-skill-md`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A `SKILL.md` file is not just documentation. It is executable intent for an AI coding agent, so
it needs to be tested like product behavior.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Many AI coding environments now use skill files, instruction files, memory files, or project
guides to teach agents how to behave. A `SKILL.md` file can tell an agent how to use tools,
follow workflows, format outputs, avoid dangerous edits, run checks, or apply domain-specific
judgment.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

When the system matters, treat `SKILL.md` as versioned agent behavior. Track skill version,
trigger terms, tool dependencies, success criteria, conflicting instructions, and replay
results. A skill that cannot be evaluated is just a wish written in Markdown.
