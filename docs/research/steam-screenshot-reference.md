# Steam Screenshot Reference (Cross-Platform Planning)
> Filed: 2026-06-01. Tier: COOL (only relevant if Steam launch decided).
> Companion to App Store storyboard work in [../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md](../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md). See also [../../../the-assembly-line/RESEARCH/2026-2027-genre-forecast.md](../../../the-assembly-line/RESEARCH/2026-2027-genre-forecast.md) §Tideward implications for the "when to decide Steam" gate.

## TL;DR
- Steam is a widescreen-first storefront. Almost nothing from the App Store portrait composition reuses cleanly: capsules are net-new art, screenshots demand fresh 1920x1080 captures from a Mac build, and the trailer wants 45-75 seconds (not 30). The only reusable assets across the boundary are the logotype, brand glyph, and editorial / press copy.
- If Tideward ships on Steam, the production estimate is roughly two weeks of solo work after the storefront approval: about 5 days for capsule variants (5 sizes), 3 days for screenshot recompositions (10-12 widescreen plates), 4 days for a 60-second trailer edited from the App Preview source footage, and a buffer for review iterations. None of this should start until iOS post-launch performance triggers a Steam decision.
- The single highest-leverage asset on Steam is the **main capsule (1232x706)**, which appears in Discovery Queue, Search, Tags, and the user's Library grid; median indie capsules sit at 1.0-2.0% visit-to-wishlist while a readability-and-clarity pass targets 3-5%. Tideward's somber scholarly identity is differentiated in this category (Melvor Idle is the only nearby cousin), so the capsule must read as "serious almanac" at 184px wide without losing the parchment+oxblood signature.
- Recommendation: do not commission Steam art before T+12 months on iOS. Track Mac sales mix, Steam Deck wishlist signals on adjacent idle titles, and the App Store post-launch CVR; if the App Store result is strong enough to fund the port, then re-open this file.

---

## Steam Asset Inventory (2026)

Steam requires **14 distinct graphical assets** before a store page can go live, plus a trailer. Pixel dimensions are exact-match (Steam rejects off-by-one); all uploads PNG or JPG. The August 2024 asset-size bump is fully phased in as of 2026; older 460x215 / 616x353 sizes are deprecated and Steam will reject submissions that use them.

### Capsules

| Asset | Dimensions | Where it appears | Notes |
|---|---|---|---|
| **Main capsule** | 1232x706 | Front page features, Daily Deals, top of category pages | The "hero" you build everything else around. Logo + key art. |
| **Small capsule** | 462x174 | Search results, top-sellers list, library, recommendations | Renders at ~184x69 in many slots; **the legibility test**. |
| **Header capsule** | 920x430 | Top of own store page, Recommended-for-You, search row | The default art people see while scrolling. |
| **Vertical capsule** | 748x896 | Front-page Featured tile when Steam features your game | Portrait-ish; required even if your game never gets featured. |
| **Page background** (optional) | 1438x810 | Behind your store page on legacy browser layouts | Mostly hidden under content; low-stakes. |

### Library Assets (logged-in users)

| Asset | Dimensions | Where it appears | Notes |
|---|---|---|---|
| **Library hero** | 3840x1240 | Top banner inside the user's Library page for your game | Safe area 860x380 center, content extends to edges. **No text allowed in the image** — text is layered separately. |
| **Library capsule** | 600x900 | Library grid view (vertical tiles) | Replaces the small capsule for owned games. |
| **Library logo** | 1280x720 max | Layered over the hero in Library | PNG, transparent background, logotype only (no character art). Position: left bottom / center top / center middle / center bottom. |

### Community Assets

| Asset | Dimensions | Notes |
|---|---|---|
| **Client icon** | 32x32 ICO | Used in the user's Library and Steam client. |
| **Community icon** | 184x184 | Appears in profile, friend activity, screenshots tab. |

### Screenshots

- **Minimum 5, recommended 8-12, maximum 30** widescreen images.
- **1920x1080 minimum, 16:9 aspect**. Higher resolutions allowed (4K useful for Steam Deck OLED + future high-DPI clients). Steam will downscale, never upscale.
- **Gameplay-only.** Per Steamworks docs: "exclusively show gameplay, avoiding concept art, pre-rendered cinematic stills, images showing awards, marketing copy, and written descriptions." Captions overlaid on the image are permitted, but text-heavy compositions are penalized in algorithmic Discovery Queue visibility per Steam's 2025 graphical asset rules update.
- **No "Wishlist Now" / award badges / sale stickers / review scores** baked into the image. Steam adds these dynamically and bakes-in marks are grounds for rejection.

