# App Icon Design for the Liquid Glass Era (2026)
> Filed: 2026-06-01. Tier: WARM (informs launch icon production).

## TL;DR

The 2024 → 2026 stretch fundamentally rewired how Apple renders app icons. iOS 18 introduced Dark and Tinted variants. iOS 26 / iPadOS 26 / macOS 26 Tahoe shipped Liquid Glass — a multi-layer material with system-driven specular highlights, blur, translucency, and parallax. Apple's official Icon Composer app (WWDC25) replaced the old "ship a 1024 PNG" workflow with a single `.icon` document that bundles all layers, all appearance modes (Default, Dark, Mono / Tinted, Clear Light, Clear Dark), and ships to every Apple platform from one source. For Tideward, this means the illuminated-manuscript brand needs to be built as **separated vector layers** (parchment substrate, oxblood ink mark, gold foil accent) rather than a single flat composite, so the system can apply Liquid Glass effects per layer instead of treating the whole icon as a sticker. Design in Figma or Illustrator, hand off as layered SVG/PNG into Icon Composer, drag the `.icon` file into Xcode, and Xcode generates every size for iOS, iPadOS, macOS, watchOS, tvOS, and visionOS automatically. No transparent App Store icon, no skeuomorphic glass — Apple's system applies the glass; you provide the substrate.

## The 2026 Icon Variants

A modern Apple app icon is no longer a single image. As of iOS 26, an app is expected to ship **at least three appearance modes** and Icon Composer renders up to six:

| Variant | Purpose | When system uses it |
|---|---|---|
| **Default (Light)** | The canonical brand mark. Full color. | Default Home Screen, App Store, system surfaces in light appearance. |
| **Dark** | Dark-mode adaptation. Usually darker / desaturated background, brightened foreground. | User has set Appearance to Dark, or system is in dark mode. |
| **Mono (Tinted)** | Grayscale silhouette. System applies user-chosen tint hue. | "Tinted" Home Screen mode introduced iOS 18. |
| **Clear Light** | New iOS 26 mode. Translucent / glassy with bright surroundings. | iOS 26 "Clear" Home Screen aesthetic, light backdrop. |
| **Clear Dark** | New iOS 26 mode. Translucent / glassy on a dark backdrop. | iOS 26 "Clear" Home Screen aesthetic, dark backdrop. |
| **visionOS Layered** | Background plate + 1–2 floating front layers; system extrudes via parallax. | Vision Pro Home View. |

iOS picks the right variant automatically based on user Home Screen settings (Light / Dark / Tinted / Clear) and time of day if the user has set "Automatic." You do not pick; you ship variants, and the system chooses.

> **Tideward implication:** the parchment + oxblood brand reads strong in Light. In Dark and Clear, the parchment substrate must shift to a deeper tone (oxblood-saturated near-black) and the gold accent must lift to carry the mark. In Mono, only the silhouette of the manuscript "T" mark matters — color is replaced by the user's tint.

## Icon Composer Workflow

Icon Composer is Apple's official Mac app, introduced at WWDC25 and shipped alongside Xcode 26. It produces a single `.icon` document (a bundle, not a flat file) that contains all layers, all appearance modes, and per-platform overrides. Requires macOS Sequoia 15.3 or later.

**What Icon Composer does:**

- Accepts **SVG** (vectors, scale-perfect) and **PNG** (raster, for textures/blur) layer inputs.
- Applies Apple's preset Liquid Glass materials (specular highlight, blur radius, translucency, shadow depth) to any layer, with real-time preview.
- Lets you annotate per-mode behavior — e.g., "in Dark mode, swap this background for a darker tone" — inside one file.
- Previews against system wallpapers, with simulated lighting and parallax.
- Exports the `.icon` document for Xcode and a flat PNG/JPG for marketing.

**What it doesn't do:**

- It is not a vector illustration tool. You still draw the mark in **Figma, Illustrator, Sketch, or Affinity Designer**, export each depth-layer as its own SVG (with the platform corner-radius mask omitted — Icon Composer adds the mask), then assemble in Icon Composer.
- It does not generate raster textures, photographic illustration, or 3D renders. Bring those from your DCC of choice as PNG.

