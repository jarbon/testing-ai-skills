---
name: testing-ai-ch18-embodied-long-running
description: "Use when an AI coding agent needs Chapter 18 of Testing AI: Embodied and Long-Running AI Systems. Trigger topics include robotics, humanoid robots, simulation, virtual worlds, recovery, physical safety, swarms, long-running agents, human-in-the-loop remote operators. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 18: Embodied and Long-Running AI Systems

Use this skill to make an AI coding agent apply Chapter 18 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

robotics, humanoid robots, simulation, virtual worlds, recovery, physical safety, swarms, long-running agents, human-in-the-loop remote operators

## Apply the chapter

- Prefer simulation and virtual worlds for speed, safety, and cost, then validate critical cases physically.
- Test embodied AI for do-no-harm defaults, safe inaction, recovery, permissions, sensor fusion, and physical boundaries.
- Run long-duration simulations for memory drift, goal drift, retry loops, cost growth, and delayed failures.
- Include remote human operators, privacy, household/factory memory, and multi-agent negotiation in the test surface.

## Produce these artifacts

- robotics safety cases
- simulation plan
- long-run test schedule
- remote-operator privacy review
- multi-agent handoff test

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 18 of Testing AI (Embodied and Long-Running AI Systems), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
