# Dark Line — SEO Setup Guide

Files in this bundle:

- `index.html` — your page rebuilt with full SEO markup (meta tags, Open Graph, Twitter cards, JSON-LD structured data for Organization/FAQ/Breadcrumb). Content and structure match your live site; styling is a placeholder — swap in your real CSS/JS.
- `robots.txt` — tells search engines they can crawl everything and where your sitemap is.
- `sitemap.xml` — a minimal sitemap listing your one page.

## 1. Fix the URL mismatch (do this first)

Your live site is at `https://darkline-editz.github.io/darkline/`, but the page's own meta tags (canonical, og:url, twitter:image, etc.) pointed to `https://darkline.github.io/` — a different, likely non-existent domain. Search engines use those tags to decide which URL is the "real" one, so this was actively confusing indexing. I corrected every reference to `https://darkline-editz.github.io/darkline/` in the new file.

If you ever move to a custom domain (see #5), update all of these again.

## 2. Drop these files into your repo

1. Copy your existing `<style>`/CSS and any JS from your current `index.html` into the new one (marked with a comment block).
2. Copy `robots.txt` and `sitemap.xml` into the **repo root** (same folder as `index.html`), so they're served at `/darkline/robots.txt` and `/darkline/sitemap.xml`.
3. Commit and push.

## 3. Submit to Google

- Go to [Google Search Console](https://search.google.com/search-console), add the property `https://darkline-editz.github.io/darkline/`, verify via the HTML tag method (or DNS if you get a custom domain).
- Submit `sitemap.xml` under Sitemaps.
- Use "Request Indexing" on the URL once it's live.

Do the same for [Bing Webmaster Tools](https://www.bing.com/webmasters) — it's low effort and Bing also feeds DuckDuckGo/Yahoo.

## 4. Embed actual TikTok videos, not just thumbnails

Right now "Latest Edits" is styled text with no real video. Search engines (and visitors) get far more value from embedded, playable clips. I left a code sample in `index.html` using TikTok's official oEmbed `<blockquote>` — just swap in your real video IDs for your 3–5 newest posts. This also turns each clip into its own indexable `VideoObject`.

## 5. Bigger wins, roughly in priority order

1. **Custom domain** (e.g. `darkline.tv` or similar) — `github.io` subdomains carry less authority than a root domain you own, and a clean domain is easier to put in TikTok bio/video captions.
2. **Real `og-image.png` and favicon** at `/assets/` — confirm these files actually exist at the paths referenced; a broken OG image kills link-preview click-through on Discord/Twitter/iMessage shares.
3. **Backlinks from TikTok**: put the site link in your TikTok bio and pin a video that says "full drop schedule + past edits: [link]" — TikTok bio links carry real referral SEO signal.
4. **Content velocity**: since this is a single static page, your main "content freshness" signal to Google is updating `Latest Edits` weekly and keeping `sitemap.xml`'s implicit last-modified fresh (add a `<lastmod>` tag each time you update, e.g. `<lastmod>2026-10-01</lastmod>`).
5. **Alt text on every image** once you add real thumbnails (`<img src="..." alt="Drift edit — Midnight Angle, phonk soundtrack">`) — this is both an accessibility and image-search ranking factor.
6. **Page speed**: keep images compressed/WebP and avoid heavy JS frameworks for a page this simple — Core Web Vitals affect ranking.

## Why this helps

- **JSON-LD structured data** makes you eligible for rich results (FAQ dropdowns in Google, richer link previews) instead of a plain blue link.
- **Correct canonical/OG tags** stop Google and social platforms from indexing/previewing a broken or wrong URL.
- **Sitemap + robots.txt** speed up discovery — without them Google has to find your page organically, which can take weeks longer.
- **TikTok embeds** give Google actual video content to index under Video results, not just static text.
