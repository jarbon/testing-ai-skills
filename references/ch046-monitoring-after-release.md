# Section 46: Monitoring After Release

**Book location:** Chapter 7, Release Readiness for AI Systems  
**Use when:** monitoring, monitoring after release  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

For non-deterministic systems, launch is not the end of testing. It is the start of real-world
measurement.

## Actions

- Build an evaluation loop that notices when reality changes.
- Version every evaluator and baseline.
- Define runnable checks that exercise monitoring and monitoring after release.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for monitoring, monitoring after release needed to reproduce work on Monitoring After Release.
- Report results for monitoring, monitoring after release by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

For non-deterministic systems, launch is the beginning of real-world quality measurement. Production behavior changes as users, data, policies, dependencies, and models change.
For example, a support assistant can pass pre-release tests and then drift when the policy database changes or users discover a new edge case.

Testing non-deterministic systems does not stop at launch.

Pre-release testing is necessary, but it cannot cover every future condition. User traffic changes. Policies change. Retrieval data changes. Model versions change. Abuse patterns change. Personalization signals drift. External dependencies behave differently. The system that passed last week may behave differently next month.

This will get more intense as AI systems start updating more dynamically in production. A model route may change, a prompt may be rewritten, a retrieval index may refresh, a memory store may grow, a policy file may update, or a fine-tuned model may learn from new feedback without waiting for a traditional release train. The production system becomes a moving target.

That does not make pre-production testing optional. It makes production testing at least as important, and often more important. Pre-production testing shows whether the system was ready for the world the team imagined. Production testing shows what happened in the world that actually arrived.

That is why AI quality is monitored, not merely certified.

Post-release monitoring should track sampled output quality, failure rates, safety violations, privacy issues, policy violations, user complaints, human escalations, latency, cost, category-level performance, and drift from previous baselines.

Canary releases are one useful pattern. A small percentage of traffic sees the new version first. Confidence Engineers and product engineers monitor quality before expanding rollout. If failure rates increase, the team can stop or roll back before most users are affected.

Shadow testing is another pattern. The new version runs in parallel with the current version, but users do not see its output. The team compares the hidden output against the production output using judges, metrics, and human review. This is especially useful when the new version might be risky but the team wants evidence from realistic traffic.

Rollback thresholds should be defined before release. Examples include: any critical safety failure, policy failure rate above 3%, average quality below 7.5, user complaint rate doubling, or latency increasing more than 25%. Predefined thresholds reduce hesitation when the system starts misbehaving.

Monitoring should also feed the test suite. Important production failures should become new golden-set cases. New abuse patterns should become adversarial tests. New user behaviors should inform future sampling.

The mindset shift is important. For deterministic systems, teams often think of release as the moment testing ends. For non-deterministic systems, release is the moment testing meets reality.

You cannot guess every possible case. Build an evaluation loop that notices when reality changes.

## From the Field: Canary Users Missed Meetings First

Chrome was the most aggressive "testing in production" culture I had seen at that point. Canary builds went out constantly, often daily or faster, and they were used by people on the Chrome team, early adopters inside Google, and some people working near the open-source tree. These builds sometimes went out before the full test suite had finished. Build breaks were visible in public. Regressions were not hidden behind a polished release process. They were part of the operating model.

That sounds risky, and it was. But it was also powerful. Canary users found real problems that no pre-release suite was likely to imagine.

One memorable example started with a weird human signal: people inside Google were missing meetings. That is not the kind of bug a browser test plan usually starts with. We narrowed it down to people running Canary builds. The failure was not "Chrome does not load Calendar." It was subtler. A JavaScript error happened when Calendar computed how to render a user's day with overlapping events. That broke both the reminder path, and the overlapping meeting was not displayed in the UI.

No one would have written that exact test ahead of time: "calendar overlap calculation breaks reminders in this particular browser build, causing Googlers to miss meetings." But canary monitoring made the failure visible while the blast radius was still small.

That is the monitoring lesson. Use an escalating path: canary, developer channel, beta, then production. Watch real users early, especially friendly users who can tolerate some risk and report clearly. Production monitoring is not a replacement for tests. It is how the system tells you about the tests you did not know you needed.

## High-Stakes Examples

### Example: CartCare Chatbot


> After release, refund-tool calls double between 11 PM and midnight.

The eval suite may still pass. The release dashboard may still look green. But production monitoring should ask why this behavior changed. Did a prompt update make the bot more generous? Did a fraud ring discover a phrase that triggers refunds? Did a store outage create legitimate claims? Did the tool retry and double-submit?

Monitor the signals that show product behavior, not only server health:

- tool-call count
- refund amount
- escalation rate
- repeated contacts
- policy refusals
- latency and retries
- slice by store, time, and customer type

Launch is the beginning of real-world quality measurement, not the end of testing.


## Expert Notes

Expert monitoring separates data drift, model drift, behavior drift, and evaluation drift. If the judge changes, apparent product quality can change even when the product did not. Version every evaluator and baseline.
