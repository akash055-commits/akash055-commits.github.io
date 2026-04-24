# akashchaurasia.com — portfolio

Personal portfolio site. Single-file static HTML; no build step.

## Local preview

Open `index.html` in a browser, or run any static server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy (GitHub Pages)

1. Create a repo on GitHub (e.g. `akashchaurasia05/portfolio` or `akashchaurasia05.github.io` for a user-site URL).
2. Push this directory to it.
3. In the repo → **Settings → Pages** → set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`. Save.
4. Site will be live in ~1 min at `https://<username>.github.io/<repo>/` (or `https://<username>.github.io/` for a user-site).

## Custom domain (optional)

1. Buy a domain (e.g. from Namecheap, Cloudflare, GoDaddy).
2. At your DNS registrar, add:
   - `A` records for `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` for `www` → `<username>.github.io`
3. Add a file named `CNAME` in this repo root containing just your domain (e.g. `akashchaurasia.com`).
4. In **Settings → Pages**, enter the custom domain and wait for the TLS certificate to provision.
