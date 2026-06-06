# Custom Product Page Variants for Tideward
> Filed: 2026-06-01. Tier: WARM (launch deliverable + ongoing).

## TL;DR

Apple raised the Custom Product Page (CPP) cap from 35 to 70 per app per locale in October 2025, added keyword-assignment to CPPs in mid-2025, and enabled deep-link routing on iOS 18+. Each CPP keeps icon, name, ratings, and description from the default page but swaps in custom screenshots, up to 3 preview videos, and up to 170 chars of promotional text. Each CPP gets a unique URL plus optional deep link. Conversion lift vs. the default page averages around +156% (2.5 pp vs. 1.6 pp baseline) when CPP creative is tightly matched to inbound intent, per Apple's data plus AppTweak's SoundCloud case (-39% CPI, +58% conversion vs. competitor-keyword ASA traffic).

Tideward's right-sized inventory at launch is roughly **15 active CPPs**: 5 per-creator (Tier A), 3 ASA campaign-type, 3 per-segment (Melvor lapsed, OSRS skiller, indie premium fan), 2 channel (newsletter, tideward.app /go redirects), 2 reserve. Not 70. CPPs cannot be A/B tested against each other inside Apple's Product Page Optimization (PPO) framework; PPO is reserved for the *default* page. Pair every CPP with a `tideward.app/go/<slug>` redirect and the promo-code workflow in [`promo-code-testflight-distribution.md`](promo-code-testflight-distribution.md). Refresh quarterly, retire low-performers. Don't build CPPs without an attached distribution plan, and don't ship CPPs visually identical to the default page.

---

## What CPPs Are (2026)

A Custom Product Page is an alternate App Store listing tied to a unique URL.

- **Customizable per CPP:** screenshots (full per-platform set), up to 3 app preview videos, promotional text (170 char max), keywords (for organic discovery, per the mid-2025 update), and an optional deep link (iOS 18 / iPadOS 18+; requires Apple review).
- **Locked to default page:** icon, app name, subtitle, ratings, description, IAP listings, price.
- **Cap:** 70 CPPs per app, up from 35 as of October 29, 2025. Each CPP supports up to 3 localized versions counted as one CPP toward the limit.
- **Per-platform asset requirement:** every CPP requires the full screenshot set across every device size. For Tideward (six Apple platforms), one CPP is a meaningful production pass.

**How a CPP gets traffic:**
1. **Direct URL share.** The `ppid=` parameter routes anyone clicking it to the CPP. Tap "Get" and the install attributes to that CPP in App Store Connect.
2. **Organic search.** Since mid-2025, assigning keywords to a CPP makes it show up in App Store search results for those terms.
3. **Apple Ads ad-group binding.** Each ad group can attach one CPP; up to 10 CPPs per ad campaign.
4. **Deep link tail.** iOS 18+ users tapping "Open" land at a specific in-app destination instead of the home screen.

CPPs are visible only to users who follow a CPP URL or hit a CPP keyword. The default page remains the canonical fallback for general browsing.

---

## Tideward's CPP Inventory Plan

Apple permits 70. Tideward needs roughly 15 at launch, with room to grow toward 25–30 by month 6.

| Slot | Bucket | Count | Rationale |
|---|---|---|---|
| 1–5 | Per-creator (Tier A) | 5 | One per Tier A creator per [`creator-outreach-playbook.md`](../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md): Olexa, DangerouslyFunny, Spiffing Brit, Aliensrock, Retromation |
| 6–8 | ASA campaign-type | 3 | One each for Brand, Competitor, Discovery ad groups (Category shares the default page) |
| 9–11 | Per-segment | 3 | Melvor lapsed adult; OSRS skiller; indie premium fan |
| 12 | Newsletter (The Assembly Line) | 1 | Linked from Beehiiv issues + footer; aligned with newsletter voice |
| 13 | tideward.app primary buy button | 1 | Website's "Get on iPhone" CTA routes here, not the default page |
| 14–15 | Reserve | 2 | Held for Reddit AMA flair, conference handouts, surprise press opportunities |

Total active at launch: **15**. Adapty 2026 and RespectASO both recommend "start small with 3–5 and grow." Production cost is the binding constraint, not the cap.

---

## Variant Differentiation Strategy

A CPP that looks identical to the default page wastes the slot. Every Tideward CPP must differ in at least two of these three layers:

1. **Hero text (promotional text, 170 chars).** Lead with the audience's value prop, not Tideward's voice. For an Olexa CPP, the first words are "Recommended by Olexa." For an ASA Competitor CPP, the first words name the differentiator vs. the competitor app the user searched for.
2. **Screenshot order and caption emphasis.** Same per-platform composition rules as [`screenshot-blueprint-strategy.md`](../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md), but reorder slots 1–3 to match the audience. Melvor segment leads with the 23-skill list, not the almanac hero. OSRS segment leads with offline progress. Indie-premium segment leads with the "One purchase. No advertisements." inclusion panel.
3. **App preview video (if produced).** Sharing a single 30s base cut across CPPs is acceptable launch-day; long-term, swap the cold-open per CPP.

