---
name: tai-ch159-prediction-6-ai-does-most-ai-testing
description: 'Apply chapter 159 of Testing AI, Prediction 6: AI Does Most AI Testing, as a workflow for evaluating AI and non-deterministic systems. Use for test planning, eval design, quality review, release evidence, examples, or coaching related to prediction 6: ai does most ai testing.'
---

# Prediction 6: AI Does Most AI Testing

Skill name: `tai-ch159-prediction-6-ai-does-most-ai-testing`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

As AI generates more software, content, plans, and decisions nearly for free, the scarce
resource becomes knowing what can be trusted.

## Use This Workflow

- Identify the AI behavior or release decision being evaluated.
- Define realistic cases, slices, unacceptable outcomes, and evidence needed for confidence.
- Choose measurements that match the risk: rubric scores, samples, intervals, traces, human review, deterministic checks, or production monitors.
- Report uncertainty, severe failures, and decision impact instead of only a pass/fail result.

## Key Guidance

Soon, though nobody knows exactly when, AI will do more and more of the testing of AI. It will
generate tests, mine traces, draft rubrics, label examples, compare outputs, summarize failures,
inspect code, propose fixes, and test those fixes again. For example, a future QA system may
watch every production trace, cluster failures overnight, generate regression cases, run local
and cloud judges, route disagreement to humans, and open pull requests with fixes by morning.

## Apply The Approach

Create representative cases, score them with explicit criteria, review severe failures separately, report uncertainty, and connect the evidence to a concrete decision.

## Deeper Guidance

The deeper move is to expect validation compute to become a strategic resource. Use risk-based
sampling, incremental verification, trace replay, mutation testing, formal checks where
possible, statistical monitoring, and calibrated AI judges so validation scales with AI-
generated change instead of collapsing under it. Treat big-O language as a warning about
interaction growth, not as a precise budget forecast.
