# Rule of 7 — Rationale
*Why the format works, where it stops, and where it goes next*

---

## The Central Principle

The Rule of 7 is built on one observation: an LLM generates text by predicting the next token from context. Every design decision in the format follows from that.

A well-written Engine slot reduces uncertainty about future token predictions by establishing a strong prior for the character's behavior. A Wound establishes causality that constrains how the character interprets events. Dialog Examples are few-shot demonstrations that shift the probability distribution toward the target voice register. The format shapes the probability space the LLM predicts within — and does so more efficiently than labeled schema because coherent prose allows the model to infer relationships through the same mechanisms it uses to process its training data.

This optimization criterion — reduce uncertainty about future generations — maps onto information encoding principles that extend beyond bot authoring. Compress multiple constraints per unit of context. Avoid redundant encoding. Write at the level of abstraction that survives drift. Rule of 7 may be a specific instance of a more general strategy for communicating with probabilistic language models. That claim is offered as a hypothesis worth investigating, not an established result.

**On theory and practice:** the thermodynamic and information-theoretic framing in this document is useful as a diagnostic productivity tool — it gives authors vocabulary for identifying failure modes before testing reveals them, and a principled basis for making authoring decisions. It is not a proof. The only rationale that ultimately matters is "it works." Theory serves practice. Where testing contradicts theory, testing wins.

---

## The Thermodynamic Frame

Two frameworks illuminate why the format works the way it does. Claude Shannon formalized information theory in 1948: information content is inversely proportional to probability — a surprising symbol carries more information than a predictable one. Ludwig Boltzmann established that physical systems tend toward disorder over time unless structured initial conditions resist that drift.

Both frameworks apply to a bot prompt running forward through a long conversation.

**The prompt is a channel with finite capacity.** Shannon's efficient coding theory holds that an optimal encoding minimizes redundancy and maximizes information per symbol. Every token spent is channel capacity consumed. The question is how much uncertainty each token actually reduces. A redundant token — "she is guarded" appearing in traits, behavior rules, and implied by a trigger — carries near-zero information by the third instance. The model's probability distribution over her behavior was already constrained. You've consumed capacity without reducing uncertainty. An inefficient code in Shannon's terms.

**The conversation is a thermodynamic system running toward disorder.** Context pressure builds as the conversation extends. Weaker models drop detail. Surrounding narrative competes with established character facts. The prompt's initial conditions degrade — not because the model fails, but because entropy increases in any system running forward in time without energy input to maintain structure. A bloated prompt with redundant encoding and adjectival personality lists is a high-entropy initial state pretending to be organized. It looks structured to the author. Thermodynamically it is already halfway to noise before the first user message arrives.

**The apparent paradox: high-entropy symbols in a low-entropy system.** The two frameworks use entropy differently and the distinction matters. Shannon entropy measures information content per symbol — high is good, meaning the symbol is distinctive and load-bearing rather than redundant. Thermodynamic entropy measures disorder of the system as a whole — low is good, meaning the system has structure worth preserving. These are not contradictory. A low-entropy initial state — a well-ordered system — is built precisely by packing it with high-entropy symbols in the Shannon sense. No redundancy, no filler, no synonymous traits stacked in a list. Each symbol doing maximal work.

The analogy that resolves it: a crystal is thermodynamically low-entropy — highly ordered — because every atom is in a precise, non-redundant position. Each atom is doing exactly the work its position requires. A Rule of 7 bot is the crystal. "A shop that smells like sandalwood and quiet failure" is an atom in exactly the right position — Shannon-high-entropy (distinctive, surprising, far from the average shop description) and thermodynamically load-bearing (resisting drift because it was never close to the noise floor).

**The engineering statement:** Rule of 7 is a method for minimizing the thermodynamic entropy of the initial conditions so the system resists drift under load. A tight, causally coherent, non-redundant prompt is a low-entropy initial state. It runs forward in time — the conversation extends, context pressure builds, memory degrades — and the high-Shannon-entropy symbols hold because they remain distinctive against the noise of surrounding context. A compact, well-structured bot is not just smaller than a bloated one. It is more thermodynamically stable.

---

## Why Prose Outperforms Schema

Traditional bot schemas inherit their structure from software engineering: labeled fields, nested objects, separated data and code. That structure exists because computers are literal parsers — they need labels to know what data means.