Constant across CPPs: icon, name, subtitle, description, and the visual brand language (oxblood + parchment + EB Garamond per the Beehiiv design recipe). A CPP is a remix, not a different game.

---

## Per-Creator CPP Specifics

Tier A creators get dedicated CPPs:

- **URL slug.** App Store Connect generates the `ppid` automatically; Tideward exposes it via `tideward.app/go/olexa` (Cloudflare 301 to the Apple URL). Cloudflare Web Analytics logs the click count, which is the only attribution that survives Apple's opt-in blackout.
- **Promotional text (170 chars).** "Recommended by Olexa. Twenty-three skills. Offline progress, honestly calculated. One purchase, no ads, no subscriptions." Frame the endorsement first.
- **Screenshots.** Same per-platform composition as default, but Slot 1 is the skill/feature the creator highlights. If Olexa's coverage centers on offline gains, Slot 1 is the offline-gain modal.
- **Preview video.** If creator coverage produced a usable 5–10s clip and they grant rights, splice it as cold-open. Otherwise reuse the base 30s cut.
- **Promo code pairing.** Each creator gets 3 codes (per [`promo-code-testflight-distribution.md`](promo-code-testflight-distribution.md)) alongside the CPP URL.

Distribute the URL only to that creator. Multi-CPP audience overlap credits last-clicked.

**Caveat:** Apple does not expose downstream revenue or retention per CPP. CPP analytics show downloads, not LTV. Cameron 2026 explicitly warns against treating CPP analytics as a UGC scorecard. Pair every CPP with a Cloudflare-logged redirect and a spreadsheet mapping creator, CPP, promo-code batch, observed redemption.

---

## ASA CPP Integration

Apple Ads recommends four campaign types: **Brand, Category, Competitor, Discovery.** Each ad group can attach one CPP; up to 10 CPPs per campaign. Tideward's three ASA CPPs map as follows:

| ASA Campaign | CPP Variant | Promo text leans into | Slot 1 leads with |
|---|---|---|---|
| Brand ("tideward", "tideward idle", "manu games") | Brand CPP | Brand voice; user knows the title. "An Idle Almanac. Six platforms. One purchase. No ads, ever." | Almanac hero |
| Competitor ("melvor idle", "melvor", "idle rpg") | Competitor CPP | Direct contrast vs. Melvor's known reviews. "23 skills, offline progress, no paywalls. One $9.99 unlock." | Skill grid |
| Discovery (Search Match on; brand/category/competitor as negatives) | Discovery CPP | Broader appeal; less context assumed. "An almanac you idle into. Twenty-three skills trained quietly." | Mood/atmosphere slot, with caption |

The **Category campaign** ("idle game", "incremental") points to the default page rather than a dedicated CPP. Category traffic is high-volume and the default page's PPO experiments need that volume; sending category traffic to a CPP starves the PPO sample.

**Performance signal:** AppTweak's SoundCloud case (Competitor ad group + matched CPP): -39% CPI, +58% conversion. Upper-bound. AppTweak's broader 2025 dataset suggests +8% conversion for games when CPP-to-intent alignment is good. Use +8% as the realistic expectation.

---

## Attribution Mechanics

Each CPP URL carries a `ppid=` parameter. App Store Connect attributes the install to that CPP. Apple exposes:

- Visit count per CPP.
- Conversion rate per CPP (visits to installs).
- Source breakdown (web referrer, App Store search if keywords assigned, Apple Ads if attached).

What Apple does not expose: revenue, LTV, refunds, cross-CPP journeys, or source attribution beyond bucket-level.

The zero-SDK attribution stack (per the promo-code file) is the only triangulation. Maintain a single spreadsheet with CPP slug, channel, promo-code batch ID, distribution date, observed redemption from Sales & Trends, and Cloudflare redirect clicks. Accept the final number is a range, not a number. Apple's privacy posture makes precise per-creator ROAS structurally impossible without an MMP, which is not Tideward's lane.

---

## A/B Testing CPPs

The most misunderstood part: **CPPs cannot be A/B tested against each other inside PPO.** PPO and CPP are distinct:

- **PPO** runs up to 3 treatments vs. the *default* page, 90-day max, 90% Bayesian confidence. Tests visual elements (icon, screenshots, preview). Winner propagates to the default page.
- **CPP** is up to 70 permanent variant pages bound to specific URLs, keywords, or ad groups. Not experiments; *targeting* artifacts.

