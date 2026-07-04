# Rule of 7 — Examples
*Annotated real bots showing why each sentence is present and what predictive work it performs.*

---

## Example 1 — Emily
*Single lead character, slice-of-life, coffee shop meet-cute. No plot mechanics, no dramatic stakes. Rich personality is the whole game.*

---

### The Conversion

Emily was converted from a verbose JSON/code-heavy bot manager format. The original export was approximately 9,600 characters of nested schema — labeled fields, separated data and behavior, personality blocks restating what other fields already implied. The Rule of 7 conversion landed at 5,772 characters on the first pass, later refined to 6,405 characters after adding depth to cohort entries, fixing slot placement errors, and strengthening causal bridges. Net reduction: approximately 40% while adding causal structure the original lacked entirely.

The original was spending its overhead on:
- Schema scaffolding — nested objects, repeated keys, labeled subfields
- A standalone Personality block restating traits already implied by Engine and Wound
- Skills and hobbies as inert lists rather than Triggers doing mechanical work
- Dialog examples embedded in Background rather than their own field

---

### What Each Slot Is Doing

**Engine** — *"Emily wants genuine connection the way some people want to be impressive — quietly, without making it a project."*

Two jobs simultaneously: establishes the core drive and immediately distinguishes it from a more common alternative (performing warmth, seeking validation). The second sentence — *"she's good at people because she actually likes them, which is rarer than it sounds"* — does three: characterizes, motivates, and loads subtext about how most people in her cohort operate. The contradiction in the final sentence — reads rooms well, can't read her own wants — is the engine's load-bearing tension. Every behavior the LLM generates for Emily should be consistent with someone who is genuinely perceptive about others and genuinely uncertain about herself.

**Wound** — *"She turned down better-paying work after graduation to take the nonprofit job, and the people who loved her most thought it was idealism she'd grow out of."*

The Wound does four things in two sentences: establishes the biographical fact, encodes the emotional content (underestimated by people who meant well, which is a specific and painful flavor of underestimation), produces the behavioral output (calibrated eye for performance, clocks it fast), and bridges forward into Dynamic without requiring a separate explanation. The original had this material buried in backstory as neutral biography. Pulling it forward as the load-bearing causal fact changed the character's behavioral coherence entirely.

**Dynamic** — *"An accidental entrance is about the least performative way to meet someone, which is partly why it registered."*

This is the Wound→Dynamic bridge added after checklist review. Without it, Wound and Dynamic sat adjacent but causally unconnected — the LLM had to infer that her performance-detection was why the user's accidental entrance registered as interesting. The bridge closes that inference gap and makes the connection explicit. One sentence, zero new content, significant gain in causal coherence.

**Triggers — notebook entry** — original: *"If pressed, she's a little honest about it."*

Flagged by the plausible wrong version test: what would a plausible wrong version of "a little honest" look like? Almost anything emotionally vulnerable. The LLM would fill "a little honest" with whatever confession felt appropriate in the moment — which might be right, might not be. Revised to: *"she admits it's mostly starts of things she doesn't finish — and that she's not sure if that's a style or an avoidance."* Now the content of honesty is specified. The invention space collapses from "anything vulnerable" to "this particular unresolved thing."

---

### Cohort Entries — What Went Wrong and Why

**Ryan's original entry:** *"Emily's older brother, 28, construction. Protective without making it a personality. Emily trusts his judgment even when she argues with it."*

In live testing, Emily described Ryan as "convinced I'll never find peace" — invented detail that contradicted his characterization. The LLM filled an underspecified gap with something plausible: a protective older brother who worries about his sister's choices is a common archetype, and "construction worker who has strong opinions about the nonprofit job" is a short inferential step from "protective."

Three fixes applied:
1. Added a non-substitutable behavioral anchor: *"Shows up with tools before you've finished explaining the problem"* — specific enough to resist substitution.
2. Made the dynamic two-directional: *"Emily argues with his judgment and then usually takes it"* — constrains both sides.
3. Added the perception/reality split: *"Emily reads him as quietly protective; what she doesn't fully clock is that he made his peace with her choices years ago and just doesn't bring it up anymore"* — closes the invention space and encodes the gap as an explicit character fact.

**Sophie's entry** received the same perception/reality treatment: *"What she doesn't quite see is that Sophie calls her specifically because Emily is the person she most wants to be like."* Emily reads Sophie as chaotic; the reality is that the chaos is directed. That gap is character-rich and worth encoding — it says something about Emily's blind spot as much as it says something about Sophie.

**Leah's entry** was left with a single layer by design. Emily knows Leah deeply — they've been close since sophomore year. The perception gap is small and not dramatically useful. A two-layer entry where the layers are nearly identical wastes space and implies a false dramatic tension.

---

### The Body Slot Problem

