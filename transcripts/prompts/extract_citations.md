# Prompt: Extract legal/tax citations from the RiceTVX / Stranger Than Fiction transcripts

You are scanning interview transcripts for citations to authoritative legal/tax
sources so they can be folded into the shared master register at
`~/Projects/citation-register/register.json` (schema: that repo's `SCHEMA.md`).

## Input

All `.txt` files in `transcripts/TXT/` (13 transcripts total):

1. `01_20260805_STF_ Collateralizing America _History Lesson_ - KL Session 1 Part 2_4b397566.txt`
2. `02_20260805_STF_ How The Legal Fiction Trickery Occurs - KL Session 2 Part 1_26119e47.txt`
3. `03_20260805_STF_ How The Legal Fiction Trickery Occurs - KL Session 2 Part 2_7c931bc4.txt`
4. `04_20260805_The Great Deception w Dr. KL Beneficiary _Lesson _1 2022__b63fd37b.txt`
5. `05_20260805_Great Birth Certificate Deception w Dr. KL Beneficiary _Lesson _2 2022__c2c65fe9.txt`
6. `06_20260805_Great Government Deception w Dr. KL Beneficiary _Lesson _3 2022__b4ee1f46.txt`
7. `07_20260805_How To Avoid Legal Pitfalls _ Traps w Dr KL Beneficiary _Lesson _4 2023__c7c17559.txt`
8. `08_20260805_The KEY To FREEDOM Is Education w Dr. KL Beneficiary _Lesson _4.5__c230ca00.txt`
9. `09_20260805_Freedom USB Package Educational Tool Information_e54c732f.txt`
10. `10_20260805_Oh You Were Finished_ Well Allow Me To Retort w KL aka Mr. Beneficiary _Lesson __57ff8eba.txt`
11. `11_20260806_Unlearning The LIES About American History w KL aka Mr. Beneficiary _Lesson _6__1185a92a.txt`
12. `12_20260806_All Roads Lead To Rome w KL aka Mr. Beneficiary _Lesson _7__65f827f4.txt`
13. `13_20260805_He Cracked Every Layer of Reality_ And Became a Target_5d4f338d.txt`

Attribute every citation to the transcript file and, where possible, the speaker
who said it (KL is the primary educator/guest; Chris Rice is the host). The
transcripts use timestamps (`[0.0s - 22.9s]`) without explicit speaker tags, so
speaker attribution must be inferred from context.

## What counts as a citation

- **SCOTUS / federal court cases** — by name ("Brushaber v. Union Pacific
  Railroad"), by reporter cite ("240 U.S. 1"), or both.
- **U.S. Code / IRC sections** — "26 U.S.C. § 61", "Section 3401", "26 USC 7701".
- **CFR sections** — "26 CFR 1.1-1".
- **Treasury Decisions** — "T.D. 8734", "Treasury Decision 2313".
- **IRS decisions/rulings, Revenue Rulings, IRS forms** — "Form 1040", "Rev. Rul.
  ...".
- **Constitutional references** — "16th Amendment", "Article I, Section 8, Clause
  1".
- **Acts of Congress, Executive Orders, secondary authorities** (dictionaries,
  IRM, Cumulative Bulletin, etc.) if named.

Capture a citation even if KL's spoken form is informal or approximate (e.g. "the
Brushaber case", "section thirty-four-oh-one") — normalize it to canonical form in
the record, but keep the as-spoken text as `matched_by` context.

## Do NOT invent URLs

Never fabricate or guess a source URL. For USC/CFR/Treasury Decisions, use the
resolver templates already defined in `citation-register/register.json`'s
`resolvers` block (read that file first). For a case, form, act, etc. with no
resolver formula, check whether it already exists in `register.json` — if so, reuse
its `url` and other fields; if not, leave `url` as `null` and flag it for manual
verification rather than guessing.

## Output — two files

### 1. Human-readable sidecar (for this project)

`transcripts/summaries/citations-sidecar.md` — one combined file across all 13
transcripts, grouped by category (cases, USC sections, CFR sections, Treasury
Decisions, constitution, IRS forms, acts/EOs, secondary authorities), each entry
showing:

- Citation (canonical form) + the as-spoken/as-written text if it differs.
- Transcript file name(s) it appears in, with a locating quote.
- URL if resolved, or `[UNRESOLVED — needs manual verification]` if not.
- Whether it already exists in the master register (`register.json`) or is new.

### 2. Pending file for the master register

`~/Projects/citation-register/pending/KL_on_RiceRadio_<YYYY-MM-DD>.json` — **only
new citations not already present in `register.json`**, in that repo's per-category
record shape (see `SCHEMA.md`), each with a `sources` entry:

```json
{"project": "KL_on_RiceRadio", "matched_by": "transcript-scan (extract_citations.md)",
 "files": ["04_20260805_The Great Deception ...", "07_20260805_How To Avoid Legal Pitfalls ..."]}
```

Do not edit `register.json` directly — per its own README/SCHEMA, additions go
through `pending/` for human review.

## Notes

- If a citation already exists in `register.json` but this project cites it too,
  still record that as a new `sources` entry to append (in the pending file) rather
  than skipping it — provenance across projects is the point of the `sources[]`
  array.
- If two transcripts give conflicting info about the same citation (e.g. different
  case name spellings), don't silently pick one — note the conflict in the sidecar
  so a human can resolve it, consistent with the register's `conflicts[]`
  convention.
- This pass is independent of the KL-ideas summary — see
  `prompts/summarize_KL_ideas.md` for that one.