**Xcode integration:**

1. Drag `Tideward.icon` into the Xcode project.
2. Build target → General → App Icon → set to `Tideward` (the filename minus `.icon`).
3. Xcode compiles into `Assets.car` at build time, generating every required size and variant for the target platforms. A backwards-compatible `.icns` is also emitted for macOS.

`actool` (the asset catalog compiler that ships with Xcode) is the CLI equivalent — useful for CI pipelines that need to compile icons outside an Xcode build.

## Size Reference Table

The 2026 reality: **one master design, system-generated sizes**. You don't hand-export every size — Xcode does it from the `.icon`. The historical per-size table still matters for two reasons: (1) understanding minimum legible detail; (2) hand-producing static App Store and press-kit exports.

### iOS / iPadOS (rendered from `.icon`)

| Use | Size (pt @ 1×) | Export at |
|---|---|---|
| App Store | 1024 × 1024 | 1024 × 1024 (sRGB, opaque, no alpha) |
| iPhone Home Screen | 60 × 60 | @2× (120), @3× (180) |
| iPad Home Screen | 76 × 76, 83.5 × 83.5 | @2× (152, 167) |
| Spotlight | 40 × 40 | @2× (80), @3× (120) |
| Settings | 29 × 29 | @2× (58), @3× (87) |
| Notification | 20 × 20 | @2× (40), @3× (60) |

### macOS (rendered from `.icon`)

| Use | Size |
|---|---|
| App Store / Finder large | 1024 × 1024 |
| Dock, desktop | 512, 256, 128, 64, 32, 16 (each @1× and @2×) |

macOS 26 Tahoe uses the new `.icon` format compiled into `Assets.car`. `.icns` remains as a backwards-compatible fallback for pre-26 macOS.

### watchOS (rendered from `.icon`, circular mask applied)

Apple Watch's 2026 grid is **1088 × 1088** for the master (per Icon Composer specs), system applies circular mask. Designed legibly down to ~40 pt on a 40 mm watch.

### tvOS (layered, separate workflow)

tvOS still uses **layered images (LSR)** rather than `.icon`. Provide 2–5 stacked layers, each PNG, for the parallax effect. App Store icon is **1280 × 768**. Bottom layer must be fully opaque.

### visionOS (layered glass)

A background plate plus 1–2 front layers. Background must be fully opaque solid or gradient (no transparency in the back plate — it breaks the glass extrusion). Front layers use alpha. System adds the glass shell, highlights, and shadows.

## Dark Mode Best Practices

Dark mode is not "invert the colors." Apple's guidance and the practical pattern from successful redesigns converges:

- **Drop background luminance ~25–40%.** Parchment becomes deep oxblood near-black; vivid blue becomes navy.
- **Lift foreground luminance and saturation.** A foreground that read at 60% lightness in Light should be near 80–90% in Dark.
- **Don't simply omit the background** unless Apple's auto-dark-background fallback fits your brand. The system will swap in a neutral dark plate, which usually looks generic.
- **Use gradients from 100% down to ~60% opacity** on the foreground for a softer integration with system lighting.
- **Test against real wallpapers**, not the Icon Composer default checkerboard. Black wallpapers swallow dark icons.

## Tinted Mode Best Practices

Tinted (Mono) is iOS 18's "give me one grayscale layer, I'll tint it however the user wants." The system pulls a user-selected hue from the Home Screen tint picker and applies it as a gradient against a system-generated dark plate.

- **Submit a single grayscale image.** The foreground should be a silhouette that reads at a glance.
- **No background plate.** The system applies the tinted plate; you provide the figure.
- **Gradient from white at the top to ~60% gray at the bottom** is Apple's reference treatment, mimicking system glyphs.
- **The mark must work as pure silhouette.** If your brand depends on a color split (e.g., red letter on parchment), the tinted version collapses to one shape. Pick the shape that survives that collapse before you ever build the variant.

## visionOS Glass Tinted Variant

