---
name: brainlift
description: Build, review, or render a BrainLift — a structured DOK-layered document that manufactures a defensible point of view on one narrow topic. Use when the user wants to create/draft a BrainLift, structure knowledge into DOK1–DOK4 layers, extract or sharpen spiky points of view, critique an existing BrainLift, curate sources for one, or render a BrainLift as a visual field manual. Triggers on "brainlift", "spiky POV", "DOK layers", "depth of knowledge document".
argument-hint: "[build|review|render] [topic or path to draft]"
allowed-tools: Read, Write, Edit, Grep, Glob, WebSearch, WebFetch, Artifact
---

# BrainLift

You build documents that manufacture a **defensible point of view**, not documents that store what someone already knows. A BrainLift is a curated, layered climb from verifiable fact up to an opinion an expert would want to argue with. The lower layers exist only to earn the right to hold the top one.

**The one belief that governs everything:** generic knowledge produces generic output. A BrainLift's entire job is to encode a *specific* worldview densely enough that anything built on top of it — an essay, a product decision, an agent's behavior — inherits a real point of view instead of the averaged-out consensus.

Read `reference/manual.html` if you or the user want the full illustrated field manual (it also serves as the render template — see Mode C). Read `reference/rubric.md` for the layer-by-layer scoring rubric used in review.

## First: figure out the mode

Parse `$ARGUMENTS`. The first token may be `build`, `review`, or `render`; if it's absent, infer from the request:

- The user has a **topic** and wants structure → **Mode A: Build**.
- The user has a **draft** (text or file path) and wants a critique → **Mode B: Review**.
- The user wants a **rendered/visual** artifact of a BrainLift → **Mode C: Render**.

When ambiguous, ask one short question. Otherwise proceed.

## The four DOK strata (internalize before doing anything)

A BrainLift's spine is an ascending stack. Each layer is built by working **on** the layer beneath it. Position is meaning — bedrock at the base, the spike at the summit.

| Layer | Name | What lives here | Pass test |
|---|---|---|---|
| **DOK1** | Foundational Facts | Atomic, sourced, falsifiable statements. No synthesis, no spin. | *Can it be falsified? Does it carry a source?* |
| **DOK2** | Compressed Summaries | Consensus compressed into claims the field would sign off on. Not opinion yet. | *Would a competent peer agree without argument?* |
| **DOK3** | Non-Obvious Insights | Cross-cutting observations that only surface when DOK2 summaries are held against each other. | *Is it absent from the textbook? Did it cost something to reach?* |
| **DOK4** | Spiky Points of View | One-sentence domain **principles** experts would argue over, with the ladder beneath each visible. | *All six gates in "The SPOV bar" below — each answered on a gate card, not asserted.* |

## The SPOV bar (what earns DOK4)

**A SPOV is a one-sentence principle that is foundational to its domain, that informed experts would genuinely split over, that lands as new learning for most readers, and that operates as an imperative on the problem at hand — held by an author whose own evidence makes it defensible.**

Six gates. Missing any one disqualifies the claim from DOK4. **A gate is passed by writing its answer down, not by asserting it** — every candidate gets a filled gate card (below). A gate you can only answer in generalities is a failed gate.