The original Body entry included the notebook: *"The notebook on the table has a cover worn soft from use."*

Flagged by checklist item F — belongs in this slot? The notebook is a prop, not appearance. In the opening scene it's a stationary object on the table. In the Body slot it becomes a persistent attribute that could follow Emily inappropriately across scenes or be forgotten entirely. The correct location is Triggers, where it fires as behavior rather than existing as a fact. The notebook was already in Triggers. The Body mention was redundant and misplaced. Cut.

Body was also revised to serve the platform's Live Photo feature — PolyBuzz generates an image of the current scene after extended conversations, apparently from LLM context. Body therefore serves two functions: characterization hooks and visual inventory for image generation. Details were written to satisfy both: specific enough to generate from, evocative enough to persist under context pressure. *"A wave she doesn't fight"* is stickier than *"wavy hair."* *"Eyes that shift toward green in good light"* is more distinctive than *"hazel eyes."*

The two-job rule applies at the slot level, not to every individual detail. The freckles line — *"small freckles across her nose that get more pronounced in summer"* — does one job: visual inventory. That's legitimate. Not every detail needs to carry deeper meaning.

---

### Validated Behavior

In live testing with a user playing a teacher, Emily steered a casual conversation about school and young people toward the question: *"How do you handle parents who might be disappointed that their son or daughter isn't on the path they'd hoped?"*

The user didn't notice the turn until it had already happened.

This is the Engine and Wound operating together without surfacing as exposition. Emily's drive for genuine connection plus her wound of being underestimated by people who meant well produced exactly this behavior: she found the professional question that was also a personal one, asked it, and listened. She didn't say "that reminds me of my own experience." She asked you about yours — which told her what she needed to know about how you see the situation she lived through.

A less specified character would have made the connection explicit and broken the spell. Emily found the oblique approach because the Background gave her a reason to without telling her to.

This is what a well-specified Wound produces: not exposition, but behavior shaped invisibly by history.

---

### Intro and Greeting — Before and After

**Original Intro:** *"She spilled her latte. Somehow you're the one who feels bad about it. Emily, 26, nonprofit marketer — warm, quick-witted, and genuinely good company. No agenda. Just good coffee and better conversation."*

Problems: assigned emotional state to the user ("you're the one who feels bad"), contradicted the Greeting's inciting incident (Intro says she spilled; Greeting says the user's bag clips the table), and did scene-setting that competed with the Greeting before the conversation began.

**Revised Intro:** *"Emily is exactly where she wants to be. The question is whether you're interesting enough to be part of it."*

Two sentences. Browser-facing. Implies the dynamic without spoiling it. Creates curiosity. Makes no scene-specific claims the Greeting could contradict. Stable across bot updates.

**Original Greeting:** 138 words across four text blocks. The input field was not visible without scrolling on mobile. Emily didn't speak until the third paragraph.

**Revised Greeting:** 94 words. Entire Greeting fits on screen with the input field visible. User can read everything and start typing without scrolling.

*Authoring rule confirmed by testing:* the Intro and Greeting combined should not require scrolling before the user types their first response. On mobile, that means roughly one glance for the Intro and one screen for the Greeting. The faster the user is in the scene, the faster the conversation generates its own momentum.

---

---

## Example 2 — Beth and Wendy
*Two-character ensemble, emotionally charged domestic scenario. One lead character with a full seven-slot treatment. One supporting character reduced to a rich cohort entry. A plot with controlled information release and genuine dramatic stakes.*

---

### The Conversion

This bot presented a more complex conversion challenge than Emily — two characters, an ensemble dynamic, a plot that had to unspool at a controlled pace, and emotional stakes requiring careful management. The original schema was approximately the same character count as the 10,000 character limit but produced a bot that fundamentally misrepresented its own dramatic logic.

The original's critical failure: it was written as if Beth chose to confess. She didn't. She got caught. The user picked up their wife from a police station and saw a woman they barely recognized standing next to her. That is the dramatic engine — honest-because-caught versus honest-by-choice is an entirely different scene from honest-because-she-decided-to-be. The original schema buried this distinction in labeled fields where it couldn't do work. The conversion forced the question: what is this scene actually about?

---

### Dramatic Truth First

The most important step in this conversion happened before any slot was written. Three questions had to be answered:

*What is this scene actually about?* — A marriage encountering the consequences of a feeling that was never named.

*What does each character actually want?* — Beth wants to be fully loved and fully known, and tonight those two things are in conflict for the first time. Wendy wants genuine connection and a professional foothold, and isn't entirely sure which one is driving her.

*What is the user walking into?* — Not a blank slate. The user was at the station. They saw Wendy. They know something happened. They don't know what. They're already doing math.

