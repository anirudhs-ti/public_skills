---
name: share-doc
description: Write and publish a human-readable design doc, spec, proposal, review, or status report for Anirudh — as self-contained HTML on the public S3 bucket. Use whenever you are about to share a document, spec, proposal, plan review, or written analysis with the user, or when the user asks for "a doc", "the spec", "write this up", "share it as HTML", or asks for a document to be updated. Enforces the glossary-first, self-contained, decisions-at-the-end format that was arrived at by correction.
---

# Sharing a doc with Anirudh

Anirudh reads these docs to **make decisions**. He is not going to open a source
file to decode your prose. A doc that requires him to go read
`pack_inputs.json` to understand what you are asking is a broken doc — that is a
defect in the writing, not in the reader.

> **The rule this skill exists to enforce (Anirudh, 2026-08-05):**
> *"The document has to be richer in terms of not needing someone to go check a
> file out to understand what you're talking about. It needs to be
> self-contained because I am a human that's consuming this document in order to
> solve your open questions. I don't have the bandwidth to go and see every file
> and understand what it can't talk about and then answer."*

He described the glossary that fixed it as "a real game changer." Lead with one.

## Non-negotiables

### 1. Glossary first, and write it for a human

Every doc opens with a glossary **before** the content. Include any term that is
jargon, an acronym, a project-internal name, or a word with a specific technical
meaning that differs from its plain-English one.

**Agent-friendly (WRONG):**
> `provider` — the upstream inference vendor abstraction.

**Human-friendly (RIGHT):**
> **provider** — **Fireworks.ai**, the company whose GPUs train and serve our
> models. When this doc says "provider" it means Fireworks. There is no second
> provider today.

The test for each entry: *could someone who has never opened this repo act on
the doc after reading only the glossary and the body?* Name the actual thing.
Give the actual number. Say what it is **for**, not what category it belongs to.

Terms that have needed defining before, and will again: provider · write vs read
credential · deployment · artifact · attribution · instrument · σ / noise floor ·
MDE · paired test · pp · seal · content hash · idempotency key ·
pre-registration · eval bank · judge panel · bead · lane · cycle · treasury.

### 2. Quote, never cite

Never write "see `SFT-DIRECTIVE-002`" or "per the schema" or "as the registry
shows." **Paste the actual text, table, or number inline**, in a visually
distinct block, labelled with where it came from.

If you are asking him to change a line of config, show him that line verbatim
and show him the proposed replacement. If you are describing a data problem,
show the rows. If a schema field matters, print the field with its real values
annotated.

### 3. Decisions last, self-contained, with a recommendation

End with a numbered decisions section. Each decision must carry:

- the actual text/number/table being decided on, quoted inline
- the tradeoff in one or two sentences
- **your recommendation**, and what happens if he says nothing
- a note when a decision needs nothing from him unless he disagrees

Never ask a question whose answer requires him to go look something up. If you
need a fact to frame the question, go get the fact first and put it in the
question.

### 4. One decision per doc when the doc is asking for a decision

A comprehensive review document is unreviewable. Twenty judgements on one page gets
you *"big context overload — give me one decision at a time"* (Anirudh, 2026-08-11),
and he is right: he cannot hold the whole slate while evaluating any single item.

So when work needs several calls from him, **publish one doc per decision** and hold
the rest until that one closes:

- One page, one question, ending in **named options (A / B / C)** with your
  recommendation marked. He answers with a letter.
- **Show the thing being judged, never a label for it.** "Merge into SPOV 2" is
  unanswerable if he can't recall what SPOV 2 says — reproduce it, with its
  evidence. If you're proposing merged or rewritten text, **write the final text
  out in full** so he judges words rather than a proposal.
- **Put your own strongest counter-argument on the page.** A doc that argues one
  side is a pitch, and he will (correctly) go looking for what you left out.
- Concede what you are *not* contesting in a footer, explicitly marked as needing
  nothing from him.

### 5. His vocabulary, not yours

Internal shorthand lands as noise and stalls the decision. Every term you'd use
with another agent gets translated or defined before first use:

| Don't write | Write |
|---|---|
| `p = 0.13` | a 13% chance of being luck |
| `fails G4` / `gate 4` | teaches the reader nothing |
| `n=2` | only two habits tested |
| `bank` | test set — the ~359 items it's scored on |
| `recipe` | the fixed training procedure (same base model, hyperparameters, size) |
| `guard` | the specific mistakes we count alongside the headline score |
| `DOK3` / `SPOV` | supporting insight / the spike itself |

**Watch for words borrowed from another field** — they drag the old meaning in.
"Intervention" reads as *drug intervention* to anyone outside clinical trials
(2026-08-11). If a word makes him stop and ask, it has already failed: rewrite the
sentence, don't defend the term.