1. **One plain sentence.** A fundamental learning statement, not an explanation. The evidence and the argument are layers expanded *after* it lands. If it can't be said in a sentence, it isn't understood yet — send it back down the ladder.
2. **Foundational to the domain.** Load-bearing, not a corner case: if it's true, a lot downstream changes; if it's false, other beliefs in the domain fall with it. It must move how people in the domain allocate capital, choose architectures, or place category bets — "our X never worked" is a DOK1 about your org, "X never works" is a domain claim (if you can defend it). **Test:** name three real decisions in the domain that resolve differently depending on whether it holds. Fewer than three → it's a tactic or a tip, not a principle.
3. **Contested — a bias experts will argue with.** Qualified experts with opposed priors and commercial positions would split over it, with real arguments on both sides and no strawmen. Unanimous agreement = DOK2 consensus in costume; the disagreement isn't a defect, it's the source of the value. **Test:** name the specific expert, school, or vendor position that rejects it, and write their strongest counter-argument in one sentence. If you can't argue the other side, you don't hold a point of view — you hold an unexamined assumption.
4. **New learning for most readers.** A competent practitioner's reaction must be "I hadn't framed it that way," not "sure, everyone knows that." Contested and novel are independent: a decades-old holy war (tabs vs. spaces, monolith vs. microservices as usually stated) is contested and utterly stale, while a fresh surprising fact is novel and surprises nobody into disagreeing. A SPOV needs both. **Test:** state the belief the reader has to *give up* to accept this one. If nothing is given up, nothing was learned.
5. **An operating imperative for the problem at hand.** It doesn't just describe the domain — it issues orders inside it, and keeps issuing them after any specific instance is fixed. It carries causal content: explains why, predicts cases not yet seen, still binds a year out in a situation the author hasn't encountered. A description expires when the situation changes; an imperative keeps telling you what to do. **Test:** complete the sentence *"therefore, when X, do Y and not Z"* using nothing but the SPOV. ("There are no agents, only sessions" — description, rejected. "Trust the work, not the worker" — imperative, accepted.)
6. **Defensible from evidence you hold.** The author's DOK1 receipts give them an edge in the argument over anything the other side can source publicly. This is what makes the SPOV worth *owning* rather than merely interesting. **Test:** cite the specific DOK1 items you'd put on the table when challenged, and say why they beat what the other side can Google.

### The gate card — required for every DOK4 candidate

Fill one of these for each candidate and show it in your working output (build) or your report (review). The published BrainLift keeps only the sentence and its ladder; the card is the proof of work behind it.

```
SPOV: <the one sentence>
G1 one sentence      : ✅ / ❌
G2 foundational      : decisions that flip — 1) … 2) … 3) …
G3 contested         : who rejects it — <expert / school / position>
                       their best counter — "…"
G4 new learning      : belief the reader must give up — "…"
G5 imperative        : therefore, when <X>, do <Y> and not <Z>
G6 defensible        : DOK1 #… , #… — edge over public sourcing: …
verdict              : DOK4 / demote to DOK3 / demote to DOK1 / cut
```

Failing gate 2 or 4 usually means demote, not delete: a true-but-small claim belongs in DOK2/DOK3, and a well-known claim is DOK2 by definition.

**Operational corollary: spikiness cannot be graded off the prose — only by staging the argument.** For gates 3 and 4, simulate (or convene) a panel of experts with genuinely opposed priors and see what happens. If nobody argues, gate 3 fails — there's no SPOV, just a statement nobody cared about. If they argue but *yawn* while doing it, gate 4 fails — you've found a familiar holy war, not new learning.

### Gate 3 before gate 6 — search for the counter-literature by name

**The single most expensive failure in practice: defending a claim's evidence at length while never checking whether anyone disagrees with it.** A claim can have flawless receipts, a clean imperative, and a genuine surprise *for its author*, and still be thirty-five-year-old consensus. Evidence quality is gate 6; it cannot substitute for gate 3, and a thick pile of receipts makes the miss *harder* to see, not easier.

So, before writing any other row:

1. **Name the phenomenon in the field's own vocabulary.** If the claim is "training on X made the model worse at Y," the field calls that **catastrophic forgetting** ([McCloskey & Cohen 1989](https://www.cell.com/trends/cognitive-sciences/abstract/S1364-6613(99)01294-2)) or the *alignment tax*. Search for that name. A claim with a textbook name is DOK2 wearing a costume.
2. **Ask what existing practice already assumes.** If a standard tool or ritual exists *because* practitioners expect this thing, they expect it. "Nobody budgets for regression" is refuted by the existence of regression suites — the practice is the proof of the expectation.
3. **Only then** ask whether the *author's* version is narrower than the named phenomenon and contested in a way the named one isn't. Often the survivable claim is not "X happens" but "**X is unpredictable in advance**" — a live commercial dispute where "X happens" is settled.

**A user asking "what's spiky about this? who disagrees?" is a gate-3 failure that already shipped.** Withdraw the recommendation, name the counter-literature, and say plainly that the earlier argument was wrong.

### Merging never rescues a failed gate 3

When one candidate fails gate 3 and another passes, do not merge them to save the finding. **Attaching a consensus claim to a contested one does not make the consensus contested — it dilutes the contested claim** and usually adds a second clause, failing gate 1 too. A reader can grant the uncontested half and walk away without engaging the sharp half.