Mental model: PPO finds the strongest default page for organic traffic; CPPs personalize that strongest page for specific traffic sources. Critically: **traffic routed to a CPP does not count toward PPO sample size.** If Tideward routes most newsletter and ASA traffic to CPPs, the PPO test loses volume. Tideward runs at ~700 PPVs/day per the screenshot blueprint, making a 6-week single-treatment PPO realistic only if CPP siphon stays modest.

**Operational rule:** When PPO is live on the default page, hold CPP creative steady. Don't push new CPPs to traffic-heavy channels mid-test. Plan PPO and CPP refresh in alternating quarters.

Informally: run CPPs in parallel with channel-attribution discipline and compare visit-to-install conversion. Descriptive monitoring with confounds, not statistical testing. Tells you which CPP to retire.

---

## Creation Workflow

App Store Connect, App, Custom Product Pages: **Create Custom Product Page**, name (internal), upload screenshots per platform, upload up to 3 previews, enter promotional text, optionally assign keywords, optionally attach a deep link, submit for review. Standalone CPP review is comparable to a metadata-only update, typically under 48h.

Per-CPP timing:
- **Screenshots for six platforms.** ~6–10 hours if reusing base assets and reordering captions; longer if Slot 1 changes meaningfully.
- **Promotional text.** ~15 minutes, including voice-check vs. the brand recipe.
- **Deep link approval.** First-time setup adds review delay; subsequent CPPs reuse the approved domain.
- **Localization.** Each of up to 3 locale variants per CPP roughly doubles production. Start English-only.

15 CPPs at ~8 hours each is ~120 hours of asset work, spread across the 3 weeks before launch.

---

## Refresh Cadence

Quarterly review. Questions:

