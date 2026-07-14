# Section 185: Appendix: Templates for AI Quality Work

**Book location:** Companion Reference, Testing AI  
**Use when:** rubric, templates quality work  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Templates make AI quality repeatable without pretending every system has the same risks.

## Actions

- Define runnable checks that exercise rubric and templates quality work.
- Set acceptable outcomes and blocker failures for rubric and templates quality work before running the evaluation.
- Run representative cases for rubric and templates quality work and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for rubric, templates quality work needed to reproduce work on Appendix: Templates for AI Quality Work.
- Report results for rubric, templates quality work by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Templates help teams move faster. They also prevent common omissions. The trick is to use them as scaffolding, not bureaucracy.
The most useful templates are eval plans, rubrics, judge prompts, failure-pattern reports, release memos, and model-comparison tables.

An eval plan template should ask: what changed, what decision is needed, what population is being sampled, what risks matter, what slices are required, what metrics will be used, and what threshold changes the decision?
A rubric template should define dimensions, score anchors, hard blockers, examples, reviewer instructions, and version history.
An LLM judge prompt template should include the task, rubric, scoring scale, blocker rules, output format, examples, and instructions to cite evidence from the answer or trace.
A failure-pattern report should include cluster name, examples, affected slices, severity, suspected causes, reproduction envelope, proposed mitigation, regression cases, and post-fix measurement.
A release decision memo should include summary recommendation, key evidence, confidence, slices, severe failures, cost/latency tradeoffs, privacy/security notes, rollout plan, rollback thresholds, and open risks.
A model-comparison table should compare quality, severe failures, cost per successful task, latency, token use, privacy posture, regional hosting, vendor risk, operational complexity, and fallback options.
Templates should stay short enough that teams actually use them. A template that no one fills out is not governance. It is decoration.

## Applied Example

### Example: BugPilot: Five Definitions of Done
> "Fix the authorization bug before tonight's release."

BugPilot changes `authorize.ts`, adds a test, and reports success. The developer checks that the new test passes. The security reviewer checks that one exploit no longer works. The release manager checks that the pull request is green. Nobody records which tenant boundary must remain intact, which files the agent was allowed to edit, or what would block release.

The same patch receives three approvals built on three different definitions of done.

A one-page eval template would have forced the team to preserve the repo snapshot, state the authorization invariant, name forbidden side effects, identify the required security tests, record the human approval rule, and capture the final evidence. When the next reviewer asks why the patch was considered safe, the answer should be a case record, not five people's memories.

The template earns its keep by making the missing decision visible before the release, not by giving the team another form to complete afterward.

## Expert Notes

When the system matters, templates should be machine-readable where possible. Structured release records make it easier to audit, compare, automate, and mine past decisions.
