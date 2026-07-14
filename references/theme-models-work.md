# How Models Work

**Book location:** Chapter 15  
**Use when:** retrieval, multimodal, voice multimodal, benchmark, monitoring, RLHF, RLAIF, tokenization, fine-tuning, modern llms trained tested, synthetic data, llm training data pollution, reward model, rlhf rlaif reward model behavior  
**Source:** [*Testing AI: Engineering Confidence in Non-Deterministic Systems* by Jason Arbon](https://www.amazon.com/dp/B0H8J9GCK1)

## Actions

- Test accents, dialects, code-switching, background noise, interruptions, silence, long pauses, barge-in, pronunciation, speaker changes, low-quality microphones, phone audio, car audio, and room echo.
- Measure first-token latency, full-response latency, awkward silence, interruption recovery, and how often users abandon the conversation.
- Test captions, transcripts, alternate text, screen-reader compatibility, visual contrast, non-visual paths for visual tasks, audio-only fallbacks, keyboard access, and whether the system works for users with hearing, speech, vision, cognitive, or motor differences.
- Do not collapse soft quality into "vibes." Treat it as measurable.
- Use preference studies, pairwise comparisons, segment-level reporting, task completion, abandonment, correction rate, replay analysis, and human ratings for tone, trust, comfort, clarity, and brand fit.
- Ask where the data came from, who had authority to include it, what licenses apply, what private data might be present, which languages and regions are missing, what time period the data represents, and which product risks are invisible in the corpus.
- Check whether benchmark questions leaked into training.
- Check whether important subgroups disappeared during "quality" filtering.

## Evidence to Produce

Produce a decision-oriented evidence package: system and population, cases and slices, measurements and uncertainty, severe failures, known blind spots, and a ship, canary, hold, rollback, or collect-more-evidence recommendation.

## Read On Demand

- [058 Voice and Multimodal AI Testing](ch058-voice-multimodal.md)
- [113 How Modern LLMs Are Trained and Tested](ch113-modern-llms-trained-tested.md)
- [114 Testing LLM Training Data and AI Pollution](ch114-llm-training-data-pollution.md)
- [115 Testing RLHF, RLAIF, and Reward Model Behavior](ch115-rlhf-rlaif-reward-model-behavior.md)
- [116 Useful and Useless LLM Bug Reports](ch116-useful-useless-llm-bug-reports.md)
- [117 Visualizing, Debugging, and Editing LLM Concepts](ch117-visualizing-debugging-editing-llm-concepts.md)
- [118 How Modern LLMs Work: A Block Diagram](ch118-modern-llms-work-block-diagram.md)
- [119 Mechanism-Aware LLM Testing: The Strawberry Trap](ch119-mechanism-aware-llm-strawberry-trap.md)
- [120 How Image Generation Models Work](ch120-image-generation-models-work.md)
- [121 How Vision-Language Models Process Images](ch121-vision-language-models-process-images.md)
- [122 Fine-Tuned Models and Regression Risk](ch122-fine-tuned-models-regression-risk.md)