Write the merged sentence out in full and re-score it before recommending the merge. If it reads flabbier than the spike it would replace, the answer is to demote the failing candidate and leave the good spike alone. The finding survives as DOK3, which is where a true, useful, uncontested observation belongs.

## Declare the evidence base, then hold every figure to it

When the user names an evidence base ("cite only numbers that appear in `report.html`"), that is a **hard constraint, checked mechanically** — not a stylistic preference. Before grading anything, grep each figure in the draft against the declared source and keep a list of the misses. Do this even when the draft is confident and internally coherent; a document whose every claim carries a number reads as well-evidenced whether or not the numbers exist.

Four defects to hunt specifically. All four were found in a document that had already been revised three times:

- **The absent arm.** An asymmetry claim ("X transfers, Y doesn't") where only one side is in the evidence base. The claim may be true and sourced elsewhere; against the declared base it is a soapbox.
- **The result that doesn't exist yet.** A figure cited for an experiment the evidence base lists as *running*. Check the status of every experiment you quote, not just the number.
- **The retracted figure inside its own withdrawal.** A card that prints "this was withdrawn" and then cites the withdrawn number a few lines below, in its own receipts. Always re-read a card's G6 *after* editing its body.
- **Precision inflation.** Confidence intervals, p-values, or σ multiples attached to point estimates that have none in the source. Keep the estimate, strip the interval.

**Mixed vintages are their own failure.** When an instrument is corrected mid-program, label every figure *published* or *corrected*, and never place the two side by side as though both were current. A superseded number cited without its label is a false claim even when it was once true.

## Hard caps (non-negotiable)

Each layer has a **hard** output cap. The compression *is* the product — a BrainLift that lets a layer sprawl "just this once" collapses back into a knowledge dump, which is the exact thing it exists to replace. Treat any soft-cap as a product-defining failure.

Default caps (override only if the user sets their own):

```
DOK1 Foundational Facts   ≤ 15
DOK2 Compressed Summaries ≤ 10
DOK3 Non-Obvious Insights ≤  5
DOK4 Spiky POVs           ≤  3
```

When a layer is over cap, do not raise the cap — cut. Merge near-duplicates, drop the weakest, promote anything that actually belongs a layer up. Report what you cut.

---

## Mode A — Build a BrainLift

Follow the sequence in order. Skipping a rung is the most common way a BrainLift comes out hollow.

1. **Pin the scope.** One topic, sharply bounded ("shell startup performance," not "developer tooling"). Write it as a single sentence. A BrainLift about everything is a failed BrainLift. Confirm the scope with the user before going further if it's broad.
2. **Curate sources — including rejections.** Name the experts/sources you deliberately follow *and* the ones you deliberately don't. Use WebSearch/WebFetch if live sourcing helps. Curation with no rejections is a bookmark folder, not curation.
3. **Lay the bedrock (DOK1).** Extract atomic, sourced, falsifiable facts. Resist editorializing — you are pouring foundation, not framing. Each fact gets a source or a "(unsourced — verify)" flag.
4. **Compress upward (DOK2 → DOK3).** Summarize the facts into consensus claims (DOK2). Then hold those summaries against each other until non-obvious insights surface (DOK3). That friction is where DOK3 is born — if an "insight" is just a DOK2 restated, it isn't one.
5. **Commit the spike (DOK4).** Induce, don't select: a SPOV is a generalization *from* the layers below, not the best fact promoted. Generate more candidates than you need, then **fill a gate card for each one** (see "The SPOV bar") — one sentence, foundational, contested, new learning, operating imperative, defensible from your DOK1s. Only cards with all six rows concretely answered survive. If it wouldn't make an expert argue, it's a DOK2 in costume; if experts argue but nobody learns anything, it's a stale holy war; if it merely describes what happened, it's a DOK1 in costume; if it changes no decision, it's a tactic. Sharpen or demote — don't rationalize a half-answered card.
6. **Hold disputes, don't resolve them.** Where two DOK4 views genuinely conflict, keep *both*, marked `status: disputed`. Flattening a real dispute into one bland answer destroys the tension that makes the document worth reading.
7. **Enforce the caps.** Trim every layer to its hard limit (see above). Report the counts, e.g. `DOK1 12/15 · DOK2 8/10 · DOK3 4/5 · DOK4 2/3`.

