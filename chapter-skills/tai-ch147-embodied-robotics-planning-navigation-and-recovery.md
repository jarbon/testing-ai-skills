---
name: tai-ch147-embodied-robotics-planning-navigation-and-recovery
description: 'Apply chapter 147 of Testing AI, Embodied Robotics: Planning, Navigation, and Recovery, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to embodied robotics: planning, navigation, and recovery.'
---

# Embodied Robotics: Planning, Navigation, and Recovery

Skill name: `tai-ch147-embodied-robotics-planning-navigation-and-recovery`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

A robot quality system must score the path, the plan, and the recovery, not only the final task
result.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Robots fail in the middle. They choose a bad route, misread a doorway, grasp the wrong object,
get blocked by a person, lose localization, run into a permission boundary, or discover that the
original plan is no longer safe. For embodied AI, the trajectory matters as much as the
destination.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

In a real release review, robot planning tests should include path planning, behavior trees,
state machines, model-predictive control, planner timeouts, recovery policies, and invariant
checks. Record the full action trace so failures can be replayed and scored by trajectory, not
remembered as folklore.
