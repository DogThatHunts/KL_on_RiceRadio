# KL_on_RiceRadio

Interview-transcript summaries for RiceTVX's "Stranger Than Fiction" series
featuring KL (same speaker as `KL_on_Crrow` — Crrow777 Radio — but a separate
show and a separate project).

## Layout

```
transcripts/
  TXT/          # 14 raw transcripts, timestamped, no explicit speaker tags
  prompts/      # the two independent analysis passes run over TXT/
    summarize_KL_ideas.md    # topic-organized summary of KL's legal claims
    extract_citations.md     # legal/tax citation extraction
  summaries/    # outputs of the passes above
    KL-ideas-RiceRadio.md    # KL's ideas by topic, with contradictions flagged
    citations-sidecar.md     # every citation found, with locating quotes
```

## Citations

This project's citations are extracted and merged into the shared, private
register at `~/Projects/citation-register/` (`register.json`), which is the
single source of truth across `dave_champion`, `KL_on_Crrow`, and
`KL_on_RiceRadio`. This project does not maintain its own copy of citation
data — `transcripts/summaries/citations-sidecar.md` is a human-readable
locating index (quotes + file references), not the data of record.

As of 2026-08-15, the citation-scan and merge are both complete — see that
repo's `CHANGELOG.md` ("KL_on_RiceRadio citation scan" and "KL_on_RiceRadio
merge" entries) for full detail: 63 distinct citations found, 10 new records
added to `register.json`, ~53 appended as new sources on existing records. A
handful of ambiguous/unidentified references (e.g. *United States v.
Slater*, *United States v. Austin Gary Cooper*, an unidentified
"Proclamation 24") were deliberately left unresolved rather than guessed —
tracked in that repo's `TBD_later.md`.

File **01** ("Session 1 Part 1") was added later (2026-11-12), after the
original 13-transcript scan/merge. Its two citations (one new — *Slaughterhouse
Cases* — and one append to the existing *Dred Scott v. Sandford* record) are
staged in a separate, not-yet-merged
`~/Projects/citation-register/pending/KL_on_RiceRadio_2026-11-12.json`.

## Ideas summary

`transcripts/summaries/KL-ideas-RiceRadio.md` is independent of the citation
pass — it summarizes KL's legal claims and arguments by topic, flags
contradictions inline, and does not attempt to verify or resolve any
citation KL mentions (that's the citation pass's job).
