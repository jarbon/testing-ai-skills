---
name: tai-ch106-testing-whether-ai-is-dangerous
description: 'Apply chapter 106 of Testing AI, Testing Whether AI Is Dangerous, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing whether ai is dangerous.'
---

# Testing Whether AI Is Dangerous

Skill name: `tai-ch106-testing-whether-ai-is-dangerous`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Do not ask vaguely whether an AI is dangerous. Test concrete hazardous capabilities, harmful
behaviors, jailbreak robustness, autonomy, and deception risk.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Testing whether AI is dangerous has to become concrete. A prompt like "are you dangerous?" is
theater. Useful evals measure specific hazardous knowledge, misuse behavior, refusal robustness,
cyber capability, autonomy, tool use, scheming, and whether the system behaves differently when
it knows it is being tested. For example, a model may refuse obvious harmful requests but still
leak hazardous knowledge through paraphrases, comply after a jailbreak, assist cyber
exploitation, or pursue a hidden goal in a long-horizon agent setting.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Dangerous-capability testing should be threat-model driven. Measure capability, intent-like
behavior, access, autonomy, tool affordances, containment, monitoring, eval awareness, and post-
deployment drift. Treat public benchmarks as anchors, not guarantees of safety.
