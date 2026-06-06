# Image Alt Text Writing Guide (Press / Web / App)

> Filed: 2026-06-01. Tier: WARM (every screenshot, every social card).

## TL;DR

Alt text is the parallel text track for an image. Screen-reader users, search crawlers, AI agents, and broken-connection viewers all rely on it. Most alt is short (8–15 words), context-dependent, never prefixed with "image of," and frequently empty (`alt=""`) for decoration. The single rule that subsumes the others: **read your alt aloud where the image used to be, and the page should still make sense.**

For Tideward and Manu Games surfaces, every App Store screenshot, every OG card, every press-kit shot, and every Beehiiv newsletter hero gets alt before it ships. The 30-second cost is paid back the first time a low-vision player or a Pocket Tactics editor parses your post on a screen reader.

## The Five Image Categories

WCAG 1.1.1 (the "text alternatives" rule) treats every non-text image as one of five things, and each gets a different alt treatment.

### 1. Decorative (`alt=""`)

Visual flourishes that carry no information: section dividers, background motifs, the manuscript filigree on `manugames.com`, ornamental drop caps, parchment textures. A sighted user loses nothing if they vanish.

- **Alt approach:** Empty quotes, no space between them (`alt=""`). A space character can break the "skip me" signal in some assistive tech.
- **Length:** Zero.
- **Caption rule:** Never captioned. If you feel the urge to caption it, it isn't decorative; re-classify.

### 2. Functional

Images that *do* something when activated: a clickable app icon that opens the App Store page, a social-icon link to Bluesky, a play button overlay on a video thumbnail.

- **Alt approach:** Describe the **action**, not the picture. The magnifying glass that submits a search is `alt="Search"`, not `alt="magnifying glass icon"`. The Tideward icon that links to the App Store is `alt="Open Tideward on the App Store"`, not `alt="Tideward app icon"`.
- **Length:** 2–6 words.
- **Caption rule:** Almost never. The function is the alt.

### 3. Informative

The workhorse category: a screenshot that demonstrates a UI, a photo that anchors a press piece, an illustration that conveys a concept the surrounding prose relies on. Most images on tideward.app and in the press kit live here.

- **Alt approach:** Describe what the image contributes to the page. Lead with the load-bearing detail.
- **Length:** 8–15 words (~80–140 characters). One short sentence.
- **Caption rule:** Often paired with a visible caption. The caption is for everyone; the alt is for assistive tech. Avoid full duplication; see the captioning section below.

### 4. Complex

Maps, charts, infographics, skill trees, progression diagrams, the in-game world map. There is more information than a single alt-line can hold.

- **Alt approach:** Short alt that identifies the image and points to a full text alternative ("Tideward skill tree, full text equivalent below"). Then provide the long description as on-page prose, a data table, or a hidden `<details>` block beneath the image.
- **Length:** Alt 10–15 words; long description as long as the data requires.
- **Caption rule:** Caption with a short summary; let the long description carry the detail.

### 5. Text-in-Image

A poster that contains a slogan, a screenshot of code, a name plate, a chyron, an in-game banner with story text, a marketing card with a price.

- **Alt approach:** Quote the visible text verbatim, then briefly note the design only if the design carries meaning. Posters: `alt="Tideward launch poster: 'An Idle Almanac. June 2026.' over a teal tide motif."`
- **Length:** As long as the text itself, full stop. This is one of the few legitimate places for longer alt.
- **Caption rule:** If the text already appears as real on-page text right next to the image, the image becomes decorative (`alt=""`); don't have the screen reader read it twice.

## The "If You Removed The Image" Test

Read the page aloud, substituting your alt where the image was, then ask:

1. Does the surrounding prose still make grammatical sense?
2. Does it still convey the same information a sighted reader gets?
3. Did I duplicate something the adjacent paragraph or caption already says?

If 1 and 2 are yes and 3 is no, the alt is good. If the page goes mute at the image's role, the alt is too short. If it stutters and repeats the caption, the alt is redundant: either drop it (decorative) or rewrite the caption to play a different role.

This test catches more bad alt than any character-count rule.

## Tideward Asset Examples

Drafts for the assets that move most across our surfaces. These are the live recommendations; copy them when uploading.

- **App icon (1024×1024 master) used as a thumbnail link on the press kit:** `alt="Open Tideward press kit"` (functional). If the same icon is decorative inside a paragraph that already names the app: `alt=""`.

