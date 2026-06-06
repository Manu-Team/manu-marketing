# Video Press Kit Production for Tideward
> Filed: 2026-06-01. Tier: WARM (launch deliverable).

## TL;DR

A complete indie video press kit is roughly **30 deliverables** spread across seven asset types: the App Store preview (already covered in [`app-preview-video-production.md`](app-preview-video-production.md)), a 60-90s public launch trailer, 3-5 short gameplay clips (mixed 16:9 and 9:16), 8-10 looping GIFs sized for Reddit/X/Discord, 5-10 minutes of plain unmarked B-roll for journalists and YouTubers to re-edit, an optional founder-narrated dev journal, and per-creator personalized intro stubs for top-priority partners. Capture all gameplay clean from a real device at 60fps, edit in DaVinci Resolve Free (cross-platform) or Final Cut Pro X (Mac speed), license music from Epidemic Sound or Artlist with Safelist/Clearlist whitelisting, burn captions on every social clip because >80% of views happen muted, and host everything behind `assets.tideward.app` (Cloudflare R2 via the strategy in [`asset-cdn-strategy-versioning.md`](asset-cdn-strategy-versioning.md)). Budget: 60-80 hours over a two-month window beginning T-2 months from launch.

## The Video Asset Inventory

A launch-grade press kit needs all seven of these. Skipping any of them limits a downstream use case.

1. **App Store preview** - already scoped in [`app-preview-video-production.md`](app-preview-video-production.md). 15-30s, per-device. Not covered again here.
2. **Launch trailer** - the 60-90s public reveal video. Embedded on the trailer YouTube watch page, the tideward.app homepage, the press kit landing page, the Steam-equivalent presence (if any), and shared the day of launch across every social channel. This is the single hero piece.
3. **Gameplay clips** - 3-5 short clips, 15-30s each, half 16:9 and half 9:16. Used in X/Bluesky posts, Reels/TikTok/Shorts, Discord drops, paid social (if used per [`x-algorithm-source-tour.md`](../../../the-assembly-line/RESEARCH/x-algorithm-source-tour.md) note that paid is deferred until alpha conversion improves).
4. **GIFs** - 8-10 looping 10-15s GIFs sized under 8MB so they actually render inline on Reddit and X. The dominant medium for r/incremental_games and r/iosgaming product showcases.
5. **B-roll** - 5-10 minutes of silent, UI-light, plain gameplay footage that journalists and YouTubers can cut into their own videos. Provided unlabeled and unbranded. This is the most-overlooked asset and the one that actually unlocks PC Gamer / Pocket Tactics / Pocket Gamer style coverage when they pick the game up post-launch.
6. **Dev journal video** (optional but high-loyalty) - a 5-10 minute founder-narrated piece walking through one mechanic, one design decision, or one milestone. Devlogs cultivate a more loyal subscriber-per-view ratio than typical YouTube content, and they double as the founder's content channel between major releases.
7. **Per-creator thumbnails + intro stubs** - for top-tier YouTube/TikTok partnerships (Olexa, AdvanceQuest, smaller idle-game creators), a custom 1280x720 thumbnail with their name baked in and a 10-15s personalized intro clip ("Hey Olexa, thanks for checking out Tideward"). Low-cost, high-conversion personal touch.

Total: roughly 30 deliverables when you count one trailer + 5 clips + 10 GIFs + 6 B-roll segments + 1 dev journal + ~7 creator thumbnails.

## Specs Per Asset Type

All specs below assume the source capture is 1920x1080 at 60fps from a real device (per [`app-preview-video-production.md`](app-preview-video-production.md) device-capture rules - the App Store rejects Simulator capture and the same standard applies here for quality reasons).

**Launch trailer**
- Container: MP4 (H.264, High Profile)
- Resolution: 1920x1080
- Aspect: 16:9
- Duration: 60-90s (90s is the upper bound at which most platforms still autoplay-in-feed; longer risks getting muted to a thumbnail)
- Bitrate: 8-12 Mbps video, 320 kbps AAC audio
- Frame rate: 30fps for the export (60fps source down-mixed to 30 reads cinematically better than native 60 for narrative trailers)
- SRT subtitle sidecar in English at minimum; reserve filenames `tideward-launch-trailer-en.srt`, `-de.srt`, `-ja.srt`, `-zh-Hans.srt`, `-es.srt` for the five most-likely featuring locales

