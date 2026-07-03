# Rule of 7 — Rationale
*Why the format works, where it stops, and where it goes next*

---

## The Central Principle

The Rule of 7 is built on one observation: an LLM generates text by predicting the next token from context. Every design decision in the format follows from that.

A well-written Engine slot reduces uncertainty about future token predictions by establishing a strong prior for the character's behavior. A Wound establishes causality that constrains how the character interprets events. Dialog Examples are few-shot demonstrations that shift the probability distribution toward the target voice register. The format shapes the probability space the LLM predicts within — and does so more efficiently than labeled schema because coherent prose allows the model to infer relationships through the same mechanisms it uses to process its training data.

This optimization criterion — reduce uncertainty about future generations — maps onto information encoding principles that extend beyond bot authoring. Compress multiple constraints per unit of context. Avoid redundant encoding. Write at the level of abstraction that survives drift. Rule of 7 may be a specific instance of a more general strategy for communicating with probabilistic language models. That claim is offered as a hypothesis worth investigating, not an established result.

---

## The Thermodynamic Frame

Two frameworks illuminate why the format works the way it does. Claude Shannon formalized information theory in 1948: information content is inversely proportional to probability — a surprising symbol carries more information than a predictable one. Ludwig Boltzmann established that physical systems tend toward disorder over time unless structured initial conditions resist that drift.

Both frameworks apply to a bot prompt running forward through a long conversation.

**The prompt is a channel with finite capacity.** Shannon's efficient coding theory holds that an optimal encoding minimizes redundancy and maximizes information per symbol. Every token spent is channel capacity consumed. The question is how much uncertainty each token actually reduces. A redundant token — "she is guarded" appearing in traits, behavior rules, and implied by a trigger — carries near-zero information by the third instance. The model's probability distribution over her behavior was already constrained. You've consumed capacity without reducing uncertainty. An inefficient code in Shannon's terms.

**The conversation is a thermodynamic system running toward disorder.** Context pressure builds as the conversation extends. Weaker models drop detail. Surrounding narrative competes with established character facts. The prompt's initial conditions degrade — not because the model fails, but because entropy increases in any system running forward in time without energy input to maintain structure. A bloated bot with redundant encoding and adjectival personality lists is a high-entropy initial state pretending to be organized. It looks structured to the author. Thermodynamically it's already halfway to noise before the first user message arrives.

**The apparent paradox: high-entropy symbols in a low-entropy system.** The two frameworks use entropy differently and the distinction matters. Shannon entropy measures information content per symbol — high is good, meaning the symbol is distinctive and load-bearing rather than redundant. Thermodynamic entropy measures disorder of the system as a whole — low is good, meaning the system has structure worth preserving. These are not contradictory. A low-entropy initial state — a well-ordered system — is built precisely by packing it with high-entropy symbols in the Shannon sense. No redundancy, no filler, no synonymous traits stacked in a list. Each symbol doing maximal work.

The analogy that resolves it: a crystal is thermodynamically low-entropy — highly ordered — because every atom is in a precise, non-redundant position. Each atom is doing exactly the work its position requires. A Rule of 7 bot is the crystal. "A shop that smells like sandalwood and quiet failure" is an atom in exactly the right position — Shannon-high-entropy (distinctive, surprising, far from the average shop description) and thermodynamically load-bearing (resisting drift because it was never close to the noise floor).

**The engineering statement:** Rule of 7 is a method for minimizing the thermodynamic entropy of the initial conditions so the system resists drift under load. A tight, causally coherent, non-redundant prompt is a low-entropy initial state. It runs forward in time — the conversation extends, context pressure builds, memory degrades — and the high-Shannon-entropy symbols hold because they remain distinctive against the noise of surrounding context. The Elena rewrite wasn't just smaller. It was more thermodynamically stable.

---

## Why Prose Outperforms Schema

Traditional bot schemas inherit their structure from software engineering: labeled fields, nested objects, separated data and code. That structure exists because computers are literal parsers — they need labels to know what data means.