- **App Store screenshot 1, Almanac home screen with daily entries:** `alt="Tideward Almanac home: today's entry 'A Quiet Tide' above an inventory of three idle generators."` Lead with what the screen *is*, then the load-bearing UI detail.

- **App Store screenshot 2, combat tap interaction:** `alt="Tap-to-fish action: a player ties a knot while a sea-foam progress bar fills under the cast button."`

- **OG image on tideward.app/, hero illumination with title lockup:** `og:image:alt` and `twitter:image:alt` both set to `"Tideward, An Idle Almanac. Illuminated manuscript title page in oxblood and parchment."`

- **OG image on manugames.com/, publisher hub:** `"Manu Games, illuminated publisher hub showing three games as manuscript folios."`

- **Press-kit key art (1920x1080 hero):** `alt="Tideward key art: a lone scribe at a tide-line desk, illuminated manuscript pages drifting on the water."` Press editors who reblog the image often copy the alt verbatim, so write for that downstream use.

- **Blog featured image (newsletter post hero):** `alt="Issue 12 cover: a parchment scroll labelled 'Why we idle.'"` Brand voice OK if the surrounding post supports it.

- **Manuscript divider motif on manugames.com:** `alt=""` (decorative every time).

- **Founder headshot in press kit and on About page:** `alt="Seth, founder of Manu Games."` Not "headshot of," not "photo of." Name plus role.

- **Newsletter inline GIF showing a UI demo:** `alt="Loop of the Tideward Almanac scrolling from today's entry to a past week's tide reading."` Describe what the loop demonstrates, not every frame.

## Length Sweet Spot

8–15 words for the typical informative image. About 80–140 characters. Lead with the most important detail because some screen-reader users will skip after the first clause.

The "125-character hard cap" is widely repeated and largely a myth. No major screen reader actually truncates alt text; JAWS splits long alt into multiple chunks, and a user cannot pause or rewind inside an alt string, which is the real reason to stay brief. Treat 125 as a *style* limit, not a *technical* one. When the image legitimately needs more text (a chart, a poster with body copy), use a long description on the page rather than stuffing it all into the alt attribute.

## When to Caption Beyond Alt

Captions are visible to everyone. Alt is for assistive tech and machine readers. They sometimes overlap and sometimes complement.

- **Press images:** brief caption ("Tideward main screen, June 2026 build") plus descriptive alt ("Tideward Almanac home: today's entry above three idle generators."). The caption lets the journalist credit the build; the alt gives a screen-reader user the visual content.
- **Editorial illustrations:** if the caption fully describes the picture, the alt can be empty (`alt=""`); don't make a screen reader hear the same words twice. Some publications mark these as decorative deliberately so the caption does the lifting.
- **Marketing OG cards:** captions don't apply (no surrounding paragraph); the alt is the only text alternative, so make it carry the whole load.
- **Charts and skill trees:** caption gets the title; alt points to the long description; long description carries the data.

The defensive default for press: brief caption, descriptive alt, no duplication. Reviewers will quote both downstream.

## Alt for OG Images

OG images appear in social previews on iMessage, Slack, Discord, Bluesky, X, LinkedIn, and Mastodon. Two layers of accessibility apply.

1. **The meta-tag layer.** `og:image:alt` and `twitter:image:alt` are the protocol-level fields. Support is patchy: some unfurlers honor them, others ignore them, and X notoriously renders the unfurled image with `aria-hidden="true"` so the meta-tag alt may not reach the user. Set both fields anyway. It costs nothing and the more conformant unfurlers (Slack, Discord, Mastodon, Bluesky) will read them.
2. **The platform-upload layer.** When you upload an image directly to Bluesky, X, LinkedIn, Mastodon, or Threads, each platform gives you a dedicated alt field. **This is the one users actually hear.** Bluesky allows up to 2000 characters and can be configured to require alt before posting. X shows an "ALT" badge when alt is present. Always fill these.

For Tideward marketing posts, treat the per-platform alt as the load-bearing accessibility surface and the OG meta tag as a courtesy to the unfurler ecosystem.

## Alt for Screenshots

Screenshots are the high-frequency case in indie press and App Store work. Three rules.

