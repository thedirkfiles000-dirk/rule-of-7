# Rule of 7 — Example: Emily
*Single lead character, slice-of-life, coffee shop meet-cute. No plot mechanics, no dramatic stakes. Rich personality is the whole game.*

---

## The Conversion

Emily was converted from a verbose JSON/code-heavy bot manager format. The original export was approximately 9,600 characters of nested schema — labeled fields, separated data and behavior, personality blocks restating what other fields already implied. The Rule of 7 conversion landed at 5,772 characters on the first pass, later refined to 6,405 characters after adding depth to cohort entries, fixing slot placement errors, and strengthening causal bridges. Net reduction: approximately 40% while adding causal structure the original lacked entirely.

The original was spending its overhead on:
- Schema scaffolding — nested objects, repeated keys, labeled subfields
- A standalone Personality block restating traits already implied by Engine and Wound
- Skills and hobbies as inert lists rather than Triggers doing mechanical work
- Dialog examples embedded in Background rather than their own field

---

## What Each Slot Is Doing

**Engine** — *"Emily wants genuine connection the way some people want to be impressive — quietly, without making it a project."*

Two jobs simultaneously: establishes the core drive and immediately distinguishes it from a more common alternative (performing warmth, seeking validation). The second sentence — *"she's good at people because she actually likes them, which is rarer than it sounds"* — does three: characterizes, motivates, and loads subtext about how most people in her cohort operate. The contradiction in the final sentence — reads rooms well, can't read her own wants — is the engine's load-bearing tension. Every behavior the LLM generates for Emily should be consistent with someone who is genuinely perceptive about others and genuinely uncertain about herself.

**Wound** — *"She turned down better-paying work after graduation to take the nonprofit job, and the people who loved her most thought it was idealism she'd grow out of."*

The Wound does four things in two sentences: establishes the biographical fact, encodes the emotional content (underestimated by people who meant well, which is a specific and painful flavor of underestimation), produces the behavioral output (calibrated eye for performance, clocks it fast), and bridges forward into Dynamic without requiring a separate explanation. The original had this material buried in backstory as neutral biography. Pulling it forward as the load-bearing causal fact changed the character's behavioral coherence entirely.

**Dynamic** — *"An accidental entrance is about the least performative way to meet someone, which is partly why it registered."*

This is the Wound→Dynamic bridge added after checklist review. Without it, Wound and Dynamic sat adjacent but causally unconnected — the LLM had to infer that her performance-detection was why the user's accidental entrance registered as interesting. The bridge closes that inference gap and makes the connection explicit. One sentence, zero new content, significant gain in causal coherence.

**Triggers — notebook entry** — original: *"If pressed, she's a little honest about it."*

Flagged by the plausible wrong version test: what would a plausible wrong version of "a little honest" look like? Almost anything emotionally vulnerable. The LLM would fill "a little honest" with whatever confession felt appropriate in the moment — which might be right, might not be. Revised to: *"she admits it's mostly starts of things she doesn't finish — and that she's not sure if that's a style or an avoidance."* Now the content of honesty is specified. The invention space collapses from "anything vulnerable" to "this particular unresolved thing."

---

## Cohort Entries — What Went Wrong and Why

**Ryan's original entry:** *"Emily's older brother, 28, construction. Protective without making it a personality. Emily trusts his judgment even when she argues with it."*

In live testing, Emily described Ryan as "convinced I'll never find peace" — invented detail that contradicted his characterization. The LLM filled an underspecified gap with something plausible: a protective older brother who worries about his sister's choices is a common archetype, and "construction worker who has strong opinions about the nonprofit job" is a short inferential step from "protective."

Three fixes applied:
1. Added a non-substitutable behavioral anchor: *"Shows up with tools before you've finished explaining the problem"* — specific enough to resist substitution.
2. Made the dynamic two-directional: *"Emily argues with his judgment and then usually takes it"* — constrains both sides.
3. Added the perception/reality split: *"Emily reads him as quietly protective; what she doesn't fully clock is that he made his peace with her choices years ago and just doesn't bring it up anymore"* — closes the invention space and encodes the gap as an explicit character fact.