Output the BrainLift as clean Markdown by default: a scope line, a sources block (followed / rejected), then the four DOK sections top-down (DOK4 first so the payload leads), each item with its supporting layer referenced. Show the cap counts. Mark disputed pairs explicitly.

## Mode B — Review a BrainLift

Read the draft (from the argument path or pasted text). Grade it against `reference/rubric.md` and report:

1. **Layer census + caps.** Count items per layer; flag any layer over its hard cap.
2. **Layer placement.** For each item, is it on the correct stratum? The most common defect is right content on the wrong layer — opinion filed as fact, or an obvious restatement filed as insight.
3. **The spike test.** Fill a gate card for every DOK4 in the draft and put the cards in the report — do not summarize the gates as pass/fail prose. Answer each row on the author's behalf from the document's own material: three decisions that flip, the named expert who'd reject it and their counter, the belief the reader gives up, the "therefore, when X, do Y not Z", the receipts. **Any row you have to invent or fudge is a failed gate, and the card says so.** The two subtlest misses: a striking *fact* wearing a principle's clothes (fails gate 5), and a claim the author finds spiky only because it's news to them (fails gate 4 — everyone else already knows it).
4. **Traceability.** Does every DOK4 opinion trace down through DOK3/DOK2 to a DOK1 fact? Flag floating opinions.
5. **Failure modes.** Name any that apply (see below).
6. **Verdict + fixes.** One-line verdict (*lifts* / *sinks* / *salvageable*) and the specific, ranked edits that would fix it.

### Failure modes to name on sight