### Trailer

- Up to 2 minutes accepted; **45-75 seconds is the empirical sweet spot** for indie conversion (verified 2026).
- First trailer in the list autoplays muted on the storefront; lead with gameplay in the first 5 seconds. One published roguelike A/B moved gameplay from second 18 to second 1 and lifted wishlist conversion by 31% in two weeks.
- Steam categorizes trailers in 2026: Announcement / Release / Gameplay / Accolades / Story / Cinematic. The Gameplay trailer is what 90% of cold visitors see first.

---

## Compared to App Store

| Dimension | App Store | Steam |
|---|---|---|
| Screenshot count | 3-10 per platform, six platforms = up to 60 distinct assets | 5-30 universal widescreen assets |
| Screenshot aspect | Portrait dominant (iPhone), landscape for iPad/Mac/tvOS | Universal landscape 16:9 |
| Caption style | Heavily captioned (Apple now indexes screenshot text as ranking signal as of 2025) | Captions less common; Steam grid-displays so dense text fights for attention |
| Trailer length | 15-30 seconds (Apple cap) | 45-75 sec sweet spot, up to 2 min cap |
| Localization | Per-locale screenshots + previews (granular) | Per-locale capsules only; **screenshots and trailer are global** |
| Hero asset | App icon (1024x1024) | Main capsule (1232x706) — needs key art, not just icon |
| Library presence | Home Screen icon (single image) | Hero (3840x1240) + capsule (600x900) + logo (1280x720) layered |
| Conversion target | 30-40% Search CVR is strong | 12-18% Coming Soon visit-to-wishlist is strong; 5-8% post-launch visit-to-purchase |
| First-impression real estate | App icon + first screenshot | Main capsule + trailer + first 2 screenshots |

Net: the only thing genuinely shared across the two storefronts is the **logotype** (which scales between Apple's icon mask and Steam's transparent-logo layer) and the brand glyph if there is one.

---

## The Steam "First-Screen" Pattern

Above the Steam page fold on a 1920x1080 monitor at default zoom:
1. **Main capsule** (top left, ~616x353 rendered).
2. **Trailer** (auto-playing muted, top right).
3. **First 2 screenshots** (small thumbnails under the trailer).
4. Description first paragraph, tags, "Add to Wishlist" / "Buy" button.

Conversion-critical implication: the first 2 screenshots are seen *while the trailer is still playing*. They should show the **core loop** (a populated skill grid, an active expedition, a real almanac page open) — not a title screen, not a menu, not the splash. The fastest A/B win on Steam pages under 5k wishlists in 2026 is reordering screenshots so the first two represent the most distinctive gameplay frame. (Source: gamineai.com 2026 Steam Discovery study, July 2026.)

---

## Trailer Conventions

- **Length:** 60-90s is Steam's documented recommendation; 45-75s is the indie empirical optimum. Tideward should plan for **60s** as a default, with a 90s "extended cut" optional.
- **Audio:** Storefront autoplays muted; trailer must read without sound for the first 10-15 seconds. Sound design should ramp from minimal to scored once the user unmutes.
- **Footage source:** Same shootlist as the App Preview video (see [./app-preview-video-production.md](app-preview-video-production.md)) but **extended**. Capture Mac builds at 1920x1080 60fps minimum, 4K preferred for future-proofing.
- **Structure that converts on Steam (2026 best practice):**
  - 0-5s: most arresting single gameplay frame, no logo
  - 5-25s: core loop showcase (skill progression, almanac browsing, expedition resolution)
  - 25-45s: variety / depth (different skills, different regions, the breadth pitch)
  - 45-55s: "what's in the box" (Mac/Steam Deck callouts if applicable)
  - 55-60s: logo + tagline + price tile

---

## Image Localization

