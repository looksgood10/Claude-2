# CLAUDE.md

Guidance for Claude Code and any agents working on this Studienarbeit.

**Working language: German.** All document content — prose, headings, captions,
comments inserted into the `.docx` — is written in German. This file and commit
messages are in English.

---

## Project overview

| | |
| --- | --- |
| **Type** | Studienarbeit (*not* a Bachelor Thesis — the length rule differs) |
| **Title** | Der Einfluss digitaler Marketinginnovationen auf den Unternehmenserfolg: Eine kritische Analyse der wertorientierten Mediation am Beispiel von Jung und Shegai (2023) |
| **Author** | Michael Looks |
| **Institution** | Steinbeis Hochschule |
| **Programme** | Bachelor of Arts Business Administration, Jahrgang 2024 |
| **1. Betreuer** | Marcel Horn |
| **2. Betreuer** | <!-- TODO: still the template placeholder "z. B. Marcel Horn" --> |
| **Bearbeitungszeitraum** | <!-- TODO: from Anmeldung, 3 months for a Studienarbeit --> |
| **Length** | 20 pages ±10% (18–22) |

**Research question / aim:**

> <!-- TODO: state it in one sentence. The Einleitung is empty, so this has never
>      been written down. Everything in chapters 2–4 has to serve it. -->

**Central source under analysis:** Jung & Shegai (2023). The whole Studienarbeit
is a critical analysis of this one paper. **It is not in this repo** — add the PDF
to `lit/` before any work that touches chapter 3.

**AI policy:** <!-- TODO: check the Steinbeis rule and paste it here. -->
Note that the Selbständigkeitserklärung on page 2 declares that no sources or aids
were used beyond those named. Whatever the AI rule turns out to be, that
declaration is what you are signing.

---

## Formatting specification

From `data/Formatvorlage_Wissenschaftliche-Arbeiten_Bachelor_Master_final082024-2.docx`.
Non-negotiable — the template enforces it.

| Element | Value |
| --- | --- |
| Margins | left 4.0 cm, right 3.0 cm, top 3.0 cm, bottom 2.5 cm |
| Font | Arial 11 pt |
| Alignment | Blocksatz **with hyphenation enabled** |
| Line spacing | 1.5 |
| Header | left: (short) title · right: Vorname Nachname |
| Footer | right: page number |
| Printing | single-sided |

**Word styles — use these, do not hand-format:**
`Überschrift 1` / `Überschrift 2` / `Überschrift 3` · `Standard` ·
`Auflistung` (unnumbered) · `Aufzählung` (numbered) · `Quellenbezeichnung` ·
`Abbildungsbezeichnung` · `Tabellenbezeichnung` · `Literatur`

**Section breaks (Abschnittswechsel) must never be deleted** — they drive the
switch from roman to arabic page numbering and back.

### Required document order

1. Titelseite
2. Second page: Betreuer, Bearbeitungszeitraum, Selbständigkeitserklärung
   (Vertraulichkeitserklärung only if needed)