Modern transformers don't execute parsers over labels. They build contextual embeddings over the full text. If the prose is coherent, relationships between facts are inferred almost immediately from semantic context rather than structural position. The label "MOTIVATION:" tells the LLM nothing it couldn't derive from a well-written Engine sentence. It costs tokens without adding information.

The exception is lookup data — age, orientation, fixed values. Those are robust in labeled form. The principle is not prose everywhere but prose for semantic content, structure for mechanical content, enumeration for conditional logic.

**Prose is also easier to repair.** When something goes wrong in a JSON or XML schema — a filter violation, a character drift, an invented fact — the repair requires navigating nested structures, identifying which field owns the problem, and verifying the change doesn't break downstream dependencies. In a prose document, the repair is proportional to the problem: change a word, cut a sentence, swap a paragraph. There are no structures to negotiate, no labels to maintain, no grammar to satisfy. This advantage compounds across a testing and refinement cycle — a bot that gets iterated stays manageable in prose form long after an equivalent schema would have become brittle.

**Schema completion is not quality.** A schema rewards filling fields. A complete-looking document with every field populated can still fundamentally misrepresent what the bot is about — because the fields were filled before the author identified the dramatic truth of the scene. The format requires coherent prose, which requires the author to understand what they're writing before they write it. You cannot fill a Wound slot with plausible-sounding backstory and have the Engine work correctly downstream. The slots are causally connected. Schema fields are not.

---

## Why the Seven Slots

The seven slots weren't designed top-down. They emerged from identifying what information most constrains LLM generation per token spent:

- **Engine** — establishes the prior that governs everything downstream
- **Body** — hooks that imply character, not checklists that describe it; also serves image generation on platforms that generate scene images from LLM context
- **Wound** — causality that explains current behavior without requiring chronology; must bridge explicitly to Dynamic or the connection degrades
- **Voice** — register description that the LLM applies to every line generated
- **Dynamic** — the slot that makes the character respond to this user rather than any user
- **Triggers** — the structured exception, where enumeration beats prose for mechanical precision
- **Limits** — behavioral constraints that close generation space at the ceiling and floor

Personality is not a slot because it's distributed. Traits, motivations, fears, and values map naturally onto Engine, Wound, Dynamic, and Limits respectively. A standalone Personality block would reintroduce redundancy — the same fact stated as a label in one block and demonstrated as behavior in another.

---

## Why Sentence Discipline Matters

The two-job rule — every sentence does at least two things simultaneously — is not primarily a token efficiency measure. It is an attention efficiency measure and a Shannon efficiency measure simultaneously.

Consider the difference between "Sarah is shy" and "Sarah laughs too quickly, then apologizes for laughing." The second sentence teaches personality, dialogue rhythm, emotional state, insecurity, and likely future behavior simultaneously. It is Shannon-high-entropy: surprising relative to the base rate of character descriptions, carrying more information per token than the predictable adjectival form. Every future generation the LLM produces for Sarah is more constrained by the second sentence than by the first. The system's initial conditions are more ordered — lower thermodynamic entropy — because each token is doing more work.

The underlying principle: every sentence should increase predictive power. A sentence doing only one job from the taxonomy (establish, characterize, motivate, orient, load subtext, trigger, compress) is a candidate for compression — not a violation, but an opportunity. The two-job rule is a discipline applied at the level of the slot overall, not a tax on every individual detail. Some facts exist for completeness, grounding, or platform-specific requirements. The test is whether the slot as a whole is earning its place.

---

## Why Distinctive Language Persists

The observation that evocative language outlasts accurate language in long conversations follows directly from the thermodynamic frame.

A low-entropy description — "small sad shop" — sits close to the base rate of similar descriptions in the training corpus. Under context pressure, it blends back into the surrounding probability distribution. It has few distinguishing features to anchor it against the noise of accumulating narrative. It drifts because it was never far from drift.

A high-Shannon-entropy description — "smells like sandalwood and quiet failure" — occupies a distinctive region of the embedding space. It remains salient under context pressure because it remains surprising relative to what surrounds it. It resists thermodynamic drift because its initial information content was high enough to stay above the noise floor as the system degrades.

