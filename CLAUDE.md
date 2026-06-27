# CLAUDE.md — Rock Mechanics & Rheology Quiz (PWA)

## What this repo is

A daily-quiz progressive web app for drilling rock-mechanics and rheology
knowledge, grounded in the canonical deformation literature. It's a single
self-contained page — the whole app lives in `index.html` (markup, styles, quiz
data, and logic in one file) — wrapped as an installable PWA so it runs on the
phone like a native app.

This is a teaching/self-study tool out of the Skemer lab (ESPM). Public repo:
`github.com/ehiatt/rheology_quiz`.

## Layout

- `index.html` — the entire app: question bank + UI + scoring logic, no build step.
- `sw.js` — service worker (offline caching so the quiz works without a connection).
- `manifest.json` — PWA manifest (name, icons, standalone display, theme color).
- `icons/` — app icons at every size iOS/Android asks for.
- `resources/` — local-only source material (the cited papers). Tracked as a
  folder; contents are gitignored — see below.
- `literature.md` — every work cited in the quiz, cross-checked against my master
  library. **Local-only (gitignored)** because it lists local library paths.

## Public repo — what must never be committed

This repo is public, so two things stay local:

- **`literature.md`** — lists absolute paths into my paper library.
- **`resources/` contents** — most cited works are paywalled; publishing the PDFs
  would be a copyright problem. The folder and its `README.md` are tracked; the
  `.gitignore` ignores everything else inside it. To ship one open asset (an
  open-license figure, a CSV of question data), un-ignore it case by case.

When adding questions, cite the literature in `index.html`, file the supporting
PDF under `resources/` locally, and log it in `literature.md` — don't lean on the
PDF being in the repo, because it won't be.

## The literature behind the questions

`literature.md` tracks 33 distinct cited works — 18 already in my library and
indexed, 15 still to grab via WashU `.edu` access (pre-OA classics, two textbooks,
and paywalled journal papers with no legitimate open-access copy). The library
itself lives at `C:\Users\Eric Hiatt\OneDrive\Desktop\Science\Papers`, indexed by
the `library` skill. When a new question cites something, check it against the
library first; if I own it, point `literature.md` at the file, otherwise add it to
the "grab via `.edu`" list.

## Current status

Live PWA on GitHub Pages: **https://ehiatt.github.io/rheology_quiz/** (URL changed
with the repo rename — the old `rheology-quiz` URL is dead; reinstall the phone PWA
from the new one). Registered in `proj` as `rheology_quiz`.

**Question bank = 70.** Set 1 (11) + Set 2 (11) authored, 3-model crosscheck-passed
(Claude+GPT+Gemini), and deployed; one dup-concept question pulled post-deploy.

**App features shipped 2026-06-27:** localStorage persistence (score, day-streak,
per-question seen/missed); modes Practice / Daily (deterministic 10/day + streak) /
Review (drill missed) / Random; tier **and** category filters; lifetime-accuracy
pill; SW cache versioning (v3). "Go deeper" is incognito-friendly — copies the
prompt + opens a BLANK claude.ai chat (claude.ai incognito is UI-only; no URL param),
so it works on the phone PWA.

Insertion pipeline: append to the `Q` array in `index.html`, validate via headless
node parse (Q.length, no dup ids, ans in range), bump the SW cache, commit + push.

Source base for question-writing is built out (all local; `resources/` is
gitignored, so none of it is in the public repo):
- **Papers:** all 35 quiz-cited works owned + indexed, plus 3 filed reviews
  (Bürgmann & Dresen 2008, Karato+ 2008, Skemer & Hansen 2016). `literature.md` is
  the per-quiz acquisition tracker; 6 still to get (see Next steps).
- **Concept KB:** 25 authoritative web sources scraped to `resources/web_sources/`
  (attributed markdown + `INDEX.md`) — DoITPoMS, MIT/ETH notes, SERC, USGS, IRIS.
- **Reading list:** `resources/canonical_candidates.md` — ~60 canonical works not
  yet owned, for future expansion.
- Master library now 376 PDFs / `eric.bib` 412 entries.

## Next steps (the learning-path roadmap)

1. **Foundations-first content** — author *basic, basic* definition questions
   (stress, strain, strain rate, deviatoric vs mean stress, elastic/viscous/plastic,
   brittle/ductile, viscosity, creep, flow law, dislocation, grain boundary,
   homologous T, stress exponent n, activation energy…), several varied questions
   per concept, building up toward the existing Tier-0 material. Crosscheck each set;
   diff topics/ids against the bank FIRST (a Set-2 dup had to be pulled).
2. **Adaptive "Learn" mode** (new mode beside the four) — walks the concept syllabus
   basics→advanced; **mastery gate = 5 correct in a row on a concept (any wrong answer
   resets that concept's streak to 0)**; subtly-varied questions, never the same one
   back-to-back; a miss resurfaces the concept.
3. **Weakness map** — aggregate misses by concept/category so Eric sees where he's thin.
4. **APS-specific question batch** — large, but only after the foundations ladder exists.
5. Acquire the 6 outstanding cited works (Stipp & Tullis 2003, Mainprice 2007,
   Gruntfest 1963, Evans & Goetze 1979 low-T, Karato 2008 & Schmid & Boas 1950 books).

## Session log

- **2026-06-27 (pm)** — App build-out. Authored + crosscheck-passed + deployed Set 1
  and Set 2 (bank 49→70; one dup pulled). Shipped persistence + 4 modes + tier/category
  filters + incognito "Go deeper". Locked the learning-path design (foundations-first,
  Learn mode with 5-in-a-row mastery, weakness map, APS later). Pages URL changed with
  the rename → reinstall phone PWA.
- **2026-06-27 (am)** — Big source-acquisition session. Renamed repo/folder to
  snake_case; filed 17 cited papers + 3 reviews (all stashed from Downloads,
  indexed, bib'd); ran a 6-lane canonical-literature research pass
  (`canonical_candidates.md`); scraped a 25-source web concept KB
  (`resources/web_sources/`). Standing rule added: stash (move) any paper filed
  from Downloads.
- **2026-06-26** — Scaffolded standard project machinery and registered in `proj`.
  Reconciled `literature.md` after the Downloads scrub.
