# Prompt: Summarize KL's ideas across the RiceTVX / Stranger Than Fiction transcripts

You are reading interview transcripts from RiceTVX's "Stranger Than Fiction" series. Each transcript uses timestamps in the form `[0.0s - 22.9s]` followed by spoken text. There are no explicit speaker tags; the speaker must be inferred from context (KL is the primary educator/guest, Chris is the host). Your job is to extract and summarize **only KL's legal ideas** — not Chris's questions/commentary (except where needed as minimal context for what KL is responding to).

## Input

All `.txt` files in `transcripts/TXT/` (14 transcripts total):

1. `00_20260804_STF_ Collateralizing America _History Lesson_ - KL Session 1 Part 1_e60951c3.txt`
2. `01_20260805_STF_ Collateralizing America _History Lesson_ - KL Session 1 Part 2_4b397566.txt`
3. `02_20260805_STF_ How The Legal Fiction Trickery Occurs - KL Session 2 Part 1_26119e47.txt`
4. `03_20260805_STF_ How The Legal Fiction Trickery Occurs - KL Session 2 Part 2_7c931bc4.txt`
5. `04_20260805_The Great Deception w Dr. KL Beneficiary _Lesson _1 2022__b63fd37b.txt`
6. `05_20260805_Great Birth Certificate Deception w Dr. KL Beneficiary _Lesson _2 2022__c2c65fe9.txt`
7. `06_20260805_Great Government Deception w Dr. KL Beneficiary _Lesson _3 2022__b4ee1f46.txt`
8. `07_20260805_How To Avoid Legal Pitfalls _ Traps w Dr KL Beneficiary _Lesson _4 2023__c7c17559.txt`
9. `08_20260805_The KEY To FREEDOM Is Education w Dr. KL Beneficiary _Lesson _4.5__c230ca00.txt`
10. `09_20260805_Freedom USB Package Educational Tool Information_e54c732f.txt`
11. `10_20260805_Oh You Were Finished_ Well Allow Me To Retort w KL aka Mr. Beneficiary _Lesson __57ff8eba.txt`
12. `11_20260806_Unlearning The LIES About American History w KL aka Mr. Beneficiary _Lesson _6__1185a92a.txt`
13. `12_20260806_All Roads Lead To Rome w KL aka Mr. Beneficiary _Lesson _7__65f827f4.txt`
14. `13_20260805_He Cracked Every Layer of Reality_ And Became a Target_5d4f338d.txt`

## What to produce

A structured summary of KL's legal claims, arguments, and positions — organized by topic, not chronologically, not per-episode. For each idea:

- **Claim** — one or two sentences stating what KL argues, in KL's terms (not softened or hedged unless KL hedges it).
- **Support** — how KL supports it (legal citation, procedural example, logical argument, etc.) — one line. Do not resolve or verify citations here (see below).
- **Source** — a Markdown link back to the transcript file the idea comes from, e.g. `[01](../TXT/01_20260805_STF_ Collateralizing America _History Lesson_ - KL Session 1 Part 2_4b397566.txt)`, immediately followed by a short locating quote (5-15 words, verbatim from the transcript) so a reader can Ctrl+F to the spot. If the same idea recurs across multiple episodes, give one link+quote per episode it appears in.

Group related ideas under topic headings inferred from what KL actually discusses (e.g. "Nature of federal income tax liability", "Affidavits of declination and notice procedure", "Strawman / artificial-person theory", "Birth certificates as collateral", "American history and the founding", "Roman law and ecclesiastical influences"). Do not force topics that aren't present.

## Contradictions and inconsistencies

Call these out **inline, at the point of discovery** — not only in a final appendix. When an idea contradicts or sits in tension with something KL said elsewhere (in an earlier or later episode, or earlier in the same one), add a `> **Contradiction:**` blockquote directly under the entry, stating the two positions and linking+quoting both sides the same way as above. Still include a short roll-up list of all flagged contradictions at the end of the document for quick scanning, but the primary flag belongs where the idea is presented.

## What to exclude

- Chris's own opinions or tangents.
- Small talk, banter, show-logistics, sponsor reads.
- Restating a claim KL repeats verbatim across episodes as a full new entry — note it once and list every episode it recurs in (each with its own link+quote), rather than duplicating the full write-up.

## Output

**One single monolithic Markdown file** — `transcripts/summaries/KL-ideas.md` — covering all 13 transcripts, organized by topic per "What to produce" above, with:

- A short intro noting the scope and source of the transcripts.
- The topic sections with claims, links/quotes, and inline contradiction flags.
- A final "Flagged contradictions" roll-up section.
- A final "Episodes by topic" cross-reference section.

## Notes

- Do not fact-check or editorialize on whether KL's legal claims are correct — this is a summary of what KL said, not a legal assessment.
- This pass is independent of citation extraction — do not attempt to resolve or verify legal citations here. Just capture what KL cites (case names, statute numbers, etc.) as plain text in the **Support** line; the follow-up pass (`prompts/extract_citations.md`) is what resolves/links/registers those.
