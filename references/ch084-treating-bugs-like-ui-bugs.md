# Section 84: Anti-Patterns: Treating AI Bugs Like UI Bugs

**Book location:** Chapter 10, Anti-Patterns That Create False Confidence  
**Use when:** retrieval, treating bugs like ui bugs  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Many AI failures do not have one screen, one selector, one line of code, or one obvious owner.

## Actions

- Define runnable checks that exercise retrieval and treating bugs like ui bugs.
- Set acceptable outcomes and blocker failures for retrieval and treating bugs like ui bugs before running the evaluation.
- Run representative cases for retrieval and treating bugs like ui bugs and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for retrieval, treating bugs like ui bugs needed to reproduce work on Anti-Patterns: Treating AI Bugs Like UI Bugs.
- Report results for retrieval, treating bugs like ui bugs by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

UI bugs usually have a location. A button overlaps, a form rejects valid input, a page crashes. The defect can often be assigned to one code path.
AI failures are often distributed across prompts, models, retrieval, tools, policies, labels, user context, logs, and release configuration.

The UI-bug anti-pattern appears when a team expects every AI failure to have a neat reproduction step and a single code fix. Some do. Many do not.
A hallucination might be caused by missing documents, ambiguous instructions, a judge that rewards confidence, a stale retrieval index, or a model limitation. A bad tool action might come from prompt wording, weak permissions, or a tool schema that permits unsafe arguments.
Issue reports need more context: prompt, model version, system message, retrieval results, tool trace, policy version, user segment, sampled frequency, and severity.
AI failures should often be analyzed like incidents. What happened? Who or what was affected? Which components contributed? What evidence suggests this is a pattern? What mitigation reduces recurrence without causing new harm?
Ownership may also be shared. Product owns policy. Engineering owns tools. Data owns retrieval content. Safety owns risk thresholds. Quality owns the evidence system.
The mistake I see teams make is forcing a distributed behavioral failure into a traditional UI-bug template.

## Expert Notes

At scale, use AI incident templates with reproduction envelope, trace artifacts, affected slices, suspected contributors, severity, mitigation options, and post-mitigation eval results.
