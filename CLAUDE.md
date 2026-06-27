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

App is built and live as a PWA on GitHub Pages (served from this repo). Standard
project machinery scaffolded 2026-06-26; registered in `proj` as `rheology_quiz`.

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

## Next steps

- **Set 1** (12 draft questions, `resources/_drafts/set1.js`) is pending a
  max-effort crosscheck before insertion into `index.html` — resume there.
- Build more question sets from the papers + `resources/web_sources/` KB.
- Acquire the 6 outstanding cited works (Stipp & Tullis 2003, Mainprice 2007,
  Gruntfest 1963, Evans & Goetze 1979 low-T plasticity, Karato 2008 & Schmid &
  Boas 1950 books) — list in `literature.md`.

## Session log

- **2026-06-27** — Big source-acquisition session. Renamed repo/folder to
  snake_case; filed 17 cited papers + 3 reviews (all stashed from Downloads,
  indexed, bib'd); ran a 6-lane canonical-literature research pass
  (`canonical_candidates.md`); scraped a 25-source web concept KB
  (`resources/web_sources/`). Standing rule added: stash (move) any paper filed
  from Downloads. Set 1 drafted, awaiting crosscheck.
- **2026-06-26** — Scaffolded standard project machinery and registered in `proj`.
  Reconciled `literature.md` after the Downloads scrub.
