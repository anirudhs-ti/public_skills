# public_skills

Claude Code skills I use day to day. Public so they can be copied, forked, or
argued with.

Each top-level directory is a self-contained skill: a `SKILL.md` (name and
description frontmatter, then instructions) plus any bundled reference assets.

## Skills

### `brainlift`

Build, review, or render a **BrainLift** — a document engineered to manufacture a
defensible point of view on one narrow topic, rather than to store what someone
already knows. Its governing belief: *generic knowledge produces generic output.*

It structures knowledge as an ascending stack — foundational facts, compressed
summaries, non-obvious insights, spiky points of view — where each layer exists
only to earn the right to hold the one above it, and enforces a **hard cap on every
layer**, because the compression is the product.

The payload is the top layer, and nothing reaches it without passing six tests
answered *in writing*, not asserted:

- **One plain sentence** — if it needs three clauses, it isn't understood yet.
- **Foundational** — name three real decisions in the field that resolve
  differently depending on whether it holds. Fewer than three is a tactic, not a
  principle.
- **Contested** — name the expert, school, or vendor who rejects it and write their
  strongest counter. Scored by *searching for the field's own name for the
  phenomenon*: a claim with a textbook name is consensus in costume, however good
  your evidence. Unanimity disqualifies.
- **New learning** — state the belief the reader must give up. Novelty is measured
  on the reader, never the author.
- **An operating imperative** — complete *"therefore, when X, do Y and not Z"*
  using nothing but the claim. A description expires; an imperative keeps issuing
  orders.
- **Defensible from your own receipts** — cite which facts you'd put on the table,
  and why they beat what the other side can look up.

Ships with an illustrated field manual and a review rubric. Also enforces a
provenance check — every figure must have a home in the declared evidence base,
verified by grep rather than by confidence.

### `share-doc`

Write and publish a decision document as self-contained HTML.

Its whole premise is that **a document asking someone to make a decision has a
different job than a document explaining a system.** The reader is deciding, not
studying, and every sentence that makes them go look something up is a defect in
the writing rather than in the reader. So the skill enforces:

- **A glossary first**, written for a human — name the actual thing, give the
  actual number, say what it is *for*.
- **Quote, never cite.** No "see the schema." Paste the schema.
- **One decision per document**, ending in named options answered with a letter.
  A comprehensive review doc is unreviewable.
- **Show the thing being judged, not a label for it.** If you're proposing
  replacement text, write the final text out.
- **Your own strongest counter-argument on the page.** A doc that argues one side
  is a pitch.
- **The reader's vocabulary, not yours** — "a 13% chance of being luck", not
  `p = 0.13`. Watch for words borrowed from other fields; they drag the old
  meaning along.
- **Verify every number by grep before writing it.** Prose whose every claim
  carries a figure reads as well-evidenced whether or not the figures exist.
- **Withdraw out loud** when you're wrong, rather than quietly re-recommending
  something adjacent.

Each of those rules is in there because a document failed without it. The
publishing section at the end is specific to my S3 bucket and AWS setup — swap it
for wherever you host, or delete it and keep the writing rules, which are the
transferable part.

## Using these

Drop a skill's folder into `~/.claude/skills/` (available everywhere) or a
project's `.claude/skills/` (that project only), then invoke it by name — Claude
Code will also pick it up automatically when a task matches its description.

```bash
git clone https://github.com/anirudhs-ti/public_skills.git
ln -s "$PWD/public_skills/brainlift" ~/.claude/skills/brainlift
ln -s "$PWD/public_skills/share-doc" ~/.claude/skills/share-doc
```

Symlinking rather than copying means `git pull` in the clone updates the skill.

## Provenance

`brainlift` began as a fork of [rahulsub/public_skills](https://github.com/rahulsub/public_skills)
and is maintained here independently; this repository shares no history with it.

## License

MIT — see [LICENSE](LICENSE).
