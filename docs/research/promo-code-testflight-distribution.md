# Promo Code + TestFlight Distribution for Tideward
> Filed: 2026-06-01. Tier: WARM (launch operational).

## TL;DR

Apple gives a paid app **100 promo codes per version per platform** (regenerates each new version, expires 4 weeks after generation, single-use). IAP codes are a separate pool: **100 per IAP, capped at 1,000 per app per six-month window** (Jan 1 / Jul 1 reset). TestFlight is the parallel rail: **up to 10,000 external testers** via public link or named-email invite, builds expire 90 days. The premium-iOS-launch posture for Tideward should treat **promo codes as a trust gift to people who will publish about the game** (press, named creators, newsletter winners) and **TestFlight as the press/creator pre-launch channel** because TestFlight has no 4-week expiry trap and gets reviewers into the build earlier. Don't post codes publicly — they get bot-scraped to r/AppCodes within hours. Pair every code/invite with a Custom Product Page URL and a `tideward.app/go/<channel>` redirect so attribution survives Apple's analytics blackout. Plan one allocation per app version, not per quarter.

## What's Available

**Paid app promo codes.** Apple App Store Connect grants **100 promo codes per app version, per platform** the app supports. (Apple's docs use "per version per platform" — not "per quarter." The common shorthand "100 per quarter" only matches if you ship roughly one version per quarter.) Tideward ships on six platforms (iOS, iPadOS, macOS, tvOS, visionOS, watchOS) but they're one app — the 100 per version limit applies to the app as a unit, not per Apple platform, with the caveat that tvOS/visionOS/watchOS code redemption is routed through an iOS device. ([Apple Developer: Request and manage promo codes](https://developer.apple.com/help/app-store-connect/offer-promo-codes/request-and-manage-promo-codes/))

**In-App Purchase promo codes (legacy).** Apple announced retirement of IAP promo codes on **March 26, 2026**, pushing developers to Offer Codes instead. If Tideward stays a one-time paid app with no IAPs, this doesn't matter. If that ever changes and something is sold as IAP, switch to Offer Codes from day one. ([Adapty: Apple Subscription Offers Guide 2026](https://adapty.io/blog/apple-subscription-offers-guide/))

**Offer Codes.** Successor to IAP promo codes. **1 million codes per app per quarter**, up to 10 active offers at a time, batch min 500 / max 25,000, expiration up to 6 months. Higher leverage than promo codes, but requires IAP/subscription products. Tideward (premium paid app, no IAP planned) doesn't currently need these. ([Appbot: Apple Offer Codes](https://appbot.co/blog/apple-offer-code/))

**TestFlight invites.** Unlimited public link invites (capped at 10k testers), unlimited named-email external invites (also pulled from the 10k pool), up to 100 internal testers (App Store Connect users — no Beta App Review). Builds expire **90 days** after upload. ([Apple Developer: Invite external testers](https://developer.apple.com/help/app-store-connect/test-a-beta-version/invite-external-testers/))

## TestFlight Invite Models

**A. Public link.** A shareable URL anyone can use to join. Cap can be set below 10k; can be disabled anytime. Use case: open beta during alpha graduation, lower-friction press/creator handout (paste in DM, no email collection). Risk: anyone can join, so build quality matters from invite-1. Per Tideward's alpha-gate policy, public link stays small until alpha conversion improves.

**B. Email invite (external).** Apple sends a per-tester email with redeem code. Targeted, named, polite. Use case: every press contact, every named creator. Pull from the same 10k external pool. Apple's email-invite flow remains the right channel for high-touch outreach.

**C. Internal testing.** Up to 100 App Store Connect users tied to the team. No Beta App Review delay — builds available immediately after Apple processing. Use case: pre-press builds for internal QA, agency partners, Seth's trusted-tester ring.

## Promo Code Models

**Pre-launch unlock.** Gift to early supporters / wishlisters / newsletter foundation list. Use case: the people who DM'd asking when it ships. **Press review codes.** Substitute for a paid review copy — the indie norm for paid iOS games is to send promo codes to reviewers because they otherwise won't buy. **Creator codes.** Streamer/YouTuber free copies. **Influencer codes.** Specific personalities outside the gaming press loop (newsletter-to-newsletter cross-promo, niche-podcast hosts). **Reserve codes.** Held for unplanned contests, conference handouts, Reddit AMA flair, surprise opportunities.

## Per-Version Allocation (100 codes)

| Bucket | Codes | Notes |
|---|---|---|
| Press: Tier A (5 outlets) | 10 | TouchArcade, AppAdvice, MacStories, etc. — 2 each (primary + backup) |
| Press: Tier B (6 outlets) | 10 | Smaller indie/Apple press — 1-2 each |
| Tier A creators (5 named) | 15 | Olexa, DangerouslyFunny, Spiffing Brit, Aliensrock, Retromation — 3 each (DM-ready, backup, redistribute-to-friend) |
| Tier B creators (6) | 18 | Mid-tier idle/cozy creators — 3 each |
| Tier C creators (scraped from outreach playbook tier-3) | 10 | 1 each, narrowcast |
| Newsletter giveaway | 10 | Run as "first 10 replies to issue" or similar |
| Conference / IRL giveaway | 10 | If any 2026 conference cycle hits |
| Reserve (unplanned) | 17 | Always keep margin |

This frames the 100 as a per-version budget. Tideward isn't shipping one version per quarter — but each shipped version on the App Store mints a fresh 100. Plan the allocation when you cut the version, not against the calendar.

## Distribution Channels

**Email (1:1).** Press, named creators, newsletter winners. Code lives in the body of a personalized note alongside the press kit URL and CPP link. **DM (relationships).** Creators who've engaged in DMs already. Pre-built rapport reduces the spam-flag risk. **Newsletter exclusive.** "Reply with the word 'tideward' to claim a code" — gates the giveaway to engaged subscribers and avoids public exposure. **Reddit comments — CAREFUL.** r/iOSGaming and adjacent subs flag code-drop bait. Per Reddit playbook (see [`reference_reddit_incremental_games`](../../../memory/reference_reddit_incremental_games.md) in the umbrella memory), follow earned credibility first; code drops can trail a successful organic post but never lead one. **Conference handout.** Physical card / sticker with code printed; small risk because each code is single-use. **Direct mail.** Rare, but for high-leverage relationships (e.g., a writer at a publication you've courted for 18 months), a printed code in a card has a wildly disproportionate response rate.

## Code Generation Workflow

App Store Connect → Apps → [Tideward] → Promo Codes section → enter quantity (up to 100 for the current version) → accept distribution-contract terms → Generate Code → download via History tab. Permissions: Account Holder, Admin, App Manager, or Marketing role. ([Apple Developer: Request and manage promo codes](https://developer.apple.com/help/app-store-connect/offer-promo-codes/request-and-manage-promo-codes/))

**Critical: codes expire 4 weeks after generation, not after distribution.** If you generate 100 codes on Day 0 and start pitching press on Day 21, reviewers have 7 days to redeem before the code is dead. The rule of thumb: **generate codes within 4 weeks of when you'll actually hand them out.** For Tideward's launch, that means generating press codes the week press outreach begins, not at the start of the campaign.

Codes are tied to the **current version** at time of generation. New versions regenerate the 100-code pool, but undistributed codes from a prior version stay valid against that prior listing — usually fine, occasionally awkward if the new version adds capabilities the redeemer wants.

## Tracking Without Analytics

The hard truth surfaced in the source research: **App Store Connect provides no revenue attribution per CPP.** It can show CPP-driven downloads, but not downstream paid conversion, retention, or LTV. Analytics opt-in is also low, so even download counts undercount. ([Stop Using Custom Product Pages to Track UGC Creators — Cameron 2026](https://medium.com/@oliver.cameron0/stop-using-custom-product-pages-to-track-your-ugc-creators-6ef7a65ec54f))

Zero-SDK attribution stack (per [the-assembly-line/RESEARCH/x-funnel-math.md](../../../the-assembly-line/RESEARCH/x-funnel-math.md) and [creator-outreach-playbook.md](../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md)):

1. **CPP per channel.** Apple lifted the cap from 35 to 70 per app in late 2025 — plenty of headroom for one-CPP-per-Tier-A-creator + one-CPP-per-press-outlet. Each CPP has a unique URL.
2. **Redirect on tideward.app.** `tideward.app/go/<creator-slug>` resolves to the creator's CPP, logged in Cloudflare Web Analytics. Click counts at the redirect layer give an upper bound on attention that survives the App Store analytics blackout.
3. **Promo code ↔ channel map.** Maintain a spreadsheet (codes column, channel column, distribution date column, observed-redemption date column). When a redeem appears in Sales & Trends, cross-reference. This is the only attribution that actually closes the loop on promo-code distribution, because **promo codes don't carry CPP attribution automatically** — a redeemer can come from anywhere.
4. **Offer Codes (if Tideward ever adopts IAP).** Offer Codes can be batched per channel and *do* carry attribution. The trade-off is they require IAP/subscription products.

Bottom line: pair every code with a redirect and a CPP, log the trio in a spreadsheet, and accept that the final attribution number is a best-guess range, not a number.

## TestFlight Allocation

**Internal: up to 100.** Use the full budget. Seth + trusted-tester ring + agency QA + a handful of seasoned indie devs for cross-feedback. Internal testers see builds with no Beta App Review delay.

**External public link: keep capped at 5k for now.** The default 10k cap is too permissive while alpha conversion is still proving out. The cap is editable anytime — bump up as build quality stabilizes.

**Per-platform:** each Apple platform has its own TestFlight roster, but the 10k external pool is shared across them. Tideward's six-platform reality means watching invite distribution across iOS/iPadOS/macOS — visionOS, tvOS, watchOS have small tester populations.

## Press TestFlight Workflow

1. Add press emails to External Testers in App Store Connect (or send the public link if the relationship is informal).
2. Apple sends the invite email with a redeem code.
3. Reviewer installs the TestFlight app (if they don't have it), redeems, downloads the beta.
4. Build remains available **until the 90-day per-build expiration** — far longer than the 4-week promo code window. This is the primary argument for TestFlight over promo codes for press: reviewers have a wider window to actually open the thing.
5. Push new builds during the review cycle; testers auto-receive prompts. ([Apple Developer: TestFlight overview](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/))

## Creator TestFlight Workflow

Same flow as press. Two creator-specific wrinkles: (1) creators often *prefer* a TestFlight build over a launch-day App Store copy because it lets them record a "first look" video that publishes ahead of the launch wave — a strategic content advantage they value. (2) Manage expectations clearly: TestFlight is BETA, the build can have rough edges, the creator should not frame any review as definitive. The press-kit cover note should state this explicitly.

## Fraud Prevention

**The leak vector.** Single distributed code, single redemption. Codes appear on r/AppCodes-style aggregators within hours of being posted publicly. If a code is posted on Reddit/X/Discord, it's gone — first redeemer wins.

**Track which code went to which channel.** Spreadsheet column for code-to-recipient mapping. If a code surfaces on r/AppCodes or similar, you can identify the leak source (usually a Tier B/C contact who didn't realize codes shouldn't be shared). One leak per cycle is normal; three from the same source means stop sending to that source.

**Never bulk-post codes.** No "we have 50 codes, first come first serve" tweets. The bot scrapers parse those threads within minutes. If running a public giveaway, gate by reply/email collection so each code goes to a specific recipient, not a public list.

**Terms-and-conditions framing.** Include a sentence in the distribution email: "This code is for your personal review. Please don't share publicly." Sets the expectation, gives you cover if it's redistributed.

## Expiration Management

**4-week window** for paid-app promo codes from generation date. Operational rule: **batch-generate against actual distribution windows, never against the calendar.** Don't pre-generate Q1 codes in January if you're distributing in March — they'll be dead.

**TestFlight build expiration: 90 days per build.** Less aggressive but still bites. If a press contact agrees to review and asks for a "next month" build, push a fresh build closer to their review date. The 90-day clock starts at upload, not at first install.

## Post-Launch Strategy

**Refresh on version cadence.** Each new shipped App Store version regenerates the 100-code pool. If Tideward ships 2-3 versions per year post-launch, that's 200-300 codes annually. Plan distribution against the [creator-outreach-playbook](../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md) cadence. **Keep 17-20% reserve per cycle.** Unplanned press opportunities, surprise creator interest, podcast hosts who DM out of the blue — these eat into reserves and are usually the highest-conversion redemptions in the batch.

## Anti-Patterns

- **Public code drops.** Bot-scraped, attribution destroyed, code wasted.
- **Auto-generating codes on a calendar.** Forgets expiration; codes expire before distribution begins. Generate to a distribution event, not to a date.
- **Skipping CPP + redirect attribution.** Redemption looks like organic install; you lose channel-effectiveness signal.
- **Treating codes as a paid-media budget substitute.** Codes are a **trust signal** (here's the game, please tell people about it), not a paid channel. Paid acquisition does not run through this rail.
- **Sending press codes without a TestFlight build option.** Reviewer might want to start writing now; if the App Store version isn't live yet, you've gated their workflow. Offer both.
- **Forgetting tvOS/visionOS/watchOS redemption goes through an iOS device.** Communicate this when shipping multi-platform codes — reviewers test on a TV/headset/watch but redeem on a phone.

## Tideward Pre-Launch Distribution Plan

**T-3 months (warm-up).** No promo codes yet — codes generated now expire before the review can publish. Use TestFlight email invites instead: 10 Tier A creator slots, 10 trusted press slots. Press kit lives at `tideward.app/press` with TestFlight join instructions.

**T-1 month (press push).** Generate 30 press codes. Distribute under embargo with TestFlight backup invite for reviewers who prefer pre-release. Pair every code with a CPP per outlet and a `tideward.app/go/<outlet>` redirect.

**T-1 week (newsletter + Reddit appreciation).** Generate 20 newsletter giveaway codes (gate by reply-to-issue). Hold 10 for launch-day Reddit thread thanks-for-the-feedback gifts to specific named commenters from earlier organic threads. **Do not post code drops.**

**T+0 launch.** Hold 15-20 codes in reserve for the surprise opportunities that show up in the launch-week noise (podcast host DMs, fellow indie dev cross-promo, a journalist who heard about the launch late). These are typically the highest-conversion codes of the whole cycle.

**Q3/Q4 2027 onward.** Each new version refresh mints a new 100. Stick to the per-channel allocation grid above, refresh creator tiers against the latest [youtube-idle-factory-creator-landscape.md](../../../the-assembly-line/RESEARCH/youtube-idle-factory-creator-landscape.md), and audit the spreadsheet quarterly for leak patterns.

## Sources

- [Apple Developer: Request and manage promo codes](https://developer.apple.com/help/app-store-connect/offer-promo-codes/request-and-manage-promo-codes/)
- [Apple Developer: Invite external testers](https://developer.apple.com/help/app-store-connect/test-a-beta-version/invite-external-testers/)
- [Apple Developer: TestFlight overview](https://developer.apple.com/help/app-store-connect/test-a-beta-version/testflight-overview/)
- [Apple Developer: Create offer codes for IAP](https://developer.apple.com/help/app-store-connect/manage-in-app-purchases/create-offer-codes-for-in-app-purchases/)
- [Apple Developer: TestFlight (product)](https://developer.apple.com/testflight/)
- [Adapty: Apple Subscription Offers Guide 2026](https://adapty.io/blog/apple-subscription-offers-guide/)
- [Adapty: Custom Product Pages Guide 2026](https://adapty.io/blog/custom-product-pages-app-store/)
- [Apptweak: Guide to Custom Product Pages 2026](https://www.apptweak.com/en/aso-blog/guide-to-custom-product-pages-cpp)
- [Appbot: Apple Offer Codes Explained](https://appbot.co/blog/apple-offer-code/)
- [Cameron 2026: Stop Using Custom Product Pages to Track UGC Creators](https://medium.com/@oliver.cameron0/stop-using-custom-product-pages-to-track-your-ugc-creators-6ef7a65ec54f)
- [AppleInsider: Apple rolls out promo codes for in-app purchases (historical)](https://appleinsider.com/articles/16/10/28/apple-rolls-out-promo-codes-for-in-app-purchases)
- [Apptamin: Everything You Need to Know About App Promo Codes](https://www.apptamin.com/blog/app-promo-codes/)
- [Adam Wulf: App Launch Guide (indie ref)](https://github.com/adamwulf/app-launch-guide)
- [Foresight Mobile: iOS Distribution Guide 2026](https://foresightmobile.com/blog/ios-app-distribution-guide-2026)
- [Kount: Promo abuse fraud prevention](https://kount.com/blog/promo-code-abuse-discount-fraud-consequences)
- [Partnerships Collective: Promo code tracking attribution](https://www.thepartnershipscollective.com/insights/promo-code-tracking-attribution)
- Sibling research: [`the-assembly-line/RESEARCH/x-funnel-math.md`](../../../the-assembly-line/RESEARCH/x-funnel-math.md), [`creator-outreach-playbook.md`](../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md), [`youtube-idle-factory-creator-landscape.md`](../../../the-assembly-line/RESEARCH/youtube-idle-factory-creator-landscape.md)
