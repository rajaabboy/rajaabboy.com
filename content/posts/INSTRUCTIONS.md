# Adding "LinkedIn Posts" to the Writing page (rajaabboy.com)

Your site is a Hugo static site. These three files add a filterable
LinkedIn Posts card grid to the Writing (`/posts/`) page.

## 1. Copy files into your repo

```
data/linkedin_posts.yaml            → repo-root/data/linkedin_posts.yaml
layouts/partials/linkedin-posts.html → repo-root/layouts/partials/linkedin-posts.html
assets/css/linkedin-posts.css       → repo-root/assets/css/linkedin-posts.css
```

If your repo already has `data/`, `layouts/partials/`, or `assets/css/`
folders, just drop these files in alongside what's there — don't overwrite
anything else.

## 2. Fill in the real post content

Open `data/linkedin_posts.yaml` and replace the placeholder `title`,
`excerpt`, and `date` for both posts with the actual text (I couldn't pull
this automatically — LinkedIn blocks scraping). To add a new post later,
copy one of the existing blocks and fill in the five fields.

## 3. Link the CSS

If your theme pipes CSS through Hugo Pipes (most themes with an
`assets/css/` folder do), add this line wherever your theme's main CSS
bundle is assembled — typically in `layouts/_default/baseof.html` or a
`head.html` partial:

```go-html-template
{{ $linkedinCSS := resources.Get "css/linkedin-posts.css" }}
<link rel="stylesheet" href="{{ $linkedinCSS.RelPermalink }}">
```

If your theme instead just serves `static/`, move the CSS file to
`static/css/linkedin-posts.css` and link it directly:

```html
<link rel="stylesheet" href="/css/linkedin-posts.css">
```

## 4. Render the section on the Writing page

Find the template that renders `/posts/` (likely
`layouts/posts/list.html`, `layouts/_default/list.html`, or wherever
`content/posts/_index.md` is rendered from) and add:

```go-html-template
{{ partial "linkedin-posts.html" . }}
```

Place it wherever you want the section to appear — e.g., right after the
"Nothing here yet." text, or replacing it once you have real posts listed
elsewhere too.

## 5. Preview and adjust styling

Run `hugo server` locally and check `/posts/`. The CSS uses generic
variable names (`--color-accent`, `--color-border`, etc.) with fallback
colors so it renders reasonably even without your theme's variables — but
for a pixel-perfect match, check your theme's actual CSS variable names
(search your `assets/css/` or `static/css/` for `:root {`) and swap them
in, or just hand-adjust the fallback hex values in
`linkedin-posts.css`.

## 6. Deploy

Commit and push as usual — same flow you use for any other content change.
