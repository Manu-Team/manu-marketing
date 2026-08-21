# Marketing Repo — Research Library

> Deep-research files supporting decisions about what to put in this **public** GitHub repo (`Manu-Team/manu-marketing`).
>
> **Filed:** 2026-06-01, 16 files (15 research files + the intake summary). Index reconciled 2026-08-21.
>
> ⚠️ **This repo is PUBLIC.** Anything in `docs/research/` is on the open web. Don't put NDA material, private contacts, embargoed pre-announcements, or anything that would burn Seth if a competitor read it. These files are deliberately suitable for public visibility — they cite industry sources and contain no Tideward secrets.

---

## Why this folder exists

The marketing repo is the **public distribution point** for lead magnets (Factory Game Starter Guide, etc.) and — eventually — for press kit assets. The research here drives decisions about *what* press assets to produce, *how* to spec them, and *how* to position Seth as a founder when press comes calling.

---

## Files

**Read this first:** [`2026-06-01-research-intake.md`](2026-06-01-research-intake.md) — a reflective
summary of the whole batch, grouped into five clusters, written to help you decide whether any of this
material is worth pulling for the task in front of you. Start there, then come back to the tables below
for the specific file.

### Wave 1 (2026-06-01)

| File | Tier | What it answers |
|---|---|---|
| [`press-kit-industry-standards.md`](press-kit-industry-standards.md) | WARM | 2026 industry baseline for what gaming press actually expects: file list, dimensions, formats, asset specifications. The minimum-viable press kit is 10 files anchored to Apple's 2026 sizes (iPhone 6.9" 1320×2868, iPad 13" 2064×2752, App Preview ≤500MB). Recommends Cloudflare R2 hosting for the heavy asset payload (zero egress beats GitHub raw under launch spike). |
| [`wallpaper-distribution-case-studies.md`](wallpaper-distribution-case-studies.md) | COOL | Skeptical assessment of branded wallpapers as growth: **defer pre-launch**, ship a small pack at Update 1 (~Apr 2027). 6 case studies (Hollow Knight, Stardew, Tunic, Disco Elysium, Hades, Frostpunk). Full Apple device dimension table + 10 named anti-patterns + iOS 26 Spatial Scenes guidance. Email-gating wallpapers is the explicit trap. |
| [`founder-bio-positioning.md`](founder-bio-positioning.md) | WARM | How a solo indie founder should write a press bio in 50/150/500-word lengths. 10 case studies (Toby Fox, Pope, Wreden, LocalThunk, Malcolm, Colotto, Barone, Mullins, Cliffski, poncle), voice spectrum, hooks that work / backfire, three SEO-to-game-dev pivot framings (recommendation: bury SEO in 50/150, surface only in 500), three drafted 50-word variants + 150 + 500 ready for press use. |

### Wave 2 (2026-06-01) — icon + video + awards

| File | Tier | What it answers |
|---|---|---|
| [`app-icon-design-2026.md`](app-icon-design-2026.md) | WARM | Liquid Glass era app icon design across iOS 26 / iPadOS / macOS / tvOS / visionOS / watchOS. Icon Composer (WWDC25, `.icon` bundle, SVG/PNG layer input), six 2026 variants (Default, Dark, Mono/Tinted, Clear Light, Clear Dark, visionOS layered), per-platform sizes, Tideward parchment+oxblood+gold direction across modes, R2 press-kit paths, no skeuomorphic glass overlays competing with system shader. |
| [`app-preview-video-production.md`](app-preview-video-production.md) | WARM | App Store preview video specs + production playbook. 886x1920 H.264 portrait at 30 fps, ≤500 MB, 15-30 s, AAC 256 kbps. **No voiceover, no device frame, real device capture only.** DaVinci Resolve Free, $60 + a weekend for v1.0. Full storyboard, A/B variant plan (PPO up to 3 videos), 15-item anti-pattern list, Phase 1 caption-only localization path. |
| [`awards-eligibility-2026-2027.md`](awards-eligibility-2026-2027.md) | WARM | Indie game awards calendar for Tideward. **Apple App Store Awards + Apple Design Awards = highest-value, both editor-curated** (no submission; lever is Featuring Nominations, submit Nov 2026). IGF 2027 is the one paid submission worth making ($75, deadline ~early Oct 2026). BAFTA 2027 + Develop:Star 2027 blocked by UK eligibility windows that already passed; 2028 cycles realistic. Skip A MAZE, IndieCade, Mobile Games Awards Cologne, D.I.C.E. |

### Wave 3 (2026-06-01) — alt text + Steam reference + promo codes

