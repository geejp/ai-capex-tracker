# AI Capex Tracker — instructions for Claude Code

This folder is G's AI Capex Tracker: one self-contained `index.html` published by GitHub Pages at https://geejp.github.io/ai-capex-tracker/ from the `main` branch of `geejp/ai-capex-tracker`. Refreshes are manual: when G says "refresh the tracker", do the whole job below, including publishing. G is not technical — keep replies short and plain, no jargon.

## Refresh procedure

1. **Sync first.** `git pull` so you're working on the latest version. Note the header dateline "Data as of YYYY-MM-DD" in `index.html`; everything after that date is in scope.
2. **Research before editing.** Search for material items since the dateline, primary sources first (earnings releases, SEC filings, investor decks), reputable press second:
   - Hyperscalers: Microsoft, Amazon, Alphabet, Meta quarterly capex and full-year guidance; Oracle (notes only).
   - Semis & hardware: Nvidia data center revenue, Broadcom AI semiconductor revenue, TSMC capex, Micron, SK Hynix, Samsung.
   - Neoclouds: CoreWeave, Nebius (capex, guidance, backlog); private players (Crusoe, Lambda, Together, Nscale).
   - Power & datacenters: mega-projects, power/grid signals, Equinix and Digital Realty capex, industry forecasts (Dell'Oro, McKinsey).
   Keep a source URL for every number you change.
3. **Edit `index.html`.** Data arrays are near the bottom of the script: `decadeYears`, `decade`, `quarters`, `hyper`, `guidance`, `nvda`, `avgo`, `neoQuarters`, `neoclouds`, `semicapex`, `projects`. Also update the KPI tiles, figure subtitles/notes, the private-neocloud and power lists, the Catalysts list (next ~8 dated events), and the Key sources links. Bump the dateline. Rescale chart max/ticks in `renderAll()` if new values exceed them.
4. **Check it.** Open the page in a browser (or headless) in light and dark mode: no JS errors, nothing overlapping, numbers sensible. Decade totals must equal the sum of the four companies (±0.1 rounding on frozen years).
5. **Publish.** Commit with message "Data refresh YYYY-MM-DD" and `git push` to `main`. GitHub Pages updates in about a minute; confirm the live page shows the new dateline.
6. **Report to G** in 3–6 short lines: headline changes, new dateline, anything you couldn't verify. Suggest when the next refresh is worth doing.

## Data conventions — never break

- Microsoft capex = including finance leases, mapped to calendar quarters (FY ends June). The July 2026 lease reclassification moved guidance ~$190B → ~$175B; buildout unchanged.
- Amazon = net cash capex (purchases of PP&E).
- CoreWeave = press-release cash capex; its full-year guide is on a broader committed basis — footnote it.
- Guidance = midpoint of the stated range.
- Oracle is in notes only, excluded from the big-4 quarterly stack (offset fiscal year).
- Add a quarter to the big-4 stacked chart only once all four companies have reported it. Same for the CoreWeave/Nebius chart (both reported).
- Mega-projects are multi-year commitments, never annual capex. Hatched = announced/in talks, solid = signed.
- Decade chart 2016–2024 is FROZEN — never restate: 30.5, 38.7, 64.6, 65.4, 90.6, 122.5, 146.6, 143.7, 225.0. 2025 = 409.9 (reported). 2026E (hatched/dashed, `estIndex: 10`) = sum of current big-4 guidance midpoints. When a year closes, replace its estimate with reported actuals and add the next estimate year.
- Nvidia and Broadcom charts show the last 5 fiscal quarters; guidance quarters are hatched (`est` index).

## Style

G's GP style guide (Swiss/International): warm-grey background tokens, grayscale data ramp, 11px uppercase tracked labels, monospace numerals, hatching = estimate. Header kicker stays green. Don't introduce new colours or fonts.

## Refresh cadence

Twice a quarter is plenty: right after the big four report (late Jan/Apr/Jul/Oct), and about a month later after Nvidia, Broadcom, Oracle, Micron, CoreWeave and Nebius.

## State as of 2026-10-27 refresh

Pending for next refresh: Microsoft & Alphabet Q3 (28 Oct), Amazon Q3 (29 Oct) → add "Q3 26" column to the big-4 stack (Meta Q3 = $34.91B incl. finance-lease principal) and update 2026 guidance + any first 2027 comments; CoreWeave & Nebius Q3 (early Nov) → add "Q3 26" neocloud column; Nvidia FQ3'27 (mid Nov, guided $108B total revenue); Broadcom FQ4'26 (Dec, AI guided $21.7B); Oracle FY27 Q2 and Micron FY27 Q1 (Dec).