- **Visit count per CPP.** Is anyone using the URL?
- **Conversion rate per CPP vs. default.** Materially above 1.6% (Apple's stated baseline)?
- **Channel context.** Is the channel active? (A creator inactive 3 months does not need a live CPP.)

Retire any CPP with <50 visits/quarter and no upcoming campaign. Reuse the slot. Maintain a graveyard log so a retired creator can be reactivated quickly.

Don't refresh creative on a performing CPP. Getting a creator to update their video description with a new URL is high friction; stability is its own value. Refresh only when conversion stalls or the brand voice update warrants disruption.

---

## Promo Code + CPP Pairing

Promo codes carry no CPP attribution on their own; a code redeem is logged as a redeem, not a CPP visit. Pair them anyway for channel mapping:

- Outreach email: "Here's a complimentary copy [code]. If your audience wants it directly, the link is [tideward.app/go/<slug>], a custom page tuned for your viewers."
- The promo code installs bypass the CPP visit funnel. The CPP URL captures the audience's non-code installs via the link. The Cloudflare-logged redirect captures click-through regardless of route.

Cross-link with [`promo-code-testflight-distribution.md`](promo-code-testflight-distribution.md) for the full allocation grid. Codes expire 4 weeks after generation, so pairing happens in the same outreach push.

---

## What NOT to Build

- **CPPs for every imaginable segment.** Production cost is real; the 70-cap is not a target.
- **CPPs without a distribution plan.** Decide the channel first.
- **CPPs visually identical to the default page.** Apple review may push back; either way the slot is wasted.
- **CPPs that violate App Review guidelines binding the default page.** 2.3.7, 2.3.3, 2.3.10 apply identically.
- **CPPs for traffic Tideward cannot route.** No TikTok CPP without a TikTok presence; no paid-Reddit CPP without a paid budget.
- **PPO and CPP launches in the same sprint.** One experimentation surface per quarter.

---

## Tideward Pre-Launch CPP Build

Staged 3-week build:

- **T-3 weeks:** Finalize the default page (icon, subtitle, description, screenshots, preview video). Without a finished default, variants have no baseline to remix from.
- **T-2 weeks:** Build 5 Tier A creator CPPs in parallel. Highest leverage, longest lead (creators need 2–3 weeks to plan video coverage). Submit each for review; bundle if possible.
- **T-1 week:** Build 3 ASA CPPs (Brand, Competitor, Discovery). These attach to ad groups on launch day; cannot ship before the campaigns exist.
- **T-3 days:** Build the newsletter CPP plus the tideward.app primary CPP. Launch issue and website link to these.
- **Launch day:** 8–10 CPPs active (5 creator + 3 ASA + newsletter + tideward.app). Segment CPPs and reserves deferred.
- **T+30 days:** Review CPP visit data. Build 3 segment CPPs (Melvor / OSRS / indie premium) using observed traffic patterns to tune Slot 1.
- **T+90 days:** First quarterly retirement / refresh pass.

Alpha-gate note: per current memory, several marketing levers stay gated on alpha conversion improving. The CPP plan is forward-compatible; the 8–10 launch-day CPPs can be staged in App Store Connect and held in "Ready for Sale" without distributing URLs until Seth opens the gate.

---

## Anti-Patterns

- **CPPs without unique URLs in distribution.** The URL routes users; without it, the default page shows.
- **Identical screenshots across CPPs.** Defeats the purpose.
- **Forgetting localization.** Each Tideward locale (en-US, eventually de, fr, ja) needs the CPP localized, or users get default-page text in their language and CPP screenshots in English.
- **Over-tagging URLs.** Third-party UTM or shortener layers can break Apple Ads attribution. Use the CPP URL natively in Apple Ads; route everything else through `tideward.app/go/<slug>` Cloudflare redirects, which preserve `ppid` cleanly.
- **Building CPPs for hypothetical creators.** Confirm coverage interest first.
- **Treating CPP analytics as ground truth.** Visits and installs only. The spreadsheet of CPP × promo-code × redirect logs is the real attribution model.
- **Skipping the deep link.** iOS 18+ routing converts visit-to-engagement better than dropping users at the home screen. Adds ~1 day of review per first-time setup; budget it.
- **Letting promotional text drift.** 170 chars is short. Each variant should be quoteable, differentiated, and reviewed against the no-em-dash / no-AI-voice contract.

---

## Sources

- [Apple Developer: Custom Product Pages overview](https://developer.apple.com/app-store/custom-product-pages/)
- [Apple Developer: Configure multiple product page versions (App Store Connect Help)](https://developer.apple.com/help/app-store-connect/create-custom-product-pages/configure-multiple-product-page-versions/)
- [Apple Developer: Get started with custom product pages (Tech Talk 10886)](https://developer.apple.com/videos/play/tech-talks/10886/)
- [Apple Ads: Campaign Structure Best Practices (Brand/Category/Competitor/Discovery)](https://ads.apple.com/app-store/best-practices/campaign-structure)
- [Apple Ads: Create Ad Variations](https://ads.apple.com/app-store/help/ads/0077-create-ad-variations)
- [Apple Developer Forum: Deep Links on Custom Product Pages](https://developer.apple.com/forums/thread/757367)
- [Custom Product Pages in 2026: 70 Pages, Keywords, Limits (RespectASO)](https://respectaso.com/blog/custom-product-pages-app-store-guide-2026/)
- [Apple doubles the custom product page limit (MobileAction)](https://www.mobileaction.co/blog/apple-doubles-the-custom-product-page-limit/)
- [App Store Custom Product Pages: Guide for 2026 (Adapty)](https://adapty.io/blog/custom-product-pages-app-store/)
- [A Step-by-Step Guide to Custom Product Pages in 2026 (AppTweak)](https://www.apptweak.com/en/aso-blog/guide-to-custom-product-pages-cpp)
- [Best practices for custom product pages with Apple Ads (AppTweak)](https://www.apptweak.com/en/aso-blog/apple-search-ads-custom-product-pages-best-practices)
- [Custom Product Pages with Apple Search Ads (Phiture)](https://phiture.com/mobilegrowthstack/custom-product-pages-with-apple-search-ads/)
- [SoundCloud CPI -39% case study (AppTweak)](https://www.apptweak.com/en/case-studies/soundcloud)
- [SoundCloud conversion +58% case study (AppTweak)](https://aso.apptweak.com/how-soundcloud-increased-conversion-rates-by-58-in-5-months)
- [Beginner's Guide to Custom Product Pages (SplitMetrics)](https://splitmetrics.com/blog/ios15-custom-product-pages-setup-guide/)
- [Product Page Optimization (PPO) on the App Store (Appbot)](https://appbot.co/blog/product-page-optimization/)
- [App Store PPO A/B testing guide 2026 (MobileAction)](https://www.mobileaction.co/blog/product-page-optimization/)
- [Apple Search Ads CPP assets requirements (AppRadar)](https://appradar.com/academy/apple-search-ads/custom-product-pages-assets-requirements)
- [Stop Using Custom Product Pages to Track UGC Creators (Cameron 2026)](https://medium.com/@oliver.cameron0/stop-using-custom-product-pages-to-track-your-ugc-creators-6ef7a65ec54f)
- Internal: [`promo-code-testflight-distribution.md`](promo-code-testflight-distribution.md), [`../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md`](../../../the-assembly-line/RESEARCH/screenshot-blueprint-strategy.md), [`../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md`](../../../the-assembly-line/RESEARCH/creator-outreach-playbook.md), [`../../../the-assembly-line/RESEARCH/apple-search-ads-2026-premium-ios-benchmarks.md`](../../../the-assembly-line/RESEARCH/apple-search-ads-2026-premium-ios-benchmarks.md).
