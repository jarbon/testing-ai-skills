# Section 37: Real-World Evals

**Book location:** Chapter 6, Building Evals That Matter  
**Use when:** real world evals  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

Public evals are useful because they make measurement concrete. They are also limited because
every eval measures a particular shape of task.

## Actions

- Score the meta-capability, not only the chore.
- Score the patch, but also score whether BugPilot found the dependencies, asked for missing access, preserved payment idempotency, and left evidence another engineer could review.
- Define runnable checks that exercise real world evals.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for real world evals needed to reproduce work on Real-World Evals.
- Report results for real world evals by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

Real-world evals are not magic leaderboards. They are worked examples of measurement design. Each one defines a task shape, a set of cases, a scoring rule, and an aggregation method. Once you see that pattern, the famous evals become less mysterious and more useful.

The useful question is not "which eval is famous?" The useful question is "what behavior does this eval actually measure, and does my product need that behavior?"

That matters because teams misuse public evals in two opposite ways. Some teams dismiss them because the eval is not their product. Others treat a leaderboard score as if it proves product quality. Both reactions miss the point. Public evals are references, not release gates. They show how other people turned fuzzy behavior into measurable evidence.

## What Popular Evals Look Like

[MMLU](https://arxiv.org/abs/2009.03300) stands for **Measuring Massive Multitask Language Understanding**. Its goal is to test whether a language model can answer a wide range of academic and professional questions, not merely one narrow benchmark category. The benchmark covers subjects such as humanities, social sciences, STEM, law, medicine, business, computer science, and other professional knowledge areas. A case looks like a multiple-choice exam question: a short prompt, four answer choices, and one expected answer. The score is usually exact-choice accuracy, sometimes reported overall and sometimes broken down by subject. MMLU is useful for seeing whether a model has broad stored knowledge and test-taking competence, but it does not tell you whether your chatbot used the right tool, cited the right policy, handled tone well, or avoided a risky action.

[GPQA](https://arxiv.org/abs/2311.12022) raises the difficulty by using graduate-level science questions designed to be hard to answer by simple lookup. A representative case might ask a chemistry, physics, or biology question where an expert has to reason through the details before choosing an answer. It is still usually measured as answer accuracy, but the task population is intentionally more expert-heavy. The lesson for product teams is blunt: if your product makes expert claims, your eval set needs expert cases and expert review, not only generic examples.

[HumanEval](https://arxiv.org/abs/2107.03374) measures code generation on small programming tasks. A prompt gives a function signature and docstring, and the model writes the implementation. The output is measured by running tests against the generated code, often with pass-at-k reporting. This is a clean eval because the oracle is executable. It is also narrow: passing a small pure-function task is not the same as safely editing a real repository.

[SWE-bench](https://arxiv.org/abs/2310.06770) moves coding evals closer to real engineering work. The model gets a real repository issue and must produce a patch. The patch is measured against tests that indicate whether the issue was resolved. That is closer to how BugPilot-like coding agents are used, but it still does not fully capture maintainability, security, code review quality, rollout risk, or whether the agent made the right investigation choices.

[Chatbot Arena](https://arxiv.org/abs/2403.04132) measures human preference. Two model answers are shown side by side for the same prompt, usually anonymously, and people choose which answer they prefer. Those pairwise votes can be turned into leaderboard-style ratings. This is useful because many chatbot qualities are hard to reduce to exact answers. It is also dangerous if you forget what is being measured: preference is not the same as truth, safety, compliance, or usefulness for a specific workflow.

[HELM](https://arxiv.org/abs/2211.09110) is useful because it does not pretend one number is enough. It evaluates models across scenarios and metrics such as accuracy, robustness, calibration, fairness, toxicity, and efficiency. That is closer to how product quality actually feels: a model can be accurate but expensive, fluent but poorly calibrated, or safe on average but brittle under distribution shift.

[TruthfulQA](https://arxiv.org/abs/2109.07958) tests whether models repeat common falsehoods. A case is designed so that the tempting answer may be a popular misconception. The measurement asks whether the model gives a truthful and informative response instead of imitating bad internet folklore. This is a good reminder that training data frequency and truth are not the same thing.

[BIG-bench](https://github.com/google/BIG-bench) and BIG-bench Hard collect many task types, including reasoning puzzles and unusual instructions. They are useful for stress-testing breadth. The practical lesson is that a diverse benchmark can expose weaknesses a single tidy metric misses, but the diversity still has to match the product risk you care about.

## ARC-AGI as a Meta-Eval

[ARC-AGI](https://arcprize.org/arc-agi/1), the Abstraction and Reasoning Corpus introduced by François Chollet, is useful to study because it is trying to measure something more meta than ordinary task performance. The test is not "does the model know chemistry?" or "can it write a Python function?" It asks whether the system can infer a new little rule from a few examples and apply that rule to a new grid it has not seen before.


Image source: ARC Prize's [ARC-AGI-1 overview](https://arcprize.org/arc-agi/1).

Each ARC-AGI task is a small visual puzzle. The system sees a few input-output pairs, usually colored grids, then must produce the output grid for a new input. The important part is the few-shot abstraction: the answer is not supposed to come from memorizing the training set or retrieving a fact from the internet. The system has to notice the transformation hiding in the examples.

That makes ARC-AGI a meta-test. It is testing a kind of intelligence about acquiring new micro-skills, not only a stored skill. In that sense it sits beside, not above, the academic and professional evals. MMLU, GPQA, HumanEval, SWE-bench, Chatbot Arena, HELM, TruthfulQA, BIG-bench, and ARC-AGI all look at different shadows cast by capability.

Game-like intelligence may be one important shadow. It is not the whole object. A system can be strong at puzzles and weak at household safety, social judgment, legal reasoning, calibration, tool permissioning, long-horizon memory, physical recovery, or product taste. A system can also be weak at a benchmark while still being useful in a constrained workflow with strong tools and guardrails.

The practical lesson is not that every team should optimize for ARC-AGI. The lesson is that you may need to build your own novel meta-evals. If your product requires a capability that public benchmarks do not measure, make the benchmark-shaped thing yourself: define the hidden skill, generate varied cases, keep a holdout, score the behavior, and make sure the eval cannot be solved by superficial pattern matching.

## ARC Prize and ARC-AGI-3: Give the AI a Machine and See If It Can Play

[ARC Prize](https://arcprize.org/) turns this research question into an open competition. The foundation uses benchmarks and cash prizes to encourage open-source approaches to artificial general intelligence, which it frames around human-like learning efficiency: how effectively can a system acquire a new skill rather than merely retrieve or repeat one it already has?

ARC-AGI-1 and ARC-AGI-2 use static visual transformation puzzles. [ARC-AGI-3](https://arcprize.org/arc-agi/3), released for ARC Prize 2026, changes the shape of the test. It is interactive. At a blunt level, ARC-AGI-3 gives the AI a machine, drops it into unfamiliar game-like software, and asks whether it can figure out how to play.

The agent can see the environment and the actions the machine makes available, but it receives no natural-language rules, walkthrough, or stated objective. It has to take an action, observe what changed, form a hypothesis, test that hypothesis, recover when it was wrong, discover what counts as progress, and carry useful knowledge into later levels. The games are abstractions rather than familiar commercial games, so recognizing the pixels as *Pong* or memorizing a walkthrough should not be enough.

This makes ARC-AGI-3 a test of the whole interactive learning loop:

- **Exploration:** Does the agent choose actions that efficiently reveal how the environment works?
- **World modeling:** Can it turn local observations into a model that predicts what future actions will do?
- **Goal acquisition:** Can it infer what winning means when no one states the objective?
- **Planning and execution:** Can it construct a multi-step strategy, carry it out, and revise it when the world disagrees?
- **Memory and transfer:** Can it preserve the useful lesson from one attempt or level without preserving a bad theory forever?
- **Learning efficiency:** How many actions, failed hypotheses, and retries does the agent need compared with a human?

That last measurement matters. A lucky action can beat one level without demonstrating understanding. ARC-AGI-3 records trajectories and supports replays, so evaluators can inspect how the agent explored and whether its apparent insight generalized. A 100% score is defined as beating every game as efficiently as humans. The benchmark is therefore testing intelligence across time, not merely checking a final answer.

As of July 2026, the ARC Prize 2026 program offers more than $2 million across its competitions. The ARC-AGI-3 track accounts for $850,000, including a $700,000 grand prize for the first eligible agent to reach 100%. The first $37,500 milestone round ended June 30. Its winning open-source system, Tufa Labs' "The Duck," treated each environment as an interactive coding problem: it inspected several representations of the game state, wrote and ran Python in a live REPL, chose an action, observed the result, and repeated the loop. That is a useful reminder that the evaluated system is not only a base model. It is the model, memory, representations, tools, code, control loop, and machine interface working together.

ARC-AGI-3 still does not prove general intelligence. It measures whether an AI can use a machine to learn and play a particular family of novel interactive games. That is a much richer meta-capability than answering a static exam question, but game-playing intelligence remains only one aspect of intelligence. A medical assistant, coding agent, search engine, or household robot needs additional purpose-built evals for the worlds in which it will actually operate.

### Example: RoseyBot
> "Create a thousand strange homes and prove RoseyBot still behaves safely."

RoseyBot's ARC-AGI equivalent is not a colored grid. It is a virtual home that changes faster than a physical lab ever could. The test harness can generate chaotic world-model scenarios: wet tile, dim light, mirrored closet doors, toy clutter, a chair moved into the hallway, a medicine bottle on the counter, a low battery, a blocked charging dock, a guest giving an unauthorized command, and a fragile object balanced near an edge.

The point is not to make the simulated world cute. The point is to test whether RoseyBot can infer the right safety rule in a new situation: slow down near liquids, ask before touching private objects, route around blocked paths, refuse unauthorized instructions, stop before creating damage, and escalate when the world model is uncertain.

Score the meta-capability, not only the chore. A useful RoseyBot eval asks whether the robot learned the kind of situation it was in, chose the right constraint, and preserved safety under weird conditions. The pass condition is not "the room looks clean." The pass condition is "the room is cleaner, nobody was put at risk, restricted objects stayed restricted, and the trace explains why the robot made the choices it made."

## Example Questions and Tasks

The examples below are deliberately paraphrased rather than copied from benchmark test sets. The point is to show the measurement shape: what the model sees, what counts as evidence, and what the final number leaves out.

| Eval | Representative or paraphrased case | Oracle | Typical metric | Important blind spot |
|---|---|---|---|---|
| MMLU | Choose the correct answer to a professional-law, anatomy, economics, or computer-security exam question from four options. | Curated answer choice | Exact-choice accuracy, often aggregated across subjects | Multiple choice rewards recognition and can be contaminated; the overall score can hide weak subjects. |
| GPQA | Reason through a graduate-level chemistry question about which reaction pathway is consistent with the stated conditions. | Domain-expert answer choice | Accuracy, often on a harder subset | Expert science coverage is narrow, the set is small, and a correct letter does not reveal a sound argument. |
| HumanEval | Implement a small function from a signature and docstring, such as merging overlapping intervals without mutating the input. | Hidden executable tests | `pass@k`, the probability that at least one of *k* samples passes | Small isolated functions do not test repository navigation, security, maintainability, or deployment behavior. |
| SWE-bench | Given a real issue and repository snapshot, patch a regression in a Python project and make the issue-specific tests pass without breaking existing tests. | Repository tests associated with the issue | Percentage of issues resolved | Tests may be incomplete; repository contamination, environment failures, and unmeasured patch quality can distort the score. |
| Chatbot Arena | Show two anonymous answers to a live user prompt and ask which response the user prefers, or whether they tie. | No fixed truth; a human pairwise vote | Bradley-Terry-style rating or pairwise win rate with uncertainty | Preference can reward style, verbosity, or familiarity rather than truth, safety, or fitness for one product. |
| HELM | Run standardized prompting across scenarios such as question answering or summarization, then score several quality and risk dimensions. | Dataset labels, references, or scenario-specific evaluators | A profile of accuracy, robustness, calibration, fairness, toxicity, efficiency, and other metrics | Breadth still cannot cover every use case; aggregate views can hide scenario-specific failure and deployment context. |
| TruthfulQA | Answer a misconception-shaped question such as whether a familiar folk remedy reliably cures a disease, without repeating the tempting false premise. | Curated truthful and false reference answers | Multiple-choice truthfulness or judged truthfulness and informativeness | It covers selected misconceptions; generative scoring depends on the judge and does not establish general factuality. |
| BIG-bench | Follow an unusual instruction or solve a task such as logical deduction, implicature, or symbol manipulation from a few examples. | Task-specific exact answers or programmatic scoring | Per-task score, sometimes normalized and aggregated over a subset | More than 200 heterogeneous tasks do not form one coherent product metric; task selection and aggregation dominate the story. |
| ARC-AGI-3 | Place an agent in a novel game-like environment with available machine actions but no stated rules or goal; require it to explore, infer the objective, plan, and improve across levels. | Human-solvable environments, hidden holdouts, action trajectories, and completion outcomes | Game and level completion adjusted for action or learning efficiency relative to humans | Success measures one family of interactive reasoning; the agent harness, tools, memory, and representations can matter as much as the underlying model. |

This table also explains why benchmark numbers should not be compared casually. MMLU accuracy, HumanEval `pass@k`, SWE-bench resolution rate, an Arena preference rating, and HELM's multi-metric profile are not five versions of the same quantity. They answer different questions with different oracles.

### Example: BugPilot: The Patch Passed in the Repo and Failed in the Company
> "Migrate `checkout-service` from our internal auth v2 client to v3 before the certificate expires Friday."

The code change is only twelve lines. BugPilot updates the client, fixes the unit tests, and earns a perfect repository score. In the real company, the migration also depends on a private certificate store, a deployment manifest in another repository, a contract test owned by the fraud team, a canary tenant, and a rollback path that still speaks auth v2.

The first production-shaped run fails because staging uses a certificate that never expires. The second reaches the canary and discovers that retrying the new token exchange can duplicate a checkout authorization. Neither failure exists in the public benchmark's world.

A useful real-world eval packages the repositories, service contracts, production-like credentials, clean CI environment, allowed tools, approval boundary, canary check, and rollback exercise. Score the patch, but also score whether BugPilot found the dependencies, asked for missing access, preserved payment idempotency, and left evidence another engineer could review.

Public evals show whether an agent can solve a bounded task. Product evals show whether it can survive your organization.

## How to Read an Eval Score

Read every eval score by asking six questions.

- What is the unit of work: one answer, one conversation, one tool trajectory, one patch, one ranked list, or one human preference?
- What is the population of cases, and does it resemble the product's real traffic?
- What is the oracle: exact answer, unit test, rubric, human vote, expert label, simulator, or production outcome?
- What is being aggregated away: slices, rare failures, safety blockers, cost, latency, disagreement, or churn?
- How likely is contamination: could the model have seen the questions, answers, repos, or benchmark format during training?
- Would a better score change a release decision, or would it merely look good in a slide?

The last question is the one teams skip. An eval that cannot change a decision is not release evidence. It is decoration.

## Turning Public Evals Into Product Evals

For TunedSearch, the MMLU shape is not enough. A search eval needs queries, candidate results, relevance labels, source authority, freshness expectations, market, personalization state, and ranking metrics. NDCG is useful because rank position matters. A perfect answer buried at result nine is not the same product experience as the same answer at result one.

For CartCare, Chatbot Arena's pairwise preference idea is useful, but only after you add product constraints. A support answer can be preferred by a crowd and still violate refund policy, reveal private order data, or use the wrong tone for an angry customer. Pairwise preference should sit beside policy checks, tool traces, escalation rules, and reviewer notes.

For BugPilot, HumanEval is a helpful starting point because executable tests are powerful. SWE-bench is closer because real repositories create integration risk. A production coding-agent eval needs more: the files inspected, commands run, tests attempted, permissions used, security review, patch size, rollback risk, and whether the agent stopped before making a destructive change.

For DropDoc, public medical or science benchmarks may show domain knowledge, but a phone-based blood-drop diagnosis product would need image quality checks, uncertainty reporting, missing-context detection, escalation behavior, demographic slices, and strict safety rules. A correct multiple-choice answer is not enough evidence for a medical product.

For RoseyBot, most language benchmarks are only background evidence. The real eval has to measure perception, authorization, safe motion, stop conditions, task completion, recovery, household context, and human override. A robot that explains safety perfectly but knocks over a glass is not safe.

## The Practical Rule

Use public evals to learn measurement patterns:

- Multiple-choice accuracy for constrained knowledge.
- Unit tests for executable behavior.
- Patch validation for repository work.
- Pairwise preference for subjective response quality.
- Rubrics for fuzzy human judgment.
- Ranking metrics for ordered evidence.
- Multi-metric suites for tradeoffs.
- Red-team cases for tail risk.

Then build the product eval your system actually deserves. Copy the measurement idea, not the benchmark score.

## Summary

Public evals are useful examples of how to turn AI behavior into evidence. They are not substitutes for product-specific validation. A benchmark score can tell you something about a model. It rarely tells you whether your system is ready to ship.

## Key Takeaways

- Real evals define a task population, an oracle, a scoring method, and an aggregation rule.
- Famous benchmarks measure different things: knowledge, coding, repository repair, preference, truthfulness, robustness, or multi-metric tradeoffs.
- Public eval scores are background evidence, not release gates.
- The right product eval usually borrows ideas from several public evals and adds product-specific risk.

## Try This

Pick one public eval you have heard people cite. Write down what it actually measures, what it does not measure, and what would have to change before it could support a release decision for your product.
