# Section 153: Testing Social Issues with AI

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** manipulation, social issues  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

AI quality includes social consequences: trust, fairness, dependency, manipulation, labor
impact, power, and who gets harmed when the system is wrong.

## Actions

- Test representation and access.
- Test manipulation and dependency.
- Test group-level outcomes.
- Test for role displacement and deskilling where it matters.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for manipulation, social issues needed to reproduce work on Testing Social Issues with AI.
- Report results for manipulation, social issues by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Social issues with AI are not separate from quality. They shape whether the system is useful, fair, trustworthy, and acceptable in the real world.
For example, a hiring assistant, tutoring system, workplace monitor, companion bot, or benefits triage tool can produce technically fluent outputs while changing incentives, excluding groups, or shifting responsibility onto people with less power.

Test representation and access. Who is included in the data, who is missing, and who gets worse service because the system was built around a different default user?
Test power dynamics. A system used by an employer, school, insurer, government, or platform may affect people who cannot easily opt out.
Test manipulation and dependency. Personalized systems can become persuasive in ways users do not notice, especially when they remember preferences, fears, goals, and vulnerabilities.
Test contestability. Users need ways to challenge, correct, appeal, or escape AI decisions that affect them.
Test transparency. The system should make clear when AI is involved, what data it used, what it can and cannot do, and where human accountability remains.
Test group-level outcomes. Average satisfaction can hide harms to smaller populations or edge cases.
Test for role displacement and deskilling where it matters. If AI takes over judgment-heavy work, humans may lose the ability to supervise it well.
A serious quality program treats social harm as observable, measurable, and reportable.

## Expert Notes

In a real release review, social AI testing should combine bias testing, participatory review, segment-level metrics, harm taxonomies, appeal-path audits, longitudinal monitoring, privacy review, and governance decisions about where AI should not be used.
