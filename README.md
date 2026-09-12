# House Ledger

A shared workspace for evaluating houses during a house hunt: log every address you see, enrich it with listing data, record positives/negatives and ratings per person, then compare finalists side by side.

## Live workspace

Published as a Claude Artifact (no install, no hosting to manage):
https://claude.ai/code/artifact/2d458058-09ed-47fd-b154-2781e8e02729

The page's shared data lives in the artifact's own database — there is no separate backend or deployment for this repo to run. `artifact/house-ledger.html` in this repo is the source of truth for the published page; edit it and republish to the same artifact URL to ship changes.

## How it works

- **Houses** — add an address, price, beds/baths/sqft, HOA, taxes, and links to the Zillow/Redfin/MLS listing. Filter by status (Interested / Touring / Offer Made / Passed).
- **Evaluations** — each person who opens the link picks a name once (stored locally in their browser) and records their own positives, negatives, a 1–10 rating, and notes per house.
- **Compare** — select 2–4 houses and see them side by side across every attribute, with the better value highlighted per row (Apple-style comparison).
- **Ranked** — houses sorted by combined average rating, or reordered manually.

## Enrichment workflow

Listing sites (Zillow/Redfin/MLS) actively block scraping, so auto-fetching happens from a Claude Code session rather than inside the page:

1. Tell Claude Code the address and listing link(s).
2. Claude fetches what it can and writes the house record directly into the artifact's shared database.
3. Anything it couldn't extract comes back as a short list to paste in manually.

## Access note

The artifact's shared database requires every reader/writer to be a signed-in member of the owner's Claude organization. If your co-buyer is on a separate personal account, confirm they can open and write to the link before relying on it — otherwise their evaluations won't sync to the shared view.