| File | Tier | What it answers |
|---|---|---|
| [`image-alt-text-writing-guide.md`](image-alt-text-writing-guide.md) | WARM | 5-category WCAG 1.1.1 split (decorative / functional / informative / complex / text-in-image), "read it aloud" test, 9 Tideward-specific asset drafts (App Store screenshots, OG cards, key art, headshot, divider motif, newsletter GIF), 125-char myth correction, OG-meta vs platform-upload alt distinction, anti-patterns, tone-per-surface, 5-step upload workflow. |
| [`steam-screenshot-reference.md`](steam-screenshot-reference.md) | COOL | Full 14-asset Steam inventory at 2026 dimensions, App Store comparison table, first-screen pattern, 45-75s trailer convention, capsule-localization rules (capsules per-language, screenshots/trailer global), Tideward-specific hypothetical capsule design, reuse audit (logotype + copy + trailer footage cross; visuals get remade), T+12mo re-evaluation gate with 4 green-light criteria. |
| [`promo-code-testflight-distribution.md`](promo-code-testflight-distribution.md) | WARM | **Key clarification: Apple's actual limit is 100 codes per app version per platform with 4-week expiration, not "100 per quarter."** IAP promo codes retired March 26 2026 in favor of Offer Codes. CPPs don't carry promo-code attribution automatically. TestFlight (90-day build expiry) is often the better press/creator rail than promo codes (4-week trap). Per-channel allocation + pre-launch distribution plan + 17-code reserve. |

### Wave 4 (2026-06-01) — CPP + trademarks + video + soundtrack

| File | Tier | What it answers |
|---|---|---|
| [`custom-product-page-variants.md`](custom-product-page-variants.md) | WARM | 70-CPP cap (Oct 29, 2025), 170-char promo text, mid-2025 keyword assignment, iOS 18+ deep links, SoundCloud -39%/+58% case, +156% avg CPP lift, PPO/CPP non-interaction except sample siphon. Tideward CPP inventory: default + 5 Tier A creator + 3-5 segment + 3 ASA = ~15 at launch. |
| [`trademark-portfolio-management.md`](trademark-portfolio-management.md) | WARM | 2026 USPTO fees verified (Section 8 $325/class, combined 8+9 $650/class). Skip watch services pre-launch. Defer Madrid Protocol Year 2-3 ($3-5k filings; worth it at >$10k/yr international revenue). Hire TM attorney for any TTAB matter. Calendar anchored to Serial 99800434. |
| [`video-press-kit-production.md`](video-press-kit-production.md) | WARM | Seven asset types (~30 deliverables): App Store preview (separate file), launch trailer 60-90s, 3-5 gameplay clips, 10 GIFs, B-roll, dev journal, per-creator thumbnails. Exact specs per type, B-roll labeling strategy, music licensing (Epidemic vs Artlist), burned-in caption rules (80% muted views), 5-phase 60-80 hour workflow. |
| [`soundtrack-ep-distribution.md`](soundtrack-ep-distribution.md) | COOL | Tier 1: 5-7 track EP. Tier 2: full album. Tier 3 vinyl deferred. Bandcamp primary ($4.99 PWYW, 40% lower fees, schedule Bandcamp Fridays) + DistroKid syndication ($23/yr) for Spotify/Apple Music. Verify music IP rights with composer (Epidemic/Artlist subscription license can't redistribute). Release T+3 months (May 2027). |

### Wave 5 (2026-06-01) — PR distribution

| File | Tier | What it answers |
|---|---|---|
| [`press-release-distribution-services.md`](press-release-distribution-services.md) | COOL | **Skip paid wires** (PRWeb $99-$455, GlobeNewswire $600-$1,200, Business Wire $400-$2,750+, EIN $149) — they reach financial/SEO syndicates, not Tier-A gaming inboxes. Skip PR agencies ($6k-$18k floor). Recommended hybrid: direct personalized outreach to 10-15 named writers + self-hosted press kit at `tideward.app/press` + Bluesky/X/Reddit amplification, $0 cash. |

### Also filed 2026-06-01 (wave not recorded)

| File | Tier | What it answers |
|---|---|---|
| [`asset-cdn-strategy-versioning.md`](asset-cdn-strategy-versioning.md) | WARM | Where public assets should live as the press kit grows: **Cloudflare R2 on a custom domain** (`assets.tideward.app`) over `raw.githubusercontent.com`, which GitHub rate-limits and which cannot be 301-redirected. Path versioning for press kits (`/press/v1/`), content-hash filenames for one-offs, three-phase additive migration. B2 and S3 rejected with numbers. **Not executed: R2 was never stood up.** The intake groups it with `promo-code-testflight-distribution.md` and `custom-product-page-variants.md` as the asset-hosting cluster. |

---

## Cross-references to sibling project research

- **Studio vs game press kit split** (which assets go in *this* repo vs `tideward-app/`): [`../../../manu-website/docs/research/game-publisher-press-kit.md`](../../../manu-website/docs/research/game-publisher-press-kit.md)
- **Press launch day playbook** (the whole T-9 → T+0 timeline): [`../../../tideward-website/docs/research/Press_Launch_Day_Playbook.md`](../../../tideward-website/docs/research/Press_Launch_Day_Playbook.md)
- **Press kit playbook with literal Tideward template**: [`../../../the-assembly-line/RESEARCH/press-kit-playbook.md`](../../../the-assembly-line/RESEARCH/press-kit-playbook.md)
- **Founder voice / when to lean in vs stay light**: [`../../../manu-website/docs/research/founder-voice-strategy.md`](../../../manu-website/docs/research/founder-voice-strategy.md)
- **Lead magnet PDFs (source of truth)**: `the-assembly-line/build_lead_magnets/`

---

## What does NOT go here

- Internal Seth-only notes — those live in private repos
- Anything embargoed / pre-announcement — public exposure burns the embargo
- NDA-protected art previews — wait for permission
- Press contact lists with names — public exposure burns the relationship
- Tideward source code, save data, or feature roadmap — wrong repo