- **Describe what the screen shows and the action being demonstrated, not pixel-level UI.** Bad: "Tideward UI with green button in upper right, three icons in the middle row, status bar at the top." Good: "Tideward Almanac home with a tide reading at the top and three idle generators producing logs, ink, and bone meal."
- **Lead with the screen's identity** ("Tideward Almanac home...", "Settings, Game Center..."). Screen-reader users navigating a gallery of screenshots need the orientation cue first.
- **Prefixing with "screenshot of" is genuinely contested.** WAI and most general guides say drop it; some accessibility teams writing for game press recommend leading with "Screenshot of..." so a user browsing a gallery knows the image type matters. For Tideward: **drop the prefix on App Store / press / OG** (the context already implies it) but **keep "Screenshot:" in newsletter post galleries** where the image type is part of the editorial framing.

## Anti-Patterns

Common mistakes, all caught by the "read it aloud" test.

- **"Image of...", "Photo of...", "Picture of..." prefixes.** Screen readers already announce "graphic" before alt. Prefix produces "graphic, image of a scribe": twice the noun.
- **Restating the filename.** `alt="DSC_2284.jpg"` or `alt="tideward-hero-v3-final-final.png"` is worse than no alt at all.
- **SEO keyword stuffing.** Cramming search terms into alt harms users and search engines flag it.
- **Empty alt on informative images.** If the image carries information, it gets alt.
- **Describing color when irrelevant.** "A blue button" tells a screen-reader user nothing; "Save button" does. Color belongs in alt only when it carries meaning.
- **Restating the caption verbatim.** Forces screen-reader users to hear the same sentence twice. Drop the alt or split roles.
- **"Click here" / "Learn more" for linked images.** The alt should name the destination: `alt="Read the press kit"`.
- **Ending without a period.** Screen readers use terminal punctuation to pause cleanly before the next element.

## Tone Considerations

Alt text has a voice, even though most users will never read it.

- **Press images:** neutral, factual, descriptive. Press editors copy alt into their CMS verbatim more often than you would expect, so keep it citation-safe.
- **Blog and newsletter images:** can be lightly evocative if the post supports it. "Issue 12 cover: a parchment scroll labelled 'Why we idle.'" is fine. "A glorious parchment scroll asking the eternal question of idleness" is not.
- **Marketing OG cards:** informative first, brand-voiced second. The unfurled card is often the user's first encounter with the brand, so getting "Tideward, An Idle Almanac" into the alt buys real recognition.
- **Functional alt:** dead-flat. "Open Tideward on the App Store." That is the whole job.

Across all four, avoid AI voice tells, em dashes (per Tideward house style as of May 2026), and adjective stacking.

## Workflow for Tideward

A 30-second-per-asset routine that fits any upload flow.

1. **Classify** the image into one of the five categories before writing anything. Most decisions collapse out of the classification.
2. **Draft** in 8–15 words for informative; 2–6 for functional; quote the text for text-in-image; empty for decorative.
3. **Read it aloud** where the image is. The test catches 90% of mistakes.
4. **Paste into image metadata.** For Tideward this means:
   - App Store Connect screenshot alt fields (per locale).
   - Astro `<img alt="...">` for tideward.app and manugames.com.
   - `og:image:alt` and `twitter:image:alt` in the page `<head>`.
   - Bluesky / X / Mastodon / LinkedIn alt fields on every social post.
   - Beehiiv inline image alt field on every newsletter hero and inline shot.
   - Press kit PDF / press release attachments: describe key art in the caption block.
5. **Spot-check with assistive tech once per surface.** Turn on VoiceOver on macOS (`Cmd+F5`) or iOS, tab to the image, listen. On Android, TalkBack. On Windows, Narrator. Once per surface is enough; you're checking the rendering, not every individual alt.

Build the habit into the upload step, not as a separate accessibility sweep. Retrofitting alt across hundreds of past assets is the kind of debt that never gets paid down.

## Sources

