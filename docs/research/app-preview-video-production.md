# App Preview Video Production Playbook (2026)
> Filed: 2026-06-01. Tier: WARM (launch deliverable).
> Sibling brief: `screenshot-pipeline-architecture.md` (in `the-assembly-line/RESEARCH/`) covers still-frame production. This file covers the moving-picture pipeline only.

## TL;DR

The App Store lets you upload up to **three 30-second app previews per device class per locale**, capped at **500 MB each**, with **strict resolution / aspect-ratio matching** by device. Videos autoplay **muted**, so the asset has to read as a silent film with burned-in captions and visible tap indicators; voiceover is permitted but a trap for indie teams (it locks the asset to a single language and a single UI revision). Tideward's v1.0 plan: **one master 30-second portrait video, captioned, scored with a single licensed harpsichord/lute cue, no voiceover, no device frame, real device capture**, edited in DaVinci Resolve (free), uploaded to the iPhone 6.9" slot as 886x1920 H.264. Storyboard: 0-4s seal-opening hook, 4-22s the loop (character, combat, skills, almanac), 22-30s "An Idle Almanac" sign-off. Budget: $300-1000 if outsourced to Fiverr/Upwork; ~$60 plus a weekend if self-edited (one-month Epidemic Sound license + your own labor). Localize Phase 1 with translated caption tracks only; reuse the master video and the music track unchanged.

---

## App Store Preview Specs (2026)

Apple enforces these specs hard — the wrong aspect ratio gets rejected on upload, not at review. Numbers below are pulled from the **App Store Connect Reference: App preview specifications** page as it stands May 2026.

### Global rules (every device class)

| Spec | Value |
|---|---|
| Max file size | **500 MB** per video |
| Min length | **15 s** |
| Max length | **30 s** |
| Default poster frame | 5 s mark |
| Max videos per locale per device class | **3** |
| Container | `.mov`, `.m4v`, `.mp4` |
| Codec | **H.264** (High Profile L4.0, ≤30 fps, 10-12 Mbps target) or **ProRes 422 HQ** (≤30 fps, ~220 Mbps VBR) |
| Audio | AAC 256 kbps stereo @ 44.1/48 kHz, or PCM 16/24/32-bit |
| Frame rate | 24, 25, 29.97, or 30 fps. **No 60 fps.** Record at 60, conform to 30 on export. |

### Per-device resolution & orientation

| Device class | Accepted resolution (portrait) | Orientation rules |
|---|---|---|
| iPhone 6.9", 6.5", 6.3", 6.1" (modern, Face ID) | **886 x 1920** (or 1920 x 886 landscape) | Portrait or landscape |
| iPhone 5.5" (legacy home-button) | 1080 x 1920 | Portrait or landscape |
| iPhone 4.7" | 750 x 1334 | Portrait or landscape |
| iPad 13" / 12.9" / 11" / 10.5" | 1200 x 1600 (or 1600 x 1200) | Portrait or landscape |
| iPad 9.7" | 900 x 1200 | Portrait or landscape |
| Mac | 1920 x 1080 | **Landscape only** |
| Apple TV | 1920 x 1080 | **Landscape only** |
| Apple Vision Pro | 3840 x 2160 | **Landscape only** |

If you skip a device class, App Store Connect scales a sibling preview down for you automatically. For Tideward the lift-to-impact ratio says: ship the iPhone 6.9" portrait video first, let it scale for 6.5"/6.3"/6.1" slots, and only commission a dedicated iPad slot once the iPhone slot is converting. Mac/Apple TV/Vision Pro previews are landscape-only and the gameplay choreography is materially different — those are separate productions, parked for v1.1+.

---

## Apple's Hard Requirements

Distilled from Apple's official **App Previews** marketing page plus the App Review Guidelines:

