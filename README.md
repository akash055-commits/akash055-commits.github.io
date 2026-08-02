# www.akashm.site

Personal site for Akash Chaurasia. Single-file static HTML — no build step, no dependencies.
Served by GitHub Pages from `main` at the repo root; `CNAME` points it at `www.akashm.site`.

```
index.html                            everything — markup, CSS tokens, JS, all inline
posts.json                            LinkedIn posts, written by the Action (never by hand)
photos/                               .jpeg + .webp pairs, plus og-card.png
favicon.svg  apple-touch-icon.png
robots.txt   sitemap.xml
.github/workflows/                    the LinkedIn feed updater
```

## Local preview

```bash
python3 -m http.server 8000     # then http://localhost:8000
```

## Ground rules

**Every number on this site has to trace back to a source.** Spend, CPV, match rates, fleet size,
dates — if a figure isn't verifiable, it doesn't go on the page. The site previously carried
several that didn't, plus hand-written "LinkedIn posts" with invented engagement counts. Don't
reintroduce either.

**`posts.json` is machine-written.** The workflow fills it from an RSS feed of the real LinkedIn
profile. If the feed is empty or unset the file stays empty and the Writing section hides itself —
that is the intended behaviour, not a bug to patch by typing posts in.

## The LinkedIn feed

Not yet live — it needs a one-time secret:

1. Create a free feed at [rss.app](https://rss.app) from the LinkedIn profile URL.
2. `gh secret set LINKEDIN_RSS_URL --repo akash055-commits/akash055-commits.github.io`
3. Run **Actions → Update LinkedIn Posts → Run workflow** once and confirm `posts.json` fills with
   real post permalinks.

Without the secret the job exits early and succeeds — so a green tick does **not** mean posts
updated. Check `posts.json` itself.

## Images

Each photo ships as a resized `.jpeg` (max 800px, q72) and a `.webp`, wired through `<picture>`
so modern browsers take the WebP. To add one:

```bash
sips --resampleHeightWidthMax 800 photo.jpeg
sips -s format jpeg -s formatOptions 72 photo.jpeg --out photo.jpeg
cwebp -q 74 photo.jpeg -o photo.webp
```

Then add the `<picture>` block with explicit `width`/`height` — they prevent layout shift.

## Deploy

Push to `main`. Pages rebuilds in about a minute.

Settings → Pages → **Enforce HTTPS** must stay on.
