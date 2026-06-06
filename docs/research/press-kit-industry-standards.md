# Gaming Press Kit: Industry Standards (2026)

> Filed: 2026-06-01. Tier: WARM (pre-launch asset prep for Tideward, ship 2027-02-11).
> Scope: Apple-platform indie game (iOS / iPadOS / macOS / tvOS / visionOS / watchOS).
> Repo context: `Manu-Team/manu-marketing` is a PUBLIC GitHub repo. Anything filed here is web-discoverable.

## TL;DR

A 2026 press kit is graded on **floor coverage**, not ceiling polish. Across press, podcast, and Apple editorial workflows, journalists and producers consistently reach for the same handful of files: **screenshots, key art, logo, factsheet, trailer**. Get those right at the dimensions below and you've cleared the bar that gets you covered. Anything beyond is bonus that occasionally tips a feature decision but never rescues a missing floor.

The dimension story in 2026 is **dominated by Apple's device cadence**: iPhone 17 Pro Max (6.9", 1320×2868) and iPad Pro M4/M5 (13", 2064×2752) are the new "primary" sizes for App Store assets. Provide native at those two sizes and Apple scales the rest. Outside Apple, the press world has converged on **4K key art + 1920×1080 (or 3840×2160) screenshots + 1200×630 OG**.

Critical empirical finding from the audit: Martin Robinson, former Editor-in-Chief of Eurogamer, summarized what journalists actually open from press kits as "a folder of nine to 12 screenshots, a trailer, a small amount of b-roll, and perhaps most importantly some good high-quality artwork." Build to that profile.

Public-repo caveat: because `marketing/` is public, this kit doubles as marketing collateral the moment it's pushed. No NDA material, no embargoed builds, no private contacts.

---

## THE MINIMUM VIABLE PRESS KIT (10 Files)

Each row below is a hard floor. Press kits missing any of these regularly get passed over or covered with stock substitutes.

