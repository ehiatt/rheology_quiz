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

App is built and deployed as a PWA. Standard project machinery scaffolded
2026-06-26 (`CLAUDE.md`, `.gitattributes`, `.claude/`, `resources/`); registered in
the `proj` index under keyword `rheology_quiz`.

## Next steps

- Acquire the 15 missing cited papers via WashU `.edu`, drop them in
  `resources/` (and the master library), and complete `literature.md`.
- Grow the question bank; keep each new question tied to a citation.
- Decide on a hosting target (GitHub Pages vs. elsewhere) for the public PWA.

## Session log

- **2026-06-26** — Scaffolded standard project machinery and registered in `proj`.
  Reconciled `literature.md` against the library after the Downloads scrub
  (Frost & Ashby 1982 and Bercovici & Ricard 2012 filed in; 33 works tracked,
  18 owned / 15 outstanding).