- **Steam supports per-language capsules** (upload localized capsule art per language slot via the partner portal; Valve's system uses filename suffixes like `tideward_japanese.jpg` as a hint).
- **Steam does NOT support per-language screenshots or trailers.** Those are global.
- **Recommended Phase 1 languages** for an indie idle in 2026: English, Simplified Chinese, Russian, German, Japanese, Spanish. Store-page translation is cheap ($100-300/language) and Steam deprioritizes games in Discovery for users whose language isn't supported.
- **Tideward-specific:** the somber scholarly voice translates well into European languages but the "almanac" framing has weaker equivalents in Chinese/Japanese; budget for a native idle/incremental community reader to gut-check the translated description rather than running it through DeepL alone.
- **Phase 1 acceptable for solo indie launch:** English-only store page is fine if it ships with a Mandarin description as a Phase 2 fast-follow. EN-only-forever is a real ceiling-setter on Steam, more than on the App Store.

---

## Capsule Design Conventions

The capsule is the single most-tested asset on Steam. The 2026 design principles that survive A/B testing:

- **Read at 184x69.** Always downscale the main capsule to small-capsule size and place it next to direct genre competitors (Melvor Idle, NGU Idle, Idle Slayer, Cookie Clicker on Steam). If the title is illegible at thumbnail size, the capsule fails before any other concern matters.
- **One focal point.** Capsules with two competing focal points (e.g., character + logo at equal weight) lose to capsules with a single dominant element. Pick: hero art OR typographic identity, not both at equal intensity.
- **Title typography.** Typography-driven capsules outperform character capsules in the idle/strategy/sim categories (verified by 2026 Steam Discovery study). Tideward's "scholarly almanac" identity argues for typography-as-hero: a single dramatic typeset of "TIDEWARD" over parchment + oxblood, with the subtitle "An Idle Almanac" smaller.
- **Genre-legible color.** Idle/incremental Steam capsules cluster around saturated yellows + purples (genre baseline) and earthier RuneScape-derived browns (Melvor). Tideward's parchment + oxblood + gold lands in the Melvor neighborhood, which is conversion-positive for that audience but warrants explicit "looking for serious players" framing.
- **Avoid:** drop shadows on text, lens flares, "WISHLIST NOW" overlays, sale tags, awards badges, three or more characters, gradient skies.
- **2026 anti-pattern to flag:** AI-generated capsule art is now penalized in Discovery as of Steam's 2026 anti-spam graphical rules update. Hand-authored or human-illustrated art only. Steam will *not* tell you it down-weighted your page.

Reference capsules that read well at 184px wide (audit these directly before commissioning):
- Mini Metro (typographic, single-color, instant read)
- Slay the Spire (single character + crisp title)
- Stardew Valley (character grid + logo, but the logo is dominant)
- Cultist Simulator (typographic, mood-driven, no character)
- **Melvor Idle (the direct genre cousin):** crest-style logomark on a textured background, ~10/10 legible at thumbnail

---

## Tideward-Specific Hypothetical

If Tideward launches on Steam in 2027-2028 (per current strategy):

- **Main capsule (1232x706):** Parchment ground (warm cream #F4E8D0), oxblood title "TIDEWARD" set in a high-contrast transitional serif (GT Sectra / Tiempos Headline / EB Garamond at display weight), gold rule beneath, subtitle "An Idle Almanac" in a humanist sans (Inter / SF Pro semibold). Single ornament glyph — a quill, an open book, a tide-rune — bottom right. No character. The capsule reads as "this is a book about a world," not "this is a game about a hero."
- **Small capsule (462x174):** Compressed version of the main capsule. Drop the subtitle, keep just "TIDEWARD" + ornament. Must pass the 184x69 legibility test.
- **Vertical capsule (748x896):** Same identity, taller. Room for the ornament to grow into a small almanac-page illustration above the title.
- **Library hero (3840x1240):** Wide parchment spread, no text (Steam adds the logo layer separately). Center 860x380 safe area shows an open almanac with handwritten skill annotations.
- **Library logo:** "TIDEWARD" + "An Idle Almanac" on transparent background, positioned center-middle over the hero.
- **Screenshots (8-10 widescreen 1920x1080):** Recompositions of the App Store iPhone storyboard at landscape aspect. Mac UI chrome visible. Captions optional and sparse — Steam grid-displays so 8 captioned screenshots become wallpaper rather than reading material.
- **Trailer (60s):** Open on an almanac page filling the frame, a quill noting an XP tick; cut to the active skill grid, then to an expedition resolution, then to a region map, then to the Mac menu bar showing Tideward running quietly. Close on logo + "One purchase. No subscriptions. No ads. Ever."
- **Tags (Steam's discovery engine):** Idle, Incremental, Indie, Singleplayer, Resource Management, Crafting, Premium, Singleplayer, Atmospheric, Relaxing, Text-Based. Avoid: RPG (too contested), Casual (signals F2P to this audience), Clicker (Tideward isn't one).

---

## Asset Reuse from App Store

| Asset | Reusable from App Store? |
|---|---|
| Logotype + glyph | Yes (designed once, used in both icon mask and Steam logo layer) |
| Brand colors + typography system | Yes |
| Capsule key art | **No** — Steam capsules need from-scratch composition at every size |
| Screenshots | **No** — App Store portrait/landscape do not crop usefully to 1920x1080 widescreen; recapture from Mac build at the canonical resolution |
| Trailer | **Partial** — same shootlist and source footage, but Steam wants a longer cut (60s vs 30s) so re-edit, do not re-export |
| Editorial / description copy | Mostly yes — Steam allows ~2000 chars on the long description (more than App Store's promo text), so the App Store description is a strict subset |
| Tags / categories | No (Steam tag taxonomy is its own thing; map manually) |
| Localizations | Capsule yes (per-language slots), screenshots/trailer no (global) |

The honest accounting: **the logotype, color system, type system, copy, and trailer source footage cross the boundary; everything visual gets remade.** Budget for ~10-12 days of solo design + capture + edit work in a contiguous block, not as a side-task during App Store launch.

---

## When the Steam Decision Becomes Real

Per [../../../the-assembly-line/RESEARCH/2026-2027-genre-forecast.md](../../../the-assembly-line/RESEARCH/2026-2027-genre-forecast.md) §Tideward implications and current product policy: **do not make the Steam decision pre-launch.** The cost of building Steam capsules + screenshots + trailer before App Store data validates demand is two weeks of solo dev work that could go into the iOS post-launch patches.

Re-evaluation gate, **T+12 months from App Store launch**, based on:
1. **iOS post-launch CVR.** If App Store visit-to-install is north of 5% sustained, the audience is there.
2. **Mac sales mix.** Mac App Store ≥15% of paid units signals desktop demand strong enough to justify a second desktop storefront.
3. **Steam Deck demand signal.** Adjacent idle titles on Steam Deck (Melvor Idle ranks high on Deck's "Most Played Indie Idle" leaderboard as of mid-2026) suggest Tideward has a real Deck audience — verify against current Deck wishlist patterns on cousin titles before committing.
4. **iOS revenue exceeds Steam build cost by 3x or more.** Steam port (capsule art + screenshots + trailer + Steamworks integration + QA on Deck) is ~3-4 weeks of work plus Valve's $100 Direct fee. If iOS profit doesn't fund that with safety margin, defer.

If all four signals fire green at T+12mo, re-open this file and begin Steam asset production. Until then, this is informational only.

---

## Sources

- [Library Assets - Steamworks Documentation](https://partner.steamgames.com/doc/store/assets/libraryassets)
- [Store Graphical Assets - Steamworks Documentation](https://partner.steamgames.com/doc/store/assets/standard)
- [Graphical Assets Overview - Steamworks Documentation](https://partner.steamgames.com/doc/store/assets)
- [Steam Capsule Art Guide 2026 - presskit.gg](https://presskit.gg/field-guides/steam-capsule-art-guide)
- [Steam Capsule Image Requirements 2026 - steampagecheck.com](https://steampagecheck.com/capsule-images.html)
- [Steam Capsule Sizes and Dimensions - Steam Analyser](https://www.steamanalyser.com/steam-capsule-size)
- [Every Image You Need for Your Steam Store Page - game-oracle.com](https://www.game-oracle.com/blog/steam-store-images)
- [Trailers - Steamworks Documentation](https://partner.steamgames.com/doc/store/trailer)
- [How Long Should a Game Trailer Be? 2026 Steam Guidelines - indiegametrailers.com](https://indiegametrailers.com/2024/08/30/how-long-should-a-game-trailer-be/)
- [Steam Store Page Conversion Rates 2026 - Steam Page Analyzer](https://www.steampageanalyzer.com/blog/steam-store-page-conversion-benchmarks)
- [Wishlists Tripled in 90 Days - 2026 Capsule, Tag, Demo Page Changes - gamineai.com](https://gamineai.com/blog/wishlists-tripled-90-days-2026-capsule-tag-demo-page-changes-actually-move-needle-steam-discovery)
- [Steam Page Localization Guide - presskit.gg](https://presskit.gg/field-guides/steam-page-localization)
- [Languages Supported on Steam - Steamworks Documentation](https://partner.steamgames.com/doc/store/localization/languages)
- [Graphical Asset Rules - Steamworks Documentation](https://partner.steamgames.com/doc/store/assets/rules)
- [Steam increases Store image requirements - gamedeveloper.com](https://www.gamedeveloper.com/business/steam-increases-store-image-requirements-details-phase-out-of-old-specs)
- Companion: [App Store screenshot blueprint](../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md)
- Companion: [2026-2027 genre forecast](../../../the-assembly-line/RESEARCH/2026-2027-genre-forecast.md)
