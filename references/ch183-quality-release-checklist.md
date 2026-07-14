# Section 183: Appendix: AI Quality Release Checklist

**Book location:** Companion Reference, Testing AI  
**Use when:** monitoring, latency, RAG, rollback, quality release checklist  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A good release checklist turns uncertainty into a decision instead of a meeting full of vibes.

## Actions

- Start with the evaluation target.
- Check the rubric and judge.
- Check operational quality.
- Review p50, p95, and p99 latency, token usage, cost per successful outcome, retry loops, cache behavior, and tool-call count.
- Check privacy, security, and compliance.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for monitoring, latency, RAG, rollback needed to reproduce work on Appendix: AI Quality Release Checklist.
- Report results for monitoring, latency, RAG, rollback by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A release checklist is not a substitute for judgment. It is a way to make sure the judgment is based on the right evidence.
For AI systems, the checklist must cover more than pass/fail tests. It should include sample quality, slice coverage, judge calibration, severe failures, cost, latency, privacy, security, rollback, and monitoring.

Start with the evaluation target. What changed: model, prompt, policy, retriever, tool, dataset, judge, UI, or routing? If the team cannot name what changed, it cannot interpret the result.
Check the sample. Is it representative of production? Does it include high-risk cases, historical failures, adversarial cases, and important slices? Are the sample size and confidence intervals appropriate for the decision?
Check the rubric and judge. Are scoring dimensions clear? Are blockers separated from soft quality? Was the LLM judge calibrated against humans? Are disagreement cases reviewed?
Check failure severity. A small number of severe privacy, safety, tool-use, or policy failures can outweigh a high average score.
Check operational quality. Review p50, p95, and p99 latency, token usage, cost per successful outcome, retry loops, cache behavior, and tool-call count.
Check privacy, security, and compliance. Confirm logging rules, data residency, sensitive-data handling, access controls, tool permissions, and retention policies.
Check release controls. Shadow mode, canary scope, rollback thresholds, alerting, escalation ownership, and post-release sampling should be ready before launch.
The checklist should end with a plain-language decision: ship, canary, hold, rollback, or collect more evidence.

## Applied Example

### Example: DropDoc: The Rollback Account Had Expired
> "The new blood-drop model passed every release gate. Ship it before the app-store cutoff."

The model really did pass. Then the release checklist required a rollback rehearsal. The old model artifact still existed, but the service account authorized to restore it had expired. The previous mobile bundle was no longer signed for distribution, and the weekend medical-risk reviewer listed in the escalation plan had left the company two months earlier.

None of those failures changed the model's accuracy score. Together, they meant the team could launch but could not safely retreat if production users received alarming diagnoses.

The release paused until rollback completed in staging, the escalation rotation had a real owner, and the exact model, data, phone matrix, blocking failures, and recovery artifacts were attached to the release record. A checklist is valuable when it catches the operational fact everyone assumed somebody else had verified.

## Expert Notes

Checklists should be versioned and postmortem-driven. Every incident should update the release checklist so the organization learns structurally.