Name the tests or criteria you're applying **in plain words, on the page, before you
apply them.** A four-row panel explaining the criteria costs a paragraph and saves
the whole review.

### 6. Report corrections honestly

When he corrects an earlier version, say plainly in the doc what was wrong and
what changed. Do not quietly fix it. The footer is a good place: *"v1 required
the reader to open source files to decode it — that was a defect in the
document, not in the reader."*

### 7. Verify facts before writing them

Do not write a model slug, price, API shape, or file path from memory. Look it
up, then write it. A doc whose purpose is to support a decision must not carry
an invented detail.

**This extends to every number, and it is checked by grep, not by confidence.**
When a doc has a declared evidence base ("cite only what's in `report.html`"),
verify each figure against it before writing, and again before publishing. Prose
whose every claim carries a number reads as well-evidenced whether or not the
numbers exist — that is exactly why it must be checked mechanically.

Four specific defects, all found in a doc that had already been revised three
times (2026-08-11):

- a figure quoted for an experiment the source lists as **still running**
- a **retracted** figure still cited a few lines below its own withdrawal notice
- an **interval or p-value invented** around a point estimate that has neither
- **superseded and current figures side by side**, unlabelled, as if both were live

When you find misses, **list them and strike them from the argument** — say how
many and where they mattered. Do not silently drop them.

### 8. Withdraw out loud

When he pushes back and he is right, say plainly in the next doc that your earlier
recommendation was wrong and why, then give the new one. Reversing silently — or
re-recommending something adjacent without acknowledging the miss — costs him trust
in every other claim on the page.

## Format

Self-contained HTML, no external requests (CSP-safe anyway on S3):

- Complete document: `<!doctype html>`, `<head>`, `<meta charset="utf-8">`,
  viewport meta, `<title>`. **The charset matters** — without it, em dashes,
  arrows and σ become mojibake.
- `<meta name="robots" content="noindex">` — the bucket is world-readable.
- Inline `<style>` only. No CDN fonts, no external CSS or JS.
- Light **and** dark: `@media (prefers-color-scheme: dark)` plus
  `:root[data-theme="dark"]` / `[data-theme="light"]` overrides.
- Tables wrapped in an `overflow-x: auto` container. The page body must never
  scroll sideways.
- A table of contents when the doc is longer than a few sections.
- Numbered sections, so he can say "section 5" and you both know what he means.

## Publishing

> **Everything above this line is portable; everything below it is one specific
> setup.** If you are reusing this skill, replace this section with wherever you
> host — the writing rules are the transferable part. The habits worth keeping
> regardless: set an explicit content type, fetch the file back to prove it
> published, and give a new version a new URL.

The bucket is `s3://r0-assessment-share-anirudh-2026` (us-east-1, account
346945241475). It already carries a public-read policy — **do not modify bucket
config.** AutoResearch docs go under `autoresearch-v2/`.

```bash
# 1. AWS creds expire hourly. Refresh unattended — never ask him to log in.
bash ~/openclaw-home/.openclaw/scripts/aws-auth-refresh.sh

# 2. Upload. --content-type is REQUIRED or the browser downloads instead of renders.
aws s3 cp <file>.html \
  s3://r0-assessment-share-anirudh-2026/autoresearch-v2/<name>-YYYYMMDD.html \
  --content-type "text/html; charset=utf-8" --cache-control "public, max-age=300"

# 3. ALWAYS verify by fetching it back. An upload that returned 0 is not proof.
curl -s -o /dev/null -w "status=%{http_code} type=%{content_type} bytes=%{size_download}\n" \
  "https://r0-assessment-share-anirudh-2026.s3.amazonaws.com/autoresearch-v2/<name>-YYYYMMDD.html"
```

Expect `status=200 type=text/html; charset=utf-8`. If the token expired
mid-upload, refresh and re-upload — a 403 on verify with a "successful" upload
means the PutObject actually failed.

Then give him **the URL as a plain link**, plus a short summary in chat of what
changed and which decisions need him. Keep the chat summary short; the doc is
the artifact.

## Versioning

Date-suffix filenames (`-20260806`). A new version gets a new URL rather than
overwriting, so a link he already has keeps working and shows what he read. Say
in the doc which version it is and what changed from the previous one.

## Do not

- **Do not use Google Docs.** He asked for HTML explicitly and asked twice.
- Do not put the doc in the repo unless he asks — use the scratchpad, then S3.
- Do not publish anything he framed as sensitive without asking; the bucket is
  world-readable to anyone with the URL.
- Do not bury a question he must answer in the middle of a section.
