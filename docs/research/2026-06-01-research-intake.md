# Marketing Repo Research Intake — 2026-06-01

> A reflective summary of the 14 research files added to `docs/research/` on 2026-06-01 during the umbrella-wide audit. This file is meant as the first thing to read when deciding whether the new material is worth pulling for a given task. It describes what's there and where the value concentrates. It does not tell the project what to do.

⚠️ **This repo is PUBLIC.** Everything in `docs/research/` is on the open web. The files filed here are deliberately suitable for public visibility — they cite industry sources, contain no NDA material, and don't disclose Tideward secrets. Anyone clicking the GitHub link will see them.

---

## What was added, in one paragraph

`docs/research/` was a new folder as of 2026-06-01 — it didn't exist before. The umbrella audit created it and filed 14 files (~35,000 words, sourced) across five small commissioning waves. The repo's purpose is the public distribution point for lead magnet PDFs and (eventually) press kit assets; the research folder is the *reasoning* behind decisions about what to put in this public repo. The catalog is in `docs/research/INDEX.md`. The repo's `README.md` was updated with a one-line pointer to the research folder.

The intake's most useful framing: this is the cluster most concerned with *production decisions* rather than strategy. What asset to make, what format, what dimensions, what to host where. The reasoning is sourced and dated because press asset standards change.

---

## The five clusters and what's in each

### 1. The press kit foundation — what to actually ship

`press-kit-industry-standards.md`, `app-icon-design-2026.md`, `app-preview-video-production.md`, `video-press-kit-production.md`.

