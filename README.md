# Dark Line

Master repo for the **Dark Line** TikTok channel landing page — automotive and motorsport video edits (drift, phonk/funk, night runs, hypercar cuts).

🔗 Live site: `https://<your-username>.github.io/<repo-name>/` (or your custom domain)

## Repo structure

```
.
├── index.html              # Full landing page (HTML/CSS/JS, no build step)
├── 404.html                # Branded not-found page
├── favicon.svg             # Scalable brand mark (used by modern browsers)
├── site.webmanifest        # PWA manifest — home-screen install on mobile
├── robots.txt               # Crawler rules + sitemap pointer
├── sitemap.xml              # Search engine index map (includes image entry)
├── .nojekyll                # Disables GitHub's Jekyll processing
├── README.md
└── assets/
    ├── og-image.png         # 1200×630 social share preview (OG/Twitter)
    ├── apple-touch-icon.png # 180×180 iOS home-screen icon
    ├── icon-192.png         # PWA icon
    ├── icon-512.png         # PWA icon
    ├── favicon-32.png       # Fallback favicon (older browsers)
    └── favicon-16.png       # Fallback favicon (older browsers)
```

## SEO coverage in this repo

- **Meta basics** — title, description, keywords, robots, canonical, author, theme-color
- **Open Graph + Twitter Cards** — full tag set with a real 1200×630 image, so links shared on TikTok bio, Discord, WhatsApp, or X render with a proper preview card instead of a blank box
- **JSON-LD structured data** — `Organization`, `WebSite`, `ItemList`/`VideoObject` (for the featured edits), and `FAQPage` (matched to the visible FAQ section on the page)
- **robots.txt + sitemap.xml** — including an image sitemap entry
- **Favicon/icon set** — SVG + PNG fallbacks + Apple touch icon + PWA manifest, so the brand mark shows up correctly on every device and if someone adds the site to their home screen
- **Performance** — font preconnect hints, `font-display: swap` on Google Fonts

## Before you deploy — update these

1. **TikTok handle** — `index.html` has `@darkline` as a placeholder in the nav, hero button, follow CTA, footer, and in three JSON-LD blocks (`Organization.sameAs`, and the `contentUrl` fields in the `ItemList`). Find-and-replace with your real handle.
2. **Domain / canonical URL** — replace `https://darkline.github.io/` everywhere it appears (`index.html` head, OG/Twitter tags, JSON-LD, `robots.txt`, `sitemap.xml`) once you know your real GitHub Pages URL or custom domain.
3. **Featured Edits section** — the three reel cards and their matching `VideoObject` schema entries (`Midnight Angle`, `Bass First`, `Wet Asphalt`) are placeholders. Swap in real clips/thumbnails and update the schema `uploadDate`/`name`/`description` to match once you have edits published.

## Deploying with GitHub Pages

1. Create a new GitHub repository (public).
2. Upload all files in this folder to the repo root, preserving the `assets/` folder — or push via git (below).
3. Go to **Settings → Pages**.
4. Under **Source**, select branch `main`, folder `/ (root)`.
5. Save. Live in a few minutes at `https://<your-username>.github.io/<repo-name>/`.

```bash
git init
git add .
git commit -m "Dark Line master site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Custom domain (optional)

Add a `CNAME` file to the repo root containing just your domain (e.g. `darkline.com`), then update every URL reference listed above to match.

## After going live

- Submit the site + `sitemap.xml` to [Google Search Console](https://search.google.com/search-console)
- Submit to [Bing Webmaster Tools](https://www.bing.com/webmasters) as well — separate index, worth the two minutes
- Test the social preview card with [Facebook's Sharing Debugger](https://developers.facebook.com/tools/debug/) and [Twitter/X Card Validator](https://cards-dev.twitter.com/validator) once the domain is live, since both cache old previews aggressively
- Keep the visible FAQ section and the `FAQPage` schema in sync if you edit either — mismatched structured data can get it ignored or flagged
