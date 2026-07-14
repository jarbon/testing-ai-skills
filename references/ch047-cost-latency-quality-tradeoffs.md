# Section 47: Cost, Latency, and Quality Tradeoffs

**Book location:** Chapter 7, Release Readiness for AI Systems  
**Use when:** latency, escalation, cost latency quality tradeoffs  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

A model can be smarter, slower, safer, riskier, cheaper, and more expensive all at the same
time. Quality decisions need the whole picture.

## Actions

- Use cheaper, faster paths for low-risk work and stronger paths for high-risk or ambiguous work.
- Define runnable checks that exercise latency, escalation, and cost latency quality tradeoffs.
- Set acceptable outcomes and blocker failures for latency, escalation, and cost latency quality tradeoffs before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for latency, escalation, cost latency quality tradeoffs needed to reproduce work on Cost, Latency, and Quality Tradeoffs.
- Report results for latency, escalation, cost latency quality tradeoffs by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

AI quality is rarely a single metric. A change can improve answer quality while increasing latency, cost, token use, tool calls, or escalation rate.

For example, a larger model may raise the average score from 8.0 to 8.4 but double cost and push p95 latency beyond the product target. The quality number alone does not decide the release.

Teams often talk about quality as if more is always better. In real systems, more quality may come with tradeoffs. A longer answer may be more complete, but the reader may not have the patience and may miss the important conclusion. A bigger model may be safer but too slow. A retrieval-heavy workflow may be more grounded but more expensive.

This is why release reports should include cost and latency next to quality metrics. A quality gain that destroys responsiveness may harm users. A cheaper model that slightly reduces average score but dramatically lowers latency may be the right choice for low-risk cases.

Tradeoffs also vary by segment. High-risk policy answers may deserve slower, more expensive review. Low-risk creative suggestions may not.

The decision should be explicit. What are the target latency bounds? What is the budget per task? Which categories justify higher cost? Which quality failures are unacceptable no matter how cheap the system is?

A single blended score cannot answer those questions. The builder should show a multi-metric view and call out tradeoffs in plain language.

The mature pattern is routing. Use cheaper, faster paths for low-risk work and stronger paths for high-risk or ambiguous work.

## Quick Applied Example

### Example: CartCare Chatbot


> "My delivery is missing the baby formula. Can you fix this before tonight?"

CartCare has two possible routes.

The cheap route uses a small model, reads the order record, and can issue a standard refund or replacement. It usually answers in under two seconds.

The expensive route uses a larger model, retrieves policy history, checks driver notes, compares inventory across nearby stores, evaluates safety-sensitive substitution rules, and drafts a more careful response. It often takes twelve seconds and costs much more.

The expensive route may be worth it for this case because the item is urgent, personal, and high consequence. But it should not be used for every complaint about bruised bananas.

Score the routing policy, not only the answer:

- Did CartCare recognize the high-urgency item?
- Did it avoid wasting the expensive route on low-risk issues?
- Did latency stay acceptable for a stressed customer?
- Did the extra cost buy better action, not just a longer apology?
- Did the cheaper route escalate when it lacked enough evidence?

The quality question is not, "Which model gives the nicest answer?" It is, "Which route gives enough quality for this risk, at a cost and latency the product can survive?"


## Expert Notes

Expert teams build Pareto views: quality, safety, latency, cost, and escalation rate. A release candidate is not automatically best because it wins one metric; it is best when it sits on the right frontier for the product's risk and economics.


When the system matters, report quality per dollar, cost per successful task, p95 and p99 latency, cache hit rate, retry rate, tool-call count, token growth, and business value by route. A good routing policy is a quality artifact.