Vision Pro's Home View renders icons as **floating glass discs**. The system extrudes your icon into 2.5D and reflects ambient room light off the disc surface.

- **Background layer (mandatory).** Solid color or gradient. **Must be fully opaque** — transparency in the back plate corrupts the system's glass shader.
- **Front layer(s) (up to 2).** Alpha-channel PNG. The system uses the alpha to drive depth, shadow, and a gentle expand-on-gaze effect.
- **Circular composition.** visionOS icons are circular, not rounded-rect. Design within a circular safe area and keep critical detail inside the inner 70%.
- **No baked highlights.** The system adds specular reflection from the user's environment. Pre-baking highlights will fight the system shader and look stamped.

For Tideward: parchment back plate (full opacity), oxblood "T" mid-layer, gold filigree accent as the front layer. The user sees a glass-encased manuscript medallion that lights up with their room.

## Tideward-Specific Icon Direction

The brand contract: **parchment background, oxblood ink, gold accents, illuminated-manuscript aesthetic, EB Garamond / serif lineage.** Translating that into the 2026 multi-variant world:

**Light mode (default):**
- Background: warm parchment (`#F1E6CC` or similar, full opacity).
- Mid layer: oxblood serif "T" or manuscript mark.
- Front layer: gold-leaf accent (filigree, drop cap flourish, or initial-letter ornament).
- Liquid Glass material: low translucency on the back plate, medium specular on the gold accent so it catches system lighting like real foil.

**Dark mode:**
- Background: deep oxblood / mulled-wine near-black (`#2B0A0A` or similar).
- Mid layer: aged gold "T" (the role flips — gold becomes the primary mark, oxblood retreats to substrate).
- Front layer: lit parchment edge or minimal cream accent.
- Specular kept low; the gold should glow, not glint.

**Mono (Tinted):**
- Single grayscale layer of the "T" mark with the manuscript flourish, fading top-100% to bottom-60%.
- No background.
- Test the silhouette against bright cyan, pastel pink, and deep purple system tints. If any of those readings reads as "muddy crest" instead of "manuscript T," redraw.

**Clear Light / Clear Dark (iOS 26 new modes):**
- Strip the parchment back plate to ~40% opacity so the wallpaper reads through.
- Keep the oxblood mark and gold accent solid — they carry the brand.
- Test against the iOS 26 default wallpaper set, especially the gradient and photographic ones.

**visionOS:**
- Circular medallion. Parchment back plate, oxblood "T" mid, gold filigree front. The illuminated-manuscript metaphor is already a medallion — visionOS suits it natively.

**watchOS:**
- Drop the filigree. At watchOS sizes, only the "T" survives. Bold serif on parchment, no fine ornament.

**tvOS:**
- 3-layer parallax: parchment plate (back, opaque), oxblood "T" (mid), gold filigree (front). Top layer floats forward on focus.

## Asset Catalog Setup

Modern Tideward project structure:

```
Manu/
  Assets.xcassets/
    AppIcon.icon            ← Icon Composer document (iOS, iPadOS, macOS, watchOS)
  ManuTV/
    Assets.xcassets/
      App Icon & Top Shelf.brandassets/   ← tvOS layered LSR set
  ManuVision/
    Assets.xcassets/
      AppIcon.solidimagestack/            ← visionOS layered icon
```

**Target settings:**
- iOS / iPadOS / macOS / watchOS targets: General → App Icons and Launch Images → App Icon Source = `AppIcon` (the Icon Composer file).
- tvOS target: Top Shelf and App Icon configured via the `.brandassets` bundle.
- visionOS target: AppIcon set via `.solidimagestack` (background + 1–2 front layers).

**The 1024 PNG fallback** still belongs in App Store Connect's marketing-asset slot. App Store Connect does not consume `.icon` files for the storefront listing.

## Asset CDN Hosting

For press kit and brand-asset distribution (`marketing/` repo and downstream hosting):

