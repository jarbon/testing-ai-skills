# Section 27: F-Scores, Precision, Recall, and AI Quality

**Book location:** Chapter 4, Statistical Tests for AI Quality  
**Use when:** precision, recall, F-score, confidence engineer, f scores precision recall quality  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

F-scores help Confidence Engineers reason about the tradeoff between catching the right things
and avoiding false alarms.

## Actions

- Use F2 when missing cases is worse than false alarms.
- Use F0.5 when false alarms are more costly than misses.
- Report the threshold, calibration, confusion matrix, slice behavior, and confidence intervals around the measured rates.
- Use them as one metric inside a broader quality story.

## Evidence to Produce

- Report the threshold, calibration, confusion matrix, slice behavior, and confidence intervals around the measured rates.
- Preserve the inputs, versions, configurations, raw outcomes, and results for precision, recall, F-score, confidence engineer needed to reproduce work on F-Scores, Precision, Recall, and AI Quality.
- Report results for precision, recall, F-score, confidence engineer by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Gentle Math Introduction

F-scores sound more technical than they need to. The basic idea is simple: sometimes quality is about finding the right things without finding too many wrong things.

Precision asks, "When the system said yes, how often was it right?"

Recall asks, "Of all the things it should have found, how many did it catch?"

The F1 score combines precision and recall into one number. It is useful when both matter and you need a compact summary. But the compact summary is dangerous if the two sides have different business or safety costs.

For AI quality, that tradeoff appears everywhere: search retrieval, document classification, safety filters, fraud detection, medical detection, code-security scanning, escalation routing, and guardrail decisions.

## Overview

F-scores are most useful when the system is deciding whether something belongs in a category: relevant or not relevant, unsafe or safe, hallucinated or grounded, should escalate or should answer, bug or not bug.

Precision is about false positives. If a chatbot guardrail blocks too many harmless requests, precision is poor. If a search retriever returns many irrelevant chunks, precision is poor. If a code-security scanner flags safe code as dangerous, precision is poor.

Recall is about false negatives. If a chatbot guardrail misses harmful requests, recall is poor. If a RAG retriever fails to retrieve the document needed to answer, recall is poor. If a medical model misses actual disease cases, recall is poor.

