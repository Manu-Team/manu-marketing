# Asset CDN Strategy + Versioning for Manu Games Public Assets

> Filed: 2026-06-01. Tier: WARM (post-launch asset growth).
>
> **Status 2026-08-21:** launch is 2027-02-11, so the T-0 / T-30 / T+90 milestones in the
> migration plan below land Feb 2027 / Jan 2027 / May 2027, not the June-2026 parentheticals
> written into the headings. R2 was never stood up: `assets.tideward.app` does not resolve, and
> the lead magnets are still served from `raw.githubusercontent.com`. The recommendation stands;
> none of it has been executed.

## TL;DR

Manu Games today hosts public assets (3 lead-magnet PDFs) directly out of the `Manu-Team/manu-marketing` GitHub repo via `raw.githubusercontent.com`. That works for ~5 files but breaks at press-launch scale: GitHub aggressively rate-limited unauthenticated raw requests in May 2025, and a coordinated press hit can trip 429s per public IP across hosts that hotlink the kit. The replacement is **Cloudflare R2 on a custom domain** (`assets.tideward.app` for game-side, `assets.manugames.com` for publisher-side), with **path versioning for press kits** (`/press/v1/`) and **content-hash filenames for one-off assets** (`keyart-abc123.png`). R2's storage cost is $0.015/GB/month and egress to anywhere is free, which is the only line item that matters during a coordinated launch spike. Backblaze B2 is cheaper at the storage layer ($0.006/GB/mo) and free-to-Cloudflare via the Bandwidth Alliance, but R2 wins on simplicity for ~10 GB of static assets where storage cost is negligible and the operational tax of a two-vendor handoff isn't worth saving $0.09/month. AWS S3 is not in the running for indie use at $0.09/GB egress. Migrate in three phases: stand R2 up alongside GitHub raw now, switch README and press-kit links over by T-30, and stop minting new `raw.githubusercontent.com` URLs from T+0 onward.

## The Asset Inventory (Growth Path)

What lives on a public CDN today, and what's coming:

- **Today:** 3 lead-magnet PDFs in `marketing/` (`factory-game-starter-guide.pdf`, `factory-optimization-checklist.pdf`, `idle-rpg-starter-guide.pdf`) plus `tideward-testflight-qr.png`. All served via `raw.githubusercontent.com/Manu-Team/manu-marketing/main/...`. Combined ~5 MB. (The June-2026 filing named three different files that were never in this repo; corrected 2026-08-21.)
- **Press launch (T-0, ~August 2026):** Press kit drops from `press-kit-industry-standards.md` build-out: ~25 assets (key art at 3 resolutions, 8 in-game screenshots at 2 resolutions, 1 logo lockup set with 5 variants, 1 founder photo set, 3 short video loops). Estimated 200 MB.
- **Blog growth:** Tideward.app blog adds ~8 posts/month with 2-4 images each. Call it ~100 images/year, ~150 MB/year at sensible AVIF/WebP sizes.
- **Tideward updates:** Each app version (currently pre-release; v1.0 ships 2027-02-11) adds a screenshot set per platform (6 platforms x 5 screenshots = 30 images), plus marketing key art revisions. Call it ~50 MB per version.
- **18-month projection:** ~500 public assets, ~1.5 GB total. Storage cost on R2 = $0.022/month. Egress is the actual cost driver, not storage.

The shape: **always small individually, never huge in aggregate, occasionally spiky on egress**. That maps cleanly to R2's pricing model and badly onto storage-tiered offerings like S3 Glacier or B2 archive tiers.

## GitHub Raw URLs (Current State)

The current pattern is `https://raw.githubusercontent.com/Manu-Team/manu-marketing/main/<path>`. This is genuinely fine for the indie pre-launch phase:

**Pros:**
- Zero cost, zero setup.
- Version-controlled by design (every commit is permanent in git history).
- TLS is handled.
- Cloudflare itself fronts `raw.githubusercontent.com`, so global latency is acceptable.

