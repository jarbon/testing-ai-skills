# Section 45: Benchmarking: Quality Is Relative Now

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** benchmark, benchmarking quality relative  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When absolute truth is hard to measure, relative quality can still tell you whether you are
competitive, broken, unusual, or missing something obvious.

## Actions

- Do not pretend the comparison is perfectly controlled.
- Report ranks, percentiles, confidence intervals when available, and qualitative gaps.
- Separate "competitors do this" from "users need this" and "regulators require this." Benchmarking is evidence, not authority.

## Evidence to Produce

- Report ranks, percentiles, confidence intervals when available, and qualitative gaps.
- Preserve the inputs, versions, configurations, raw outcomes, and results for benchmark, benchmarking quality relative needed to reproduce work on Benchmarking: Quality Is Relative Now.
- Report results for benchmark, benchmarking quality relative by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Benchmarking compares your AI system, workflow, page, answer, agent, or product behavior against similar systems. It does not prove that your system is good. It gives you a reference frame.

That reference frame matters because AI quality is often hard to judge in isolation. A sign-in page that loads in 4.2 seconds might sound merely "not ideal" until every competitor loads in under 1.5 seconds. A chatbot that resolves 72% of refund conversations might sound decent until similar products resolve 88%. A coding agent that needs twelve tool calls for a small change might sound acceptable until another agent consistently does it in four.

AI makes this kind of benchmarking practical in a way that used to be difficult or impossible. Large companies could barely test their own products deeply, let alone compare many competitor flows at scale. Now AI agents can inspect many similar pages, run similar tasks, evaluate responses, summarize differences, and identify missing affordances across a market.

Benchmarking is especially useful when your own evidence feels thin. One bug report may be anecdotal. One performance number may be hard to interpret. One page may look fine to the team that built it. But if twenty comparable products all show a password reset link, multi-factor sign-in recovery, visible support options, faster page load, clearer error messages, or better mobile layout, absence becomes evidence.

Think of benchmarking as measuring the structural fingerprint of a system. I sometimes call this the eigenvector of the UI: what elements tend to exist, where they tend to appear, which paths usually exist, and what users implicitly expect because the rest of the world trained them that way. The phrase is a little nerdy, but the idea is simple. You can detect missing things by comparing against the shape of similar things.

Benchmarking works for outputs too. Search engines can compare result freshness, source diversity, answer placement, snippets, and page speed against other search experiences. Chatbots can compare tone, escalation behavior, refund resolution, localization, and refusal quality. Coding agents can compare patch size, tool-call count, time to fix, tests run, security review, and whether the final diff is reviewable.

The warning is important: competitors are not truth. The market can converge on bad patterns. Every competitor may be inaccessible, insecure, manipulative, slow, or legally risky. Benchmarking should not replace domain judgment, user research, safety analysis, or direct measurement. It should add context.

Used well, benchmarking turns a lonely number into a business conversation. "Our page loads in 4.2 seconds" gets a nod. "We are slower than every competitor we measured" gets a roadmap.

## From the Field: Nothing Motivates Like a Competitor

At test.ai, we used AI to compare apps, sites, and workflows at a scale that would have been impossible by hand. One thing we learned quickly was that absolute quality numbers often did not motivate teams very much.

If you tell someone, "Your app is slow," they may agree politely. They may say, yes, performance matters. They may add it to a backlog. They may even mean it.

But if you show them their app side by side with competitors, the room changes. I remember a prospect team becoming very animated when we showed the performance difference between their dictionary app and other dictionary apps. Most dictionary apps loaded words on demand: search for words starting with A, and the A entries appear. This app had a different idea. It loaded the entire dictionary into the DOM first, then hid and revealed subsets of nodes.

You can guess which one was slower.

That was the power of the benchmark. The performance number was no longer abstract. It was visible, comparative, and embarrassing in the productive sense. The team could see that users were not merely waiting; they were waiting in a market where competing apps had taught them not to wait.

We did not close that deal. In a slightly painful twist, we had already given them the data. Their company decided this was the biggest problem to solve, gave the team several weeks to fix it, and then brought in outside help when the fix did not land. Last I heard, the problem still had not really been solved.

This is one of the best new tricks AI gives quality work. We can benchmark systems that used to be too expensive to compare. We can test our own product, competitors, adjacent products, and similarly structured flows. We can build evidence from the shape of the market, not just from the shape of our own test suite.

The lesson is not to copy competitors. The lesson is to learn from them. Relative quality is not the same as absolute quality, but it is often the thing that finally makes people care.

## Expert Notes

The deeper move is to make benchmark design explicit: define the peer set, task set, sampling frame, measurement method, normalizations, and known unfairness. Competitors may differ in traffic, geography, device mix, business model, legal obligations, data access, and product goals. Do not pretend the comparison is perfectly controlled.

Still, imperfect benchmarking can be useful if the limitations are visible. Report ranks, percentiles, confidence intervals when available, and qualitative gaps. Separate "competitors do this" from "users need this" and "regulators require this." Benchmarking is evidence, not authority.
