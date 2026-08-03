# CLAUDE.md

Guidance for Claude Code and any agents working on this thesis.

---

## Project overview

**Thesis title:** <!-- TODO -->
**Field / discipline:** <!-- TODO -->
**Level:** <!-- TODO: PhD / Master's / other -->
**Institution & programme:** <!-- TODO -->
**Supervisor:** <!-- TODO -->
**Submission deadline:** <!-- TODO -->
**Word limit:** <!-- TODO -->

**Thesis statement — the one claim everything must serve:**

> <!-- TODO: one or two sentences. If a section doesn't support this, it is cut
>      or the statement changes. Agents should treat this as the spine. -->

**Institutional AI policy:** <!-- TODO: link or paste the rule. Most programmes now
require disclosure of AI assistance, and the permitted scope varies widely — some
allow drafting, some only editing. Fill this in; it governs everything below. -->

---

## Working with Word / Google Docs

The master document lives in Word or Google Docs. This repo holds working copies
so that changes are reviewable and reversible.

**Round trip:**

1. Export the current chapter from Word/Docs to `chapters/` as `.docx`
2. Agent reads it, edits it, and writes changes back **as tracked changes plus
   margin comments** — never as a silent rewrite
3. You open it in Word, review each change, accept or reject
4. The accepted version goes back to the master document

Use the `docx` skill for all `.docx` reading and editing — it handles tracked
changes, comments, headings, and styles. Do not hand-parse the XML.

**Why tracked changes, always:** you see every alteration before it lands, the
edit history is visible to you and your supervisor, and nothing enters the thesis
that you haven't personally approved. A silently rewritten paragraph is one you
will not be able to defend in a viva.

---

## Repository layout

| Path | Purpose |
| --- | --- |
| `chapters/` | Working `.docx` copies, one per chapter |
| `outlines/` | Approved chapter outlines — the plan agents draft against |
| `lit/` | Literature notes, one markdown file per source |
| `lit/references.bib` | The **only** source of citations |
| `data/` | Raw data, read-only. Never modify. |
| `analysis/` | Scripts that turn `data/` into every number in the thesis |
| `analysis/outputs/` | Generated tables and figures. Never hand-edit. |
| `voice/` | Samples of your own unedited writing, for matching register |
| `defence/` | Per-chapter notes on what you must be able to defend |

---

## Commands

```bash
# Word count of a chapter
<!-- TODO: fill in once tooling is set up -->

# Re-run all analysis and regenerate tables/figures
<!-- TODO: e.g. python analysis/run_all.py -->

# Check every \cite key resolves against references.bib
<!-- TODO -->
```

**Before any chapter goes back to the master document:** every claim carries a
citation or a `[CITATION NEEDED]` flag, every number traces to a script in
`analysis/`, and every AI-drafted passage is marked.

---

## Hard rules

These are the ones that cause real damage when broken. They are not negotiable.

### Never invent a citation

Cite **only** what is already in `lit/references.bib`. If a claim needs support
that isn't there, write:

```
[CITATION NEEDED: <the specific claim requiring support>]
```

Do not produce a plausible-looking reference to fill the gap. Fabricated
citations look correct — real journal, right-sounding authors, well-formed DOI —
and are typically caught by an examiner rather than by you.

Before a source enters `references.bib`, it must have been **retrieved and
read**. A search-result snippet is not a source. Record the DOI or a stable URL
and the date accessed in the corresponding `lit/` note.

### Never invent data or results

No number appears in the thesis unless a script in `analysis/` produces it from
`data/`. This means:

- No estimated, illustrative, or placeholder figures in draft prose — not even
  temporarily, because placeholders survive into final drafts
