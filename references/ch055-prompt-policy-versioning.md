# Section 55: Prompt and Policy Versioning

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** rubric, retrieval, policy versioning, prompt policy versioning  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Many AI regressions come from changing the instructions around the model, not the model itself.

## Actions

- Version the system prompt.
- Version policy documents and retrieval indexes.
- Version tools and tool schemas.
- Version judges and rubrics.
- Version data and labels.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for rubric, retrieval, policy versioning, prompt policy versioning needed to reproduce work on Prompt and Policy Versioning.
- Report results for rubric, retrieval, policy versioning, prompt policy versioning by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI system behavior depends on prompts, system messages, policies, tools, retrieval indexes, judges, rubrics, parsers, and model versions. If those are not versioned together, teams cannot explain why quality changed.
For example, a support bot may regress because the refund policy changed, the retriever index was rebuilt, or the judge rubric was edited. The model version may be identical.

Version the system prompt. Small edits to tone, priority, refusal wording, or tool instructions can cause large behavior changes.
Version policy documents and retrieval indexes. A RAG system using yesterday's policy should not be compared casually against one using today's policy.
Version tools and tool schemas. If a tool gains a parameter, changes an enum, or returns a different error shape, agent behavior changes.
Version judges and rubrics. A score change may come from the evaluator changing its standard, not the product improving or regressing.
Version data and labels. If the eval set or label corrections changed, trend lines need annotation.
A release report should state the full evaluation bundle: model, prompt, policy, tool schema, retriever, index snapshot, judge, rubric, dataset, labels, and scoring code.
Do not edit prompts directly in production without provenance. Prompt management is release management.
Versioning earns its keep when the team can compare runs honestly and roll back the right thing when quality moves.

## From the Field: When the Blacklist Became the Product

When I was the test manager for automation on Chrome, I was working from a Starbucks on a Sunday and saw CNN reporting that the internet seemed to be down. That sounded wrong, so I did what testers do: I tried quick repros. It was not the whole internet. It was specific behavior in Chrome and related Safe Browsing-style warning paths, and only some versions and clients were affected. The rest of the team was already investigating that morning in parallel too, but the lesson stuck with me.

The broad public incident around that period was a Google malware blacklist problem: a `/` entry was accidentally checked into the malware site list after being pulled from a public blacklist source, and that entry expanded to match essentially every URL. For a short window, essentially every search result looked dangerous. The executable was not the interesting part. The detection idea was not the interesting part. The data file was the behavior. A rule, blacklist, policy, or configuration file changed what users experienced as dramatically as a code release.

That is exactly the AI versioning lesson. In modern AI systems, the "blacklist" might be an LLM safety policy, a system prompt, a retrieval index, a tool-permission rule, a model router, a guardrail configuration, or a judge rubric. People call those things data or config because they are not compiled code. Users do not care. If the behavior changes, the product changed.

So test these artifacts like code. Validate their syntax and semantics before rollout. Include malformed-entry, root-path, wildcard, delimiter, and encoding cases. Canary them with real traffic slices. Reject malformed updates. Keep near-instant rollback. Log exactly which policy, prompt, index, tool schema, and rule bundle produced each answer. The most dangerous regression may come from the file everyone thought was "just data."

Source: [The Guardian: Google blacklists entire internet](https://www.theguardian.com/technology/2009/jan/31/google-blacklist-internet)

## Expert Notes

At scale, treat prompts, policies, retrieval snapshots, tool contracts, judges, rubrics, datasets, and labels as a single versioned eval bundle. Comparisons across incompatible bundles should be marked as non-equivalent.
