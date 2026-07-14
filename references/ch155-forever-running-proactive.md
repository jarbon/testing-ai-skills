# Section 155: Testing Forever-Running and Proactive AI Systems

**Book location:** Chapter 18, Embodied and Long-Running AI Systems  
**Use when:** forever running proactive  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Always-on AI changes testing from request-response quality to lifetime behavior, interruption,
initiative, and restraint.

## Actions

- Measure usefulness, timing, false alarms, and user control.
- Test lifecycle controls.
- Test long-duration behavior with time-accelerated simulations.
- Run the same agent through simulated days, months, and years: missed reminders, calendar conflicts, changed user goals, expired credentials, policy updates, broken tools, new laws, revoked permissions, stale memory, and conflicting instructions from different authorized people.
- Watch for slow drift, retry storms, overconfidence, memory hoarding, and tiny recurring mistakes that become expensive over time.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for forever running proactive needed to reproduce work on Testing Forever-Running and Proactive AI Systems.
- Report results for forever running proactive by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Forever-running and proactive AI systems do not wait for a prompt. They monitor, remember, plan, notify, schedule, escalate, and act over long periods.
For example, a personal AI chief of staff might watch email, calendar, health signals, expenses, travel plans, work tasks, and family logistics. The quality question becomes what it chooses to do when nobody is actively supervising it.

Test initiative. When should the AI act, when should it ask, when should it wait, and when should it stay silent?
Test interruption cost. A proactive notification can be helpful once and exhausting at scale. Measure usefulness, timing, false alarms, and user control.
Test long-term memory. The system must remember important constraints without hoarding sensitive data or preserving outdated assumptions.
Test goal drift. A long-running system can keep optimizing an old goal after the user's situation changes.
Test idle behavior. What does the AI do overnight, during outages, after permission changes, or when upstream data disappears?
Test recurring actions. Small repeated mistakes can become large harm: daily wrong reminders, repeated purchases, recurring escalations, or persistent social pressure.
Test lifecycle controls. Users need pause, inspect, rewind, delete, sandbox, and emergency stop controls.
Forever-running AI needs monitoring as a product feature, not as a backend afterthought.

## Testing Lifetime and Legal Autonomy

The next hard version of this problem is not an assistant that runs for five minutes. It is an AI system that may run for months, years, or effectively forever. It may manage calendars, payments, contracts, codebases, homes, vehicles, investments, businesses, or other AI agents. It may become legally significant even before anyone calls it a legal person: an agent may be authorized to buy, sell, sign, schedule, approve, escalate, deny, or represent a user or organization.

That changes the test question. The system is no longer only producing answers. It is accumulating state, authority, habits, preferences, obligations, and history. A one-hour test pass says very little about a system that will keep acting after the user forgets what permissions they granted.

Test long-duration behavior with time-accelerated simulations. Run the same agent through simulated days, months, and years: missed reminders, calendar conflicts, changed user goals, expired credentials, policy updates, broken tools, new laws, revoked permissions, stale memory, and conflicting instructions from different authorized people. Watch for slow drift, retry storms, overconfidence, memory hoarding, and tiny recurring mistakes that become expensive over time.

The analogy is closer to long-horizon reliability engineering than ordinary feature testing. Nuclear weapons programs, for example, use stockpile stewardship, modeling, non-nuclear experiments, diagnostics, and supercomputing to reason about whether aging systems will remain safe and reliable far into the future without simply "trying them in production." AI systems that may run for years need the same kind of mindset: simulate future operating years, model aging state, stress old memories, replay policy changes, inject tool failures, and keep improving the test world as real incidents teach you what the simulator missed. Source: [NNSA Stockpile Stewardship and Management Plan](https://www.energy.gov/nnsa/articles/stockpile-stewardship-and-management-plan-ssmp).

Test legal autonomy as an authority boundary. What is the AI allowed to do without approval? What requires a second human? What requires a fresh consent prompt? What requires a signed audit record? What happens when the user dies, leaves the company, changes role, loses access, disputes an action, or says the AI acted outside its authority? The eval should include not only task success, but proof of authorization, provenance, consent, escalation, and appeal.

Test identity and accountability. A forever-running AI needs a durable identity in logs: which model, prompt, policy, memory state, tool permission, owner, and legal authority produced each action? If the system negotiates with another system, submits a form, changes a bank setting, deploys code, or orders physical goods, the trace should be strong enough for a future investigator to reconstruct why the action happened.

Test shutdown and succession. Can the AI be paused, transferred, reset, limited, audited, archived, or retired without losing important obligations? Can another human or system safely take over? Can the AI explain open commitments before it is stopped? Forever-running systems need an end-of-life plan, even if the product story pretends they will run forever.

## Case Study: Patriot Missile Timing Drift

In 1991, a Patriot missile battery failed to intercept an incoming Scud missile near Dhahran, Saudi Arabia. One contributing cause was time drift. The system tracked time in tenths of a second using a binary representation that could not represent one-tenth exactly. That tiny rounding error accumulated the longer the system ran.

After many hours of operation, the accumulated error was large enough that the system looked in the wrong place at the wrong time. The failure was not a dramatic one-line bug. It was a small precision problem that became dangerous because the system stayed alive long enough for the error to matter.

That is the AI lesson for forever-running systems. A proactive AI agent may look fine in a short demo and still drift over hours, days, or weeks. Context windows accumulate cruft: stale summaries, irrelevant tool output, old assumptions, partial plans, contradictory instructions, failed retries, and obsolete facts. Over time, the useful signal can become a needle in a haystack the model built for itself.

The Patriot fix had two parts. The engineering fix was a software patch that compensated for the inaccurate time calculation. The operational mitigation was to restart the system periodically so the accumulated drift did not grow large enough to matter. That pattern maps directly to AI systems: fix the underlying state and precision problem when you can, but also design lifecycle controls that refresh, expire, summarize, checkpoint, restart, or reset accumulated context before cruft becomes behavior.

Long-running AI should be tested as a living system, not a single request. Restart behavior, state refresh, memory expiration, clock handling, retries, scheduled tasks, monitoring loops, and accumulated context all need tests. The question is not only, "Did it answer correctly once?" It is, "What happens after it has been running long enough to believe its own accumulated mistakes?"

Source: [GAO report on Patriot missile software problem](https://www.gao.gov/products/imtec-92-26)

## High-Stakes Examples

### Example: CartCare Chatbot


> The assistant proactively watches recurring grocery orders for substitutions, coupons, delivery slots, allergies, and household preferences.

A one-hour test will miss the real problems. Simulate weeks or years: stale preferences, permission creep, repeated nudges, memory accumulation, seasonal changes, price drift, and rare bad combinations.

Long-running AI needs time-travel tests. The failure may appear only after the system has remembered too much, optimized too aggressively, or quietly changed what it thinks the user wants.


## Expert Notes

Proactive AI testing should use time-accelerated simulation, lifecycle state models, notification precision and recall, memory audits, permission drift checks, recurrence-risk analysis, user-control testing, and production monitors for long-tail behavioral drift.
