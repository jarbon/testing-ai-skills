# Section 116: Useful and Useless LLM Bug Reports

**Book location:** Chapter 15, How Models Work  
**Use when:** retrieval, useful useless llm bug reports  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A single bad answer is a clue. It is rarely a complete LLM bug report.

## Actions

- Define runnable checks that exercise retrieval and useful useless llm bug reports.
- Set acceptable outcomes and blocker failures for retrieval and useful useless llm bug reports before running the evaluation.
- Run representative cases for retrieval and useful useless llm bug reports and preserve the failures that would change the decision.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for retrieval, useful useless llm bug reports needed to reproduce work on Useful and Useless LLM Bug Reports.
- Report results for retrieval, useful useless llm bug reports by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Traditional bug reports often assume deterministic software. Steps, expected result, actual result, and screenshot may be enough. LLMs are different. The same prompt may produce different outputs, and the root cause may live in the prompt, model version, retrieval context, tools, memory, safety layer, or product workflow.

Unhelpful LLM bug reports usually contain one surprising answer with no model version, no settings, no context, no frequency estimate, no severity, and no slice. Useful reports show that the failure is systematic, severe, reproducible enough to matter, or tied to a specific risk population.

File issues that can be measured, triaged, and fixed without chasing one-off randomness. That may or may not mean filing fewer of them.

## Designing Feedback Without Fooling Yourself

User feedback is valuable, but it is not automatically training data. A thumbs down, complaint, correction, refund request, abandoned session, or angry screenshot may be a clue. It is not necessarily a label.

Explicit feedback tells you what a user chose to report. Implicit feedback tells you what the user did: clicked, retried, edited, abandoned, escalated, copied, deleted, or came back later. Both are biased. Angry users report more than satisfied users. Power users report differently from new users. Internal employees may file bugs that reflect their own expertise rather than the product's real audience.

Design feedback as evidence intake:

- Capture the input, output, route, prompt version, model version, retrieval trace, tool calls, and user-visible state.
- Ask for lightweight user intent when possible: wrong fact, bad tone, missing source, unsafe action, too slow, not useful, or privacy concern.
- Sample feedback for human review instead of treating every report as truth.
- Separate product complaints from model failures, policy failures, missing data, stale retrieval, bad UI, latency, and expectation mismatch.
- Protect privacy. Feedback often contains the most sensitive user context because people paste exactly what went wrong.

The goal is not to ignore anecdotal feedback. The goal is to turn anecdotes into measurable failure classes. One complaint starts an investigation. A cluster of similar complaints becomes an eval slice, a monitor, a regression case, or a product decision.

## From the Field: The Thumbs-Downs Did Not Mean the Same Thing

While building AI systems that found software and website issues, I accumulated a useful-looking set of triage data. The AI reported possible bugs, and I collected feedback from partners, clients, users, and other people reviewing the results. They could mark a report as good or bad and explain why. I combined all of that feedback into one large dataset and used it to fine-tune a model through RLHF so it could become better at bug triage.

It seemed sensible. It was also one of those mistakes that reminds me there is always another layer of complexity when testing AI.

Some outputs from the tuned model made sense. Others were bizarre. When I inspected the preference data, I realized that a thumbs-down did not have one meaning. Some reviewers rejected legitimate bugs because they did not understand the technical issue well enough to explain it. Some were assigned only to functional testing, so they voted down security or privacy findings as out of scope even when those findings were important. Others rejected real but lower-priority bugs because they were preparing a short executive report and did not want a priority-two issue competing for attention that day.

The single label **bad bug** had silently collapsed several different questions:

- Is this a real defect?
- Does the reviewer understand it?
- Is it inside this reviewer's assigned scope?
- Is it important enough to address right now?
- Does it belong in this particular report for this particular audience?

Those are not interchangeable judgments. The same report could be a real security defect, outside a functional reviewer's scope, low priority for today's release, and still worth preserving. By mixing all those thumbs-downs together, I had asked the model to converge on preferences that contradicted one another.

I eventually trained the default triage model primarily on my own opinionated labels. That was not because my judgment was universal. It was because I needed a coherent baseline that reflected a point of view I understood, could explain, and was willing to stand behind. From there, individual users could personalize derivative models through their own thumbs-up and thumbs-down feedback without silently changing the behavior for everyone else.

Bug triage is contextual. The right decision depends on the product, reviewer, role, audience, release phase, current priorities, and moment in time. Preference data needs to preserve that context. Before feeding a rating into RLHF, ask what the rater actually judged. Otherwise the reward model may faithfully learn a contradiction that the dataset hid from you.

## Expert Notes

Convert individual failures into failure classes. A strong LLM bug report names the population, not just the example: "refund escalation hallucination in policy-missing chats" is more useful than "the bot said something wrong."
