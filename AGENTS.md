# maxposch.com — Agent Instructions

Personal academic website of Max Posch (Quarto → GitHub Pages).
Read `README.md` first for structure, conventions, and the deploy mechanics; this file
covers only what an agent needs beyond that.

**Canonical path:** `~/Library/CloudStorage/OneDrive-UniversityofExeter/maxposch-site`
(`~/OneDrive - University of Exeter/…` is a symlink to the same folder. Use the canonical
path when starting a session — it is what every other cloud-backed project here uses, and
it keeps project history and auto-memory in one bucket instead of two.)
**Remote:** <https://github.com/mxwinkler/maxposch-site> (public)
**Live:** <https://maxposch.com>

## Definition of done

A change is not done when the file is edited. It is done when:

1. `quarto render` has run (Pages serves `docs/`, not the `.qmd` sources), **and**
2. the change is committed and pushed, **and**
3. it has been verified **on the live site**, not only in a local preview —
   e.g. `curl -s https://maxposch.com/ | grep ...`. Pages takes a minute or two;
   poll rather than assume.

Report what was verified. If a step was skipped, say so.

## Boundaries

- **The repository is public.** Everything committed is world-readable, permanently, including
  history. Never commit unpublished drafts, referee reports, student or personal data, or
  credentials. The only PDFs that belong in `files/` are ones already meant for the open web.
- **Never touch DNS, the domain, or Pages settings** without Max asking. The custom domain took
  manual DNS work at GoDaddy; a stray change takes the site offline.
- **Do not delete `CNAME`.**
- Editing site content is pre-authorised after a clear request. Cancelling services, changing
  billing, or anything requiring Max's account credentials is not — hand those back to him.

## Evidence rule for content

Every talk, date, publication status, and press mention must trace to a real source — a
conference programme, an invitation email, a journal page. Never infer a date, a seminar
series name, or an acceptance from context. If it cannot be evidenced, leave it out and say
why. Prefer day-precise dates from programme PDFs over month-level guesses.

## Settled decisions (do not re-litigate)

- **No display serif.** A serif heading font was tried in Aug 2026 and reverted; headings stay
  on the system sans stack.
- **Public repo is deliberate** — GitHub Pages requires it on a free account, and the site
  content is public anyway.
- **`docs/` is committed on purpose.** It is generated output, but Pages serves it directly.
- **No news archive page.** The home page's "Recent" block is the only news surface; a separate
  news page was removed as redundant.

## Housekeeping

This directory lives in OneDrive. Git and a syncing folder are an uneasy pair: if `.git` ever
looks corrupted, the GitHub remote is the source of truth — re-clone rather than repair.