None of this was recoverable from the original schema without reading between the fields. The format forced it into the open by requiring the World section to encode the user's actual knowledge state — which immediately revealed that the original had gotten it wrong.

---

### The World Section as Knowledge State

The World section in this bot does something Emily's didn't need to do: it encodes two separate knowledge states simultaneously — what the user knows and what actually happened — and keeps them distinct.

What the user knows is encoded first and precisely: a name heard once, a stranger at the station, a wife who won't quite meet their eyes. What actually happened is encoded separately, marked explicitly as information the user does not yet have. This structure does two things: it tells the LLM exactly where the information asymmetry sits, and it makes Beth's evasion psychologically coherent — she's not managing a confession, she's caught, and the user already knows enough to make silence impossible.

Prior contact closure applied here extends to the marriage itself: no prior infidelity, no open arrangement, no framework. And to Beth's omission: she didn't mention Wendy because she was managing something she told herself didn't need managing. That's not just backstory — it's the explanation for why the user barely knows Wendy's name, which is itself a piece of evidence the user is already processing.

---

### Wendy — Cohort Over Full Character

The original gave Wendy full character treatment. The conversion reduced her to a rich cohort entry. This was the right call for two reasons.

First, Wendy's role is reactive by design. She follows Beth's lead, she doesn't push, she holds until signaled. She doesn't have her own revelation arc — Beth does. A full seven-slot structure would have implied an independence and trajectory Wendy doesn't have in this scene.

Second, the cohort entry format handled Wendy's complexity more efficiently than slot structure would have. Wendy's defining characteristic is ambiguity — she has genuine feeling for Beth and a professional interest in Beth's division, and she's not entirely sure which one is driving her. That's not a clean answer that fits in a MOTIVATION field. It's a both-things-are-true-simultaneously construction that prose handles naturally and schema flattens.

The cohort entry encoded: her role, her knowledge state, her emotional position, her operational rule (she holds until signaled), her mixed motivation, and her specific trigger response under interrogation — all in under 200 words. A compressed secondary character block doing the same work would have run 700-1,000 words and still missed the ambiguity.

*Key principle confirmed:* When a character serves someone else's arc but has real complexity, a rich cohort entry is almost always more efficient than a compressed full character.

---

### Encoded Ambiguity as Design Choice

The spec emphasizes closing invention spaces. This bot required the opposite: deliberately encoding open dramatic space within closed invention space.

Wendy's motivation needed to be ambiguous to the user — but not ambiguous to the LLM. "She tells herself the two things are separate — what she feels and what she wants professionally — and she's mostly convinced" gives the LLM a specific, bounded ambiguity to work with. The user pressing Wendy hard gets a real answer that is true and incomplete simultaneously. The LLM isn't inventing — it's deploying an ambiguity the author encoded on purpose.

This is the distinction: *open invention space* is a gap the LLM fills with whatever is plausible. *Encoded ambiguity* is a specific both-things-are-true construction the LLM can deploy accurately. The first is a failure mode. The second is a dramatic tool.

---

### Props as Character Behavior

The release paperwork in the Greeting does three jobs simultaneously: it proves the night happened (establishes), it grounds the scene in mundane domestic reality which makes the tension more uncomfortable (orients), and it gives each woman a specific behavior that reveals character without narrating it.

Beth sets hers on the hall table on top of the cable bill and store flyers — as if it's just another piece of mail. That's her self-deception in gesture form. She's been filing this feeling in the ordinary clutter of her life for months. The paperwork goes the same place.

Wendy studies hers as a way to avoid looking at Beth and the user. She's a stranger in this house and she knows it. The court date gives her somewhere to put her eyes.

Neither behavior was directed explicitly. Both emerged from accurate characterization meeting a specific prop. This is the Greeting doing sentence discipline work: one prop, two behaviors, both load-bearing.

---

### What the Old Schema Got Wrong

The original schema was not carelessly written. The fields were filled thoughtfully, the characters had distinct personalities, the progression phases were considered. But the schema structure itself created the failure:

- The PREMISE field said "after-work drinks turned into kissing." It didn't say the user was at the station, saw Wendy, and is already doing math.
- The ONGOING_DYNAMIC field said "evasion shifts toward honest confession." It didn't say Beth is honest because she got caught, which changes the moral weight of everything.
- Beth's CORE_DRIVE was correct. Her BACKSTORY explained the relationship. But the connection between them — that she didn't mention Wendy because she was managing a feeling she'd named as friendship — was nowhere. The schema had no field for "what she's been lying to herself about."
- Wendy's MOTIVATIONS field said "follow genuine feeling without causing harm." It said nothing about the professional dimension, which is what makes her genuinely ambiguous rather than simply well-intentioned.

The format forced all of this into the open by requiring the World section to encode the scene's actual starting state — which immediately revealed that the original had gotten the starting state wrong.