**Gameplay clips (horizontal)**
- 1920x1080, MP4 H.264, 15-30s, 30fps, 8-10 Mbps
- Burned-in captions (white text, black 2px outline) per the muted-autoplay rule below
- Filename convention: `tideward-clip-<topic>-16x9.mp4`

**Gameplay clips (vertical)**
- 1080x1920, MP4 H.264, 15-30s, 30fps, 6-8 Mbps
- Same caption rules
- Filename: `tideward-clip-<topic>-9x16.mp4`

**GIFs**
- Horizontal: 800x450 (16:9 at half resolution; full 1280x720 blows the 8MB Reddit budget)
- Vertical: 480x800 (Discord-friendly)
- 10-15s loop, 15fps (dropping from 30 to 15 is the single biggest size win; the visual hit on idle/menu-driven gameplay is negligible)
- Target file size: under 8MB so Reddit and X render them inline (X's hard cap is 15MB but feed performance degrades above ~10MB)
- Encoder: gifski for the actual encoding (cross-frame palettes, temporal dithering, far better than ffmpeg's palettegen for 256-color UIs), with ffmpeg used only to demux frames or `-f yuv4mpegpipe` directly into gifski

**B-roll**
- 1920x1080, MP4 H.264, 60fps preserved (editors will reframe/slo-mo and the extra frames matter), 20+ Mbps
- 30-120s clip lengths, ideally several takes of each scene type
- No music. No UI overlay text. No watermark. Plain gameplay so a video producer can drop their own voiceover and chyrons.

**Dev journal**
- 1920x1080, MP4 H.264, 30fps, 8-10 Mbps, 5-10 minutes
- Founder face cam optional (lower-third title card works just as well for a Seth-as-narrator format)

**Thumbnails**
- 1280x720 PNG (YouTube standard), 16:9
- Under 2MB to stay inside YouTube's custom-thumbnail size cap

## B-Roll Strategy

The unedited B-roll bundle is what unlocks press coverage that involves video. Pocket Tactics, PC Gamer, Eurogamer, TouchArcade, and 90% of YouTube creators will re-edit your footage, not the trailer. The bundle should provide at minimum:

- **60s overworld traversal** - walking the map, atmosphere, UI hidden where possible
- **60s combat** - several encounters across different skill levels
- **60s skill progression** - the moment of leveling up, the visual feedback loop
- **60s inventory/bank** - menu navigation, item interactions
- **60s late-game depth tease** - one piece of high-tier content that signals "this game has legs"
- **30-60s ambient menu screens** - main menu, settings, the somber-scholarly visual identity holding still

Label each clip by content (`broll-combat-01.mp4`, `broll-overworld-tundra.mp4`) so a tired editor can find the shot they need in 10 seconds. Disobey and presskit.gg both flag this labeling step as the difference between a B-roll bundle that gets used and one that doesn't.

## Trailer Music Strategy

The trailer's sonic identity must match the brand. Tideward reads somber-scholarly per [`Sound_Design_Framework.md`](../../../tideward-app/ManuResearch/Sound_Design_Framework.md) - parchment textures, a slow musical pulse, no synth-orchestral bombast.

**Library choice:**
- Epidemic Sound ($19/mo Creator or $49/mo Commercial) - 55,000+ tracks, all rights owned in-house, stems on every track, Safelist whitelisting that survives subscription cancellation
- Artlist ($14.99/mo+) - broader licensing flexibility for broadcast use, Clearlist whitelisting
- Both work for indie game trailers and YouTube monetization without ContentID strikes

**Budget:** the trailer itself needs one hero track plus 1-2 transition stings. Either platform's monthly plan covers it; license a single Epidemic track if you don't want a subscription.

**The trap to avoid:** YouTube Audio Library tracks. They're free but every other indie trailer uses them, and the cinematic-strings standards are recognizable enough that they actively dilute the brand. Pay the $19 instead.

## Captioning & Subtitles

Over 80% of social video views happen muted. 80% of viewers react negatively when sound autoplays. Captions are not optional.

**Rules:**
- **Burn captions into every social clip** (gameplay clips and GIFs). The viewer should never see your video without text on screen. Use white text with a 2px black outline - this stands out on every background tested.
- **SRT sidecar files for the launch trailer.** YouTube/Vimeo will use them; Apple Editorial may request multi-language versions if you get featuring consideration. Ship English first; reserve filenames for de, ja, zh-Hans, es per the launch-trailer spec above.
- **Two lines max per caption.** Keep each visible for 1.5-3s.
- **Mobile safe zone.** Keep captions within the central 80% of the frame so platform UI (X's like/repost buttons, TikTok's right-rail icons, YouTube Shorts' overlays) doesn't cover them.
- **Editor tooling.** CapCut and Descript both auto-caption with high accuracy; manual cleanup takes about 10 minutes per minute of video. VEED is fastest for one-off social clips.

## Production Workflow

**Phase 1 (T-2 months): Capture.**
Record 4-6 hours of clean gameplay on a real device per [`app-preview-video-production.md`](app-preview-video-production.md). One iPhone 17 Pro Max session, one iPad Pro session, one Mac session. Don't try to capture and edit in the same week - capture is its own skill and rushing it produces footage you'll re-shoot.

**Phase 2 (T-6 weeks): Launch trailer V1.**
Edit the 90s hero piece first. This is the asset everything else feeds. Music license, captions, color, three review rounds. Budget 25-30 hours.

**Phase 3 (T-4 weeks): Social cuts + GIFs.**
The trailer footage gets recut into 3-5 horizontal gameplay clips, 3-5 vertical clips, and 8-10 GIFs. Roughly 15-20 hours because you're reusing color-graded source.

**Phase 4 (T-2 weeks): Dev journal (optional).**
5-10 minute founder-narrated piece. Script first, then capture face-cam B-roll, then edit. Skip this if launch is tight - it's the lowest-cost-to-defer of any asset on the list.

**Phase 5 (T-1 week): Per-creator thumbnails + intro stubs.**
For the 5-10 top creators on your outreach list, ship custom 1280x720 thumbnails and 10-15s personalized intro clips. Roughly 1 hour per creator.

**Phase 6 (T+0): Distribution.**
Press kit page goes live with every asset. Outreach emails to journalists ship with direct links (not Dropbox folders - links to specific files keyed off `assets.tideward.app`).

Total: 60-80 hours over the eight-week window. DIY-able solo if comfortable in Resolve or FCPX; budget $1500-3500 for a contract editor if not.

## Tooling Stack

**Capture:**
- QuickTime screen recording from a tethered iPhone/iPad (clean, no system overlays)
- macOS native screen recording for Mac gameplay
- Real-device capture for Vision Pro (Simulator does not show the visual fidelity reviewers expect)
- The Tideward UITest rig (see [`reference_tideward_uitest_signing_gotcha.md`](../../../tideward-app/ManuResearch/) - careful, never pass `CODE_SIGNING_ALLOWED=NO`) can drive deterministic scripted runs if you want repeatable captures of the same scene

**Edit:**
- DaVinci Resolve Free (Mac/Win/Linux) - industry-grade color, free tier covers everything a 90s trailer needs, cross-platform if you outsource
- Final Cut Pro X ($299 lifetime) - faster on Mac, better for solo-creator speed, smoother proxy workflow with Apple silicon

**GIF generation:**
- ffmpeg (demux frames or pipe via `-f yuv4mpegpipe`)
- gifski (the actual encoder - far better than ffmpeg's palettegen for the kinds of flat-color UIs Tideward shows)
- gifsicle (optional post-optimization, mostly for crunching the last 10-20% of file size)

**Music:**
- Epidemic Sound or Artlist Pro (subscription) or single-track Epidemic licenses

**Captions:**
- CapCut (free, fast auto-captioning)
- Descript (paid, but transcript-driven editing is faster for the dev journal video)
- Aegisub for hand-crafted SRT files when the launch trailer needs multi-language subtitle precision

## Apple Editorial Submission

Apple's featuring nomination flow in App Store Connect accepts up to 5 supplemental URLs. These can include promo videos, artwork, press kits, and TestFlight links. If your app is selected for consideration, Apple's editorial team emails Admin/App Manager/Marketing role members with a request for promotional assets.

**What to ship:**
- The 15-30s App Store preview (already submitted as the in-listing video)
- The 60-90s launch trailer (as a supplemental URL)
- A 60s atmospheric piece highlighting visual identity (a B-roll cut, music-only, no captions)

**Timing:** Apple recommends giving the editorial team minimum two weeks notice. For wider featuring consideration, submit a nomination up to three months in advance. For Tideward's launch on the calendar discussed in [`awards-eligibility-2026-2027.md`](awards-eligibility-2026-2027.md), that means the nomination must be ready when the press kit ships - same week.

**Cross-reference:** the positioning context in [`Premium_Idle_App_Store_Positioning.md`](../../../tideward-app/ManuResearch/Premium_Idle_App_Store_Positioning.md) governs how the trailer frames the game ("premium idle almanac" not "best mobile RPG").

## Hosting

All assets live behind Cloudflare R2 with the custom-domain scheme established in [`asset-cdn-strategy-versioning.md`](asset-cdn-strategy-versioning.md):

- `assets.tideward.app/video/launch-trailer-v1.mp4`
- `assets.tideward.app/video/clip-combat-16x9.mp4`
- `assets.tideward.app/video/gif/overworld-loop.gif`
- `assets.tideward.app/video/broll/combat-01.mp4`
- `assets.tideward.app/video/devjournal/01-design-decisions.mp4`
- `assets.tideward.app/video/thumb/olexa-1280x720.png`

The press kit landing page on `tideward.app/press` links directly to each file. Don't ship a single ZIP - journalists hate downloading 800MB when they want the one B-roll cut.

R2 charges zero egress so even heavy press-kit traffic is free.

## Per-Creator Customization

For the top 5-10 creators on the outreach list (Olexa, Aldarocks, AdvanceQuest, the few idle-game-focused channels worth seeding):

1. Custom thumbnail: 1280x720 with the creator's name and channel-branded color accent. Their viewers recognize the styling instantly.
2. 10-15s personalized intro clip: "Hey [name], thanks for checking out Tideward. Here's a special early build for you." Drops into the front of their video.
3. Direct R2 link in the outreach email, not an attachment.

This pattern adds ~1 hour per creator and converts partnership response rates measurably. Multiple devlog success-story writeups call out personalization as the difference between a 5% and a 25% creator-response rate.

## Anti-Patterns

- **Trailer text-on-screen claims** like "Best idle RPG of 2027." Apple Editorial rejects featuring nominations that make superlative claims they can't verify. Show, don't claim.
- **Music with ContentID issues.** YouTube Audio Library is overused and recognizable. Royalty-free aggregator sites (no Safelist mechanism) get you struck post-launch.
- **B-roll with UI watermarks, debug overlays, or build numbers.** Editors won't use it. Capture clean.
- **GIFs over 8MB.** Reddit hides them behind a click-through. X downsamples to a still image. The whole point is in-feed autoplay.
- **Vertical-only social clips when a creator's channel is horizontal.** Match the platform.
- **Simulator capture.** The App Store rejects it for the preview video, and even outside App Store rules the fidelity gap is obvious to viewers.
- **One mega-ZIP press kit.** Journalists want direct links to specific files.
- **Burned captions on the SRT-version trailer.** Subtitle them, don't burn them - some embeds want native subs.
- **Re-encoding source footage multiple times.** Every re-export degrades quality; edit from the original ProRes/H.264 master and export once.
- **Trailer over 90s.** Past 90s the autoplay window closes and view-through rates collapse. The launch trailer is not the cinematic teaser.

## Tideward Action List

1. **T-2 months:** Schedule three capture sessions (iPhone 17 Pro Max, iPad Pro M-series, Mac). 4-6 hours each. Use Tideward UITest rig for deterministic runs.
2. **T-2 months:** Decide DIY-vs-contract edit. If contracting, brief now and contract by T-7 weeks.
3. **T-6 weeks:** Trailer V1 cut, with placeholder music. Review with Seth + at least one outside eye.
4. **T-5 weeks:** Music license selected and Safelist/Clearlist whitelisting confirmed.
5. **T-4 weeks:** Social clips + GIFs produced. Captions burned.
6. **T-3 weeks:** B-roll bundle organized, labeled, uploaded to R2 under `assets.tideward.app/video/broll/`.
7. **T-2 weeks:** Dev journal video drafted (skip if schedule tight).
8. **T-1 week:** Per-creator thumbnails + intro stubs delivered to outreach list. Press kit page goes live, links audited end-to-end.
9. **T+0:** Launch trailer goes public on YouTube + tideward.app + social. Press kit email blasts to journalist list (per the press-kit-industry-standards research at [`press-kit-industry-standards.md`](press-kit-industry-standards.md)).
10. **T+2 weeks:** Submit Apple Editorial featuring nomination if not done at launch, attaching trailer + atmospheric B-roll as supplemental URLs.

## Sources

- [The Complete Guide to Indie Game Press Kits 2026 (presskit.gg)](https://presskit.gg/blog/indie-game-press-kit-guide)
- [How to Make a Video Game Press Kit (Disobey)](https://www.disobey.gg/blog/how-to-make-a-video-game-press-kit-the-ultimate-guide-for-indie-devs)
- [Press Kit Guide for Indie Games (Indieformer)](https://indieformer.com/press-kit-guide/)
- [What needs to be in your Press Kit? (Pirate PR)](https://piratepr.com/treasure-trove/what-needs-to-be-in-your-press-kit/)
- [How to Build an Effective Game Press Kit (GameTrowel)](https://gametrowel.com/blog/how-to-build-an-effective-press-kit-for-your-indie-game-with-a-copy-paste-checklist)
- [How to Make Game Trailers For Influencers and Content Creators (Derek Lieu Creative)](https://www.derek-lieu.com/blog/2023/2/4/how-to-make-game-trailers-for-influencers-and-content-creators)
- [Kert Gartner - Game Trailer Editor](http://www.kertgartner.com/)
- [Used YouTubers to make the trailer of my indie game (Game Developer)](https://www.gamedeveloper.com/business/i-used-youtubers-to-make-the-trailer-of-my-indie-game-here-s-how-it-went-)
- [Twitter (X) GIF Size Limit: Desktop, Mobile, and Best Specs (curl-x)](https://www.curl-x.com/blog/twitter-gif-size-limit)
- [Best GIF Sizes for Social Media in 2025 (FastMakerGIF)](https://fastmakergif.com/blog/best-gif-sizes-social-media)
- [Social Media Guideline for Indie Game Developers (Toge Productions / Medium)](https://medium.com/toge-productions/social-media-guideline-made-with-love-for-indie-game-developers-6f57683312c3)
- [Social Media Video Aspect Ratios and Sizes - The 2026 Guide (Kapwing)](https://www.kapwing.com/resources/social-media-video-aspect-ratios-and-sizes-the-2025-guide/)
- [Social Media Video Specs: Dimensions, Ratios and File Sizes (Sendible)](https://www.sendible.com/insights/social-media-video-specs)
- [Sprout Social up-to-date guide to social media video specs](https://sproutsocial.com/insights/social-media-video-specs-guide/)
- [DaVinci Resolve vs Final Cut Pro Complete Guide (Miracamp)](https://www.miracamp.com/learn/davinci-resolve/vs-final-cut-pro)
- [DaVinci Resolve vs Final Cut Pro 2026 (Capterra)](https://www.capterra.com/compare/209733-233399/DaVinci-Resolve-vs-Final-Cut-Pro)
- [High quality GIF with FFmpeg (ubitux/blog)](https://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html)
- [gifski - ImageOptim GIF encoder (GitHub)](https://github.com/ImageOptim/gifski/)
- [How To Make and Optimize GIFs on the Command Line (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-make-and-optimize-gifs-on-the-command-line)
- [Music licensing for games (Epidemic Sound)](https://www.epidemicsound.com/blog/music-licensing-for-video-games/)
- [Artlist vs Epidemic Sound - 5 Things You Need To Know (Red11 Media)](https://www.red11media.com/blog/artlist-vs-epidemic-sound)
- [Royalty-Free Music for Creators - 2025 Guide (Paste)](https://www.pastemagazine.com/tech/epidemic-sound/royalty-free-music-for-creators)
- [Why Subtitles and Captions Matter More Than Ever in Social Ads (LeadEnforce)](https://leadenforce.com/blog/why-subtitles-and-captions-matter-more-than-ever-in-social-ads)
- [What Are the Benefits of Burn-In Captions? (Rev)](https://www.rev.com/blog/benefits-of-burn-in-captions)
- [Social Media Subtitle Best Practices (SubtitlesFast)](https://subtitlesfast.com/blog/social-media-subtitle-best-practices/)
- [Nominate your app for featuring (Apple Developer)](https://developer.apple.com/help/app-store-connect/manage-featuring-nominations/nominate-your-app-for-featuring/)
- [Getting featured on the App Store (Apple Developer)](https://developer.apple.com/app-store/getting-featured/)
- [Nominations template (Apple Developer)](https://developer.apple.com/help/app-store-connect/reference/nominations/nominations-template/)
- [How to Get Featured on the Apple App Store (Radaso)](https://radaso.com/blog/apple-app-store-featuring-how-to-get-into-the-recommended-apps)
- [Dev Logs give a window into game development (NPR)](https://www.npr.org/2025/06/03/nx-s1-5422235/dev-logs-give-a-window-into-the-fun-and-messy-world-of-game-development)
- [YouTube for Indie Games: A Devlog Success Story (Freaking Cool Indies)](https://freakingcoolindies.com/1-2/)
