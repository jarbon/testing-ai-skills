# Section 13: Reproducibility: Logging the Right Things

**Book location:** Chapter 2, From Tests to Release Evidence  
**Use when:** reproducibility, confidence engineer, reproducibility logging right things  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Non-deterministic bugs are hard to debug unless Confidence Engineers capture the context around
the failure.

## Actions

- Save the repo commit, branch, dependency lockfile, OS image, browser version, environment variables, test seed, exact command, failing output, screenshots, tool calls, files inspected, model version, prompt template, and diff.
- Define runnable checks that exercise reproducibility, confidence engineer, and reproducibility logging right things.
- Set acceptable outcomes and blocker failures for reproducibility, confidence engineer, and reproducibility logging right things before running the evaluation.

## Evidence to Produce

- Save the repo commit, branch, dependency lockfile, OS image, browser version, environment variables, test seed, exact command, failing output, screenshots, tool calls, files inspected, model version, prompt template, and diff.
- Preserve the inputs, versions, configurations, raw outcomes, and results for reproducibility, confidence engineer, reproducibility logging right things needed to reproduce work on Reproducibility: Logging the Right Things.
- Report results for reproducibility, confidence engineer, reproducibility logging right things by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Reproducibility in non-deterministic systems is less about forcing the exact same output and more about preserving enough context to explain and investigate the failure.
For example, an LLM failure may depend on model version, retrieved documents, tool outputs, prompt configuration, temperature, timestamp, or feature flags.

Non-deterministic failures can be frustrating because they may not reproduce on demand. A Confidence Engineer sees a bad output. An engineer tries the same input and gets a good output. Without logs, the team is left guessing.

That is why reproducibility starts with capturing context.

For LLM systems, the important context includes the user input, system prompt, developer prompt, model name, model version, temperature, seed if available, retrieved documents, tool calls, tool outputs, timestamps, feature flags, configuration, final output, judge score, and judge explanation.

Each item helps answer a different question. The prompt shows what instructions the model received. The model version shows whether behavior changed because of an upgrade. Retrieved documents show what evidence the model saw. Tool outputs show whether the model acted on bad data. The judge explanation shows why the output was considered a failure.

For distributed systems, context may include request IDs, event IDs, service versions, timing, retries, cache state, region, feature flags, and dependency responses. The goal is the same: reconstruct the conditions around the failure.

Perfect reproduction is not always possible. Even with all the logs, an LLM may not produce the exact same answer again. That is normal. When exact replay is unavailable, preserve enough evidence to make the failure explainable, diagnosable, and testable again.

Good logs also improve evaluation quality. If a judge gives a low score, the team can inspect the input, output, policy context, and explanation. If a failure becomes part of the golden set, the captured context helps preserve the lesson.

Without logs, failures become arguments. The Confidence Engineer says it failed. The developer cannot reproduce it. The team debates whether it was real. With logs, failures become evidence.

For non-deterministic systems, logging is not an afterthought. It is part of the test design. If you cannot replay or explain the conditions around a failure, you can barely debug it.

## From the Field: Clean Machines Lie

When I work on AI-powered browser automation now, the system is a chain of small decisions. One model decides what matters on the page. Another step may need high precision because it is about to click a destructive control. Another may need high recall because it is trying to find every plausible target. Then the system learns from attempts: if the first click failed but the second click worked, maybe it should remember the element, the selector, the page shape, or the trick that made the second attempt succeed.

That learning is useful. It is also state.

The next run is not the same as the first run if the system carries memory, cached observations, prior failures, user-specific hints, or a longer context window. A tiny piece of remembered state can change the next output dramatically. Sometimes that is the product getting smarter. Sometimes it is the product becoming impossible to reproduce.

I learned the same lesson the old-fashioned way on Chrome. A lot of browser testing happened on clean machines. Fresh install. Empty cache. No weird cookies. No extensions. No long-lived profile. Those tests were valuable, but they were not the real world.

So I brought in crowdsource testers to run Chrome against real machines in the wild. Real browser profiles. Real history. Real bookmarks. Real cookies. Real caches. Real regional networks. We found bugs the clean lab never saw. One memorable class was large sites that failed only when an old cached login script or cookie state interacted with a new Chrome build. On a clean machine, the site looked fine. On a real user's machine, it could become a blank page.

The AI lesson is simple: test with a clean slate, then test with dirty state. For agents and AI products, dirty state includes user memory, previous failed attempts, cached tool results, prior context windows, retrieved documents, learned UI hints, personalization, cookies, feature flags, and production data. State is not just setup. State is one of the sources of non-determinism.

## Examples

### Example: BugPilot


> "The login test failed once on CI. Please fix it."

If BugPilot changes the code, the reviewer needs more than a confident summary. Save the repo commit, branch, dependency lockfile, OS image, browser version, environment variables, test seed, exact command, failing output, screenshots, tool calls, files inspected, model version, prompt template, and diff.

Without that evidence, the team cannot tell whether the agent fixed a race condition, papered over a timeout, ran against a different browser, or never reproduced the failure at all.

The reproduction question is not, "Can the agent explain what happened?" It is, "Can another engineer replay the evidence trail and see the same failure mode?"


## Expert Notes

Expert logging distinguishes replay data from diagnosis data. Replay data tries to recreate conditions. Diagnosis data explains why the system behaved that way. Both should be privacy-aware, access-controlled, and tied to durable artifact IDs.