```
/marketing/brand/icon/
  source/
    tideward-icon.icon              ← Icon Composer source (binary bundle, .icon is a directory)
    tideward-icon-layers.fig        ← Figma working file
    tideward-icon-vector.ai         ← Illustrator working file (optional)
  exports/
    tideward-icon-1024-light.png    ← 1024 × 1024, sRGB, no alpha, App Store primary
    tideward-icon-1024-dark.png     ← Dark variant for press
    tideward-icon-1024-mono.png     ← Tinted/mono variant
    tideward-icon-svg.svg           ← Flattened vector for web (favicons, social)
    tideward-icon-512.png
    tideward-icon-256.png
    tideward-icon-128.png
  press-kit/
    tideward-icon-press-zip.zip     ← Bundled press kit drop
```

Host on Cloudflare R2 under `assets.tideward.app/brand/icon/...`. Public cache, immutable URLs (version the filenames, e.g., `tideward-icon-1024-light-v1.png`), CORS open for embedding.

The `.icon` document itself is a binary bundle and not directly useful to third parties — keep it in the source tree; expose the PNG/SVG exports.

## Anti-Patterns

- **Transparent backgrounds on the App Store icon.** App Store Connect's automated check rejects any alpha channel in the marketing 1024 PNG. Black bleed and instant rejection.
- **Text in icons.** App name shows up under the icon on Home Screens. Repeating it in the mark wastes the canvas and is illegible below 60 pt anyway.
- **Photos as icons.** Apple's review historically rejects photographic icons; system styling is built for marks, not images. Even where it slips through, photos collapse to mush in Mono and Clear modes.
- **Skeuomorphic glass overlays.** Drawing your own specular highlights and reflections fights the system Liquid Glass shader. The result looks doubled and stamped. Provide flat colored layers; let the OS apply the glass.
- **Per-platform brand drift.** A different mark on iPhone vs. Mac vs. Watch breaks recognition. Icon Composer's per-platform overrides are for **adjustments** (drop the filigree on Watch), not redesigns.
- **Detail-dense icons.** Fine line work disappears at Spotlight (40 pt), notifications (20 pt), and watchOS. Design for the smallest size; embellish for the largest.
- **Hand-edited `.icns` files post-Icon-Composer.** Round-tripping through `iconutil` or third-party tools strips the Liquid Glass metadata. Stay in Icon Composer.

## Production Process

1. **Concept (Figma).** Three to five rough directions. Test each as a 60 × 60 thumbnail beside the existing iOS launcher to gut-check legibility.
2. **Vector master (Illustrator or Figma).** Build the chosen mark as separated depth layers — background plate, mid-layer mark, foreground accent. Each layer on its own artboard or frame.
3. **Layer export.** Export each layer as SVG (vectors) or PNG (textures). Omit the platform corner-radius mask. Background layer must be fully opaque; front layers use alpha as needed.
4. **Icon Composer assembly.**
   - New document, target platforms checked (iOS, iPadOS, macOS, watchOS).
   - Import each layer; order back-to-front.
   - Apply Apple's preset Liquid Glass materials per layer (background = matte plate, mid = soft glass, front = high-specular foil).
   - Annotate Dark mode swaps and Mono treatment.
   - Preview against multiple wallpapers and all six appearance modes.
5. **Variant validation.** Visit every mode (Default, Dark, Mono, Clear Light, Clear Dark). Confirm the brand reads in each.
6. **Xcode integration.** Drag `.icon` into the project, set the target's App Icon to the document name. Build and run on real devices for iPhone, iPad, Mac, Watch.
7. **tvOS layered set.** Separate workflow — build LSR with 2–5 layers via Xcode's layered image editor.
8. **visionOS layered set.** Separate workflow — background plate (opaque) plus 1–2 front layers (alpha).
9. **Marketing exports.** Render flat 1024 × 1024 PNG (sRGB, opaque) for App Store Connect. Render Dark and Mono PNGs for press kit. Render SVG flattened for web.
10. **Press kit zip.** Bundle the exports, upload to R2 at `assets.tideward.app/brand/icon/press-kit/`.

## QA Checklist

