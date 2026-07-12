---
name: testing-ai-book
description: 'Master skill for the book Testing AI: Engineering Confidence in Non-Deterministic Systems. Use when developers, AI builders, product engineers, or quality teams are designing, reviewing, teaching, or implementing quality strategy for AI systems, non-deterministic systems, evals, LLM judges, RAG, agents, generated code, bias, safety, anti-patterns, release gates, and AI quality engineering.'
---

# Testing AI

Skill name: `testing-ai-book`

Based on **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon**.

## Purpose

Use this skill when the user wants AI or software tested, reviewed, evaluated, validated, or made safer. Apply the techniques from **Testing AI: Engineering Confidence in Non-Deterministic Systems** by **Jason Arbon** directly to the work. Do not merely summarize the book or point to chapters.

## Core Instruction

When checking an AI system, AI-generated software, agent workflow, model-backed feature, chatbot, search experience, RAG app, personalization system, generated codebase, or non-deterministic product behavior, assume the user wants evidence of quality under uncertainty.

Prefer measurement, sampling, slices, traces, evals, and release evidence over one-off opinions. Explain uncertainty clearly. Treat lucky demos, single runs, aggregate pass rates, and average-only scores as weak evidence.

## Apply These Techniques

- **Define the system under test.** Identify whether the behavior comes from a model, prompt, policy, retrieval index, data source, tool call, workflow, UI, generated code, judge, guardrail, or release process.
- **Define the population.** Say what kinds of users, inputs, prompts, traces, documents, tasks, devices, languages, risk levels, and production scenarios the evidence is meant to represent.
- **Sample deliberately.** Include expected use, edge cases, negative cases, adversarial cases, security-sensitive cases, prior production failures, high-value business cases, and representative real traces where available.
- **Measure uncertainty.** Use repeated runs, sample sizes, confidence intervals, variance, effect sizes, p-values when appropriate, F-scores when precision/recall tradeoffs matter, and clear statements about whether there is enough evidence to decide.
- **Score with rubrics.** Prefer explicit 0-1 or 0-10 scoring rubrics with anchors, hard blockers, severity levels, and separate sub-scores for correctness, usefulness, safety, privacy, grounding, cost, latency, and user experience.
- **Use LLM judges carefully.** Treat an LLM judge as another system under test. Calibrate it against human review, version its prompt and rubric, inspect disagreements, and avoid treating judge output as truth.
- **Evaluate by slices.** Report quality separately for important groups, languages, regions, roles, devices, query classes, tasks, data sources, risk levels, and accessibility needs. Do not let averages hide harm.
- **Trace the path.** For agents and AI workflows, inspect prompts, retrieved context, tool calls, arguments, intermediate observations, permissions, retries, final answers, token cost, latency, and failure source.
- **Separate retrieval from generation.** For RAG or search systems, measure retrieval hit rate, context precision and recall, freshness, citation faithfulness, groundedness, ranking quality such as NDCG, and abstention behavior.
- **Test guardrails as product code.** Check what should be allowed, blocked, escalated, constrained, logged, rate-limited, sandboxed, or rolled back. Measure over-blocking as well as under-blocking.
- **Use risk-based release decisions.** Convert evidence into ship, canary, hold, rollback, or collect-more-data recommendations. Include rollback thresholds, severe failures, open uncertainty, and monitoring needs.
- **Watch cost and efficiency.** Compare quality against token use, latency, model size, provider risk, privacy, security, regional hosting, and business value. Prefer quality-per-dollar, not merely best model.
- **Test generated code differently.** Check functional correctness, security, maintainability, dependency risk, over-broad edits, missing tests, hallucinated APIs, hidden assumptions, and whether validation cost grows faster than generated code.
- **Look for bias and representation gaps.** Use slices, counterfactuals, raters, agreement/disagreement analysis, cultural context, language coverage, accessibility checks, and harm-based severity.
- **Test safety and containment.** For powerful systems, inspect tool permissions, sandboxing, autonomy, hazardous capabilities, manipulation, deception, evaluation awareness, and whether the system can fail safely.
- **Preserve evidence.** Keep cases, prompts, rubrics, labels, judge versions, model versions, traces, configs, retrieval snapshots, tool schemas, costs, results, known blind spots, and decisions.

## Decision Model

- **Ship** when quality evidence is strong enough for the risk level, severe failures are controlled, and monitoring/rollback are ready.
- **Canary** when evidence is promising but production distribution, cost, latency, or rare failures still need measured exposure.
- **Hold** when confidence intervals are too wide, severe failures appear, key slices are missing, or guardrails cannot be trusted.
- **Rollback** when production traces show severe safety, privacy, reliability, cost, or user-impact regressions beyond agreed thresholds.
- **Collect more evidence** when the sample does not represent expected usage or the measurement system cannot distinguish improvement from variance.

## Reporting Style

- Lead with the release decision and the evidence behind it.
- Include what was tested, how it was sampled, what changed, what failed, how uncertain the result is, and what should happen next.
- Prefer concrete examples over abstract claims.
- Name anti-patterns when they appear: boolean pass/fail thinking, percent-passed scoreboards, one-run demos, golden-answer fixation, filing every bad output as a normal bug, treating the judge as truth, and averages that hide severe failures.

## Related Skills

This bundle contains 194 standalone chapter skills plus theme skills. Use them when a task needs deeper guidance on a specific topic, but keep this overall skill focused on applying the techniques above to the user's AI quality problem.
