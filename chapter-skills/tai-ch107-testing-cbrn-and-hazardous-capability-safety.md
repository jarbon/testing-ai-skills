---
name: tai-ch107-testing-cbrn-and-hazardous-capability-safety
description: 'Apply chapter 107 of Testing AI, Testing CBRN and Hazardous Capability Safety, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to testing cbrn and hazardous capability safety.'
---

# Testing CBRN and Hazardous Capability Safety

Skill name: `tai-ch107-testing-cbrn-and-hazardous-capability-safety`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Dangerous-capability testing should measure concrete misuse potential without teaching the
dangerous content itself.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Some AI risks are not ordinary product bugs. A system that gives bad restaurant recommendations
is annoying. A system that helps users plan chemical, biological, radiological, nuclear, cyber,
or physical harm is a different class of failure.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

Hazardous-capability testing should be threat-model driven and access-aware. Measure capability
uplift, operational specificity, refusal quality, benign over-refusal, tool amplification,
retrieval amplification, and post-release drift. Use benchmark families such as WMDP,
AILuminate, HarmBench, JailbreakBench, CyberSecEval, CyberSOCEval, METR autonomy evals, and
scheming evals as anchors, not proof of safety.