- **Real, in-app footage only.** No simulated UI, no stock footage, no premium cut-down "trailer" content that doesn't appear in the shipping app.
- **No people on camera.** "Don't film people interacting with a device, such as an over-the-shoulder angle or fingers tapping the screen." Use digital tap indicators instead.
- **Show gameplay, not cutscenes.** Apple specifically calls out that cutscenes mislead users about what the app actually plays like. Cutscene-heavy previews routinely get rejected as "do not sufficiently reflect the app in use."
- **No marketing claims, no comparisons.** Don't say "#1 RPG," don't superimpose pricing ("only $4.99"), don't compare to other apps. Pricing varies by locale and ages the asset; superlatives get rejected for being unverifiable.
- **No seasonal or dated references.** "New for spring 2026" ages your video the day you launch.
- **Disclose IAP / subscription / login** if any of those appear. Tideward is a premium one-time purchase, so no disclosure copy is required from that angle. If that ever changes, the preview has to say so.
- **You own the music.** Stock royalty-free is fine if you have a license that covers "marketing use across all territories." Pulled-from-the-game music is fine. Random YouTube background tracks will get the video pulled.
- **Subtitles / on-screen captions are permitted.** Music is permitted. Voiceover is permitted but discouraged (see below).
- **Tap indicators required** wherever on-screen interaction matters to comprehension. Apple's language: "If you need to demonstrate how interaction or navigation works within your app, you may add graphic elements, such as touch hotspots."

The single hardest item to internalize: **the video plays muted by default in the App Store feed.** Anyone watching with sound is the exception. Treat the preview as a silent film. If your story falls apart with the audio dropped, you don't have a preview, you have a trailer.

---

## The 30-Second Structure

Industry-converged structure for a converting 30s preview, adapted to Tideward's voice:

### Three-act breakdown

| Beat | Time | What's on screen | What's at stake |
|---|---|---|---|
| **Act I — The Hook** | 0:00 - 0:04 | The brand promise in one image. Tideward's seal opens; the parchment unfurls; first sigil draws itself. Caption: *"An idle almanac."* | Average view time on App Store previews is 4-12 seconds. If the hook doesn't land in act I, the rest of the video is wasted bytes. |
| **Act II — The Loop** | 0:04 - 0:22 | The gameplay loop in four short vignettes: (1) character/class pick, (2) first combat exchange with damage numbers, (3) skill tree level-up with parchment animation, (4) almanac browse. Each vignette ~4-5s with a one-line caption. Tap indicators on every interaction. | This is the conversion engine. Show the loop, not a montage of features. A user must be able to answer "what do I do in this game?" by 0:18. |
| **Act III — The Sign-off** | 0:22 - 0:30 | Wide shot of the running game. Title card: **Tideward** with subtitle *An Idle Almanac*. Optional small icon. No price. No "download now" CTA — Apple says you can't add one, and the install button is already on the same screen. | Brand close. Reinforce the sigil and tone. Leave with the feeling you'd get from finishing a chapter, not a tutorial. |

Storyboard sketch (one frame per second is enough; an Apple Notes table works fine for v1.0):

```
0:00  Seal closed, parchment background
0:01  Seal cracks open, ink draw-on
0:02  First sigil materializes
0:03  Caption fade-in: "An idle almanac"
0:04  Hard cut → character selection list
0:05  Tap indicator → class selected
0:06-7  Class detail card with stats
0:08  Cut → combat scene, first attack
0:09-10  Damage number, enemy reaction
0:11  Tap indicator → skill button
0:12-13  Skill animates, enemy falls
0:14  Cut → skill tree level-up
0:15-17  Node unlocks, parchment animates
0:18  Cut → almanac page browsing
0:19-21  Pages turn, entries scroll
0:22  Slow zoom out to running game
0:23-25  Hold on world view
0:26-28  Title card draws: "Tideward"
0:29  Subtitle: "An Idle Almanac"
0:30  Cut to black
```

---

## Tideward-Specific Narrative

The preview is the one place where new users get to feel the somber-scholarly tone before they buy. Tone choices to bake in:

- **Open on the seal, not on combat.** Most idle-RPG previews open on a numerical damage spike or a flashy ability proc. Tideward's positioning is the opposite: this is a quiet, patient game. Lead with the parchment and the sigil. The hook should feel like opening a book, not like a casino floor.
- **Tap indicators in low-saturation oxblood**, not bright white or neon. Even the UI affordances are in-character.
- **Caption typography:** EB Garamond italic, ~32px line height, oxblood on parchment, lower-third aligned. Match the brand recipe documented in the Beehiiv design-scope memory.
- **No "+999 DMG" floaters or screen shake.** Show real combat numbers as they ship — small, two-digit, with brief sigil flashes.
- **No emoji captions.** No exclamation points. The voice rule that bans them in newsletter copy extends to preview captions verbatim.
- **The closing card should resemble a book's title plate**, not a logo splash. The audience read-through is: "this is a deliberate, illuminated thing, not a slot machine."

What NOT to include in v1.0:

- No social/friends features even if they ship in v1.1.
- No watch / widget cameos. Those are widget-suite assets, not preview frames.
- No multiplayer hint, no PvP framing, no "compete with friends" anything.
- No "AI-generated content" anywhere on screen, even incidentally.

---

## Production Pipeline

### Capture (pick one)

| Method | When to use | Quality | Watch-outs |
|---|---|---|---|
| **Xcode iOS Simulator + macOS screen capture** (`Cmd+Shift+5` → record at Physical Size `Cmd+1`) | Building polished UI shots where you control the entire scene | High, deterministic | Simulator drops some Metal effects; verify particle/glass visuals match device |
| **Real device → QuickTime "Movie Recording" → select iPhone as camera source** | Showing real combat / real frame pacing / Vision Pro reflections | Highest, real-device fidelity | iPhone must be on a USB-C/Lightning cable; pre-disable notifications, set Do Not Disturb, hide battery percent |
| **ScreenFlow 10 with iOS capture** | One-stop record + edit on a deadline | High; built-in iOS bridge | $129 one-time; less granular color grading than Resolve |

For Tideward v1.0, **real device + QuickTime** is the right primary. Simulator captures should only be used if a specific scene (e.g., a long skill-tree montage) is more controllable in the sim. Always record source at the **highest fidelity available** (60 fps if the device supports it) and conform down at export — never up.

