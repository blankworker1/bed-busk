# Bed & Busk

*A barter platform for travelling artists.*

A peer-to-peer barter and gift-economy hospitality platform for traveling artists and buskers. Hosts are called **patrons**, guests are called **artists**. No cash gig marketplace, no live location tracking, no built-in payments in v1 — the platform stays deliberately at the barter/gift level.

## Status

Pre-MVP. Currently in the planning and pilot-design stage — no live site yet.

## Repo contents

| File | What it covers |
| --- | --- |
| [`PLATFORM_OVERVIEW.md`](./PLATFORM_OVERVIEW.md) | Core exchange model (Bed for Busk / Bed for Skill / Standard Stay), the Patron Profile / Listings split, Community Map, the Bed & Busk Guide, trust/safety and staged verification, MVP scope, website information architecture, and the two-stage build plan |
| [`GROWTH_STRATEGY.md`](./GROWTH_STRATEGY.md) | Six-phase growth plan: pilot-city seeding, festival-anchored acquisition, adjacent-community acquisition, patron pacing, the referral loop, SEO (blog + comparison pages), and SMO |
| [`patrons_template.csv`](./patrons_template.csv) | Pilot-city patron intake template — importable into Airtable as the Patrons table |
| [`artists_template.csv`](./artists_template.csv) | Pilot-city artist intake template — importable into Airtable as the Artists table |

## Wireframes

Four working, standalone pages under [`docs/`](./docs) — plain HTML/CSS, no build step, no framework. This is also the folder GitHub Pages serves: with **Settings → Pages → Source** set to branch `main`, folder `/docs`, the live site is at https://blankworker1.github.io/bed-busk/

| Page | Covers |
| --- | --- |
| `index.html` | Homepage — a live world map with one pin per active city (just Bosa so far) and a city-name search box with autocomplete (shows region + country per match). No Country/Region pages — this is the only geography layer. |
| `bosa.html` | City Hub for Bosa — hero, a live Leaflet/OpenStreetMap city map with pitch pins, Pitches, Patrons, Guide preview, Community notes |
| `patron.html` | Patron profile — Offer/Expectation Profile, reviews, "Request to stay" |
| `artist.html` | Artist profile — Offer/Expectation Profile, travel history, reviews, "Invite to stay" |
| `pitch.html` | Pitch detail — a live zoomed-in Leaflet map for that one pitch, acoustics/foot-traffic notes, reviews |

The city map (`index.html`) and the pitch map (`pitch.html`) are both real, working maps — Leaflet with OpenStreetMap tiles, loaded from a CDN, no API key needed. Coordinates are approximate placements around Bosa, not surveyed pitch locations. This is the same map stack recommended for the production build in `PLATFORM_OVERVIEW.md`, so nothing here gets thrown away later.

The original four screens are still live on a design canvas too, useful for click-through review without opening files: https://claude.ai/artifact/JRdiw5sbchCtanTQHVaQBr

## Build plan (summary)

**Stage A — Pilot site**: Airtable Forms collect patron/artist submissions → manual review → GitHub Actions pulls approved rows from Airtable's API → static site generator (Astro or 11ty) rebuilds the site → served on GitHub Pages. No custom backend.

**Stage B — Full MVP**: Cloudflare Pages/Workers (frontend + API), D1 (database), R2 (photos), Turnstile (signup bot protection). Built once live signup, matching requests, and reviews are actually needed. The Airtable CSVs import directly into D1 as seed data — nothing from Stage A is thrown away.

Full detail on both stages is in `PLATFORM_OVERVIEW.md`.

## Open decisions

- Confirm the pilot city (Bosa has been the working example throughout)
- Legal entity structure
- Formal data model / D1 schema for Stage B
- Actually stand up Stage A (Airtable base, GitHub repo scaffold, Actions workflow, site template)

## License

TBD.