The press kit industry standards file is the cluster's most operational single document. The minimum viable press kit is 10 files anchored to Apple's 2026 sizes (iPhone 6.9" 1320×2868, iPad 13" 2064×2752, App Preview ≤500MB). The empirical anchor (Eurogamer's Martin Robinson: press uses "9-12 screenshots, a trailer, small b-roll, high-quality artwork") is the kind of journalist-side truth that calibrates production.

The app icon design file covers the Liquid Glass era for the six Apple platforms. Icon Composer (WWDC25, `.icon` bundle, SVG/PNG layer input), six 2026 variants (Default, Dark, Mono/Tinted, Clear Light, Clear Dark, visionOS layered), per-platform sizes, Tideward parchment+oxblood+gold direction across modes, R2 press-kit paths. The "no skeuomorphic glass overlays competing with system shader" note is the kind of anti-pattern easier to call out before production than after.

The App Store preview video file proposes 886x1920 H.264 portrait at 30 fps, ≤500 MB, 15-30 s, AAC 256 kbps. No voiceover, no device frame, real device capture only. DaVinci Resolve Free + $60 + a weekend for v1.0. Full storyboard included, A/B variant plan (PPO up to 3 videos), 15-item anti-pattern list, Phase 1 caption-only localization path.

The broader video press kit file (separate from the App Store preview) covers seven asset types (~30 deliverables): launch trailer 60-90s, 3-5 gameplay clips, 10 GIFs, B-roll, dev journal, per-creator thumbnails. Exact specs per type, B-roll labeling strategy, music licensing (Epidemic vs Artlist), burned-in caption rules (80% muted views are common on socials), 5-phase 60-80 hour workflow.

### 2. The asset hosting and distribution layer

`asset-cdn-strategy-versioning.md`, `promo-code-testflight-distribution.md`, `custom-product-page-variants.md`.

The asset CDN file is the answer to "where do the assets live as the press kit grows." Cloudflare R2 with custom domains (`assets.tideward.app`, `assets.manugames.com`) over GitHub raw (rate-limited since May 2025), B2 (storage savings irrelevant under R2's 10 GB free tier for the projected ~1.5 GB), and S3 (too expensive). Path versioning for press kits, content-hash filenames for one-offs, immutable cache headers throughout. The three-phase additive migration is needed because `raw.githubusercontent.com` can't be 301-redirected.

The promo code + TestFlight distribution file makes one important factual correction: **Apple's actual limit is 100 promo codes per app version per platform with 4-week expiration, not "100 per quarter."** IAP promo codes were retired March 26 2026 in favor of Offer Codes. Per-channel allocation + pre-launch distribution plan + 17-code reserve. TestFlight's 90-day build expiry is often the better press / creator rail than promo codes' 4-week trap.

The Custom Product Page variants file is the cluster's most attribution-focused document. 70-CPP cap (Oct 29, 2025), 170-char promo text, mid-2025 keyword assignment, iOS 18+ deep links, SoundCloud -39%/+58% case, +156% avg CPP lift, PPO/CPP non-interaction except sample siphon. Tideward CPP inventory: default + 5 Tier A creator + 3-5 segment + 3 ASA = ~15 at launch.

### 3. Founder bio + alt text + identity

`founder-bio-positioning.md`, `image-alt-text-writing-guide.md`, `trademark-portfolio-management.md`.

The founder bio file is the cluster's most subjective work product. Three drafted lengths (50 / 150 / 500 words), 10 case studies (Toby Fox, Pope, Wreden, LocalThunk, Malcolm, Colotto, Barone, Mullins, Cliffski, poncle), three SEO-to-game-dev pivot framings with the recommendation being to bury the SEO angle in 50/150 and surface only in 500. Three drafted 50-word variants for press use, plus 150 + 500.

The image alt text file is technical-accessibility-aligned. 5-category WCAG 1.1.1 split (decorative / functional / informative / complex / text-in-image), the "read it aloud" test, 9 Tideward-specific asset drafts. The 125-char myth correction (it's a screen-reader-by-screen-reader truncation, not a WCAG rule) is the kind of small precision that saves time.

The trademark portfolio file is the cluster's most calendar-anchored work. 2026 USPTO fees verified (Section 8 $325/class, combined 8+9 $650/class). Skip watch services pre-launch. Defer Madrid Protocol Year 2-3 ($3-5k filings; worth it at >$10k/yr international revenue). Hire TM attorney for any TTAB matter. Calendar anchored to Serial 99800434.

### 4. The community-fed surfaces

`wallpaper-distribution-case-studies.md`, `steam-screenshot-reference.md`, `soundtrack-ep-distribution.md`.

The wallpaper file is the cluster's most skeptical piece. Branded wallpapers are community-maintenance, not growth. Defer pre-launch; ship a small pack at Update 1 (~Apr 2027). 6 case studies (Hollow Knight, Stardew, Tunic, Disco Elysium, Hades, Frostpunk). Full Apple device dimension table + 10 named anti-patterns + iOS 26 Spatial Scenes guidance. Email-gating wallpapers is the explicit trap.

The Steam screenshot reference is hypothetical-only (Tideward is App Store only currently) but worth-having. Full 14-asset Steam inventory at 2026 dimensions, App Store comparison table, first-screen pattern, 45-75s trailer convention, capsule-localization rules. Tideward-specific hypothetical capsule design. T+12mo re-evaluation gate with 4 green-light criteria.

The soundtrack EP file lays out a tiered release plan. Tier 1: 5-7 track EP. Tier 2: full album. Tier 3 vinyl deferred. Bandcamp primary ($4.99 PWYW, 40% lower fees, schedule Bandcamp Fridays) + DistroKid syndication ($23/yr) for Spotify/Apple Music. Verify music IP rights with composer (Epidemic/Artlist subscription license can't redistribute). Release T+3 months (May 2027).

### 5. Press release distribution — the standalone verdict

`press-release-distribution-services.md` is a one-file cluster. Verdict: skip paid wires (PRWeb $99-$455, GlobeNewswire $600-$1,200, Business Wire $400-$2,750+, EIN $149) — they reach financial / SEO syndicates, not Tier-A gaming inboxes. Skip PR agencies ($6k-$18k floor). Recommended hybrid: direct personalized outreach to 10-15 named writers + self-hosted press kit at `tideward.app/press` + Bluesky/X/Reddit amplification, $0 cash.

---

## Where the contradictions and cross-currents live

- **App Store preview spec (this folder) ↔ Premium_Idle_App_Store_Positioning.md (Tideward app folder)**: aligned on substance, different in scope. The marketing-folder file is production-focused; the app-folder file is positioning-focused.
- **Press kit folder split (this repo) ↔ game-publisher-press-kit.md (manu-website folder)**: the two-tier model proposed in `manu-website/docs/research/game-publisher-press-kit.md` says studio press kit at `manugames.com/press`, game press kit at `tideward.app/press`. This intake file lives in the *asset distribution repo*, not in either press-kit destination. Be careful not to assume this repo IS the press kit — it's the asset substrate underneath.
- **Wallpaper file skepticism ↔ Apple's iOS 26 Spatial Scenes push**: the wallpaper file is appropriately skeptical but doesn't fully resolve whether Apple's Spatial Scenes changes the calculus. Worth a re-read when an iOS 26 wallpaper trend emerges.

---

## How the cluster is likely to be used

- The `INDEX.md` is the entry point.
- Most files here are tier-WARM and become hot during a specific production window (icon design + screenshot capture happen once pre-launch; trademark renewals happen on a calendar; soundtrack release is T+3 months post-launch).
- The most likely-to-be-accessed files in the next 6 months: `press-kit-industry-standards.md`, `app-icon-design-2026.md`, `app-preview-video-production.md`, `custom-product-page-variants.md`, `founder-bio-positioning.md`. These cover the production window for the Feb 11 2027 launch.
- The most likely-to-sit-unused-until-a-trigger files: `wallpaper-distribution-case-studies.md`, `steam-screenshot-reference.md`, `soundtrack-ep-distribution.md`.

Cross-references with sister projects:
- `press-kit-industry-standards.md` pairs with `manu-website/docs/research/game-publisher-press-kit.md` (split model).
- `app-icon-design-2026.md` pairs with `tideward-app/ManuResearch/` Liquid Glass design system references.
- `founder-bio-positioning.md` pairs with `manu-website/docs/research/founder-voice-strategy.md` (the strategy says when to lean in; the bio says how).
- `custom-product-page-variants.md` pairs with `the-assembly-line/RESEARCH/apple-search-ads-2026-premium-ios-benchmarks.md` (CPPs are the attribution rails for ASA).

---

## Memory-worthy candidates

- "Apple's promo code limit is 100 per app version per platform with 4-week expiration, NOT 100 per quarter. IAP promo codes were retired March 26 2026 in favor of Offer Codes."
- "Cloudflare R2's free tier covers the projected ~1.5 GB Tideward asset payload at $0/mo (R2's zero-egress to Cloudflare-proxied domains is the standout)."
- "Skip paid PR wires for indie game launches — they reach the wrong syndicates. Direct outreach to 10-15 named writers + self-hosted press kit is the $0 baseline."
- "Burn captions on all social-video assets — 80% of mobile-feed views are muted."
- "Music subscription licenses (Epidemic, Artlist) do NOT permit standalone redistribution. A Tideward soundtrack EP requires 100% original / commissioned-with-rights music."

None of these are written to memory yet.

---

## Public-repo specific considerations

Because this repo is public, the research files here are also public. A few things worth noting:

- None of the new files contain Tideward secrets, NDA-protected previews, or embargoed press material. They cite industry sources throughout.
- Future-Seth deciding what to add to this repo should keep the public-by-default discipline. If a research file might surface private contacts or compete-sensitive numbers, it belongs in another repo.
- The `INDEX.md` already includes a "What does NOT go here" section that documents this for future agents.

---

## Open questions the body of work doesn't close

- The actual Cloudflare R2 bucket setup (the file proposes; the doing is Seth's).
- Whether to commission custom music for the soundtrack EP or use Epidemic/Artlist for v1.0 with EP commissioning at T+3.
- The exact promo code allocation (the file proposes 17 reserved; the per-channel distribution is opinion-shaped).
- Whether to host the press kit on `tideward.app/press` (path) or `press.tideward.app` (subdomain). The game-publisher-press-kit file in manu-website recommends path; this repo doesn't argue otherwise but doesn't fully settle.

---

## What this intake doesn't try to do

It doesn't propose updates to the marketing repo's README. It doesn't sign up for a Cloudflare R2 bucket. It doesn't commission music. It doesn't open Linear tickets. The cluster is sized to be absorbed over the production window (T-9 to T+0 months) rather than all at once.

If a single file in the new material is going to surprise an experienced reader of the existing material, it's probably `promo-code-testflight-distribution.md` (the 100-per-version-not-quarter correction) followed by `asset-cdn-strategy-versioning.md` (the GitHub raw rate-limit since May 2025 closes a fallback path), followed by `press-release-distribution-services.md` (the verdict that paid wires aren't worth it is sharp).

---

*Filed by the umbrella-audit session, 2026-06-01. Companion files exist for all five sister subprojects. The umbrella `INDEX.md` and this folder's `INDEX.md` both reflect the cluster.*
