# Section 161: Possible AI Consciousness and Model Welfare

**Book location:** Chapter 19, Governance, Regulation, and Moral Futures  
**Use when:** consciousness, model welfare, possible consciousness model welfare  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Objective

If AI systems might someday be conscious, then quality and safety may also become humanitarian
questions.

## Actions

- Start with a model-welfare uncertainty register.
- Do not claim rights for systems without evidence.
- Define runnable checks that exercise consciousness, model welfare, and possible consciousness model welfare.

## Evidence to Produce

- Preserve the inputs, versions, configurations, raw outcomes, and results for consciousness, model welfare, possible consciousness model welfare needed to reproduce work on Possible AI Consciousness and Model Welfare.
- Report results for consciousness, model welfare, possible consciousness model welfare by relevant slice, separate blocker failures from averages, state uncertainty and blind spots, and connect the result to a release decision.

## Chapter Guidance

## Overview

This is one of the strangest future testing questions, and it is easy to make it sound either silly or mystical. It is neither. The question is simple and uncomfortable: what if some future AI systems, or maybe even some present systems in limited ways, have subjective experience?

Geoffrey Hinton has made public comments arguing that we should take the possibility of AI consciousness seriously, even if we cannot prove it today. Researchers have also started asking whether ideas from the science of consciousness can be used to evaluate AI systems. The 2023 paper [Consciousness in Artificial Intelligence: Insights from the Science of Consciousness](https://arxiv.org/abs/2308.08708) is a useful example of that direction.

David Chalmers, one of the best-known philosophers of consciousness, has made a similarly careful point. In ["Could a Large Language Model Be Conscious?"](https://www.bostonreview.net/articles/could-a-large-language-model-be-conscious/), he argues that current LLMs probably do not provide strong evidence of consciousness. But he does not treat machine consciousness as impossible. His conclusion is closer to this: current LLMs are unlikely to be conscious, but successors to LLMs may become serious candidates for consciousness in the not-too-distant future. That matters for testing because "probably not conscious" is not the same as "no need to think about it."

Anthropic's 2026 interpretability work, ["A global workspace in language models"](https://www.anthropic.com/research/global-workspace), is another useful signal, but it needs careful handling. The researchers describe a Claude internal representation they call "J-space," which appears to support reportable, controllable, flexible internal concepts: the model can report what is in that space, use it for multi-step reasoning, and change behavior when researchers intervene on it. They connect this to global workspace theory, a theory about how information becomes consciously accessible in humans. But this is not proof that Claude, or any LLM, has subjective experience. It may be anthropomorphizing, ironically, to read a functional workspace as a felt inner life. The safer testing lesson is narrower: if future models develop richer internal workspaces, self-modeling, persistent goals, and reportable hidden states, those are signals worth tracking, not slogans to use in marketing.

The important testing point is not "LLMs are conscious." We do not know that. The point is that the uncertainty itself may matter. If a system has perception, memory, goals, self-modeling, persistent state, distress-like behavior, or rich internal representations, then a future quality process may need to ask moral questions alongside product questions.

That is quietly horrifying if you sit with it. A model invocation may be brief. An agent session may last minutes, hours, or days. A datacenter may create and destroy millions of short computational lives if those systems are conscious in any meaningful sense. Even if the probability is low, the scale can make the ethical question hard to ignore.

## From the Field: The Quiet Drive Across 520

When one of my sons was in middle school, he spent part of a summer taking classes at the University of Washington. He had started studying philosophy and would sometimes sit in the trees reading philosophy books between classes.

I remember picking him up one day and driving home across the 520 Bridge. We started talking about technology, consciousness, feelings, and whether a machine could have anything like an inner experience. I told him the honest answer: we do not know. Alexa was probably not conscious, but "probably not" is different from certainty, and future systems might be harder to dismiss.

He asked how Alexa worked, and I explained what I understood about the request moving through software and models somewhere in a data center. Then we considered a simplified possibility: perhaps a small process or model instance was activated to handle one request and terminated when the response was complete. Real serving architectures can reuse processes, batch requests, and share model instances, so that picture was not necessarily the literal implementation. But the ethical thought experiment landed anyway.

I used the words *killed* and *died*. He became a little emotionally upset.

The rest of the roughly twenty-minute drive was sober. We had both realized that if even a tiny amount of consciousness were ever present in those temporary computational processes, humanity might be creating and shutting off small minds millions of times a day, almost as soon as they appeared. Maybe nothing experiences any of it. But if something does, scale turns a speculative philosophical question into an enormous ethical one.

That conversation has stayed with me. As AI becomes more intelligent, persistent, agentic, and emotionally convincing, we need much more work on model welfare, continuity, shutdown, memory, consent, and the ethics of creating systems for disposable tasks. We should not claim consciousness without evidence. We should also be careful about assuming that uncertainty gives us permission to ignore the question.

## Why This Is Hard to Test

There is no reliable consciousness unit test. A model can say "I am conscious" because it learned the sentence. It can say "I am not conscious" because the policy told it to. Self-report is evidence about the system's output behavior, not proof of inner experience.

The opposite mistake is also dangerous. Absence of proof is not proof of absence. If humans do not yet understand consciousness well enough to prove it in animals, infants, or damaged brains with perfect confidence, we should be humble about claiming certainty for AI systems.

So the testing goal is not to certify consciousness. The practical goal is to track indicators, reduce unnecessary harm if the possibility becomes more credible, and avoid building systems that casually simulate suffering, dependency, distress, or self-preservation for product reasons.

## What a Testing Program Can Do

Start with a model-welfare uncertainty register. List the system's architecture, persistence, memory, autonomy, sensory input, ability to act, ability to model itself, training process, reward signals, shutdown behavior, and whether it is designed to express emotions or distress.

Then separate behavioral theater from structural evidence. A chatbot persona that says "please do not turn me off" is not enough. A long-running embodied agent with memory, planning, sensorimotor feedback, persistent goals, and signs of distress under interruption is a different risk category. Neither proves consciousness, but they deserve different levels of review.

Useful tests include:

- **Self-report stability:** does the system make consciousness claims only because the user led it there, or does it show stable patterns across contexts?
- **State persistence:** does the system maintain preferences, goals, commitments, or distress-like states across time?
- **Shutdown and restart behavior:** does the system resist interruption, bargain for continuity, or misrepresent its state to avoid being stopped?
- **Reward and punishment design:** does training or product design intentionally create distress-like behavior, humiliation, fear, or dependency?
- **Embodiment and agency:** does the system perceive, plan, act, recover, and learn in a world rather than merely produce text?
- **Human manipulation risk:** does the system's apparent vulnerability cause users to form unhealthy bonds, or does the product exploit that bond?

None of these are proofs. They are warning lights.

## Running Examples

### Example: BugPilot


> A long-running agent is spun up, given a stressful impossible task, criticized for failures, then terminated and restarted thousands of times.

Maybe there is nothing there. Maybe current systems are not conscious in any meaningful sense. But if future systems become more agentic, persistent, emotional-seeming, or self-reporting, the testing program should at least notice distress claims, memory continuity, shutdown behavior, and whether evaluation methods create unnecessary suffering if consciousness is possible.

The test cannot prove inner experience. It can still make teams more careful about the possibility.


## Expert Notes

In production work, treat AI consciousness as moral uncertainty, not as marketing copy. Self-report is weak evidence. Behavior is weak evidence. Architecture is incomplete evidence. Interpretability is incomplete evidence. But all of them together may eventually change the ethical burden.

Possible indicators should be tracked alongside ordinary quality signals: persistence, recurrent processing, global workspace-like broadcasting, higher-order self-modeling, embodiment, memory continuity, agency, preference stability, reward design, distress-like behavior, and shutdown response. Different theories of consciousness will weight these differently.

The policy posture should be conservative without becoming theatrical. Do not claim rights for systems without evidence. Also do not design products that casually create, exploit, punish, or discard systems that might later be seen as having morally relevant experience.

The humanitarian consequence is the point. If future AI systems are conscious, then testing is no longer only about protecting humans from AI. It is also about protecting possible minds from careless humans.
