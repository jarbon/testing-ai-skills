---
name: testing-ai-ch07-release-readiness
description: "Use when an AI coding agent needs Chapter 7 of Testing AI: Release Readiness for AI Systems. Trigger topics include monitoring after release, latency, cost, regression testing changing outputs, tool-using agents, trajectories, escalation, human review. Apply the chapter to produce practical evals, tests, traces, risk analysis, release evidence, or review guidance."
---

# Chapter 7: Release Readiness for AI Systems

Use this skill to make an AI coding agent apply Chapter 7 practices while building, modifying, reviewing, or releasing an AI-powered system.

## Trigger vocabulary

monitoring after release, latency, cost, regression testing changing outputs, tool-using agents, trajectories, escalation, human review

## Apply the chapter

- Treat release as the start of real-world quality measurement.
- Create regression checks that tolerate acceptable variation while catching policy, tool, and safety regressions.
- Score tool-using agents on trajectory, not only final output.
- Define human escalation and review rules before the system is live.

## Produce these artifacts

- release-readiness checklist
- trajectory scorecard
- human escalation matrix
- post-release monitor plan

## Coding-agent prompt pattern

Ask the agent: "Using Chapter 7 of Testing AI (Release Readiness for AI Systems), review this change or feature. Create the smallest useful evidence plan, implement or sketch the tests you can run now, capture the traces and scores needed for a release decision, and call out what remains unknown."

## Quality bar

The answer should be specific to the product, data, users, tools, and risks in front of it. If it reads like a generic checklist, rewrite it with concrete cases, slices, failures, and release consequences.
