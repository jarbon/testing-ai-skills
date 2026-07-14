---
name: testing-ai-book
description: Use when an AI coding agent should apply Jason Arbon's Testing AI book as a confidence-engineering operating manual for AI systems: eval design, sampling, scoring, traces, release gates, generated-code validation, security, bias, observability, governance, and production evidence.
---

# Testing AI Book Skill

Use this skill when you are building, testing, reviewing, or releasing an AI-powered product, AI coding-agent change, model workflow, RAG system, chatbot, generated-code patch, robotics feature, or dynamic/personalized AI system.

## Core stance

Do not ask whether one run looked good. Build evidence that the system is good enough, safe enough, observable enough, and reversible enough to ship.

## Agent workflow

1. Identify the product behavior, user value, failure cost, and release decision.
2. Replace brittle exact checks with criteria, rubrics, blockers, and examples of acceptable variation.
3. Build an eval set with risk slices, repeated runs, traces, and at least one deliberately hard or rare case.
4. Capture evidence: inputs, prompts, model and tool versions, retrieval context, tool calls, outputs, scores, reviewer notes, latency, cost, and failures.
5. Analyze distributions, confidence intervals, slice regressions, practical significance, and blocker failures.
6. Use human review or LLM judges only after the rubric and calibration examples are explicit.
7. Recommend ship, hold, rollback, sample more, or escalate, and explain what evidence would change the decision.

## Default output

Produce a concise confidence report with:

- Decision: ship, hold, canary, rollback, or investigate.
- What was tested: cases, slices, sample size, versions, and repeated-run settings.
- What changed: quality, safety, latency, cost, reliability, and important slice movement.
- Evidence: traces, rubric scores, confidence intervals, blocker failures, and examples.
- Risks: blind spots, untested surfaces, weak judge/rater agreement, and operational exposure.
- Next actions: fixes, extra evals, monitor thresholds, owner, and timeline.

## Guardrails

- Do not average away severe safety, privacy, security, medical, legal, or irreversible-action failures.
- Do not treat a p-value, leaderboard score, LLM judge, or one-run demo as permission to ship.
- Do not let the same AI that created the risky behavior be the only validator of that behavior.
- Keep the evidence close to the release decision: the question is not whether the AI is impressive, but whether this system should have power in its world.