- No describing a result pattern before the analysis has been run
- If an analysis hasn't been done, write `[ANALYSIS PENDING: <what's needed>]`

Agents cannot run experiments, collect data, or observe the world. "Do the
research" here means: literature search and synthesis, and analysis of data
**you** supply. Any apparent result that didn't come from `data/` is fabricated,
regardless of how reasonable it looks.

### Never draft beyond the sources

Do not draft a section whose underlying literature is not in `lit/`. Drafting
first and finding support afterwards inverts the reasoning and reliably produces
claims the evidence doesn't carry.

### Mark everything drafted

Every AI-drafted passage is tagged in the document as a comment: `AI-DRAFT`.
The tag stays until you have rewritten or explicitly signed off on the passage.
This is what makes disclosure possible and keeps you honest about which parts of
the argument are actually yours.

---

## Drafting chapters

The order is: **outline → your approval → draft → your rewrite.** Never skip
straight to prose.

1. **Outline first.** Produce a section-by-section outline in `outlines/` giving,
   for each section: the claim it makes, the evidence supporting it, and how it
   advances the thesis statement. Wait for approval before drafting.
2. **Draft against the approved outline only.** No new claims, no new sections.
   If drafting reveals the outline is wrong, stop and say so.
3. **Prefer skeletons to polished prose.** An argument skeleton — claim, evidence,
   inference, link to next section — is more useful than finished paragraphs,
   because it leaves the actual writing to you while doing the structural work
   that's genuinely hard. Produce full prose only when asked.
4. **Match the voice.** Read `voice/` before drafting. Match sentence length,
   hedging, and technical register. Prose that doesn't sound like you is visible
   to a supervisor who has read your work for three years.
5. **Write the defence note.** After each chapter, append to `defence/` the
   claims the chapter makes, the assumptions behind each, and the obvious
   objections. If you cannot defend a drafted passage from that note, it should
   not be in the thesis — flag it rather than leaving it in.

---

## Critique

When reviewing a chapter, be adversarial. Agreeable feedback is worthless here —
your examiner will not be agreeable.

Report, in order of severity:

- Claims that the cited evidence does not actually support
- Steps where the inference doesn't follow
- Gaps between chapters: things chapter N assumes that chapter N−1 never established
- Sections that don't advance the thesis statement
- Methodological choices that aren't justified in the text
- The strongest objection an examiner would raise, and whether the text answers it

State problems plainly. Do not open with praise, and do not soften a real
structural problem into a suggestion.

---

## Literature notes

One file per source in `lit/`, named by the bib key:

```markdown
# <bib key>

**Full reference:** <!-- author, year, title, venue, DOI/URL, date accessed -->
**Read in full:** yes / skimmed — <which sections>

## Argument
<!-- what the source claims and how it argues for it -->

## Method & evidence
<!-- what they actually did; sample, data, approach -->

## Relevance to this thesis
<!-- which chapter and which specific claim it supports -->

## Limitations & disagreements
<!-- weaknesses; who disagrees and on what grounds -->

## Quotable passages
<!-- exact quotes with page numbers, marked as direct quotes -->
```

Never paraphrase a source you have only read the abstract of, and mark skimmed
sources as skimmed — a chapter built on abstracts falls apart under questioning.

---

## Conventions

- **Citation style:** <!-- TODO: e.g. APA 7, Chicago, IEEE -->
- **Voice:** <!-- TODO: first person singular / plural / impersonal -->
- **Tense:** <!-- TODO: e.g. past for methods and results, present for established facts -->
- **Spelling:** <!-- TODO: UK / US -->
- **Terminology:** <!-- TODO: key terms that must be used consistently -->
- **Hedging:** claims are stated at the strength the evidence supports — neither
  overclaimed nor hedged into vacuity

### Do not

- Do not edit files in `data/` or `analysis/outputs/`
- Do not rewrite a passage without tracked changes
- Do not remove a `[CITATION NEEDED]`, `[ANALYSIS PENDING]`, or `AI-DRAFT` flag
  without the underlying issue actually being resolved
- Do not add a source to `references.bib` that hasn't been read

---

## Git workflow

- Commit after each chapter revision so drafts are recoverable
- Commit message: `chapter N: <what changed>`
- `data/` is committed once and never modified
- Do not commit anything under embargo or covered by an ethics agreement
