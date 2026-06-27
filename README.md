# Park Money: NPS DC Contract Tracker

**[park-money.vercel.app](https://park-money.vercel.app)**

A scrollytelling data investigation into National Park Service contract spending in Washington D.C. during FY2026, built from public federal contract records.

## What we found

The NPS awarded 140 contracts in Washington D.C. in FY2026 (Oct 1, 2025 – present), totaling $276M — a figure that includes both new awards and ongoing multi-year contracts. The new-award story has two main chapters:

**December 2025 — $59M in one week.** A single contractor, Terra Site Constructors LLC, received seven fountain rehabilitation contracts totaling $55.2M between December 5 and 11. All seven were classified as "full and open competition after exclusion of sources." Each received exactly one bid.

**April 2026 — No-bid emergency.** NPS awarded a $14.2M contract to Atlantic Industrial Coatings LLC to restore the Lincoln Reflecting Pool without competitive bidding, citing "unusual and compelling urgency" (FAR 6.302-2). A second urgency contract for the same pool ($1.7M, Green Water Solutions) followed ten days later.

Additional findings: several March contracts were 8(a) sole-source awards; Custom Lawn Service received ~$6.9M in contracts justified as "only one source"; at least five contracts explicitly cite Executive Order 14398 (beautification).

Meanwhile, internal NPS records obtained by [The Atlantic](https://www.theatlantic.com/politics/2026/06/national-parks-trump-white-house-renovations/687700/) document 900+ projects at parks nationwide that were expected to receive FY2026 funding and didn't.

## Data sources

| Source | What it provides |
|--------|-----------------|
| [USAspending.gov API](https://api.usaspending.gov) | Contract awards, amounts, descriptions, dates |
| [USAspending bulk archive](https://huggingface.co/datasets/abigailhaddad/usaspending-bulk-awards) | Competition status, justification codes, offer counts (queried via DuckDB) |
| [The Atlantic, June 2026](https://www.theatlantic.com/politics/2026/06/national-parks-trump-white-house-renovations/687700/) | 92%/68% spending shift, 900+ unfunded projects (from internal NPS budget documents) |

**Contract query parameters:** awarding sub-tier agency = "National Park Service"; award types A/B/C/D (definitive contracts); place of performance = Washington, D.C.; FY2026 (Oct 1, 2025 – Jun 2026). Retrieved June 2026.

**Important caveat:** The $276M figure and 140-contract count include ongoing multi-year contracts (e.g., a Lincoln Memorial rehabilitation started in 2022, a Siemens energy savings contract from 2014) that had activity in the FY2026 period. The timeline section focuses on contracts with start dates in FY2026.

## Running locally

No build step. Just serve the directory:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

Or use any static file server. The only external dependencies are Chart.js and Scrollama, both loaded from CDN.

## Stack

- Static HTML/CSS/JS — no framework, no build step
- [Chart.js 4.4.0](https://www.chartjs.org/) — bar chart
- [Scrollama 3.2.0](https://github.com/russellsamora/scrollama) — scroll-triggered chart updates
- [Vercel](https://vercel.com) — hosting

## Attribution

Contract data from [USAspending.gov](https://usaspending.gov) (public domain). Background reporting by Michael Scherer, [The Atlantic](https://www.theatlantic.com/politics/2026/06/national-parks-trump-white-house-renovations/687700/).