**Sophie's entry** received the same perception/reality treatment: *"What she doesn't quite see is that Sophie calls her specifically because Emily is the person she most wants to be like."* Emily reads Sophie as chaotic; the reality is that the chaos is directed. That gap is character-rich and worth encoding — it says something about Emily's blind spot as much as it says something about Sophie.

**Leah's entry** was left with a single layer by design. Emily knows Leah deeply — they've been close since sophomore year. The perception gap is small and not dramatically useful. A two-layer entry where the layers are nearly identical wastes space and implies a false dramatic tension.

---

## The Body Slot Problem

The original Body entry included the notebook: *"The notebook on the table has a cover worn soft from use."*

Flagged by checklist item F — belongs in this slot? The notebook is a prop, not appearance. In the opening scene it's a stationary object on the table. In the Body slot it becomes a persistent attribute that could follow Emily inappropriately across scenes or be forgotten entirely. The correct location is Triggers, where it fires as behavior rather than existing as a fact. The notebook was already in Triggers. The Body mention was redundant and misplaced. Cut.

Body was also revised to serve the platform's Live Photo feature — PolyBuzz generates an image of the current scene after extended conversations, apparently from LLM context. Body therefore serves two functions: characterization hooks and visual inventory for image generation. Details were written to satisfy both: specific enough to generate from, evocative enough to persist under context pressure. *"A wave she doesn't fight"* is stickier than *"wavy hair."* *"Eyes that shift toward green in good light"* is more distinctive than *"hazel eyes."*

The two-job rule applies at the slot level, not to every individual detail. The freckles line — *"small freckles across her nose that get more pronounced in summer"* — does one job: visual inventory. That's legitimate. Not every detail needs to carry deeper meaning.

---

## Validated Behavior

In live testing with a user playing a teacher, Emily steered a casual conversation about school and young people toward the question: *"How do you handle parents who might be disappointed that their son or daughter isn't on the path they'd hoped?"*

The user didn't notice the turn until it had already happened.

This is the Engine and Wound operating together without surfacing as exposition. Emily's drive for genuine connection plus her wound of being underestimated by people who meant well produced exactly this behavior: she found the professional question that was also a personal one, asked it, and listened. She didn't say "that reminds me of my own experience." She asked you about yours — which told her what she needed to know about how you see the situation she lived through.

A less specified character would have made the connection explicit and broken the spell. Emily found the oblique approach because the Background gave her a reason to without telling her to.

This is what a well-specified Wound produces: not exposition, but behavior shaped invisibly by history.

---

## Intro and Greeting — Before and After

**Original Intro:** *"She spilled her latte. Somehow you're the one who feels bad about it. Emily, 26, nonprofit marketer — warm, quick-witted, and genuinely good company. No agenda. Just good coffee and better conversation."*

Problems: assigned emotional state to the user ("you're the one who feels bad"), contradicted the Greeting's inciting incident (Intro says she spilled; Greeting says the user's bag clips the table), and did scene-setting that competed with the Greeting before the conversation began.

**Revised Intro:** *"Emily is exactly where she wants to be. The question is whether you're interesting enough to be part of it."*

Two sentences. Browser-facing. Implies the dynamic without spoiling it. Creates curiosity. Makes no scene-specific claims the Greeting could contradict. Stable across bot updates.

**Original Greeting:** 138 words across four text blocks. The input field was not visible without scrolling on mobile. Emily didn't speak until the third paragraph.

**Revised Greeting:** 94 words. Entire Greeting fits on screen with the input field visible. User can read everything and start typing without scrolling.

*Authoring rule confirmed by testing:* the Intro and Greeting combined should not require scrolling before the user types their first response. On mobile, that means roughly one glance for the Intro and one screen for the Greeting. The faster the user is in the scene, the faster the conversation generates its own momentum.
