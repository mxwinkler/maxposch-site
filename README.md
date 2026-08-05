# maxposch.com

Source for [maxposch.com](https://maxposch.com) — a [Quarto](https://quarto.org) website
deployed via GitHub Pages.

## Quick start

Edit a `.qmd` file, then:

```bash
quarto render
git add -A && git commit -m "..." && git push
```

The live site updates within a minute or two of the push. Nothing else is required —
no build server, no deploy step.

## How it fits together

| Piece | Where |
| --- | --- |
| Source | this repository |
| Rendered site | `docs/` (committed — GitHub Pages serves it directly) |
| Hosting | GitHub Pages, from `main` branch, `/docs` folder |
| Repository | <https://github.com/mxwinkler/maxposch-site> (public — required for Pages on a free account) |
| Domain | `maxposch.com`, registered at GoDaddy (expires 2031) |

The domain points at GitHub via four `A` records at GoDaddy
(`185.199.108.153`, `.109.153`, `.110.153`, `.111.153`) plus a `www` `CNAME` to
`mxwinkler.github.io`. The `CNAME` file in this repo tells GitHub which domain to
answer for; Quarto copies it into `docs/` on render because it is listed under
`project: resources:` in `_quarto.yml`. **Do not delete `CNAME`** — losing it breaks
the custom domain on the next deploy.

## Files

| File | Purpose |
| --- | --- |
| `_quarto.yml` | Site config: navigation, theme, output dir, page width |
| `index.qmd` | Home — bio, Recent, Upcoming talks |
| `research.qmd` | Publications, working papers, work in progress, press |
| `teaching.qmd` | Courses and office hours |
| `talks.qmd` | Past talks by year (upcoming ones live on the home page) |
| `custom.scss` | All styling on top of the `cosmo` theme |
| `files/` | PDFs: papers, slides, CV |
| `images/` | Headshot |
| `docs/` | Rendered output — generated, but committed because Pages serves it |

## Conventions

- **Upcoming talks go on the home page**, past talks on `talks.qmd`. When a talk passes,
  move it across; keep `talks.qmd` newest-first within each year.
- **Dates**: month + year (`Apr 2026`) for news; day-precise ranges
  (`17–18 Sep 2026`) for upcoming talks. Use en dashes in ranges.
- **News and talks rows** on the home page use the `.news` / `.news-date` /
  `.news-body` pattern — copy an existing row rather than writing a plain bullet,
  or the date column will not line up.
- **Seminars** are named by their actual series where known ("Political Economy
  Seminar, University of Oxford"), not just "Seminar".
- **Papers** on `research.qmd` follow: title → coauthors + venue → plain-language
  summary → links (PDF, journal, replication package, press).
- Talks and dates should be traceable to a real source (a programme, an invitation
  email). Do not add an entry that cannot be evidenced.

## Updating the CV or a paper

Replace the file in `files/` keeping the same filename, then `quarto render` and push.
Keeping the name stable means existing links elsewhere on the web keep working.

Watch PDF size: the JPE working paper was 68 MB until its appendix maps — pure vector
county polygons — were rasterised to 300 dpi PNGs in the LaTeX source. If a paper PDF
is tens of megabytes, the fix belongs in the figure pipeline (rasterise or simplify
geometry), not in PDF compression, which cannot shrink vector paths.

## Gotchas

- **GitHub sometimes commits to this repo itself** (`Create CNAME` / `Delete CNAME`)
  when the Pages custom domain is changed in its settings UI. If a push is rejected,
  `git pull --rebase` first.
- **Renders are not automatic.** Editing a `.qmd` and pushing without `quarto render`
  publishes nothing — Pages serves `docs/`, not the source.
- **The repo is public.** Never commit unpublished drafts, referee reports, data, or
  anything else not meant for the open web.

## Local preview

```bash
quarto preview
```

Or serve the built site exactly as Pages does:

```bash
python3 -m http.server 8741 -d docs
```