Pre-capture device checklist:
- Battery ≥ 80%, charging cable disconnected during record if it shows on screen
- Status bar set with `xcrun simctl status_bar` (sim) or carrier-mode toggle (real device)
- Brightness max, True Tone off, Night Shift off
- Do Not Disturb on, all notifications hidden
- Time set to 9:41 (Apple's marketing convention) for consistency with screenshots

### Edit

**DaVinci Resolve Free** is the recommended editor for v1.0. Why over Final Cut:
- Free. FCP is $300.
- Subtitle workflow is first-class (TTML/SRT import + export, animated subtitles via AI Animated Subtitles in v20).
- Color page can match the parchment/oxblood grade to brand exactly.
- Resolve's Fairlight page handles the music ducking under UI SFX without leaving the app.

ScreenFlow is fine if Seth already owns it, but it's weak at color grading and the export presets don't match Apple's 886x1920 spec — you'd be doing a Resolve pass anyway.

### Export

- **H.264** (not ProRes — ProRes is overkill for App Store delivery)
- **886 x 1920 portrait** for iPhone 6.9" slot
- **30 fps** (conform from 60 fps source)
- **AAC 256 kbps stereo @ 48 kHz**
- Target bitrate **10-12 Mbps** (Apple's spec range)
- Container: **`.mp4`** for upload

Final check before upload: drop the master into QuickTime Player, hit `Cmd+I`, verify the resolution reads exactly 886 x 1920 and the duration is between 0:15.00 and 0:30.00 with no over-run. App Store Connect rejects 0:30.05.

---

## Music & SFX

**Use one continuous music bed** across the whole 30 seconds. Apple specifically recommends this for continuity. Cutting between tracks for each act fragments the asset.

Licensed library options (ranked for Tideward's tone):

| Library | Monthly | What you get | Fit for Tideward |
|---|---|---|---|
| **Epidemic Sound (Personal)** | ~$10 | 50k+ tracks, royalty-free for marketing use, stems available | Best — has a strong "early music" / "medieval" / "folk strings" catalog; license explicitly covers app store assets |
| **Artlist (Personal)** | ~$10 | Smaller library, broader broadcast license at higher tiers | Good fallback; less deep on early-music tones |
| **PremiumBeat (per-track)** | $49-199 one-time | One-shot license per track | Use if you find one perfect track and don't want a subscription |
| **Game's own soundtrack** | $0 marginal | What ships in the app | **Best if available.** Apple says: "you can include sound effects from your UI or gameplay in your footage." Pulling the game's own theme is the cleanest license story. |

Tone target: **harpsichord, lute, low strings, soft hand drum, no synth pads, no four-on-the-floor.** Aim for something a viewer would describe as "scholarly" or "monastic," not "epic" or "heroic." Tracks that sit at 60-80 BPM in a minor key, with a single melodic line, fit Tideward's voice better than full orchestral cues.

**Critical:** do NOT use any track without an explicit "marketing use in all territories" license. Apple will pull a video where a rights claim comes in post-publish, and the resolution path involves App Review tickets.

UI SFX: pull the actual page-turn and sigil-impact SFX from the game build. Layer them ~6 dB below the music bed. If you don't have them yet, ship music-only — silence on UI interaction reads as "stylized" rather than "broken" when paired with strong visuals.

---

## Captioning & Accessibility

**Default state of the asset is muted.** Captions are not optional for Tideward — they carry the entire narrative.

Caption discipline:
- **One short caption per act**, not a running narration. Three to five captions total across the 30s.
- **EB Garamond italic, oxblood, parchment background bar** behind the text for legibility on any frame.
- **WCAG 2.1 AA contrast** — minimum 4.5:1 contrast ratio against whatever's behind the text. The parchment bar guarantees this.
- **Burned-in, not closed captions.** App Store previews don't render external caption tracks. The text must be in the video itself.
- **Captions stay on screen ≥ 2 seconds** so a slow reader can land on them.

Accessibility extras that punch above their weight:
- VoiceOver users will hear nothing from the preview itself (it's an opaque video element to the screen reader). The Promotional Text and Subtitle copy on the product page do that job. Coordinate caption text with subtitle copy so a screen-reader user gets the same beats.
- Audio description tracks are not supported by App Store previews. Leave that gap for the YouTube cut of the trailer (a separate asset).
- Don't rely on color alone for any caption. The text says "An idle almanac" — it doesn't matter if the user can't perceive oxblood.

---

## Localization

App Store Connect lets you upload **a separate preview per locale.** Localizing the preview correlates with stronger conversion in non-English markets — users convert better when the video matches their language and cultural cues.

The pragmatic split for Tideward:

| Locale tier | Approach | Effort |
|---|---|---|
| **English (en-US)** | Master video, primary asset | Full production |
| **Phase 1 locales** (pull from existing localization roadmap — typically en-GB, de, fr, es, ja) | Reuse master video, replace burned-in captions with translated versions, reuse music bed | One render per locale, half a day total |
| **Phase 2 locales** | Use scaled English video until traffic justifies the per-locale render | Zero incremental |

Why this works:
- The music bed has no language. Reusable everywhere.
- The visual story is language-independent — no voiceover means nothing to re-record.
- The only per-locale asset is a fresh DaVinci render with the caption track swapped. Resolve makes this a 10-minute job per locale once the master timeline exists.
- **Don't translate the title card.** "Tideward" stays as the wordmark. Subtitle ("An Idle Almanac") can localize or stay English depending on brand call.

Voice-element warning: if a future version of the preview includes any spoken word — even a single sigh or chant in act III — every locale needs a re-record. Sidestep this by keeping vocals out of the music bed in v1.0.

---

## Device Frame

**Ship full-screen, no device frame.** Reasons:

- Apple's guidance discourages fake hardware frames that might be confused with marketing for a physical product. Real screen capture, no chrome.
- The App Store UI surrounds the preview with a thin device-shape mask automatically when it renders. Adding your own frame creates a frame-inside-a-frame moiré.
- A frame steals 15-20% of the screen real estate that should be showing gameplay. At 886x1920 every pixel of UI matters.
- Full-screen reads as "professional" to a viewer; framed reads as "screenshot of a video" to a viewer who's seen 1,000 framed previews this week.

Exception: the iPad version (when produced) may benefit from a subtle framing because the iPad slot reads more "promotional" than the iPhone slot. Decision deferred to v1.1.

---

## Asset Production Checklist

### Source / archive

- [ ] Master capture: real device, 60 fps, native device resolution, ProRes if possible
- [ ] Backup masters mirrored to R2 alongside the screenshot archive
- [ ] DaVinci Resolve project file checked into a private repo (not the public marketing repo)
- [ ] Music license PDF saved with project file

### Delivery (per upload)

- [ ] H.264, 886 x 1920, 30 fps, 10-12 Mbps, ≤30 s, ≤500 MB
- [ ] AAC 256 kbps stereo
- [ ] Burned-in captions, oxblood on parchment, EB Garamond italic
- [ ] Tap indicators present on every UI interaction shown
- [ ] No price, no comparative claim, no seasonal text, no real human in frame
- [ ] No simulated UI or unreleased feature shown
- [ ] Title card at end with wordmark
- [ ] One music track, no track changes, license documented
- [ ] Final QC: muted playback tells the full story

### Per-locale variants

- [ ] Translated caption track only; everything else reused
- [ ] Locale-appropriate title card if translation policy says so
- [ ] Filename convention: `tideward-preview-v1-{locale}-iphone69.mp4`

---

## A/B Testing Variants

App Store Connect's **Product Page Optimization (PPO)** lets you run up to three alternate product pages against the default, with up to three preview videos in any single test. Tests run 90 days or until you stop them, allocate a configurable traffic %, and report per-treatment install rate in App Analytics.

Test plan for Tideward post-launch:

| Variant | Hook | Loop emphasis | Sign-off | Hypothesis |
|---|---|---|---|---|
| **A — Brand-led** (default) | Seal opening, parchment, sigil | All four vignettes equally | Title card with "An Idle Almanac" | Premium aesthetic converts the right buyer; lower install volume, higher LTV |
| **B — Gameplay-led** | Hard cut into combat at 0:01 | Combat + skill tree dominant | Title card only | More casual buyers convert; install volume up, return rate uncertain |
| **C — Hybrid** | Parchment for 2s, then combat | Combat + almanac (skip skill tree) | Title card + sigil pulse | Splits the difference; useful as a tiebreaker |

Run A vs B first. If A wins on install rate AND retention, ship A everywhere and skip C. If B wins on install rate but loses on D1 retention, the audience mismatch story is confirmed and A stays as default with B reserved for paid acquisition pages. PPO discipline mirrors the screenshot-blueprint A/B framework — don't run more than one test at a time.

---

## Anti-Patterns

Common preview mistakes that get videos rejected, depressed, or quietly underperforming:

- **Voiceover narration of UI** ("Tap to attack! Watch your stamina!") — reads as a tutorial, breaks the muted-by-default consumption model, and locks the video to one locale. Apple permits it; the market punishes it.
- **Music drowning out UI SFX** — page-turn and combat hit sounds carry brand. If the music sits at -6 dB and the SFX at -12 dB, the SFX disappear; flip the relationship.
- **Showing UI that hasn't shipped** — feature creep into the preview is the #1 reason indie previews get rejected as "do not sufficiently reflect the app in use."
- **Cutscene-heavy opens** — Apple specifically calls this out as misleading. Treat the preview as a "gameplay reel," not a "story trailer."
- **Comparison claims** ("Better than Melvor!") — instant rejection.
- **Hardcoded prices** ("$4.99!") — instant rejection. Pricing varies by locale.
- **Seasonal copy** ("New for summer 2026!") — ages the asset.
- **Real human hands or over-the-shoulder shots** — explicitly banned.
- **Landscape orientation when the app is portrait-first** — frequent rejection driver.
- **One pixel off the spec** (e.g., 887 x 1920) — App Store Connect rejects the upload.
- **Music without a marketing-use license** — slow-burn copyright takedown post-publish.
- **Burning a "Download now!" CTA into the video** — the install button is already on screen; the CTA reads as desperate and offers nothing.
- **Splitting the music into two tracks** — Apple recommends one bed; cutting tracks per act fragments the asset.
- **Showing simulated achievements / fake notifications** — counts as simulated UI.
- **AI-generated background art in frame** — risks rejection under updated 2025 review guidelines around AI content disclosure.

---

## Tideward v1.0 Recommendation

### Concrete production plan

| Field | Value |
|---|---|
| Duration | 30.0 s exactly |
| Orientation | Portrait |
| Device slot | iPhone 6.9" (886 x 1920), let App Store Connect scale to 6.5"/6.3"/6.1" |
| Resolution / fps / codec | 886x1920 / 30 fps / H.264 |
| Audio | AAC stereo 256 kbps, one music bed + UI SFX |
| Captions | Burned-in, EB Garamond italic, oxblood on parchment, 4 caption beats total |
| Frame | None (full-screen) |
| Voiceover | None |
| Music source | Epidemic Sound Personal ($10/mo) OR pull from the game's shipping soundtrack |
| Tap indicators | Oxblood ripple, ~40px diameter, 0.4s fade |
| Title card | Wordmark "Tideward" + subtitle "An Idle Almanac" |
| Captured by | Real iPhone over USB to QuickTime |
| Edited in | DaVinci Resolve Free |
| Master archived to | R2 alongside screenshot masters |

### Storyboard (final)

```
0:00-0:03  Seal closed. Ink draw-on. Caption: "An idle almanac."
0:04-0:07  Character selection. Tap → class chosen. Caption: "Choose your hand."
0:08-0:13  Combat: attack, damage number, skill cast, enemy falls. No caption (visuals carry it).
0:14-0:17  Skill tree node unlocks. Parchment ribbon animates.
0:18-0:21  Almanac browse, pages turn. Caption: "Read the world."
0:22-0:25  Wide shot of the running game world.
0:26-0:29  Title card draws: "Tideward". Subtitle: "An Idle Almanac".
0:30        Cut to black.
```

### Budget options

| Option | Cost | Time | Recommendation |
|---|---|---|---|
| **Self-edit weekend** | ~$60 (one month Epidemic Sound or a single PremiumBeat track) + Seth's time | One weekend | **Recommended for v1.0.** Learning curve is real but the resulting asset is on-brand and re-editable in-house |
| **Fiverr editor** | $200-400 | 5-10 days, two revision rounds | Acceptable if Seth's time is more constrained. Pick an editor with a verifiable portfolio of app previews, not "video editor in general." |
| **Upwork specialist** | $600-1500 | 1-2 weeks | The right call if Tideward hits a v1.1 marketing budget and needs three test variants produced concurrently |
| **Boutique app-preview studio** (Apptamin, Yellowhead) | $3000-8000 | 3-4 weeks | Overkill at premium-indie scale; revisit if Apple features the app and ad spend becomes meaningful |

### Critical path

1. Capture session on real device, all four loop vignettes plus the seal-open hook.
2. License music track (or pull from shipping build).
3. Single Resolve cut. Caption pass. Color match to brand recipe. Export.
4. Upload English video to iPhone 6.9" slot in App Store Connect.
5. Defer iPad / Mac / TV / Vision Pro previews until v1.1 or until that platform's install volume justifies the cost.
6. After 30 days of live data, evaluate PPO test A vs B per the variants table.

---

## Sources

- [App preview specifications — App Store Connect Reference](https://developer.apple.com/help/app-store-connect/reference/app-preview-specifications/)
- [App Previews — Apple Developer](https://developer.apple.com/app-store/app-previews/)
- [Captions evaluation criteria — App Store Connect](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/captions-evaluation-criteria/)
- [Creating Your Product Page — Apple Developer](https://developer.apple.com/app-store/product-page/)
- [Product Page Optimization — Apple Developer](https://developer.apple.com/app-store/product-page-optimization/)
- [Get started with product page optimization — Tech Talks](https://developer.apple.com/videos/play/tech-talks/10888/)
- [Make the most of product page optimization — Tech Talks](https://developer.apple.com/videos/play/tech-talks/110349/)
- [The Complete Guide to Creating App Store Preview Videos in 2026 — SmoothCapture](https://www.smoothcapture.app/blog/app-store-preview-video-guide)
- [App Store Preview Video Requirements: What Apple Actually Wants in 2026 — DemoScope](https://demoscope.app/blog/posts/app-store-preview-video-requirements-apple-guidelines)
- [App Preview Video Sizes & Specs 2026 — Matte](https://matte.app/blog/app-store-preview-video-specs)
- [App Store Preview Dimensions 2026 — Screenshototter](https://screenshototter.com/blog/app-store-preview-dimensions)
- [How to Make App Store Preview Videos in 2026 — Matte](https://matte.app/blog/app-store-preview-video-tutorial-2026)
- [App Store Preview Video Sizes & Dimensions Spec Guide — ScreenKit](https://screenkit.tools/specs/app-store-app-preview-video-specs)
- [App Store Preview Videos: The 2026 Conversion Guide — AppScreenshotStudio](https://appscreenshotstudio.com/blog/app-store-preview-videos-the-2026-conversion-guide)
- [How to record and show screen taps gestures in App Previews videos — Whisper Arts](https://medium.com/whisperarts/how-to-record-and-show-screen-taps-gestures-in-app-previews-videos-for-ios-4f82d7b6fdc9)
- [The 11 Commandments of Incredible App Preview Videos — yellowHEAD](https://www.yellowhead.com/blog/11-commandments-app-preview-videos/)
- [App Store Preview: The Complete Guide to iOS App Store videos — Apptamin](https://www.apptamin.com/app-previews/guide-app-previews/)
- [How to Create the Best Mobile Game App Preview videos — Apptamin](https://www.apptamin.com/blog/mobile-game-app-preview-videos/)
- [An ASO Guide to App Store Preview Videos for iOS Apps — SplitMetrics](https://splitmetrics.com/blog/create-app-preview-video-app-store-ios/)
- [An ASO Guide to App Store Preview Videos — AppRadar](https://appradar.com/academy/preview-video)
- [App Store product page optimization: how to run A/B tests (2026) — MobileAction](https://www.mobileaction.co/blog/product-page-optimization/)
- [Apple App Store Rejection Reasons In 2025 — Twinr](https://twinr.dev/blogs/apple-app-store-rejection-reasons-2025/)
- [App Review Guidelines — Apple Developer](https://developer.apple.com/app-store/review/guidelines/)
- [Final Cut Pro vs ScreenFlow — Software Advice](https://www.softwareadvice.com/video-making/final-cut-pro-profile/vs/screenflow/)
- [DaVinci Resolve — Edit — Blackmagic Design](https://www.blackmagicdesign.com/products/davinciresolve/edit)
- [DaVinci Resolve — Color — Blackmagic Design](https://www.blackmagicdesign.com/products/davinciresolve/color)
- [Epidemic Sound Pricing & Licensing](https://www.epidemicsound.com/pricing/)
- [Artlist vs. Epidemic Sound — Epidemic Sound Blog](https://www.epidemicsound.com/blog/artlist-vs-epidemic-sound/)
- [App Store Conversion Rate by Category in 2026 — Adapty](https://adapty.io/blog/app-store-conversion-rate/)
- [App Store Conversion Rate Benchmarks (2026) — Kirro](https://kirro.io/app-store-conversion-rate)
- [How to Record Xcode & iOS Simulator — Screenify](https://www.screenify.studio/blog/2026-04-19-record-xcode-simulator)
