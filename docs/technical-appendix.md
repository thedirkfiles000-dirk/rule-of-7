# Rule of 7 — Technical Appendix
*Hypotheses and mechanisms for readers with machine learning backgrounds*

The claims in this document are offered as hypotheses grounded in observed behavior rather than controlled experimental results. The format was developed empirically through bot authoring practice, not through controlled ML experimentation. Correction and refinement from technically informed readers are welcome.

---

## On the Core Mechanism

The Rule of 7 is grounded in one observation: LLMs generate text by predicting the next token from context. Everything in the format follows from that.

The format operates on two levels simultaneously. First, semantic characterization: coherent prose narrows the probability distribution the LLM predicts within by establishing strong priors for character behavior, motivation, and voice. Second, behavioral conditioning: modern instruction-tuned models have been explicitly trained through supervised fine-tuning and reinforcement learning to treat imperative language as learned control signals. "You are," "Never," and "Always" are not merely semantic context — they trigger conditioned compliance behaviors that are distinct from passive next-token prediction. Rules placed early in the prompt leverage both mechanisms: they establish semantic priors and activate instruction-following conditioning.

The format therefore does not rely solely on shaping probability space, nor solely on issuing instructions. It uses both, and the two mechanisms reinforce each other when the prompt is well-structured.

---

## On the Information Theory Framing

The central optimization criterion — reduce uncertainty about future generations — maps directly onto information-theoretic principles. Compress multiple constraints per unit of context. Avoid redundant encoding. Write at the level of abstraction that survives drift. These are the same principles that govern efficient encoding in other domains.

Rule of 7 may be a specific instance of a more general information encoding strategy for probabilistic language models rather than a prompt engineering convention specific to roleplay. The repeated ideas throughout the specification — maximize predictive information per token, avoid redundant encoding, prefer high-level abstractions over low-level facts — are consistent with efficient coding theory applied to a probabilistic generative system.

This framing is offered as a hypothesis worth investigating. It is not a claim that the format was designed with information theory in mind — it was not. The convergence is empirical.

---

## On Positional Priority

Early versions of this specification claimed that earlier content receives higher attention weight. This is directionally true but mechanistically overstated for modern models.

GPT-3 era models showed strong primacy effects due to their positional encoding schemes and context window limitations. Modern long-context models with RoPE scaling, attention sinks, and improved positional encoding have substantially reduced but not eliminated this effect. Beginning-of-context retains some privilege, but the effect is weaker and less reliable than earlier transformer architectures exhibited.

The practical guidance — place Rules and Engine early — remains valid as a heuristic for a different reason: early placement reduces competition with later narrative detail and establishes priors before the model has accumulated conflicting context. This is a weaker but more defensible claim than positional attention weighting. It should be treated as a useful heuristic, not a mechanistic guarantee.

---

## On Markdown as Semantic Chunking

The claim that `##` headings function as meaningful chapter markers for LLMs is probably correct in effect but uncertain in mechanism.

The LLM was trained on vast quantities of Markdown-formatted text — technical documentation, wikis, README files — where heading hierarchy consistently correlates with semantic boundaries. Two candidate mechanisms exist: the model has learned to treat headings as meaningful separators (a learned semantic association), or headings simply create lexical anchors that reduce interference between adjacent sections by increasing token distance between related content clusters (a positional effect). The practical outcome — reduced bleed between character blocks — is consistent in testing. The mechanism behind it remains an open question.

The authoring implication is the same regardless of mechanism: use heading hierarchy deliberately to separate content that should not bleed between sections.

---

## On Plot Locking

Earlier versions of this specification used language like "locked" and "non-substitutable" to describe Trigger entries for plot-critical events. This language has been replaced with "statistically dominant" and "alternatives unattractive" throughout.

The actual mechanism is probabilistic, not deterministic. The LLM is not executing a runtime constraint. Explicit, detailed specification of a plot-critical event concentrates probability mass around the intended continuation, making alternative continuations statistically less likely to be generated. The model predicts tokens from a context that strongly favors one outcome. The practical result is reliable enough for authoring purposes. The language of "locking" was a useful authoring metaphor but an inaccurate technical description.

---

## On Prose Versus Structure

The claim that prose outperforms rigid schema is supported by the observation that modern transformers build contextual embeddings over the full text rather than executing parsers over field labels. Coherent prose allows the model to infer relationships through distributional semantics — the same mechanism it uses to process its training corpus. A labeled field adds no inferential value that well-written prose doesn't already provide.