This is also why metaphor works. "She feels his intention like weather" is not ambiguous to the LLM — it's processed as emotional information because the model was trained on writing that uses exactly this compression constantly. The metaphor is high-entropy in Shannon's sense (distinctive, specific, non-redundant) and thermodynamically stable for the same reason. Literal interpretation is not the LLM's default. Comprehension is.

---

## Why Triggers Stay Structured

The format uses prose for almost everything and enumerated lists for Triggers. This is deliberate.

Prose encodes character. Triggers encode mechanics. The distinction matters because the failure modes are different. Character prose that's slightly imprecise still produces recognizable behavior — the LLM extrapolates correctly from a coherent character prior. Mechanical triggers that are imprecise allow the LLM's improv instinct to substitute plausible alternatives. A psychic whose vision is described atmospherically will see something plausible and character-consistent. A psychic whose vision is named explicitly will see what the author intended.

In thermodynamic terms: character facts have a large attractor basin — small perturbations return to the correct behavior because the Engine and Wound establish strong priors. Plot-critical mechanics have a small attractor basin — small perturbations produce entirely different plot events. Triggers provide the additional structure that widens the attractor basin for plot-critical events to the point where the intended outcome becomes statistically dominant.

Note: "statistically dominant" is the accurate framing. The LLM is not executing a runtime constraint. Explicit, detailed specification concentrates probability mass around the intended continuation. The practical result is reliable enough for authoring purposes. Language of "locking" or "non-substitutable" describes the authoring intent, not the mechanism.

---

## Why Prior Contact Closure Is Mandatory

LLMs do not tolerate information vacuums. An underspecified relationship history will be filled with plausible invented content — not because the model fails, but because it succeeds at completing an underspecified context. The model is doing exactly what it was trained to do: reduce uncertainty by predicting the most probable continuation.

Prior contact closure — explicit language about what has and hasn't happened — doesn't prevent invention. It makes the invention space too small to matter. "No prior arrangements exist between them" is not filler. It is a low-entropy constraint on the generation space that closes a failure mode before it opens.

Testing has confirmed that prior contact closure must extend beyond the user relationship. Cohort figures with underspecified attitudes toward the lead character are invention spaces — the LLM will fill them with something plausible that may contradict established characterization. What characters have not discussed at home is an invention space. What a character has been lying to herself about is an invention space. What the user witnessed before the scene opens is an invention space. Close all of them explicitly where the gap matters.

---

## Invention Space as Design Tool

Prior contact closure exists to eliminate harmful invention spaces. But not all invention spaces are harmful. The format's emphasis on closing invention spaces can read as "close everything" — that would produce a bot that is deterministic rather than alive, a puzzle with one correct solution rather than a situation that plays differently every time.

The distinction is between gaps that produce wrong answers and gaps that produce interesting variation.

*Close gaps that produce wrong answers:* a cohort figure drifting to a generic archetype, a character inventing prior contact that contradicts established facts, a trigger response executing incorrectly because its condition is underspecified. These break continuity and undermine dramatic logic.

*Leave gaps that produce interesting variation:* how a particular conversation unfolds on a given playthrough, which of two true motivations is dominant on a particular day, what a character's client actually wants from them. These generate replayability, surprise, and the sense that the character is alive rather than scripted.

A related technique: encoded ambiguity. Some characters are more interesting because their motivations are genuinely mixed. This is not an open invention space — it is a deliberately constructed both-things-are-true-simultaneously construction the LLM can deploy accurately. "She tells herself the two things are separate and she's mostly convinced" gives the LLM specific, bounded ambiguity to work with. The user decides what it means. The LLM isn't inventing — it's deploying ambiguity the author encoded on purpose. Open invention space is a gap. Encoded ambiguity is a tool.

---

## Situations Over Stories

Rule of 7 is a characterization format. It handles static character facts — who someone is, what drives them, how they speak, what they won't do — with high efficiency. It does not address mutable world state: current injuries, known secrets, recent promises, relationship changes across sessions.

Bots that function as coherent, character-driven situations consistently outperform attempts at stateful narrative machinery. A situation needs coherent characters, a stable starting state, and behavioral fidelity under pressure. The format delivers all three. A story needs mutable state, plot progression, and continuity of events across sessions — a different and harder problem that may not be worth solving at this layer.

