# Dark Line — Site Build

## Files

- `index.html` — full site: SEO markup, structured data, sticky nav, accordion FAQ, brand mark, film-grain texture.
- `robots.txt`, `sitemap.xml` — crawler/indexing config.
- `site.webmanifest` — icon + PWA metadata (lets browsers show your brand mark when saved to a home screen).
- `assets/favicon.svg` — ready to use immediately, no export needed. Modern browsers render SVG favicons natively.
- `assets/og-image.svg` — source for your social share image. **Needs one manual step below.**

## The one manual step: export `og-image.png`

Facebook, Twitter/X, Discord, and iMessage link previews require a real raster image file — they don't read SVGs. I can't rasterize it in this environment, so:

1. Open `assets/og-image.svg` in a browser (drag the file in) or import it into Figma/Canva.
2. Export at exactly **1200x630px**, PNG.
3. Save it as `assets/og-image.png` in your repo.
4. Also export a 192x192 PNG from `favicon.svg` and save as `assets/favicon.png` (covers Safari/older browsers referenced in the manifest and `<link rel="alternate icon">`).

Until you do this, the page still works fine — it just falls back to a blank/default preview when shared on platforms that require PNG.

## Everything else is drop-in

1. Copy `index.html`, `robots.txt`, `sitemap.xml`, `site.webmanifest` into your repo root.
2. Copy the `assets/` folder in alongside them (add the two PNGs from the step above).
3. Commit, push, done.

## What changed in this pass (vs. the earlier draft)

- **Fixed the canonical URL mismatch** — meta tags now correctly point to `https://darkline-editz.github.io/darkline/`.
- **Real brand mark** — an actual SVG mark (not just text) in the nav, favicon, and OG image, so the brand is recognizable, not generic.
- **Working icons** — before, `favicon.png`/`og-image.png` were referenced but never existed. Now there's a real SVG favicon (works today) and an OG image source ready to export.
- **Accordion FAQ** — uses native `<details>/<summary>`, so it's interactive, accessible, and needs zero JavaScript.
- **Sticky nav** with a subtle blur-on-scroll, and a light film-grain texture — small touches that read as intentional rather than templated.
- **Structured data, sitemap, robots.txt** — unchanged from the SEO pass, still in place.

## Reminder: SEO ceiling for this kind of site

This is a strong, correct landing page — it'll index cleanly and look right when shared. But for a TikTok edit channel, discovery happens on TikTok's algorithm, not Google search. Treat this site as your link-in-bio / credibility page, not your main growth lever. Posting consistency, trending audio, and strong hooks in the first two seconds will move the follower count far more than any amount of on-page SEO.