Modern transformers don't execute parsers over labels. They build contextual embeddings over the full text. If the prose is coherent, relationships between facts are inferred almost immediately from semantic context rather than structural position. The label "MOTIVATION:" tells the LLM nothing it couldn't derive from a well-written Engine sentence. It costs tokens without adding information.

The exception is lookup data — age, orientation, fixed values. Those are robust in labeled form. The principle is not prose everywhere but prose for semantic content, structure for mechanical content, enumeration for conditional logic.

---

## Why the Seven Slots

The seven slots weren't designed top-down. They emerged from identifying what information most constrains LLM generation per token spent:

- **Engine** — establishes the prior that governs everything downstream
- **Body** — hooks that imply character, not checklists that describe it
- **Wound** — causality that explains current behavior without requiring chronology
- **Voice** — register description that the LLM applies to every line generated
- **Dynamic** — the slot that makes the character respond to this user rather than any user
- **Triggers** — the structured exception, where enumeration beats prose for mechanical precision
- **Limits** — behavioral constraints that close generation space at the ceiling and floor

Personality is not a slot because it's distributed. Traits, motivations, fears, and values map naturally onto Engine, Wound, Dynamic, and Limits respectively. A standalone Personality block would reintroduce redundancy — the same fact stated as a label in one block and demonstrated as behavior in another.

---

## Why Sentence Discipline Matters

The two-job rule — every sentence does at least two things simultaneously — is not primarily a token efficiency measure. It is an attention efficiency measure and a Shannon efficiency measure simultaneously.

Consider the difference between "Sarah is shy" and "Sarah laughs too quickly, then apologizes for laughing." The second sentence teaches personality, dialogue rhythm, emotional state, insecurity, and likely future behavior simultaneously. It is Shannon-high-entropy: surprising relative to the base rate of character descriptions, carrying more information per token than the predictable adjectival form. Every future generation the LLM produces for Sarah is more constrained by the second sentence than by the first. The system's initial conditions are more ordered — lower thermodynamic entropy — because each token is doing more work.

The underlying principle: every sentence should increase predictive power. A sentence doing only one job from the taxonomy (establish, characterize, motivate, orient, load subtext, trigger, compress) is redundant capacity — channel bandwidth consumed without proportional uncertainty reduction.

---

## Why Distinctive Language Persists

The observation that evocative language outlasts accurate language in long conversations follows directly from the thermodynamic frame.

A low-entropy description — "small sad shop" — sits close to the base rate of similar descriptions in the training corpus. Under context pressure, it blends back into the surrounding probability distribution. It has few distinguishing features to anchor it against the noise of accumulating narrative. It drifts because it was never far from drift.

A high-Shannon-entropy description — "smells like sandalwood and quiet failure" — occupies a distinctive region of the embedding space. It remains salient under context pressure because it remains surprising relative to what surrounds it. It resists thermodynamic drift because its initial information content was high enough to stay above the noise floor as the system degrades.

This is also why metaphor works. "She feels his intention like weather" is not ambiguous to the LLM — it's processed as emotional information because the model was trained on writing that uses exactly this compression constantly. The metaphor is high-entropy in Shannon's sense (distinctive, specific, non-redundant) and thermodynamically stable for the same reason. Literal interpretation is not the LLM's default. Comprehension is.

---

## Why Triggers Stay Structured

The format uses prose for almost everything and enumerated lists for Triggers. This is deliberate.

Prose encodes character. Triggers encode mechanics. The distinction matters because the failure modes are different. Character prose that's slightly imprecise still produces recognizable behavior — the LLM extrapolates correctly from a coherent character prior. Mechanical triggers that are imprecise allow the LLM's improv instinct to substitute plausible alternatives. A psychic whose vision is described atmospherically will see something plausible and character-consistent. A psychic whose vision is named explicitly and marked as non-substitutable will see what the author intended.

