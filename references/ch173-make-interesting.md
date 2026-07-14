# Section 173: Make Testing Interesting

**Book location:** Chapter 20, The Practical Playbook  
**Use when:** make interesting  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Quality work gets better when people actually want to read the failures.

## Actions

- Do not make a test cute at the expense of clarity.
- Do not hide severity behind jokes.
- Do not let personality make a failure seem less important than it is.
- Use AI to test more, test differently, and test earlier.
- Use it to summarize clusters, title incidents, rewrite failure reports for different audiences, generate readable scenario names, and explain why a weird case matters.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for make interesting needed to reproduce work on Make Testing Interesting.
- Report results for make interesting by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Testing can be dry. Regression suites, failure reports, dashboards, and eval runs can become a wall of sameness. That is dangerous. If nobody wants to read the results, the quality system can be technically correct and socially invisible.

Making testing interesting does not mean making it unserious. It means making the work memorable enough that humans notice the signal. Good names, vivid scenarios, running jokes, small bits of personality, and readable failure reports can make people pay attention without compromising coverage.

AI systems make this easier. You can name agents after famous robots, fictional assistants, old operating systems, or internal team jokes instead of `agent_1`, `agent_2`, and `agent_3`: R2-D2 for the scrappy fixer, C-3PO for the translator, WALL-E for cleanup, TARS for the calm planner, HAL 9000 for the system you absolutely should not overtrust, KITT for the driving assistant, or Clippy for the agent that is trying very hard to help. You can make eval cases readable. You can make failure summaries sound like something a human would forward. You can ask an LLM judge to generate a crisp incident title, a funny-but-accurate failure label, or a short narrative explaining why a case matters.

The rule is simple: entertainment should serve evidence. Do not make a test cute at the expense of clarity. Do not hide severity behind jokes. Do not let personality make a failure seem less important than it is. But when the coverage is intact, make the work a little more alive.

Interesting tests help teams remember the weird failures. They help managers read the report. They help developers care about the regression. They help reviewers talk about the issue without needing to decode a thousand anonymous rows. They may even help AI agents reason over the results later, because the artifacts carry richer context than generic labels.

## From the Field: Cookie Monster in the Lab

When I was testing Internet Explorer HTML4 features on Windows CE, I had to test cookie behavior. The basic job was not glamorous: generate cookies, save them, load them, validate them, repeat the whole thing thousands of times in a tight loop.

So I added a little flair. While the test ran, it showed an animated Cookie Monster GIF and played a sound file of him eating and saying something like "yum, yum, yum."

Then I forgot about it.

Later, people started talking about random machines waking up in the lab at night and making strange noises. Somewhere in the dark, a Windows CE device was running thousands of cookie tests and enthusiastically announcing its progress. It was silly, but people noticed it. They noticed the test. They noticed that the work existed.

That lesson stuck with me. Quality work is often invisible until something breaks. A little personality can make the work visible before the outage. It can make a failure report more likely to be read. It can make a boring regression suite feel like something a team owns.

I was promoted not long after. I am not saying Cookie Monster did it. But I am also not ruling it out.

## Quick Applied Example

### Example: BugPilot


> Name the regression agents R2-D2, HAL, WALL-E, TARS, and Optimus instead of agent_1 through agent_5.

The failures can still be rigorous: "HAL deleted the test again" is more memorable than "agent_3 failed scenario 17." Interesting names, readable cases, and funny-but-useful failure summaries help humans pay attention.

Do not sacrifice coverage for jokes. Use personality to make the quality signal easier to notice and discuss.


## How AI Helped Test This Book

Yes, I used AI to test the book about testing AI. That felt recursive enough to be funny, but it was also useful.

The useful part was not asking a model, "Is this book good?" That question is too vague. The useful part was turning the book into a test surface. I asked AI to read it as different reader personas: Confidence Engineer, automation engineer, developer, architect, engineering manager, CTO, safety reviewer, and technical book editor. I often made that last role more specific by asking for feedback as if the AI were a professional technical book editor working at O'Reilly. That framing helped surface structural problems, repeated machinery, weak explanations, missing context, and sections that did not yet feel like part of one authored book. Each persona noticed different things. Confidence Engineers found weak examples. Managers wanted clearer release decisions. Developers wanted more concrete harnesses. Editors noticed where the book still sounded like assembled articles instead of a guided argument.

I also used AI as a tireless pattern finder. It looked for repeated phrases, scaffolded examples, generic links, duplicated anecdotes, weak transitions, stale current-source claims, figure-caption gaps, mobile layout problems, and places where examples no longer matched the fictional systems introduced in the front matter. Then I used ordinary scripts and searches to verify the claims where possible: counts of examples, From the Field notes, figures, appendices, generated files, source headings, and HTML artifacts.

The visual work was another loop. AI helped propose diagrams, but I still had to reject many of them. Some were too busy. Some had arrows that looked wrong. Some had text misaligned, overlapping, or too small for print. That was a nice reminder that AI can generate a candidate quickly, but quality still lives in review, taste, and iteration. The same pattern showed up in prose: AI could suggest examples, but the good ones needed specificity, friction, humor, and a reason to exist.

The most useful workflow was boring in the best way:

- Ask AI for critique.
- Convert the critique into concrete edits.
- Patch the source files.
- Rebuild the Markdown, HTML, DOCX, and PDF versions.
- Run stats, link, and figure checks.
- Inspect rendered pages and screenshots.
- Keep only the changes that improved the reader's confidence.

AI did not make the book correct. It made it cheaper to ask more questions. It increased the number of review passes I could afford. It helped find patterns a tired human would miss. It also introduced its own failure modes: overconfident suggestions, repetition, generic examples, false certainty, and a tendency to smooth away voice. That is the point of the book in miniature. AI is a force multiplier for testing, not a replacement for judgment.

So yes: the book is a case study in its own argument. Use AI to test more, test differently, and test earlier. Then verify the verifier.

## Expert Notes

When the system matters, treat interesting test design as part of quality communication. A useful eval artifact has technical fidelity and human salience. It preserves exact inputs, outputs, versions, scores, traces, and statistics, but also gives people names, narratives, and summaries they can remember.

Good failure labels should be stable, searchable, and respectful. They should not leak private data, mock users, hide severity, or create incentives to write clever names instead of good tests. The best labels become shared language for the team: short handles for real risks.

AI can help here. Use it to summarize clusters, title incidents, rewrite failure reports for different audiences, generate readable scenario names, and explain why a weird case matters. Then review the result like any other AI output. Funny is optional. Clear is mandatory.
