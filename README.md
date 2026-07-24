# rajaabboy.com

Personal site for Raja Abboy — Senior Service Delivery Manager, Global Delivery
& Program Leadership. Built with [Hugo](https://gohugo.io), using the same
minimal, content-first layout approach (sticky sidebar + single scrolling
content column, Instrument Serif + Lora typography, warm neutral palette) as
the reference site this was modeled on. No JS framework, no build step beyond
Hugo itself, no client-side dependencies except two Google Fonts.

See [CONTENT.md](CONTENT.md) for exactly what content is real (sourced
directly from Raja) vs. still a placeholder.

## Quick start

1. **Install Hugo** (extended version): https://gohugo.io/installation/
2. **Run the dev server**:
   ```bash
   hugo server -D
   ```
3. Open http://localhost:1313

## Build for production

```bash
hugo --minify
```

Output goes to `public/`. That folder is git-ignored — it's a build artifact,
not source.

## Project structure

```
rajaabboy.com/
├── hugo.toml                 # Site config: params, menu, markup
├── content/
│   ├── about.md              # About page (full bio)
│   └── posts/
│       └── _index.md         # Writing index (empty for now — see CONTENT.md)
├── layouts/
│   ├── index.html            # Homepage: Experience, Selected Work, stats, skills
│   ├── partials/
│   │   ├── head.html         # <head>: meta, OG tags, fonts
│   │   ├── sidebar.html      # Sticky sidebar: name, tagline, bio, nav, connect
│   │   └── footer.html       # Footer (used on non-home pages via nav.html pattern)
│   └── _default/
│       ├── single.html       # Individual post/page template
│       └── list.html         # Writing archive template
├── static/
│   ├── avatar.svg            # Initials-based placeholder avatar ("RA")
│   ├── favicon.svg           # Initials-based favicon ("RA")
│   └── css/main.css          # All site styling
└── RAJA_CONTENT_SOURCE.md    # Original content brief supplied by Raja (not a Hugo page)
```

## Deployment (Cloudflare Pages via GitHub Actions)

`.github/workflows/deploy.yml` builds the site with Hugo and deploys it to
Cloudflare Pages on every push to `main` (and creates a preview deployment
for pull requests) using `cloudflare/wrangler-action`.

**One-time setup, done in the Cloudflare dashboard and GitHub — not by me:**

1. **Create the Pages project** (Cloudflare dashboard → Workers & Pages →
   Create → Pages → "Direct Upload", or let the first Actions run create it —
   `wrangler pages deploy` creates the project automatically if it doesn't
   exist yet, as long as the API token has permission). Project name must
   match `CLOUDFLARE_PAGES_PROJECT` in the workflow file (currently
   `rajaabboy-com`).
2. **Create a scoped API token**: Cloudflare dashboard → My Profile →
   API Tokens → Create Token → custom token with **Account → Cloudflare
   Pages → Edit** permission (no need for a broader/global key).
3. **Find your Account ID**: Cloudflare dashboard → any domain's Overview
   page → right sidebar → "Account ID".
4. **Add both as GitHub Actions secrets** (repo → Settings → Secrets and
   variables → Actions → New repository secret) — not pasted anywhere else:
   - `CLOUDFLARE_API_TOKEN`
   - `CLOUDFLARE_ACCOUNT_ID`
5. **Custom domain**: once the project has deployed at least once, go to the
   Pages project → Custom domains → Add `rajaabboy.com` (and `www` if wanted).
   This only auto-configures DNS if `rajaabboy.com` is already an active zone
   in the same Cloudflare account; otherwise you'll need to point the
   registrar's nameservers at Cloudflare first.

No secrets are needed in this repo or in `hugo.toml` — `baseURL` is already
set to `https://rajaabboy.com`.

## Content TODO checklist

These are the only things still needed before this site is 100% real:

- [ ] **Professional headshot** — replace `/avatar.svg` with a real photo
      (referenced in `layouts/partials/sidebar.html`, `data-placeholder="RAJA_PHOTO_URL"`)
- [ ] **Résumé PDF** — drop the final résumé at `static/resume.pdf` (path is
      already wired up via `params.resume` in `hugo.toml` and linked from the
      sidebar + footer as "Résumé")
- [ ] **Testimonials/recommendations** — not built yet; add 2–3 quotes with
      name/title/company once available (see `RAJA_CONTENT_SOURCE.md`)
- [ ] **Writing** — the Writing section/page is empty by design (no real
      articles exist yet). Add posts under `content/posts/` when ready;
      the homepage and `/posts/` list will pick them up automatically.
- [ ] **Optional**: phone number, if Raja wants it public (currently omitted
      per the source brief's own caution)
- [ ] **Optional**: confirm which client/project names in "Selected Work" are
      OK to publish as-is

Everything else on the site (name, title, company history, achievements,
skills, bio) is sourced directly from `RAJA_CONTENT_SOURCE.md`, which Raja
supplied — see [CONTENT.md](CONTENT.md) for the full sourcing breakdown.