3. Vorwort *(optional)*
4. **Zusammenfassung — mandatory**, the Zeugnis cannot be issued without it
5. Gender-Klausel
6. Inhaltsverzeichnis (dynamic field, right-click → „Felder aktualisieren")
7. Abkürzungs- / Abbildungs- / Tabellen- / Symbolverzeichnis *(each only if needed)*
8. 1 Einleitung
9. Hauptteil, in three sections (Dreigliederungsprinzip)
10. Fazit
11. Literaturverzeichnis (alphabetical, uncategorised; Internetquellen in a
    separate list)
12. Anhang *(optional, roman numerals)*

### Rules the template states explicitly

- A new outline level needs **at least two** sub-points (no lone 2.1 under 2)
- A paragraph is **at least two sentences**
- Figures and tables: centred, framed, announced and explained in the running
  text so the point survives without seeing them; **source line above the
  caption**, both centred; must not be split by a page break; text must follow
  before the next section starts
- Abkürzungsverzeichnis lists only non-everyday abbreviations (not `ca.`, `bzw.`)
- **All red template guidance must be deleted from the final document**

### Citation style

In-text citation follows **APA** (per the template's own instruction), with the
detail in the Leitfaden Wissenschaftliches Arbeiten on the Lernplattform.

Be aware of a genuine conflict: the template *says* APA, but its
Literaturverzeichnis examples use a German house style
(`Keuper, F. (2001): Titel. 2. Auflage, München.`). The existing draft mixes both.
**Ask Marcel Horn which one governs** and record the answer here — then apply it
uniformly. Do not silently pick one.

---

## Repository layout

| Path | Purpose |
| --- | --- |
| `data/` | Original uploads. **Read-only — never modify.** |
| `chapters/` | The working copy that gets edited |
| `lit/` | One note per source, plus the Jung & Shegai PDF |
| `lit/references.md` | The **only** source of citations |
| `outlines/` | Approved outlines — agents draft against these |
| `defence/` | Per-section notes on what must be defensible |

**Round trip with Word:**

1. Edits are made to the working copy in `chapters/`
2. Every change is written **as a tracked change**, with a margin comment in
   German explaining why
3. You open it in Word, review each change, accept or reject
4. `data/` keeps the pristine original so any edit can be compared or undone

Use the `docx` skill for all `.docx` work — it handles tracked changes, comments,
and styles. Do not hand-parse the XML.

---

## Hard rules

### Never invent a citation

Cite only what is in `lit/references.md`, and a source goes in there only after it
has been **retrieved and read**. A search-result snippet is not a source.

If a claim needs support that does not exist yet, insert a Word comment:

```
[QUELLE FEHLT: <the specific claim needing support>]
```

Fabricated references look completely correct — real journal, plausible authors,
well-formed DOI — and are caught by the examiner rather than by you.

### Every number traces to the source paper

Chapter 3 reports coefficients, p-values, ACME/ADE and confidence intervals from
Jung & Shegai (2023). Each one must be checked against the paper itself and
carry a page number. **These have not been verified** — the PDF is not in the
repo. Do not restate, round, or reinterpret any statistic until it has been
confirmed against the original. If a figure cannot be located in the paper, flag
it; do not smooth it over.

No number enters the text from memory, inference, or plausibility.

### Rewrite the pasted passages — do not extend them

Two blocks in chapter 2 are pasted near-verbatim from a source and still carry
that source's numeric reference markers (`[20]`, `[28]`, `[42]`, …) — roughly 600
words across sections 2.1.3 and 2.1.4, including the literal marker
"NEU aus der PDF". This is the highest-risk material in the document.

These must be rewritten in Michael's own words with proper APA citations, or cut.
Do not build on them, do not merely reword them lightly, and do not simply
convert the bracket numbers into names.

### Never draft beyond the sources

Do not draft a section whose underlying literature is not in `lit/`. Drafting
first and locating support afterwards inverts the reasoning and produces claims
the evidence does not carry.

### Mark everything drafted

Every AI-drafted passage gets a Word comment tagged `AI-DRAFT`. The tag stays
until Michael has rewritten or explicitly signed off on the passage.

---

## Drafting

Order: **outline → approval → draft → Michael's rewrite.** Never jump to prose.

1. **Outline first**, into `outlines/`: per section, the claim, the evidence, and
   how it serves the research question. Wait for approval.
2. **Draft only against the approved outline.** If drafting shows the outline is
   wrong, stop and say so.
3. **Prefer argument skeletons** — claim, evidence, inference, link to the next
   section — over finished paragraphs. Full prose only when asked.
4. **Match the voice.** Chapters 2–4 are Michael's own writing; read them before
   drafting. German academic register, long subordinate constructions, hedged
   claims, `Homburg (2017)`-style integration of sources into the sentence.
5. **Write the defence note** into `defence/`: the claims made, assumptions
   behind them, and the obvious examiner objection.

---

## Critique

Be adversarial. Agreeable feedback is worthless — the Betreuer will not be
agreeable. Report in order of severity:

- Claims the cited evidence does not actually support
- Inferences that do not follow
- Sections that do not serve the research question
- Gaps: what chapter N assumes that chapter N−1 never established
- Unjustified methodological claims about the source study
- The strongest objection a Betreuer would raise, and whether the text answers it

State problems plainly. Do not open with praise.

---

## Literature notes

One file per source in `lit/`, named by citation key:

```markdown
# <key>

**Volle Quellenangabe:** <!-- Autor, Jahr, Titel, Journal, DOI/URL, Zugriffsdatum -->
**Vollständig gelesen:** ja / überflogen — <welche Abschnitte>

## Argument
## Methode & Evidenz
## Relevanz für diese Arbeit
<!-- which section, which specific claim -->
## Limitationen & Gegenpositionen
## Zitierfähige Passagen
<!-- exact quotes with page numbers -->
```

Never paraphrase a source read only as an abstract, and mark skimmed sources as
skimmed.

---

## Conventions

- **Language:** German
- **Citation:** APA in-text — pending the clarification noted above
- **Voice:** impersonal academic German; no first person
- **Terminology:** keep consistent — *digitale Marketinginnovation (DMI)*,
  *Marketing Capability*, *Unternehmenserfolg*, *Tobin's Q*, *Resource-based View
  (RBV)*. Introduce each abbreviation once, then use it.
- **Hedging:** state claims at the strength the evidence supports

### Do not

- Do not modify anything in `data/`
- Do not rewrite a passage without tracked changes
- Do not remove a `[QUELLE FEHLT]` or `AI-DRAFT` flag unless the underlying issue
  is actually resolved
- Do not add a source to `references.md` that has not been read
- Do not delete the Abschnittswechsel
- Do not leave template boilerplate in the document

---

## Git workflow

- Commit after each revision so drafts are recoverable
- Commit message: `kapitel N: <what changed>`
- `data/` is committed once and never modified