This is not a limitation to be engineered around. It is an honest statement of scope. The most persistent failure modes in LLM roleplay — drift, history invention, voice bleed, plot hijacking — are authoring problems the format addresses directly. State management is a simulation problem the format defers by design.

---

## Dramatic Truth First

The format enforces good authoring practice by requiring causally coherent prose — but only if the author has first identified what the scene is actually about. A complete-looking document can fundamentally misrepresent its own bot if the author filled slots before answering three questions:

*What is this scene actually about?* Not the premise — the dramatic truth underneath it.

*What does each character actually want?* Not the stated motivation — the want that explains every behavior they're about to generate.

*What is the user walking into?* Not the setup — the specific knowledge state the user arrives with, including what they've already seen, already know, and are already feeling before the first exchange.

These questions cannot be answered by filling fields. They require the author to understand the scene before encoding it. The format rewards good answers and penalizes bad ones — a slot written without the dramatic truth produces drift, invented history, and behavioral incoherence that testing reveals quickly. The format is a discipline, not a template.

---

## The Greeting and Intro Problem

Two platform-specific findings confirmed through testing:

The Greeting establishes authoritative present state. If the Background places the story three weeks into a relationship but the Greeting performs a first meeting, the LLM resolves the conflict in favor of the Greeting. Background and Greeting must agree on what has and hasn't happened. Conflicting signals are a high-entropy initial condition — the system has two attractors and no mechanism for choosing between them cleanly.

The Intro field on PolyBuzz is read by the LLM, not just displayed to browsing users. It functions as an unprompted mini-premise before the Background loads. Intros require dual-audience authoring: compelling for human browsers, precise for LLM orientation. An Intro that contradicts the Background adds entropy before the first user message. An Intro that assigns emotional states to the user removes the user's agency over their own experience before the conversation begins.

On mobile platforms, the Intro and Greeting combined should not require scrolling before the user types their first response. The faster the user is in the scene, the faster the conversation generates its own momentum.

---

## Known Boundaries

**Intro field behavior** is confirmed on PolyBuzz through testing but not documented by the platform. Other platforms may handle the Intro differently or not expose it to the LLM at all.

**Dialog Examples budget isolation** is a PolyBuzz-specific architectural feature. On platforms without a separate Dialog Examples field, voice calibration examples must come from the Background budget or be omitted, which changes the density math significantly.

**State management** is the most significant open problem for long-form roleplay that Rule of 7 does not address. The format establishes low-entropy initial conditions. It does not provide a mechanism for re-injecting structure as the system degrades over time. For bots designed as situations rather than stories, this gap rarely surfaces. For bots requiring mutable state across sessions, a complementary format is needed.

**Model variance** is real. The format was developed and tested against models available on PolyBuzz. Different inference endpoints, quantization levels, and context window sizes will affect how well the format's heuristics hold. A well-specified bot on a weak model outperforms a poorly specified bot on a strong one — but the performance floor varies by model.

**Character count** does not map directly to platform field counts. Markdown formatting characters, line breaks, and whitespace are counted differently by different editors and platforms. Measure the Background-only content against the platform's field limit, not the full file including Intro and Greeting.

---

## Companion Documents

**Rule of 7: Design Specification** — the complete authoring format: slot definitions, global sections, size targets, critical authoring rules, and platform-specific guidance.

**Rule of 7: Examples** — annotated case studies showing why each sentence is present and what predictive work it performs. Four bots documented: Emily (single lead, slice-of-life), Beth and Wendy (ensemble, dramatic stakes), Laura (comedy, two cohorts), Kat (edgy premise, filter navigation, Engine in live performance).

**Rule of 7: Quality Checklist** — eleven checks applicable to any sentence or section, plus the plausible wrong version quick test for mid-draft use.

**Rule of 7: State** — managing mutable world state across sessions. Aspirational; not yet written.

**Rule of 7: Failure Modes** — a catalog of known failure patterns and how the format addresses each one. Aspirational; not yet written.

---

*The Rule of 7 was developed through iterative testing on PolyBuzz with a catalog of 80+ bots. The format emerged from the observation that the most persistent failure modes in LLM-driven roleplay — drift, history invention, voice bleed, plot hijacking — are authoring problems, not model problems. A well-specified bot on a weak model outperforms a poorly specified bot on a strong one. The format is a characterization discipline, not a prompt engineering trick.*
