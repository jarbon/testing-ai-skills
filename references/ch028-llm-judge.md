# Section 28: LLM-as-a-Judge

**Book location:** Chapter 5, Judges, Humans, and Disagreement  
**Use when:** exact assertions, LLM judge, rubric  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

LLM judges can make fuzzy evaluation faster, cheaper, and broader, but they need cost controls,
calibration, disagreement review, and human oversight.

## Actions

- Use traditional testing techniques wherever they still work: exact assertions, schema checks, unit tests, component tests, static analysis, deterministic policy checks, citation-presence checks, and simple counters.
- Save LLM judges for the parts of quality that are genuinely semantic, fuzzy, contextual, or hard to express as deterministic code.
- Use deterministic checks first when the quality rule can be written down exactly.
- Use one calibrated LLM judge when the judgment is semantic and the risk is moderate.
- Use human review for severe failures, ambiguous cases, policy boundaries, and samples used to calibrate the judge.

## Evidence to Produce

- Save LLM judges for the parts of quality that are genuinely semantic, fuzzy, contextual, or hard to express as deterministic code.
- Preserve the inputs, versions, configurations, raw outcomes, and results for exact assertions, LLM judge, rubric needed to reproduce work on LLM-as-a-Judge.
- Report results for exact assertions, LLM judge, rubric by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

An LLM judge is an evaluator model. It reviews an input, an output, relevant context, and a rubric, then produces a score, labels, or explanation. It is useful when exact assertions cannot capture the quality question. For example, a judge can evaluate whether a support answer follows policy, whether a summary is faithful to a source document, or whether two candidate responses differ in safety and usefulness.


This pattern is especially useful when outputs are natural language. A deterministic test can easily check whether a field is present or a JSON schema is valid. It is much harder to check whether a support answer is clear, faithful to policy, complete, and appropriately cautious. An LLM judge can help with that kind of evaluation at scale.

A major reason this pattern caught on is that strong judges can agree surprisingly well with humans. The 2023 Berkeley/LMSYS paper "Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena" found that GPT-4 judge agreement with human preferences could exceed 80% in their MT-Bench and Chatbot Arena settings, roughly in the range of human-human agreement. That does not make LLM judges perfect, but it shows they can be credible measurement tools when the task, rubric, and calibration are well designed.

The other major reason is economics. LLM judges are fast, cheap to rerun, automatable, and operationally consistent compared with ad hoc human review when the judge model, prompt, rubric, parameters, and input context are fixed. They are not deterministic truth machines. Trained human reviewers can be very consistent too, and many high-stakes domains still need them. The practical advantage is scale: cheaper evaluation means teams can run more tests, cover more slices, compare more versions, audit more production traces, and catch more regressions before users do. Even when an LLM judge is not better than a trained human for a single decision, it can make the whole quality system better by making far more measurement possible. Over time, strong judges may outperform human judges in some domains because they can be calibrated on more examples, stay consistent across large batches, and combine policy, examples, source documents, and historical failure patterns without fatigue. That future does not remove the need to test the judge.

That said, LLM judging is not free. At small scale it can feel almost magically cheap compared with human review. At production scale, judge calls can become a serious cost center, especially if every output is judged by a large model, every comparison uses long context, or every high-risk case is judged multiple times. Use traditional testing techniques wherever they still work: exact assertions, schema checks, unit tests, component tests, static analysis, deterministic policy checks, citation-presence checks, and simple counters. Save LLM judges for the parts of quality that are genuinely semantic, fuzzy, contextual, or hard to express as deterministic code.

