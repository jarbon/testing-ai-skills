# Section 42: AI Passing Testing Certification Exams

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** confidence engineer, passing certification exams  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

When AI can pass certification-style testing exams, the human advantage moves from memorizing
terminology to designing evidence.

## Actions

- Test the incentive system around the benchmark.
- Define runnable checks that exercise confidence engineer and passing certification exams.
- Set acceptable outcomes and blocker failures for confidence engineer and passing certification exams before running the evaluation.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for confidence engineer, passing certification exams needed to reproduce work on AI Passing Testing Certification Exams.
- Report results for confidence engineer, passing certification exams by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

A recent study, [*Can Language Models Pass Software Testing Certification Exams? a case study*](https://arxiv.org/abs/2603.23142), asked whether language models can pass software testing certification exams using 30 International Software Testing Qualifications Board (ISTQB) sample exams across foundation, advanced, specialist, and expert categories. The result was blunt: two models passed all 30 sample certification exams by scoring at least 65%. I will avoid commenting on whether 65% should be considered "passing."
That does not mean an AI officially became ISTQB certified. It means certification-style exam questions are increasingly solvable by models, which should make Confidence Engineers rethink what professional competence really means.

This matters because certification exams often reward terminology, syllabus recall, and exam-pattern reasoning. Those skills are not worthless, but they are no longer enough to define testing expertise in an AI world.
If a model can answer many certification questions, then the valuable human work moves up the stack. The Confidence Engineer must define the right risk, build the right rubric, choose the right sample, interpret uncertainty, challenge the benchmark, and explain the release decision.
The ISTQB result should not be read as "certifications are useless." A shared vocabulary can help teams communicate. A syllabus can introduce important concepts. But passing a knowledge exam is different from designing a credible evaluation for a live AI product.
There is another lesson: exams are evals too. They have oracles, wording assumptions, possible ambiguous answers, syllabus boundaries, and pass thresholds. If AI can pass them, builders should ask what the exam is measuring and what it is not measuring.
The same applies to internal training tests. If the assessment only checks recall, AI will do well. If it asks someone to investigate a flaky non-deterministic failure, build a sampling plan, calibrate an LLM judge, or defend a release recommendation, the assessment becomes more meaningful.
The future Confidence Engineer does not win by knowing definitions that a model can retrieve. They win by turning messy product risk into measurable evidence and responsible action.

### From the Field: Testing the Test

Around the early GPT-3 and ChatGPT era, I ran a similar experiment myself. I fed certification-style ISTQB exam questions to the model, scored the answers harshly, and published the result: the model passed almost everything. The exam world did not exactly send flowers. Soon after, I noticed more legal language around publishing results from running those tests.

That reaction was the interesting part. The people writing tests for testers still had incentives around the outcome of the test. That is not a moral failure; it is a reminder that every benchmark has owners, economics, reputation, and politics around it.

The failures were also instructive. Many of the missed questions were ambiguous. Some depended on previous questions or shared context I had not provided because I wanted to err on the side of failing the model. Some multiple-choice questions had more than one professionally defensible answer. A few expected answers looked simply wrong to me, as if someone had reverse-engineered a question from terminology rather than from actual testing experience.

The lesson is not that exams are bad. The lesson is that even tests need testing. Test the test. Test the oracle. Test the scoring rule. Test the incentive system around the benchmark. It is testing all the way down, and critical thinking matters more than the certificate.

## Quick Applied Example

### Example: BugPilot


> Ask the model an ISTQB-style multiple-choice question about boundary value analysis.

Passing the question may show that the model recognizes the textbook pattern. It does not prove the model can design a useful boundary test for a messy checkout flow, a robotic gripper, or an AI judge rubric.

For certification-style evals, inspect the failures too. Did the model miss the question because it lacked testing knowledge, because the question was ambiguous, because two answers were defensible, or because prior context was required? Those are different lessons.

The useful claim is modest: exam performance is evidence about learned testing vocabulary and patterns. It is not the same as field judgment.


## Expert Notes

The deeper move is to treat certification performance as a benchmark with limits. The cited ISTQB study used sample exams, not official proctored certification records. There is also a contamination question: if sample questions, answer keys, explanations, or close variants were public on the web, a model may have memorized some of the benchmark rather than learned testing judgment.

That said, my own experiment used protected, non-crawlable test results rather than material that should have been sitting in ordinary web training data. That makes the result harder to dismiss as simple memorization, at least in that case. The larger point still holds: exam-style testing knowledge is increasingly automatable, while real evaluation design remains context-heavy.