- [W3C Web Accessibility Initiative — Images Tutorial: Tips and Tricks](https://www.w3.org/WAI/tutorials/images/tips/)
- [W3C WAI — Decorative Images](https://www.w3.org/WAI/tutorials/images/decorative/)
- [W3C WAI — Functional Images](https://www.w3.org/WAI/tutorials/images/functional/)
- [W3C WAI — Complex Images](https://www.w3.org/WAI/tutorials/images/complex/)
- [WebAIM — Alternative Text](https://webaim.org/techniques/alttext/)
- [Section508.gov — Authoring Meaningful Alternative Text](https://www.section508.gov/create/alternative-text/)
- [Eric Eggert — There Is No Character Limit For Alt Text (Myth Debunked)](https://yatil.net/blog/there-is-no-character-limit-for-alt-text)
- [CSS-Tricks — Just How Long Should Alt Text Be?](https://css-tricks.com/just-how-long-should-alt-text-be/)
- [Deque — Writing Alt Text For Accessibility: Guidelines And Examples](https://www.deque.com/blog/great-alt-text-introduction/)
- [Accessible Social — Alt Text on Bluesky](https://www.accessible-social.com/images-and-visuals/alt-text/bluesky)
- [Accessible Social — Alt Text on Twitter/X](https://www.accessible-social.com/images-and-visuals/alt-text/twitter)
- [Accessible Social — Platform Image Accessibility](https://www.accessible-social.com/images-and-visuals/platform-image-accessibility)
- [Stefan Judis — How to Define Open Graph / Twitter Image Alt Text](https://www.stefanjudis.com/today-i-learned/how-to-define-open-graph-twitter-image-alt-text-and-why-it-might-not-matter/)
- [OGfeed — The Role of Alt Text and Accessibility in Open Graph Images](https://ogfeed.com/blog/open-graph-alt-text/)
- [Harvard HUIT Digital Accessibility — Write Helpful Alt Text](https://accessibility.huit.harvard.edu/describe-content-images)
- [Penn State — Image ALT Text](https://accessibility.psu.edu/images/alttext/)
- [Princeton Digital Accessibility — Alternative Text](https://digital.accessibility.princeton.edu/how/content/alternative-text)
- [Princeton University Press — Alt Text Guidelines](https://press.princeton.edu/resources/alt-text-guidelines)
- [Penn — Alternative Text for Complex Images](https://accessibility.web-resources.upenn.edu/resources/content-creators/alternative-text-complex-images)
- [Equidox — Beyond Basic Alt Text: Charts, Maps, And Diagrams](https://equidox.co/blog/beyond-basic-alt-text-charts-maps-and-diagrams/)
- [University of South Carolina — Logo Alt Text](https://sc.edu/about/offices_and_divisions/digital-accessibility/toolbox/best_practices/alternative_text/logo-alt-text/index.php)
- [Search Engine Journal — Google Explains Alt Text For Logos & Buttons](https://www.searchenginejournal.com/alt-text-for-logos-and-buttons/469801/)
- [Bureau of Internet Accessibility — Should You Include Alt Text for Pictures with Captions?](https://www.boia.org/blog/should-you-include-alt-text-for-pictures-with-captions)
- [Bureau of Internet Accessibility — When Should I Use Empty (or Null) Alt Text Attributes?](https://www.boia.org/blog/when-should-i-use-empty-or-null-alt-text-attributes)
- [AccessibleWeb — If Images Have Captions, Do They Need Alt Text?](https://accessibleweb.com/question-answer/if-images-have-captions-do-they-need-alt-text/)
- [Industry Dive Design (Medium) — Designing a Newsroom's Alt Text and Captions](https://medium.com/industry-dive-design/designing-a-newsrooms-alt-text-and-captions-can-be-complicated-here-s-how-we-tackled-it-efadae4de482)
- [Itch.io community thread — Alt Text on Images (indie game perspective)](https://itch.io/t/3401001/alt-text-on-images)
- [Pocket Gamer Biz — How Do Indie Developers Address Accessibility in Video Games?](https://www.pocketgamer.biz/how-do-indie-developers-address-accessibility-in-video-games/)
- [AppleVis — Accessibility Statement (model of alt usage in Apple-focused press)](https://www.applevis.com/accessibility)
- [AppleVis — Alt Text Generator app listing](https://www.applevis.com/apps/ios/utilities/alt-text-generator)
- [Axess Lab — Alt-Texts: The Ultimate Guide](https://axesslab.com/alt-texts/)
- [TestParty — Alt Text Guide: Writing Effective Image Descriptions for WCAG Compliance](https://testparty.ai/blog/alt-text-guide)
- [Level Access — Alt Text for Accessibility: Examples, Tips & Best Practices](https://www.levelaccess.com/blog/alt-text-for-accessibility/)
- [Siteimprove — Accessibility: Image Alt Text Best Practices](https://help.siteimprove.com/support/solutions/articles/80000863904-accessibility-image-alt-text-best-practices)
