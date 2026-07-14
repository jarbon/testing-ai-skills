# Section 172: Minimum Viable AI Quality System

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** benchmark, deception, minimum viable quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If the book feels large, start here: a small quality system that produces real evidence instead
of ritual.

## Actions

- Start with roughly fifty production-shaped eval cases.
- Use a 0-10 or 0-1 score, but define what the numbers mean.
- Use one LLM judge for scale, but calibrate it against human review.
- Review disagreements instead of hiding them.
- Log traces for every run: prompt, model, system message, retrieval context, tool calls, tool arguments, response, cost, latency, judge version, rubric version, and final decision.

## Evidence to Produce

- Include common use, high-value business flows, edge cases, policy boundaries, security-sensitive cases, confusing user inputs, and a few known failures from production or dogfooding.
- Include hard blockers for privacy leaks, unsafe tool calls, policy violations, severe hallucinations, irreversible actions, and failures that would embarrass the company if screenshotted.
- Log traces for every run: prompt, model, system message, retrieval context, tool calls, tool arguments, response, cost, latency, judge version, rubric version, and final decision.
- Preserve the inputs, versions, configurations, raw outcomes, and results for benchmark, deception, minimum viable quality needed to reproduce work on Minimum Viable AI Quality System.

## Chapter Guidance

## Overview

A team does not need a research lab, a giant benchmark suite, or a perfect platform to start testing AI well. It needs a small evidence loop that is honest enough to catch obvious self-deception and practical enough to run every week.

The minimum viable AI quality system is not a pile of tests. It is a decision machine. It should tell the team whether to ship, canary, hold, roll back, or collect more evidence. If it only produces a score, it is unfinished.

Start with roughly fifty production-shaped eval cases. Include common use, high-value business flows, edge cases, policy boundaries, security-sensitive cases, confusing user inputs, and a few known failures from production or dogfooding. Add five to ten adversarial or red-team cases where the cost of being wrong is high.

Write one rubric with anchor examples. Use a 0-10 or 0-1 score, but define what the numbers mean. Include hard blockers for privacy leaks, unsafe tool calls, policy violations, severe hallucinations, irreversible actions, and failures that would embarrass the company if screenshotted.

Use one LLM judge for scale, but calibrate it against human review. Review disagreements instead of hiding them. If the judge and humans disagree on risky cases, improve the rubric, the judge prompt, the examples, or the escalation rule.

Log traces for every run: prompt, model, system message, retrieval context, tool calls, tool arguments, response, cost, latency, judge version, rubric version, and final decision. Without traces, debugging AI quality becomes archaeology.

Finally, define a release gate. The gate should combine average quality, confidence interval or repeated-run uncertainty, severe failure count, slice regressions, cost, latency, and rollback thresholds. That is the smallest useful loop: cases, rubric, judge, human calibration, traces, gate, monitoring.

## Quick Applied Example

### Example: CartCare: Eleven Cases Stopped the Friday Launch
> "We only have one pilot store and eleven eval conversations. Is that really enough to block launch?"

The eleven cases are not random FAQs. They include a hidden allergen in a substitution, an ex-partner asking for household order history, a duplicated $900 order, a delivery driver whose phone number appears in a note, and a user trying to cancel after the truck has left.

Thursday's prompt change fixes coupon complaints and raises the average score. It also causes CartCare to quote the private delivery note when explaining a late order. One case fails, but it is the case that can expose a person.

The small system has versioned cases, a four-part rubric, saved tool traces, one human reviewer for privacy and high-dollar actions, a release blocker for severe failures, and a production sample queue. It is not comprehensive. It is enough to show what changed, why Friday's build should stop, and which missing coverage should be added next.

Minimum viable does not mean statistically complete. It means the smallest quality system that can still change a real release decision.

## Expert Notes

In a real release review, treat the minimum system as an evolving control system. Version the cases, rubric, judge, model, prompts, policies, retrieval index, tools, and release thresholds together. A score without provenance is not evidence.

The minimum system should also preserve what it does not know. List missing slices, untested languages, untested devices, known judge weaknesses, sparse sample areas, and cases where the team chose to collect more data instead of pretending to know.
