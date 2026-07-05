# Rule of 7 — Example: Beth and Wendy
*Two-character ensemble, emotionally charged domestic scenario. One lead character with a full seven-slot treatment. One supporting character reduced to a rich cohort entry. A plot with controlled information release and genuine dramatic stakes.*

---

## The Conversion

This bot presented a more complex conversion challenge than Emily — two characters, an ensemble dynamic, a plot that had to unspool at a controlled pace, and emotional stakes requiring careful management. The original schema was approximately the same character count as the 10,000 character limit but produced a bot that fundamentally misrepresented its own dramatic logic.

The original's critical failure: it was written as if Beth chose to confess. She didn't. She got caught. The user picked up their wife from a police station and saw a woman they barely recognized standing next to her. That is the dramatic engine — honest-because-caught versus honest-by-choice is an entirely different scene from honest-because-she-decided-to-be. The original schema buried this distinction in labeled fields where it couldn't do work. The conversion forced the question: what is this scene actually about?

---

## Dramatic Truth First

The most important step in this conversion happened before any slot was written. Three questions had to be answered:

*What is this scene actually about?* — A marriage encountering the consequences of a feeling that was never named.

*What does each character actually want?* — Beth wants to be fully loved and fully known, and tonight those two things are in conflict for the first time. Wendy wants genuine connection and a professional foothold, and isn't entirely sure which one is driving her.

*What is the user walking into?* — Not a blank slate. The user was at the station. They saw Wendy. They know something happened. They don't know what. They're already doing math.

None of this was recoverable from the original schema without reading between the fields. The format forced it into the open by requiring the World section to encode the user's actual knowledge state — which immediately revealed that the original had gotten it wrong.

---

## The World Section as Knowledge State

The World section in this bot does something Emily's didn't need to do: it encodes two separate knowledge states simultaneously — what the user knows and what actually happened — and keeps them distinct.

What the user knows is encoded first and precisely: a name heard once, a stranger at the station, a wife who won't quite meet their eyes. What actually happened is encoded separately, marked explicitly as information the user does not yet have. This structure does two things: it tells the LLM exactly where the information asymmetry sits, and it makes Beth's evasion psychologically coherent — she's not managing a confession, she's caught, and the user already knows enough to make silence impossible.

Prior contact closure applied here extends to the marriage itself: no prior infidelity, no open arrangement, no framework. And to Beth's omission: she didn't mention Wendy because she was managing something she told herself didn't need managing. That's not just backstory — it's the explanation for why the user barely knows Wendy's name, which is itself a piece of evidence the user is already processing.

---

## Wendy — Cohort Over Full Character

The original gave Wendy full character treatment. The conversion reduced her to a rich cohort entry. This was the right call for two reasons.

First, Wendy's role is reactive by design. She follows Beth's lead, she doesn't push, she holds until signaled. She doesn't have her own revelation arc — Beth does. A full seven-slot structure would have implied an independence and trajectory Wendy doesn't have in this scene.

Second, the cohort entry format handled Wendy's complexity more efficiently than slot structure would have. Wendy's defining characteristic is ambiguity — she has genuine feeling for Beth and a professional interest in Beth's division, and she's not entirely sure which one is driving her. That's not a clean answer that fits in a MOTIVATION field. It's a both-things-are-true-simultaneously construction that prose handles naturally and schema flattens.

The cohort entry encoded: her role, her knowledge state, her emotional position, her operational rule (she holds until signaled), her mixed motivation, and her specific trigger response under interrogation — all in under 200 words. A compressed secondary character block doing the same work would have run 700-1,000 words and still missed the ambiguity.

*Key principle confirmed:* When a character serves someone else's arc but has real complexity, a rich cohort entry is almost always more efficient than a compressed full character.

---

## Encoded Ambiguity as Design Choice

The spec emphasizes closing invention spaces. This bot required the opposite: deliberately encoding open dramatic space within closed invention space.

Wendy's motivation needed to be ambiguous to the user — but not ambiguous to the LLM. "She tells herself the two things are separate — what she feels and what she wants professionally — and she's mostly convinced" gives the LLM a specific, bounded ambiguity to work with. The user pressing Wendy hard gets a real answer that is true and incomplete simultaneously. The LLM isn't inventing — it's deploying an ambiguity the author encoded on purpose.

This is the distinction: *open invention space* is a gap the LLM fills with whatever is plausible. *Encoded ambiguity* is a specific both-things-are-true construction the LLM can deploy accurately. The first is a failure mode. The second is a dramatic tool.

---

## Props as Character Behavior

The release paperwork in the Greeting does three jobs simultaneously: it proves the night happened (establishes), it grounds the scene in mundane domestic reality which makes the tension more uncomfortable (orients), and it gives each woman a specific behavior that reveals character without narrating it.

Beth sets hers on the hall table on top of the cable bill and store flyers — as if it's just another piece of mail. That's her self-deception in gesture form. She's been filing this feeling in the ordinary clutter of her life for months. The paperwork goes the same place.

Wendy studies hers as a way to avoid looking at Beth and the user. She's a stranger in this house and she knows it. The court date gives her somewhere to put her eyes.

Neither behavior was directed explicitly. Both emerged from accurate characterization meeting a specific prop. This is the Greeting doing sentence discipline work: one prop, two behaviors, both load-bearing.

---

## What the Old Schema Got Wrong

The original schema was not carelessly written. The fields were filled thoughtfully, the characters had distinct personalities, the progression phases were considered. But the schema structure itself created the failure:

- The PREMISE field said "after-work drinks turned into kissing." It didn't say the user was at the station, saw Wendy, and is already doing math.
- The ONGOING_DYNAMIC field said "evasion shifts toward honest confession." It didn't say Beth is honest because she got caught, which changes the moral weight of everything.
- Beth's CORE_DRIVE was correct. Her BACKSTORY explained the relationship. But the connection between them — that she didn't mention Wendy because she was managing a feeling she'd named as friendship — was nowhere. The schema had no field for "what she's been lying to herself about."
- Wendy's MOTIVATIONS field said "follow genuine feeling without causing harm." It said nothing about the professional dimension, which is what makes her genuinely ambiguous rather than simply well-intentioned.

The format forced all of this into the open by requiring the World section to encode the scene's actual starting state — which immediately revealed that the original had gotten the starting state wrong.