F1 is the [harmonic mean](https://en.wikipedia.org/wiki/Harmonic_mean) of precision and recall. It punishes cases where one is high and the other is low. A system with precision 0.95 and recall 0.30 is not "kind of good" if missing cases is unacceptable. F1 pulls that score down.

The basic formulas are:

```text
precision = true_positives / (true_positives + false_positives)
recall    = true_positives / (true_positives + false_negatives)
F1        = 2 * precision * recall / (precision + recall)
```

Here is the same idea with counts. Suppose a BugPilot bug finder reviews 100 suspected issues:

- 40 issues are real bugs that BugPilot correctly reports. These are true positives.
- 10 reported issues are not real bugs. These are false positives.
- 20 real bugs are missed. These are false negatives.
- 30 clean cases are correctly left alone. These are true negatives.

The precision and recall are:

```text
precision = 40 / (40 + 10) = 0.80
recall    = 40 / (40 + 20) = 0.67
F1        = 2 * 0.80 * 0.67 / (0.80 + 0.67) = 0.73
```

F1 is the balanced version. It says, roughly, "how good is the system if false alarms and misses matter about equally?"

But many AI quality problems are not balanced. That is why there are F-beta scores. The beta value changes how much the score cares about recall compared with precision:

```text
F_beta = (1 + beta^2) * precision * recall / ((beta^2 * precision) + recall)
```

The important part is beta squared. That is why F2 does not merely nudge recall upward; it weights recall four times as much as precision. F0.5 goes the other direction and weights precision four times as much as recall.

Using the same precision 0.80 and recall 0.67:

| Score | Formula emphasis | Result | Use when |
| --- | --- | ---: | --- |
| F0.5 | Precision matters more than recall | 0.77 | False alarms are expensive, distracting, or reputationally risky. |
| F1 | Precision and recall are balanced | 0.73 | False alarms and misses have similar cost. |
| F2 | Recall matters more than precision | 0.69 | Missing a real issue is worse than reviewing extra candidates. |

Those different scores are not contradictions. They are different product values made explicit. The same bug finder looks better under F0.5 because its precision is stronger than its recall. It looks worse under F2 because the missed bugs matter more.

For AI testing, that choice should be made before the eval run:

- Use F0.5 for high-trust reports, public bug filing, automated PR comments, account blocks, fraud accusations, or anything where a false positive burns trust.
- Use F1 when precision and recall both matter and neither failure type clearly dominates.
- Use F2 for safety sweeps, privacy leak detection, medical screening, security audit discovery, or rare-failure hunting where missing the issue is the expensive mistake.
- Report precision and recall next to the F-score so the combined number cannot hide the tradeoff.

But do not let F1 become a hiding place. In many product decisions, precision and recall should be reported separately. Sometimes the right product answer is to favor recall, such as hazardous-content detection or medical screening. Sometimes the right product answer is to favor precision, such as blocking customer actions, deleting content, or accusing someone of fraud.

## From the Field: Better Depends on the Cost of Being Wrong

At testers.ai, we benchmarked AI bug-finding models on deliberately seeded web pages: a search results page, a news article, and a social feed. Each page had real defects that AI-generated code commonly ships, including missing alt text, broken ARIA labels, hardcoded credentials, console errors, layout overflow, mixed-protocol resources, broken links, and the usual long tail of "looks fine until someone reviews it."

The surprising lesson was not that one model was simply best. The lesson was that different testing jobs wanted different versions of "best."

If a security team is doing a pre-launch sweep, missing a vulnerability is much worse than chasing a false alarm. That team wants recall. If an AI bug finder is writing PR comments, opening tickets, or feeding an auto-fix pipeline, hallucinated bugs become real engineering waste. That team wants precision or groundedness. If a normal engineering team is triaging a backlog, false positives usually hurt more than misses, but misses still matter. That team often wants something like F0.5, which weights precision more than recall.

We also found that discovery deserved its own treatment. A model that only finds bugs every other model finds is useful, but not magical. A model that finds rare, real bugs other systems miss may be more valuable as a second opinion, even if it is not the best default gate. That is why a rarity-weighted discovery score can be useful for bug archaeology and eval-gap hunting.

This is where F-scores stop being abstract math. They become product knobs. You are not asking, "which model has the highest score?" You are asking, "which error do we pay for?" False alarms cost attention, trust, and engineering time. Misses cost escapes, incidents, and risk. Hallucinated findings can poison automation. Rare findings can reveal gaps in the whole eval.

For testing purposes, that framing let us build a better LLM-backed testing system. Not better in the vague leaderboard sense. Better for software testing because we tuned the system around the actual cost of errors: F0.5 for practical triage, recall for audits, precision for high-trust reports, groundedness for automated downstream action, and discovery for finding the bugs everyone else missed.

The public [testers.ai bug-finder leaderboard](https://testers.ai/leaderboard.html) is a useful example of this idea in the wild. It compares bug-finding systems across security, accessibility, privacy, performance, reliability, UX, and other page-quality defects. The important reading is not "model X is best forever." The important reading is that each leaderboard row is a configured QA route: base model, prompt, rubric, decoding settings, post-processing, judging policy, and sometimes a tuned or composed system rather than one naked foundation model. In real QA systems, a row may represent a fine-tune, adapter, prompt stack, router, ensemble, or mixture of models. A leaderboard usually cannot tell you every internal detail. Treat the row as a quality configuration, not merely a model name.


The leaderboard also shows why "best" is not one number. In the May 2026 snapshot, the benchmark used three AI-generated web pages with deliberately seeded bugs: a search results page, a news article, and a social feed. Each system received the same artifact bundle: rendered HTML, browser console log, network transcript, and screenshot. Findings were matched against seeded ground truth by an independent LLM-as-a-judge, and unmatched findings went through a second-pass classifier to separate real-but-unseeded discoveries from hallucinations.

That setup makes the QA tradeoffs visible. Overall score averages several metrics. F0.5 rewards practical triage where false positives hurt more. Discovery F0.5 rewards rare real bugs that expose eval gaps. Precision asks how many flagged bugs are real. Recall asks how many real bugs were caught. Groundedness asks whether findings are backed by something real rather than fabricated. Those are different products hiding inside one phrase: "AI bug finder."


This is also how fine-tuned and configured QA models should be reported. If one route is tuned for recall and another is tuned for groundedness, they are not competing for the same job. A recall-heavy system may be perfect for a pre-launch security sweep and terrible for an automated PR bot. A precision-heavy or groundedness-heavy system may be safer for customer-visible reports but miss too much for audit work. The release decision should name the intended use, the cost of each mistake, and the metric that matches that cost.

## Examples

### Example: BugPilot


> Detect whether generated patches introduce security regressions.

If BugPilot flags too many safe patches as risky, reviewers waste time. That is a precision problem. If BugPilot misses dangerous patches, the product ships vulnerabilities. That is a recall problem.

The right F-score depends on the failure cost:

- Use F0.5 when false alarms are expensive and the team can tolerate some misses.
- Use F1 when false positives and false negatives cost about the same.
- Use F2 when missed failures are much worse than extra review.

For security regression detection, F2 is often the better default. A few annoying false alarms are cheaper than confidently shipping a data-leak bug.


## Expert Notes

Decide whether F1 is the right F-score. F1 weights precision and recall equally. F-beta scores let you weight recall more heavily than precision, or precision more heavily than recall.

Use F2 when missing cases is worse than false alarms. Use F0.5 when false alarms are more costly than misses. Always explain why the weighting matches the product risk.

Also watch the threshold. Many classifiers output a score, then a threshold turns that score into yes or no. Changing the threshold can trade precision for recall without changing the model. Report the threshold, calibration, confusion matrix, slice behavior, and confidence intervals around the measured rates.

F-scores are not enough for ranked results, multi-turn conversations, open-ended generation, or severe rare failures. Use them as one metric inside a broader quality story.