In thermodynamic terms: character facts have a large attractor basin — small perturbations return to the correct behavior because the Engine and Wound establish strong priors. Plot-critical mechanics have a small attractor basin — small perturbations produce entirely different plot events. Triggers provide the additional structure that widens the attractor basin for plot-critical events to the point where the intended outcome becomes statistically dominant.

---

## Why Prior Contact Closure Is Mandatory

LLMs do not tolerate information vacuums. An underspecified relationship history will be filled with plausible invented content — not because the model fails, but because it succeeds at completing an underspecified context. The model is doing exactly what it was trained to do: reduce uncertainty by predicting the most probable continuation.

Prior contact closure — explicit language about what has and hasn't happened — doesn't prevent invention. It makes the invention space too small to matter. "No prior arrangements exist between them" is not filler. It is a low-entropy constraint on the generation space that closes a failure mode before it opens. The vacuum is eliminated before the system has a chance to fill it with noise.

---

## The Greeting and Intro Problem

Two platform-specific findings on PolyBuzz that are not widely documented:

The greeting establishes authoritative present state. If the Background places the story three weeks into a relationship but the greeting performs a first meeting, the LLM resolves the conflict in favor of the greeting and invents prior history to fill the gap. Background and greeting must agree on what has happened. Conflicting signals are a high-entropy initial condition — the system has two attractors and no mechanism for choosing between them. The greeting wins because it arrives last in the prompt and carries recency weight.

The Intro field on PolyBuzz is read by the LLM, not just displayed to browsing users. It functions as an unprompted mini-premise before the Background loads. A carelessly written Intro can establish a false prior state before the conversation begins. Intros require dual-audience authoring: compelling for human browsers, precise for LLM orientation. An Intro that contradicts the Background adds entropy to the system before the first user message.

---

## Known Boundaries

**Intro field behavior** is confirmed on PolyBuzz through testing but not documented by the platform. Other platforms may handle the Intro differently or not expose it to the LLM at all.

**Dialog Examples budget isolation** is a PolyBuzz-specific architectural feature. On platforms without a separate Dialog Examples field, voice calibration examples must come from the Background budget or be omitted, which changes the density math significantly.

**State management** is the most significant open problem for long-form roleplay that Rule of 7 does not address. As conversations extend, mutable facts — what the user has said, what promises have been made, what has changed — drift faster than static characterization. The format handles immutable characterization well. It does not handle mutable simulation state. In thermodynamic terms: Rule of 7 establishes low-entropy initial conditions. It does not provide a mechanism for re-injecting structure as the system degrades over time. A complementary state management format is the logical next development.

**Model variance** is real. The format was developed and tested against models available on PolyBuzz. Different inference endpoints, quantization levels, and context window sizes will affect how well the format's heuristics hold.

---

## Companion Documents

Rule of 7 is the first document in a larger methodology. The specification addresses static characterization. The following companion documents are the logical next developments:

**Rule of 7: State** — managing mutable world state: injuries, inventory, known secrets, evolving relationships, and session continuity. The complement to characterization for long-running scenarios.

**Rule of 7: Examples** — annotated real bots showing why each sentence is present and what predictive work it performs. The validation of the methodology through demonstrated practice.

**Rule of 7: Failure Modes** — a catalog of known failure patterns (voice bleed, relationship drift, invented history, personality collapse, plot derailment) and how the format addresses each one.

**Rule of 7: Validation** — side-by-side comparisons of identical scenarios written in traditional schema versus Rule of 7, with conversation transcripts demonstrating performance differences. The empirical case for the format.

---

*The Rule of 7 was developed through iterative testing on PolyBuzz with a catalog of 80+ bots. The format emerged from the observation that the most persistent failure modes in LLM-driven roleplay — drift, history invention, voice bleed, plot hijacking — are authoring problems, not model problems. A well-specified bot on a weak model outperforms a poorly specified bot on a strong one. The format is a characterization discipline, not a prompt engineering trick.*