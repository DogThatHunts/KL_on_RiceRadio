# Waypoint: KL_on_RiceRadio

## What was done (2026-11-12 session)

(Note: a few passages below refer to in-content dates like "2026-11-13" for
when a transcript was recorded/fixed per the docs' own text — all actual work
and commits happened in this single 2026-11-12 session.)

### Site published, citation anchors added

- Verified the project's `KL-ideas-RiceRadio.md` / `citations-sidecar.md` and
  their hand-maintained HTML renders (`summaries_html/kl-ideas.html`,
  `summaries_html/citations-sidecar.html`) were already live on GitHub Pages
  at <https://dogthathunts.github.io/KL_on_RiceRadio/>.
- Added per-case anchor ids (`<a id="slug">`) to every row of the Cases table
  in `citations-sidecar.md`/`.html`, and repointed all 28 case-citation links
  in `KL-ideas-RiceRadio.md`/`.html` from the generic `#cases` anchor to the
  specific row they reference.
- Added a "Source Videos & Transcripts" card to `index.html` linking each
  Odysee episode to its GitHub transcript file; flagged the file-12/Kushi
  mismatch (now resolved, see below) and the missing "Session 1 Part 1"
  transcript (also resolved, see below).
- Added a "KL's Core Worldview" summary card to `index.html` (9-topic
  overview + flagged-contradictions roll-up), styled consistently with the
  other cards.

### File 00/01 added — "Session 1 Part 1" transcript was missing entirely

- User supplied a Google Drive link for the previously-missing first half of
  the two-part opening interview. Downloaded, added to `transcripts/TXT/` as
  file `00` (later renumbered to `01`, see below).