**Cons (the launch-day killers):**
- **GitHub tightened unauthenticated rate limits in May 2025.** Anonymous requests to `raw.githubusercontent.com` are now capped per source IP, and the ceiling is low enough that a single shared-IP corporate network (think: a press outlet's office) can trip 429s after dozens of hits. Multiple downstream tools (Bazarr, OpenTofu, others) have logged production breakage from this change. ([changelog](https://github.blog/changelog/2025-05-08-updated-rate-limits-for-unauthenticated-requests/))
- **No custom domain.** Links read `raw.githubusercontent.com/Manu-Team/manu-marketing/main/press/keyart.png`, which screams "this is a GitHub repo" rather than "this is Manu Games' press kit."
- **No purge control.** A bad upload sits in caches until TTL expires; there's no first-party way to force a refresh.
- **No analytics.** No way to see which press outlets are pulling the kit.
- **Hard-coded `main` branch.** Press references like `/main/press/keyart.png` will mutate silently if the file is overwritten on `main`, which makes in-flight press citations fragile.

The combination is fine for 3 lead magnets. It's not fine for a press kit that will be hotlinked by Polygon/Eurogamer/RPS-equivalents on a coordinated launch day.

## Cloudflare R2

R2 is Cloudflare's S3-compatible object store, designed to undercut S3 on the dimension indie businesses care about most: **egress is free, period.** Not "free to Cloudflare," not "free under our partner program" — free to the open internet, no per-GB transfer charge, no tiering. ([R2 pricing](https://developers.cloudflare.com/r2/pricing/))

**Pricing (2026):**
- Storage: $0.015/GB/month. First 10 GB free per account/month.
- Class A operations (writes, lists): $4.50 per million. First 1M free per month.
- Class B operations (reads): $0.36 per million. First 10M free per month.
- Egress: **$0.** Always.

**At Manu Games' scale:** 1.5 GB stored = $0 (under the 10 GB free tier). Press-launch day with, say, 100K reads of the press kit = $0 (under 10M Class B free tier). Real-money R2 charges for this project start somewhere around 50 GB stored or 50M reads/month, which is well past press launch.

**Setup is straightforward:**
1. Create a Cloudflare account (already exists — both `tideward.app` and `manugames.com` are on Cloudflare with proxied DNS).
2. Enable R2 (one-click in dashboard, no separate signup).
3. Create bucket: `manu-marketing-prod`.
4. Settings → Public access → Custom Domains → Connect Domain → `assets.manugames.com`.
5. Cloudflare auto-provisions TLS and adds the CNAME record. Activation takes ~5 minutes. ([R2 custom domain setup](https://developers.cloudflare.com/r2/buckets/public-buckets/))
6. Repeat for `assets.tideward.app` (separate bucket: `tideward-assets-prod`, or single bucket with path-based routing — pick the simpler path).

**Operational benefits Manu Games will actually use:**
- Custom domain means press links read `https://assets.tideward.app/press/v1/keyart.png` — looks like a first-party product, not a code repo URL.
- WAF / cache / bot management apply because R2 sits behind the Cloudflare proxy.
- Cache purge via dashboard or `wrangler r2 object delete` (purge quota is generous: 1000/day on the free plan, more than enough for our churn).
- Web Analytics works out of the box, so we can see which press outlets actually pulled the kit.

**The one R2 gotcha:** R2 buckets are not directly browsable without a custom domain. If you want the bucket to appear at `assets.tideward.app` rather than the auto-generated `pub-<hash>.r2.dev` URL, the custom domain setup above is required, and the zone must be on Cloudflare. (Both ours are.)

## Backblaze B2

B2 is the cost-optimized alternative. ([B2 pricing](https://leanopstech.com/blog/backblaze-b2-pricing-2026/))

**Pricing (2026):**
- Storage: $0.006/GB/month (60% cheaper than R2).
- Egress: $0.01/GB to most networks. **Free to Cloudflare** via the Bandwidth Alliance, with no caps or ratio limits.

**The trap for indie use:** B2's cost win materializes at the storage tier, but Manu Games' asset library is permanently in R2's free 10 GB tier. So the per-GB-stored savings is $0.00 vs $0.00 — i.e., zero savings.

**When B2 + Cloudflare beats R2:**
- Storage > 10 GB *and* you're willing to run a two-vendor stack.
- Workloads where storage cost dominates (archival, backups, infrequent reads). Not our shape.

**When R2 beats B2:**
- Storage < 10 GB (free tier).
- You want a single-vendor stack with Cloudflare DNS / Workers / WAF / Analytics already in place.
- You want cache invalidation and custom-domain TLS without a second control plane.

For Manu Games, R2 wins on operational simplicity. We're not Mixpeek or a hosting provider; we have ~10 hours/quarter of sysadmin budget. ([R2 vs B2 vs S3 breakdown](https://www.flowverify.co/blog/cloudflare-r2-vs-s3-vs-backblaze-b2-cost-breakdown))

## AWS S3

S3 is the most expensive option on both dimensions that matter:
- Storage: $0.023/GB/month (53% more than R2).
- Egress: $0.09/GB to the open internet. A 10K-download press-launch day of a 50 MB press kit = ~$45 in egress alone.

S3 is in the running for enterprise workloads where AWS lock-in already exists or where Glacier-tier archival is the use case. **Not recommended for Manu Games.** Skip.

## Custom Domain Pattern

Two domains, two buckets, kept architecturally parallel to the website split:

- `assets.tideward.app` — game-side assets. Bucket: `tideward-assets-prod`.
- `assets.manugames.com` — publisher-side assets (lead magnets, founder photos, press kit if cross-brand). Bucket: `manu-marketing-prod`.

**Setup steps (per domain):**
1. R2 dashboard → bucket → Settings → Public access → Custom Domains → Connect Domain.
2. Enter `assets.tideward.app` (or `assets.manugames.com`).
3. Cloudflare auto-creates the CNAME record (`assets` → `pub-<hash>.r2.dev`).
4. TLS auto-provisions in ~5 minutes.
5. Verify with `curl -I https://assets.tideward.app/test.png`.

**URL pattern (final):**
```
https://assets.tideward.app/press/v1/keyart-3840x2160.png
https://assets.tideward.app/press/v1/keyart-2560x1440.png
https://assets.manugames.com/lead-magnets/melvor-vs-tideward-2026-06.pdf
https://assets.tideward.app/blog/2026/06/screenshot-loop-jpg.jpg
```

Reads like a first-party asset CDN. Looks professional in press citations.

## Versioning Strategy

Two patterns, applied based on asset type:

**Path versioning (for press kits, lead magnets, anything cited externally):**
```
/press/v1/keyart.png          ← current press kit
/press/v2/keyart.png          ← next press kit (Q4 update)
/lead-magnets/melvor-comparison-2026-06.pdf  ← date suffix as version
```

Why: when an outlet writes "image courtesy of Manu Games (assets.tideward.app/press/v1/keyart.png)," that URL must stay live forever. Path versioning means v1 sits there immutably while v2 ships beside it. Old citations don't 404, new press gets the fresh version.

**Content-hash filenames (for blog images, screenshots, any one-off asset):**
```
/blog/2026/06/dashboard-screenshot-a3f9d2c.png
/screenshots/app/v1.0/widgets-overview-b7c8e1d.png
```

Why: content-hash naming is the gold-standard cache-busting pattern. Same content = same hash = infinite-cache safe; content change = new hash = automatic cache miss without manual purge. ([CDN best practices](https://blog.blazingcdn.com/en-us/cdn-js-best-practices-minification-versioning-cache-bust-rules))

**Mixed in practice:** Press kit ships as a versioned directory (`/press/v1/`), and individual assets inside that directory get content-hash suffixes (`/press/v1/keyart-3840x2160-a3f9d2c.png`). Belt and suspenders, because press citations are too costly to break.

## Cache Headers

Set on upload via the `Cache-Control` metadata field on the R2 object:

**Immutable / content-hashed / versioned-path assets:**
```
Cache-Control: public, max-age=31536000, immutable
```
One year, immutable, never re-validate. Safe because the URL itself encodes the version.

**Updateable-in-place assets (avoid, but if needed):**
```
Cache-Control: public, max-age=3600
```
One-hour TTL, used sparingly. Don't use this on anything press will cite.

**HTML or asset manifest files (n/a for our use case but worth noting):**
```
Cache-Control: no-cache
```
Always re-validate. If we ever ship a manifest.json that lists current asset hashes, this is the right header. Don't apply this to the assets themselves.

The pattern Manu Games will run is **immutable everything**, because path versioning + content hashes mean we never need to update a file in place. If we need a new version, we publish it at a new URL.

## Cache Invalidation

Even with immutable URLs, occasional purges happen (wrong file uploaded, NDA leak, taking down a deprecated kit).

**Two paths:**
1. **Cloudflare dashboard** → Caching → Configuration → Purge by URL. Up to 30 URLs per request. Free.
2. **`wrangler r2 object delete <bucket> <key>`** — deletes the object from R2. Cache purge happens automatically when the underlying object is gone.

Free-plan purge quota is 1000 purges/day, which is roughly 1000x what Manu Games needs. We will essentially never hit a quota.

## Content Negotiation

For images, three formats are worth shipping: AVIF (smallest, modern browsers), WebP (broad support, smaller than JPEG), JPEG (universal fallback). Two paths:

**Option A — separate URLs per format (simpler, recommended for us):**
```
/blog/2026/06/screenshot-a3f9d2c.avif
/blog/2026/06/screenshot-a3f9d2c.webp
/blog/2026/06/screenshot-a3f9d2c.jpg
```
HTML emits a `<picture>` tag with all three. Browser picks the best supported. Zero server-side intelligence, zero Cloudflare add-on cost.

**Option B — Cloudflare Image Resizing / Polish (paid, more flexible):**
$5/mo Pro plan unlocks Image Resizing, which auto-negotiates format and size from a single URL. Probably worth it once we hit >100 images and shipping three variants per image becomes operationally annoying. Not needed at launch.

Manu Games ships Option A for the press launch. Reconsider Option B at the 100-image mark.

## Path Structure

Final directory layout, locked in for both buckets:

```
/lead-magnets/                    PDFs, named with date suffix
  melvor-vs-tideward-2026-06.pdf
  founder-letter-2026-06.pdf
  soundtrack-onepager-2026-06.pdf

/press/v1/                        Current press kit (immutable once published)
  keyart-3840x2160-<hash>.png
  keyart-2560x1440-<hash>.png
  screenshots/
    main-screen-<hash>.png
    ...
  logos/
    wordmark-light-<hash>.svg
    wordmark-dark-<hash>.svg
  founder-photo-<hash>.jpg
  press-release.pdf
  fact-sheet.pdf

/press/v2/                        Next press kit (ships when ready)

/blog/2026/06/                    Blog images by year/month
  <slug>-<hash>.{avif,webp,jpg}

/screenshots/app/v1.0/            App screenshots per app version
  ios/
  ipados/
  macos/
  ...

/wallpapers/2026/                 Lead-magnet adjacent
  tideward-4k-<hash>.png
```

Clean, browseable (in theory — R2 doesn't expose dir listing by default and that's fine), and survives 18 months of growth without restructuring.

## Public vs Private

**Every asset on this CDN is public by design.** The buckets are public. Anyone with a URL can download. This is correct for press kits, blog images, screenshots, lead magnets — all things we want hotlinked.

**Do not put on this CDN:**
- NDA pre-release material (use a separate private bucket with signed URLs or Cloudflare Access if needed).
- Beta build binaries (use TestFlight / direct Apple distribution).
- Internal docs (use the umbrella `manu-shared` repo, which is private).
- Anything containing PII (subscriber data, support ticket attachments).

The rule: **if it would be embarrassing to find on Google in six months, don't upload it.**

## Migration from GitHub Raw

Three-phase migration that doesn't break any existing links:

**Phase 1 (now, June 2026):** Stand up R2 + custom domains alongside GitHub raw.
- Upload the 3 lead magnets to R2 under new URLs.
- Keep GitHub raw URLs alive (we can't 301-redirect `raw.githubusercontent.com`; GitHub controls that hostname).
- Pin the lead-magnet URLs in the `marketing/` repo README to the new R2 URLs going forward.

**Phase 2 (T-30, July 2026):** Press-kit launch ships on R2 exclusively.
- All new press-kit assets go to `assets.tideward.app/press/v1/`.
- Update beehiiv, social bios, email footers, website CTAs to point at R2 URLs.
- Old GitHub raw URLs remain live (they're in the git history forever anyway), but we stop minting new ones.

**Phase 3 (T+90, October 2026):** R2 is canonical, GitHub raw is dead-but-not-deleted.
- All new assets go to R2.
- Periodically audit `marketing/` repo README for stale GitHub raw links and replace.
- Old links continue to work indefinitely because the files remain in `marketing/` git history.

The key constraint: **we cannot 301-redirect `raw.githubusercontent.com/Manu-Team/...`** because GitHub owns that hostname. The migration is therefore additive, not destructive. Acceptable.

## Manu Games Action List

1. **Sign up for R2** in the existing Cloudflare account. Both `tideward.app` and `manugames.com` are already in the account, so no DNS migration needed.
2. **Create buckets:** `tideward-assets-prod` and `manu-marketing-prod`.
3. **Wire custom domains:** `assets.tideward.app` → `tideward-assets-prod`; `assets.manugames.com` → `manu-marketing-prod`.
4. **Upload the 3 existing lead magnets** to `assets.manugames.com/lead-magnets/`.
5. **Update `marketing/` README.md** to point download links at R2 URLs.
6. **Document the path structure** in `marketing/docs/asset-cdn.md` (a short ops note pointing at this file).
7. **Establish the upload workflow:** `wrangler r2 object put manu-marketing-prod/lead-magnets/<file> --file=<path>` with `Cache-Control: public, max-age=31536000, immutable`.
8. **Set up versioning convention in writing:** press kits get `/press/vN/` directories with content-hash filenames inside; lead magnets get date-suffixed filenames; blog images get content-hash suffixes.
9. **Add a Cloudflare Web Analytics tag** on `assets.tideward.app` to track press-kit pulls.

Total setup time: ~90 minutes for someone who has never touched R2.

## Anti-Patterns

- **Hosting press assets on Dropbox / Google Drive / WeTransfer.** All three throw cert warnings or rate-limit downloads at any scale press would generate. Looks unprofessional in citations ("download from a random Dropbox URL"). Don't do this.
- **No versioning whatsoever.** Overwriting `keyart.png` in place breaks every in-flight press citation. Always version, either by path or by content hash.
- **`Cache-Control: no-cache` on immutable assets.** Defeats the entire point of a CDN. Hashed/versioned URLs should ship with `max-age=31536000, immutable`.
- **Custom domain without TLS.** Any public asset URL must be HTTPS. Cloudflare auto-provisions, so this is mostly a "don't manually disable" rule.
- **Mixing public and private in one bucket.** Don't. Public R2 is public. If a private asset needs protection, that's a separate bucket with Cloudflare Access in front. ([R2 + Access tutorial](https://developers.cloudflare.com/r2/tutorials/cloudflare-access/))
- **Two CDN vendors when one suffices.** R2 + B2 + S3 split for "redundancy" is operational debt indie teams cannot afford. Pick R2 and ship.
- **Hotlinking GitHub raw URLs in published press kits.** Once an outlet writes `raw.githubusercontent.com/...` into their article, we own that URL's stability forever, and we don't control the hostname. Move off before press launch, not after.

## Sources

- [Cloudflare R2 pricing](https://developers.cloudflare.com/r2/pricing/)
- [Cloudflare R2 public buckets + custom domains](https://developers.cloudflare.com/r2/buckets/public-buckets/)
- [Cloudflare R2 + Access (for private subsets)](https://developers.cloudflare.com/r2/tutorials/cloudflare-access/)
- [R2 vs S3 vs B2 cost breakdown — FlowVerify, 2026](https://www.flowverify.co/blog/cloudflare-r2-vs-s3-vs-backblaze-b2-cost-breakdown)
- [Backblaze B2 pricing 2026 — LeanOps](https://leanopstech.com/blog/backblaze-b2-pricing-2026/)
- [Cloudflare R2 pricing deep-dive — LeanOps](https://leanopstech.com/blog/cloudflare-r2-pricing-2026/)
- [Object storage comparison 2026 — Mixpeek](https://mixpeek.com/blog/object-storage-comparison-2026)
- [GitHub raw rate-limit changelog (May 2025)](https://github.blog/changelog/2025-05-08-updated-rate-limits-for-unauthenticated-requests/)
- [Persistent 429s on raw.githubusercontent.com — GitHub community thread](https://github.com/orgs/community/discussions/157887)
- [CDN cache-busting best practices — BlazingCDN](https://blog.blazingcdn.com/en-us/cdn-js-best-practices-minification-versioning-cache-bust-rules)
- [CDN cache busting strategies — HTTPFixer](https://httpfixer.dev/blog/cache/cache-busting-strategies/)
- [Serve static assets with R2 — Brett Weir](https://brettweir.com/blog/static-assets-cloudflare-r2/)
- [Building a free image CDN with R2 + Workers — Transloadit](https://transloadit.com/devtips/creating-a-free-image-cdn-with-cloudflare-r2/)