| # | Asset | Floor spec | Why it's load-bearing |
|---|---|---|---|
| 1 | **Logo** | Vector SVG + 1024×1024 PNG transparent (light + dark variants) | Press composites logos against varied backgrounds; transparency + dark/light cover both. SVG covers any print or scale-up. |
| 2 | **App icon** | 1024×1024 PNG, no transparency, sRGB | Apple's master icon size; outlets reuse it as the article hero in roundups. |
| 3 | **Key art** | 3840×2160 (4K, 16:9 landscape), PNG or high-quality JPEG (90-95%); also provide 3:4 portrait and 1:1 square variants | "Most importantly some good high-quality artwork" (Robinson, ex-Eurogamer). Used as article hero, social card, podcast episode art. |
| 4 | **Screenshots, iPhone** | 5-10 PNGs at **1320×2868** (iPhone 6.9" Pro Max class — covers 17 Pro Max, 16 Pro Max, 16 Plus, 15 Pro Max, 15 Plus, 14 Pro Max) | Apple's primary screenshot slot in 2026; if uploaded, it scales down for 6.5", 6.3", 6.1". Skipping this forces Apple to upscale older sizes. |
| 5 | **Screenshots, iPad** | 5-10 PNGs at **2064×2752** (iPad 13" — iPad Pro M5/M4, iPad Air M4/M3/M2) | Apple's required primary iPad size; covers down to 11" and 10.5" via Apple scaling. |
| 6 | **Trailer** | 1080p MP4 (H.264) at 30 or 60 fps, 25 Mbps+ bitrate, AAC stereo, **direct download link** plus YouTube embed | Press requires the actual file, not a YouTube link, for embedding inside their CMS. Eurogamer / RPS / GameSpot all reuse trailer frames as B-roll. |
| 7 | **Fact sheet** | Single-page PDF + plain-text or Markdown twin | Title, developer, publisher, platforms, release date, price, genre, engine, player count, content rating, website, social handles, press contact. Scannable in under 10 seconds. |
| 8 | **Boilerplate descriptions** | 50-word + 150-word + 500-word variants, plain text | 50 = social caption / podcast intro; 150 = news brief; 500 = preview article skeleton. Outlets paste these directly. |
| 9 | **Founder bio + headshot** | 50/150/500-word bio variants. Headshot at 2000×2000 (1:1, full color) + same at 1:1 800×800 web-optimized | Used by podcasts, profile pieces, founder-story coverage. Square crop is podcast guest standard. |
| 10 | **Press contact + release template** | `press@tideward.app` mailbox + a release template (Markdown + PDF) | Without a clear contact and a starter template that outlets can rephrase, coverage stalls. Two prominent placements on the press page minimum. |

**ZIP it all** as one downloadable archive at the top of the kit, plus expose every file individually. Press regulars want the ZIP; first-time reviewers want one specific file.

---

## DESIRABLE EXTRAS

These don't fail the kit if absent, but materially improve odds of features, podcast bookings, and creator pickup:

- **Gameplay GIFs** — 5-10 loops, 10-15 seconds, 1080p, MP4 + WebM (Discord embeds prefer WebM under 8MB). Single most-shared format on Bluesky and Discord in 2026.
- **B-roll footage** — 60-90 seconds raw unedited gameplay, no overlays / music / cuts, 4K downsampled to 1080p delivery file (Disobey guide; Robinson confirms "a small amount of b-roll" is in the journalist's working set). Lets YouTube / TikTok creators score-and-cut without rebuilding from your trailer.
- **Alternative key art variants** — with and without logotype overlay; landscape, portrait, square. Saves the press designer's time and increases the chance your art is what runs.
- **Illustrated character roster** — transparent PNGs of hero characters, each on its own file. Thumbnail-makers reuse these constantly.
- **World bible PDF** — 5-15 pages of lore, factions, setting. Powers the "explainer" features that drive long-tail traffic.
- **Sound clips for podcasts** — 3-5 SFX, 3-5 music stings, WAV (mastered) + MP3 (preview). Producers drop these into intros and transitions.
- **Soundtrack samples** — 1-2 minute MP3 + WAV with cleared use rights spelled out in a `LICENSE-AUDIO.txt`.
- **Character voice samples** (if applicable) — same dual format, with named cast file alongside.
- **Apple-specific bonus assets** — Apple Promotional Artwork templates filled in (Today Tab card, product page hero). Apple's editorial team requests these directly via App Store Connect when considering a feature; pre-baking them signals readiness.
- **Brand kit** — hex codes, font files (OTF/TTF) with embedding license, logo usage rules (clear-space, minimum size, do/don't pairs).
- **Awards & quotes block** — once any coverage drops, slot it in. Becomes self-reinforcing for the next outlet.
- **Embargo notice** — exact date + hour in PT, ET, GMT, JST. Standard professional courtesy; absence reads amateur.

---

## DIMENSIONS REFERENCE TABLE

Every dimension below is verified against either Apple's developer documentation or convergent independent sources. The "Where used" column tells you which slot the asset feeds.

### Apple platform assets

| Asset | Dimensions | Format | Limit | Where used | Source |
|---|---|---|---|---|---|
| iPhone 6.9" screenshot | **1320×2868** (P) / 2868×1320 (L) | PNG / JPEG | 1-10 per device, no alpha | App Store iPhone 17/16 Pro Max, 16 Plus, 15 Pro Max, 15 Plus, 14 Pro Max | Apple developer docs |
| iPhone 6.5" screenshot | 1284×2778 (P) / 2778×1284 (L) | PNG / JPEG | 1-10 | App Store iPhone 14 Plus, 13 Pro Max, 12 Pro Max, 11 Pro Max, 11, XS Max, XR | Apple |
| iPhone 6.3" screenshot | 1206×2622 (P) / 2622×1206 (L) | PNG / JPEG | 1-10 | App Store iPhone 17 Pro, 17, 16 Pro, 16, 15 Pro, 15, 14 Pro | Apple |
| iPhone 6.1" screenshot | 1170×2532 (P) / 2532×1170 (L) | PNG / JPEG | 1-10 | App Store iPhone 17e, 16e, 14, 13 Pro, 13/mini, 12 Pro, 12/mini, 11 Pro, XS, X | Apple |
| iPad 13" screenshot | **2064×2752** (P) / 2752×2064 (L) | PNG / JPEG | 1-10, REQUIRED | App Store iPad Pro M5/M4, iPad Air M4/M3/M2 | Apple |
| iPad 12.9" screenshot | 2048×2732 (P) / 2732×2048 (L) | PNG / JPEG | optional | App Store legacy iPad Pro 2nd gen | Apple |
| iPad 11" screenshot | 1488×2266 (P) / 2266×1488 (L) | PNG / JPEG | optional | App Store iPad Pro 4th-1st gen, iPad Air | Apple |
| Mac screenshot | 1280×800, 1440×900, **2560×1600**, 2880×1800 (16:10) | PNG / JPEG | 1-10, REQUIRED | App Store Mac | Apple |
| Apple TV screenshot | 1920×1080 or **3840×2160** | PNG / JPEG | 1-10, REQUIRED | App Store tvOS | Apple |
| Apple Vision Pro screenshot | **3840×2160** | PNG / JPEG | REQUIRED | App Store visionOS | Apple |
| Apple Watch Ultra 3 | 422×514 | PNG / JPEG | REQUIRED | App Store watchOS Ultra 3 | Apple |
| Apple Watch Series 11/10 | 416×496 | PNG / JPEG | optional | App Store watchOS Series 11/10 | Apple |
| App icon master | 1024×1024 | PNG, **no alpha, sRGB** | mandatory | App Store, editorial features, Today tab | Apple |
| App Preview video | per device (see below) | MP4 / MOV / M4V | 15-30 sec, ≤500 MB | App Store preview slot, all platforms | Apple |

### App Preview video specs (Apple)

| Device | Portrait | Landscape | Length | Codec |
|---|---|---|---|---|
| iPhone 6.9" / 6.5" / 6.3" / 6.1" | 886×1920 | 1920×886 | 15-30 sec | H.264 ≤Level 4.0 @ 10-12 Mbps, AAC 256 kbps stereo, ≤30 fps. ProRes 422 HQ ~220 Mbps acceptable. |
| iPhone 5.5" / 4" | 1080×1920 | 1920×1080 | 15-30 sec | Same |
| iPhone 4.7" | 750×1334 | 1334×750 | 15-30 sec | Same |
| iPad 13" / 11" / 10.5" | 1200×1600 | 1600×1200 | 15-30 sec | Same |
| iPad 9.7" | 900×1200 | 1200×900 | 15-30 sec | Same |
| Mac | — | 1920×1080 | 15-30 sec | Same |
| Apple TV | — | 1920×1080 | 15-30 sec | Same |
| Apple Vision Pro | — | 3840×2160 | 15-30 sec | Same |

Audio: 44.1 or 48 kHz, stereo (1 track of 2-channel, or 2 tracks of mono L/R). PCM 16/24/32-bit acceptable for ProRes.

### Press / editorial / social assets

| Asset | Dimensions | Format | Where used |
|---|---|---|---|
| Key art (master) | **3840×2160** (16:9) | PNG or JPEG 90-95% | Article hero, podcast cover, store featured banner |
| Key art (portrait) | 1600×2400 or 1200×1600 (2:3 / 3:4) | PNG / JPEG | IGDB box-art slot (1200×1600), vertical hero on mobile |
| Key art (square) | 2400×2400 (1:1) | PNG / JPEG | Bluesky / X feed, Instagram, podcast cover backstop |
| Game logo (with text) | Vector SVG + 2400×1200 PNG transparent | SVG + PNG | Hero compositing, light + dark variants |
| Game logo (mark only) | Vector SVG + 1024×1024 PNG transparent | SVG + PNG | Avatar, badge, small-screen substitution |
| Open Graph image | **1200×630** | PNG or JPEG | Twitter card, Bluesky card, Discord embed, LinkedIn |
| Twitter/X horizontal | 1600×900 | PNG / JPEG | X in-feed image |
| Twitter/X square | 1080×1080 | PNG / JPEG | X in-feed, threaded image |
| Twitter/X vertical | 1080×1350 (4:5) | PNG / JPEG | X mobile-first feed |
| Bluesky banner | 1500×500 | PNG / JPEG | Profile header |
| YouTube thumbnail | **1280×720** (16:9) | JPEG | Trailer + devlog thumbs (≤2 MB) |
| Trailer master | 3840×2160 ProRes 422 HQ | MOV | Archive master; ProRes ~220 Mbps |
| Trailer press deliverable | **1920×1080** H.264 MP4 | MP4 | Direct download for press CMS use, 25 Mbps+ |
| Trailer YouTube cut | 1920×1080 H.264 MP4 (45 Mbps VBR) | MP4 | YouTube upload |
| B-roll | 1920×1080 H.264 MP4, 60-90 sec, no overlays | MP4 | Creator / streamer reuse |
| Animated GIF / WebM | 1080p (or 720p for size), 10-15 sec loop, ≤8 MB | MP4 + WebM (GIF if must) | Discord embed, Bluesky feed |
| Podcast cover backstop | **3000×3000** (1:1) | JPEG @ 80-90% under 512 KB | Apple Podcasts (1400×1400 floor), Spotify (640×640 floor) |
| Founder headshot | 2000×2000 (1:1) | JPEG / PNG | Podcast guest art, profile features |
| Founder headshot web | 800×800 (1:1) | JPEG optimized | Press kit page, About page |

---

## FILE FORMAT RULES

**Always provide:**

- **Vector** (SVG) when one exists. Single file scales infinitely. Logos and icons especially.
- **PNG transparent** for anything that will composite over arbitrary backgrounds (logos, icons, character cutouts, UI elements).
- **JPEG opaque** at 90-95% quality for photographs and dense screenshots. Files are 3-5x smaller than PNG, and 90-95% is visually indistinguishable.
- **PNG** for App Store screenshots even if larger — Apple's preference, especially for text clarity.
- **MP4 H.264** for any video deliverable to press (universal CMS support). Pair with **WebM** for in-page embeds and Discord previews.
- **WAV** mastered and **MP3** preview for any audio (SFX, music, voice).

**Never provide:**

- **PSD / AI / RAW** as the primary deliverable. Optional in a "source files" folder for designers who ask, but never as the only version of an asset.
- **BMP / TIFF** for web/press. TIFF acceptable only in a print-specific subfolder.
- **GIF** as a trailer or screenshot substitute. GIF is acceptable only for tiny chat-embed loops where MP4/WebM autoplay isn't supported.
- **HEIC** for press. Outlets' CMSs choke on it. Convert to JPEG before publishing.

**Naming convention** — every file gets a descriptive, lowercase, hyphenated filename: `tideward-screenshot-04-combat-forest-1320x2868.png`. Filenames show up in URLs and journalists' download folders; clarity here pays for itself.

---

## WHAT PRESS ACTUALLY USES

The single most-cited working-set statement is from Martin Robinson, former Editor-in-Chief of Eurogamer, quoted in the 2026 presskit.gg guide: journalists open "a folder of nine to 12 screenshots, a trailer, a small amount of b-roll, and perhaps most importantly some good high-quality artwork."

Games Press (`gamespress.com`), the dominant press asset clearinghouse with 30,000+ registered journalists, surfaces the same four-asset working set: screenshots, key art, trailer, fact sheet. They explicitly ask users to "only download the images and files they actually need to accompany their editorial" — the platform has no fixed quota but the norm is **2-4 screenshots + 1 key art + 1 trailer cut** per published article.

Audit takeaway for solo devs: **optimize the floor for journalist throughput**, not for completeness. A press kit with 10 screenshots, one strong piece of key art, one 30-second trailer that downloads, and a one-pager fact sheet will be picked up faster than a kit with 50 screenshots and no fact sheet. Most coverage uses 2-3 screenshots and the trailer. Anything beyond is for the 10% of features that go deep.

Featured Apple App Store editorial picks lean on different assets — Apple's editorial team works from "Promotional Artwork" templates that developers fill in inside App Store Connect (Today Tab card, product page hero, Apps tab card). Apple provides these as custom templates, and the artwork **excludes** UI screenshots, logos of other companies, weapons, hardware models, pricing, and Apple wordmarks. Pre-baking those templates signals editorial readiness even before Apple requests them.

---

## ASSET HOSTING PATTERNS

Six realistic hosting setups for a solo dev in 2026:

| Pattern | Cost | Bandwidth | Pros | Cons |
|---|---|---|---|---|
| **GitHub raw URLs (current path)** | Free | Soft-capped, not for hot traffic | Already where the marketing repo lives. Zero new infra. URL stability tied to git history. | Not designed as a CDN; rate-limited under spike load. Public-repo only. Repo size cap (1 GB recommended, 5 GB hard) limits high-res video. |
| **GitHub Pages** | Free | 100 GB/mo soft, 100k req/mo soft | Custom domain, HTTPS, sits on top of repo. | Same bandwidth caveats as raw. Static only. |
| **Cloudflare R2** | $0.015/GB/mo storage, **$0 egress** | Unlimited egress | Zero bandwidth cost is decisive for video-heavy kits. Pair with Cloudflare CDN (already in front of tideward.app). Native S3-compatible. | Requires Worker or public bucket policy to expose URLs. Slight setup overhead. |
| **Cloudflare Pages** | Free tier (500 builds/mo, unlimited bandwidth) | Unlimited | Free + fast + same vendor as tideward.app DNS. | Static only; tied to a separate repo or branch. |
| **Backblaze B2 + bunny.net or Cloudflare CDN** | ~$0.005/GB storage + CDN egress | High | Cheapest storage. Pairs with CDN of your choice. | Two-vendor setup; B2 alone has paid egress without a CDN cache. |
| **AWS S3 + CloudFront** | $0.023/GB storage + ~$0.085/GB egress | High | Industry standard, every dev knows it. | Most expensive for video traffic. Bills surprise solo devs during launch spikes. |

**Recommended for Tideward**: Cloudflare R2 + a Worker or public bucket policy on the `tideward.app` domain. R2 zero-egress + existing Cloudflare presence on tideward.app + manugames.com makes it the lowest-friction high-headroom option for a launch where one viral trailer download could blow a GitHub bandwidth quota. For the lead-magnet PDFs and small images already in `marketing/`, GitHub raw URLs are fine. Move only the video and ZIP archive to R2.

**Don't** rely on Google Drive or Dropbox public links. Press desks block them as security risk; the link rot under load is real; analytics are zero.

---

## REVIEW-COPY DELIVERY

For an Apple-platform launch in 2026, three delivery channels stack:

**1. TestFlight (primary)** — Apple Developer Program covers TestFlight at the $99/yr membership cost. Up to **10,000 external testers** via either email invite or public link. First build per app requires App Review (typically <24 hr in 2026; ~90% of submissions clear inside a day). Subsequent builds in the same group don't re-review unless they cross a beta-eligibility threshold.

**Mechanics that matter for press distribution:**
- Create a dedicated TestFlight group named "Press" (or per-outlet groups like "Press-IGN", "Press-PocketGamer") so revoking access is per-group.
- Use the public link in private email to outlets. Don't post the public link anywhere indexable until launch — it's a slot drain otherwise.
- Builds in the sandbox environment process IAPs without real money, so reviewers can exercise the full economy.
- TestFlight slots are per build, not per app. A press group of 50 reviewers consumes 50 of the 10,000.

**2. App Store promo codes (post-launch)** — Once the app is live, you get **100 promo codes per platform per app per version**. These grant free download of the live app from the App Store. Use these for late-add outlets and creators who want the live experience rather than a beta build. TestFlight promo code behavior for IAPs is unreliable in 2026 (confirmed limitations on testing IAP promo flow inside TestFlight); reserve App Store promo codes for the live-app handoff.

**3. Apple editorial submission via App Store Connect** — Separate from press: use the "Pitch your app to Apple editors" flow inside App Store Connect at least 4-6 weeks before launch. This is the channel for Today Tab features, "Apps We Love," and Apple Arcade negotiation. Pre-baked Promotional Artwork dramatically raises the strike rate.

**Don't:**
- Don't burn promo codes on people who can install the live app for free anyway (other devs, friends).
- Don't share TestFlight build URLs in public Discord channels — they're public links and slot quotas are real.
- Don't send 50 outlets the same code; track per-outlet so you know who covered.

**For Tideward specifically**, given the Feb 11 2027 launch: open a press-only TestFlight group around 6 weeks before launch (early January 2027). Stage builds. Reserve ~30 App Store promo codes per platform for post-launch late-adds.

---

## VERSIONING & DATESTAMPS

Press kits go stale fast. Three hygiene rules:

1. **"Last updated" date** at the top of every press kit page, in ISO format. Re-bump on every meaningful change. Outlets check the date to gauge whether what they're seeing matches the live game.
2. **Quarterly review pass** even when nothing changes. Walk every link, every file. Update the boilerplate if any factsheet line is wrong (price, platforms, release window).
3. **Datestamped filenames for substantive revisions** — `tideward-key-art-landscape-v2-2027-01-15.png`, not just `tideward-key-art-landscape.png`. Older revisions stay accessible so journalists who cached the old version can confirm they have current. Symlink `tideward-key-art-landscape-latest.png` to the current revision.

For Tideward, plan three major press-kit revisions:
- **2026-Q4** — initial public-press version, Tideward branded, no live screenshots yet (placeholder key art OK).
- **2027-Q1, pre-embargo** — locked-down screenshots, final trailer, final fact sheet, embargo notice with exact PT/ET/GMT/JST times.
- **2027-Q1, embargo-lifted** — strip the embargo notice, add an "Awards & Press Quotes" block, replace fact-sheet release-date field with "Out Now."

---

## Public-Repo Specifics

`Manu-Team/manu-marketing` is a public GitHub repo. Everything filed under `marketing/` is web-discoverable the moment it's pushed — by Google, by archive.org, by competitors monitoring repo activity. Concrete implications:

- **No private contacts.** The press contact is `press@tideward.app` (a Cloudflare-routed alias), never a personal email. Do not commit a phone number.
- **No NDA-protected previews.** Anything you'd show only behind an NDA gets staged in `tideward-app/`, not here. NDA assets ship via password-protected R2 buckets or email attachments, not the public press kit.
- **No pre-announcement embargoed material.** If Tideward is announcing a partnership or DLC, the announcement doc lives in `tideward-app/` until the embargo lifts, then is pushed to `marketing/`.
- **No draft press releases.** Drafts go in a private repo or in `the-assembly-line/`. Only finalized, embargo-cleared releases ship here.
- **README reminder.** The `marketing/README.md` should include a "Before committing" checklist that future-Seth and future-LLM-sessions see: no contacts, no NDA, no embargoed copy, no draft.

The `marketing/` repo benefits from public discoverability — Google indexes a key-art file, that's marketing surface area you'd otherwise pay to acquire. The trade-off is irreversibility: anything committed is in git history forever, even after deletion. Treat the commit threshold accordingly.

---

## Sources

Apple developer documentation (canonical):
- [Apple — App Store Screenshot Specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications/)
- [Apple — App Preview Specifications](https://developer.apple.com/help/app-store-connect/reference/app-information/app-preview-specifications)
- [Apple — Invite External Testers (TestFlight)](https://developer.apple.com/help/app-store-connect/test-a-beta-version/invite-external-testers/)
- [Apple — TestFlight Overview](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/)
- [Apple — Provide Test Information](https://developer.apple.com/help/app-store-connect/test-a-beta-version/provide-test-information/)
- [Apple — TestFlight](https://developer.apple.com/testflight/)
- [Apple — App Store Submission](https://developer.apple.com/app-store/submitting/)

Industry guides and press-kit standards:
- [presskit.gg — Complete Guide to Indie Game Press Kits (2026)](https://presskit.gg/blog/indie-game-press-kit-guide)
- [presskit.gg — Best Press Kit Tools for Indie Games (2026)](https://presskit.gg/blog/best-press-kit-tools-indie-games)
- [presskit.gg — Steam Capsule Art Guide (2026)](https://presskit.gg/field-guides/steam-capsule-art-guide)
- [Disobey — How to Make a Video Game Press Kit](https://www.disobey.gg/blog/how-to-make-a-video-game-press-kit-the-ultimate-guide-for-indie-devs)
- [Indieformer — Press Kit Guide for Indie Games](https://www.indieformer.com/press-kit-guide)
- [Acorn Games — Indie Dev's Guide to Assembling the Perfect Press Kit](https://acorngames.gg/blog/2024/6/12/the-indie-devs-guide-to-assembling-the-perfect-press-kit)
- [GameTrowel — How to Build an Effective Game Press Kit](https://gametrowel.com/blog/how-to-build-an-effective-press-kit-for-your-indie-game-with-a-copy-paste-checklist)
- [Pirate PR — What needs to be in your Press Kit?](https://piratepr.com/treasure-trove/what-needs-to-be-in-your-press-kit/)
- [GameAnalytics — How to Create a Press Kit for Your Mobile Game](https://www.gameanalytics.com/blog/press-kit-mobile-game)
- [IMPRESS — Video Game Press Kit Examples](https://impress.games/video-game-press-kit-examples)
- [Jaleo PR — How to Create a Good Press Kit for Your Indie Game](https://jaleopr.com/blog/create-good-press-kit-indie-game/)
- [dopresskit.com — presskit() by Rami Ismail](https://dopresskit.com/)

Press distribution & editorial:
- [Games Press](https://www.gamespress.com/en-US)
- [Gummicube — What is Apple Promotional Artwork?](https://www.gummicube.com/blog/aso-academy/apple-promotional-artwork)
- [MobileAction — App Store Screenshot Sizes & Guidelines (2026)](https://www.mobileaction.co/guide/app-screenshot-sizes-and-guidelines-for-the-app-store/)
- [Screenhance — App Store Screenshot Dimensions 2026: iPhone 17 & iPad Pro](https://screenhance.com/blog/app-store-screenshot-dimensions-2026)
- [Apple Launch Pad — App Store Screenshot Guidelines 2026](https://theapplaunchpad.com/blog/app-store-screenshot-guidelines/)

Video / trailer specs:
- [Derek Lieu — Video Game Trailer Specifications List](https://www.derek-lieu.com/blog/2017/10/13/video-game-trailer-specifications-list)
- [DIY Photography — Video Bitrate Guide 2025](https://www.diyphotography.net/video-bitrate-explained-guide/)

Social and OG image dimensions:
- [Hootsuite — Social Media Image Sizes 2026](https://blog.hootsuite.com/social-media-image-sizes-guide/)
- [Buffer — Social Media Image Sizes 2026](https://buffer.com/resources/social-media-image-sizes/)
- [OGMagic — Social Media Preview Image Sizes 2026](https://ogmagic.dev/blog/social-media-preview-image-sizes)
- [SocialPilot — Social Media Image Sizes Cheat Sheet 2026](https://www.socialpilot.co/blog/social-media-image-sizes)

Podcast art specs:
- [Transistor — Specs for Podcast Cover Art (Apple Podcasts, Spotify)](https://support.transistor.fm/en/article/specs-for-podcast-cover-art-on-apple-podcasts-spotify-etc-1dyjud8/)
- [Moda — Podcast Cover Art Size 2026](https://moda.app/resources/sizes/spotify-podcast-cover)
- [Podcastools — Podcast Cover Art Size: The 2026 Guide](https://www.podcastools.com/blog/podcast-cover-art-size)

iOS distribution & promo codes:
- [Foresight Mobile — iOS Distribution Guide 2026](https://foresightmobile.com/blog/ios-app-distribution-guide-2026)
- [PTKD — TestFlight vs Sandbox: How Do I Test In-App Purchases](https://ptkd.com/journal/testflight-testing-iap-guide)