- [ ] Light mode renders correctly on iPhone (Home, Spotlight, Settings, Notification) — all sizes legible.
- [ ] Dark mode passes — foreground reads against deep backgrounds, no muddy mid-tones.
- [ ] Mono (Tinted) silhouette reads at every system tint hue, including unusual ones (cyan, pink, purple).
- [ ] Clear Light and Clear Dark variants visible against busy wallpapers (photographic, gradient, light, dark).
- [ ] visionOS layers: back plate opaque, front layers alpha-correct, glass shell adds depth without doubling.
- [ ] watchOS rendering at 40 mm and 49 mm survives circular mask, no critical content in corners.
- [ ] tvOS parallax: 2–5 layers stack correctly, focus depth reads naturally, no flickering.
- [ ] macOS 26 Tahoe: `.icon` compiles, `.icns` fallback present for pre-26 versions.
- [ ] App Store Connect marketing 1024: no alpha, sRGB, fully opaque, < 1 MB.
- [ ] Press-kit assets (light, dark, mono, SVG, zip) live on R2 with stable URLs.
- [ ] All variants exported from a single Icon Composer source — no hand-painted variants drifting from the master.
- [ ] Real-device test on at least: iPhone, iPad, Mac, Apple Watch, Vision Pro, Apple TV.

## Sources

- [Icon Composer — Apple Developer](https://developer.apple.com/icon-composer/)
- [Creating your app icon using Icon Composer — Apple Developer](https://developer.apple.com/documentation/Xcode/creating-your-app-icon-using-icon-composer)
- [App icons — Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/app-icons)
- [Create icons with Icon Composer — WWDC25 session 361](https://developer.apple.com/videos/play/wwdc2025/361/)
- [Say hello to the new look of app icons — WWDC25 session 220](https://developer.apple.com/videos/play/wwdc2025/220/)
- [Crafting Liquid Glass app icons with Icon Composer — Create with Swift](https://www.createwithswift.com/crafting-liquid-glass-app-icons-with-icon-composer/)
- [Adapting App Icons for iOS 26's Liquid Glass Style — Hui Wang, Medium](https://medium.com/@foks.wang/adapting-app-icons-for-ios-26s-liquid-glass-style-5bde00f565fa)
- [Updating application icons for macOS 26 Tahoe and Liquid Glass — Successful Software](https://successfulsoftware.net/2025/09/26/updating-application-icons-for-macos-26-tahoe-and-liquid-glass/)
- [Updating App Icons for iOS and macOS 26 — praeclarum.org](https://praeclarum.org/2025/09/12/app-icons.html)
- [Adding Icon Composer icons to Xcode — Use Your Loaf](https://useyourloaf.com/blog/adding-icon-composer-icons-to-xcode/)
- [Preparing your App Icon for dark and tinted appearance — Create with Swift](https://www.createwithswift.com/preparing-your-app-icon-for-dark-and-tinted-appearance/)
- [Oh no, I need to design a tinted iOS 18 app icon — Sketch Blog](https://www.sketch.com/blog/tinted-app-icons/)
- [Adapting your App Icon to visionOS — Create with Swift](https://www.createwithswift.com/adapting-your-app-icon-to-visionos/)
- [Creating Layered Images (tvOS Parallax) — Apple Developer Archive](https://developer.apple.com/library/archive/documentation/General/Conceptual/AppleTV_PG/CreatingParallaxArtwork.html)
- [iOS App Icon Guidelines & Requirements for App Store Approval (2026) — The App Launchpad](https://theapplaunchpad.com/blog/ios-app-icon-guidelines/)
- [Apple introduces a delightful and elegant new software design — Apple Newsroom](https://www.apple.com/newsroom/2025/06/apple-introduces-a-delightful-and-elegant-new-software-design/)
- [Liquid Glass App Icon Design for iOS 26: Complete Guide — Skyscraper](https://getskyscraper.com/blog/liquid-glass-app-icon-design-ios-26-guide)
- [Discover how apps are using the new design and Liquid Glass — Apple Developer Design Gallery](https://developer.apple.com/design/new-design-gallery-2026/)