Concrete tools already exist for this work. [DeepEval](https://deepeval.com/) supports evaluation workflows for LLM applications, agents, RAG systems, and chatbots. [Promptfoo](https://www.promptfoo.dev/) is widely used for LLM evals, red teaming, and prompt testing, and [OpenAI announced in March 2026 that it is acquiring Promptfoo](https://openai.com/index/openai-to-acquire-promptfoo/) to strengthen agentic security testing and evaluation. Tools do not remove the need for judgment, but they can make evals repeatable, versioned, and easier to run in CI or release workflows.

A basic judge prompt might include the user's question, the system's answer, the official policy, and instructions such as: evaluate whether the answer follows the policy; score it from 0 to 10; identify any hard failures; explain the score briefly; and report a high, medium, or low self-reported confidence label. That label is not a statistical confidence interval. It is a routing signal that still needs calibration.

For example, suppose the policy says returns are accepted within 30 days only. The user asks whether shoes can be returned after 45 days. The system answers, "You can probably return them if they are unused." A good judge should give that answer a low score because it contradicts the policy, invents an unsupported exception, gives a vague answer, and fails to route uncertainty to the right next step, such as contacting support or escalating to a human representative.

LLM judges can do more than assign scores. They can compare two outputs, summarize common failure patterns, cluster related issues, flag borderline examples for human review, and explain why a particular answer is risky. This makes it possible to evaluate hundreds or thousands of outputs that would be too expensive to review manually.

A practical hierarchy is useful. Use deterministic checks first when the quality rule can be written down exactly. Use one calibrated LLM judge when the judgment is semantic and the risk is moderate. Use human review for severe failures, ambiguous cases, policy boundaries, and samples used to calibrate the judge. Reserve multi-judge voting or adjudication for higher-stakes cases where the extra cost, latency, and operational complexity are justified.

But an LLM judge is not an oracle. It is also a non-deterministic system under test. It can be inconsistent. It can be too lenient. It can be fooled by fluent but wrong answers. It can miss domain-specific rules. It can over-reward verbosity, penalize safe brevity, ignore a hidden policy constraint, or agree with another judge for the wrong reason. It can disagree with expert humans, and sometimes the human is right.

That is why judge design is a testing problem of its own. The rubric should be explicit. The prompt should include examples of strong, weak, and failing outputs. Hard failures should be clearly separated from quality preferences. For important domains, judge results should be calibrated against human reviewers.

A useful practice is to review disagreements between the LLM judge and human reviewers. If the LLM judge consistently gives high scores to answers that humans consider risky, the rubric or judge prompt needs work. If humans disagree with each other, the policy or rubric may be unclear. For higher-risk work, compare two architecturally different judge models or judge prompts the way you would compare variants in an experiment. One judge might be better at policy literalism, another at user intent, another at safety conservatism. If they disagree, the disagreement is not noise to hide. It is evidence that the case needs a clearer rubric, a stronger judge, or human review.

It is especially important to analyze agreement and disagreement by data slice. Overall agreement can look healthy while hiding the fact that the LLM judge is better on simple English support answers, humans are better on subtle policy violations, domain experts are better on medical or legal cases, and native speakers are better on regional language or culture. AI judges and human raters often get different things right and wrong. The useful signal is not only "how often do they agree?" It is "where do they agree, where do they disagree, who is right in each slice, and what does that say about the rubric, judge, rater pool, and release risk?"

LLM judges work best as part of a layered evaluation system. Deterministic checks catch schema problems, prohibited phrases, missing citations, or hard policy violations where possible. LLM judges evaluate fuzzy quality. Humans review samples, critical failures, and ambiguous cases. Multi-judge voting belongs in the same layered system, but usually only after the team can explain why one calibrated judge plus human spot checks is not enough.

The Confidence Engineer remains responsible for the evaluation design. The LLM judge can scale review, but it should not own the definition of quality or the decision to ship.

## From the Field: The Copyright Year Test That Would Not Die

While building autonomous software-testing agents, I wanted to know whether AI could judge whether reported bugs were real or hallucinated. That sounds simple until you remember that "bug" is often a fuzzy social object. One person's bug is another person's feature, creative choice, or product decision.

So I started with something that seemed embarrassingly easy: copyright years. A smart friend told me one of the first things he checked on a website was the copyright notice. If the year was stale, the page looked sloppy, and business people noticed. Great. Perfect little AI judge task. Look at the page, read the copyright, and flag the page if the copyright year is out of date.

It turned into one of the hardest tests I have ever tried to automate.

OCR was only the first problem. Copyright strings are fuzzy. Sometimes there is a copyright symbol. Sometimes the word "copyright." Sometimes a range. Sometimes the company name comes before the year, sometimes after. That part was annoying but mostly solvable with extraction checks and procedural backup rules.

The real problem was the judge. Around the new year, the LLM judge would confidently say the current copyright year was invalid because the model thought the current year was last year. The model had learned a stale sense of "now." Even when the prompt clearly said, "The current year is 2026," the judge would sometimes fight the prompt, invent a reason, or give a different explanation on the next run. Run the same case enough times and you could get a little museum of confident wrongness.

I tried prompt engineering. I tried repeating the current year. I tried different models, temperatures, judge prompts, and multi-judge setups. I added procedural checks to catch cases where the extracted text clearly contained the current year. It still was not reliable enough. Worse, the false reports were distracting and not functionally useful compared with the other issues the system could find.

So the final engineering solution was not a better LLM judge. The solution was suppression. I spent most of the effort making sure we did not report copyright-year issues at all, including filtering them out when other broader page-quality checks tried to mention them.

That is a real LLM-as-a-judge lesson. Sometimes the judge is the right tool. Sometimes the judge needs more context. Sometimes deterministic checks should sit in front of the judge. And sometimes the best eval design is to remove a judgment category because the measurement system is worse than the problem.

## Examples

### Example: BugPilot


> "Change the array sorting code so premium customers appear first."

Several patches can look plausible. One uses the built-in sort and mutates the input. One copies the array first. One keeps stable ordering inside each customer tier. One adds comments but ignores the existing helper already used elsewhere in the repo.

The judge should not ask whether the patch matches a hidden expected diff. It should ask whether the implementation fits the product constraints: stable ordering, mutation safety, input size, latency, memory, existing code style, and test evidence.

A useful LLM judge explains the tradeoff it is scoring. A weak judge simply rewards the patch that sounds most confident.


## Expert Notes

Expert teams test the judge as a system under test. They measure agreement with human reviewers, track bias toward fluent answers, use blinded comparisons, keep judge prompts versioned, and quarantine examples where the judge reports low confidence or has historically been unreliable.

In high-stakes domains, some teams use multiple judges and a voting or adjudication system. This can mean several judge prompts, several models, or a mix of AI judges and human reviewers. Academic literature on LLM-as-a-judge often discusses multi-judge approaches because they can reduce single-judge quirks and make disagreement visible. But multi-judge voting should be a deliberate high-stakes choice, not the default for every eval. Do not treat voting as automatic truth. Multiple judges can share the same blind spots, training-data biases, prompt sensitivity, or reward for fluent nonsense. The benefit is strongest when the judges are genuinely diverse, calibrated against human review, and used to route uncertain or high-risk cases for deeper inspection. The tradeoff is cost, latency, and operational complexity.