However, this is not universal. Certain structured information is genuinely robust in labeled form:

- Lookup data (age, height, fixed values) is difficult to misrepresent in a labeled field and benefits from the precision of explicit structure.
- Enumerated conditionals (triggers, limits) benefit from structural clarity because the failure mode of imprecision is different — a prose trigger that's slightly vague allows the improv instinct to substitute; a bulleted trigger with explicit content does not.
- Inventory, state, and other simulation data benefits from structured representation for the same reason.

The principle is therefore not prose everywhere but a three-way division: prose for semantic characterization, structure for lookup data, enumeration for conditional mechanics.

---

## On Evocative Language and Drift Resistance

The observation that distinctive language outlasts accurate language in long conversations is consistent with how attention mechanisms weight semantically salient tokens.

A phrase like "smells like sandalwood and quiet failure" is more semantically distinctive than "small declining shop" — it occupies a more unique region of the embedding space. Under the context pressure that produces drift in long conversations, more distinctive embeddings are less likely to be competed away by surrounding narrative content. The evocative phrase survives because it has fewer near-neighbors in the model's semantic space.

This is a hypothesis consistent with transformer behavior rather than a verified experimental result. Controlled testing — comparing drift rates for evocative versus accurate descriptions of the same character attribute across conversation length — would be required to confirm it.

---

## On Few-Shot Calibration via Dialog Examples

The use of Dialog Examples as voice calibration is grounded in established few-shot learning behavior. Demonstration examples shift the model's output distribution toward the demonstrated register more reliably than prose descriptions of the same register.

"She deflects with humor" is a description. It tells the model what to do but relies on the model's prior distribution over "deflecting with humor" to determine what that looks like. An example of her deflecting with humor with a specific challenge prompt and a specific response is a demonstration. It directly narrows the distribution by providing a concrete sample of the target output.

Demonstrations are more predictively constraining than descriptions per token spent. This is why Dialog Examples belonging in a separate budget-isolated field rather than embedded in prose Background is architecturally significant on platforms where that separation exists — it allows the author to spend demonstration tokens without consuming characterization budget.

The practical implication: prioritize emotional register variation over content variety in Dialog Examples. The same character under four different emotional pressures (guarded, deflecting, direct, frightened) provides more distributional coverage than four examples of the character in similar emotional states discussing different topics.

---

## On the Information Hierarchy

A reviewer proposed a priority ranking for the seven slots based on predictive importance rather than literary convention:

1. Rules
2. Engine
3. Dynamic
4. Triggers
5. Wound
6. Voice
7. Limits
8. Body

This ranking reflects the observation that Engine and Dynamic most directly constrain per-exchange generation. Engine establishes the character's behavioral prior. Dynamic constrains how that prior expresses in response to the specific user. Together they determine more about what the model generates in any given exchange than the remaining slots combined.

The specification places Engine first in the character block for this reason. It does not enforce a strict ordering of remaining slots because Wound and Dynamic are causally linked in ways that make their relative priority context-dependent — for some characters the Wound is the highest-value slot because it explains everything downstream; for others the Dynamic is dominant because the user relationship is the primary driver of scene behavior.

Authoring clarity and causal coherence are weighted against strict predictive hierarchy for practical usability. Authors should treat Engine and Dynamic as the two highest-priority slots and order the remainder based on which facts are most load-bearing for the specific character.

---

## Open Questions

The following are unresolved questions that empirical testing or ML expertise could address:

- Does heading-separated structure genuinely reduce semantic bleed between character blocks, and if so, is the mechanism learned semantic association or positional token distance?
- Does evocative language produce measurably lower drift rates than accurate language for equivalent semantic content, and across what conversation lengths?
- Do the positional priority heuristics hold consistently across different model architectures and context window sizes, or are they GPT-3 era artifacts that have largely decayed?
- Is the instruction-tuning conditioning effect (imperative language as learned control signal) consistent across models trained with different RLHF approaches, or does it vary significantly by training methodology?
- Does the few-shot demonstration effect in Dialog Examples scale with example count, and is there a point of diminishing returns within the 10,000 character budget?

---

*The Rule of 7 was developed through iterative testing on PolyBuzz with a catalog of 80+ bots. The format emerged from the observation that the most persistent failure modes in LLM-driven roleplay — drift, history invention, voice bleed, plot hijacking — are authoring problems, not model problems. A well-specified bot on a weak model outperforms a poorly specified bot on a strong one. The format is a characterization discipline, not a prompt engineering trick.*