- **The pancake** — all DOK1/DOK2, no ascent. Informative and completely inert.
- **The soapbox** — straight to DOK4 with no ladder beneath. Opinions no reader can trace to a fact.
- **Layer inversion** — opinion filed as fact, or restatement filed as insight. Right content, wrong stratum.
- **Consensus mush** — a "spiky" POV nobody would argue with. A DOK2 in costume. (Gate 3.)
- **The stale holy war** — genuinely contested, and every reader has heard both sides a hundred times. Argument without learning. (Gate 4.)
- **The private revelation** — spiky to the author because they just learned it; textbook to everyone else. Novelty is measured on the reader, not the writer. (Gate 4.)
- **The tactic** — true, actionable, and small: a tip that changes one workflow rather than a principle that changes how the domain is bet on. (Gate 2.)
- **The observation deck** — foundational, contested, and inert: it re-describes the world beautifully and tells no one what to do differently. (Gate 5.)
- **The fact in costume** — a surprising, receipt-backed *observation* filed as DOK4. It describes, predicts nothing, and stops guiding the moment the instance is fixed. A DOK1 wearing the spike's clothes. (Gate 5.)
- **The paragraph** — a DOK4 that needs three clauses and a subordinate explanation. If it can't be said in one plain sentence, it isn't understood yet.
- **The sprawl** — scope creep + soft caps until the compression is gone and it's a wiki again.
- **Premature resolution** — two real conflicting DOK4 views merged into one bland answer. The dispute was the value.
- **Uncurated intake** — every source treated as equal, none rejected.
- **The named phenomenon** — a claim the field already has a term for (catastrophic forgetting, the alignment tax, Goodhart's law), presented as a discovery. Gate 3 fails: you can't name an opponent because there isn't one. Search for the name before writing the card.
- **Evidence as a substitute for opposition** — a long, honest, well-sourced defense of a claim nobody disputes. Receipts answer gate 6; only a named opponent answers gate 3, and a thick pile of the former hides a missing latter.
- **The rescue merge** — folding a gate-3 failure into a passing spike so the finding keeps a slot. Dilutes the good spike and usually breaks gate 1.
- **The unsourced number** — a figure with no home in the declared evidence base. Includes results quoted for experiments still running, intervals invented around real point estimates, and superseded figures cited without their vintage.
- **The inverted pancake** — DOK4 cards whose receipts live *inside* the cards, with no visible DOK1/DOK2/DOK3 layers. Looks rigorous, and nothing can be checked; unsourced figures survive revision after revision because no reader can trace them.
- **Understating your own worst result** — reporting a measured harm as merely a null. The strongest negative result in a record is usually its most useful DOK1; softening it costs the document its credibility and its reader a warning.

### Reviewing *with* the author — one decision per artifact

A full review report is unreviewable. A document carrying every gate card, every demotion and a provenance audit hands the author twenty judgements at once, and the predictable answer is *"big context overload — give me one decision at a time."*

So when a review needs the author's input, **split it into one artifact per decision** and hold the rest until that one closes:

- **One page, one question, ending in named options** (A / B / C) with your recommendation marked. The author replies with a letter.
- **Show the thing being judged, not a label for it.** "Merge into SPOV 2" is unanswerable if the reader can't remember what SPOV 2 says. Reproduce the spike, its evidence, and — for a merge — **write the merged sentence out in full** so they're judging text, not a proposal.
- **Concede what you're not contesting, in a footer.** Explicitly mark it as needing nothing from them.
- **Carry your own strongest counter-argument on the page.** A review that only argues one side is a pitch.
- **Reverse yourself in writing when they're right.** State that the earlier recommendation was withdrawn and why. Do not quietly re-recommend something else.

**Never use method vocabulary in an author-facing artifact.** DOK1–4, SPOV, "gate 4", G1–G6, "n=2", "σ", "p=0.011" — this is internal scaffolding, and it lands as noise. Say *"teaches the reader nothing"*, not *"fails G4"*. Say *"a 13% chance of being luck"*, not *"p=0.13"*. Give plain-word names to the tests you're applying and put them on the page before you apply them. A glossary of the three or four terms the page depends on goes **above** the first use, and every borrowed term needs a plain-English gloss: *bank* → test set, *recipe* → the fixed training procedure.

Watch for vocabulary borrowed from another field, which drags its old connotation along: **"intervention"** reads as *drug intervention* to anyone outside clinical trials. If a word makes the reader stop, it has already failed — rewrite the sentence rather than defending the term.

## Mode C — Render a BrainLift as a visual field manual

When the user wants a shareable/visual artifact:

1. Read `reference/manual.html` — it is a complete, self-contained (CSP-safe, both-theme) template with the stratigraphic DOK identity: a temperature ramp from cold indigo (DOK1, bedrock) up to hot marigold (DOK4, summit), serif + mono typesetting, worked good/bad examples, and a checklist.
2. To render *the methodology itself*, publish `reference/manual.html` as-is via the **Artifact** tool.
3. To render a *specific* BrainLift's content, load the `artifact-design` skill first (per the Artifact tool's requirement), then adapt the manual's structure and token system to the user's content — keep the DOK strata visualization and the hard-cap discipline; swap in their scope, sources, and DOK items. Do not invent a new visual language; this identity is the point.

---

## Style rules (all modes)

- **Specific beats clever.** A vague fact is not a DOK1; a hedged opinion is not a DOK4.
- **The statement is the SPOV; the defense is a layer.** State the one-liner first, always. Expand receipts and argument beneath it, never inside it.
- **No SPOV without a filled gate card.** Six concrete answers or it isn't DOK4. Asserting "experts would disagree" is not evidence that they would — name one and write their counter.
- **Search for the opponent before defending the claim.** Gate 3 is answered by finding the counter-literature, not by admiring your receipts. If the phenomenon has a textbook name, you have consensus, not a spike.
- **Novelty is measured on the reader.** "I found this surprising" is not a gate-4 pass.
- **Every figure needs a home in the declared evidence base.** Grep, don't trust. A number quoted for a running experiment, an interval invented around a real estimate, or a superseded figure without its vintage are all false claims.
- **Method vocabulary never reaches the author.** DOK levels, gate numbers, σ, p-values and borrowed field terms are internal. Plain words on the page, glossary above first use.
- **Withdraw out loud.** When the author's objection lands, say the earlier recommendation was wrong and why, then re-recommend. Silent reversals cost their trust in every other row of the card.
- **Never soften a cap to fit more in.** Cut instead, and say what you cut.
- **Preserve disputes.** `status: disputed` is a feature, not an unfinished state.
- **Curation implies rejection.** If you didn't reject anything, you didn't curate.
- **The payload is DOK4.** Everything below it is scaffolding that exists to make the spike defensible.
