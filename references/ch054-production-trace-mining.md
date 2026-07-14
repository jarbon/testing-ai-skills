# Section 54: Production Trace Mining

**Book location:** Chapter 8, Operating AI: Observability, Relevance, and Economics  
**Use when:** trace, production trace, production trace mining  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

The strongest eval sets are often hiding inside production logs.

## Actions

- Start with privacy and governance.
- Choose cases that represent important user behavior, high risk, new failure modes, or recurring regressions.
- Keep raw traces separate from sanitized eval cases.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for trace, production trace, production trace mining needed to reproduce work on Production Trace Mining.
- Report results for trace, production trace, production trace mining by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Production trace mining turns real interactions into better tests. It samples live conversations, clusters failures, anonymizes sensitive data, labels important examples, and promotes high-value cases into eval and regression suites.
For example, a chatbot may pass launch tests and then fail in production because users ask in ways the team never imagined. Trace mining turns those surprises into durable quality assets.

Start with privacy and governance. Production logs can contain personal data, secrets, account details, medical-style text, internal policy, and proprietary workflows. Decide what can be stored, redacted, sampled, and reviewed.
Sample broadly, then target deeply. Random samples estimate ordinary quality. Targeted samples find unresolved conversations, escalations, low ratings, long sessions, retries, refusals, and high-cost traces.
Cluster similar failures. A hundred bad conversations may collapse into five root causes: missing document, bad tool call, ambiguous policy, unsafe refusal, or context-window overflow.
Label traces at the right level. Sometimes the answer is wrong. Sometimes the retrieval was wrong. Sometimes the tool call was wrong. Sometimes the system recovered well after an error.
Promote examples deliberately. Not every production trace belongs in the golden set. Choose cases that represent important user behavior, high risk, new failure modes, or recurring regressions.
Keep raw traces separate from sanitized eval cases. The eval should contain enough context to reproduce the behavior without leaking data unnecessarily.
Trace mining should be continuous. As users adapt, policies change, and models update, the eval set should learn from the product.
This is where AI quality becomes operational. The product teaches the tests, and the tests protect the product.

## From the Field: Feedback Is Not a Metric

At Google, I worked on a project that let users highlight something on a page and send feedback with the surrounding context. The idea was simple and, from a quality point of view, obviously useful: if a user can point directly at the broken thing, the team gets a much better signal than a vague complaint.

The tool worked. One team tried it. Then the idea moved up the review chain, and the response was not what young quality-me expected. The concern was not only whether the feedback could be collected. The concern was what happened after that. Once you ask users for feedback, somebody has to read it, triage it, answer it, and decide what to do when users ask for things the product cannot or should not provide.

Search made that lesson especially sharp. A site owner may sincerely believe their page should rank first. A user may be frustrated that the answer they wanted was not on top. Some of that feedback is real product signal. Some of it is self-interest. Some of it is anecdote. Some of it is noise. If you optimize a large ranking system from individual complaints, you can make the whole system worse while feeling very responsive.

The AI lesson is not "ignore users." It is "treat feedback as evidence, not as the metric." Cluster it, sample it, compare it with production traces, logs, evals, slices, and severe-failure reports. Use it to discover blind spots in the eval system. Do not let one loud anecdote rewrite the model.

## From the Field: The Indexer Stopped in the Dark

When I worked on Google Desktop Search, one of the worst production problems was not a crash, a relevance bug, or a bad new feature. It was quieter than that. Some users reported that indexing just stopped. New files would not show up. The product still opened. Searches still returned results. It just stopped learning about the user's current machine.

That kind of bug is difficult in production because the failure can look like absence. There was no dramatic error screen, no obvious stack trace, and not enough production signal to know how often it happened or why. We could guess. Maybe the disk was full. Maybe an index file was corrupted. Maybe a write failed. Maybe a background process got wedged. We tried local reproductions, including deliberately corrupting files and forcing edge conditions, and found some paths that could explain it. But the bigger lesson was that we did not have enough privacy-safe instrumentation to see the shape of the problem in the wild.

That tension matters. Desktop search is privacy-sensitive. You cannot casually collect a user's filenames, document contents, or local search behavior just because it would make debugging easier. But if you collect too little health signal, the product can fail silently and the team can be left arguing from anecdotes.

AI systems have the same problem, only bigger. A retriever can stop refreshing documents. A memory system can stop writing. A tool can silently fail and return stale state. A personalization layer can get stuck. A model can keep answering fluently while the underlying system has stopped learning from the world.

The lesson is to design privacy-safe health traces before you need them. Log counts, ages, failure classes, redacted state transitions, freshness, queue depth, retries, corruption detection, and user-visible recovery paths. Do not wait for users to tell you the system feels stale. If the product learns, indexes, remembers, retrieves, or adapts, the trace should prove that those loops are still alive.

## Expert Notes

Production trace mining should track sampling frame, redaction method, cluster stability, label confidence, recurrence rate, severity, business impact, and whether promoted cases reduce future incident classes.
