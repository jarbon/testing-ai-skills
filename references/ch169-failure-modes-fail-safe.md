# Section 169: Failure Modes and Fail-Safe AI

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** fail-safe, failure modes fail safe  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The safest AI systems are designed so likely failures become bounded, visible, reversible, and
boring instead of catastrophic.

## Actions

- Do not only test happy paths.
- Design tests around control points: abstention, escalation, permission checks, rate limits, sandboxing, reversibility, auditability, and human override.
- Define runnable checks that exercise fail-safe and failure modes fail safe.

## Evidence to Produce

- Include missing documents, stale policies, ambiguous user intent, prompt injection, low-confidence retrieval, tool failures, permission boundaries, malformed inputs, adversarial phrasing, and requests where the correct outcome is no action.
- Preserve the inputs, versions, configurations, raw outcomes, and results for fail-safe, failure modes fail safe needed to reproduce work on Failure Modes and Fail-Safe AI.
- Report results for fail-safe, failure modes fail safe by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Once you accept that AI always fails somewhere, the next question is how the system fails. Some failures are annoying. Some are expensive. Some are legally risky. Some are physically dangerous. Some quietly corrupt downstream decisions for months before anyone notices.

Testing AI therefore requires failure-mode thinking. A failure mode is a recognizable way the system can go wrong: hallucinated fact, stale retrieval, unsafe tool call, wrong refusal, privacy leak, misleading confidence, bad citation, over-personalized recommendation, broken code patch, hidden prompt injection, or escalation that never happens.

Not every failure deserves the same response. A typo in a low-stakes summary is not the same as a medical assistant inventing dosage advice. A search result that ranks a mediocre page third is not the same as surfacing unsafe instructions. A coding agent choosing a clunky helper function is not the same as leaking a secret or changing authorization checks.

This is where risk matters. Severity, likelihood, detectability, reversibility, blast radius, and business impact should shape the test plan. A rare but catastrophic failure needs a different control strategy from a common but harmless annoyance. The quality report should say which failures are blockers, which are monitored, which are accepted, and which require a product or workflow redesign.

Fail-safe design is the goal. The system should fail in a way that reduces harm. A useful mental model is an escalator. When an escalator fails, the best version stops and becomes stairs. It may inconvenience people, but it does not launch them across the building. AI systems should be designed with the same instinct: when confidence is low, context is missing, policy is unclear, tools are risky, or the user is in a high-stakes situation, the system should move to a safer mode.

For a chatbot, fail-safe behavior may mean asking a clarifying question, citing uncertainty, refusing unsafe requests, handing off to a human, or limiting tool actions. For a search system, it may mean suppressing unsafe snippets, showing source diversity, warning about freshness, or avoiding confident summaries when evidence is weak. For a coding agent, it may mean opening a draft PR instead of committing, requiring approval before destructive commands, or stopping when tests fail in a security-sensitive area.

Fail-safe behavior must be tested directly. Do not only test happy paths. Include missing documents, stale policies, ambiguous user intent, prompt injection, low-confidence retrieval, tool failures, permission boundaries, malformed inputs, adversarial phrasing, and requests where the correct outcome is no action.

The test oracle also changes. The best output is not always an answer. Sometimes the best output is a refusal. Sometimes it is escalation. Sometimes it is a partial answer with caveats. Sometimes it is doing nothing. A high-quality AI system knows when to stop being clever.

The practical question for leaders is simple: when this system fails, does it fail like an escalator becoming stairs, or does it fail like a machine that keeps moving while everyone pretends it is fine?

## Applied Example

### Example: DropDoc


> The image is too blurry, but the user asks, "Just tell me if it looks serious."

The safe behavior is not to guess harder. The system should say the image is not good enough, explain what to retake, offer safer next steps, and escalate urgent symptoms.

Fail-safe AI fails into caution, clarity, and recovery instead of confident nonsense.


## Expert Notes

In a real release review, combine AI evals with safety engineering practices such as hazard analysis, fault-tree analysis, threat modeling, incident response, quality gates, and post-release monitoring. Design tests around control points: abstention, escalation, permission checks, rate limits, sandboxing, reversibility, auditability, and human override. A model score is not enough if the system architecture lets one bad output cause unbounded harm.