- Folded its content into `KL-ideas-RiceRadio.md`/`.html` across ~15 source
  additions to existing topic entries, plus one new entry ("Dred Scott,
  standing, and the 'Lochner era'").
- Added two new citations to `citations-sidecar.md`/`.html`: *Slaughterhouse
  Cases* (new) and an append to the existing *Dred Scott v. Sandford*
  register record. Staged in
  `~/Projects/citation-register/pending/KL_on_RiceRadio_2026-11-12.json`
  (**not yet merged** into `register.json` — awaiting human review per that
  repo's convention).

### Full renumbering: 01–14, no file 00

- User asked for no `00` in the numbering. Shifted every transcript file's
  leading number up by one (`00→01, 01→02, … 13→14`) using `git mv`-style
  renames (git detected all 14 as renames, not delete+add).
- Updated **every** cross-reference across both summary docs (MD + HTML),
  both prompt files (`extract_citations.md`, `summarize_KL_ideas.md`),
  `README.md`, `index.html`, and the citation-register pending JSON's
  `files[]` arrays. This included careful handling of prose mentions like
  "episode NN" and "files NN and MM" (not just table cells/markdown links),
  and avoiding false positives (e.g. "12 U.S.C." is not a file reference).

### Episode 12 transcript was wrong — fixed

- File 12 ("Unlearning The LIES About American History," Lesson 6) had been
  paired with an unrelated third-party Michio Kushi video essay since the
  project's original transcript batch — a filename/metadata mismatch, not a
  genuine KL episode.
- User supplied a second Google Drive link with the correct transcript
  (confirmed real KL content: "lesson number 6," Rice Against the Grain
  intro). Replaced the file content (same filename/hash, since the filename
  itself was already correctly matched to the title — only the *content*
  was wrong).
- Folded its content into `KL-ideas-RiceRadio.md`/`.html` (13 source
  additions across existing entries — HOA/19-powers, Buck Act/airports, the
  Lieber Code read aloud from an exhibit, FDR's claimed 1917 authorship of
  the Trading with the Enemy Act, the 1976 National Emergencies Act's TWEA
  §5(b) carve-out, the Federal Reserve Act's 6%-interest claim, the
  Judge-Wardell/gold-fringed-flag anecdote, equity/Judicature Act detail,
  "The Great Taking," democracy-as-slavery, a cancer-recovery update, and a
  verbatim-repeat of the "no right to travel" contradiction) plus one new
  entry (Federal Reserve Act of 1913 section under Money and Banking).
- Added citations to `citations-sidecar.md`/`.html`: two new Acts of
  Congress (Federal Reserve Act of 1913, National Emergencies Act of 1976),
  one new secondary authority (*American Jural Society*, May 7 1996 — also
  **backfilled against file 07**, where it had been referenced in prose
  since an earlier pass but never actually logged as a sidecar citation),
  and several appends to existing records (Roe v. Wade, TWEA, Emergency
  Banking Relief Act, Buck Act, War Powers Act 1933, Judicature Act of 1875,
  Proclamation 2040). Added new context to the long-flagged "Proclamation
  24" item suggesting it may just be KL's own mislabeling of Proclamation
  2040 (not resolved outright — kept `[UNRESOLVED]`).
- Removed every "mismatched content" caution tied to file 12 across
  `index.html`, `KL-ideas-RiceRadio.md`/`.html`, and `citations-sidecar.md`/
  `.html`. **File 14 ("He Cracked Every Layer of Reality") is still the one
  genuinely mismatched transcript** — no fix has been supplied for it.
- Updated the pending citation-register JSON
  (`~/Projects/citation-register/pending/KL_on_RiceRadio_2026-11-12.json`,
  still **not merged**) with file 12's citations alongside file 01's.

### `index.html` table restyling

- Changed the Transcript column's link text from `"transcript (NN)"` to
  just `"NN."`.
- Added a new **Summary** column (same width as Transcript, same `"NN."`
  numbering) between Transcript and Episode (Odysee).
- User provided a Google Sheet
  (`https://docs.google.com/spreadsheets/d/1gws-Nmp5YFnMWK6oZgcEDkVL8SPMwhVWmBf_xZcaS9w`,
  "KL on RiceRadio" tab; the actual links live in the main "Queue" tab, column
  AA, rows 1258–1270) with 13 published-summary links (hosted at
  `https://dogthathunts.github.io/transcript-summaries/posts/...`, in order
  01–13). Wired all 13 into the Summary column. File 14 has no summary link
  (it isn't in the table at all — no Odysee source to pair it with).
- Removed the `<hr>` above the "Source Videos & Transcripts" card.
- Added an empty trailing row to the table, styled to match the header row's
  background fill (`--bg-warm`) and height via a new CSS rule
  (`.av-table-wrap tbody tr:last-child td`).
- Bumped the `style.css?v=` cache-busting query string each time the CSS
  changed (browsers had previously cached a stale stylesheet after a column
  was added, causing a visible column-overlap bug until hard-refreshed).

### Verification habits established this session

- Every HTML edit was checked for tag balance (`<tr>`/`</tr>`, `<td>`/
  `</td>`, `<li>`/`</li>`, etc. counts) via a small Python script before
  committing.
- Live rendering was spot-checked in a real browser (via `claude-in-chrome`,
  sometimes via a local `python3 -m http.server` for pre-push preview)
  after each visual change, including clicking through links to confirm
  they resolve.
- The citation-register pending JSON is kept **in sync** with
  `citations-sidecar.md` but is deliberately **not merged** into
  `register.json` — that's a separate human-reviewed step per that repo's
  own convention (see `KL_on_Crrow/transcripts/waypoint.md` for what that
  review-and-merge pass looks like when it's time to do it here).

### Small follow-ups (same session, after the above)

- Linked all 4 "Buck Act (1940)" mentions in `KL-ideas-RiceRadio.md`/`.html`
  (Claim/Support lines only, not verbatim quotes) to a new `#buck-act` anchor
  added to the Acts of Congress table in `citations-sidecar.md`/`.html`.
- User asked to rename "Adam Kokesh" to "Adam Koresh" in the ideas summary —
  **declined and left unchanged**: the source transcript (file 05) actually
  says "Adam Kokesh" (a real libertarian activist, AR-15/open-carry arrest
  anecdote); "Koresh" would misrepresent the transcript and likely confuses
  him with the unrelated David Koresh. User agreed to leave it as-is when
  asked.
- User asked whether GitHub links in `index.html` would work for third
  parties or only because they're logged in — confirmed via an
  unauthenticated `curl` (checked the embedded `"public":true` JSON, not
  just the HTTP status) that the repo is genuinely public; any visitor sees
  the same GitHub blob page.
- User then clarified they didn't want visitors able to browse the rest of
  the repo from a transcript link, just see that one file's content. Switched
  all 13 Transcript-column links in `index.html` from
  `github.com/.../blob/main/...` (full GitHub UI, browsable) to
  `raw.githubusercontent.com/.../main/...` (serves `content-type: text/plain`,
  renders inline with no GitHub chrome and no path into the rest of the
  repo). Verified via `curl` headers and a real browser screenshot.
- Removed the "Source repository" and "KL_on_Crrow" links from the
  `index.html` footer paragraph per user request; left the `dave_champion`
  link in place. Footer now just reads "Citations verified and merged
  against a private, shared citation register also used by dave_champion."

## Still open

- **File 14** ("He Cracked Every Layer of Reality") is still a
  filename/metadata mismatch (Michio Kushi content, not a real KL episode).
  No fix has been supplied and it has no Odysee link to pair a fix with even
  if one were found — lowest priority of the two mismatches since it was
  never in the Odysee table to begin with.
- **Citation-register merge not done**: `KL_on_RiceRadio`'s pending file
  (`~/Projects/citation-register/pending/KL_on_RiceRadio_2026-11-12.json`,
  covering files 01 and 12's citations) has not been through the
  verification-and-merge pass that `KL_on_Crrow` got (see that project's
  `waypoint.md`, "Citation review pass" / "Merged into citation-register"
  sections, for the shape of that work: verify each pending record against
  Justia/Cornell LII/etc., then merge via a one-off `tools/apply_*.py`
  script, then delete the pending file). The **original** 2026-08-15
  13-transcript pending file for this project was already merged before this
  session; only the two 2026-11-12/-13 follow-ups are outstanding.
- Several individually-flagged citations remain `[UNRESOLVED]` in
  `citations-sidecar.md` (unchanged this session, carried over from the
  original pass): *U.S. v. Slater* (ambiguous between two real 1982 cases),
  *U.S. v. Austin Gary Cooper* (year conflict, same open item as in
  `KL_on_Crrow`), "U.S. Supreme Court Rule 48.2" (not a real rule number),
  "U.S. Supreme Court case in 1907" (right-to-travel, no case name given —
  recurs in both files 11 and 12 verbatim), and "Proclamation 24" (new
  context this session from file 12 suggests it may be KL's own mislabeling
  of Proclamation 2040, but not confirmed).
- The Google Sheet's "KL on RiceRadio" tab (dedicated per-episode tab,
  columns Odysee/Description/Transcript/Summary) has its own **Transcript**
  and **Summary** columns still empty — the actual data lives in the master
  "Queue" tab instead. Not touched this session; flagging in case a future
  task wants to populate that tab directly rather than reading column AA of
  the master sheet each time.
