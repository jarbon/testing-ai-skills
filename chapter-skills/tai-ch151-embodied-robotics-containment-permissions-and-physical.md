---
name: tai-ch151-embodied-robotics-containment-permissions-and-physical
description: 'Apply chapter 151 of Testing AI, Embodied Robotics: Containment, Permissions, and Physical Fail-Safes, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to embodied robotics: containment, permissions, and physical fail-safes.'
---

# Embodied Robotics: Containment, Permissions, and Physical Fail-Safes

Skill name: `tai-ch151-embodied-robotics-containment-permissions-and-physical`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Physical AI needs layered control because model judgment is not a safety system by itself.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

A robot should not be trusted merely because it usually behaves well. Embodied AI needs
containment: physical limits, software permissions, geofences, force caps, speed caps, emergency
stops, approval gates, audit logs, and independent monitors. The more the system can move,
unlock, purchase, cut, heat, lift, drive, or touch, the more containment matters.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

At scale, use layered controls: model policy, tool schema validation, runtime monitors, physical
interlocks, independent safety controllers, access control, rate limits, geofencing, and
incident review. Containment should be testable without asking the model to explain why it feels
safe.
